---
title: "Setting up as a wireless AP"
date: 2011-04-18
forum: Networking &amp; Wireless
---

### Post by jshalabh on 2011-04-18
Hello,

I was trying to set up my computer as a wireless AP/router. I am using a  D-Link wireless dongle for the wireless network. I have ensured it can  be put in the master mode. I followed the instructions on [https://help.ubuntu.com/community/Router](https://help.ubuntu.com/community/Router) and steps seemed to have been completed without a problem.

However, the wireless signal is not being broadcasted. I cannot see it  on my phone or my laptop. The only difference I see is that my Ubuntu  installation is the desktop version instead of the server edition.  However, I don't think that should be the issue!

Can somebody suggest what I may be doing incorrectly?

Thanks
Shalabh

The ip addr command produces
> 3: wlan1: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc pfifo_fast state DOWN qlen 1000
    link/ether 00:0d:88:67:f6:c7 brd ff:ff:ff:ff:ff:ff
    inet 192.168.1.1/24 brd 192.168.1.255 scope global wlan1

I suspect this down state to be an issue but the command ip link set  wlan1 up is not doing anything

> The following is the /etc/network/interfaces
 auto lo
 iface lo inet loopback
 
 auto eth0
 iface eth0 inet dhcp
 
 auto wlan1
 iface wlan1 inet static
     wireless-mode Master
     wireless-essid SJWireless
     wireless-channel 6
     wireless-key 0f0bd544f5
     address 192.168.1.1
     network 192.168.1.0
     netmask 255.255.255.0
     broadcast 192.168.1.255
 
 The iwconfig output is as follows
 > lo        no wireless extensions.
 
 eth0      no wireless extensions.
 
 wlan1     IEEE 802.11-DS  ESSID:"SJWireless"  Nickname:"SJWireless"
           Mode:Auto  Frequency:2.467 GHz  Access Point: 00:26:CB:AB:06:50   
           Bit Rate:2 Mb/s   Tx-Power:18 dBm   
           Retry short limit:8   RTS thr:off   Fragment thr:off
           Encryption key:0F0B-D544-F5 [4]   Security mode:restricted
           Link Quality=65/100  Signal level=-62 dBm  Noise level=-88 dBm
           Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
           Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by jshalabh on 2011-04-19
Bump

---

### Post by josephmills on 2011-04-19
could I please see a ```
rfkill list all
``` and ```
lsusb
``` thanks

---

### Post by jshalabh on 2011-04-19
The command rfkill list all produces no output

The output of lsusb is as follows
> Bus 005 Device 004: ID 2001:3700 D-Link Corp. [hex] DWL-122 802.11b
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 003: ID 413c:2003 Dell Computer Corp. Keyboard
Bus 003 Device 002: ID 046d:c012 Logitech, Inc. Mouseman Dual Optical
I think figured out part of my stupidity but the problem seems worst now. I was not aware of using hostapd which has to be enabled for managing the 802.11 frames. It seems that that will enable advertising of the access point. 

However the problem is that the DWL-122 uses the prism2_usb driver. hostapd doesn't support that driver. So I cannot run hostapd. 

My question now is, is there any alternative to hostapd that can be used for managing the 802.11 frame management?

Thanks
Shalabh

---

