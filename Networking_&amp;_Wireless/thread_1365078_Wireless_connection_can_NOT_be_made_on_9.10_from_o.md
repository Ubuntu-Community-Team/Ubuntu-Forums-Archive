---
title: "Wireless connection can NOT be made on 9.10 from older laptops"
date: 2009-12-26
forum: Networking &amp; Wireless
---

### Post by pieguy on 2009-12-26
I'm trying to figure out why "wireless connections" dont work on 9.10(or 9.04) on 2 older laptops I have but does connect wirelessly with 8.10(I presume also on earlier versions) and how to fix it so my laptop can make "wireless connections" on 9.10.

I have a sony vaio pcg-fxa49 with a linksys wpc11 ver.3 wireless card running 8.10 that is able to see and connect to wireless networks(also connects to hidden wireless networks).  I have tried 9.04 and 9.10 on the sony laptop and neither ubuntu version will connect wirelessly.  As a result I reverted that laptop to 8.10 and it connects wirelessly.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=141277&stc=1&d=1261870730[/IMG]
I also have a dell inspiron 1100 with a linksys wpc546 ver.3 wireless card running on 9.10 that is unable to connect wirelessly, it can connect wired.  An assumption I make is that the dell running 8.10 would be able to connect wirelessly(and may be the course of action I take if I can not get 9.10 connecting wirelessly).

Using an updated 9.10 fresh install on the dell, the networkmanager applet does NOT see any wireless networks even when my wireless router is broadcasting and the sony with 8.10 can see and connect wirelessly to the router.  I know that 9.10 on the dell can recognize the linksys wireless card because when I take the wireless card out of the dell the wireless options are gone.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=141278&stc=1&d=1261870730[/IMG]

I surmise that though 9.10 can see the linksys wireless card it has lost its compatibility since 8.10 and no longer works with it.  Also when I attempt to connect manually from the dell wirelessly to my router, on the creation of the wireless network connection it will flash "Network Disconnected you are now offline".  And if I attempt to connect using that created connection the "connect" button is greyed and unclickable.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=141281&stc=1&d=1261871356[/IMG]


If anyoen wishs to help, I will greatly appreciate it and assist as you say.  Though the sony will stay on 8.10, I wont be altering the sony, I only wish to get the dell connecting wirelessly on 9.10.

---

### Post by pieguy on 2009-12-26
```
home@home-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 03)
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 82)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 02)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 02)
02:01.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01)
02:04.0 CardBus bridge: Texas Instruments PCI1510 PC card Cardbus Controller
03:00.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
```

```
home@home-laptop:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 046d:c001 Logitech, Inc. N48/M-BB48 [FirstMouse Plus]
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

```
home@home-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0d:56:e9:f2:16  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:7 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```

```
home@home-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

```
home@home-laptop:~$ lsmod
Module                  Size  Used by
binfmt_misc             8356  1 
ppdev                   6688  0 
arc4                    1660  2 
ecb                     2524  2 
b43                   122136  0 
mac80211              181076  1 b43
cfg80211               93052  2 b43,mac80211
led_class               4096  1 b43
snd_intel8x0           30168  2 
snd_ac97_codec        101216  1 snd_intel8x0
ac97_bus                1532  1 snd_ac97_codec
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75296  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           2656  0 
pcmcia                 36808  0 
iptable_filter          3100  0 
snd_seq_oss            28576  0 
ip_tables              11692  1 iptable_filter
snd_seq_midi            6432  0 
x_tables               16544  1 ip_tables
snd_rawmidi            22208  1 snd_seq_midi
yenta_socket           24200  2 
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
joydev                 10272  0 
rsrc_nonstatic         11644  1 yenta_socket
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
pcmcia_core            35792  3 pcmcia,yenta_socket,rsrc_nonstatic
snd_timer              22276  2 snd_pcm,snd_seq
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    59204  14 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               7264  1 snd
snd_page_alloc          9156  2 snd_intel8x0,snd_pcm
psmouse                56500  0 
shpchp                 32272  0 
dell_wmi                2564  0 
serio_raw               5280  0 
dcdbas                  7292  0 
lp                      8964  0 
parport                35340  2 ppdev,lp
dm_raid45              84228  0 
xor                    15620  1 dm_raid45
fbcon                  36640  72 
tileblit                2460  1 fbcon
font                    8124  1 fbcon
bitblit                 5372  1 fbcon
softcursor              1756  1 bitblit
usbhid                 38208  0 
i915                  221064  2 
drm                   159584  2 i915
i2c_algo_bit            5760  1 i915
b44                    28684  0 
ssb                    35300  2 b43,b44
mii                     5212  1 b44
video                  19380  1 i915
output                  2780  1 video
intel_agp              27484  2 i915
agpgart                34988  2 drm,intel_agp
```

```
home@home-laptop:~$ sudo lshw -C network
[sudo] password for home: 
  *-network               
       description: Ethernet interface
       product: BCM4401 100Base-T
       vendor: Broadcom Corporation
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth0
       version: 01
       serial: 00:0d:56:e9:f2:16
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=half latency=32 link=no multicast=yes port=twisted pair speed=10MB/s
       resources: irq:7 memory:fcffe000-fcffffff
  *-network
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 1
       bus info: pci@0000:03:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64
       resources: irq:11 memory:f8000000-f8001fff
  *-network DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:16:b6:a5:49:d3
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
```

```
home@home-laptop:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Failed to read scan data : Network is down
```

```
home@home-laptop:~$ uname -mr
2.6.31-16-generic i686
```

---

### Post by pieguy on 2009-12-27
```
home@home-laptop:~$ dmesg
[   69.816155] b44: eth0: Link is down.
[  103.305721] b43 ssb1:0: firmware: requesting b43/ucode5.fw
[  103.807396] b43 ssb1:0: firmware: requesting b43-open/ucode5.fw
[  103.830419] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[  103.830427] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found
[  103.830431] b43-phy0 ERROR: You must go to http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware and download the correct firmware for this driver version. Please carefully read all instructions on this website.
[  104.557316] b43 ssb1:0: firmware: requesting b43/ucode5.fw
[  104.575289] b43 ssb1:0: firmware: requesting b43-open/ucode5.fw
[  104.588916] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[  104.588925] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found
[  104.588929] b43-phy0 ERROR: You must go to http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware and download the correct firmware for this driver version. Please carefully read all instructions on this website.
```

Reading some posts I realized it could be this firmware problem, So I followed the instructions at the [link]("http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware").

```
lspci -vnn | grep 14e4
```

My info was [14e4:4318] and is supported using the b43 drivers.

I then

```
sudo apt-get install b43-fwcutter
```
Agreed to fetch and install.

I then find my version kernel and follow the instructions.

[QUOTE=wireless.kernel.org]You are using the b43 driver from linux-2.6.25 or newer

Follow these instructions if you are using the b43 driver from linux-2.6.25 and newer or compat-wireless-2.6, or from any current GIT tree.

Use version 012 of b43-fwcutter.
Download, extract the b43-fwcutter tarball and build it:

```
wget [http://bu3sch.de/b43/fwcutter/b43-fwcutter-012.tar.bz2](http://bu3sch.de/b43/fwcutter/b43-fwcutter-012.tar.bz2)
tar xjf b43-fwcutter-012.tar.bz2
cd b43-fwcutter-012
make
cd ..
```

Use version 4.150.10.5 of Broadcom's proprietary driver.
Download and extract the firmware from this driver tarball:

```
export FIRMWARE_INSTALL_DIR="/lib/firmware"
wget [http://mirror2.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2](http://mirror2.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2)
tar xjf broadcom-wl-4.150.10.5.tar.bz2
cd broadcom-wl-4.150.10.5/driver
sudo ../../b43-fwcutter-012/b43-fwcutter -w "$FIRMWARE_INSTALL_DIR" wl_apsta_mimo.o
```

Note that you must adjust the FIRMWARE_INSTALL_DIR path to your distribution. The standard place where firmware is installed to is /lib/firmware. However some distributions put firmware in a different place. [/QUOTE]

Each line of code above is done individually(or can it be done as a block? I did them individually *shrug).
I changed the FIRMWARE_INSTALL_DIR to /lib/firmware

[COLOR="Blue"]**My dell now sees wireless networks and connects wirelessly.**[/COLOR]

It sucks that 9.04 and later versions lost alot of hardware compatibility "out of the box" because they had to drop certain drivers, no doubt for intellectual property reasons.  IP sucks.

---

### Post by pieguy on 2009-12-28
It turns out that the assumption I make about 8.10 "just working" wirelessly on the dell is wrong.  I notice the same firmware error showing up during live boots of 8.10, 8.04 and 9.04 aswell as kubuntu 8.10.  Plus only 9.10 actually loads succefully on the dell, which I find disturbing because that means linux didnt work on that model till oct this year! and the sony doesnt have any problems with other versions/distros.  That means I still dont know why the sony wont connect wirelessly but I'm happy the way its setup with 8.10 now so I dont need worry about the 9s.

---

### Post by Stewie2kill on 2009-12-30
It looks like you have one of those pesty Air Force One BCM4318 cards. 

I myself am the owner of one right now. If you're happy with your 8.10 setup then all is well and good but I figured I'd throw in something I managed to dig up from the maze of documentation in launchpad.

I was initially having the same exact issues as you in 9.04 but found out that the fwcutter did the job. Then something happened that made me have to nuke my system. I chose 9.10 instead because it was newer but found out (much to my dismay) that the fwcutter tool no longer worked for me.

Instead I was pointed towards ndiswrapper. Initially it was a headache and I almost just gave up completely if it weren't for the handy guide below.

[http://sampbar.com/2009/04/broadcom-bcm4318-ubuntu-intrepid/](http://sampbar.com/2009/04/broadcom-bcm4318-ubuntu-intrepid/)

Step for step, you hardly have to think and for me it got everything working again, despite being designed for Intrepid Ibex. If you ever switch again and have the same issues with that card try the above and see if it works.

---

### Post by SandRat on 2010-01-02
I had a *similar *problem. Here's how I found and solved my specific problem for 9.10 (Karmic) on a 10 year old T21.

I spent 2 days trying to get my old IBM T21 with Linksys WPC54G PCMCIA card to work (the dreaded Air Force One problem). I followed all the information on this forum (mostly redundant as this question is asked over and over), many sources elsewhere (also redundant) and couldn't get it to connect to my Linkssy WRT54G.

Installed ndiswrapper and b43-fwcutter - check

Did ifconfig show proper setup - check

Did iwconfig show proper setup - check

Did lswh -C Network show correct info - check

And on and on.... The card was configured and active, it just wouldn't connect to the router.

My suspicion proved correct, at least as far as I can tell, that the culprit was the security choices for the default network tool do not include a choice for a network that has security disabled. Only WPA, WPA-2, etc. Could this be the issue?

Finally, out of pure frustration, I installed Wicd to see what would happen. BAM! Without doing anything it immediately found my router and connected. Problem solved.

Just goes to show that there can be many different solutions for what appears to be the same or similar problem. The information I was reading and following here and other places was great information, they just didn't solve my particular problem (but most definitely got me closer to a solution).

I'll also say that I really like Wicd. If I plugin via hard cable it turns down my wireless connection and automatically ifconfigs. If I do the reverse, physically unplug, all I have to do is choose a listed wireless network from the tray icon and it connects (if it's open or you have creds to do so). You can even setup different profiles for different wired networks (wireless is scanned automatically so no need for profiles). Great for traveling around.

Hope this can be of use to others searching here for the Broadcom, BCM43xx and/or Air Force One 54G problem.

---

