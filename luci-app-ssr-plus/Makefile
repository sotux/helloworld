include $(TOPDIR)/rules.mk

PKG_NAME:=luci-app-ssr-plus
PKG_VERSION:=183
PKG_RELEASE:=8

define Package/$(PKG_NAME)/conffiles
/etc/config/shadowsocksr
/etc/ssrplus/
endef

define Package/$(PKG_NAME)/config
config PACKAGE_$(PKG_NAME)_INCLUDE_Shadowsocks
	bool "Include Shadowsocks"
	default y

config PACKAGE_$(PKG_NAME)_INCLUDE_Xray_plugin
	bool "Include Xray Plugin"
	default y

config PACKAGE_$(PKG_NAME)_INCLUDE_Xray
	bool "Include Xray (V2RAY/Trojan-GO implemented)"
	default n

config PACKAGE_$(PKG_NAME)_INCLUDE_Trojan
	bool "Include Trojan (OpenSSL)"
	default y

config PACKAGE_$(PKG_NAME)_INCLUDE_Redsocks2
	bool "Include Redsocks2"
	default n

config PACKAGE_$(PKG_NAME)_INCLUDE_NaiveProxy
	bool "Include NaiveProxy"
	depends on !(arc||armeb||mips||mips64||powerpc)
	default n

config PACKAGE_$(PKG_NAME)_INCLUDE_Kcptun
	bool "Include Kcptun"
	default n

config PACKAGE_$(PKG_NAME)_INCLUDE_ShadowsocksR_Server
	bool "Include ShadowsocksR Server"
	default n
endef

LUCI_TITLE:=SS/SSR/V2Ray/Trojan/NaiveProxy/Socks5/Tun LuCI interface
LUCI_PKGARCH:=all
LUCI_DEPENDS:=+shadowsocksr-libev-ssr-check +ipset +ip-full +iptables-mod-tproxy +dnsmasq-full +coreutils +coreutils-base64 +pdnsd-alt +wget-ssl +lua +libuci-lua \
	+microsocks +dns2socks +tcping +resolveip \
	+PACKAGE_$(PKG_NAME)_INCLUDE_Shadowsocks:shadowsocks-libev-alt \
	+PACKAGE_$(PKG_NAME)_INCLUDE_Shadowsocks:simple-obfs \
	+PACKAGE_$(PKG_NAME)_INCLUDE_Xray_plugin:xray-plugin \
	+PACKAGE_$(PKG_NAME)_INCLUDE_Xray:xray-core-alt \
	+PACKAGE_$(PKG_NAME)_INCLUDE_Trojan:trojan \
	+PACKAGE_$(PKG_NAME)_INCLUDE_Trojan:ipt2socks \
	+PACKAGE_$(PKG_NAME)_INCLUDE_NaiveProxy:naiveproxy \
	+PACKAGE_$(PKG_NAME)_INCLUDE_Redsocks2:redsocks2 \
	+PACKAGE_$(PKG_NAME)_INCLUDE_Kcptun:kcptun-client \
	+PACKAGE_$(PKG_NAME)_INCLUDE_ShadowsocksR_Server:shadowsocksr-libev-server

include $(TOPDIR)/feeds/luci/luci.mk

# call BuildPackage - OpenWrt buildroot signature
