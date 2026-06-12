---
title: "Wireless works perfectly but wired seems to have dns issues"
date: 2009-01-17
forum: Networking &amp; Wireless
---

### Post by stormtrooprdave on 2009-01-17
I have been using a wireless connection on Hardy and then Intrepid with no problems what so ever.  I need to now use a wired connection but cannot get it to work.  When I try to browse websites using the wired connection I can only access google sites such as picassa, google news, gmail, etc, but no other site will load.  It just keeps loading.... for as long as I leave it.

I have tried all sorts of solutions on these forums but none have worked. I will outline what I have tried already below:

Added blacklist ipv6 to etc/modprobe.d/blacklist - no effect
Made adjustments to etc/ppp/options and the mtu level - no effect
Added my ISP's dns servers to resolv.conf - no effect
Added the lines auto eth0, iface eth0 inet dhcp to eth/network/interface - no effect
Also tried changing ifupdown:managed=false to true in /etc/NetworkManager/nm-system-settings.conf = no effect

The wired connection does have a connection then as it will browse google related pages with no problem,  other pages hang indefinitely. It also will not access the router settings or my NAS drive. Wireless works perfectly.  Wired also works perfectly on XP and Windows 7 Beta.

I;ve been searching a lot on these forums and have run out of ideas - please help!

---

### Post by stormtrooprdave on 2009-01-18
bump

---

### Post by stormtrooprdave on 2009-01-20
bumpity bump

---

### Post by stormtrooprdave on 2009-01-22
bump

---

### Post by stormtrooprdave on 2009-01-25
results from ifconfig -

eth0      Link encap:Ethernet  HWaddr 00:50:8d:98:57:25  
          inet addr:192.168.1.69  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::250:8dff:fe98:5725/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:459 errors:36 dropped:0 overruns:0 frame:36
          TX packets:442 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:141928 (141.9 KB)  TX bytes:53759 (53.7 KB)
          Interrupt:19 Base address:0xdead 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1184 (1.1 KB)  TX bytes:1184 (1.1 KB)

wlan0     Link encap:Ethernet  HWaddr 00:17:3f:b1:a5:54  
          inet6 addr: fe80::217:3fff:feb1:a554/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:28 errors:0 dropped:0 overruns:0 frame:0
          TX packets:21 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3395 (3.3 KB)  TX bytes:5563 (5.5 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-17-3F-B1-A5-54-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

Please can anyone suggest something or help in anyway?

---

### Post by stormtrooprdave on 2009-01-27
More info:

dig [www.yahoo.com](www.yahoo.com)

; <<>> DiG 9.5.0-P2 <<>> [www.yahoo.com](www.yahoo.com)
;; global options: printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 12369
;; flags: qr rd ra; QUERY: 1, ANSWER: 2, AUTHORITY: 9, ADDITIONAL: 9

;; QUESTION SECTION:
;[www.yahoo.com](www.yahoo.com). IN A

;; ANSWER SECTION:
[www.yahoo.com](www.yahoo.com). 112 IN CNAME [www.yahoo-ht3.akadns.net](www.yahoo-ht3.akadns.net).
[www.yahoo-ht3.akadns.net](www.yahoo-ht3.akadns.net). 4 IN A 87.248.113.14

;; AUTHORITY SECTION:
akadns.net. 113659 IN NS eur1.akadns.net.
akadns.net. 113659 IN NS use3.akadns.net.
akadns.net. 113659 IN NS use4.akadns.net.
akadns.net. 113659 IN NS usw2.akadns.net.
akadns.net. 113659 IN NS asia9.akadns.net.
akadns.net. 113659 IN NS za.akadns.org.
akadns.net. 113659 IN NS zb.akadns.org.
akadns.net. 113659 IN NS zc.akadns.org.
akadns.net. 113659 IN NS zd.akadns.org.

;; ADDITIONAL SECTION:
za.akadns.org. 2391 IN A 195.219.3.169
zb.akadns.org. 2460 IN A 12.183.125.5
zc.akadns.org. 1376 IN A 124.211.40.4
zd.akadns.org. 2009 IN A 204.2.178.133
eur1.akadns.net. 67719 IN A 195.59.44.134
use3.akadns.net. 67719 IN A 204.2.178.133
use4.akadns.net. 58504 IN A 208.44.108.137
usw2.akadns.net. 64062 IN A 12.183.125.5
asia9.akadns.net. 67719 IN A 220.73.220.4

;; Query time: 36 msec
;; SERVER: 192.168.1.254#53(192.168.1.254)
;; WHEN: Tue Jan 27 17:40:46 2009
;; MSG SIZE rcvd: 403

telnet [www.yahoo.com](www.yahoo.com) 80
Trying 87.248.113.14...
Connected to [www.yahoo-ht3.akadns.net](www.yahoo-ht3.akadns.net).
Escape character is '^]'.

I have no idea what any of this means lol

---

### Post by stormtrooprdave on 2009-02-01
bump

---

### Post by ugm6hr on 2009-02-07
I am no expert, but thought I'd offer some thoughts.

It seems dig finds the IP appropriately using the default DNS lookup.  Presumably you ran that command with wired connection only?

Can you also ping (with wired)?

```
ping -c 3 www.yahoo.com
```

Will yahoo load with the IP in Firefox?
[http://87.248.113.14/](http://87.248.113.14/)

Can you ping the router?

Hopefully this will find whether the issue is Firefox or Ubuntu itself.

I am interested in DNS issues having suffered a problem when connected to a hotel network.

---

### Post by stormtrooprdave on 2009-02-08
I've almost given up on this.  After trying various solutions (which people post without telling you how to undo any changes if it doesn't work) I now don't have any wired connection at all.  There is nothing listed under ifconfig and if I do lshw -C network it says "network unclaimed" for the ethernet controller, which I guess means somehow the driver has disappeared.  

So I'm now even further back, having to figure out how to get the lan to even show up before I can attempt to fix it. :mad:

---

### Post by ugm6hr on 2009-02-08
Maybe tell us what you've tried and we might be able to help reverse the situation.

Or if you have a separate /home partition, consider reinstalling if you think it would be faster.

---

### Post by stormtrooprdave on 2009-02-08
It was suggested to use ndiswrapper to install the ethernet driver but nothing happened so I uninstalled ndiswrapper and the whole lan has gone missing.  I just used the jaunty alpha 4 live cd and it had the eth0 back but it still had the exact same problem.  I'm close to writing this one off as a lost cause.

---

### Post by ugm6hr on 2009-02-08
Your choice.

You never needed ndiswrapper.  The driver was working fine - dig found the correct IP.

This was probably a DNS issue.

If you want to try and find out what was going on - follow the advice I gave earlier, and report back with results from the LiveCD (probably best to stick with a released version though).

---

### Post by stormtrooprdave on 2009-02-09
Is it possible to launch into a livecd and copy the ethernet driver from there into lib/modules or something like that?

---

### Post by ugm6hr on 2009-02-09
Why not just remove ndiswrapper?

```
sudo apt-get remove ndiswrapper-common
```

If you blacklisted the native driver, you will need to unblacklist it.

```
gksudo gedit /etc/modprobe.d/blacklist
```

Just undo whatever you did there.

---

### Post by stormtrooprdave on 2009-02-10
I didn't blacklist anything and I've already removed ndiswrapper.  Removing it is what seems to have taken the native driver away with it.  So I need to get the default drivers back, I thought they might be on a livecd?

---

### Post by stormtrooprdave on 2009-02-10
Been looking into how drivers work on Ubuntu.  

In /lib/modules/2.6.27-11-generic/kernel/drivers/net/modules.dep it lists the ethernet driver as the following:

/lib/modules/2.6.27-11-generic/kernel/drivers/net/sis190.ko: /lib/modules/2.6.27-11-generic/kernel/drivers/net/mii.ko

Should it not point to sis190.ko instead of mii.ko, which is in the same folder?

---

### Post by ugm6hr on 2009-02-10
> **stormtrooprdave said:**
> I didn't blacklist anything and I've already removed ndiswrapper.  Removing it is what seems to have taken the native driver away with it. 

Removing ndiswrapper will not remove any native drivers.

It is unlikely that you didn't blacklist the natibe driver, since ndiswrapper will not work unless you remove the default native driver, and blacklisting is the simplest way to do that.

Perhaps post the contents of your blacklist file (as my previous post), and also the output from:
```
lspci
lshw -class network
```

Also - links to the advice you followed re: ndiswrapper would be helpful.

---

### Post by stormtrooprdave on 2009-02-10
**Blacklist:**

# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

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

#disable system beep from internal speaker
blacklist pcspkr


**lspci:**

00:00.0 Host bridge: Silicon Integrated Systems [SiS] 662 Host (rev 01)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS966 [MuTIOL Media IO] (rev 59)
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev 01)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] 190 Ethernet Adapter (rev 01)
00:05.0 IDE interface: Silicon Integrated Systems [SiS] SATA Controller / IDE mode (rev 02)
00:06.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
00:07.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
00:0f.0 Audio device: Silicon Integrated Systems [SiS] Azalia Audio Controller
01:00.0 VGA compatible controller: nVidia Corporation G71 [GeForce 7950 GT] (rev a1)



**lshw -class network:**

WARNING: you should run this program as super-user.
  *-network UNCLAIMED     
       description: Ethernet controller
       product: 190 Ethernet Adapter
       vendor: Silicon Integrated Systems [SiS]
       physical id: 4
       bus info: pci@0000:00:04.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:17:3f:b1:a5:54
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.1.65 multicast=yes wireless=IEEE 802.11bg


As you can see it says network unclaimed, which from reading around these forums means there is no driver installed for it?

---

### Post by stormtrooprdave on 2009-02-18
Found out that **sudo modprobe sis190** brings my auto eth0 back so ready to try and fix this again if anyone can help?

(also I have to add the module each time after startup, I'm on intrepid and there doesn't seem to be a modprobe.conf for me to add the module to for it to auto load?)

---

### Post by stormtrooprdave on 2009-02-20
I added sis190 to etc/modules and it loads on startup now. Still attempting to solve eth0 problem.  The struggle continues...

---

