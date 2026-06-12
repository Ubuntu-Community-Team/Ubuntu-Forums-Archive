---
title: "Hp laptop doesn't wifi"
date: 2019-01-13
forum: MINT
---

### Post by tackskull on 2019-01-13
Hi there, I have formatted my laptop and now after boot the first time I am not able to get the internet from wifi, only from ethernet cable.

Here some informations

```
tackskull@tackskull-HP-250-G4-Notebook-PC:~$ uname -r; grep [[:alnum:]] /sys/module/rtl8723be/parameters/*
4.15.0-43-generic
/sys/module/rtl8723be/parameters/ant_sel:0
/sys/module/rtl8723be/parameters/aspm:1
/sys/module/rtl8723be/parameters/debug_level:0
/sys/module/rtl8723be/parameters/debug_mask:0
/sys/module/rtl8723be/parameters/disable_watchdog:N
/sys/module/rtl8723be/parameters/fwlps:Y
/sys/module/rtl8723be/parameters/ips:Y
/sys/module/rtl8723be/parameters/msi:N
/sys/module/rtl8723be/parameters/swenc:N
/sys/module/rtl8723be/parameters/swlps:N

```

```
tackskull@tackskull-HP-250-G4-Notebook-PC:~$ dpkg -l | grep linux-image-generic
ii  linux-image-generic                        4.15.0.43.45                                amd64        Generic Linux kernel image

```

---

### Post by praseodym on 2019-01-13
Please run the wireless script from the sticky thread and show the output

---

### Post by tackskull on 2019-01-13
did it


```

########## wireless info START ##########

Report from: 13 Jan 2019 22:10 CET +0100

Booted last: 13 Jan 2019 00:00 CET +0100

Script from: 22 Oct 2018 03:34 UTC +0000

##### release ###########################

Distributor ID:    LinuxMint
Description:    Linux Mint 19.1 Tessa
Release:    19.1
Codename:    tessa

##### kernel ############################

Linux 4.15.0-43-generic #46-Ubuntu SMP Thu Dec 6 14:45:28 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=1

##### desktop ###########################

MATE

##### lspci #############################

02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8723BE PCIe Wireless Network Adapter [10ec:b723]
    Subsystem: Hewlett-Packard Company RTL8723BE PCIe Wireless Network Adapter [103c:804c]
    Kernel driver in use: rtl8723be

03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [10ec:8136] (rev 07)
    Subsystem: Hewlett-Packard Company RTL810xE PCI Express Fast Ethernet controller [103c:80c5]
    Kernel driver in use: r8169

##### lsusb #############################

Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 005: ID 0bda:b006 Realtek Semiconductor Corp. 
Bus 001 Device 004: ID 1bcf:0005 Sunplus Innovation Technology Inc. Optical Mouse
Bus 001 Device 003: ID 1a40:0101 Terminus Technology Inc. Hub
Bus 001 Device 002: ID 0c45:651b Microdia 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

##### secure boot #######################

SecureBoot disabled

##### lsmod #############################

rtl8723be              98304  0
btcoexist             135168  1 rtl8723be
rtl8723_common         24576  1 rtl8723be
rtl_pci                32768  1 rtl8723be
rtlwifi                77824  4 rtl_pci,rtl8723be,btcoexist,rtl8723_common
mac80211              778240  3 rtl_pci,rtl8723be,rtlwifi
cfg80211              622592  2 rtlwifi,mac80211
wmi_bmof               16384  0
hp_wmi                 16384  0
sparse_keymap          16384  1 hp_wmi
wmi                    24576  2 hp_wmi,wmi_bmof

##### interfaces ########################

[/etc/network/interfaces]
auto lo
iface lo inet loopback

##### ifconfig ##########################

1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback <MAC address> brd <MAC address>
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: enp3s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    link/ether <MAC 'enp3s0' [IF1]> brd <MAC address>
    inet 192.168.1.19/24 brd 192.168.1.255 scope global dynamic noprefixroute enp3s0
       valid_lft 19914sec preferred_lft 19914sec
    inet6 fe80::76e0:d41d:ebda:84c4/64 scope link noprefixroute 
       valid_lft forever preferred_lft forever
3: wlp2s0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc mq state DOWN group default qlen 1000
    link/ether <MAC 'wlp2s0' [IF2]> brd <MAC address>

##### iwconfig ##########################

enp3s0    no wireless extensions.

lo        no wireless extensions.

wlp2s0    IEEE 802.11  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:on
          

##### route #############################

default via 192.168.1.1 dev enp3s0 proto dhcp metric 100 
192.168.1.0/24 dev enp3s0 proto kernel scope link src 192.168.1.19 metric 100 

##### resolv.conf #######################

[777 root '/etc/resolv.conf' -> '../run/systemd/resolve/stub-resolv.conf']

nameserver 127.0.0.53
search homenet.telecomitalia.it

##### network managers ##################

Installed:

    NetworkManager

Running:

root       761     1  0 21:39 ?        00:00:01 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         enp3s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL810xE PCI Express Fast Ethernet controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               --
GENERAL.HWADDR:                         <MAC 'enp3s0' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.3/0000:03:00.0/net/enp3s0
GENERAL.IP-IFACE:                       enp3s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Wired connection 1
GENERAL.CON-UUID:                       1e4bc671-13ec-3b35-8960-5f1c576e0a64
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/1
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     100 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
CAPABILITIES.SRIOV:                     no
WIRED-PROPERTIES.CARRIER:               on
IP4.ADDRESS[1]:                         192.168.1.19/24
IP4.GATEWAY:                            192.168.1.1
IP4.ROUTE[1]:                           dst = 0.0.0.0/0, nh = 192.168.1.1, mt = 100
IP4.ROUTE[2]:                           dst = 192.168.1.0/24, nh = 0.0.0.0, mt = 100
IP4.DNS[1]:                             192.168.1.1
IP4.DOMAIN[1]:                          homenet.telecomitalia.it
DHCP4.OPTION[1]:                        requested_host_name = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_time_offset = 1
DHCP4.OPTION[4]:                        requested_domain_name = 1
DHCP4.OPTION[5]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[6]:                        requested_broadcast_address = 1
DHCP4.OPTION[7]:                        broadcast_address = 192.168.1.255
DHCP4.OPTION[8]:                        requested_netbios_scope = 1
DHCP4.OPTION[9]:                        domain_name = homenet.telecomitalia.it
DHCP4.OPTION[10]:                       next_server = 0.0.0.0
DHCP4.OPTION[11]:                       expiry = 1547433731
DHCP4.OPTION[12]:                       dhcp_message_type = 5
DHCP4.OPTION[13]:                       requested_subnet_mask = 1
DHCP4.OPTION[14]:                       dhcp_lease_time = 21600
DHCP4.OPTION[15]:                       ip_address = 192.168.1.19
DHCP4.OPTION[16]:                       routers = 192.168.1.1
DHCP4.OPTION[17]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[18]:                       requested_domain_name_servers = 1
DHCP4.OPTION[19]:                       requested_wpad = 1
DHCP4.OPTION[20]:                       domain_name_servers = 192.168.1.1 192.168.1.1
DHCP4.OPTION[21]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[22]:                       requested_ntp_servers = 1
DHCP4.OPTION[23]:                       requested_routers = 1
DHCP4.OPTION[24]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[25]:                       requested_interface_mtu = 1
DHCP4.OPTION[26]:                       network_number = 192.168.1.0
DHCP4.OPTION[27]:                       dhcp_server_identifier = 192.168.1.1
DHCP4.OPTION[28]:                       requested_static_routes = 1
IP6.ADDRESS[1]:                         fe80::76e0:d41d:ebda:84c4/64
IP6.GATEWAY:                            --
IP6.ROUTE[1]:                           dst = ff00::/8, nh = ::, mt = 256, table=255
IP6.ROUTE[2]:                           dst = fe80::/64, nh = ::, mt = 256
IP6.ROUTE[3]:                           dst = fe80::/64, nh = ::, mt = 100
IP6.DNS[1]:                             fe80::1
DHCP6.OPTION[1]:                        dhcp6_client_id = 0:4:a9:a0:76:2d:c9:3d:c2:14:b0:47:6e:15:83:d7:52:67
DHCP6.OPTION[2]:                        requested_dhcp6_name_servers = 1
DHCP6.OPTION[3]:                        dhcp6_name_servers = fe80::1
DHCP6.OPTION[4]:                        requested_dhcp6_domain_search = 1
DHCP6.OPTION[5]:                        dhcp6_solmax_rt = 3600
DHCP6.OPTION[6]:                        requested_dhcp6_client_id = 1
DHCP6.OPTION[7]:                        dhcp6_unicast = fe80::1
DHCP6.OPTION[8]:                        dhcp6_server_id = 0:1:0:1:18:74:e4:99:78:81:2:99:56:68
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{1}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   1e4bc671-13ec-3b35-8960-5f1c576e0a64 | Wired connection 1

GENERAL.DEVICE:                         wlp2s0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8723BE PCIe Wireless Network Adapter
GENERAL.DRIVER:                         rtl8723be
GENERAL.DRIVER-VERSION:                 4.15.0-43-generic
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         <MAC 'wlp2s0' [IF2]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          30 (disconnected)
GENERAL.REASON:                         42 (The supplicant is now available)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.2/0000:02:00.0/net/wlp2s0
GENERAL.IP-IFACE:                       --
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     --
GENERAL.CON-UUID:                       --
GENERAL.CON-PATH:                       --
GENERAL.METERED:                        unknown
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               no
CAPABILITIES.SRIOV:                     no
WIFI-PROPERTIES.WEP:                    yes
WIFI-PROPERTIES.WPA:                    yes
WIFI-PROPERTIES.WPA2:                   yes
WIFI-PROPERTIES.TKIP:                   yes
WIFI-PROPERTIES.CCMP:                   yes
WIFI-PROPERTIES.AP:                     yes
WIFI-PROPERTIES.ADHOC:                  yes
WIFI-PROPERTIES.2GHZ:                   yes
WIFI-PROPERTIES.5GHZ:                   no
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: --

SSID  BSSID  MODE  CHAN  FREQ  RATE  SIGNAL  BARS  SECURITY  ACTIVE  IN-USE 

##### NetworkManager.state ##############

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true

##### NetworkManager config #############

[[/etc/NetworkManager/conf.d/default-wifi-powersave-on.conf]]
[connection]
wifi.powersave = 3

[[/etc/NetworkManager/NetworkManager.conf]]
[main]
plugins=ifupdown,keyfile
[ifupdown]
managed=false
[device]
wifi.scan-rand-mac-address=no

[[/usr/lib/NetworkManager/conf.d/10-dns-resolved.conf]]
[main]
dns=systemd-resolved

[[/usr/lib/NetworkManager/conf.d/10-globally-managed-devices.conf]]
[keyfile]
unmanaged-devices=*,except:type:wifi,except:type:wwan

[[/usr/lib/NetworkManager/conf.d/20-connectivity-ubuntu.conf]]
[connectivity]
uri=http://connectivity-check.ubuntu.com/

[[/usr/lib/NetworkManager/conf.d/no-mac-addr-change.conf]]
[device-mac-addr-change-wifi]
match-device=driver:rtl8723bs,driver:rtl8189es,driver:r8188eu,driver:8188eu,driver:eagle_sdio,driver:wl
wifi.scan-rand-mac-address=no
wifi.cloned-mac-address=preserve
ethernet.cloned-mac-address=preserve

##### NetworkManager profiles ###########

##### Netplan config ####################

[/etc/netplan/1-network-manager-all.yaml]
network:
  version: 2
  renderer: NetworkManager

##### iw reg get ########################

Region: Europe/Rome (based on set time zone)

global
country 00: DFS-UNSET
    (2402 - 2472 @ 40), (N/A, 20), (N/A)
    (2457 - 2482 @ 20), (N/A, 20), (N/A), AUTO-BW, PASSIVE-SCAN
    (2474 - 2494 @ 20), (N/A, 20), (N/A), NO-OFDM, PASSIVE-SCAN
    (5170 - 5250 @ 80), (N/A, 20), (N/A), AUTO-BW, PASSIVE-SCAN
    (5250 - 5330 @ 80), (N/A, 20), (0 ms), DFS, AUTO-BW, PASSIVE-SCAN
    (5490 - 5730 @ 160), (N/A, 20), (0 ms), DFS, PASSIVE-SCAN
    (5735 - 5835 @ 80), (N/A, 20), (N/A), PASSIVE-SCAN
    (57240 - 63720 @ 2160), (N/A, 0), (N/A)

##### iwlist channels ###################

enp3s0    no frequency information.

lo        no frequency information.

wlp2s0    13 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz

##### iwlist scan #######################

enp3s0    Interface doesn't support scanning.

lo        Interface doesn't support scanning.

wlp2s0    No scan results

##### module infos ######################

[rtl8723be]
filename:       /lib/modules/4.15.0-43-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtl8723be/rtl8723be.ko
firmware:       rtlwifi/rtl8723befw_36.bin
firmware:       rtlwifi/rtl8723befw.bin
description:    Realtek 8723BE 802.11n PCI wireless
license:        GPL
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         PageHe    <page_he@realsil.com.cn>
srcversion:     4460AA5584590927164B1F2
depends:        rtlwifi,rtl8723-common,rtl_pci,btcoexist,mac80211
retpoline:      Y
intree:         Y
name:           rtl8723be
vermagic:       4.15.0-43-generic SMP mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4
parm:           swenc:Set to 1 for software crypto (default 0)
 (bool)
parm:           ips:Set to 0 to not use link power save (default 1)
 (bool)
parm:           swlps:Set to 1 to use SW control power save (default 0)
 (bool)
parm:           fwlps:Set to 1 to use FW control power save (default 1)
 (bool)
parm:           msi:Set to 1 to use MSI interrupts mode (default 0)
 (bool)
parm:           aspm:Set to 1 to enable ASPM (default 1)
 (int)
parm:           debug_level:Set debug level (0-5) (default 0) (int)
parm:           debug_mask:Set debug mask (default 0) (ullong)
parm:           disable_watchdog:Set to 1 to disable the watchdog (default 0)
 (bool)
parm:           ant_sel:Set to 1 or 2 to force antenna number (default 0)
 (int)

[rtl8723_common]
filename:       /lib/modules/4.15.0-43-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtl8723com/rtl8723-common.ko
description:    Realtek RTL8723AE/RTL8723BE 802.11n PCI wireless common routines
license:        GPL
author:         Larry Finger    <Larry.Finger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
srcversion:     90DB9C652E26F4135F339B8
depends:        rtlwifi
retpoline:      Y
intree:         Y
name:           rtl8723_common
vermagic:       4.15.0-43-generic SMP mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4

[rtl_pci]
filename:       /lib/modules/4.15.0-43-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtl_pci.ko
description:    PCI basic driver for rtlwifi
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     D883A6C5A490FBE0CDF1B6A
depends:        mac80211,rtlwifi
retpoline:      Y
intree:         Y
name:           rtl_pci
vermagic:       4.15.0-43-generic SMP mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4

[rtlwifi]
filename:       /lib/modules/4.15.0-43-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtlwifi.ko
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     12BDF0F9FFC2ACFD3465C5A
depends:        mac80211,cfg80211
retpoline:      Y
intree:         Y
name:           rtlwifi
vermagic:       4.15.0-43-generic SMP mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4

[mac80211]
filename:       /lib/modules/4.15.0-43-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     10B87D6D65DDD085D1326C9
depends:        cfg80211
retpoline:      Y
intree:         Y
name:           mac80211
vermagic:       4.15.0-43-generic SMP mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/4.15.0-43-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     62FD05DCC5AEEA290640C3D
depends:        
retpoline:      Y
intree:         Y
name:           cfg80211
vermagic:       4.15.0-43-generic SMP mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4
parm:           bss_entries_limit:limit to number of scan BSS entries (per wiphy, default 1000) (int)
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[rtl8723be]
ant_sel: 0
aspm: 1
debug_level: 0
debug_mask: 0
disable_watchdog: N
fwlps: Y
ips: Y
msi: N
swenc: N
swlps: N

[mac80211]
beacon_loss_count: 7
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
minstrel_vht_only: Y
probe_wait_ms: 500

[cfg80211]
bss_entries_limit: 1000
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00

##### /etc/modules ######################

##### modprobe options ##################

[/etc/modprobe.d/amd64-microcode-blacklist.conf]
blacklist microcode

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/blacklist.conf]
blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist prism54
blacklist bcm43xx
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac

[/etc/modprobe.d/blacklist-rare-network.conf]
alias net-pf-3 off
alias net-pf-6 off
alias net-pf-9 off
alias net-pf-11 off
alias net-pf-12 off
alias net-pf-19 off
alias net-pf-21 off
alias net-pf-36 off

[/etc/modprobe.d/intel-microcode-blacklist.conf]
blacklist microcode

[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211

##### rc.local ##########################

grep: /etc/rc.local: No such file or directory

##### pm-utils ##########################

##### udev rules ########################

##### dmesg #############################

[   54.357132] rtl8723be: Using firmware rtlwifi/rtl8723befw_36.bin
[   54.660964] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[   54.661473] rtlwifi: rtlwifi: wireless switch is on
[   54.891925] rtl8723be 0000:02:00.0 wlp2s0: renamed from wlan0
[   55.846469] Bluetooth: hci0: rtl: examining hci_ver=06 hci_rev=000b lmp_ver=06 lmp_subver=8723
[   55.846474] Bluetooth: hci0: rtl: loading rtl_bt/rtl8723b_config.bin
[   55.886919] bluetooth hci0: Direct firmware load for rtl_bt/rtl8723b_config.bin failed with error -2
[   55.886927] Bluetooth: hci0: rtl: loading rtl_bt/rtl8723b_fw.bin
[   69.493933] IPv6: ADDRCONF(NETDEV_UP): enp3s0: link is not ready
[   69.772246] r8169 0000:03:00.0 enp3s0: link down
[   69.772718] IPv6: ADDRCONF(NETDEV_UP): enp3s0: link is not ready
[   69.910814] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready (repeated 3 times)
[  217.930957] r8169 0000:03:00.0 enp3s0: link up
[  217.930994] IPv6: ADDRCONF(NETDEV_CHANGE): enp3s0: link becomes ready

########## wireless info END ############

```

---

### Post by jeremy31 on 2019-01-13
Moved to Mint

---

### Post by tackskull on 2019-01-14
> **praseodym said:**
> Please run the wireless script from the sticky thread and show the output

What now?

---

### Post by tackskull on 2019-01-18
Are you guys still there?

---

