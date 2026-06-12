---
title: "Wireless not working-Dell Inspiron 1545"
date: 2010-06-06
forum: Networking &amp; Wireless
---

### Post by SunJune on 2010-06-06
Hi,

I am having trouble in getting the wireless up in Ubunto 10.04. Under Wireless Networks it says "wireless disabled". I have a dual boot with Windows 7, installed Ubunto with the help of Wubi installer. My laptop is Dell Inspiron 1545, with a 64 bit architecture.

 I have already done checking and enabling the wireless driver by going to System- Administration-Hardware Drivers and choosing Broadcom STA driver. Wired connection is working perfectly fine, it is the wireless that is bothering me.Few things I checked for and here are the outputs.

1) lshw -c network

WARNING: you should run this program as super-user.
  *-network DISABLED      
       description: Wireless interface
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: eth1
       version: 01
       serial: 70:1a:04:76:67:11
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.60.48.36 latency=0 multicast=yes wireless=IEEE 802.11
      


2) lspci -nn |grep 14e4

0c:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g [14e4:4315] (rev 01)

3) rfkill list
 
 0: dell-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: yes

4) iwconfig

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:0  Noise level:0
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0


 Please help,  have checked other posts and tried to resolve it but with  no luck. Thanks in advance.

---

### Post by bkratz on 2010-06-07
It seems to think that you have the wireless switch "off". 

3) rfkill list

0: dell-wifi: Wireless LAN
Soft blocked: no
[COLOR="Red"]Hard blocked: yes[/COLOR]

---

### Post by jangozo on 2010-06-07
I have the exact same problem on my dell 1545. I turned it to Hard blocked: no by pressing Fn + F2, but I still get the same problem.

I should also add that following the WifiDocsDriverNdiswrapper guide doesn't help. ( [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper) ) Blacklisting the drivers completely disables everything, even after I add the driver using ndisgtk and attempt to enable it. This may be a Ubuntu 10.4 thing.

Thanks

---

### Post by jangozo on 2010-06-07
Ok so I did a bit more testing and it turns out that those on Dell 1545 don't need all this setup.

System -> Administration -> Hardware Drivers finds you the Broadcom STA proprietary wireless driver. Now, after activating this driver it all works fine. If it is already activated, remove it and then activate it.

Also make sure your wireless card is on (Fn + F2).

However, the problem is that now I have to remove and install the driver from Hardware Drivers every time I want to use my Ubuntu. What should I do to make it load at startup?

Thanks

---

### Post by SunJune on 2010-06-07
Thanks, I did turn on the switch and the rfkill list now shows the output as :

rfkill list
0: dell-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no

But now the problem is that it doesn't recognizes the wireless connections at all. In Network Manager, under wireless networks-->disconnected

Any workarounds?

Thanks

---

### Post by EricNMiller on 2010-06-07
My Dell 1545 wireless network worked just fine under Hardy Heron 8.04.  It stopped working after upgrading to Lucid Lynx 10.04.  The wired network also works well under 10.04.

When I try to activate the Broadcom STA  wireless driver it get an error message saying - Failed to fetch [http://us.archive](http://us.archive) ubuntu1_i386.deb  Could not resolve 'us.archive.ubuntu.com'.  

I performed the upgrade to my Dell 1545 to 10.04 using the live CD because I had problems with the download upgrade with my desktop PC locking it up in kernel panic mode  I had to use the SystemRescueCD to regain control and install 10.04 there.

Hey, I found that my problem was that when I activate the Broadcom STA I hadn't connected the network cable to allow the system to go online to find the driver file.  As I looked over the READ.ME at [http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php), I realized the error was caused by me.

Sorry for the false alarm.  Ubuntu 10.04 fixed itself when given the chance.

---

### Post by jangozo on 2010-06-08
> **SunJune said:**
> Thanks, I did turn on the switch and the rfkill list now shows the output as :

rfkill list
0: dell-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no

But now the problem is that it doesn't recognizes the wireless connections at all. In Network Manager, under wireless networks-->disconnected

Any workarounds?

Thanks

As you know, I have the same setup, so here is the thread there I sorted it out [http://ubuntuforums.org/showthread.php?t=1503893](http://ubuntuforums.org/showthread.php?t=1503893) . In a nutshell, establish a wired connection so that Hardware Drivers can find and download the correct drivers, then activate the Broadcom proprietary STA driver. This will make it work. Then add it to the list of starting drivers using the thread I posted.

---

### Post by lrios on 2010-10-19
Hi, you can try using this link, i think that you must update your BIOS, I resolve this problem on my dell Inspiron 1764, i3,

[http://ubuntu-ky.ubuntuforums.org/showthread.php?p=9972124](http://ubuntu-ky.ubuntuforums.org/showthread.php?p=9972124)

[https://bugzilla.kernel.org/show_bug.cgi?id=14098](https://bugzilla.kernel.org/show_bug.cgi?id=14098)

See you,


Luis Ríos

---

