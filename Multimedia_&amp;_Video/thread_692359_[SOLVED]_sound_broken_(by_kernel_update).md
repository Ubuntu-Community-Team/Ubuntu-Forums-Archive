---
title: "[SOLVED] sound broken (by kernel update?)"
date: 2008-02-09
forum: Multimedia &amp; Video
---

### Post by magicman5421 on 2008-02-09
hey. So after this latest kernel update, my sound appears to have stopped working. I have looked all around for a solution but nothing works. I have an hp dv9500.
Here is the output from lspci -v
```
me@my-laptop:~$ sudo lspci -v
[sudo] password for me:
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
        Subsystem: Hewlett-Packard Company Unknown device 30cc
        Flags: bus master, fast devsel, latency 0
        Capabilities: [e0] Vendor Specific Information

00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        I/O behind bridge: 00002000-00002fff
        Memory behind bridge: c4000000-c6ffffff
        Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff
        Capabilities: [88] Subsystem: Hewlett-Packard Company Unknown device 30cc
        Capabilities: [80] Power Management version 3
        Capabilities: [90] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
        Capabilities: [a0] Express Root Port (Slot+) IRQ 0

00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Contoller #4 (rev 03) (prog-if 00 [UHCI])
        Subsystem: Hewlett-Packard Company Unknown device 30cc
        Flags: bus master, medium devsel, latency 0, IRQ 16
        I/O ports at 1800 [size=32]

00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03) (prog-if 00 [UHCI])
        Subsystem: Hewlett-Packard Company Unknown device 30cc
        Flags: bus master, medium devsel, latency 0, IRQ 20
        I/O ports at 1820 [size=32]

00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03) (prog-if 20 [EHCI])
        Subsystem: Hewlett-Packard Company Unknown device 30cc
        Flags: bus master, medium devsel, latency 0, IRQ 18
        Memory at f8404800 (32-bit, non-prefetchable) [size=1K]
        Capabilities: [50] Power Management version 2
        Capabilities: [58] Debug port

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
        Subsystem: Hewlett-Packard Company Unknown device 30cc
        Flags: bus master, fast devsel, latency 0, IRQ 11
        Memory at f8400000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: [50] Power Management version 2
        Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
        Capabilities: [70] Express Unknown type IRQ 0

00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=03, sec-latency=0
        I/O behind bridge: 00004000-00007fff
        Memory behind bridge: f4000000-f7ffffff
        Prefetchable memory behind bridge: 00000000f0000000-00000000f3ffffff
        Capabilities: [40] Express Root Port (Slot+) IRQ 0
        Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
        Capabilities: [90] Subsystem: Hewlett-Packard Company Unknown device 30cc
        Capabilities: [a0] Power Management version 2

00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=04, subordinate=05, sec-latency=0
        I/O behind bridge: 00008000-0000bfff
        Memory behind bridge: bc000000-bfffffff
        Prefetchable memory behind bridge: 00000000c8000000-00000000cbffffff
        Capabilities: [40] Express Root Port (Slot+) IRQ 0
        Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
        Capabilities: [90] Subsystem: Hewlett-Packard Company Unknown device 30cc
        Capabilities: [a0] Power Management version 2

00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 03) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=06, subordinate=06, sec-latency=0
        I/O behind bridge: 0000c000-0000cfff
        Memory behind bridge: f8000000-f80fffff
        Prefetchable memory behind bridge: 0000000088000000-00000000880fffff
        Capabilities: [40] Express Root Port (Slot+) IRQ 0
        Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
        Capabilities: [90] Subsystem: Hewlett-Packard Company Unknown device 30cc
        Capabilities: [a0] Power Management version 2

00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03) (prog-if 00 [UHCI])
        Subsystem: Hewlett-Packard Company Unknown device 30cc
        Flags: bus master, medium devsel, latency 0, IRQ 19
        I/O ports at 1840 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03) (prog-if 00 [UHCI])
        Subsystem: Hewlett-Packard Company Unknown device 30cc
        Flags: bus master, medium devsel, latency 0, IRQ 21
        I/O ports at 1860 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03) (prog-if 00 [UHCI])
        Subsystem: Hewlett-Packard Company Unknown device 30cc
        Flags: bus master, medium devsel, latency 0, IRQ 18
        I/O ports at 1880 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03) (prog-if 20 [EHCI])
        Subsystem: Hewlett-Packard Company Unknown device 30cc
        Flags: bus master, medium devsel, latency 0, IRQ 19
        Memory at f8404c00 (32-bit, non-prefetchable) [size=1K]
        Capabilities: [50] Power Management version 2
        Capabilities: [58] Debug port

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3) (prog-if 01 [Subtractive decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=07, subordinate=07, sec-latency=32
        Memory behind bridge: f8100000-f81fffff
        Capabilities: [50] Subsystem: Hewlett-Packard Company Unknown device 30cc

00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
        Subsystem: Hewlett-Packard Company Unknown device 30cc
        Flags: bus master, medium devsel, latency 0
        Capabilities: [e0] Vendor Specific Information

00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03) (prog-if 8a [Master SecP PriP])
        Subsystem: Hewlett-Packard Company Unknown device 30cc
        Flags: bus master, medium devsel, latency 0, IRQ 21
        I/O ports at 01f0 [size=8]
        I/O ports at 03f4 [size=1]
        I/O ports at 0170 [size=8]
        I/O ports at 0374 [size=1]
        I/O ports at 18a0 [size=16]

00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03) (prog-if 01 [AHCI 1.0])
        Subsystem: Hewlett-Packard Company Unknown device 30cc
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 21
        I/O ports at 18d8 [size=8]
        I/O ports at 18cc [size=4]
        I/O ports at 18d0 [size=8]
        I/O ports at 18c8 [size=4]
        I/O ports at 18e0 [size=32]
        Memory at f8404000 (32-bit, non-prefetchable) [size=2K]
        Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/2 Enable-
        Capabilities: [70] Power Management version 3
        Capabilities: [a8] #12 [0010]

00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
        Subsystem: Hewlett-Packard Company Unknown device 30cc
        Flags: medium devsel, IRQ 10
        Memory at 88100000 (32-bit, non-prefetchable) [size=256]
        I/O ports at 1c00 [size=32]

01:00.0 VGA compatible controller: nVidia Corporation GeForce 8600M GS (rev a1) (prog-if 00 [VGA])
        Subsystem: Hewlett-Packard Company Unknown device 30cc
        Flags: bus master, fast devsel, latency 0, IRQ 16
        Memory at c6000000 (32-bit, non-prefetchable) [size=16M]
        Memory at d0000000 (64-bit, prefetchable) [size=256M]
        Memory at c4000000 (64-bit, non-prefetchable) [size=32M]
        I/O ports at 2000 [size=128]
        Capabilities: [60] Power Management version 2
        Capabilities: [68] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
        Capabilities: [78] Express Endpoint IRQ 0

02:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN Network Connection (rev 61)
        Subsystem: Intel Corporation Unknown device 1100
        Flags: bus master, fast devsel, latency 0, IRQ 16
        Memory at f4000000 (64-bit, non-prefetchable) [size=8K]
        Capabilities: [c8] Power Management version 3
        Capabilities: [d0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
        Capabilities: [e0] Express Endpoint IRQ 0

06:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
        Subsystem: Hewlett-Packard Company Unknown device 30cc
        Flags: bus master, fast devsel, latency 0, IRQ 17
        I/O ports at c000 [size=256]
        Memory at f8000000 (64-bit, non-prefetchable) [size=4K]
        [virtual] Expansion ROM at 88000000 [disabled] [size=128K]
        Capabilities: [40] Power Management version 2
        Capabilities: [48] Vital Product Data
        Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/1 Enable-
        Capabilities: [60] Express Endpoint IRQ 0
        Capabilities: [84] Vendor Specific Information

07:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05) (prog-if 10 [OHCI])
        Subsystem: Hewlett-Packard Company Unknown device 30cc
        Flags: bus master, medium devsel, latency 32, IRQ 22
        Memory at f8100000 (32-bit, non-prefetchable) [size=2K]
        Capabilities: [dc] Power Management version 2

07:09.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
        Subsystem: Hewlett-Packard Company Unknown device 30cc
        Flags: bus master, medium devsel, latency 32, IRQ 20
        Memory at f8100800 (32-bit, non-prefetchable) [size=256]
        Capabilities: [80] Power Management version 2

07:09.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
        Subsystem: Hewlett-Packard Company Unknown device 30cc
        Flags: bus master, medium devsel, latency 32, IRQ 11
        Memory at f8100c00 (32-bit, non-prefetchable) [size=256]
        Capabilities: [80] Power Management version 2

07:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
        Subsystem: Hewlett-Packard Company Unknown device 30cc
        Flags: bus master, medium devsel, latency 32, IRQ 11
        Memory at f8101000 (32-bit, non-prefetchable) [size=256]
        Capabilities: [80] Power Management version 2

07:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
        Subsystem: Hewlett-Packard Company Unknown device 30cc
        Flags: bus master, medium devsel, latency 32, IRQ 11
        Memory at f8101400 (32-bit, non-prefetchable) [size=256]
        Capabilities: [80] Power Management version 2

me@my-laptop:~$ 

```
And here is the output of lsmod:
```

jason@jason-laptop:~$ lsmod
Module                  Size  Used by
af_packet              24840  4 
binfmt_misc            12936  1 
rfcomm                 42136  2 
l2cap                  26240  11 rfcomm
ppdev                  10244  0 
ipv6                  273892  12 
acpi_cpufreq           10568  1 
cpufreq_stats           7232  0 
cpufreq_userspace       5280  0 
cpufreq_powersave       2688  0 
cpufreq_conservative     8072  0 
cpufreq_ondemand        9612  1 
freq_table              5792  3 acpi_cpufreq,cpufreq_stats,cpufreq_ondemand
sbs                    19592  0 
container               5504  0 
video                  18060  8 
button                  8976  0 
dock                   10656  0 
ac                      6148  0 
battery                11012  0 
sbp2                   24072  0 
parport_pc             37412  0 
lp                     12580  0 
parport                37448  3 ppdev,parport_pc,lp
joydev                 11328  0 
arc4                    2944  2 
ecb                     4608  2 
blkcipher               7556  1 ecb
snd_hwdep              10244  0 
snd_pcm_oss            44672  0 
snd_pcm                80388  1 snd_pcm_oss
snd_page_alloc         11400  1 snd_pcm
snd_mixer_oss          17664  1 snd_pcm_oss
snd_seq_dummy           4740  0 
snd_seq_oss            33152  0 
snd_seq_midi            9600  0 
uvcvideo               48644  0 
snd_rawmidi            25728  1 snd_seq_midi
compat_ioctl32          2304  1 uvcvideo
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
videodev               29312  1 uvcvideo
v4l1_compat            15364  2 uvcvideo,videodev
iwl4965               101480  0 
iwlwifi_mac80211      175112  1 iwl4965
nvidia               6221648  36 
v4l2_common            18432  2 uvcvideo,videodev
hci_usb                18332  2 
snd_seq                53232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24324  2 snd_pcm,snd_seq
snd_seq_device          9228  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
sdhci                  18828  0 
mmc_core               28420  1 sdhci
cfg80211                7304  1 iwlwifi_mac80211
bluetooth              57060  7 rfcomm,l2cap,hci_usb
serio_raw               8068  0 
psmouse                39952  0 
i2c_core               26112  1 nvidia
snd                    54660  9 snd_hwdep,snd_pcm_oss,snd_pcm,snd_mixer_oss,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
intel_agp              25620  0 
agpgart                35016  2 nvidia,intel_agp
shpchp                 34580  0 
pci_hotplug            32704  1 shpchp
soundcore               8800  1 snd
evdev                  11136  6 
ext3                  133896  1 
jbd                    60456  1 ext3
mbcache                 9732  1 ext3
sr_mod                 17828  0 
cdrom                  37536  1 sr_mod
sg                     36764  0 
sd_mod                 30336  5 
ata_piix               17540  0 
ahci                   23300  3 
ohci1394               36528  0 
ieee1394               96312  2 sbp2,ohci1394
r8169                  32260  0 
ata_generic             8452  0 
libata                125168  3 ata_piix,ahci,ata_generic
scsi_mod              147084  5 sbp2,sr_mod,sg,sd_mod,libata
uhci_hcd               26640  0 
ehci_hcd               36492  0 
usbcore               138632  5 uvcvideo,hci_usb,uhci_hcd,ehci_hcd
thermal                14344  0 
processor              32072  2 acpi_cpufreq,thermal
fan                     5764  0 
fuse                   47124  3 
apparmor               40728  0 
commoncap               8320  1 apparmor
jason@jason-laptop:~$ alsamixer

alsamixer: function snd_ctl_open failed for default: No such device
jason@jason-laptop:~$ snd_mixer_oss
bash: snd_mixer_oss: command not found
jason@jason-laptop:~$ lsmod
Module                  Size  Used by
af_packet              24840  4 
binfmt_misc            12936  1 
rfcomm                 42136  2 
l2cap                  26240  11 rfcomm
ppdev                  10244  0 
ipv6                  273892  12 
acpi_cpufreq           10568  1 
cpufreq_stats           7232  0 
cpufreq_userspace       5280  0 
cpufreq_powersave       2688  0 
cpufreq_conservative     8072  0 
cpufreq_ondemand        9612  1 
freq_table              5792  3 acpi_cpufreq,cpufreq_stats,cpufreq_ondemand
sbs                    19592  0 
container               5504  0 
video                  18060  8 
button                  8976  0 
dock                   10656  0 
ac                      6148  0 
battery                11012  0 
sbp2                   24072  0 
parport_pc             37412  0 
lp                     12580  0 
parport                37448  3 ppdev,parport_pc,lp
joydev                 11328  0 
arc4                    2944  2 
ecb                     4608  2 
blkcipher               7556  1 ecb
snd_hwdep              10244  0 
snd_pcm_oss            44672  0 
snd_pcm                80388  1 snd_pcm_oss
snd_page_alloc         11400  1 snd_pcm
snd_mixer_oss          17664  1 snd_pcm_oss
snd_seq_dummy           4740  0 
snd_seq_oss            33152  0 
snd_seq_midi            9600  0 
uvcvideo               48644  0 
snd_rawmidi            25728  1 snd_seq_midi
compat_ioctl32          2304  1 uvcvideo
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
videodev               29312  1 uvcvideo
v4l1_compat            15364  2 uvcvideo,videodev
iwl4965               101480  0 
iwlwifi_mac80211      175112  1 iwl4965
nvidia               6221648  36 
v4l2_common            18432  2 uvcvideo,videodev
hci_usb                18332  2 
snd_seq                53232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24324  2 snd_pcm,snd_seq
snd_seq_device          9228  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
sdhci                  18828  0 
mmc_core               28420  1 sdhci
cfg80211                7304  1 iwlwifi_mac80211
bluetooth              57060  7 rfcomm,l2cap,hci_usb
serio_raw               8068  0 
psmouse                39952  0 
i2c_core               26112  1 nvidia
snd                    54660  9 snd_hwdep,snd_pcm_oss,snd_pcm,snd_mixer_oss,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
intel_agp              25620  0 
agpgart                35016  2 nvidia,intel_agp
shpchp                 34580  0 
pci_hotplug            32704  1 shpchp
soundcore               8800  1 snd
evdev                  11136  6 
ext3                  133896  1 
jbd                    60456  1 ext3
mbcache                 9732  1 ext3
sr_mod                 17828  0 
cdrom                  37536  1 sr_mod
sg                     36764  0 
sd_mod                 30336  5 
ata_piix               17540  0 
ahci                   23300  3 
ohci1394               36528  0 
ieee1394               96312  2 sbp2,ohci1394
r8169                  32260  0 
ata_generic             8452  0 
libata                125168  3 ata_piix,ahci,ata_generic
scsi_mod              147084  5 sbp2,sr_mod,sg,sd_mod,libata
uhci_hcd               26640  0 
ehci_hcd               36492  0 
usbcore               138632  5 uvcvideo,hci_usb,uhci_hcd,ehci_hcd
thermal                14344  0 
processor              32072  2 acpi_cpufreq,thermal
fan                     5764  0 
fuse                   47124  3 
apparmor               40728  0 
commoncap               8320  1 apparmor
jason@jason-laptop:~$ 

```
I had ALSA 1.0.15 installed. After the kernel update, my volume icon appeared muted. When I clicked on it, it gave me this:
The volume control did not find any elements and/or devices to control. This means either that you don't have the right GStreamer plugins installed, or that you don't have a sound card configured.

You can remove the volume control from the panel by right-clicking the speaker icon on the panel and selecting "Remove From Panel" from the menu.
After that when I double clicked on it:
No volume control GStreamer plugins and/or devices found.
When I run alsamixer:
```
me@my-laptop:~$ alsamixer

alsamixer: function snd_ctl_open failed for default: No such device
me@my-laptop:~$ 
```
Other assorted information:
```
me@my-laptop:~$ grep -i audio

me@my-laptop:~$ lspci|grep -i audio
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
me@my-laptop:~$ cat /proc/asound/cards
--- no soundcards ---
me@my-laptop:~$ aplay -l
aplay: device_list:204: no soundcards found...
me@my-laptop:~$ 

```
Help me please.
kthxbai.

---

### Post by doddo on 2008-02-09
Hello! 

which alsa tools do u have? I recall using some setup tool when I troubleshooted my own sound card
```
 for a in `echo $PATH | sed 's/:/ /g'`; do find "$a" -name *alsa*; done 
```


Additionaly, When I used arch, I followed [ this guide ]("http://wiki.archlinux.org/index.php/ALSA"). It says that
> No Sound with Onboard Intel Sound Card

There may be an issue with two conflicting modules loaded, namely snd_intel8x0 and snd_intel8x0m. In this case, edit rc.conf and in the MODULES array blacklist the latter one so that it reads !snd_intel8x0m afterwards. 

I would like to see the output of. This will show if you have any sound modules loaded
```
lspci | grep ^snd
```

---

### Post by magicman5421 on 2008-02-09
> **doddo said:**
> Hello! 

which alsa tools do u have? I recall using some setup tool when I troubleshooted my own sound card
```
 for a in `echo $PATH | sed 's/:/ /g'`; do find "$a" -name *alsa*; done 
```


Additionaly, When I used arch, I followed [ this guide ]("http://wiki.archlinux.org/index.php/ALSA"). It says that


I would like to see the output of. This will show if you have any sound modules loaded
```
lspci | grep ^snd
```

OK. Both of the terminal commands you told me to input returned nothing and that page you gave me is still loading after trying for 5 mins.

EDIT: upon further investigation, it would appear that the arch site is down for now so i'll try in a little bit.
EDIT^2: apparently my rc.conf file is empty. Tried:
```

gksudo gedit rc.conf

```
and there was nothing. Is that ok?

---

### Post by tibiker1966 on 2008-02-09
For what it's worth - I'm seeing the same thing on my laptop.   I'm seeing this error message in my dmesg log:

[ 34.060000] AC'97 1 does not respond - RESET
[ 34.072000] AC'97 1 access is not valid [0xffffffff], removing mixer.
[ 34.072000] ali mixer 1 creating error.


Here's my sound hardware:

00:06.0 Multimedia audio controller: ALi Corporation M5451 PCI AC-Link Controller Audio Device (rev 02)
Subsystem: Hewlett-Packard Company Pavilion ze4400 builtin Audio
Flags: bus master, medium devsel, latency 64, IRQ 5
I/O ports at 8400 [size=256]
Memory at d0005000 (32-bit, non-prefetchable) [size=4K]
Capabilities: <access denied>

kgiusti@kgiusti-laptop:/proc/asound$ cat /proc/asound/version 
Advanced Linux Sound Architecture Driver Version 1.0.14rc1 (Tue Jan 09 09:56:17 2007 UTC).
kgiusti@kgiusti-laptop:/proc/asound$ cat /proc/asound/devices 
  2:        : timer
  3:        : sequencer
  4: [ 0- 0]: digital audio playback
  5: [ 0- 0]: digital audio capture
  6: [ 0]   : control

kgiusti@kgiusti-laptop:/proc/asound$ cat /proc/asound/cards
 0 [A5451          ]: ALI5451 - ALI 5451
                      ALI 5451 at 0x8400, irq 5

---

### Post by parsim on 2008-02-09
Same here: sound stopped working after latest software update (including new kernel version).

I can't find any errors, though -- alsamixer runs, pressing volume keys brings up onscreen display, devices are listed in System -> Preferences -> Sound, etc. There's just no sound.

I use a SoundBlaster Live 5.1 card as my output device.

```
$ cat /proc/asound/cards 
 0 [Live           ]: EMU10K1 - SB Live 5.1 [SB0220]
                      SB Live 5.1 [SB0220] (rev.10, serial:0x80651102) at 0xa800, irq 17
 1 [nForce3        ]: NFORCE - NVidia nForce3
                      NVidia nForce3 with ALC658D at irq 22

$ lsmod | grep ^snd
snd_emu10k1_synth       9344  0 
snd_emux_synth         40064  1 snd_emu10k1_synth
snd_seq_virmidi         9216  1 snd_emux_synth
snd_seq_midi_emul       9088  1 snd_emux_synth
snd_intel8x0           40104  0 
snd_seq_dummy           5380  0 
snd_seq_oss            36864  0 
snd_seq_midi           11008  0 
snd_emu10k1           152864  3 snd_emu10k1_synth
snd_ac97_codec        122200  2 snd_intel8x0,snd_emu10k1
snd_pcm_oss            50048  0 
snd_mixer_oss          20096  1 snd_pcm_oss
snd_rawmidi            29824  3 snd_seq_virmidi,snd_seq_midi,snd_emu10k1
snd_seq_midi_event      9984  3 snd_seq_virmidi,snd_seq_oss,snd_seq_midi
snd_pcm                94344  5 snd_intel8x0,snd_emu10k1,snd_ac97_codec,snd_pcm_oss
snd_util_mem            6656  2 snd_emux_synth,snd_emu10k1
snd_seq                62496  9 snd_emux_synth,snd_seq_virmidi,snd_seq_midi_emul,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              27272  3 snd_emu10k1,snd_pcm,snd_seq
snd_seq_device         10260  8 snd_emu10k1_synth,snd_emux_synth,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_emu10k1,snd_rawmidi,snd_seq
snd_hwdep              12168  2 snd_emux_synth,snd_emu10k1
snd                    69288  17 snd_emux_synth,snd_seq_virmidi,snd_intel8x0,snd_seq_oss,snd_emu10k1,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_rawmidi,snd_pcm,snd_seq,snd_timer,snd_seq_device,snd_hwdep
snd_page_alloc         12560  3 snd_intel8x0,snd_emu10k1,snd_pcm
```

---

### Post by SergeiFranco on 2008-02-09
I also would like to confirm that kernel upgrade has broken my sound, the devices all there but there is no sound coming out.

---

### Post by tibiker1966 on 2008-02-09
Ok, mine's working now.   I think that perhaps some setting got munged during the upgrade, not sure why it works, but here's what I did:

1) Rebooted into older ubuntu kernel release (using the boot menu).  Still no sound.  The microphone panel applet appeared muted (as it did on the latest upgrade), but this time I was able to Right-Click on it and brought up the volume control applet.

2) The applet showed that my master channel was muted.   Turned mute off - viola!  Sound!

3) rebooted back into newest ubuntu kernel - Sound is working fine now.

I've never turned on muting before, so somehow it was turned on during the upgrade.

-K

---

### Post by magicman5421 on 2008-02-09
tibiker a modified version of your fix worked for me. I restarted into the recovery mode, started x, adjusted the volume (it wasn't muted, but i adjusted it anyway) and rebooted. When I started up, voila! I had sound! By the way, two things. First of all, that is a huge security flaw. I could start up someone's computer, running ubuntu, into recovery mode and have instant root access. I don't know if there is something that could be done about that but w/e. Second, how do you boot into a previous kernel? All I have as options are the current kernel, the current kernel (recovery), and a memtest86+, along with winblows. Is there a way to keep the kernel when you upgrade?

---

### Post by doddo on 2008-02-10
> **magicman5421 said:**
> tibiker a modified version of your fix worked for me. I restarted into the recovery mode, started x, adjusted the volume (it wasn't muted, but i adjusted it anyway) and rebooted. When I started up, voila! I had sound! By the way, two things. First of all, that is a huge security flaw. I could start up someone's computer, running ubuntu, into recovery mode and have instant root access. I don't know if there is something that could be done about that but w/e. Second, how do you boot into a previous kernel? All I have as options are the current kernel, the current kernel (recovery), and a memtest86+, along with winblows. Is there a way to keep the kernel when you upgrade?

Hello!
Having Physical acces to someones computer is always a security risk. If they couldnt get root access through grub by booting into single user mode, then they could boot a liveCD and get root that way. 
They could also simply remove your hard drive. You can set a grub password thogh, but AFAIK, that  will only prevent people from editing boot options or entering command mode.

The kernel is a file, whis is located in your /boot partition.

doing a ls in /boot will show you which kernels you currently have, those are then pointed to from /boot/grub/menu.lst. If you examine that file, it will show you how to make a suitable entry to  boot

To save an old kernel:
You can check out /boot/grub/menu.lst and see the name of the one you'd like to save, and make a copy of it. That as well as the corresponding initrd.img. A good idea. I suppose, would be to also make an tar archieve of the kernel modules too. They are in /lib/modules and should have the same prefix as the kernel you'd like to save

Glad the sound works BTW :)

---

### Post by tibiker1966 on 2008-02-11
Re: saving previous kernels.   

To be honest, I haven't done anything special to enable this.   I've been running 7.04 for awhile, and whenever a kernel fix is made available the software updater leaves the older ones around in the boot menu.  As of this time, I've got about four older kernels (and their recovery images) available.  IIRC, this was also the case in previous ubuntu releases.  

Sorry I couldn't shed more light on this, but I'm glad you've got sound again!

-K

---

### Post by parsim on 2008-02-11
Still no sound! I've tried rebooting into old kernels, recovery mode, reinstalling ALSA, and changing volume controls.

I can get the test tone noise out of System -> Preferences -> Sound when specifying "Multichannel Playback" for my SB Live card, but no other apps work with that set. Neither Autodetect nor "ADC Capture/Standard PCM Playback" (which is the default and should be used) can produce even the test tone.

Crazy. Can't play any of my music!

---

### Post by Stemman on 2008-02-12
My sound is all messed up on ubtuntu now.  It was working fine untill I plugged in headphones, this happened for BOTH my computers.  I get weird static when i push PCM volume up to max.  I plugged in headphones and poof, sound went gone.  It might be something unrelated but i have used headphones for the computer before with no problem swapping them in and out.

I don't know whats going on.  Its more annoying than anything else.

---

### Post by senshisteph on 2008-02-15
> **tibiker1966 said:**
> Ok, mine's working now.   I think that perhaps some setting got munged during the upgrade, not sure why it works, but here's what I did:

1) Rebooted into older ubuntu kernel release (using the boot menu).  Still no sound.  The microphone panel applet appeared muted (as it did on the latest upgrade), but this time I was able to Right-Click on it and brought up the volume control applet.

2) The applet showed that my master channel was muted.   Turned mute off - viola!  Sound!

3) rebooted back into newest ubuntu kernel - Sound is working fine now.

I've never turned on muting before, so somehow it was turned on during the upgrade.

-K

I was able to open the volume control applet without restarting into a previous version - none of the channels appeared muted, but I muted then unmuted 'master' and hey presto, sound!
Weird!

---

