---
title: "Broadcom Corporation BCM4311 WLAN card no longer working"
date: 2009-01-19
forum: Networking &amp; Wireless
---

### Post by ssearcy on 2009-01-19
Hello,

I've been happily using Ubuntu Intrepid Ibex 8.10 fully patched as patches come out since early Dec. 2008.  I've had great success, including with the proprietary wifi drivers for my built-in Broadcom BC4311 b/g wlan card.  I use this system at home with my Netgear wireless b/g router, using WPA2 encryption.  Wifi has been starting on it's own just fine, with this laptop having no problems automatically connecting to my home network after a reboot.  Now, just yesterday, after accepting an ACPI update (can't remember the number, but it came out around 1/14/2009 or so) and doing a reboot, I can no longer get WIFI to work, no matter what I do, or change.  Keep in mind, I have been using linux of some sort since the '80s and my day job is a systems admin for a variety of systems, mostly linux and windows.  I'm also accomplished at hardware and networking, so feel the last 30 hours of me banging my head against the wall is not worth it.

After trying many things in the Ubuntu forums and having none work, I decided to re-install from scratch.  I've now done that, installed updates via the wired connection and again enabled the BC43 proprietary drivers found in System->Admin->Hardware drivers.  A reboot, etc., tell it manually my SSID, WPA key, etc. (ensuring the MAC address is in the router - again this was working so MAC access list in the router shouldn't need to be changed).  Still no dice - all I get is that the radio is DISABLED (dmesg) even though the wireless box is checked in the network GUI (gnome) and the blue light is on on the front of my laptop.

Here's all the specifics as required:

**Laptop:**  HP DV6000 (specific model number from bottom of laptop is:  DV6500.

OS fully patched (as of 1/19/2009) Unbuntu Intrepid Ibex 8.10

**output of uname -a:** 
Linux ufp-laptop 2.6.27-9-generic #1 SMP Thu Nov 20 22:15:32 UTC 2008 x86_64 GNU/Linux

**applicable output of lspci:**
03:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 02)

**output of ifconfig:**
eth0      Link encap:Ethernet  HWaddr 00:1b:24:81:55:6d  
          inet addr:192.168.0.3  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:24ff:fe81:556d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:13393 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11446 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:8052572 (8.0 MB)  TX bytes:855043 (855.0 KB)
          Interrupt:252 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:6 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:376 (376.0 B)  TX bytes:376 (376.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:1a:73:91:50:ea  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-1A-73-91-50-EA-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

**output of iwconfig:**
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

**output of  lsmod | grep b43**
b43                   144424  0 
rfkill                 19364  3 rfkill_input,b43
mac80211              253440  1 b43
led_class              13192  1 b43
input_polldev          12816  1 b43
ssb                    46340  1 b43

**applicable output of dmesg:**
[ 2270.031056] input: b43-phy1 as /devices/virtual/input/input16
[ 2270.285052] b43-phy1: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[ 2270.424851] Registered led device: b43-phy1::tx
[ 2270.429557] Registered led device: b43-phy1::rx
[ 2270.431384] Registered led device: b43-phy1::radio
[ 2270.470213] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2271.060047] b43-phy1: Radio hardware status changed to DISABLED
[ 2271.144031] b43-phy1: Radio turned on by software
[ 2271.144051] b43-phy1: The hardware RF-kill button still turns the radio physically off. Press the button to turn it on.
[ 2279.459987] input: b43-phy1 as /devices/virtual/input/input17
[ 2279.717049] b43-phy1: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[ 2279.856838] Registered led device: b43-phy1::tx
[ 2279.860829] Registered led device: b43-phy1::rx
[ 2279.864615] Registered led device: b43-phy1::radio
[ 2279.917235] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2280.112023] eth0: no IPv6 routers present
[ 2280.488095] b43-phy1: Radio hardware status changed to DISABLED

**output of lshw -C network**
  *-network               
       description: Ethernet interface
       product: MCP67 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a2
       serial: 00:1b:24:81:55:6d
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi ht bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.61 duplex=full ip=192.168.0.3 latency=0 link=yes maxlatency=20 mingnt=1 module=forcedeth multicast=yes port=MII speed=100MB/s
  *-network
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb
  *-network:0 DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 96:28:1c:ba:98:c0
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
  *-network:1
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:1a:73:91:50:ea
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg

**output of iwlist scan**
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

pan0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     No scan results

**lsb_release -d**
Description:	Ubuntu 8.10

** uname -mr**
2.6.27-9-generic x86_64

** /etc/init.d/networking restart**
 * Reconfiguring network interfaces...                                                                                                                   Ignoring unknown interface eth0=eth0.


And of course no wifi when I do this.  Same message in dmesg - DISABLED.  I think this would all work normally (the way it did just a day or so ago), if I could actually get the card turned on, or at least get the system to realize it's on and enabled (wireless is turned on in network manager and blue light is on on front of laptop).  

An additional piece of info., before this happened, I didn't have to turn off the physical wlan switch on the laptop, deselect wireless in the network manager, turn on the switch and then re-enable wireless in the network manager.  It just worked.  Now, to even get the light to turn blue, I have to do the procedure I just described.

Going to stick another hard drive in with Vista (yuk) so I have a laptop with wireless.  Hopefully, there's enough info. in here for someone more knowledgeable about wireless linux drivers than me to present me with more solutions than the countless I've tried.

Thank you,

Shane

---

