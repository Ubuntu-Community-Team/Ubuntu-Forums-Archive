---
title: "HP Pavilion, a6600f,Fresh Install, No Network Noob"
date: 2010-08-23
forum: Networking &amp; Wireless
---

### Post by Sxynerd on 2010-08-23
OK so I'm clueless about this format I need to use for starting this thread.  I am trying to connect to the internet but have no network connections available and it says my wireless is disabled.  (Ubuntu Studio 10.04)

How do I turn it on?

Thanks,
-Nerd




1 ) Machine Brand and Model (PC/Laptop):
Code:
**HP Pavilion, a6600f**

2 ) Wireless Brand, Model and Wireless Chipset:
Code:

$ **Broadband Corp. BCM4318 [air force one 54g]**
$ lsusb (No Idea how to transpose this to this computer except long hand)

(hint) use grep to get only information about the Wireless
Code:

$ lspci -nn | grep 'Wireless Brand'  [B](NO idea what this means)
[/B]
3 ) check interface:
Code:

$ ifconfig   **Local Loopback: 127.0.0.2, 255.0.0.0, 1/28, Host, 16436, 1 **
$ iwconfig      **No wireless ext, No wireless ext.,  IEEE 802.11bg Off/Any, Not associated, **

(hint) if the Wireless interface name is wlan0 you can also use
Code:

$ iwconfig wlan0

4 ) Check for modules:
Code:

$ lsmod  **NO IDEA WHAT THIS IS EITHER but I found something called CFG80211 / 149242/ 2 / b42.mac80211**

(hint) search for the Wireless module
Code:

$ lsmod | grep "wlan_module_name"

5 ) Kernel boot messages
Code:

$ dmesg
**No idea what part to write here.  At least 100 lines of text**

(hint) the same as in (4)

6 ) Network configuration
Code:

$ sudo lshw -C network
[B]*network
description: Network Controller
Product: BBCM4318 [AirForce One 54g] 802.11g wireless LAN Controller
Vender: Broadcom Corp
Physical id: 6
bus info: pci@0000:01:06.0
version: 02
width: 32 bits
clock 33MHz
Cap: bus_master
Config: driver=b43-pci-bridge latency=64
Resources: irq:18 mem:efbfc000-efbfdfff
*Network DISABLED
Desc: Ethernet Interface
Product: MCP73 Ethernet
Vendor: nVidia Corp   
^ON BOARD  Not Using this, I'm trying to use the wireless
*Network DISABLED
Desc: Wireless Interface
Phys ID: 1
logical name wlano
serial: 00:22:75:19:6d:51
Capa: ethernet physical wireless
config: broadcast=yes multicast=yes wireless=IEEE 802.11bg[/B]

7 ) Scan for networks:
Code:

$ iwlist scan
[B]Lo: Int. doesn't support scanning
eth0: SAA
wlan0 FFailed to read scan data : Network is Down[/B]

(hint) the same as in (3)
Code:

$ iwlist scan wlan0
**"Unknown command"**

8 ) Ubuntu Version:
Code:

$ lsb_release -d
**Ubuntu 10.04 LTS**

9 ) Kernel/architecture (including 32 vs. 64 bit):
Code:

$ uname -mr
**2.6.32-21-preempt x86_64**

10 ) Restarting the network:
Code:

$ sudo /etc/init.d/networking restart
**Reconfiguring networking interface [ ok ]**

---

### Post by Iowan on 2010-08-23
Check **ifconfig -a** again. Something looks unusual having "lo" at 127.0.0.2...

Unless I missed it, I don't see a driver listed for **wlan0** in **lshw**

---

### Post by Sxynerd on 2010-08-23
Thanks for your reply.  I am completely lost here, lol.  Ubuntu on my EEEPC was so much easier.   I don't know if I was clear or not, I do not have a hard lan connection since I don't have a cable long enough.  I am trying to use Wireless only.


Here is the response.

eth0
Link encap: Ethernet  HWaddr 00:lf:e2:55:44:7a
Broadband multicast MTU:1500 Metric:1
RX Pac:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 Carrier:0
RX bytes:0 (0.0 B) TX bytes:0 (0.0B)
Iterupt:20 Base address:0xa000

lo
Link encap:Local Loopbacl
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr:  ::1/128 Scope:Host
UP LOOPBACK RUNNING  MTU:16436 Metric:1
RX packets:896 errors:0 dropped:0 overruns:0 frame:0
TX packets:896 errors:0 dropped:0 overrunds:0 carrier:0
collisions:0 txqeuelen:0
RX bytes:69640 (69.6 KB) tx bytes:69640 (69.6 KB)

wlan0
link encap:Ethernet  HWaddr  00:22:75:19:6d:51
Broadcast Multicast MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 Dropped:0 overruns:0 carrier:0
Collisions:0 txqeuelen:1000
RX bytes:0 (0.0 B) TX bytes:0 (0.0B)


I don't know what I am looking for with the lshw but here it is the last section I think might matter:

*-network Disabled
descr:  Wireless interface
physical id: 3
logical name: wlan0
serial: 00:22:75:19:6d:51
capa: ethernet physical wireless
Config:  Broadcast=yes multicast=yes wireless=IEEE 802.11bg

---

### Post by Sxynerd on 2010-08-24
I just don't know if this Ubuntu is worth it.  I've been on this problem for nearly 24 hours and I can't figure it out.  From what everyone tells me Ubuntu is faster than Windows and all the programs are free but what good is it, if you give up ease of installation and lack of basic operations? 

-frustrated

---

### Post by cchhrriiss121212 on 2010-08-24
> **Sxynerd said:**
> I just don't know if this Ubuntu is worth it.  I've been on this problem for nearly 24 hours and I can't figure it out.  From what everyone tells me Ubuntu is faster than Windows and all the programs are free but what good is it, if you give up ease of installation and lack of basic operations? 

-frustrated
Wireless connections and network manager are disabled by default in Ubuntu Studio. This is intentional as it interferes with audio processing, which is one of the things studio is produced for.

Have a read [here]("http://ubuntuforums.org/showthread.php?t=1525705") to find out a bit more, and get a solution. If you are getting frustrated over anything in Ubuntu then try taking a break from it, and wait for a response on the forums rather than trying to fix things yourself.

---

### Post by Sxynerd on 2010-08-24
Thanks for your reply.  From your link, I have figured out that in "Studio"  The network manager is not either installed or activated.  I have tried as many of the things in the link and corresponding links as I can I have yet to figure out what to do next.

here is the response from one of those things.  
[SIZE="2"][B][FONT="Arial Black"]michael@UbuntuHP:~$ nm-applet
The program 'nm-applet' can be found in the following packages:
 * network-manager-gnome
 * mythbuntu-diskless-client
Try: sudo apt-get install <selected package>
michael@UbuntuHP:~$ sudo apt-get install
[sudo] password for michael: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up b43-fwcutter (1:012-1build1) ...
--2010-08-24 12:55:40--  [http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o](http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o)
Resolving downloads.openwrt.org... failed: Name or service not known.
wget: unable to resolve host address `downloads.openwrt.org'
dpkg: error processing b43-fwcutter (--configure):
 subprocess installed post-installation script returned error exit status 4
E: Sub-process /usr/bin/dpkg returned an error code (1)
michael@UbuntuHP:~$ [/FONT][/B][/SIZE]

I also tried this.

---

### Post by cchhrriiss121212 on 2010-08-24
This should be your first step:
> Put the studio dvd in the drive and browse to this location:
 /media/cdrom1/pool/main/n
Then install the .deb packages in network-manager and network-manager-applet.
Did you try to get those packages installed? If I remember correctly you need to install them in a certain order, so that the lowest dependencies are satisfied first. You can't continue with the other steps if you have not installed network manager.

---

### Post by Sxynerd on 2010-08-24
Yes, here is the screen shot from the Network-manager folder.  I installed them from left to right (Install windows below not the apps in the folder.  (manager, util1 and then glib2)

When I tried installing network-manager-applet folder, file "network-manager_0.8-0ubuntu3_amd64.deb"  I was met with "[COLOR="Red"]error: Discrepancy is not satisfied: mobile broadband-provider-info (>= 20090622[/COLOR]"

---

### Post by cchhrriiss121212 on 2010-08-25
So now just go to the m folder and install that package, and any other package that is required, they are all on the DVD image.

---

### Post by Sxynerd on 2010-08-25
> **cchhrriiss121212 said:**
> So now just go to the m folder and install that package, and any other package that is required, they are all on the DVD image.

Thanks.  I tried that to no avail.  I gave up and installed Desktop.  Unfortunately, I'm running across similar problems.  Here's the new link.
[http://ubuntuforums.org/showthread.php?p=9763000#post9763000](http://ubuntuforums.org/showthread.php?p=9763000#post9763000)

I now have the program called "Windows Wireless Drivers" in my system/admin section.  I have place in the INF file but I still have no connection to the internet.


-still frustrated.

Thanks

---

