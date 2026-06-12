---
title: "No Wireless Internet with Realtek RTL-8185 in Ubuntu 10.04"
date: 2010-05-12
forum: Networking &amp; Wireless
---

### Post by mvanderlaen on 2010-05-12
Dear readers,

**I’m not able to establish a Wireless Internet connection in Ubuntu 10.04.**

_I’ve tried these steps_:
1. Wireless Internet did not show via the Network-icon. Only the 2 LAN-gates where shown
2. I installed the Windows Driver (net8185.inf) via ndisgtk package
3. After restarting the computer, 2 LAN-gates and 1 WLAN where listed via the Network-icon
4. Normally WLAN should automatically start scanning for available networks, but that didn’t happen
5. When I tried to connect to my own network, the computer tries to connect for 1 minute and than stops because no connection could be established
6. A wired Internet-connection does not give any problems

_Details_:
- I first had Ubuntu 9.10 but I wasn’t able to make a WLAN connection either. I followed the same steps. After that I upgraded to 10.04
- iwconfig in Terminal gives an IP-address which consists of 12 identical characters.
- lspci in Terminal shows these data:
01:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5787M Gigabit Ethernet PCI Express (rev 02)
02:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5787M Gigabit Ethernet PCI Express (rev 02)
03:0f.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller (rev 20)

- sudo lshw -C network in Terminal does not show any of these words: "CLAIMED, UNCLAIMED, ENABLED or DISABLED" (source: [https://help.ubuntu.com/10.04/internet/C/troubleshooting-wireless.html#troubleshooting-wireless-device](https://help.ubuntu.com/10.04/internet/C/troubleshooting-wireless.html#troubleshooting-wireless-device))


_My questions_:
- How to create an Internet connection via my WLAN-card?
- How to install the option to search for available networks automatically?

Many thanks for your help!

---

### Post by PouncingAnt on 2010-06-18
I'm having the exact same symptoms, did you get anywhere with this?

I used to have to use the acpi=off (or pci=noacpi, or similar, I forget which) on boot to get wireless, but this doesn't work anymore (I just get messages saying "disabling IRQ #1" etc.)

As you say, there is no "CLAIMED, UNCLAIMED, ENABLED or DISABLED" anywhere when using sudo lshw -C network.

I should say I'm using the rtl8187 driver (according to nm-tool, lshw doesnt tell me the driver either). But, I suspect our problems are the same.

---

### Post by leorolla on 2010-06-18
Just a try:

Remove the driver from ndisgtk and ndiswrapper.
Reboot.
Run lsmod and check there is no ndiswrapper there.
Run sudo modprobe tg3
If there is no tg3 module, you can download the zip file from
[http://zh-tw.broadcom.com/support/ethernet_nic/netlink.php](http://zh-tw.broadcom.com/support/ethernet_nic/netlink.php)
read the README.TXT file and follow the instructions.

Hope it works.

---

### Post by Pithikos on 2010-06-28
Leorolla I tried what you suggested but with no luck :/ The thing with most sucess was with loading manually the rlt8180 with the command ```
sudo modprobe rlt8180
```
But that just made the network manager to show the available wireless connections. Tryied many times to connect but with no sucess.
Drives me crazy that I bought 4 wifi cards and now I can't seem to make them work with Linux.

---

### Post by gilbh on 2010-06-29
I have sort of or maybe have the same problem I have been working on this problem for a couple weeks and still do not have internet access. I have tried numerous fixes nothing worked. The only fix that even seemed to help was disabling ipv6 my wireless would connect to the router momentarily untill i would try to open firefox then it would disconnect automatically. then to even get connection back to router i would have to restart. after disabling ipv6 this seemes to have changed and it doesn`t disconnect when starting firefox but still no internet. i can ping [www.google.com]("http://www.google.com") just fine and i can also ping it by ip address just fine. I am a beginner to linux but i have always wanted to try it so i did a complete format and install on a dell box i really wish someone could come up with a fix that works.

---

### Post by leorolla on 2010-06-29
> **Pithikos said:**
> Leorolla I tried what you suggested but with no luck :/ 

And what does it mean exactly?

Were you able follow all the steps, compile/install the driver, rebuild the kernel, etc, etc, reboot, load the module without error messages?

Could you show us the output of
```
lspci -vnn | grep 14e4
```

If you get 14e4:4328 then these may help you:
[http://ubuntuforums.org/showthread.php?t=1512254](http://ubuntuforums.org/showthread.php?t=1512254)
[http://ubuntuforums.org/showpost.php?p=9223467&postcount=21](http://ubuntuforums.org/showpost.php?p=9223467&postcount=21)

---

### Post by Pithikos on 2010-06-29
That command didn't work for me so I tried just **lspci** and I found this line in the output: ```
01:0a.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller (rev 20)
```And I was wrong I think. It must have been the rtl8180 that made my card work a bit. Though when I tried today it showd all area connections but wasn't able to connect at all. Yesterday I achieved to connect at some point but was stuck to 2Mbps and the signal was too low. Made browsing seem like you were on a 56k.

Somehow yesterday night(after a whole day searching and experimenting) my internet worked as a charm but it was only for then. When I restarted my previous problems reappeared. In that stage when it worked as good as in Windows I ran some commands that I remembered from the whole day and saved their output in a txt file in case they can be of any help:

```
>ifconfig

wlan0     Link encap:Ethernet  HWaddr 00:27:19:c1:9d:ad  
          inet addr:192.168.1.103  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::227:19ff:fec1:9dad/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:18718 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14768 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:22949993 (22.9 MB)  TX bytes:4525600 (4.5 MB)





>lsmod

Module                  Size  Used by
arc4                    1473  2 
rtl8180                30082  0                                           ¤HERE¤
mac80211              243373  1 rtl8180
eeprom_93cx6            1765  1 rtl8180
cfg80211              152987  2 rtl8180,mac80211
nls_utf8                1421  1 
isofs                  33399  1 
snd_hda_codec_realtek   278890  1 
binfmt_misc             7960  1 
vboxnetadp              5171  0 
vboxnetflt             15064  0 
vboxdrv              1792472  2 vboxnetadp,vboxnetflt
hid_a4tech              2518  0 
snd_hda_intel          25645  4 
snd_hda_codec          85727  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               6924  1 snd_hda_codec
snd_pcm_oss            41394  0 
snd_mixer_oss          16299  1 snd_pcm_oss
snd_pcm                87850  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1782  0 
snd_seq_oss            31219  0 
snd_seq_midi            5829  0 
snd_rawmidi            23388  1 snd_seq_midi
snd_seq_midi_event      7267  2 snd_seq_oss,snd_seq_midi
snd_seq                57417  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
ppdev                   6375  0 
snd_timer              23553  2 snd_pcm,snd_seq
snd_seq_device          6824  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
parport_pc             29958  1 
usbhid                 40988  0 
ohci1394               30260  0 
snd                    70978  20 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
fbcon                  39270  72 
tileblit                2487  1 fbcon
font                    8053  1 fbcon
bitblit                 5811  1 fbcon
softcursor              1565  1 bitblit
ndiswrapper           244768  0                                            ¤HERE¤
lp                      9336  0 
edac_core              45423  0 
edac_mce_amd            9214  0 
nvidia               8096262  54 
vga16fb                12757  1 
vgastate                9857  1 vga16fb
i2c_nforce2             6099  0 
soundcore               8052  1 snd
snd_page_alloc          8500  2 snd_hda_intel,snd_pcm
parport                37160  3 ppdev,parport_pc,lp
hid                    83376  2 hid_a4tech,usbhid
ieee1394               94675  1 ohci1394
r8169                  39650  0                                     
mii                     5237  1 r8169
sata_nv                23778  2 
pata_amd               11962  1 

```The "¤HERE¤" annotations are just mine. The network manager was not running and the driver loaded with Windows Wireless Driver was net8185(I think Vista64 but not sure). I run Ubuntu 10.04 x64. I run the wireless network so that anyone can connect to it. My wifi cards are TL-WN353GD so I guess those links are not suitable to provide any help for my card :/

---

### Post by leorolla on 2010-06-29
Could you reboot and run
```
sudo lshw -C network
lsmod
cat /etc/modules
grep rtl /etc/modprobe.d/*
grep mac /etc/modprobe.d/*
grep ndis /etc/modprobe.d/*

```

Just to see which modules are being loaded...

Maybe they are conflicting.

---

### Post by tjose on 2010-06-29
Hi 

My laptop (Thinkpad T410i) too have a RealTek wireless driver (not RTL-8185) called RTL-8192. I too have the same problem. From /var/log/syslog the following message is given;

Jun 29 17:54:09 jose NetworkManager: <info>  (wlan0): supplicant interface state:  starting -> ready
Jun 29 17:54:09 jose NetworkManager: <info>  (wlan0): device state change: 2 -> 3 (reason 42)

and it refuse to go to any other state.

Any pointers will be useful 
TIA
Jose

---

### Post by Pithikos on 2010-06-29
At the moment I blacklisted *ndivwrapper* and *rtl8180* to try and install the rtl8185 driver for Linux. That didn't work at all. With ifconfig wlan doesn't show at all. Here's the output from the commands you gave me:

```

**>sudo lshw -C network**
  *-network UNCLAIMED     
       description: Ethernet controller
       product: RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: a
       bus info: pci@0000:01:0a.0
       version: 20
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=64 maxlatency=64 mingnt=32
       resources: ioport:d800(size=256) memory:dfeff400-dfeff5ff
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 03
       serial: 40:61:86:c0:e3:ee
       size: 1GB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.102 latency=0 link=yes multicast=yes port=MII speed=1GB/s
       resources: irq:27 ioport:e800(size=256) memory:dcfff000-dcffffff(prefetchable) memory:dcff8000-dcffbfff(prefetchable) memory:dffe0000-dfffffff(prefetchable)
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes




**>lsmod**
nls_utf8                1421  1 
isofs                  33399  1 
snd_hda_codec_realtek   278890  1 
binfmt_misc             7960  1 
vboxnetadp              5171  0 
vboxnetflt             15064  0 
vboxdrv              1792472  2 vboxnetadp,vboxnetflt
ppdev                   6375  0 
snd_hda_intel          25645  2 
snd_hda_codec          85727  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               6924  1 snd_hda_codec
snd_pcm_oss            41394  0 
snd_mixer_oss          16299  1 snd_pcm_oss
snd_pcm                87850  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1782  0 
snd_seq_oss            31219  0 
snd_seq_midi            5829  0 
snd_rawmidi            23388  1 snd_seq_midi
snd_seq_midi_event      7267  2 snd_seq_oss,snd_seq_midi
snd_seq                57417  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23553  2 snd_pcm,snd_seq
snd_seq_device          6824  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    70978  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
parport_pc             29958  1 
fbcon                  39270  72 
tileblit                2487  1 fbcon
font                    8053  1 fbcon
bitblit                 5811  1 fbcon
softcursor              1565  1 bitblit
soundcore               8052  1 snd
edac_core              45423  0 
edac_mce_amd            9214  0 
nvidia               8096262  24 
snd_page_alloc          8500  2 snd_hda_intel,snd_pcm
vga16fb                12757  1 
i2c_nforce2             6099  0 
vgastate                9857  1 vga16fb
lp                      9336  0 
parport                37160  3 ppdev,parport_pc,lp
hid_a4tech              2518  0 
usbhid                 40988  0 
hid                    83376  2 hid_a4tech,usbhid
ohci1394               30260  0 
ieee1394               94675  1 ohci1394
r8169                  39650  0 
mii                     5237  1 r8169
pata_amd               11962  1 
sata_nv                23778  2 




**>cat /etc/modules**
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
rtc 





**>grep rtl /etc/modprobe.d/***
/etc/modprobe.d/blacklist.conf:blacklist rtl8180





**>grep mac /etc/modprobe.d/***
/etc/modprobe.d/blacklist-oss.conf:blacklist dmasound_pmac
/etc/modprobe.d/blacklist-watchdog.conf:blacklist machzwd




**>grep ndis /etc/modprobe.d/***
/etc/modprobe.d/blacklist.conf:blacklist ndiswrapper
/etc/modprobe.d/ndiswrapper:alias pci:v000010ECd00008180sv*sd*bc*sc*i* ndiswrapper
/etc/modprobe.d/ndiswrapper:alias pci:v000010ECd00008185sv000013F2sd000010BDbc*sc*i* ndiswrapper
/etc/modprobe.d/ndiswrapper:alias pci:v000010ECd00008185sv000014F2sd000010BDbc*sc*i* ndiswrapper
/etc/modprobe.d/ndiswrapper:alias pci:v000010ECd00008185sv00006165sd000018E8bc*sc*i* ndiswrapper
/etc/modprobe.d/ndiswrapper:alias pci:v000010ECd00008185sv00008225sd000010ECbc*sc*i* ndiswrapper
/etc/modprobe.d/ndiswrapper:alias pci:v000010ECd00008185sv00008255sd000010ECbc*sc*i* ndiswrapper
/etc/modprobe.d/ndiswrapper:alias pci:v000010ECd00008185sv*sd*bc*sc*i* ndiswrapper

```

Maybe it was the conflict that made my wifi work yesterday? That is pure luck :p

---

### Post by leorolla on 2010-06-29
Good.

Let's backup and remove ndiswrapper:
```
cp /etc/modprobe.d/ndiswrapper ~ && sudo rm /etc/modprobe.d/ndiswrapper

```

Now reboot.

Let's load module rtl8187, which is the driver for your device according to the kernel documentation:
```
sudo modprobe rtl8187
```

And see what happens.

By the way, you know why this "rtc" line is on /etc/modules ?

---

### Post by Pithikos on 2010-06-29
Well I have some good news :) I just did the first line, rebooted and my network card was running just great! I disabled r8185b(which I guess is the realtek driver for linux) and I loaded rtl8187 instead but that just made things worse. So I just disabled it and tryied to load r8185b again and YAY! Worked again! I get right percentage of signal and the speed is realistic for my connection.

Leo thanks mate. As about that rtc I don't know. I was frustrated yesterday so installed a bunch of stuff so I'm not so sure thus I am kind of new in serious linux. I run some command yesterday: [COLOR=Red]sudo apt-get install linux-backports-*modules*-* [COLOR=Black]so maybe it's from that? I also got some notify message about broken packets and in bootup now, [/COLOR][/COLOR][COLOR=Red][COLOR=Black]except the generic options[/COLOR][/COLOR][COLOR=Red][COLOR=Black], it shows server and emppt(or how it's spelled), plus I don't seem to be able to switch user at the moment. I just will search further to solve these issues. I am happy enough to have wireless internet :guitar:

For others having problem getting rtl8185 to work follow the instructions in [http://ubuntuforums.org/showthread.php?p=9526548](http://ubuntuforums.org/showthread.php?p=9526548) and if you tryied the ndiswrapper method before that, just add[/COLOR][/COLOR]
```
sudo cp /etc/modprobe.d/ndiswrapper ~ && sudo rm /etc/modprobe.d/ndiswrapper
```[COLOR=Red][COLOR=Black] Make sure r8185b is running without any other modules(ndiswrapper, rtl8185). It worked for me :D
[/COLOR][/COLOR]

---

### Post by leorolla on 2010-06-30
Nice!!!

Could you run again the commands from post #8 ?

Just to be sure of what is running there so it can help others...

In my 10.04 there is no module called rtl8185b.

---

### Post by Pithikos on 2010-06-30
r8185b is not from the kernel. It's a 3d party driver from realtek. You can get it from here: [http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=1&PFid=1&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true#RTL8185L](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=1&PFid=1&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true#RTL8185L)
I had some issues compiling/installing the driver so I followed the instructions given here: [http://ubuntuforums.org/showthread.php?p=9526548](http://ubuntuforums.org/showthread.php?p=9526548) (post #4)
After that I just made sure that only the installed driver(r8185b) was running and it worked fine. I still got some small issues on my pc today but it must be because I have been messing up too much with the OS to fix the problem. In an other pc it still works perfect so I ran the commands at that pc and here are the results:

```
**> sudo lshw -C network**
  *-network               
       description: Wireless interface
       product: RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 4
       bus info: pci@0000:01:04.0
       logical name: wlan0
       version: 20
       serial: 00:27:19:c1:a6:86
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8185B ip=192.168.1.105 latency=64 maxlatency=64 mingnt=32 multicast=yes wireless=802.11bg linked
       resources: irq:18 ioport:d800(size=256) memory:feaffc00-feaffdff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 01
       serial: 00:25:11:52:07:6c
       size: 10MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
       resources: irq:27 ioport:e800(size=256) memory:febff000-febfffff memory:febc0000-febdffff(prefetchable)

**> lsmod**
Module                  Size  Used by
btrfs                 458906  0 
zlib_deflate           19568  1 btrfs
crc32c                  2519  1 
libcrc32c                875  1 btrfs
ufs                    72774  0 
qnx4                    6484  0 
hfsplus                70800  0 
hfs                    40754  0 
minix                  25197  0 
ntfs                   94791  0 
vfat                    8901  0 
msdos                   6392  0 
fat                    47767  2 vfat,msdos
jfs                   172650  0 
xfs                   513904  0 
exportfs                3437  1 xfs
reiserfs              225633  0 
binfmt_misc             6587  1 
ppdev                   5259  0 
snd_hda_codec_realtek   203168  1 
snd_hda_intel          21877  5 
snd_hda_codec          74201  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70662  4 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26726  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
fbcon                  35102  72 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
snd                    54148  21 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
nvidia               7087672  38 
soundcore               6620  1 snd
usb_storage            39425  0 
r8185b                172928  0 
psmouse                63245  0 
serio_raw               3978  0 
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
agpgart                31724  1 nvidia
vga16fb                11385  1 
vgastate                8961  1 vga16fb
i2c_nforce2             5199  0 
lp                      7028  0 
parport                32635  2 ppdev,lp
usbhid                 36110  0 
hid                    67032  1 usbhid
ahci                   32008  2 
r8169                  33884  0 
mii                     4381  1 r8169
pata_amd                8766  0 

**> cat /etc/modules**
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp

[B]>grep rtl /etc/modprobe.d/*

> grep mac /etc/modprobe.d/*[/B]
/etc/modprobe.d/blacklist-oss.conf:blacklist dmasound_pmac
/etc/modprobe.d/blacklist-watchdog.conf:blacklist machzwd

**> grep ndis /etc/modprobe.d/***
```

---

### Post by leorolla on 2010-06-30
Oh, OK.

So all you need to do was to follow
[http://ubuntuforums.org/showpost.php?p=8735769&postcount=4](http://ubuntuforums.org/showpost.php?p=8735769&postcount=4)

and not try and mess up with ndiswrapper.

---

### Post by alpeterson on 2010-08-01
I just bought a PCI card with this chipset

It didn't work at first.
  -- It didn't show up in the network manager...

Well, it turns out that the network manager wasn't running!

I started the network manager, and my RTL-8185 worked with the RTL-8180 driver that was automatically detected for it.

I am using WPA2
Kubuntu 10.04

---

### Post by tiggers on 2010-12-19
> **Pithikos said:**
> Well I have some good news :) I just did the first line, rebooted and my network card was running just great! I disabled r8185b(which I guess is the realtek driver for linux) and I loaded rtl8187 instead but that just made things worse. So I just disabled it and tryied to load r8185b again and YAY! Worked again! I get right percentage of signal and the speed is realistic for my connection.

Leo thanks mate. As about that rtc I don't know. I was frustrated yesterday so installed a bunch of stuff so I'm not so sure thus I am kind of new in serious linux. I run some command yesterday: [COLOR=Red]sudo apt-get install linux-backports-*modules*-* [COLOR=Black]so maybe it's from that? I also got some notify message about broken packets and in bootup now, [/COLOR][/COLOR][COLOR=Red][COLOR=Black]except the generic options[/COLOR][/COLOR][COLOR=Red][COLOR=Black], it shows server and emppt(or how it's spelled), plus I don't seem to be able to switch user at the moment. I just will search further to solve these issues. I am happy enough to have wireless internet :guitar:

For others having problem getting rtl8185 to work follow the instructions in [http://ubuntuforums.org/showthread.php?p=9526548](http://ubuntuforums.org/showthread.php?p=9526548) and if you tryied the ndiswrapper method before that, just add[/COLOR][/COLOR]
```
sudo cp /etc/modprobe.d/ndiswrapper ~ && sudo rm /etc/modprobe.d/ndiswrapper
```[COLOR=Red][COLOR=Black] Make sure r8185b is running without any other modules(ndiswrapper, rtl8185). It worked for me :D
[/COLOR][/COLOR]


I followed everything in those instructions, but my network manager connections now, has:
 ifupdown (eth0)
ifupdown (wlan0)

in the Wired tab.

Not sure what went wrong?

Thanks in advance,
Tiggers

---

