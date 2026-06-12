---
title: "No Sound with Creative E-MU 0404"
date: 2008-01-28
forum: Multimedia &amp; Video
---

### Post by petesalty on 2008-01-28
I've just moved over to Linux after a long time with M$. Overall the experience has been pretty good - only drawback is that I can't get my Creative E-MU 0404 card to spit out any sound. Works fine with Windows 2K (the machine I'm using is dual boot), but won't work on Gutsy (7.10). I've followed half a dozen tutorials, but no dice. I've installed the latest ALSA drivers - alsa-driver-1.0.15 - which supposedly support this card. The following is system information

> 
sudo lshw -C sound

>   *-multimedia UNCLAIMED  
       description: Multimedia audio controller
       product: SB0400 Audigy2 Value
       vendor: Creative Labs
       physical id: 4
       bus info: pci@0000:05:04.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm cap_list
       configuration: latency=64 maxlatency=20 mingnt=2

> 
uname -a

> 
Linux development 2.6.22-14-generic #1 SMP Tue Dec 18 08:02:57 UTC 2007 i686 GNU/Linux


> lspci -v

> 00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub
        Subsystem: Dell Unknown device 01a7
        Flags: bus master, fast devsel, latency 0
        Capabilities: <access denied>

00:01.0 PCI bridge: Intel Corporation 82945G/GZ/P/PL PCI Express Root Port (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        I/O behind bridge: 0000d000-0000dfff
        Memory behind bridge: ed000000-efefffff
        Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff
        Capabilities: <access denied>

00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
        Memory behind bridge: ecf00000-ecffffff
        Capabilities: <access denied>

00:1c.4 PCI bridge: Intel Corporation 82801GR/GH/GHM (ICH7 Family) PCI Express Port 5 (rev 01) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
        Capabilities: <access denied>

00:1c.5 PCI bridge: Intel Corporation 82801GR/GH/GHM (ICH7 Family) PCI Express Port 6 (rev 01) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
        Capabilities: <access denied>

00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01) (prog-if 00 [UHCI])
        Subsystem: Dell Unknown device 01a7
        Flags: bus master, medium devsel, latency 0, IRQ 18
        I/O ports at ff80 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01) (prog-if 00 [UHCI])
        Subsystem: Dell Unknown device 01a7
        Flags: bus master, medium devsel, latency 0, IRQ 19
        I/O ports at ff60 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01) (prog-if 00 [UHCI])
        Subsystem: Dell Unknown device 01a7
        Flags: bus master, medium devsel, latency 0, IRQ 20
        I/O ports at ff40 [size=32]

00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01) (prog-if 00 [UHCI])
        Subsystem: Dell Unknown device 01a7
        Flags: bus master, medium devsel, latency 0, IRQ 21
        I/O ports at ff20 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01) (prog-if 20 [EHCI])
        Subsystem: Dell Unknown device 01a7
        Flags: bus master, medium devsel, latency 0, IRQ 18
        Memory at ffa80800 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1) (prog-if 01 [Subtractive decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=05, subordinate=05, sec-latency=32
        I/O behind bridge: 0000c000-0000cfff
        Memory behind bridge: ece00000-ecefffff
        Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
        Flags: bus master, medium devsel, latency 0
        Capabilities: <access denied>

00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01) (prog-if 8a [Master SecP PriP])
        Subsystem: Dell Unknown device 01a7
        Flags: bus master, medium devsel, latency 0, IRQ 16
        I/O ports at 01f0 [size=8]
        I/O ports at 03f4 [size=1]
        I/O ports at 0170 [size=8]
        I/O ports at 0374 [size=1]
        I/O ports at ffa0 [size=16]

00:1f.2 SATA controller: Intel Corporation 82801GR/GH (ICH7 Family) SATA AHCI Controller (rev 01) (prog-if 01 [AHCI 1.0])
        Subsystem: Dell Unknown device 01a7
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 22
        I/O ports at fe00 [size=8]
        I/O ports at fe10 [size=4]
        I/O ports at fe20 [size=8]
        I/O ports at fe30 [size=4]
        I/O ports at fea0 [size=32]
        Memory at effffc00 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>

00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
        Subsystem: Dell Unknown device 01a7
        Flags: medium devsel, IRQ 10
        I/O ports at ece0 [size=32]

01:00.0 VGA compatible controller: nVidia Corporation G71 [GeForce 7900 GS] (rev a1) (prog-if 00 [VGA])
        Subsystem: eVga.com. Corp. Unknown device c624
        Flags: bus master, fast devsel, latency 0, IRQ 11
        Memory at ed000000 (32-bit, non-prefetchable) [size=16M]
        Memory at d0000000 (64-bit, prefetchable) [size=256M]
        Memory at ee000000 (64-bit, non-prefetchable) [size=16M]
        I/O ports at dc80 [size=128]
        Expansion ROM at efe00000 [disabled] [size=128K]
        Capabilities: <access denied>

05:04.0 Multimedia audio controller: Creative Labs SB0400 Audigy2 Value
        Subsystem: Creative Labs Unknown device 4002
        Flags: medium devsel, IRQ 16
        I/O ports at cc80 [size=64]
        Capabilities: <access denied>

05:08.0 Ethernet controller: Intel Corporation 82801G (ICH7 Family) LAN Controller (rev 01)
        Subsystem: Dell Unknown device 01a7
        Flags: bus master, medium devsel, latency 64, IRQ 22
        Memory at eceff000 (32-bit, non-prefetchable) [size=4K]
        I/O ports at ccc0 [size=64]
        Capabilities: <access denied>


> aplay -l

> aplay: device_list:204: no soundcards found...

So, the system seems to see the card, but other than that I'm stumped. Can anyone help out here?

Pete

---

### Post by Metaljaz on 2008-01-28
Right click on the volume button in the top right hand corner. Open volume control and make sure that PCM is not muted. Mute PC speaker and Line in to start with.
Then again right click on the volume control button and select preferences. try selecting alsa mixer and then scroll down to PCM. Give that a try.

if all else fails try these troubleshooting threads/wiki:

[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

---

### Post by petesalty on 2008-01-28
Thanks for the advice, but selecting Open Volume Control from the right click menu produces the error message 

> 
No volume control GStreamer plugins and/or devices found

I've also tried both of those tutorials, and still no luck.

Pete

---

### Post by Metaljaz on 2008-01-28
This wiki should solve the problem.

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

Should install the gstreamer plugins needed

---

### Post by petesalty on 2008-01-28
Yes, but it's not a problem with the plugins (I've already installed this), it's a problem with the system not recognizing the soundcard as a soundcard, even though it finds it in the PCI port., So for example

> 
alsamixer

produces

> alsamixer: function snd_ctl_open failed for default: No such device

and 

> aplay -l

produces

> 
aplay: device_list:204: no soundcards found...

but the card is clearly recognized in the PCI port (as you'll see from my original post)

Pete

---

### Post by Metaljaz on 2008-01-28
I could be wrong but this still sounds like an alsa problem:

[http://alsa.opensrc.org/index.php/TroubleShooting](http://alsa.opensrc.org/index.php/TroubleShooting)

---

### Post by petesalty on 2008-01-28
Maybe this will help:

>  sudo lsmod

produces

> 
Module                  Size     Used by
isofs                      36412  0 
udf                         87204  1 
ipv6                  273892  17 
af_packet              24840  2 
rfcomm                 42136  2 
l2cap                  26240  11 rfcomm
bluetooth              57060  4 rfcomm,l2cap
ppdev                  10244  0 
cpufreq_userspace       5280  0 
cpufreq_ondemand        9612  0 
cpufreq_stats           7232  0 
freq_table              5792  2 cpufreq_ondemand,cpufreq_stats
cpufreq_conservative     8072  0 
cpufreq_powersave       2688  0 
sbs                    19592  0 
video                  18060  0 
button                  8976  0 
dock                   10656  0 
ac                      6148  0 
container               5504  0 
battery                11012  0 
parport_pc             37412  0 
lp                     12580  0 
parport                37448  3 ppdev,parport_pc,lp
snd_emu10k1_synth       8192  0 
snd_emux_synth         35456  1 snd_emu10k1_synth
snd_seq_virmidi         7936  1 snd_emux_synth
snd_seq_midi_emul       7680  1 snd_emux_synth
snd_emu10k1           140064  1 snd_emu10k1_synth
snd_ac97_codec        101284  1 snd_emu10k1
ac97_bus                3200  1 snd_ac97_codec
snd_pcm_oss            43008  0 
snd_mixer_oss          17664  1 snd_pcm_oss
snd_pcm                80004  3 snd_emu10k1,snd_ac97_codec,snd_pcm_oss
snd_page_alloc         11400  2 snd_emu10k1,snd_pcm
snd_util_mem            5760  2 snd_emux_synth,snd_emu10k1
snd_hwdep              10244  2 snd_emux_synth,snd_emu10k1
snd_seq_dummy           4740  0 
snd_seq_oss            33152  0 
snd_seq_midi            9600  0 
snd_rawmidi            25728  3 snd_seq_virmidi,snd_emu10k1,snd_seq_midi
snd_seq_midi_event      8448  3 snd_seq_virmidi,snd_seq_oss,snd_seq_midi
snd_seq                53360  9 snd_emux_synth,snd_seq_virmidi,snd_seq_midi_emul,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
usblp                  15104  0 
snd_timer              24324  3 snd_emu10k1,snd_pcm,snd_seq
snd_seq_device          9228  8 snd_emu10k1_synth,snd_emux_synth,snd_emu10k1,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
serio_raw               8068  0 
snd                    54788  13 snd_emux_synth,snd_seq_virmidi,snd_emu10k1,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd
i2c_core               26112  0 
psmouse                39952  0 
pcspkr                  4224  0 
iTCO_wdt               11940  0 
iTCO_vendor_support     4868  1 iTCO_wdt
intel_agp              25620  0 
agpgart                35016  1 intel_agp
shpchp                 34580  0 
pci_hotplug            32704  1 shpchp
evdev                  11136  3 
ext3                  133896  1 
jbd                    60456  1 ext3
mbcache                 9732  1 ext3
usb_storage            73024  0 
ide_core              116804  1 usb_storage
libusual               18448  1 usb_storage
sg                     36764  0 
sd_mod                 30336  3 
sr_mod                 17828  1 
cdrom                  37536  1 sr_mod
usbhid                 29536  0 
hid                    28928  1 usbhid
ata_generic             8452  0 
ata_piix               17540  1 
e100                   37644  0 
mii                     6528  1 e100
ahci                   23300  2 
libata                125168  3 ata_generic,ata_piix,ahci
scsi_mod              147084  5 usb_storage,sg,sd_mod,sr_mod,libata
ehci_hcd               36492  0 
uhci_hcd               26640  0 
usbcore               138632  7 usblp,usb_storage,libusual,usbhid,ehci_hcd,uhci_hcd
thermal                14344  0 
processor              32072  1 thermal
fan                     5764  0 
fuse                   47124  1 
apparmor               40728  0 
commoncap               8320  1 apparmor


Sorry, it's a little mashed up from the forum formatting.

---

### Post by petesalty on 2008-01-28
This might also help, it's the output from the aadebug script:

> ALSA Audio Debug v0.1.0 - Mon Jan 28 17:38:17 PST 2008
[http://alsa.opensrc.org/aadebug](http://alsa.opensrc.org/aadebug)
[http://www.gnu.org/licenses/gpl.txt](http://www.gnu.org/licenses/gpl.txt)

Kernel ----------------------------------------------------
Linux development 2.6.22-14-generic #1 SMP Tue Dec 18 08:02:57 UTC 2007 i686 GNU/Linux

Loaded Modules --------------------------------------------
snd_emu10k1_synth       8192  0 
snd_emux_synth         35456  1 snd_emu10k1_synth
snd_seq_virmidi         7936  1 snd_emux_synth
snd_seq_midi_emul       7680  1 snd_emux_synth
snd_emu10k1           140064  1 snd_emu10k1_synth
snd_ac97_codec        101284  1 snd_emu10k1
snd_pcm_oss            43008  0 
snd_mixer_oss          17664  1 snd_pcm_oss
snd_pcm                80004  3 snd_emu10k1,snd_ac97_codec,snd_pcm_oss
snd_page_alloc         11400  2 snd_emu10k1,snd_pcm
snd_util_mem            5760  2 snd_emux_synth,snd_emu10k1
snd_hwdep              10244  2 snd_emux_synth,snd_emu10k1
snd_seq_dummy           4740  0 
snd_seq_oss            33152  0 
snd_seq_midi            9600  0 
snd_rawmidi            25728  3 snd_seq_virmidi,snd_emu10k1,snd_seq_midi
snd_seq_midi_event      8448  3 snd_seq_virmidi,snd_seq_oss,snd_seq_midi
snd_seq                53360  9 snd_emux_synth,snd_seq_virmidi,snd_seq_midi_emul,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24324  3 snd_emu10k1,snd_pcm,snd_seq
snd_seq_device          9228  8 snd_emu10k1_synth,snd_emux_synth,snd_emu10k1,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54788  13 snd_emux_synth,snd_seq_virmidi,snd_emu10k1,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device

Modprobe Conf ---------------------------------------------
Warning: module config file does not exist
This means any kernel modules will not be auto loaded
See your linux distro docs on how to create this file

Proc Asound -----------------------------------------------
Advanced Linux Sound Architecture Driver Version 1.0.15rc3.
--- no soundcards ---
  2:        : timer
  3:        : sequencer
Client info
  cur  clients : 3
  peak clients : 3
  max  clients : 192

Client   0 : "System" [Kernel]
  Port   0 : "Timer" (Rwe-)
  Port   1 : "Announce" (R-e-)
    Connecting To: 15:0
Client  14 : "Midi Through" [Kernel]
  Port   0 : "Midi Through Port-0" (RWe-)
Client  15 : "OSS sequencer" [Kernel]
  Port   0 : "Receiver" (-we-)
    Connected From: 0:1

Dev Snd ---------------------------------------------------
seq  timer

CPU -------------------------------------------------------
model name      : Intel(R) Pentium(R) 4 CPU 3.00GHz
cpu MHz         : 2992.701
model name      : Intel(R) Pentium(R) 4 CPU 3.00GHz
cpu MHz         : 2992.701

RAM -------------------------------------------------------
MemTotal:      3374976 kB
SwapTotal:      899568 kB

Hardware --------------------------------------------------
00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub
05:04.0 Multimedia audio controller: Creative Labs SB0400 Audigy2 Value


---

### Post by petesalty on 2008-01-29
Anybody have any further ideas?

---

### Post by uBeer on 2008-02-04
Your card won't work with alsa 1.0.15 (is my experience).
For me the alsa 1.0.16rc1 does work for my EMU 0404 pci. Compiled it from source (driver, lib, utils and firmware).
There is some information on the alsa wiki about installing the drivers. If that isn't enough, just ask!
Good luck!

---

### Post by redhairfreerider on 2008-02-08
> **uBeer said:**
> Your card won't work with alsa 1.0.15 (is my experience).
For me the alsa 1.0.16rc1 does work for my EMU 0404 pci. Compiled it from source (driver, lib, utils and firmware).
There is some information on the alsa wiki about installing the drivers. If that isn't enough, just ask!
Good luck!

Hello, I have the exact same problem!Tried to install 1.0.16 but have problem trying to "make" the util package!i get this error message

ing all in include
make[1]: Entering directory `/home/redhairfreerider/downloads/alsa-utils-1.0.16/include'
make  all-am
make[2]: Entering directory `/home/redhairfreerider/downloads/alsa-utils-1.0.16/include'
make[2]: Leaving directory `/home/redhairfreerider/downloads/alsa-utils-1.0.16/include'
make[1]: Leaving directory `/home/redhairfreerider/downloads/alsa-utils-1.0.16/include'
Making all in alsactl
make[1]: Entering directory `/home/redhairfreerider/downloads/alsa-utils-1.0.16/alsactl'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/redhairfreerider/downloads/alsa-utils-1.0.16/alsactl'
Making all in alsaconf
make[1]: Entering directory `/home/redhairfreerider/downloads/alsa-utils-1.0.16/alsaconf'
Making all in po
make[2]: Entering directory `/home/redhairfreerider/downloads/alsa-utils-1.0.16/alsaconf/po'
mv: cannot stat `t-ja.gmo': No such file or directory
make[2]: *** [ja.gmo] Error 1
make[2]: Leaving directory `/home/redhairfreerider/downloads/alsa-utils-1.0.16/alsaconf/po'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/redhairfreerider/downloads/alsa-utils-1.0.16/alsaconf'
make: *** [all-recursive] Error 1
 Do you have any suggestions cause you seem to have 0404 working!Thanks for your time an please keep it simple cause I just  switched to Ubuntu and linux in general

---

### Post by uBeer on 2008-02-15
I have the same problem, it happens when trying to make the utils package.
But that should be no problem if you've compiled and installed the rest. The only thing you'll have to do is:
```
 modprobe snd-emu10k1 ; modprobe snd-pcm-oss ; modprobe snd-mixer-oss ; modprobe snd-seq-oss

```
You'll probably have to run it with superuser rights (sudo).
After this log out and in (or reboot) and you'll have your sound working!

---

