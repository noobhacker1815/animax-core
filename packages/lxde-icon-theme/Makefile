include $(SUPPORT_DIR)/functions.mk

SOURCE := $(SOURCES_DIR)/lxde-icon-theme-0.5.1.tar.xz
SOURCE_URL := https://downloads.sourceforge.net/lxde/lxde-icon-theme-0.5.1.tar.xz
MD5 := 7467133275edbbcc79349379235d4411

system:
	@export CC=$(TOOLS_DIR)/usr/bin/$(CONFIG_TARGET)-gcc
	@export CXX=$(TOOLS_DIR)/usr/bin/$(CONFIG_TARGET)-g++
	@export AR=$(TOOLS_DIR)/usr/bin/$(CONFIG_TARGET)-ar
	@export AS=$(TOOLS_DIR)/usr/bin/$(CONFIG_TARGET)-as
	@export LD=$(TOOLS_DIR)/usr/bin/$(CONFIG_TARGET)-ld
	@export RANLIB=$(TOOLS_DIR)/usr/bin/$(CONFIG_TARGET)-ranlib
	@export READELF=$(TOOLS_DIR)/usr/bin/$(CONFIG_TARGET)-readelf
	@export STRIP=$(TOOLS_DIR)/usr/bin/$(CONFIG_TARGET)-strip
	@$(STEP) "lxde-icon-theme 0.5.1"
	@$(call check_source, $(SOURCE), $(MD5), $(SOURCE_URL))
	@$(EXTRACT) $(SOURCE) $(BUILD_DIR)
	@( cd $(BUILD_DIR)/lxde-icon-theme-0.5.1 && \
	PKG_CONFIG="$(TOOLS_DIR)/usr/bin/pkg-config" \
	ac_cv_lbl_unaligned_fail=yes \
	ac_cv_func_mmap_fixed_mapped=yes \
	ac_cv_func_memcmp_working=yes \
	ac_cv_have_decl_malloc=yes \
	gl_cv_func_malloc_0_nonnull=yes \
	ac_cv_func_malloc_0_nonnull=yes \
	ac_cv_func_calloc_0_nonnull=yes \
	ac_cv_func_realloc_0_nonnull=yes \
	lt_cv_sys_lib_search_path_spec="" \
	ac_cv_c_bigendian=no \
	CONFIG_SITE=/dev/null \
	./configure \
	--target=$(CONFIG_TARGET) \
	--host=$(CONFIG_TARGET) \
	--build=$(CONFIG_HOST) \
	--prefix=/usr \
	--exec-prefix=/usr \
	--sysconfdir=/etc \
	--localstatedir=/var \
	--program-prefix="" \
	--disable-static \
	--enable-shared )
	@make -j$(CONFIG_PARALLEL_JOBS) DESTDIR=$(SYSROOT_DIR) install -C $(BUILD_DIR)/lxde-icon-theme-0.5.1
	@$(call dependency_libs_patch)
	@make -j$(CONFIG_PARALLEL_JOBS) DESTDIR=$(ROOTFS_DIR) install -C $(BUILD_DIR)/lxde-icon-theme-0.5.1
	@rm -rf $(BUILD_DIR)/lxde-icon-theme-0.5.1
