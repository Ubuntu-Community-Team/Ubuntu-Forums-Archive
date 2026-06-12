---
title: "Broadcom/Ubuntu 10.04/Gateway MX6445 - Unable to connect to wifi router"
date: 2010-06-26
forum: Networking &amp; Wireless
---

### Post by pipher on 2010-06-26
I recently installed Ubuntu 10.04 on a partition on my laptop.  I have spent hours scouring support and following tutorials trying to configure my wifi connection, but I cannot connect to the router no matter what I try.

I know the adapter can see the router from using iwscan, but I am unable to connect.  I am using ndiswrapper with windows drivers, and I believe it is installed and recognized (see details below).  I got the windows driver files from the following website:

[http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=Broadcom_BCM4318](http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=Broadcom_BCM4318)

I have checked both the Ubuntu wireless card compatibility list and the ndiswrapper compatibility list and my Broadcom BCM4318 card is included in both.

See the section below for output from all the relevant commands and files that I have encountered so far.  If any more information is needed let me know and I will retrieve it ASAP.

wpa_supplicant I believe is installed, but I'm not sure if it is correctly configured or working properly (or even necessary for that matter).

Any suggestions or insight into what I might be missing or doing wrong would be much appreciated.  I am becoming exceedingly frustrated with this, and I would hate to just give up on it.

==========================================================

COMMAND:
ndiswrapper -l
OUTPUT:
bcmwl5a : driver installed
device (14E4:4318) present (alternate driver: ssb)

==========================================================


COMMAND:
lshw -c network
OUTPUT:
 *-network
      description: Ethernet interface
      product: 88E8036 PCI-E Fast Ethernet Controller
      vendor: Marvell Technology Group Ltd.
      physical id: 0
      bus info: pci@0000:03:00.0
      logical name: eth0
      version: 10
      serial: 00:e0:b8:b5:dc:df
      width: 64 bits
      clock: 33MHz
      capabilities: bus_master cap_list ethernet physical
      configuration: broadcast=yes driver=sky2 driverversion=1.25 firmware=N/A latency=0 multicast=yes
      resources: irq:18 memory:d0200000-d0203fff ioport:a000(size=256)
 *-network
      description: Wireless interface
      product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
      vendor: Broadcom Corporation
      physical id: 2
      bus info: pci@0000:05:02.0
      logical name: wlan0
      version: 02
      serial: 00:c0:a8:bc:5e:3f
      width: 32 bits
      clock: 33MHz
      capabilities: bus_master ethernet physical wireless
      configuration: broadcast=yes driver=ndiswrapper+bcmwl5a driverversion=1.55+Broadcom,12/22/2004, 3.100. latency=64 multicast=yes wireless=IEEE 802.11g
      resources: irq:22 memory:d0304000-d0305fff

NOTES:
Before I blacklisted b43-pci-bridge, it was what showed up as the driver.  Once I blacklisted it, the command output changed to what is shown above.  

Also noteworthy is that as soon as I blacklisted that driver and rebooted, the network icon on my desktop bar disappeared.  Also, the "System > Administration > Networking" program disappeared from the menu.  When I try to run nm-applet I get an error message:
"An instance of nm-applet is already running."
I get this straight off a boot without manually starting any programs, and no visible applet is on the screen at this time.

The only way that I can get into the network settings now is "System > Administration > Windows Wireless Drivers" and click on "Configure Network."  Currently I do not have anything under the wireless tab, although I have tried adding a connection with the SSID, BSSID (Access point address), and "WPA & WPA2 Personal" security as well as the password under the "Security" tab.  After doing this and hitting apply, I still am unable to connect.

==========================================================
COMMAND:
lspci
OUTPUT (for card):
05:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN controller (rev 02)

==========================================================


COMMAND:
dmesg | grep -e ndis -e wlan
OUTPUT:
[   16.339239] ndiswrapper version 1.55 loaded (smp=yes, preempt=no)
[   17.515026] ndiswrapper: driver bcmwl5a (Broadcom,12/22/2004, 3.100.46.0) loaded
[   17.516180] ndiswrapper 0000:05:02.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   17.529553] ndiswrapper: using IRQ 22
[   18.069010] wlan0: ethernet device 00:c0:a8:bc:5e:3f using NDIS driver: bcmwl5a, version: 0x3642e00, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 14E4:4318.5.conf
[   18.069060] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[   18.069136] usbcore: registered new interface driver ndiswrapper
[   18.194567] ADDRCONF(NETDEV_UP): wlan0: link is not ready

NOTES:

I was reading some How-to which said this is the correct dmesg output for ndiswrapper.  I'm not sure though..

==========================================================


COMMAND:
sudo dhclient
OUTPUT:
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)

Listening on LPF/eth0/00:e0:b8:b5:dc:df
Sending on   LPF/eth0/00:e0:b8:b5:dc:df
Listening on LPF/wlan0/00:c0:a8:bc:5e:3f
Sending on   LPF/wlan0/00:c0:a8:bc:5e:3f
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 19
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 21
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 18
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 20
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 1
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

NOTES:

I know this is not good^^, but I have no idea how to fix it.

==========================================================


COMMAND:
iwconfig
OUTPUT:
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
         Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
         Bit Rate:54 Mb/s   Tx-Power:25 dBm   
         RTS thr:2347 B   Fragment thr:2346 B   
         Power Management:off
         Link Quality:0  Signal level:0  Noise level:0
         Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
         Tx excessive retries:0  Invalid misc:0   Missed beacon:0

NOTES:

I have tried modifying the access point and essid using iwconfig commands but it doesn't seem to ever do anything (although I don't get any error messages either.. but nothing changes when i generate the output above again)

I can see that some of the settings above are inconsistent with the router I am trying to connect to (see further down), but I can't figure out how to modify them!

==========================================================



COMMAND:
nm-tool
OUTPUT:
NetworkManager Tool

State: connected

- Device: eth0 -----------------------------------------------------------------
 Type:              Wired
 Driver:            sky2
 State:             unavailable
 Default:           no
 HW Address:        00:E0:B8:B5:DC:DF

 Capabilities:
   Carrier Detect:  yes

 Wired Properties
   Carrier:         off


- Device: wlan0 ----------------------------------------------------------------
 Type:              802.11 WiFi
 Driver:            ndiswrapper
 State:             unmanaged
 Default:           no
 HW Address:        00:C0:A8:BC:5E:3F

 Capabilities:

 Wireless Properties
   WEP Encryption:  yes
   WPA Encryption:  yes
   WPA2 Encryption: yes

 Wireless Access Points 

==========================================================


COMMAND:
lsmod
OUTPUT (snipped to show ndiswrapper is loaded and running):
ndiswrapper           184677  0 

==========================================================


COMMAND:
sudo iwlist scan
OUTPUT (for my router):
         Cell 03 - Address: 00:1F:33:FE:AA:53
                   ESSID:"602"
                   Protocol:IEEE 802.11g
                   Mode:Managed
                   Frequency:2.417 GHz (Channel 2)
                   Quality:54/100  Signal level:-61 dBm  Noise level:-96 dBm
                   Encryption key:on
                   Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                             9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                             48 Mb/s; 54 Mb/s
                   Extra:bcn_int=100
                   Extra:atim=0
                   IE: IEEE 802.11i/WPA2 Version 1
                       Group Cipher : TKIP
                       Pairwise Ciphers (2) : CCMP TKIP
                       Authentication Suites (1) : PSK
                   IE: WPA Version 1
                       Group Cipher : TKIP
                       Pairwise Ciphers (2) : CCMP TKIP
                       Authentication Suites (1) : PSK

==========================================================


FILE:	/etc/modprobe.d/blacklist.conf
CONTENTS (modules that i added to avoid driver conflict):

blacklist amd76x_edac
blacklist bcm43xx
blacklist b43
blacklist b43legacy
blacklist ssb
blacklist b43-pci-bridge

NOTES:

The last entry here (b43-pci-bridge) was the default driver for my wireless card before I blacklisted it.

==========================================================


FILE:	/etc/network/interfaces
CONTENTS:
auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet dhcp
wpa-driver wext
wpa-ssid 602
wpa-ap-scan 1
wpa-proto RSN
wpa-pairwise CCMP
wpa-group CCMP
wpa-key-mgmt WPA-PSK
wpa-psk 6861d5c302132fe41b25a58f7b52b94f50497404de980095d18dab1cf22e6808

NOTES:
The wlan0 is not the default setting from a fresh install, I modified this entry according to a tutorial I was following.  The wpa-psk key was generated using the wpa_passphrase command with my essid and password.

---

### Post by pipher on 2010-07-15
Solved!

I don't know that it would have made a difference, but I backleveled to 9.04 first.  Then after some research I learned that my wireless adapter is supported by the b43 drivers included with Ubuntu, however there is b43 driver **firmware**that needs to be obtained from the web (not included with Ubuntu) and installed.  Once I installed the firmware and rebooted, VOILA.

---

