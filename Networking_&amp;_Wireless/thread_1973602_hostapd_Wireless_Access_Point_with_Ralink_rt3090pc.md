---
title: "hostapd Wireless Access Point with Ralink rt3090pci  card"
date: 2012-05-05
forum: Networking &amp; Wireless
---

### Post by i_am_lost on 2012-05-05
I have most of the issues resolved with these awful cheap cards, but after 3 evenings on google I've decided to ask the community for assistance with the communication errors.

############################################
#Build rt3090  support for AP mode
Downloaded and installed compat-wireless-3.4-rc3-1.tar.bz2 source

############################################
# Hardware driver: compat-wireless-3.4-rc3-1.tar.bz2
  *-network
       description: Wireless interface
       product: RT3090 Wireless 802.11n 1T/1R PCIe
       vendor: Ralink corp.
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: wlan0
       version: 00
       serial: 48:02:2a:40:40:40
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless logical
       configuration: broadcast=yes driver=rt2800pci driverversion=3.2.0-20-generic firmware=0.34 ip=10.2.1.1 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:18 memory:d8200000-d820ffff

############################################      
#removed: network-manager  dnsmasq dnsmasq-base
#installed: dhcp3-server bind9
#problem: 802.11g clients refuse to connect and get a dhcp entry
       
############################################      
#On boot up:
>iw wlan0 info
Interface wlan0
        ifindex 4
        type managed
        wiphy 2

>ip route show
default via 192.168.1.1 dev eth0  metric 100
192.168.1.0/23 dev eth0  proto kernel  scope link  src 192.168.1.107


>cat /etc/dhcp/dhcpd.conf
subnet 10.2.0.0 netmask 255.255.0.0 {
        interface wlan0;
        option interface-mtu 1492;
        range 10.2.1.10 10.2.1.20;

        option domain-name-servers 10.2.1.1;
        option ip-forwarding off;
        max-lease-time 7200;
        default-lease-time 600;

        option broadcast-address 10.2.1.255;
        option subnet-mask 255.255.0.0;
        option routers 10.2.1.1;
}

>cat /etc/default/dhcp3-server
INTERFACES="wlan0"

>cat /etc/hostapd/hostapd.conf                                
interface=wlan0
driver=nl80211
wme_enabled=0
macaddr_acl=0
#auth_algs=0
ignore_broadcast_ssid=0
ctrl_interface_group=0
ssid=omgthissux
hw_mode=g
channel=6
 
############################################      
#On running the known hostapd  ap_ctl script :
# [http://ubuntuforums.org/showthread.php?t=1488953](http://ubuntuforums.org/showthread.php?t=1488953)

>iw wlan0 info
Interface wlan0
        ifindex 4
        type AP
        wiphy 3

>ip route show
default via 192.168.1.1 dev eth0  metric 100
10.0.0.0/8 dev wlan0  proto kernel  scope link  src 10.2.1.1
192.168.1.0/23 dev eth0  proto kernel  scope link  src 192.168.1.107


>netstat -rn
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
0.0.0.0         192.168.1.1      0.0.0.0         UG        0 0          0 eth0
10.0.0.0        0.0.0.0         255.0.0.0       U         0 0          0 wlan0
192.168.1.0      0.0.0.0         255.255.254.0   U         0 0          0 eth0


>cat /var/log/hostapd.log
ctrl_interface_group=0
nl80211: Add own interface ifindex 4
nl80211: New interface mon.wlan0 created: ifindex=6
nl80211: Add own interface ifindex 6
BSS count 1, BSSID mask 00:00:00:00:00:00 (0 bits)
nl80211: Added 802.11b mode based on 802.11g information
RATE[0] rate=10 flags=0x1
RATE[1] rate=20 flags=0x1
RATE[2] rate=55 flags=0x1
RATE[3] rate=110 flags=0x1
RATE[4] rate=60 flags=0x0
RATE[5] rate=90 flags=0x0
RATE[6] rate=120 flags=0x0
RATE[7] rate=180 flags=0x0
RATE[8] rate=240 flags=0x0
RATE[9] rate=360 flags=0x0
RATE[10] rate=480 flags=0x0
RATE[11] rate=540 flags=0x0
Completing interface initialization
Mode: IEEE 802.11g  Channel: 1  Frequency: 2412 MHz
Flushing old station entries
Deauthenticate all stations
wpa_driver_nl80211_set_key: ifindex=4 alg=0 addr=(nil) key_idx=0 set_tx=1 seq_len=0 key_len=0
wpa_driver_nl80211_set_key: ifindex=4 alg=0 addr=(nil) key_idx=1 set_tx=0 seq_len=0 key_len=0
wpa_driver_nl80211_set_key: ifindex=4 alg=0 addr=(nil) key_idx=2 set_tx=0 seq_len=0 key_len=0
wpa_driver_nl80211_set_key: ifindex=4 alg=0 addr=(nil) key_idx=3 set_tx=0 seq_len=0 key_len=0
Using interface wlan0 with hwaddr 48:02:2a:40:40:40 and ssid 'omgthissux'
nl80211: Set beacon (beacon_set=0)
wlan0: Setup of interface done.
nl80211: Event message available
nl80211: Scan aborted
RTM_NEWLINK: operstate=0 ifi_flags=0x1043 ([UP][RUNNING])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Unknown event 5
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Unknown event 5
RTM_NEWLINK: operstate=0 ifi_flags=0x1002 ()
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Unknown event 5
RTM_NEWLINK: operstate=0 ifi_flags=0x1002 ()
RTM_NEWLINK, IFLA_IFNAME: Interface 'mon.wlan0' added
Unknown event 5
RTM_NEWLINK: operstate=0 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'mon.wlan0' added
Unknown event 5
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Unknown event 5
RTM_NEWLINK: operstate=0 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Unknown event 5
mgmt::proberesp cb
mgmt::proberesp cb
mgmt::auth
authentication: STA=00:14:a5:d0:00:0d auth_alg=0 auth_transaction=1 status_code=0 wep=0
  New STA
wlan0: STA 00:14:a5:d0:00:0d IEEE 802.11: authentication OK (open system)
wlan0: STA 00:14:a5:d0:00:0d MLME: MLME-AUTHENTICATE.indication(00:14:a5:d0:00:0d, OPEN_SYSTEM)
wlan0: STA 00:14:a5:d0:00:0d MLME: MLME-DELETEKEYS.request(00:14:a5:d0:00:0d)
authentication reply: STA=00:14:a5:d0:00:0d auth_alg=0 auth_transaction=2 resp=0 (IE len=0)
mgmt::auth cb
wlan0: STA 00:14:a5:d0:00:0d IEEE 802.11: did not acknowledge authentication response
mgmt::assoc_req
association request: STA=00:14:a5:d0:00:0d capab_info=0x421 listen_interval=10
  new AID 1
wlan0: STA 00:14:a5:d0:00:0d IEEE 802.11: association OK (aid 1)
mgmt::assoc_resp cb
wlan0: STA 00:14:a5:d0:00:0d IEEE 802.11: did not acknowledge association response
Data/PS-poll frame from not associated STA 00:14:a5:d0:00:0d
unknown mgmt cb frame subtype 10
mgmt::proberesp cb
mgmt::proberesp cb


a.k.a.  no Wifi for you...:lolflag:

---

### Post by i_am_lost on 2012-05-06
The obscure issue is related to the cards driver to handle the Acks correctly.  This is a very old problem with these cards, and the only practical option is patching and building hostapd from source. 

Find and comment out these two Ack checks, and build after editing hostap/.config build 
parameters.  This will allow the clients to connect, and not flood the log files with a known problem.

/*
     if (!ok) {
       hostapd_logger(hapd, mgmt->da, HOSTAPD_MODULE_IEEE80211,
                      HOSTAPD_LEVEL_NOTICE,
                      "did not acknowledge authentication response");
       return;
    }
*/

/*
    if (!ok) {
       hostapd_logger(hapd, mgmt->da, HOSTAPD_MODULE_IEEE80211,
                      HOSTAPD_LEVEL_DEBUG,
                      "did not acknowledge association response");
       return;
    }
*/

( mg 2008.12.14 , "http://eznemegy.blog.hu/2008/12/14/using_rt2x00_wireless_driver_with_hostapd/fullcommentlist/1" ) 

These PCIe cards work, but may stop working if additional USB wireless cards are plugged in once. You may have to remove reference to other wlan2 cards in:
/etc/udev/rules.d/70-persistent-net.rules

):P

---

