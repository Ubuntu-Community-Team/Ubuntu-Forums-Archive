---
title: "disabled wireless on pavillion dv6022 and ubuntu 12.04"
date: 2012-07-18
forum: Networking &amp; Wireless
---

### Post by El-ahrairah on 2012-07-18
Hi everybody,

I'm opening this thread 'cause I have a problem after a fresh install of ubuntu 12.04 on my HP Pavillion DV6022EA.

The problem is that, even after installing the ndiswrapper and downloading the STA additional drivers as explained [here]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#Installing%20STA%20drivers") for my broadcom wireless card, when I boot up the pc the wireless card stays off and I find no way of turning it on.

There is a switch close to the trackpad which shows orange led for disabled wireless and blue led for enabled. Even if I move the switch in the enabled position, the led stays orange and the system does not see the wireless card.

Instead, if I boot the computer having a lan cable connected to my router, then the wireless card would enable too.

Also, even if I correctly installed STA driver, when accessing to additional driver sometimes it would tell me that it is activated but not used (as it is right now), or it would even disappear.

I really do not know what to do, I'm quite new to ubuntu and linux in general...

---

### Post by Finnicella on 2012-07-18
Give this command
```
rfkill list all
```
if in the output you'll find block=yes
try this:
```
sudo rfkill unblock all
```
Sorry for my  english :D

---

### Post by 23senick on 2012-07-18
I'd be very clear about which card you have - open terminal and type 
[FONT=monospace]
[/FONT]lspci -vvnn | grep 14e4

once you know the number, use it to search for other posts. My experience with 4313 was it can be a pain, but you should find a good solution.

---

### Post by El-ahrairah on 2012-07-23
Sorry for the late reply, could not try until today...

[QUOTE=Finnicella]```
rfkill list all
```[/QUOTE]

The command gave no output at all. The switch is activated but the led is still orange.

I tried to deactivate the switch and then reactivate it, and I got a full freeze of my computer O.o

[QUOTE=23senick]```
lspci -vvnn | grep 14e4
```[/QUOTE]

There was no output, but I'm SURE that it used to at least "see" the card before...



EDIT: I just tried going into the computer BIOS and resetting all settings, 'cause I remember it seemed to help once, but with no effect.

The card is not listed in the lspci command output, and the STA wireless drivers just "disappeared" from the additional available drivers, even though synaptic reports them as properly installed...



EDIT 2: I also tried disabling ndiswrapper and reinstalling the STA wireless drivers, but they won't show up in the additional drivers list. I do not know what else to try...

---

### Post by 23senick on 2012-07-25
hmmm...beyond me I'm afraid, you could try re-pasting your query.

I read quite a lot about ndis wrapper causing problems - I think you're better off finding a solution without it.    But how you do that without a fresh install, I'm not sure.

Hope it gets sorted

---

### Post by chili555 on 2012-07-25
Please show us:```
lspci -nn | grep 0280
rfkill list all
lsb_release -d
```Thanks.

---

### Post by Finnicella on 2012-07-26
If rfkill list all doesn't work, try with ```
sudo rfkill list all
```
and then ```
sudo rfkill unblock all
```
Bye

---

### Post by El-ahrairah on 2012-08-13
Here is the output for the suggested commands.

```
lspci -nn | grep 0280
```

no output.

```
rfkill list all
```

again no output.

```
lsb_release -d
```

output: Description:	Ubuntu 12.04 LTS

```
sudo rfkill list all
```

no output.

```
sudo rfkill unblock all
```

again no output.



I'm quite short on ideas, I must admit I do not know the system very well...

I'll try to do a fresh install and then go with the "STA driver" way, avoiding the ndiswrapper at all, hoping this will work, but I'm still open to other options.



EDIT:

After rebooting a couple of times, trying to load the installer on my usb key (and failing in the process, 'cause it would keep loading my actual ubuntu installation for some reason...), I got the card active with blue led.

I'm trying the suggested commands again.

```
lspci -nn | grep 0280
```

03:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11a/b/g [14e4:4312] (rev 01)

```
rfkill list all
```

0: hp-wifi: Wireless LAN
Soft blocked: no
Hard blocked: no

I've just rechecked the additional driver, the STA driver entry reappeared and says "active but not in use"

I'll try now to reboot and see if it maintains the active state or not.

---

### Post by El-ahrairah on 2012-08-13
So... I uninstall and purged the ndiswrapper, updated to latest kernel and reinstalled the STA driver.

No the wireless card is dead again: I tried again to do

```
rfkill list all
```

and it was shown as

```
0: hp-wifi: Wireless LAN
Soft blocked: no
Hard blocked: no
```

but I had no way to activate it (turning the led to blue), I also tried

```
sudo rfkill unblock all
```

but to no avail.

After a second reboot, it does not show up anymore... What could I do now? I really do not understand why it worked a few times and now won't work anymore, it is really frustrating!

---

### Post by chili555 on 2012-08-14
> What could I do now? I really do not understand why it worked a few times and now won't work anymore, it is really frustrating!I really have no idea. The only times I've seen a wireless device appear and disappear was either a defective installation of the operating system or a defective card. Are there any clues here?```
dmesg | grep -i warn
dmesg | grep -i err
```

---

### Post by El-ahrairah on 2012-08-15
Here is the output of the suggested commands:

```
dmesg | grep -i warn
```

No output.

```
dmesg | grep -i err
```

The output was:

```
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] spurious 8259A interrupt: IRQ7.
[    0.169818] ACPI: Using IOAPIC for interrupt routing
[    0.180433] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.180546] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P0._PRT]
[    0.180583] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.XVR0._PRT]
[    0.180622] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.XVR1._PRT]
[    0.180658] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.XVR2._PRT]
[    0.205069] ACPI: PCI Interrupt Link [LNK1] (IRQs 5) *0, disabled.
[    0.205181] ACPI: PCI Interrupt Link [LNK2] (IRQs 7) *11
[    0.205288] ACPI: PCI Interrupt Link [LNK3] (IRQs 10) *11
[    0.205394] ACPI: PCI Interrupt Link [LNK4] (IRQs 11) *0, disabled.
[    0.205501] ACPI: PCI Interrupt Link [LK1E] (IRQs 16) *11
[    0.205607] ACPI: PCI Interrupt Link [LK2E] (IRQs 17) *0, disabled.
[    0.205714] ACPI: PCI Interrupt Link [LK3E] (IRQs 18) *0, disabled.
[    0.205821] ACPI: PCI Interrupt Link [LK4E] (IRQs 19) *0, disabled.
[    0.205930] ACPI: PCI Interrupt Link [LSMB] (IRQs *10)
[    0.206037] ACPI: PCI Interrupt Link [LPMU] (IRQs 11) *10
[    0.206146] ACPI: PCI Interrupt Link [LUS0] (IRQs 22) *11
[    0.206254] ACPI: PCI Interrupt Link [LUS2] (IRQs 22) *7
[    0.206362] ACPI: PCI Interrupt Link [LMAC] (IRQs 20) *10
[    0.206470] ACPI: PCI Interrupt Link [LAZA] (IRQs 21) *0, disabled.
[    0.206579] ACPI: PCI Interrupt Link [LACI] (IRQs 21) *0, disabled.
[    0.206689] ACPI: PCI Interrupt Link [LMCI] (IRQs 21) *0, disabled.
[    0.206798] ACPI: PCI Interrupt Link [LPID] (IRQs 21) *0, disabled.
[    0.206919] ACPI: PCI Interrupt Link [LTID] (IRQs 23) *5
[    0.207036] ACPI: PCI Interrupt Link [LSI1] (IRQs 20) *10
[    0.274410] ACPI: PCI Interrupt Link [LUS0] enabled at IRQ 22
[    0.536241] ACPI: PCI Interrupt Link [LUS2] enabled at IRQ 22
[    1.013571] ACPI: PCI Interrupt Link [LTID] enabled at IRQ 23
[    1.340297] sdhci: Copyright(c) Pierre Ossman
[    1.342765] ACPI: PCI Interrupt Link [LMAC] enabled at IRQ 20
[    2.193296] ACPI: PCI Interrupt Link [LNK2] enabled at IRQ 7
[    2.196944] ACPI: PCI Interrupt Link [LNK1] enabled at IRQ 5
[   21.038378] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   21.315171] k8temp 0000:00:18.3: Temperature readouts might be wrong - check erratum #141
[   21.755395] ACPI: PCI Interrupt Link [LK1E] enabled at IRQ 16
[   21.950478] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 21
```

Any hint?

---

### Post by El-ahrairah on 2012-08-15
I just made a fresh install of ubuntu 12.04

At first boot, the network manager showed the wireless card as present but not ready due to missing firmware, and its led indicator was orange.

I installed all the updates, then installed the additional STA and NVidia driver.

Now, after reboot, the STA driver has disappeard from the additional driver and the network manager no longer "sees" the wireless network card.

Could it be that the problem is the STA driver itself? What I should do if this is the case?

---

### Post by chili555 on 2012-08-15
> **El-ahrairah said:**
> I just made a fresh install of ubuntu 12.04

At first boot, the network manager showed the wireless card as present but not ready due to missing firmware, and its led indicator was orange.

I installed all the updates, then installed the additional STA and NVidia driver.

Now, after reboot, the STA driver has disappeard from the additional driver and the network manager no longer "sees" the wireless network card.

Could it be that the problem is the STA driver itself? What I should do if this is the case?I don't know why the card appears and disappears but I am quite sure that the STA driver is not correct. Please do:```
sudo apt-get remove --purge bcmwl-kernel-source
sudo apt-get install linux-firmware-nonfree
```Reboot and let us see:```
dmesg | grep b43
```Thanks.

---

### Post by El-ahrairah on 2012-08-15
I've done as you suggested. The command

```
dmesg | grep b43
```

gave no output.

I hope I do not have to go through another fresh install...

---

### Post by chili555 on 2012-08-15
Please try loading it and then see what the messages might be:```
sudo modprobe b43
dmesg | grep b43
```Thanks.

---

### Post by El-ahrairah on 2012-08-20
After rebooting now my laptop after a few days away from home, the wireless network card automatically turned on! This is gonna make me crazy...

So, let's try again:

```
dmesg | grep b43
```

It seems that this time the b43 drivers automatically loaded, the output was:

```
[    1.303410] b43-pci-bridge 0000:03:00.0: PCI INT A -> Link[LK4E] -> GSI 19 (level, high) -> IRQ 19
[    1.303422] b43-pci-bridge 0000:03:00.0: setting latency timer to 64
[   23.501404] b43-phy0: Broadcom 4311 WLAN found (core revision 10)
[   23.879031] Registered led device: b43-phy0::tx
[   23.879066] Registered led device: b43-phy0::rx
[   23.879097] Registered led device: b43-phy0::radio
[   24.349143] b43-phy0: Loading firmware version 666.2 (2011-02-23 01:15:07)
```

And, if it could be of any use:

```
rfkill list all
```

Output:

```
0: hp-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
```

Here I see a new phy0 entry which I've never seen before.

Some other various commands previously requested:

```
lspci -vvnn | grep 14e4
03:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11a/b/g [14e4:4312] (rev 01)
```

```
lspci -nn | grep 0280
03:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11a/b/g [14e4:4312] (rev 01)
```

I will now try to reboot leaving the lan cable detached to see if something changes.

---

### Post by El-ahrairah on 2012-08-20
So, I tried rebooting a total of 4 times:
- 2 simple reboots
- 2 complete system shutdown, turning the system on after a couple of minutes

After this 4 tests, all done with the lan cable not connected, the wireless card turned on only once.

I also tried manually loading the b43 module, but nothing changed.

I'll now try a reboot leaving the lan cable connected to see if something changes.



EDIT:

After a few more reboots with the lan cable connected, the wireless remains off, I even tried to put the b43 module in the /etc/modules file but to no avail.

I really cannot understand why it would work only a few times...

Ideas, anyone? Should I go, again, for a fresh install and completely avoid the STA drivers this time?

---

### Post by chili555 on 2012-08-20
Please reboot and when it's not working, do:```
dmesg | grep -e wlan -e b43 > info.txt
lsmod >> info.txt
iwconfig >> info.txt
```Find the file info.txt in your user directory and attach it to your reply using the paperclip tool at the top of the reply box.

---

### Post by El-ahrairah on 2012-08-20
Here you go!

I also tried installing the following two modules using synaptic:
firmware-b43-installer
firmware-b43-lpphy-installer

I obviously tried them one at a time, with some reboots between the two tests, but still nothing changed.

---

### Post by chili555 on 2012-08-20
Your thread mentions ndiswrapper, the STA driver and b43 firmware. Of these three methods, two are incorrect. Please do:```
sudo apt-get remove --purge bcmwl-kernel-source
sudo apt-get remove --purge ndiswrapper
```> I even tried to put the b43 module in the /etc/modules file It is not loaded in your info.txt. Let's look for blacklists:```
ls /etc/modprobe.d
```Let's check:```
cat /etc/modules
```Please do not add any new drivers until we can fix this!

---

### Post by El-ahrairah on 2012-08-20
Both the STA drivers and ndiswrapper were purged some days ago.

```
ls /etc/modprobe.d
alsa-base.conf              blacklist-oss.conf
blacklist-ath_pci.conf      blacklist-rare-network.conf
blacklist.conf              blacklist-watchdog.conf
blacklist-firewire.conf     dkms.conf
blacklist-framebuffer.conf  nvidia-graphics-drivers.conf
blacklist-modem.conf        vmwgfx-fbdev.conf
```

```
cat /etc/modules
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
```

The b43 module seems to not be blacklisted:

```
cat /etc/modprobe.d/*.conf | grep b43
# replaced by b43 and ssb.
```

After manually loading b43 module:

```
lsmod
Module                  Size  Used by
b43                   342643  0 
mac80211              436455  1 b43
cfg80211              178679  2 b43,mac80211
bcma                   25651  1 b43
ssb                    50691  1 b43
vesafb                 13516  1 
rfcomm                 38139  0 
parport_pc             32114  0 
ppdev                  12849  0 
bnep                   17830  2 
bluetooth             158438  10 rfcomm,bnep
snd_hda_codec_conexant    52554  1 
joydev                 17393  0 
snd_hda_intel          32765  2 
snd_hda_codec         109562  2 snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80845  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
hp_wmi                 13652  0 
sparse_keymap          13658  1 hp_wmi
snd_rawmidi            25424  1 snd_seq_midi
nvidia               7102452  37 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
r592                   17808  0 
r852                   17901  0 
sm_common              16737  1 r852
nand                   49667  2 r852,sm_common
uvcvideo               67203  0 
nand_ids                8547  1 nand
snd                    62064  13 snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
mtd                    35584  2 sm_common,nand
nand_bch               13003  1 nand
videodev               86588  1 uvcvideo
bch                    21757  1 nand_bch
memstick               15857  1 r592
nand_ecc               13070  1 nand
psmouse                72919  0 
soundcore              14635  1 snd
k8temp                 12905  0 
serio_raw              13027  0 
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
video                  19068  0 
nv_tco                 13399  0 
wmi                    18744  1 hp_wmi
mac_hid                13077  0 
i2c_nforce2            12906  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
firewire_ohci          40172  0 
sata_nv                23360  2 
sdhci_pci              18324  0 
sdhci                  28241  1 sdhci_pci
firewire_core          56906  1 firewire_ohci
crc_itu_t              12627  1 firewire_core
forcedeth              58096  0 
pata_amd               13750  0
```

---

### Post by chili555 on 2012-08-20
Now b43 *is* loaded! Any change here?```
iwconfig
```If no interface wlan0 appears, let us see:```
dmesg | grep b43
```Thanks.

---

### Post by El-ahrairah on 2012-08-21
After manually loading the b43 module:

```
iwconfig 
lo        no wireless extensions.

eth0      no wireless extensions.
```

And

```
dmesg | grep b43
```

No output.

---

### Post by chili555 on 2012-08-21
> **El-ahrairah said:**
> After manually loading the b43 module:

```
iwconfig 
lo        no wireless extensions.

eth0      no wireless extensions.
```

And

```
dmesg | grep b43
```

No output.This is baffling! Let's see if there is an issue with the PCI bus:> [COLOR="Red"]03:00.0[/COLOR] Network controller [0280]: Broadcom Corporation BCM4311 802.11a/b/g [14e4:4312] (rev 01)Please do:```
sudo su
echo b43 >> /etc/modules
modprobe b43
exit
dmesg > info2.txt
```Please post info2.txt as before. 

Crazy!!

---

### Post by El-ahrairah on 2012-08-21
It is crazy indeed!

Here is the file you asked for, I had to zip it 'cause the upload manager said it was too big.

---

### Post by chili555 on 2012-08-21
Wow! Some very interesting things in there. For instance:> [    0.177161] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.177243] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.177408] pci_root PNP0A03:00: host bridge window [io  0x0000-0x0cf7]
<snip>
[    0.177484] pci_root PNP0A03:00: ignoring host bridge window [mem 0x000cc000-0x000cffff] (conflicts with Video ROM [mem 0x000c0000-0x000cefff])
[    0.177490] [COLOR="Red"]pci_root PNP0A03:00: ignoring host bridge window[/COLOR] [mem 0x000d0000-0x000d3fff] (conflicts with Adapter ROM [mem 0x000cf000-0x000d07ff])Searching for this term I've highlighted shows a bug. 

Also, I do not see your device bus listed *at all* in dmesg! Does it still show up in:```
lspci
```You might look around in the computer's BIOS to see if anything's amiss or disabled. Usually, you can safely reset the BIOS to defaults safely in Linux.

---

### Post by El-ahrairah on 2012-08-22
here is the full output of the command:

```
lspci
00:00.0 RAM memory: NVIDIA Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: NVIDIA Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: NVIDIA Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: NVIDIA Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: NVIDIA Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: NVIDIA Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: NVIDIA Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: NVIDIA Corporation C51 Memory Controller 2 (rev a2)
00:02.0 PCI bridge: NVIDIA Corporation C51 PCI Express Bridge (rev a1)
00:03.0 PCI bridge: NVIDIA Corporation C51 PCI Express Bridge (rev a1)
00:04.0 PCI bridge: NVIDIA Corporation C51 PCI Express Bridge (rev a1)
00:09.0 RAM memory: NVIDIA Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: NVIDIA Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: NVIDIA Corporation MCP51 SMBus (rev a3)
00:0a.3 Co-processor: NVIDIA Corporation MCP51 PMU (rev a3)
00:0b.0 USB controller: NVIDIA Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB controller: NVIDIA Corporation MCP51 USB Controller (rev a3)
00:0d.0 IDE interface: NVIDIA Corporation MCP51 IDE (rev f1)
00:0e.0 IDE interface: NVIDIA Corporation MCP51 Serial ATA Controller (rev f1)
00:10.0 PCI bridge: NVIDIA Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: NVIDIA Corporation MCP51 High Definition Audio (rev a2)
00:14.0 Bridge: NVIDIA Corporation MCP51 Ethernet Controller (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
05:00.0 VGA compatible controller: NVIDIA Corporation G72M [GeForce Go 7200] (rev a1)
07:05.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
07:05.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
07:05.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
07:05.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)
```

The card seems to have disappeared again... I'll now try to reset the bios defaults.



EDIT:

I reset the bios to the default values, and nothing seems to have changed. Please note that in the bios interface there is no option AT ALL regarding wireless card, all you can setup is the boot password and the boot order.

---

### Post by chili555 on 2012-08-22
I don't know what else to suggest. The wireless isn't going to work if the system doesn't even see it. You might try running the install CD in a live session to see if it's found there.```
lspci
```I'm afraid I'm out of ideas.

---

### Post by El-ahrairah on 2012-08-22
Well, I dunno what to say, except this: thank you for all your kind efforts in trying to help me solve my problem =)

I'll try a new, fresh install of ubuntu 12.04 when I'll have the time to do this, and report back here on the results.

Cross your fingers for me!

---

### Post by chili555 on 2012-08-22
> Cross your fingers for me!Fingers and toes crossed!!

---

