---
title: "[HELP] popping/cracking sound from speakers"
date: 2010-03-16
forum: Multimedia Software
---

### Post by WarrenSH on 2010-03-16
I am having some sound issues with Karmic Koala 9.10 32bit AMD. My problem is that when sound plays over my speakers I hear a popping/cracking noise. 
[B]
Examples are.[/B]
When someone sends me a message over Pidgin 
When I open a .mp3 
When opening a video using VLC 
& so on... When I was using windows my sound driver was RealTek HD 
[B]
this is my output[/B]

```
00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:04.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:05.0 VGA compatible controller: nVidia Corporation C51 [GeForce Go 6100] (rev a2)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
00:0a.3 Co-processor: nVidia Corporation MCP51 PMU (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev f1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
04:05.0 Ethernet controller: Atheros Communications Inc. AR2413 802.11bg NIC (rev 01)
04:06.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
04:06.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)

```

---

### Post by oldsoundguy on 2010-03-16
check and clean all of your connections before you go looking for software issues.  Make sure the connection for your wall wart is good and make sure that the wall wart is putting out a constant output under load.  
Then check to see if your sound card (if you are using one) is properly seated.  If you are using on board, make sure the connection is solid in the board.

IF all that passes .. then it is time to go software searching .. but doubt that will be your issue as over 95% of all audio problems whether computer or home or pro are related to wiring and connections.
Trust me, that is how I made my beans and bacon for years.

---

### Post by WarrenSH on 2010-03-16
> **oldsoundguy said:**
> check and clean all of your connections before you go looking for software issues.  Make sure the connection for your wall wart is good and make sure that the wall wart is putting out a constant output under load.  
Then check to see if your sound card (if you are using one) is properly seated.  If you are using on board, make sure the connection is solid in the board.

IF all that passes .. then it is time to go software searching .. but doubt that will be your issue as over 95% of all audio problems whether computer or home or pro are related to wiring and connections.
Trust me, that is how I made my beans and bacon for years.


I am using a **Laptop &  2 days ago I was running Windows 7** & the sound was great then I installed Ubuntu 9.10 & this is when I started to have problems. All my connections are clean & everything is working well I can hear sound but I get this pop/cracking noise first then I get sound that is clear as can be.

---

### Post by qwerty2009 on 2010-03-16
give this ago (googles your friend),

 press alt + f2 and type: 

gksu gedit etc/modprobe.d/alsa-base.conf 

And comment (add a "#" in front of it) the last line called "options snd-hda-intel power_save=10".

Basically, this is how the line should look after editing it: 

#options snd-hda-intel power_save=10 

Then save the file.

---

### Post by WarrenSH on 2010-03-16
> **qwerty2009 said:**
> give this ago (googles your friend),

 press alt + f2 and type: 

gksu gedit etc/modprobe.d/alsa-base.conf 

And comment (add a "#" in front of it) the last line called "options snd-hda-intel power_save=10".

Basically, this is how the line should look after editing it: 

#options snd-hda-intel power_save=10 

Then save the file.


I did that & I got an error once I pushed save. I took screen shoots of the step by steps I did just like you said. 

[CENTER][IMG]http://shafordesigns.com/1.png[/IMG]


[IMG]http://shafordesigns.com/2.png[/IMG]




[IMG]http://shafordesigns.com/3.png[/IMG]
[/CENTER]

---

### Post by RedSingularity on 2010-03-16
Post the output of 

aplay -l

---

### Post by RedSingularity on 2010-03-16
Oh and the output of 

lspci -v

thats going to be a long one.

---

### Post by WarrenSH on 2010-03-16
> **RedSingularity said:**
> Post the output of 

aplay -l

```
 aplay: device_list:223: no soundcards found... 
```

> **RedSingularity said:**
> Oh and the output of 

lspci -v

thats going to be a long one.

```
aspire9300@aspire9300-laptop:~$ lspci -v
 00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
     Subsystem: Acer Incorporated [ALI] Device 0112
     Flags: bus master, 66MHz, fast devsel, latency 0
     Capabilities: <access denied>
 
 00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
     Subsystem: Acer Incorporated [ALI] Device 0112
     Flags: 66MHz, fast devsel
 
 00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
     Subsystem: Acer Incorporated [ALI] Device 0112
     Flags: 66MHz, fast devsel
 
 00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
     Subsystem: Acer Incorporated [ALI] Device 0112
     Flags: 66MHz, fast devsel
 
 00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
     Subsystem: Acer Incorporated [ALI] Device 0112
     Flags: bus master, 66MHz, fast devsel, latency 0
 
 00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
     Subsystem: Acer Incorporated [ALI] Device 0112
     Flags: bus master, 66MHz, fast devsel, latency 0
     Capabilities: <access denied>
 
 00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
     Subsystem: Acer Incorporated [ALI] Device 0112
     Flags: 66MHz, fast devsel
 
 00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
     Subsystem: Acer Incorporated [ALI] Device 0112
     Flags: 66MHz, fast devsel
 
 00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
     Flags: bus master, fast devsel, latency 0
     Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
     Capabilities: <access denied>
     Kernel driver in use: pcieport-driver
     Kernel modules: shpchp
 
 00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
     Flags: bus master, fast devsel, latency 0
     Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
     I/O behind bridge: 00004000-00004fff
     Memory behind bridge: c4000000-c40fffff
     Capabilities: <access denied>
     Kernel driver in use: pcieport-driver
     Kernel modules: shpchp
 
 00:04.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
     Flags: bus master, fast devsel, latency 0
     Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
     Capabilities: <access denied>
     Kernel driver in use: pcieport-driver
     Kernel modules: shpchp
 
 00:05.0 VGA compatible controller: nVidia Corporation C51 [GeForce Go 6100] (rev a2)
     Subsystem: Acer Incorporated [ALI] Device 0112
     Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 20
     Memory at c2000000 (32-bit, non-prefetchable) [size=16M]
     Memory at d0000000 (64-bit, prefetchable) [size=256M]
     Memory at c1000000 (64-bit, non-prefetchable) [size=16M]
     [virtual] Expansion ROM at 84000000 [disabled] [size=128K]
     Capabilities: <access denied>
     Kernel driver in use: nvidia
     Kernel modules: nvidia, nvidiafb
 
 00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
     Subsystem: Acer Incorporated [ALI] Device 0112
     Flags: bus master, 66MHz, fast devsel, latency 0
     Capabilities: <access denied>
 
 00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
     Subsystem: Acer Incorporated [ALI] Device 0112
     Flags: bus master, 66MHz, fast devsel, latency 0
 
 00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
     Subsystem: Acer Incorporated [ALI] Device 0112
     Flags: 66MHz, fast devsel, IRQ 10
     I/O ports at 3040 [size=64]
     I/O ports at 3000 [size=64]
     Capabilities: <access denied>
     Kernel driver in use: nForce2_smbus
     Kernel modules: i2c-nforce2
 
 00:0a.3 Co-processor: nVidia Corporation MCP51 PMU (rev a3)
     Subsystem: Acer Incorporated [ALI] Device 0112
     Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 11
     Memory at c0040000 (32-bit, non-prefetchable) [size=256K]
 
 00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3) (prog-if 10)
     Subsystem: Acer Incorporated [ALI] Device 0112
     Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22
     Memory at c0004000 (32-bit, non-prefetchable) [size=4K]
     Capabilities: <access denied>
     Kernel driver in use: ohci_hcd
 
 00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3) (prog-if 20)
     Subsystem: Acer Incorporated [ALI] Device 0112
     Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 23
     Memory at c0005000 (32-bit, non-prefetchable) [size=256]
     Capabilities: <access denied>
     Kernel driver in use: ehci_hcd
 
 00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev f1) (prog-if 8a [Master SecP PriP])
     Subsystem: Acer Incorporated [ALI] Device 0112
     Flags: bus master, 66MHz, fast devsel, latency 0
     [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
     [virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
     [virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
     [virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
     I/O ports at 3080 [size=16]
     Capabilities: <access denied>
     Kernel driver in use: pata_amd
 
 00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2) (prog-if 01)
     Flags: bus master, 66MHz, fast devsel, latency 0
     Bus: primary=00, secondary=04, subordinate=08, sec-latency=64
     I/O behind bridge: 00005000-00005fff
     Memory behind bridge: c3000000-c30fffff
     Prefetchable memory behind bridge: 80000000-83ffffff
     Capabilities: <access denied>
 
 00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
     Subsystem: Acer Incorporated [ALI] Device 0112
     Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 18
     Memory at c0000000 (32-bit, non-prefetchable) [size=16K]
     Capabilities: <access denied>
     Kernel driver in use: oss_hdaudio
 
 00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
     Subsystem: Acer Incorporated [ALI] Device 0112
     Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 21
     Memory at c0007000 (32-bit, non-prefetchable) [size=4K]
     I/O ports at 30b8 [size=8]
     Capabilities: <access denied>
     Kernel driver in use: forcedeth
     Kernel modules: forcedeth
 
 00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
     Flags: fast devsel
     Capabilities: <access denied>
 
 00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
     Flags: fast devsel
 
 00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
     Flags: fast devsel
 
 00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
     Flags: fast devsel
     Capabilities: <access denied>
     Kernel driver in use: k8temp
     Kernel modules: k8temp
 
 04:05.0 Ethernet controller: Atheros Communications Inc. AR2413 802.11bg NIC (rev 01)
     Subsystem: AMBIT Microsystem Corp. Device 0418
     Flags: bus master, medium devsel, latency 168, IRQ 19
     Memory at c3000000 (32-bit, non-prefetchable) [size=64K]
     Capabilities: <access denied>
     Kernel driver in use: ath5k
     Kernel modules: ath5k
 
 04:06.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
     Subsystem: Acer Incorporated [ALI] Device 0112
     Flags: bus master, medium devsel, latency 168, IRQ 11
     Memory at c3010000 (32-bit, non-prefetchable) [size=4K]
     Bus: primary=04, secondary=05, subordinate=08, sec-latency=176
     Memory window 0: 80000000-83fff000 (prefetchable)
     Memory window 1: 88000000-8bfff000
     I/O window 0: 00005000-000050ff
     I/O window 1: 00005400-000054ff
     16-bit legacy interface ports at 0001
     Kernel driver in use: yenta_cardbus
     Kernel modules: yenta_socket
 
 04:06.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
     Subsystem: Acer Incorporated [ALI] Device 0112
     Flags: bus master, medium devsel, latency 64, IRQ 11
     Memory at c3012000 (32-bit, non-prefetchable) [size=4K]
     Capabilities: <access denied>
     Kernel driver in use: tifm_7xx1
     Kernel modules: tifm_7xx1
```

---

### Post by RedSingularity on 2010-03-16
Post the output of 

lsmod

---

### Post by WarrenSH on 2010-03-16
> **RedSingularity said:**
> Post the output of 

lsmod


```
Module                  Size  Used by
nls_iso8859_1           3740  0 
nls_cp437               5372  0 
vfat                   10716  0 
fat                    51452  1 vfat
binfmt_misc             8356  1 
ppdev                   6688  0 
vboxnetflt             84840  0 
vboxnetadp             78344  0 
vboxdrv               121160  1 vboxnetflt
oss_usb               104972  1 
oss_hdaudio           143412  3 
osscore               567892  2 oss_usb,oss_hdaudio
arc4                    1660  2 
ecb                     2524  2 
joydev                 10240  0 
pcmcia                 36808  0 
ath5k                 124772  0 
mac80211              181140  1 ath5k
ath                     8060  1 ath5k
iptable_filter          3100  0 
ip_tables              11692  1 iptable_filter
x_tables               16544  1 ip_tables
yenta_socket           24296  1 
rsrc_nonstatic         11644  1 yenta_socket
pcmcia_core            36528  3 pcmcia,yenta_socket,rsrc_nonstatic
cfg80211               93052  3 ath5k,mac80211,ath
tifm_7xx1               5372  0 
tifm_core               7832  1 tifm_7xx1
gspca_m5602            49416  0 
gspca_main             22812  1 gspca_m5602
videodev               36736  1 gspca_main
v4l1_compat            14336  1 videodev
k8temp                  4188  0 
nvidia               9586440  39 
agpgart                34988  1 nvidia
i2c_nforce2             6784  0 
acer_wmi               15936  0 
led_class               4096  2 ath5k,acer_wmi
psmouse                56500  0 
serio_raw               5280  0 
lp                      8964  0 
parport                35340  2 ppdev,lp
hid_a4tech              2652  0 
usbhid                 38208  0 
usb_storage            52768  0 
forcedeth              54152  0 
video                  19380  0 
output                  2780  1 video

```

---

### Post by RedSingularity on 2010-03-16
Now in a terminal do this,

sudo modprobe -r oss_hdaudio

See if you have any sound after that.

---

### Post by WarrenSH on 2010-03-16
> **RedSingularity said:**
> Now in a terminal do this,

sudo modprobe -r oss_hdaudio

See if you have any sound after that.


Nope now I have no sound at all.

---

### Post by RedSingularity on 2010-03-16
Good thats what we want.  Now do this

sudo modprobe snd-hda-intel

And see if you have sound.

---

### Post by WarrenSH on 2010-03-16
> **RedSingularity said:**
> Good thats what we want.  Now do this

sudo modprobe snd-hda-intel

And see if you have sound.

I do not have anything Intel this is a AMD laptop. But I dud run the command & this is what the reply was.

```
FATAL: Module snd_hda_intel not found.
```

---

### Post by RedSingularity on 2010-03-16
I am getting the info on your sound card from this[FONT=monospace]

[/FONT]"Audio device: nVidia Corporation MCP51 High Definition Audio"

I looked at the ALSA drivers available for that sound card and it seems that your particular soundcard is not supported very well under ALSA. 

try this then and see what happens,

sudo modprobe snd-hda-intel

---

### Post by RedSingularity on 2010-03-16
Make sure you type it exactly.

---

### Post by WarrenSH on 2010-03-16
> **RedSingularity said:**
> I am getting the info on your sound card from this[FONT=monospace]

[/FONT]"Audio device: nVidia Corporation MCP51 High Definition Audio"

I looked at the ALSA drivers available for that sound card and it seems that your particular soundcard is not supported very well under ALSA. 

try this then and see what happens,

sudo modprobe snd-hda-intel


I got another error message

```
FATAL: Module snd_hda_intel not found.
```

[IMG]http://img695.imageshack.us/img695/8859/screenshotaspire9300asp.png[/IMG]

---

### Post by RedSingularity on 2010-03-16
Ok how about this

sudo modprobe snd-intel8x0

---

### Post by WarrenSH on 2010-03-16
> **RedSingularity said:**
> Ok how about this

sudo modprobe snd-intel8x0


FATAL: Module snd_intel8x0 not found.

---

### Post by WarrenSH on 2010-03-16
I was once running 8.04 LTS 64bit last year on this same laptop & I had no probs with sound or anything & now that I am using 9.10 32bit things are acting up. :( 

This was a fresh install I used KillDisk to wipe out my HD & did a fresh install of 9.10 32bit

---

### Post by RedSingularity on 2010-03-16
Bahhh restart the computer.  You will have your sound back.  Also try the above command again after the restart. 

sudo modprobe snd-hda-intel

---

### Post by WarrenSH on 2010-03-16
> **RedSingularity said:**
> Bahhh restart the computer.  You will have your sound back.  Also try the above command again after the restart. 

sudo modprobe snd-hda-intel

Sound is back on but I can not control the sound volume on my keyboard I use the commands Fn & UP Arrow & Fn Down Arrow to change the levels on the volume. But now it is loud & I have to manual turn the knob on the speakers. 

```
FATAL: Module snd_hda_intel not found.
```

---

### Post by RedSingularity on 2010-03-17
System>Prefs>Keyboard Shortcuts

Look in there and set your shortcuts for volume up and down.

Do you still have the cracking sound?

---

### Post by WarrenSH on 2010-03-17
> **RedSingularity said:**
> System>Prefs>Keyboard Shortcuts

Look in there and set your shortcuts for volume up and down.

Do you still have the cracking sound?


The short cuts work but when I go to use the Fn + Up arrow or down arrow nothing happens with the volume the disply of the volume works it shows it getting louder & quieter but I still have to manually adjust the volume on the speakers. 

I think that that popping & cracking sound went away.

---

### Post by WarrenSH on 2010-03-17
I think I am going to reformat & install Ubuntu 8.04 LTS 64-bit & then upgrade to 9.04 or what ever the highest upgrade I can go is to see if it is a 32bit prob or 64bit ;) Also I will dual boot Windows XP yarggg!!! lol ill be back to let you all know what happens :)

---

### Post by RedSingularity on 2010-03-17
If you can, do a fresh install of the newest ubuntu.  That is always better than doing an upgrade from an older one.

---

### Post by WarrenSH on 2010-03-18
> **RedSingularity said:**
> If you can, do a fresh install of the newest ubuntu.  That is always better than doing an upgrade from an older one.

I am still having the popping/cracking sounds after fresh install of 9.10 64bit :(

---

### Post by RedSingularity on 2010-03-19
Want to try and troubleshoot it again?

---

