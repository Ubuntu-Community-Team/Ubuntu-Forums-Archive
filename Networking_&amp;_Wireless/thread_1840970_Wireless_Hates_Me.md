---
title: "Wireless Hates Me"
date: 2011-09-08
forum: Networking &amp; Wireless
---

### Post by Densetsu on 2011-09-08
Yesterday I downloaded and installed Ubuntu 10.4, and when I turned it on today (via dual-boot system) it seemed to work fine. The one thing that didn't work was the internet connection. It works well on my Windows XP, but as soon as I switch to Ubuntu, nothing happens to my internet.

I've tried it wired and wireless, but both return negative results. I've spent the whole morning trying to find a solution online, but I cannot find any help. If someone could aid me with my problem, I would greatly appreciate it.

Thank you.

---

### Post by rcayea on 2011-09-08
Do you know what kind of wireless card you have? 

Maybe a driver problem?

Try this link:[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)

---

### Post by wildmanne39 on 2011-09-08
Hi, I will see if I can help it is much harder to get wireless working when you do not have a wired connection.

Please run these commands in a terminal and post the results:
```
sudo lshw -C network
```
```
lspci -nn | grep -e 0280 -e 0200 
```
```
iwconfig
```
```
rfkill list all
```
```
lsmod
```
by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by Densetsu on 2011-09-08
@rcayea Not really; my wireless is built into the laptop.

@wildmanne39

```
sudo lshw -C network
[CODE]*-network
description: Network controller
product: BCM4322 802.11a/b/g/n Wireless LAN Controller
vendor: Broadcom Corporation
physical id: 0
bus info: pci@0000:03:00.0
version: 01
width: 64 bits
clock: 33HMz
capabilities: pm msi pciexpress bus_master cap_list
configuration: driver=b43-pci-bridge latency=0
resources: irq:17 memory:f0100000-f0103fff
*-network
description: Ethernet interface
product: RTL8101E/RTL9102E PCI Express Fast Ethernet controller
vendor: Realktek Semiconductor Co., Ltd.
physical id: 0
bus info: pci@0000:04:00.0
logical name: eth0
version: 02
serial: 00:26:b9:a1:b9:37
size: 10MB/s
capacity: 100MB/s
width: 64 bits
clock: 33MHz
capabilities:  pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp  mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
configuration:  autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI  duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
resources:  irq:27 ioport:2000(size=256) memory:f051000-f0510fff(prefetchable)  memory=f0500000-f050ffff(prefetchable)  memory:f0520000-f053ffff(prefetchable)
```[/CODE]```
lspci -nn | grep -e 0280 -e 0200
[CODE]03:00.0 Network controller [0280]: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller [14e4:432b] (rev 01)
04:00.0  Ethernet controller [0200]: Realtek Semiconductor Co., Ltd.  RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev   02)
```[/CODE]```
iwconfig
[CODE]lo         no wireless extensions.
eth0     no wireless extensions.
```[/CODE]```

rfkill list all
[CODE]0: compal=wifi: Wireless LAN
Soft blocked: no
Hard blocked: no
1: compal-bluetooth: Bluetooth
Soft blocked: no
Hard blocked: no
```[/CODE]```

lsmod
[CODE]
Module                              Size    Used by
binfmt_misc                       6587   1
ppdev                               5259    0
joydev                              8740    0
snd_hda_codec_realtek      203376    1
fbcon                                35102    71
tileblit                               1999    1 fbcon
font                                  7557    1 fbcon
bitblit                                4707    1 fbcon
softcursor                         1189     1 bitblit
vga16fb                            11385    0
vgastate                           8961    1 vga16fb
snd_hda_intel                    22069    2
snd_hda_codec                  74201    2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep                        5412    1 snd_hda_codec
snd_pcm_oss                     35308    0
snd_mixer_oss                   13746    1 snd_pcm_oss
snd_pcm                            70694    3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy                 1338    0
snd_seq_oss                       26722    0
snd_seq_midi                      4557    0
snd_rawmidi                       19056    1 snd_seq_midi
dell_wmi                             1793    0
snd_seq_midi_event            6003    2 snd_seq_oss,snd_seq_midi
snd_seq                              47263    6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer                           19098    2 snd_pcm,snd_seq
snd_seq_device                   5700    5 snd_seq_dummy,snd_seq_oss,snd_seq,midi,snd_rawmidi,snd_seq
b43                                    163556    0
i915                                   288611    3
mac80211                           205402    1 b43 
compal_laptop                     2034    0
drm_kms_helper                  29329    1 i915
snd                                      54255    16  snd_hda_codec_realktek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
dcdbas                                5211    0
uvcvideo                             57374   0
cfg80211                            126144    2 b43,mac80211
drm                                   162377    4 i915,drm_kms_helper
videodev                            34361    1 uvcvideo
v4l1_compat                       63677     0
psmouse                             63677    0
serio_raw                            3978    0
led_class                             2864    1 b43
soundcore                           6620    1 snd
intel_agp                             24375    2 i915
agpgart                               31724    2 drm,intel_agp
i2c_algo_bit                         5028    1 i915
snd_page_alloc                    7076    2 snd_hda_intel,snd_pcm
video                                  17375    1 i915
output                                 1871    1 video
lp                                        7028    0
parport                               32635    2 ppdev,lp
usbhid                                36110    0
hid                                     67288    1 usbhid
usb_storage                        39841    0
r8169                                 34140    0
mii                                      4381   1 r8169
ssb                                    38934    1 b43

```[/CODE]

---

### Post by praseodym on 2011-09-08
Hello,

load the driver for wired by hand:

```
sudo modprobe -v r8169
sudo depmod -a
sudo update-initramfs -u
sudo service network-manager restart
```

For wireless:

If wired works, go to System->Settings->Hardware drivers and activate the Broadcom-STA-driver.

If wired doesnt work:
Put the installation CD/DVD into the drive and add it to your software sources. Install from CD the packages dkms, patch, fakeroot, and bcmwl-kernel-source. After that:

```
sudo depmod -a
```

and activate the driver. You may reboot after all of that and show:

```
lspci -nnk | grep -iA2 net
ifconfig -a
iwconfig
lsmod
rfkill list
route -n
sudo iwlist scan
```

---

### Post by wildmanne39 on 2011-09-08
Hi, I see you are in good hands, sorry it took me so long to get back to you I have been researching an issue for another user.
Thank you

---

### Post by bkratz on 2011-09-08
@praseodym

According to the OP's module list he already has r8169 loaded. Is this one of those that needs the 8168???

---

### Post by praseodym on 2011-09-08
Oh, I didnt see that.

No, the device ID is [10ec:8136], you need the r**8168** for [10ec:**8168**].

---

### Post by Densetsu on 2011-09-09
@wildmanne39 It's okay. Thanks anyways~

@praseodym I tried all three r81XX, but they didn't do anything.

 	```
sudo modprobe -v r8169
[CODE]WARNING: All config files need .conf: /etc./modprobe.d/bad_list, is will be ignored in a future release
```[/CODE][FONT=monospace]

[/FONT]```
sudo modprobe -v r8168
[CODE]WARNING: All config files need .conf: /etc./modprobe.d/bad_list, is will be ignored in a future release
FATAL: Module r8168 not found.
```[/CODE][FONT=monospace]

[/FONT]```
sudo modprobe -v r8136
 [CODE]WARNING: All config files need .conf: /etc./modprobe.d/bad_list, is will be ignored in a future release
FATAL: Module r8136 not found.
```[/CODE][FONT=monospace]
[/FONT][FONT=monospace]
[/FONT]```
sudo depmod -a
```
^ Returned nothing

```
sudo update-initramfs -u
[CODE]update-initramfs: Generating /boot/initrd.img-2.6.32-33-generic
```[/CODE]

```
sudo service network-manager restart
[CODE]network-manager start/running, process 5620
```[/CODE]
 	 
Wired didn't work, so I inserted the installation CD into the drive. It was in my Software Sources. I went into the Synatic Package Manager, but I could not find the packages I needed to install.

I've never used Ubuntu before, so I may have messed up somewhere important.

---

### Post by wildmanne39 on 2011-09-09
Hi, so did you get both connections working? one? or none? please let me know.
Thank you

---

### Post by Densetsu on 2011-09-09
No, I could not get any of my connections working. I'm pretty sure I messed up somewhere; I could not find the correct packages to install from the CD.

---

### Post by wildmanne39 on 2011-09-09
Hi, I just helped someone two days ago with this same issue here are the directions, I know they were already given to you but they might not have been explained clear enough.

Hi, I have been researching your wireless card this is what you need.
> broadcom-sta-source + broadcom-sta-common only
You need to open synaptic then click on settings, repositories and put a check by cdrom so when you put in your livecd you will be able to install from it the packages you need.

Then type in bcm or broadcom and remove anything with a green square by it. 

Then restart your computer after you get booted back up put the livecd in and open synaptic install the two packages I mentioned earlier.

Also you will need to click on additional or restricted drivers and activate the driver.

Then remove your livecd and if you have your wired connection plugged in even though it is not working please unplug it and restart your computer and you should be able to enter your wireless key for your router, if not post back and we will go from there.
Thank you

---

### Post by wildmanne39 on 2011-09-09
Hi, here is the screen shot I wanted to give you.
Thank you

---

### Post by madmagik on 2011-09-09
any advice on how to get my darned wnda3100 v2 wireless dongle working? runnung blackbuntu

---

### Post by Densetsu on 2011-09-09
Okay, thanks, Wildmanne! I'll try that out when I have the time (should be soon).

---

### Post by wildmanne39 on 2011-09-09
> **madmagik said:**
> any advice on how to get my darned wnda3100 v2 wireless dongle working? runnung blackbuntu
Hi, I have never used ndiswrapper but this is the only way to get this adapter to work in ubuntu here is a link.
[http://www.iheartubuntu.com/2010/10/netgear-wnda3100-usb-in-ubuntu.html](http://www.iheartubuntu.com/2010/10/netgear-wnda3100-usb-in-ubuntu.html)

If you need more help please start your on thread with a good title and someone should be able to help you install it, I do know that you will also need to get the windows driver from xp the drivers from later windows do not work.
Thank you

---

### Post by Densetsu on 2011-09-09
I put a check by the CDrom in the Repositories, but when I try to activate, I get this error:

```
SystemError: Failed to fetch cdrom:[Ubuntu 10.04.3 LTS _Lucid Lynx_ - Release i386 (20110720.1)]/pool/main/b/b43-fwcutter_012-1build1_i386/deb Disk not found.
```

	 	 		 			 				```
broadcom-sta-source + broadcom-sta-common only 			 		
```
^ Also I could not find these packages

Thanks for your help~

---

### Post by wildmanne39 on 2011-09-09
Hi, here is a link with exact directions to install the packages you need from the cd, start with post 26.
[http://ubuntuforums.org/showthread.php?t=1838927&page=3](http://ubuntuforums.org/showthread.php?t=1838927&page=3)
Thank you

---

### Post by Densetsu on 2011-09-10
Well, I finally got those packages installed, but whenever I activate the Broadcom B43 Wireless Driver, everything freezes and I have to force turn off the computer.

Running into problems one after another. 0_-

---

### Post by wildmanne39 on 2011-09-10
Hi, now that you have installed the driver please post the results of these commands: 
```
lsmod
```
```
nm-tool
```
```
iwconfig
```
```
rfkill list all
```
```
sudo iwlist scan
```
```
sudo lshw -C network
```
Thank you

---

### Post by Densetsu on 2011-09-13
```
lsmod[CODE]Module                  Size  Used by 
binfmt_misc             6587  1 
ppdev                   5259  0 
snd_hda_codec_realtek   203376  1 
joydev                  8740  0 
fbcon                  35102  71 
tileblit                1999  1 fbcon 
font                    7557  1 fbcon 
bitblit                 4707  1 fbcon 
softcursor              1189  1 bitblit 
vga16fb                11385  0 
vgastate                8961  1 vga16fb 
snd_hda_intel          22069  2 
snd_hda_codec          74201  2 snd_hda_codec_realtek,snd_hda_intel 
snd_hwdep               5412  1 
snd_hda_codec 
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 
snd_pcm_oss 
snd_pcm                70694  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss 
snd_seq_dummy           1338  0 
snd_seq_oss            26722  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi 
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi 
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event 
dell_wmi                1793  0 
snd_timer              19098  2 snd_pcm,snd_seq 
b43                   163556  0 
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq 
i915                  288611  3 
mac80211              205402  1 b43 
compal_laptop           2034  0 
drm_kms_helper         29329  1 i915 
uvcvideo               57374  0 
intel_agp              24375  2 i915 
dcdbas                  5422  0 
cfg80211              126144  2 b43,mac80211 
snd                    54244  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device 
drm                   162377  4 i915,drm_kms_helper 
psmouse                63677  0 
videodev               34361  1 uvcvideo 
v4l1_compat            13251  2 uvcvideo,videodev 
serio_raw               3978  0 
soundcore               6620  1 snd 
i2c_algo_bit            5028  1 i915 
led_class               2864  1 b43 
agpgart                31724  2 intel_agp,drm 
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm 
video                  17375  1 i915 
output                  1871  1 video 
lp                      7028  0 
parport                32635  2 ppdev,lp 
usb_storage            39841  0 
r8169                  34140  0 
mii                     4381  1 r8169 
ssb                    38934  1 b43
```[/CODE]  
```
nm-tool[CODE]NetworkManager Tool 
State: disconnected 
- Device: eth0 ----------------------------------------------------------------- 
Type:              Wired 
Driver:            r8169 
State:             unavailable 
Default:           no 
HW Address:        00:26:B9:A1:B9:37 
Capabilities: 
Carrier Detect:  yes     
Speed:           10 Mb/s 
Wired Properties 
Carrier:         off
```[/CODE]  
 ```
iwconfig[CODE]lo        no wireless extensions. 

eth0      no wireless extensions. 
```[/CODE] ```
rfkill list all[CODE]0: compal-wifi: Wireless LAN 
Soft blocked: no 
Hard blocked: no 

1: compal-bluetooth: Bluetooth 
Soft blocked: no 
Hard blocked: no
```[/CODE]```
sudo iwlist scan[CODE]lo        Interface doesn't support scanning. 

eth0      Interface doesn't support scanning.
```[/CODE] ```
sudo lshw -C network[CODE]*-network               
description: Network controller 
product: BCM4322 802.11a/b/g/n Wireless LAN Controller 
vendor: Broadcom Corporation 
physical id: 0 
bus info: pci@0000:03:00.0 
version: 01 
width: 64 bits 
clock: 33MHz 
capabilities: pm msi pciexpress bus_master cap_list 
configuration: driver=b43-pci-bridge latency=0 
resources: irq:17 
memory:f0100000-f0103fff 

*-network 
description: Ethernet interface 
product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller 
vendor: Realtek Semiconductor Co., Ltd. 
physical id: 0 
bus info: pci@0000:04:00.0 
logical name: eth0 
version: 02 
serial: 00:26:b9:a1:b9:37 
size: 10MB/s 
capacity: 100MB/s 
width: 64 bits 
clock: 33MHz 
capabilities:  pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp  mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation 
configuration:  autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI  duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s 
resources: irq:27 
ioport:2000(size=256) memory:f0510000-f0510fff(prefetchable) memory:f0500000-f050ffff(prefetchable) memory:f0520000-f053ffff(prefetchable) 

```[/CODE]

Thank you~

---

### Post by pdc on 2011-09-14
so this is extraordinary;

in post #12 wildmanne clearly says install

> broadcom-sta-source + broadcom-sta-common only 

and provides detailed instructions

and then Densetsu comes back in post #19

> but whenever I activate the Broadcom B43 Wireless Driver,

.........how did that happen...........

so, not surprisingly

> lsmod 

shows

> b43                   163556  0 

and > sudo lshw -C network

still shows > BCM4322

and [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

clearly confirms what wildmanne said: install

> broadcom-sta-source + broadcom-sta-common only 

---

### Post by Densetsu on 2011-09-14
And I clearly stated in post #17 that I could not find said packages. Which, still, remains true.

In post #18 wildmanne gave me a link to a thread that could help me. My reply in post #19 was stating that one of the steps in the link did not work.

---

### Post by wildmanne39 on 2011-09-15
Hi, I am sorry I have been away but I was in the hospital for a few days. Let's try this with the livecd in and a check by cdrom in synaptic in that same window go to updates and put a check by restricted then install bcmwl-kernel-source, broadcom-sta-source + broadcom-sta-common only, if everything installs restart your computer, we may still need to blacklist a few things but hopefully not.

I am not going to be on a lot until I am completely well.
Thank you

---

