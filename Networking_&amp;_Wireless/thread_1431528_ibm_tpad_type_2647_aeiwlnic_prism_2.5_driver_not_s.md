---
title: "ibm tpad type 2647 aeiwlnic prism 2.5 driver not seen in network connections"
date: 2010-03-16
forum: Networking &amp; Wireless
---

### Post by metal4pg on 2010-03-16
I had been using breezy for the longest time & decided to perform a clean install of 9.10. Everything had worked fine using ndiswrapper under breezy. I performed the default install of 9.10 & noticed that my wireless did not function. I figured that since I needed ndiswrapper before, it would just be a simple install & away I go. Unfortuntely, not so much.....

What I've wound up with is a configuration where my wlan0 is shown when doing ifconfig or iwconfig but never appears under system ->preferences -> network connections -> wireless nor is it able to scan for any wireless AP in the area.

I'm still fairly green when it comes to commands & where to look during troubleshooting. I've gone through the [wifi troubleshooting guide]("https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide") & according to it, everything should be functioning properly. I've also ran across a few other topics about a similar usb version of this chipset. All of these had some helpful commands but none seemed to the magic trick to get it all fixed.

I'm at my wits end. I feel like i've traveled down so many rat holes trying to resolve this that I'm all spun around & dizzy as to everything i've done now. I'm posting some entries for some files in the hopes that maybe someone can see something i'm not. 

here's the /etc/modprobe.d/ndiswrapper file:
install pci:v00001260d00003873sv00000406sd00001668bc*sc*i* /sbin/modprobe ndiswrapper
#install pci:v00001260d00003873sv00002406sd00001668bc*sc*i* /sbin/modprobe ndiswrapper
#install pci:v00001260d00003873sv00003406sd00001668bc*sc*i* /sbin/modprobe ndiswrapper
#install pci:v00001260d00003873sv*sd*bc*sc*i* /sbin/modprobe ndiswrapper

I remarked out the bottom 3 entries manually thinking maybe something might be conflicting, restarting afterwards & no change. They originally had all been active entries.

iwconfig:
lo        no wireless extensions.

eth0      no wireless extensions.

irda0     no wireless extensions.

wlan0     IEEE 802.11b  ESSID:"MyRouter"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:11 Mb/s   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

Here's ifconfig:

eth0      Link encap:Ethernet  HWaddr 00:d0:59:33:65:fb  
          inet addr:192.168.10.66  Bcast:192.168.10.255  Mask:255.255.255.0
          inet6 addr: fe80::2d0:59ff:fe33:65fb/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2292 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1602 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1942127 (1.9 MB)  TX bytes:268784 (268.7 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:20:e0:89:05:78  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:11 Memory:ec000000-ec001000 

wlan0:avahi Link encap:Ethernet  HWaddr 00:20:e0:89:05:78  
          inet addr:169.254.6.232  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:11 Memory:ec000000-ec001000 

I manually added my routers info into system -> administration ->network . I have yet to ever see a local wireless network appear on it's own.

Here is the result of ndiswrapper -l: 
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
aeiwlnic : driver installed
	device (1260:3873) present (alternate driver: orinoco_pci)

here is the output of lshw -C network:

 *-network:0             
       description: Wireless interface
       product: Prism 2.5 Wavelan chipset
       vendor: Intersil Corporation
       physical id: 2
       bus info: pci@0000:02:02.0
       logical name: wlan0
       version: 01
       serial: 00:20:e0:89:05:78
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+aeiwlnic driverversion=1.55+Actiontec,09/23/2002, 2.00. latency=64 multicast=yes wireless=IEEE 802.11b
       resources: irq:11 memory:ec000000-ec000fff(prefetchable)
  *-network:1
       description: Ethernet interface
       product: 82801CAM (ICH3) PRO/100 VE (LOM) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:02:08.0
       logical name: eth0
       version: 41
       serial: 00:d0:59:33:65:fb
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI firmware=N/A ip=192.168.10.66 latency=66 maxlatency=56 mingnt=8 multicast=yes
       resources: irq:11 memory:c0200000-c0200fff ioport:7000(size=64)

This is not a wireless usb device & is a chipset that comes as part of the laptop.

Here is the blacklist.conf file:

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5
#blacklist aeiwlnic


# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp

# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac


This laptop works fine on my win-xp side.

I'm extremely frustrated after working on this for the past 3 days. I appear to be missing something but I just don't know what or where to look. Any help would be appreciated. 

Thank you.....

---

