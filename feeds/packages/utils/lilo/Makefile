# 
# Copyright (C) 2006 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#
# $Id: Makefile 11744 2008-07-07 15:19:23Z florian $

include $(TOPDIR)/rules.mk

PKG_NAME:=lilo
PKG_VERSION:=22.8
PKG_RELEASE:=1

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).src.tar.gz
PKG_SOURCE_URL:=ftp://metalab.unc.edu/pub/Linux/system/boot/lilo/
PKG_MD5SUM:=72765f2aafd20e23ecf07ebd22baeec7

include $(INCLUDE_DIR)/package.mk

define Package/lilo
  SECTION:=base
  CATEGORY:=Boot Loaders
  DEPENDS:=@TARGET_x86
  TITLE:=lilo
  URL:=ftp://metalab.unc.edu/pub/Linux/system/boot/lilo/
endef

define Package/lilo/conffiles
/etc/lilo.conf
endef

define Build/Compile
	$(MAKE) -C $(PKG_BUILD_DIR) alles
endef

define Package/lilo/install
	$(INSTALL_DIR) $(1)/sbin
	$(CP) $(PKG_BUILD_DIR)/lilo.static $(1)/sbin/lilo
	$(INSTALL_DIR) $(1)/etc
	$(CP) ./files/lilo.conf $(1)/etc/
	$(CP) ./files/boot.msg $(1)/etc/
endef

$(eval $(call BuildPackage,lilo))

$(foreach command, as86 ld86, \
  $(eval $(call RequireCommand,$(command), \
   $(PKG_NAME) requires $(command). \
  )) \
)
