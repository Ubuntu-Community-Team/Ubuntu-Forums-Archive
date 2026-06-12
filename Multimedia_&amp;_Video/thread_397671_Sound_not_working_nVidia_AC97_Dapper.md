---
title: "Sound not working nVidia AC97 Dapper"
date: 2007-03-30
forum: Multimedia &amp; Video
---

### Post by opus1 on 2007-03-30
Hello,

I have a machine I put together with an ASUS motherboard.  The sound worked with Windows, but now doesn't with Dapper.  I've followed the comprehensive sound troubleshooting guide down to the part where it recommends kernel mods and decided to look for other alternatives.  Pardon the long post, but I realize all of this information is important.

*cat /etc/lsb-release*
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=6.06
DISTRIB_CODENAME=dapper
DISTRIB_DESCRIPTION="Ubuntu 6.06.1 LTS"

*sudo asoundconf list*
Names of available sound cards:
nForce2
UART

*sudo lspci -v*
0000:00:00.0 Host bridge: nVidia Corporation nForce2 AGP (different version?) (rev a2)
        Subsystem: ASUSTeK Computer Inc.: Unknown device 80ac
        Flags: bus master, 66MHz, fast devsel, latency 0
        Memory at d0000000 (32-bit, prefetchable) [size=128M]
        Capabilities: [40] AGP version 3.0
        Capabilities: [60] #08 [2001]

0000:00:00.1 RAM memory: nVidia Corporation nForce2 Memory Controller 1 (rev a2)        Subsystem: ASUSTeK Computer Inc.: Unknown device 80ac
        Flags: 66MHz, fast devsel

0000:00:00.2 RAM memory: nVidia Corporation nForce2 Memory Controller 4 (rev a2)        Subsystem: ASUSTeK Computer Inc.: Unknown device 80ac
        Flags: 66MHz, fast devsel

0000:00:00.3 RAM memory: nVidia Corporation nForce2 Memory Controller 3 (rev a2)        Subsystem: ASUSTeK Computer Inc.: Unknown device 80ac
        Flags: 66MHz, fast devsel

0000:00:00.4 RAM memory: nVidia Corporation nForce2 Memory Controller 2 (rev a2)        Subsystem: ASUSTeK Computer Inc.: Unknown device 80ac
        Flags: 66MHz, fast devsel

0000:00:00.5 RAM memory: nVidia Corporation nForce2 Memory Controller 5 (rev a2)        Subsystem: ASUSTeK Computer Inc.: Unknown device 80ac
        Flags: 66MHz, fast devsel

0000:00:01.0 ISA bridge: nVidia Corporation nForce2 ISA Bridge (rev a3)
        Subsystem: ASUSTeK Computer Inc. A7N8X Mainboard
        Flags: bus master, 66MHz, fast devsel, latency 0
        Capabilities: [48] #08 [01e1]

0000:00:01.1 SMBus: nVidia Corporation nForce2 SMBus (MCP) (rev a2)
        Subsystem: ASUSTeK Computer Inc.: Unknown device 0c11
        Flags: 66MHz, fast devsel, IRQ 11
        I/O ports at ec00 [size=32]
        Capabilities: [44] Power Management version 2

0000:00:02.0 USB Controller: nVidia Corporation nForce2 USB Controller (rev a3) (prog-if 10 [OHCI])
        Subsystem: ASUSTeK Computer Inc. A7N8X Mainboard
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 177
        Memory at ea003000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: [44] Power Management version 2

0000:00:02.1 USB Controller: nVidia Corporation nForce2 USB Controller (rev a3) (prog-if 10 [OHCI])
        Subsystem: ASUSTeK Computer Inc. A7N8X Mainboard
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 185
        Memory at ea004000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: [44] Power Management version 2

0000:00:02.2 USB Controller: nVidia Corporation nForce2 USB Controller (rev a3) (prog-if 20 [EHCI])
        Subsystem: ASUSTeK Computer Inc. A7N8X Mainboard
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 193
        Memory at ea000000 (32-bit, non-prefetchable) [size=256]
        Capabilities: [44] #0a [2080]
        Capabilities: [80] Power Management version 2

0000:00:04.0 Ethernet controller: nVidia Corporation nForce2 Ethernet Controller (rev a1)
        Subsystem: ASUSTeK Computer Inc. A7N8X Mainboard onboard nForce2 Ethernet
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 177
        Memory at ea001000 (32-bit, non-prefetchable) [size=4K]
        I/O ports at e000 [size=8]
        Capabilities: [44] Power Management version 2

0000:00:06.0 Multimedia audio controller: nVidia Corporation nForce2 AC97 Audio Controler (MCP) (rev a1)
        Subsystem: ASUSTeK Computer Inc.: Unknown device 8095
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 185
        I/O ports at e400 [size=256]
        I/O ports at e800 [size=128]
        Memory at ea002000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: [44] Power Management version 2

0000:00:08.0 PCI bridge: nVidia Corporation nForce2 External PCI Bridge (rev a3) (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, fast devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=32

0000:00:09.0 IDE interface: nVidia Corporation nForce2 IDE (rev a2) (prog-if 8a [Master SecP PriP])
        Subsystem: ASUSTeK Computer Inc.: Unknown device 0c11
        Flags: bus master, 66MHz, fast devsel, latency 0
        I/O ports at f000 [size=16]
        Capabilities: [44] Power Management version 2

0000:00:1e.0 PCI bridge: nVidia Corporation nForce2 AGP (rev a2) (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, medium devsel, latency 32
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=32
        I/O behind bridge: 0000d000-0000dfff
        Memory behind bridge: e8000000-e9ffffff
        Prefetchable memory behind bridge: d8000000-e7ffffff

0000:02:00.0 VGA compatible controller: ATI Technologies Inc Radeon R300 NE [Radeon 9500 Pro] (prog-if 00 [VGA])
        Subsystem: ATI Technologies Inc Radeon R300 NE [Radeon 9500 Pro]
        Flags: bus master, stepping, 66MHz, medium devsel, latency 32, IRQ 201
        Memory at d8000000 (32-bit, prefetchable) [size=128M]
        I/O ports at d000 [size=256]
        Memory at e9000000 (32-bit, non-prefetchable) [size=64K]
        Expansion ROM at e8000000 [disabled] [size=128K]
        Capabilities: [58] AGP version 3.0
        Capabilities: [50] Power Management version 2

0000:02:00.1 Display controller: ATI Technologies Inc Radeon R300 [Radeon 9500 Pro] (Secondary)
        Subsystem: ATI Technologies Inc Radeon R300 NE [Radeon 9500 Pro]
        Flags: stepping, 66MHz, medium devsel
        Memory at e0000000 (32-bit, prefetchable) [disabled] [size=128M]
        Memory at e9010000 (32-bit, non-prefetchable) [disabled] [size=64K]
        Capabilities: [50] Power Management version 2

*sudo lsmod*
Module                  Size  Used by
rfcomm                 40216  0
l2cap                  26244  5 rfcomm
bluetooth              50020  4 rfcomm,l2cap
ppdev                   9220  0
radeon                116000  1
drm                    73236  2 radeon
cpufreq_userspace       4696  0
cpufreq_stats           5636  0
freq_table              4740  1 cpufreq_stats
cpufreq_powersave       1920  0
cpufreq_ondemand        6428  0
cpufreq_conservative     7332  0
video                  16260  0
tc1100_wmi              6916  0
sony_acpi               5644  0
pcc_acpi               12416  0
hotkey                 11556  0
dev_acpi               11140  0
container               4608  0
button                  6672  0
acpi_sbs               19980  0
battery                 9988  1 acpi_sbs
ac                      5252  1 acpi_sbs
i2c_acpi_ec             5120  1 acpi_sbs
ipv6                  265856  8
af_packet              22920  0
dm_mod                 58936  1
md_mod                 72532  0
lp                     11844  0
tsdev                   8000  0
analog                 12320  0
snd_mpu401              6728  0
snd_mpu401_uart         7808  1 snd_mpu401
snd_rawmidi            25504  1 snd_mpu401_uart
parport_pc             35780  1
parport                36296  3 ppdev,lp,parport_pc
gameport               15496  1 analog
snd_seq_device          8716  1 snd_rawmidi
psmouse                36100  0
floppy                 62148  0
rtc                    13492  0
serio_raw               7300  0
snd_intel8x0           33692  3
snd_ac97_codec         93216  1 snd_intel8x0
snd_ac97_bus            2304  1 snd_ac97_codec
pcspkr                  2180  0
snd_pcm_oss            53664  0
snd_mixer_oss          18688  1 snd_pcm_oss
snd_pcm                89864  4 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              25220  2 snd_pcm
shpchp                 45632  0
pci_hotplug            29236  1 shpchp
snd                    55268  14 snd_mpu401,snd_mpu401_uart,snd_rawmidi,snd_seq_device,snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              10208  1 snd
snd_page_alloc         10632  2 snd_intel8x0,snd_pcm
nvidia_agp              8348  1
i2c_nforce2             6912  0
i2c_core               21904  2 i2c_acpi_ec,i2c_nforce2
forcedeth              30732  0
agpgart                34888  2 drm,nvidia_agp
evdev                   9856  1
ext3                  135944  1
jbd                    58772  1 ext3
ide_generic             1536  0
ehci_hcd               34184  0
ohci_hcd               21892  0
usbcore               130820  3 ehci_hcd,ohci_hcd
ide_cd                 33028  0
cdrom                  38560  1 ide_cd
ide_disk               17664  3
generic                 5124  0
amd74xx                15260  0 [permanent]
sata_nv                 9732  0
libata                 78992  1 sata_nv
scsi_mod              139496  1 libata
thermal                13576  0
processor              23360  1 thermal
fan                     4868  0
capability              5000  0
commoncap               7296  1 capability
vga16fb                13704  1
vgastate               10368  1 vga16fb
fbcon                  42784  72
tileblit                2816  1 fbcon
font                    8320  1 fbcon
bitblit                 6272  1 fbcon
softcursor              2304  1 bitblit

*dpkg -l | grep linux-sound-base*
ii  linux-sound-base                       1.0.10-4ubuntu4       base package for ALSA and OSS sound systems

*dpkg -l |grep alsa*
ii  alsa-base                              1.0.10-4ubuntu4       ALSA driver configuration files
ii  alsa-utils                             1.0.10-1ubuntu14       ALSA utilities
ii  gstreamer0.10-alsa                     0.10.7-0ubuntu5       GStreamer plugin for ALSA
ii  libesd-alsa0                           0.2.36-3ubuntu3       Enlightened Sound Daemon (ALSA) - Shared lib
ii  libpt-plugins-alsa                     1.10.0-1ubuntu1       Portable Windows Library Audio Plugin for th
ii  libsdl1.2debian-alsa                   1.2.9-0.0ubuntu2       Simple DirectMedia Layer (with X11 and ALSA


I disabled the onboard modem in the BIOS since I read that can cause conflicts.  I also confirmed that the snd_intel8x0m driver is blacklisted.  Tried the kubuntu live CD with no luck.  Speakers plugged in, everything unmuted.  I'm just baffled.   I'm sure it's something obvious that I'm glazing over now.  

Thanks for any help you can give!

---

### Post by dnns on 2007-03-31
Are you using the SPDIF output of your soundcard? If so then the only way that it worked for me (I have the same motherboard) is to forego NVIDIA's 'obsolete' nforce audio drivers and go with ALSA, thereby editing your asound.conf or asoundrc to redirect all your analog outputs to the digital one (IEC958) and use software sound mixing. A wonderful waste of the potential of the SoundStorm chipset, I know, but you must blame Nvidia for that.

---

### Post by opus1 on 2007-03-31
Thanks for replying so fast!

I'm a little embarassed, but I don't know if I'm using the SPDIF output or not.  I'm a noob when it comes to sound.  Since I haven't had any problems with any of my other computers, I haven't really learned much about it! :) 
  
So, If you don't mind telling me how to check I'll look and let you know. 

Thanks again!

---

### Post by ed_d on 2007-03-31
I have just acquired an Intellistation M Pro, and it uses the AC'97 Intel based sound on it, built in. I have followed the comprehensive guide, and all my outputs show that I have the driver loaded, but still no sound. What info do You need from me to assist in helping me out. I know I could just throw in another card, but would like to use whats available already. TIA
Ed

Edit:
Well, I put in a different sound card, all is great now. But if someone could remedy this "bug" that would be nice.

---

### Post by opus1 on 2007-04-01
Ed,

What sound card did you use?  I don't mind buying a sound card if I know it's going to work...

Anyone out there had any problems with Creative Sound Blaster 16's?  While I'd rather trouble shoot and get the on-board card working (just to see if I can do it if nothing else), my schedule for the next 6-8 months won't allow me to spend that kind of time.

---

### Post by ed_d on 2007-04-01
Ensoniq audio card. Had it for a while now and seems to work well. You know when they are old if they still have the 15 pin joystick port on them.

---

