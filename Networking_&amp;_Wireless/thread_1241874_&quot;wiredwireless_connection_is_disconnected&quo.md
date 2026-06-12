---
title: "&quot;wired/wireless connection is disconnected&quot;"
date: 2009-08-16
forum: Networking &amp; Wireless
---

### Post by luomo on 2009-08-16
Ubuntu tries to connect to my modem through wireless or wired connection and then shows message:"wired/wireless connection is disconnected". Could anyone tell me what to do?

---

### Post by Iowan on 2009-08-16
The "disconnected" message pops up when DHCP fails to get address. You can see if [this]("http://ubuntuforums.org/showthread.php?t=1156441") helps.

---

### Post by luomo on 2009-08-17
thanks Iowan for your help.
but my problem is not solved. I have setup all connections and put dsl configuration still my internet is not working. I am hopeful that you will help me to resolve this issue also.

---

### Post by superprash2003 on 2009-08-17
post output of **ifconfig **from the terminal

---

### Post by luomo on 2009-08-18
I am using Live CD and not have installed.

---

### Post by luomo on 2009-12-01
[SIZE=3]If someone is still there then please help me. I have shifted my OS to ubuntu 9.10.
[/SIZE][SIZE=3]
[/SIZE]

---

### Post by luomo on 2009-12-01
[SIZE=2]I am connecting to my **modem in breezy mode** and it is accepting DHCP request. I have read all steps told earlier by Iowan and prashant speaks and followed them. But still i am unable to get my connection working. 
**Result of iwconfig:**
[/SIZE][HTML]
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"UTStarcom"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:1B:57:F4:F7:EF   
          Bit Rate=1 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=62/70  Signal level=-48 dBm  Noise level=-70 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
[/HTML]
[SIZE=2]
[/SIZE]

---

### Post by luomo on 2009-12-03
Iowan Please help me

---

### Post by Iowan on 2009-12-03
Breezy mode? 
By modem, you mean DSL (or dialup)?
Early on, Karmic had some problems with DSL (actually, PPPOE) - I think I read where they'd been resolved (but can't point to a page). My modem does all the dirty work - so I connect to it like a router. How are you configured - Network Manager?

---

### Post by luomo on 2009-12-04
My Modem is DSL Modem and having Breezy mode means need DHCP connection and I have done all the steps that you have suggested in previous threads like changing and saving dhclient.conf file. I have network card of BCM b4311 seris but i have resolved that issue by fwcutter. Iowan you are my only hope. So please help me in resolving this issue.

---

### Post by luomo on 2009-12-04
My connection is PPPOE also.

---

### Post by luomo on 2009-12-04
Supransh2003 Please help me in solving this problem

---

### Post by hardfire_avk on 2009-12-04
post the output of ifconfig !!

---

### Post by northd_tech on 2009-12-04
The "wlan0" indicates that you do have a wireless network interface module already installed in whichever kernel you are using.  

It will also help if you post the output of the following commands to determine exactly what kind of hardware you have (some of these will have very long output results):

```
lsmod

uname -a

lspci

lsusb

sudo lshw -C network

```Just cut and paste each of those commands one at a time into a terminal window, and then paste the results in BETWEEN either code tags (the # sign at the right of the forum post reply window, just to the left of the "<>" HTML tags) or else a pair of quote tags (that you get from clicking the icon just to the left of the "#" CODE tag button).

---

### Post by luomo on 2009-12-04
sorry, I am a newbie. I have tied ifconfig and sudo ifconfig both on terminal but its showing unknown command.

---

### Post by northd_tech on 2009-12-04
OK, since we don't know the machine architecture, the first thing is to post the results of this command:

```
uname -a
```If you are running ubuntu 9.04, I recall that being codenamed "Jaunty Jackalope," and the net-tools package (that contains ifconfig) should be available here (with links for the other versions):

[http://packages.ubuntu.com/jaunty/net-tools](http://packages.ubuntu.com/jaunty/net-tools)

You should probably install that "libc6" library at that page first (it's needed by a ton of programs and you might not have it for some strange reason if you don't have "ifconfig" either).  When you get error messages about dependencies, libraries, or headers, this is the kind of thing being referred to.  

Did you install a "lite" or customized version of ubuntu, or is it a "standard" version?  If you are running off a "live CD", then ubuntu won't save any of the changes that you make- the Linux OS is actually running off a RAM"disk", and installing any packages will be a waste of time until ubuntu is installed on the hard disk (or on a USB stick- but that's another project).

See if either of the following commands give any results (or just a blank line):

```
locate ifconfig

```Run these commands in order from a terminal:
```
cd /
find ifconfig
```Edit:  Also, here is the Wiki page for ifconfig:

[http://en.wikipedia.org/wiki/Ifconfig](http://en.wikipedia.org/wiki/Ifconfig)

You can often find some pretty good Linux information on the Wiki(s)- that's one of the very few things it is actually good for.

---

### Post by luomo on 2009-12-04
**output of  uname -a**
[HTML]Linux cyber-laptop 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:04:26 UTC 2009 i686 GNU/Linux
[/HTML]
and I am on ubuntu 9.10

---

### Post by luomo on 2009-12-04
**Output of sudo lshw -C network** 
 [html]*-network               
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:16 memory:d6000000-d6003fff
  *-network
       description: Ethernet interface
       product: PRO/100 VE Network Connection
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:05:08.0
       logical name: eth0
       version: 02
       serial: 00:1b:24:06:02:cc
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=half firmware=N/A latency=64 link=no maxlatency=56 mingnt=8 multicast=yes port=MII speed=10MB/s
       resources: irq:20 memory:d8000000-d8000fff ioport:4000(size=64)
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:1a:73:50:4e:b0
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
[/html]

---

### Post by luomo on 2009-12-04
I am using windows XP and ubuntu 9.10 on the same machine and cant coonect to internet through ubuntu as it is not connection to my modem through wired or wireless connection.

---

### Post by northd_tech on 2009-12-04
> **luomo said:**
> output of  uname -a
Linux cyber-laptop 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:04:26 UTC 2009 i686 GNU/Linux

and I am on ubuntu 9.10

OK, that's a 32-bit ubuntu 9.10.  Be sure to only get 32-bit packages for that (and the .deb files are probably the easiest way, other than using the Synaptics package manager).

I think that if you run either the Update Manager or possibly the Synaptics Package Manager (both under System, Administration, and they will want your "sudo" password every so often), you can update to the 2.6.31-15-generic linux kernel.  There is a decent chance that might fix your wireless issue, if you are able to get a cable internet connection to work.

If not, you will need to download the appropriate 32-bit .deb files on another machine and transfer (probably via USB stick) to the laptop.  Then just open the .deb files with the Package Manager, and tell it install/update.  A Toshiba laptop I've been swearing at for weeks worked great under 32-bit with those 2 kernels, but I've had ZERO luck with the 64-bit and wireless.

You might need to look into a thing called "ndiswrapper" and Windows drivers for wireless.  See if you've got a "Windows Wireless Drivers" icon on that same System, Administration menu way down at the bottom.  You should have one there under Koala 9.10.

Edit:  WinXP should download those .deb files just fine if you right-click "Save Link As" to your USB stick.  They should be about 25 MB each, and you might need to click "Places" to mount the USB drive when you're in ubuntu.  The ubuntu Package Manager(s) are slick- probably the best I've seen under any operating system ever.

I don't have time to search for the correct 32-bit 2.6.31-15-generic kernel, but search with those numbers, "kernel" "generic" and ".deb" and you should be able to find one.  MAKE SURE it is the 32-bit "i686" version, NOT the "amd64" version though.

---

### Post by luomo on 2009-12-04
Please tell me from where to download .deb package in ubuntu 9.10. and i dont know what happen but this time ifconfig commands run smoothly and give following output:

---

### Post by luomo on 2009-12-04
[SIZE=2]My computer scans all the connections wireless or wired and showed it properly but the circle moves and moves on then this comes as written "connection is disconnected"
**output of ifconfig**:
[/SIZE][HTML]
 eth0      Link encap:Ethernet  HWaddr   
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

wlan0     Link encap:Ethernet  HWaddr   
          inet6 addr: fe80::21a:73ff:fe50:4eb0/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:15 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:3816 (3.8 KB)

wmaster0  Link encap:UNSPEC  HWaddr   
          UP RUNNING  MTU:0  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
[/HTML]
[SIZE=2] 
[/SIZE]

---

### Post by Iowan on 2009-12-04
Standard font, please. > Please use color and font properties for highlighting portions of your text, and not for all of the text in your post. Standard font, please. > **luomo said:**
> Iowan you are my only hope.I rather doubt it... If so, you're in trouble.

 There is supposed to be an update available that fixes the PPPOE bug. I don't (yet) have 9.10, so can't verify. I suspect I know the results of **sudo dhclient eth0**, but post them anyway.

How are your int3erfaces configured - via Network Manager? Or have you installed WICD... or configured bu dorectly editing */etc/netowrk/interfaces* ?

---

### Post by cariboo on 2009-12-04
Please don't create multiple threads on the same subject. I have merged your two threads.

---

### Post by luomo on 2009-12-05
[B]result of sudo dhclient eth0:
[/B]```

sudo dhclient eth0

Internet Systems Consortium DHCP Client V3.1.2
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:1b:24:06:02:cc
Sending on   LPF/eth0/00:1b:24:06:02:cc
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 20
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
No DHCPOFFERS received.
No working leases in persistent database - sleeping.


```**Result of nm-applet --sm-disable on terminal:**
> 

nm-applet --sm-disable

** (nm-applet:2017): WARNING **: <WARN>  request_name(): Could not acquire the session service as it is already taken.  Return: 3


** (nm-applet:2017): WARNING **: <WARN>  constructor(): Couldn't initialize the D-Bus manager.

I have not configured interfaces these are automatically configured.
When I start my laptop,network manager on the top right automatically detects access point and then start connecting to it. Is there need to configure it manually? In windows I do not need to configure it. Once connection is detected and laptop is connected to modem/Access Point i just start my DSL/Internet connection. Thanks for helping till now and please please help me in resolving this issue. I want to leave windows.

---

### Post by luomo on 2009-12-05
I have also upgraded the ubuntu 9.10 kernel to v2.6.32 but still issue is not resolved. Any help.

---

### Post by luomo on 2009-12-06
I am getting frustrated. I have tried to establish static wired connection. It established for few minutes and then I try to connect my DSL connection but the internet connection is not started so I restart my PC and after that wired connection stops working.
I have also checked /etc/network/interfaces and posting the result which appears me some awkward:
[html]
auto lo
iface lo inet loopback
[/html]Please help me. Iowan you have much knowledge, you could at least assist me solving the problem.

---

### Post by northd_tech on 2009-12-06
> **luomo said:**
> **Output of sudo lshw -C network** 
 [html]*-network               
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:16 memory:d6000000-d6003fff
  *-network
       description: Ethernet interface
       product: PRO/100 VE Network Connection
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:05:08.0
       logical name: eth0
       version: 02
       serial: 00:1b:24:06:02:cc
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=half firmware=N/A latency=64 link=no maxlatency=56 mingnt=8 multicast=yes port=MII speed=10MB/s
       resources: irq:20 memory:d8000000-d8000fff ioport:4000(size=64)
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:1a:73:50:4e:b0
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
[/html]
That Broadcom 4311 wireless interface should work under ubuntu.  Take a look at this thread for tips:

[http://ubuntuforums.org/showthread.php?t=1336676](http://ubuntuforums.org/showthread.php?t=1336676)

The Intel PRO 100 is an ancient network interface, and I'm surprised that it wouldn't automatically work "out of the box" with any Linux from the last 10 years or so, unless this is some "oddball" version.

Are you sure you aren't having troubles on your ISP or internet side?  That wireless looks to be working properly to me from what you posted, and the Broadcom 4311 is one of the easier ones from what I've seen- maybe the wireless router's "radio" is not broadcasting properly.    Take a look in the router manuals and see if you can find an IP address and username/password to access the router itself.  That is often just typed into a web browser with the newer routers.  Sometimes a "hardware reset" helps, and you sometimes have to poke a small, rigid wire into a hole on the router to do that (but check the documentation first, because that will blow out any custom router settings you might have).

Edit:  Have you got Network Manager (or WiCD) installed?  Do you have that little network icon up at the top of the screen, and what does it say?  Maybe you should take a screenshot of whatever network tools your ubuntu has got and post that.  It might be that your Network Manager has been uninstalled.

If you don't have a network connection, you might need to get the proper .deb packages using another computer with a good network connection and transfer them on a USB stick.   You will want to get the correct packages (32-bit vs. 64-bit, and for your version of ubuntu, etc.).   Ubuntu is usually pretty good about refusing to install the incorrect packages, but I wouldn't count on that 100%.

---

### Post by luomo on 2009-12-06
Thanks northd_tech for your time.
> **northd_tech said:**
> That Broadcom 4311 wireless interface should work under ubuntu.  Take a look at this thread for tips:

[http://ubuntuforums.org/showthread.php?t=1336676](http://ubuntuforums.org/showthread.php?t=1336676)


Actually I have got sbb or STA and wl driver on my Live CD restricted section so I just take these .deb packages and install them on my ubuntu 9.10.
But after installing STA or sbb package (sl-modem-daemon_2.9.11) there is no change at the settings in Network Manager.
But as I install wl driver (bcmwl-kernel-source_5.10.91.9),I lost my all connections and have to put 5 commands by Iowan to get it working and still that doesn't work so I uninstall wl driver and now STA driver is installed already.
4 coomands by Iowan:
sudo modprobe -r b43 b44 ssb wl
sudo modprobe ieee80211_crypt_tkip
sudo modprobe wl
sudo modprobe b44

---

### Post by luomo on 2009-12-06
> **northd_tech said:**
> 
Are you sure you aren't having troubles on your ISP or internet side?  That wireless looks to be working properly to me from what you posted, and the Broadcom 4311 is one of the easier ones from what I've seen- maybe the wireless router's "radio" is not broadcasting properly.    Take a look in the router manuals and see if you can find an IP address and username/password to access the router itself.  That is often just typed into a web browser with the newer routers.  Sometimes a "hardware reset" helps, and you sometimes have to poke a small, rigid wire into a hole on the router to do that (but check the documentation first, because that will blow out any custom router settings you might have).


I am quite sure that there is no problem from ISP side as I am dual booting windows XP and Ubuntu 9.10 and internet is working fine in Windows and I get locked my router settings otherwise I have already changed the configuration. I am already fighting with this problem and in no situation to increase it multifold by resetting the router through that hole.

> 
Edit:  Have you got Network Manager (or WiCD) installed?  Do you have that little network icon up at the top of the screen, and what does it say?
I have network manager installed and its working and I will attach a screen shot of it after a few minutes.

---

### Post by luomo on 2009-12-06
Screen Shots of Network Manager:

---

### Post by luomo on 2009-12-06
**output of netstat -rn:**
[html]
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
[/html][B]
output of netstat -r:[/B]
[html]
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
[/html]**output of route add default gw 169.254.137.187**
[html]
SIOCADDRT: Operation not permitted
[/html]

---

### Post by northd_tech on 2009-12-06
> **luomo said:**
> Thanks northd_tech for your time.

Actually I have got sbb or STA and wl driver on my Live CD restricted section so I just take these .deb packages and install them on my ubuntu 9.10.
But after installing STA or sbb package (sl-modem-daemon_2.9.11) there is no change at the settings in Network Manager.
But as I install wl driver (bcmwl-kernel-source_5.10.91.9),I lost my all connections and have to put 5 commands by Iowan to get it working and still that doesn't work so I uninstall wl driver and now STA driver is installed already.
You should probably try "blacklisting" that "wl" driver (as well as the b43 and any other Broadcom driver except "STA", if the "STA" is the one that you are trying to fix).

If you do a forum search here for blacklist, b43, and Broadcom, you should be able to find at least 1 thread about how and where to blacklist them.  I had to do that with an older ubuntu to get ndiswrapper to work, but that's been over a year ago.

Several people have had very good luck with that proprietary "STA" driver though.  It looks like your WiFi radio is connected and is talking properly to station "UTStarcom" from those screenshots.

Does your connection have anywhere that you could cable in (router, cable modem, etc.)?  

Have you posted the results of these terminal commands here already?

```
ifconfig

iwconfig

lspci

lsusb

lsmod

lshw -C network
```

---

### Post by northd_tech on 2009-12-06
If you can't get any of the Linux drivers to connect, you could always try ndiswrapper and use the Windows drivers (it should already be installed under Karmic Koala 9.10 under System>Administration>Wireless Windows Drivers and then you just point that to the 2 proper *.inf and *.sys Windows files).  I've seen some problems with 64-bit Linux and wireless drivers though (even under Windows with Windows drivers).  XP is a lot better than Vista for driver support though has been my experience. 

You can check whether you're using 32-bit or 64-bit ubuntu by typing:

```
uname -a
```

It should be pretty easy to find the correct Windows drivers for that Broadcom 4311 online.

---

### Post by luomo on 2009-12-06
**Output of ifconfig**:post 22
**output of uname -a**: post 17
**Output of sudo lshw -C network**: post 18
**Result of iwconfig**: post 7

**Output of lsmod:**
[html]

Module                  Size  Used by
binfmt_misc             8356  1 
snd_hda_codec_conexant    20060  1 
snd_hda_intel          26920  2 
snd_hda_codec          75708  2 snd_hda_codec_conexant,snd_hda_intel
snd_hwdep               7200  1 snd_hda_codec
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
ppdev                   6688  0 
snd_pcm                75296  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           2656  0 
joydev                 10272  0 
snd_seq_oss            28576  0 
arc4                    1660  2 
snd_seq_midi            6432  0 
snd_rawmidi            22208  1 snd_seq_midi
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
ecb                     2524  2 
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              22276  2 snd_pcm,snd_seq
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    59204  16 snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
lp                      8964  0 
b43                   122136  0 
soundcore               7264  1 snd
mac80211              181236  1 b43
cfg80211               93052  2 b43,mac80211
iptable_filter          3100  0 
psmouse                56180  0 
serio_raw               5280  0 
snd_page_alloc          9156  2 snd_hda_intel,snd_pcm
led_class               4096  1 b43
ip_tables              11692  1 iptable_filter
x_tables               16544  1 ip_tables
parport                35340  2 ppdev,lp
fbcon                  36640  72 
tileblit                2460  1 fbcon
font                    8124  1 fbcon
bitblit                 5372  1 fbcon
softcursor              1756  1 bitblit
i915                  221064  3 
drm                   159584  3 i915
i2c_algo_bit            5760  1 i915
e100                   32452  0 
mii                     5212  1 e100
ssb                    35300  1 b43
video                  19380  1 i915
output                  2780  1 video
intel_agp              27484  2 i915
agpgart                34988  2 drm,intel_agp

[/html]**Output of lsusb:**
[html]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

[/html]Output of lspci -b:
[html]
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
02:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)
05:08.0 Ethernet controller: Intel Corporation PRO/100 VE Network Connection (rev 02)
[/html]

---

### Post by luomo on 2009-12-06
> **northd_tech said:**
> You should probably try "blacklisting" that "wl" driver (as well as the b43 and any other Broadcom driver except "STA", if the "STA" is the one that you are trying to fix).



Does your connection have anywhere that you could cable in (router, cable modem, etc.)?  


I don't need to blacklist the driver as I have uninstalled wl driver and STA driver is causing no problem to me.
As I have read ndiswrapper and have installed it on my ubuntu but I am unable to get proper .sys and .inf files for it and moreover I have read somewhere that its last option to switch.
Thanks for your help till now and I need it more.

---

### Post by northd_tech on 2009-12-06
> **luomo said:**
> [SIZE=2]My computer scans all the connections wireless or wired and showed it properly but the circle moves and moves on then this comes as written "connection is disconnected"
**output of ifconfig**:
[/SIZE][html]
 eth0      Link encap:Ethernet  HWaddr   
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

wlan0     Link encap:Ethernet  HWaddr   
          inet6 addr: fe80::21a:73ff:fe50:4eb0/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:15 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:3816 (3.8 KB)

wmaster0  Link encap:UNSPEC  HWaddr   
          UP RUNNING  MTU:0  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
[/html][SIZE=2] 
[/SIZE]
Are you still seeing that "wmaster0" interface after running ifconfig?  

You might have a conflict between that and "eth0" network interface.  I've never seen a "wmaster0" network- the "eth0" looks more normal to me.  "Wlan0" is your wireless, and it really looks to be working properly to me- something else must be preventing the connection to the outside world.  "wlan0" has transmitted 15 packets with none dropped (from that older output anyway, unless that has since changed).

It didn't look like anything was transmitted or received on "eth0" or "wmaster0" (probably did not have a network cable connected).

Maybe you should try running this command and then restarting to get your modules straightened out:

```
sudo depmod -a
```

---

### Post by luomo on 2009-12-06
wmaster0 is still appearing in the latest outputs also and I will post after few minutes the output after doing that command.

---

### Post by northd_tech on 2009-12-06
> **luomo said:**
> **Output of ifconfig**:post 22

**Output of lsmod:**

Module                  Size  Used by

[COLOR=Red]b43                   122136  0 [/COLOR]
soundcore               7264  1 snd
[COLOR=Red]mac80211              181236  1 b43
cfg80211               93052  2 b43,mac80211[/COLOR]

[COLOR=Blue]e100                   32452  0 
mii                     5212  1 e100[/COLOR]
[COLOR=Red]ssb                    35300  1 b43[/COLOR]
Output of lspci -b:
[html]
02:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)
05:08.0 Ethernet controller: Intel Corporation PRO/100 VE Network Connection (rev 02)
[/html]
It looks like you've still got that old Broadcom "b43" driver still hanging around.  I'd try to uninstall the Broadcom "STA" driver in System>Admininstration>Hardware Drivers, then run these commands:
```
sudo rmmod b43
sudo rmmod mac80211
sudo rmmod cfg80211
sudo rmmod ssb
```It looks like a module conflict to me with pieces of the old drivers still hanging around.  The red are the wireless modules, and the blue are the Intel Pro 100 modules for "eth0" from what I remember.

Then try reinstalling the "STA" driver under Hardware Drivers.  Also can you post the results of:

```
less /etc/modules
```You will probably need to use "sudo gksu gedit /etc/modules" to comment out (with some of these "#" ) some of those module names too and then restart again.

Edit:  If none of that works you might want to try this Broadcom 4312 thread and what worked there:

[http://ubuntuforums.org/showthread.php?t=1312603](http://ubuntuforums.org/showthread.php?t=1312603)

We are considering going back to 32-bit and ubuntu 9.04 on the 64-bit laptop that I've been working on (its wireless is much more difficult than the Broadcoms though).  I've been hearing from a few people that they don't like ubuntu 9.10 lately, and I seem to recall a 2.6.31-16 kernel that didn't have nearly so many problems for us.

---

### Post by luomo on 2009-12-06
> **northd_tech said:**
> 

Maybe you should try running this command and then restarting to get your modules straightened out:

```
sudo depmod -a
```

[html]
 sudo depmod -a
 
 lsmod
Module                  Size  Used by
binfmt_misc             8356  1 
ppdev                   6688  0 
snd_hda_codec_conexant    20060  1 
joydev                 10272  0 
snd_hda_intel          26920  2 
snd_hda_codec          75708  2 snd_hda_codec_conexant,snd_hda_intel
snd_hwdep               7200  1 snd_hda_codec
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75296  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           2656  0 
snd_seq_oss            28576  0 
arc4                    1660  2 
snd_seq_midi            6432  0 
iptable_filter          3100  0 
snd_rawmidi            22208  1 snd_seq_midi
ecb                     2524  2 
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
ip_tables              11692  1 iptable_filter
b43                   122136  0 
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
psmouse                56180  0 
mac80211              181236  1 b43
snd_timer              22276  2 snd_pcm,snd_seq
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
serio_raw               5280  0 
lp                      8964  0 
parport                35340  2 ppdev,lp
snd                    59204  16 snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
x_tables               16544  1 ip_tables
soundcore               7264  1 snd
cfg80211               93052  2 b43,mac80211
snd_page_alloc          9156  2 snd_hda_intel,snd_pcm
led_class               4096  1 b43
fbcon                  36640  72 
tileblit                2460  1 fbcon
font                    8124  1 fbcon
bitblit                 5372  1 fbcon
softcursor              1756  1 bitblit
i915                  221064  3 
drm                   159584  3 i915
i2c_algo_bit            5760  1 i915
e100                   32452  0 
mii                     5212  1 e100
ssb                    35300  1 b43
video                  19380  1 i915
output                  2780  1 video
intel_agp              27484  2 i915
agpgart                34988  2 drm,intel_agp


[/html]

---

### Post by luomo on 2009-12-06
As you have said I uninstalled STA driver and b43-fwcutter as well and these are the outputs:
**Outputs of rmmod commands:**
[html]
cyber@cyber-laptop:~$ rmmod b43
ERROR: Removing 'b43': Operation not permitted
cyber@cyber-laptop:~$ rmmod mac80211
ERROR: Module mac80211 is in use by b43
cyber@cyber-laptop:~$ rmmod cfg80211
ERROR: Module cfg80211 is in use by b43,mac80211
cyber@cyber-laptop:~$ rmmod ssb
ERROR: Module ssb is in use by b43

[/html]Output of less /etc/modules:
[html]
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp


[/html]

---

### Post by northd_tech on 2009-12-06
Sorry about that- I edited in the "sudo" before those rmmod commands, but it must have gotten lost in the "cross-posting."  I came from the "old school" Linuces where we ran as root and didn't need to type "sudo" or "sudo su" all the time.  The ubuntu does things a little differently, but it's probably safer this way (but a little hard to remember).

Try those "sudo rmmod" commands and then reinstall the "STA" driver.  That Broadcom 4311 is supposed to be very close the 4312.  You might try what worked on these threads too:

[http://ubuntuforums.org/showthread.php?t=1347483](http://ubuntuforums.org/showthread.php?t=1347483)

[http://ubuntuforums.org/showthread.php?t=1266620](http://ubuntuforums.org/showthread.php?t=1266620)

I'm still not sure where that "wmaster0" network interface is getting loaded from (it's not /etc/modules though- you're only loading a lineprinter driver there with the "lp").  It might have "ridden in" on your kernel.  If that wmaster0 interface is "intercepting" your network traffic somehow, that could cause your connection to not work and prevent you from "seeing" the outside world with your "wlan0" (which appears to be talking to the router just fine).  Hopefully someone else has seen this "wmaster0" before or has worked with that Intel Pro 100 VE ethernet interface.

My laptop uses an nVidia nForce (which is modified from the old Intel Pro 100 "eth0" interface as I understand) and it just works "out of the box."  This other Toshiba laptop I've been working on is a complete "oddball," and 64-bit is making everything about 10x worse there.

Try this command from a terminal:

```
ping www.stanford.edu

```

You might need CTRL-C to stop that terminal command from running.

---

### Post by luomo on 2009-12-06
Thanks for helping me upto this point. Its actually late here. So I am going for bed. I will post all the outputs tomorrow. Please Visit this thread tomorrow and help me in solving this issue.
Again thanks a lot.

---

### Post by northd_tech on 2009-12-06
> **northd_tech said:**
> 
I'm still not sure where that "wmaster0" network interface is getting loaded from (it's not /etc/modules though- you're only loading a lineprinter driver there with the "lp").  It might have "ridden in" on your kernel.  If that wmaster0 interface is "intercepting" your network traffic somehow, that could cause your connection to not work and prevent you from "seeing" the outside world with your "wlan0" (which appears to be talking to the router just fine).  Hopefully someone else has seen this "wmaster0" before or has worked with that Intel Pro 100 VE ethernet interface.

Hi luomo,

I just saw someone else with that "wmaster0" network interface- see post #28 here (although his isn't fixed yet either):

[http://ubuntuforums.org/showpost.php?p=8453925&postcount=28](http://ubuntuforums.org/showpost.php?p=8453925&postcount=28)

---

### Post by luomo on 2009-12-07
I have a lot of Data this time and posting it one by one:[B]
Output of dmesg | grep b43 (before):[/B]
[html]
cyber@cyber-laptop:~$ dmesg | grep b43
[    1.431918] b43-pci-bridge 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.431933] b43-pci-bridge 0000:02:00.0: setting latency timer to 64
[    6.671667] b43-phy0: Broadcom 4311 WLAN found (core revision 10)
[   13.492092] b43 ssb0:0: firmware: requesting b43/ucode5.fw
[   13.543564] b43 ssb0:0: firmware: requesting b43/pcm5.fw
[   13.776894] b43 ssb0:0: firmware: requesting b43/b0g0initvals5.fw
[   13.860042] b43 ssb0:0: firmware: requesting b43/b0g0bsinitvals5.fw
[   13.992058] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[   14.064595] Registered led device: b43-phy0::tx
[   14.064621] Registered led device: b43-phy0::rx
[   14.064645] Registered led device: b43-phy0::radio
cyber@cyber-laptop:~$ lspci -vnn | grep 14e4
02:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
[/html]**Output of dmesg |grep b43 (after):**
[html]
cyber@cyber-laptop:~$ dmesg | grep b43
[    1.473626] b43-pci-bridge 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.473641] b43-pci-bridge 0000:02:00.0: setting latency timer to 64
[    7.013959] b43-phy0: Broadcom 4311 WLAN found (core revision 10)
[   15.588075] b43 ssb0:0: firmware: requesting b43/ucode5.fw
[   15.715091] b43 ssb0:0: firmware: requesting b43/pcm5.fw
[   15.756722] b43 ssb0:0: firmware: requesting b43/b0g0initvals5.fw
[   15.787440] b43 ssb0:0: firmware: requesting b43/b0g0bsinitvals5.fw
[   16.004078] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[   16.089612] Registered led device: b43-phy0::tx
[   16.089641] Registered led device: b43-phy0::rx
[   16.089670] Registered led device: b43-phy0::radio

[/html]Before  means before the uninstalling and  after means after reinstalling.
What you see is there any issue with driver as this output is after reinstalling b43-fwcutter and STL driver?

---

### Post by luomo on 2009-12-07
[B]Output of lsmod after reinstalling b43 and STL driver:
[/B][html]
cyber@cyber-laptop:~$ lsmod
Module                  Size  Used by
binfmt_misc             8356  1 
ppdev                   6688  0 
snd_atiixp_modem       11940  0 
snd_via82xx_modem      11204  0 
snd_intel8x0m          13896  0 
snd_ac97_codec        101216  3 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m
ac97_bus                1532  1 snd_ac97_codec
snd_hda_codec_conexant    20060  1 
snd_hda_intel          26920  2 
snd_hda_codec          75708  2 snd_hda_codec_conexant,snd_hda_intel
snd_hwdep               7200  1 snd_hda_codec
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75296  7 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m,snd_ac97_codec,snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           2656  0 
snd_seq_oss            28576  0 
snd_seq_midi            6432  0 
snd_rawmidi            22208  1 snd_seq_midi
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              22276  2 snd_pcm,snd_seq
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
arc4                    1660  2 
iptable_filter          3100  0 
ip_tables              11692  1 iptable_filter
ecb                     2524  2 
joydev                 10272  0 
lp                      8964  0 
x_tables               16544  1 ip_tables
b43                   122136  0 
snd                    59204  20 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m,snd_ac97_codec,snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
parport                35340  2 ppdev,lp
soundcore               7264  1 snd
snd_page_alloc          9156  5 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m,snd_hda_intel,snd_pcm
mac80211              181236  1 b43
cfg80211               93052  2 b43,mac80211
psmouse                56180  0 
led_class               4096  1 b43
serio_raw               5280  0 
fbcon                  36640  72 
tileblit                2460  1 fbcon
font                    8124  1 fbcon
bitblit                 5372  1 fbcon
softcursor              1756  1 bitblit
i915                  221064  3 
drm                   159584  3 i915
i2c_algo_bit            5760  1 i915
e100                   32452  0 
mii                     5212  1 e100
ssb                    35300  1 b43
intel_agp              27484  2 i915
agpgart                34988  2 drm,intel_agp
video                  19380  1 i915
output                  2780  1 video


[/html]

---

### Post by luomo on 2009-12-07
Output of ifconfig does **not **change during all the installing and reinstalling and issue is at the same point means "connection is disconnected".

---

### Post by luomo on 2009-12-07
> **northd_tech said:**
> Hi luomo,

I just saw someone else with that "wmaster0" network interface- see post #28 here (although his isn't fixed yet either):

[http://ubuntuforums.org/showpost.php?p=8453925&postcount=28](http://ubuntuforums.org/showpost.php?p=8453925&postcount=28)

But northd_tech that issue is appearing to be different. His wmaster0 is showing: "wmaster0  no wireless extensions" and my wmaster0 showing a lot of things which is hard to understand for me.

---

### Post by northd_tech on 2009-12-07
The "b43" and "STA" drivers are usually either/or- you don't want to install both of them at the same time.  My Broadcom 4321 has worked/will work with either, but the STA is by far the easiest (and it gives me the faster speed).

Do both the b43 and the "STA" drivers show up in System>Administration>Hardware Drivers?  I remember something about the order that you install/uninstall making a difference.  You only want to "activate" one of those at a time, and we might need to remove one of them completely.

I don't believe that the 4311 needs the 802.11n speed, so the b43 (and "fwcutter") method should be fine if you can get that working.

Any of the methods on these threads should work for the 4311, but just choose only one method and follow it through (we don't want to mix and match them):

HOW-TO: Wi-fi driver install for Broadcom B43 cards
[http://ubuntuforums.org/showthread.php?t=1044898](http://ubuntuforums.org/showthread.php?t=1044898)

How to install native broadcom drivers for  BCM4311, BCM4312, BCM4321, and BCM4322
[http://ubuntuforums.org/showthread.php?t=896713](http://ubuntuforums.org/showthread.php?t=896713)

Broadcom 14e4 4311 problem
[http://ubuntuforums.org/showthread.php?t=1345038](http://ubuntuforums.org/showthread.php?t=1345038)

HOWTO: Use b43 driver with 14e4:4315 (Broadcom bcm4312 rev 01) 
[http://ubuntuforums.org/showthread.php?t=1266620](http://ubuntuforums.org/showthread.php?t=1266620)

There should not be a big difference between the Broadcom 4311 and 4312 wireless interfaces, and the install/setup should be the same (my 4321 will even use the same drivers, but I just use the "STA" in Hardware Drivers).  I haven't used any of the older "b43" modules with either ubuntu 9.04 or 9.10 (but my 9.10 USB install got messed up by updates).

I'll be reinstalling tonight or tomorrow, and I plan on using the "STA" driver only under 9.10 and blacklisting anything else.  That has always been the easiest way for me, but it wasn't available in ubuntu 8.04 that I remember (I was still using ndiswrapper back then with Windows drivers).

---

### Post by luomo on 2009-12-07
> **northd_tech said:**
> T

Do both the b43 and the "STA" drivers show up in System>Administration>Hardware Drivers?  I remember something about the order that you install/uninstall making a difference.  You only want to "activate" one of those at a time, and we might need to remove one of them completely.

northd_tech, Hardwares drivers are appearing in Live CD and first is WL drivera nd after that STA driver. So WL driver doesn't work so I install STA driver but that doesn't work even in Live CD and it shows no b43-fwcutter that means you are right and only one is needed.
But I have first installed b43-fwcutter and checked all the connections and take outputs from terminal but it doesn't help. Then I installed STA driver.
Please help!

---

### Post by uncaspi on 2009-12-07
Funny things these cards. I have 2 Ethernet cards called eth0 and eth1. Then I have an Cisco wireless card which is called eth2 and also wifi0. And when I shall connect manually to the wireless without using nm I have to type dhclient eth2 and NOT dhclient wifi0 
So if you try to see if there is a card called eth1 in your machine try sudo /sbin/ifconfig eth1 up
and if it comes up, check it by sudo /sbin/ifconfig
do dhclient eth1
We have to turn all stones in this issue so give it a try.

---

### Post by luomo on 2009-12-07
Thanks uncaspi for your time. 
I have done sudo /sbin/ifdown wmaster0 and it is of no help and posting some new results.
**Output of lsmod| grep b43:**
[html]
cyber@cyber-laptop:~$ lsmod | grep b43
b43                   122136  0 
mac80211              181236  1 b43
cfg80211               93052  2 b43,mac80211
led_class               4096  1 b43
ssb                    35300  1 b43
[/html]**Output of dmesg | grep ssb0:**
[html]
cyber@cyber-laptop:~$ dmesg | grep ssb0
[   13.104076] b43 ssb0:0: firmware: requesting b43/ucode5.fw
[   13.201606] b43 ssb0:0: firmware: requesting b43/pcm5.fw
[   13.230023] b43 ssb0:0: firmware: requesting b43/b0g0initvals5.fw
[   13.251297] b43 ssb0:0: firmware: requesting b43/b0g0bsinitvals5.fw

[/html]

---

### Post by luomo on 2009-12-07
> **uncaspi said:**
> Funny things these cards. I have 2 Ethernet cards called eth0 and eth1. Then I have an Cisco wireless card which is called eth2 and also wifi0. And when I shall connect manually to the wireless without using nm I have to type dhclient eth2 and NOT dhclient wifi0 
So if you try to see if there is a card called eth1 in your machine try sudo /sbin/ifconfig eth1 up
and if it comes up, check it by sudo /sbin/ifconfig
do dhclient eth1
We have to turn all stones in this issue so give it a try.
I am  trying to turn all the stones. And eth0 and wlan0 are the same names and it doesn't change the things.

---

### Post by uncaspi on 2009-12-07
Have you tried to access the router giving its MAC address? Look at man iwconfig  option ap

---

### Post by luomo on 2009-12-07
I have tried that also but it is not working.
Some strange things which i noticed:
1."wired connection: device not found"- this message comes even after I connect through wired connection to my modem.
2.same service provider and same settings, everything works fine in my Laptop with Windows and also connection works on My friends laptop with ubuntu installed.
I can't understand whether its router problem or driver problem but it is appearing to me drivers are working.

---

### Post by luomo on 2009-12-08
Is here no help for me? Should reinstalling ubuntu could help? Please tell me something that could help me in solving the problem? ](*,)

---

### Post by uncaspi on 2009-12-08
Will you please post the contest of /etc/udev/rules.d/70-persistent-net.rules

---

### Post by luomo on 2009-12-08
**Here is the output of /etc/udev/rules.d/70-persistent-net.rules**:
[HTML]
# This file maintains persistent names for network interfaces.
# See udev(7) for syntax.
#
# Entries are automatically added by the 75-persistent-net-generator.rules
# file; however you are also free to add your own entries.

# PCI device 0x14e4:0x4311 (b43-pci-bridge)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:1a:73:50:4e:b0", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

# PCI device 0x8086:0x1092 (e100)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:1b:24:06:02:cc", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x14e4:0x4311 (wl)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:1a:73:50:4e:b0", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"

[/HTML]

---

### Post by uncaspi on 2009-12-08
It says that eth1 is your wireless card together with wlan0. Then you could try what I suggested in an earlier reply to sudo /sbin/ifconfig eth1 up
then type sudo /sbin/ifconfig to see if the interface is brought up.

---

### Post by uncaspi on 2009-12-08
And comment out (put # in the beginning of the line) the line containing wlan0 and then restart the network sudo /etc/init.d/networking restart
Then sudo /sbin/ifconfig eth1 up
see if its brought up by typing sudo /sbin/ifconfig
If it is brought up then type dhclient eth1

---

### Post by luomo on 2009-12-08
There is one thing on which I want to bring in notice, a message in Network Manager:

> Wired Network
device not managed
and wired network is not automatically detected. and you could see it in the screenshot pic on previous posts in this thread.(page 4,post 41)

**Output of sudo /sbin/ifconfig/eth1 up:**
[html]
cyber@cyber-laptop:~$ sudo /sbin/ifconfig eth1 up
[sudo] password for cyber: 
eth1: ERROR while getting interface flags: No such device
[/html][B]
Output of sudo /sbin/ifconfig:[/B]
[html]
cyber@cyber-laptop:~$ sudo /sbin/ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:1b:24:06:02:cc  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:1a:73:50:4e:b0  
          inet6 addr: fe80::21a:73ff:fe50:4eb0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:2016 (2.0 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-1A-73-50-4E-B0-35-30-00-00-00-00-00-00-00-00  
          UP RUNNING  MTU:0  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


[/html]

---

### Post by luomo on 2009-12-08
> **uncaspi said:**
> And comment out (put # in the beginning of the line) the line containing wlan0 and then restart the network sudo /etc/init.d/networking restart


In which file I have to comment?

---

### Post by uncaspi on 2009-12-08
In /etc/udev/rules.d/70-persistent-net.rules


Then reboot and please post dmesg | grep eth
and dmesg | grep wlan

---

### Post by luomo on 2009-12-08
I have commented as you have said but it doesn't help in bringing up the eth1.
**Output of sudo /sbin/ifconfig eth1 up:**
[html]
cyber@cyber-laptop:~$ sudo /sbin/ifconfig eth1 up
[sudo] password for cyber: 
eth1: ERROR while getting interface flags: No such device
[/html][B]Output of dmesg | grep eth:
[/B][html]
cyber@cyber-laptop:~$ dmesg |grep eth
[    1.549479] e100: eth0: e100_probe: addr 0xd8000000, irq 20, MAC addr 00:1b:24:06:02:cc
[    9.665892] ADDRCONF(NETDEV_UP): eth0: link is not ready

[/html]**Output of dmesg | grep wlan:**
[html]
cyber@cyber-laptop:~$ dmesg |grep wlan
[   15.077392] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   43.784885] wlan0: authenticate with AP 00:1b:57:f4:f7:ef
[   43.786582] wlan0: authenticated
[   43.786588] wlan0: associate with AP 00:1b:57:f4:f7:ef
[   43.790466] wlan0: RX AssocResp from 00:1b:57:f4:f7:ef (capab=0x401 status=0 aid=1)
[   43.790471] wlan0: associated
[   43.791595] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   54.644060] wlan0: no IPv6 routers present
[   88.821787] wlan0: disassociating by local choice (reason=3)

[/html]

---

### Post by uncaspi on 2009-12-08
Then try the opposite. Comment out the line with eth1 and leave the line with wlan0 in it uncommented. Reboot and post dmesg | grep wlan
If it says link is ready (bottom line) try dhclient wlan0 and 
and sudo /sbin/ifconfig wlan0  to see if it got an ip address from the router.

---

### Post by uncaspi on 2009-12-08
From dmesg | grep wlan you see that the link is ready, so I think there is noting wrong with your wireless card. I think it had to do with the handshaking protocol between your DSL modem and the dhclient due to you do not get any ip address from the modem. I would go into windows and google an HOWTO Linux connecting to DSL modem. I doubt a fresh Ubuntu installation will solve the problem.

---

### Post by luomo on 2009-12-09
> **uncaspi said:**
> Then try the opposite. Comment out the line with eth1 and leave the line with wlan0 in it uncommented. Reboot and post dmesg | grep wlan
If it says link is ready (bottom line) try dhclient wlan0 and 
and sudo /sbin/ifconfig wlan0  to see if it got an ip address from the router.
I have commented out the line with eth1 and leave the line with wlan0 in it uncommented.
then I tried to up the signal:
> 
cyber@cyber-laptop:~$ sudo /sbin/ifconfig wlan0 up
then **Output of sudo dhclient wlan0:**
[html]
cyber@cyber-laptop:~$ sudo dhclient wlan0
There is already a pid file /var/run/dhclient.pid with pid 2138
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.2
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan0/00:1a:73:50:4e:b0
Sending on   LPF/wlan0/00:1a:73:50:4e:b0
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 21
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 21
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
[/html][B]Output of dmesg | grep wlan:
[/B][html]
cyber@cyber-laptop:~$ dmesg | grep wlan
[   15.000417] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   43.597017] wlan0: authenticate with AP 00:1b:57:f4:f7:ef
[   43.598713] wlan0: authenticated
[   43.598719] wlan0: associate with AP 00:1b:57:f4:f7:ef
[   43.600904] wlan0: RX AssocResp from 00:1b:57:f4:f7:ef (capab=0x401 status=0 aid=1)
[   43.600908] wlan0: associated
[   43.601923] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   53.964057] wlan0: no IPv6 routers present
[   88.816315] wlan0: disassociating by local choice (reason=3)
[   99.217516] wlan0: authenticate with AP 00:1b:57:f4:f7:ef
[   99.219256] wlan0: authenticated
[   99.219262] wlan0: associate with AP 00:1b:57:f4:f7:ef
[   99.221665] wlan0: RX AssocResp from 00:1b:57:f4:f7:ef (capab=0x401 status=0 aid=1)
[   99.221672] wlan0: associated
[  144.820912] wlan0: disassociating by local choice (reason=3)
[  168.624482] wlan0: authenticate with AP 00:1b:57:f4:f7:ef
[  168.626207] wlan0: authenticated
[  168.626213] wlan0: associate with AP 00:1b:57:f4:f7:ef
[  168.628729] wlan0: RX AssocResp from 00:1b:57:f4:f7:ef (capab=0x401 status=0 aid=1)
[  168.628737] wlan0: associated
[  213.818690] wlan0: disassociating by local choice (reason=3)
[  222.713480] wlan0: authenticate with AP 00:1b:57:f4:f7:ef
[  222.715219] wlan0: authenticated
[  222.715225] wlan0: associate with AP 00:1b:57:f4:f7:ef
[  222.717786] wlan0: RX AssocResp from 00:1b:57:f4:f7:ef (capab=0x401 status=0 aid=1)
[  222.717793] wlan0: associated
[  267.822518] wlan0: disassociating by local choice (reason=3)
[  282.029451] wlan0: authenticate with AP 00:1b:57:f4:f7:ef
[  282.031163] wlan0: authenticated
[  282.031169] wlan0: associate with AP 00:1b:57:f4:f7:ef
[  282.033336] wlan0: RX AssocResp from 00:1b:57:f4:f7:ef (capab=0x401 status=0 aid=1)
[  282.033342] wlan0: associated
[/html][B]Output of sudo /sbin/ifconfig wlan0:
[/B][html]
cyber@cyber-laptop:~$ sudo /sbin/ifconfig wlan0
wlan0     Link encap:Ethernet  HWaddr 00:1a:73:50:4e:b0  
          inet6 addr: fe80::21a:73ff:fe50:4eb0/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:74 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:17838 (17.8 KB)
[/html]

---

### Post by uncaspi on 2009-12-10
Try this link 

[http://www.techotopia.com/index.php/Connecting_an_Ubuntu_Linux_System_to_a_DSL_Modem#Making_the_Connections](http://www.techotopia.com/index.php/Connecting_an_Ubuntu_Linux_System_to_a_DSL_Modem#Making_the_Connections)

or search google keywords +ubuntu +dsl

---

### Post by luomo on 2009-12-10
> **uncaspi said:**
> Try this link 

[http://www.techotopia.com/index.php/Connecting_an_Ubuntu_Linux_System_to_a_DSL_Modem#Making_the_Connections](http://www.techotopia.com/index.php/Connecting_an_Ubuntu_Linux_System_to_a_DSL_Modem#Making_the_Connections)

or search google keywords +ubuntu +dsl
uncaspi, configuring dsl connection is not my problem. My problem is setting up of WiFi connection. My dhcp connnection is not setting up. It tries to connect and then message comes:"Wireless connection is Disconnected".

---

### Post by uncaspi on 2009-12-10
Do you have a router or a DSL modem?

---

### Post by luomo on 2009-12-11
> **uncaspi said:**
> Do you have a router or a DSL modem?
My DSL Modem is router as well.

---

### Post by luomo on 2010-02-12
Do anybody have any solution to my problem? Which other OS should I use if Ubuntu is not working?

---

