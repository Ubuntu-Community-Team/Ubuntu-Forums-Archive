---
title: "hostapd and madwifi drivers"
date: 2009-01-18
forum: Networking &amp; Wireless
---

### Post by zanophol on 2009-01-18
I have compiled all sorts of different builds of hostapd (most notably the latest stable build 0.5.11 and even the dev build 0.6.7) while trying to compile in madwifi support. I have tried various builds of the madwifi drivers. No matter what combination I try, hostapd always reports that it "Could not connect to kernel driver." This is becoming infuriating. Does anyone have hostapd running a WPA/WPA2 access point?

My AP runs just fine through iwconfig (it is an atheros card) without encryption enabled.

My hostapd.conf:
interface=ath0
bridge=br0
driver=madwifi
logger_syslog=-1
logger_syslog_level=2
logger_stdout=-1
logger_stdout_level=2
debug=4
hw_mode=g
dump_file=/tmp/hostapd.dump
ctrl_interface=/var/run/hostapd
ctrl_interface_group=0
ssid=test
#macaddr_acl=1
#accept_mac_file=/etc/hostapd/accept
auth_algs=3
eapol_key_index_workaround=0
eap_server=0
wpa=3
wpa_psk_file=/etc/hostapd/wpa_psk
wpa_key_mgmt=WPA-PSK
wpa_pairwise=CCMP

sudo hostapd -dd -K -t /etc/hostapd/hostapd.conf
Configuration file: /etc/hostapd/hostapd.conf
1232295145.232803: ctrl_interface_group=0
Configure bridge br0 for EAPOL traffic.
1232295145.233670: madwifi_set_iface_flags: dev_up=0
madwifi_set_privacy: enabled=0
BSS count 1, BSSID mask ff:ff:ff:ff:ff:ff (0 bits)
1232295145.234091: SIOCGIWRANGE: WE(compiled)=22 WE(source)=13 enc_capa=0xf
1232295145.234217: ath0: IEEE 802.11 Fetching hardware channel/rate support not supported.
1232295145.234294: Flushing old station entries
madwifi_sta_deauth: addr=ff:ff:ff:ff:ff:ff reason_code=3
ioctl[IEEE80211_IOCTL_SETMLME]: Invalid argument
1232295145.234769: madwifi_sta_deauth: Failed to deauth STA (addr ff:ff:ff:ff:ff:ff reason 3)
**Could not connect to kernel driver.**
1232295145.234896: Deauthenticate all stations
madwifi_set_privacy: enabled=0
madwifi_del_key: addr=00:00:00:00:00:00 key_idx=0
madwifi_del_key: addr=00:00:00:00:00:00 key_idx=1
madwifi_del_key: addr=00:00:00:00:00:00 key_idx=2
madwifi_del_key: addr=00:00:00:00:00:00 key_idx=3
Using interface ath0 with hwaddr 00:0d:88:57:fb:77 and ssid 'test'
madwifi_set_ieee8021x: enabled=1
madwifi_configure_wpa: group key cipher=3
madwifi_configure_wpa: pairwise key ciphers=0x8
madwifi_configure_wpa: key management algorithms=0x2
madwifi_configure_wpa: rsn capabilities=0x0
madwifi_configure_wpa: enable WPA=0x3
ioctl[IEEE80211_IOCTL_SETPARAM]: Invalid argument
1232295145.287452: set80211param: Failed to set parameter (op 3 arg 5)
1232295145.287574: ath0: DRIVER Error enabling WPA/802.1X!
IEEE 802.1X initialization failed.
1232295145.288329: ath0: Unable to setup interface.
l2_packet_receive - recvfrom: Network is down
1232295145.288757: Flushing old station entries
madwifi_sta_deauth: addr=ff:ff:ff:ff:ff:ff reason_code=3
ioctl[IEEE80211_IOCTL_SETMLME]: Invalid argument
1232295145.289111: madwifi_sta_deauth: Failed to deauth STA (addr ff:ff:ff:ff:ff:ff reason 3)
**Could not connect to kernel driver.**
1232295145.289296: Deauthenticate all stations
rmdir[ctrl_interface]: No such file or directory
madwifi_set_ieee8021x: enabled=0
1232295145.289682: madwifi_set_iface_flags: dev_up=0

My hostapd .config file:
# Example hostapd build time configuration
#
# This file lists the configuration options that are used when building the
# hostapd binary. All lines starting with # are ignored. Configuration option
# lines must be commented out complete, if they are not to be included, i.e.,
# just setting VARIABLE=n is not disabling that variable.
#
# This file is included in Makefile, so variables like CFLAGS and LIBS can also
# be modified from here. In most cass, these lines should use += in order not
# to override previous values of the variables.

# Driver interface for Host AP driver
CONFIG_DRIVER_HOSTAP=y

# Driver interface for wired authenticator
#CONFIG_DRIVER_WIRED=y

# Driver interface for madwifi driver
CONFIG_DRIVER_MADWIFI=y
CFLAGS += -I /home/zanophol/dloads/new/madwifi-ng

# Driver interface for Prism54 driver
#CONFIG_DRIVER_PRISM54=y

# Driver interface for drivers using Devicescape IEEE 802.11 stack
#CONFIG_DRIVER_DEVICESCAPE=y
# Currently, driver_devicescape.c build requires some additional parameters
# to be able to include some of the kernel header files. Following lines can
# be used to set these (WIRELESS_DEV must point to the root directory of the
# wireless-dev.git tree).
#WIRELESS_DEV=/usr/src/wireless-dev
#CFLAGS += -I$(WIRELESS_DEV)/net/mac80211

# Driver interface for FreeBSD net80211 layer (e.g., Atheros driver)
#CONFIG_DRIVER_BSD=y
#CFLAGS += -I/usr/local/include
#LIBS += -L/usr/local/lib

# IEEE 802.11F/IAPP
CONFIG_IAPP=y

# WPA2/IEEE 802.11i RSN pre-authentication
CONFIG_RSN_PREAUTH=y

# PeerKey handshake for Station to Station Link (IEEE 802.11e DLS)
CONFIG_PEERKEY=y

# IEEE 802.11w (management frame protection)
# This version is an experimental implementation based on IEEE 802.11w/D1.0
# draft and is subject to change since the standard has not yet been finalized.
# Driver support is also needed for IEEE 802.11w.
#CONFIG_IEEE80211W=y

# Integrated EAP server
CONFIG_EAP=y

# EAP-MD5 for the integrated EAP server
CONFIG_EAP_MD5=y

# EAP-TLS for the integrated EAP server
CONFIG_EAP_TLS=y

# EAP-MSCHAPv2 for the integrated EAP server
CONFIG_EAP_MSCHAPV2=y

# EAP-PEAP for the integrated EAP server
CONFIG_EAP_PEAP=y

# EAP-GTC for the integrated EAP server
CONFIG_EAP_GTC=y

# EAP-TTLS for the integrated EAP server
CONFIG_EAP_TTLS=y

# EAP-SIM for the integrated EAP server
#CONFIG_EAP_SIM=y

# EAP-AKA for the integrated EAP server
#CONFIG_EAP_AKA=y

# EAP-PAX for the integrated EAP server
#CONFIG_EAP_PAX=y

# EAP-PSK for the integrated EAP server (this is _not_ needed for WPA-PSK)
#CONFIG_EAP_PSK=y

# EAP-SAKE for the integrated EAP server
#CONFIG_EAP_SAKE=y

# EAP-GPSK for the integrated EAP server
#CONFIG_EAP_GPSK=y
# Include support for optional SHA256 cipher suite in EAP-GPSK
#CONFIG_EAP_GPSK_SHA256=y

# PKCS#12 (PFX) support (used to read private key and certificate file from
# a file that usually has extension .p12 or .pfx)
CONFIG_PKCS12=y

# RADIUS authentication server. This provides access to the integrated EAP
# server from external hosts using RADIUS.
#CONFIG_RADIUS_SERVER=y

# Build IPv6 support for RADIUS operations
CONFIG_IPV6=y

---

