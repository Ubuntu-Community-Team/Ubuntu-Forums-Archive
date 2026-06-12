---
title: "Trouble with Intersil Prism 2.5 chipset for Linksys wmp11"
date: 2009-02-06
forum: Networking &amp; Wireless
---

### Post by thirdrev on 2009-02-06
I'm running Ubuntu 8.10 64bit and am unable to get my wireless card working. It was previously working under 8.04 32bit. I have tried ndiswrapper to no avail (which I believe is what I was using before but I can't remember for certain). My outputs are as follows:

**sudo lshw -C network:**
  *-network               
       description: Wireless interface
       product: Prism 2.5 Wavelan chipset
       vendor: Intersil Corporation
       physical id: 6
       bus info: pci@0000:01:06.0
       logical name: eth1
       version: 01
       serial: 00:06:25:09:95:df
       width: 32 bits
       clock: 33MHz
       capabilities: pm cap_list ethernet physical wireless
       configuration: broadcast=yes driver=orinoco driverversion=0.15 firmware=Intersil 1.4.2 latency=0 link=no module=orinoco_pci multicast=yes wireless=IEEE 802.11b
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 0a:cc:e4:33:4b:fe
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

**ifconfig:**
eth0      Link encap:Ethernet  HWaddr 00:21:97:a4:78:3a  
          inet6 addr: fe80::221:97ff:fea4:783a/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:11107 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6547 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:10223883 (10.2 MB)  TX bytes:934111 (934.1 KB)
          Interrupt:252 Base address:0xc000 

eth1      Link encap:Ethernet  HWaddr 00:06:25:09:95:df  
          inet6 addr: fe80::206:25ff:fe09:95df/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:362 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:12994 (12.9 KB)  TX bytes:792 (792.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

**iwconfig:**
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

eth1      IEEE 802.11b  ESSID:"2W1RE020"  Nickname:"Prism  I"
          Mode:Managed  Frequency:2.462 GHz  Access Point: None   
          Bit Rate:11 Mb/s   Sensitivity:1/3  
          Retry short limit:8   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=92/92  Signal level=-2 dBm  Noise level=-149 dBm
          Rx invalid nwid:0  Rx invalid crypt:18  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

**ndiswrapper -l:**
wmp11nds : driver installed
	device (1260:3873) present (alternate driver: orinoco_pci)

if I blacklist the orinoco_pci driver it changes the eht1 output for iwconfig to "no wireless extensions"

A few other things that may be important:
-Whenever I enter the key a 128bit 13 character Ascii passphrase - network manager changes it to something else.

-In the post [http://ubuntuforums.org/showthread.php?t=885847](http://ubuntuforums.org/showthread.php?t=885847) under part two it says I need a driver with the same architecture to match the Ubuntu version (e.g. 64bit) However, I can only find a 32bit version from linksys. Is this my ultimate problem? (I think it might be) If so, is there some thing other than ndiswrapper that may be used to get a Prism 2.5 working? or somewhere to find a 64bit version of the wmp11 driver?

Thanks

---

### Post by thirdrev on 2009-02-06
I found [http://ubuntuforums.org/showthread.php?t=968797](http://ubuntuforums.org/showthread.php?t=968797) 
and tried inserting: 

# possible coflict with hostap drivers
blacklist hermes
blacklist orinoco
blacklist orinoco_pci
blacklist orinoco_cs
blacklist orinoco_plx 

into blacklist, rebooted, and now it works. Hooray.

---

