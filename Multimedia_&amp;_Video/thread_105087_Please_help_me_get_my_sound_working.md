---
title: "Please help me get my sound working"
date: 2005-12-17
forum: Multimedia &amp; Video
---

### Post by KittyCat on 2005-12-17
I am a new Linux user with an equally new install of the 5.10 32-bit version. I've been scouring the forums to learn all I can about my system and Linux, but a lot of this is over my head. So far, I have gotten everything working-except for my sound card, a SB Audigy 4. For some reason the system reads the card as an Audigy 2 Value. I have no sound at all in any application or system sounds. MP3's and CD's play in XMMS and Amarok, but there's no sound output. Same thing for DVD's in Totem and MPlayer. The speakers are connected, they work fine in XP. I have onboard sound as well as the sound card, and the onboard sound is disabled in BIOS. 

Here's my lspci:

kelly@ubuntu:~$ lspci
0000:00:00.0 Host bridge: VIA Technologies, Inc.: Unknown device 0238
0000:00:00.1 Host bridge: VIA Technologies, Inc.: Unknown device 1238
0000:00:00.2 Host bridge: VIA Technologies, Inc.: Unknown device 2238
0000:00:00.3 Host bridge: VIA Technologies, Inc.: Unknown device 3238
0000:00:00.4 Host bridge: VIA Technologies, Inc.: Unknown device 4238
0000:00:00.5 PIC: VIA Technologies, Inc.: Unknown device 5238
0000:00:00.7 Host bridge: VIA Technologies, Inc.: Unknown device 7238
0000:00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI bridge [K8T800 South]0000:00:02.0 PCI bridge: VIA Technologies, Inc.: Unknown device a238
0000:00:03.0 PCI bridge: VIA Technologies, Inc.: Unknown device c238
0000:00:03.1 PCI bridge: VIA Technologies, Inc.: Unknown device d238
0000:00:03.2 PCI bridge: VIA Technologies, Inc.: Unknown device e238
0000:00:03.3 PCI bridge: VIA Technologies, Inc.: Unknown device f238
0000:00:05.0 VGA compatible controller: nVidia Corporation: Unknown device 0343 (rev a1)
0000:00:09.0 Multimedia audio controller: Creative Labs: Unknown device 0008
0000:00:0f.0 RAID bus controller: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
0000:00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
0000:00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
0000:00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
0000:00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
0000:00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
0000:00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
0000:00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [K8T800 South]0000:00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
0000:00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge

My lsmod | grep snd

My kelly@ubuntu:~$ lsmod | grep snd
snd_emu10k1_synth       6528  0
snd_emux_synth         31744  1 snd_emu10k1_synth
snd_seq_virmidi         6912  1 snd_emux_synth
snd_seq_midi_emul       6528  1 snd_emux_synth
snd_seq_dummy           3844  0
snd_seq_oss            29440  0
snd_seq_midi            8608  0
snd_seq_midi_event      6656  3 snd_seq_virmidi,snd_seq_oss,snd_seq_midi
snd_seq                44688  9 snd_emux_synth,snd_seq_virmidi,snd_seq_midi_emul,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_emu10k1            96772  3 snd_emu10k1_synth
snd_rawmidi            22816  3 snd_seq_virmidi,snd_seq_midi,snd_emu10k1
snd_seq_device          8204  8 snd_emu10k1_synth,snd_emux_synth,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq,snd_emu10k1,snd_rawmidi
snd_ac97_codec         72188  1 snd_emu10k1
snd_pcm_oss            46368  0
snd_mixer_oss          16128  1 snd_pcm_oss
snd_pcm                78344  3 snd_emu10k1,snd_ac97_codec,snd_pcm_oss
snd_timer              21764  3 snd_seq,snd_emu10k1,snd_pcm
snd_page_alloc         10120  2 snd_emu10k1,snd_pcm
snd_util_mem            4480  2 snd_emux_synth,snd_emu10k1
snd_hwdep               8608  2 snd_emux_synth,snd_emu10k1
snd                    48644  17 snd_emux_synth,snd_seq_virmidi,snd_seq_oss,snd_seq,snd_emu10k1,snd_rawmidi,snd_seq_device,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_hwdep
soundcore               9184  1 snd

And my lsmod

kelly@ubuntu:~$ lsmod
Module                  Size  Used by
isofs                  32824  0
udf                    75524  0
nls_utf8                2176  1
rfcomm                 34972  0
l2cap                  22404  5 rfcomm
bluetooth              43012  4 rfcomm,l2cap
powernow_k8            11528  0
cpufreq_userspace       4444  1
cpufreq_stats           5124  0
freq_table              4484  2 powernow_k8,cpufreq_stats
cpufreq_powersave       1920  0
cpufreq_ondemand        5916  0
cpufreq_conservative     6820  0
apm                    19308  1
ipv6                  217408  6
af_packet              20232  2
floppy                 52692  0
pcspkr                  3652  0
rtc                    11832  0
usblp                  11776  0
i2c_viapro              7696  0
i2c_core               19728  1 i2c_viapro
snd_emu10k1_synth       6528  0
snd_emux_synth         31744  1 snd_emu10k1_synth
snd_seq_virmidi         6912  1 snd_emux_synth
snd_seq_midi_emul       6528  1 snd_emux_synth
snd_seq_dummy           3844  0
snd_seq_oss            29440  0
snd_seq_midi            8608  0
snd_seq_midi_event      6656  3 snd_seq_virmidi,snd_seq_oss,snd_seq_midi
snd_seq                44688  9 snd_emux_synth,snd_seq_virmidi,snd_seq_midi_emul,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_emu10k1            96772  2 snd_emu10k1_synth
snd_rawmidi            22816  3 snd_seq_virmidi,snd_seq_midi,snd_emu10k1
snd_seq_device          8204  8 snd_emu10k1_synth,snd_emux_synth,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq,snd_emu10k1,snd_rawmidi
snd_ac97_codec         72188  1 snd_emu10k1
snd_pcm_oss            46368  0
snd_mixer_oss          16128  1 snd_pcm_oss
snd_pcm                78344  3 snd_emu10k1,snd_ac97_codec,snd_pcm_oss
snd_timer              21764  3 snd_seq,snd_emu10k1,snd_pcm
snd_page_alloc         10120  2 snd_emu10k1,snd_pcm
snd_util_mem            4480  2 snd_emux_synth,snd_emu10k1
snd_hwdep               8608  2 snd_emux_synth,snd_emu10k1
snd                    48644  15 snd_emux_synth,snd_seq_virmidi,snd_seq_oss,snd_seq,snd_emu10k1,snd_rawmidi,snd_seq_device,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_hwdep
soundcore               9184  1 snd
pci_hotplug            24628  0
amd64_agp              11464  1
agpgart                32328  1 amd64_agp
nls_iso8859_1           4224  2
nls_cp437               5888  3
vfat                   12288  3
fat                    46492  1 vfat
dm_mod                 50364  1
tsdev                   7616  0
evdev                   9088  0
psmouse                26116  0
mousedev               10912  1
parport_pc             31812  0
lp                     11460  0
parport                32072  2 parport_pc,lp
md                     40656  0
ext3                  115976  1
jbd                    48536  1 ext3
processor              23100  1 powernow_k8
sd_mod                 17424  4
usb_storage            64704  2
via_rhine              20356  0
mii                     5248  1 via_rhine
ehci_hcd               29448  0
uhci_hcd               28048  0
usbcore               104316  5 usblp,usb_storage,ehci_hcd,uhci_hcd
sata_via                8836  3
libata                 47876  1 sata_via
scsi_mod              124872  3 sd_mod,usb_storage,libata
ide_cd                 36996  0
cdrom                  33952  1 ide_cd
ide_disk               16128  5
ide_generic             1664  0
via82cxxx              12188  1
ide_core              125268  5 usb_storage,ide_cd,ide_disk,ide_generic,via82cxxx
unix                   24624  644
vesafb                  8088  0
capability              5000  0
commoncap               6784  1 capability
vga16fb                12232  1
vgastate                8320  1 vga16fb
softcursor              2432  2 vesafb,vga16fb
cfbimgblt               2944  2 vesafb,vga16fb
cfbfillrect             3840  2 vesafb,vga16fb
cfbcopyarea             4480  2 vesafb,vga16fb
fbcon                  34176  72
tileblit                2560  1 fbcon
font                    8448  1 fbcon
bitblit                 5248  1 fbcon


Here's what I've done so far:

I went into Alsamixer and unmuted and turned up the volume on everything. When I unmuted the Audigy Analog/Digital Output jack, there was a "thump" from the speakers. I thought I was home free, but there's still no sound. Interestingly, when I reboot, I get the same thump when Alsa shuts down or starts up.

Alsa is selected in both catagories in the Multimedia selector.

In Volume Control, the Audigy card is labeled "Audigy 2 Value [Unknown] (Alsa Mixer). There's also a SigmaTel STAC9750,51 (OSS Mixer.) I have selected the Audigy. 

I've read to both select and deselect the "Enable Sound Server Startup" in System-> Preferences-> Sound. I've tried it both ways and nothing happens.

I've stopped ESD with the killall command.


I followed the "No Sound Troubleshooting Guide" at:[http://linux.iuplog.com/default.asp?item=94639]("http://linux.iuplog.com/default.asp?item=94639")

Since Ubuntu seems to detect my card I checked the chmod of /dev/dsp. I typed:

kelly@ubuntu:~$ sudo xmms
Message: device: default
- using device default
- using device default
Audio device open for 44.1Khz, stereo, 16bit failed
Trying 44.1Khz, 8bit stereo.
Audio device open for 44.1Khz, stereo, 8bit failed
Trying 48Khz, 16bit stereo.

It opened XMMS, but there was no sound.

I did the following:

"Run alsamixer and turn off IEC related options."
 I did this both in alsamixer and volume control, after restarting no sound.

I read: 
[http://wiki.ubuntu.com/SoundProblemsHoary]("http://wiki.ubuntu.com/SoundProblemsHoary") and changed the /etc/esound/esd.conf to read:

[esd] 
auto_spawn=0
spawn_wait_ms=100
default_options= -terminate -nobeeps -as 2

I logged out and back in, and got no sound.

In XMMS, it said to "press ctrl+p and select libesdout.so as the output plugin and click apply." I did this and restarted XMMS-no sound.


I then went to:[www.ubuntuforums.org/showthread.php?t=26567and](www.ubuntuforums.org/showthread.php?t=26567and) read through the thread. I followed the directions and did this:

kelly@ubuntu:~$ sudo killall esd
kelly@ubuntu:~$ lsof /dev/dsp
lsof: WARNING: can't stat() ext3 file system /dev/.static/dev
      Output information may be incomplete.


Next I did:

kelly@ubuntu:~$ lsof /dev/snd/*
lsof: WARNING: can't stat() ext3 file system /dev/.static/dev
      Output information may be incomplete.
COMMAND     PID  USER   FD   TYPE DEVICE SIZE NODE NAME
mixer_app 11692 kelly   35u   CHR  116,0      7872 /dev/snd/controlC0

I have no idea what this means or if it's the right output.



The next section said to edit the /etc/esound/esd.conf to read:

[esd]
auto_spawn=1
spawn_options=-terminate -nobeeps -as 2 -d default
spawn_wait_ms=100
# default options are used in spawned and non-spawned mode
default_options=

I did this and restarted, and as usual no sound.


I followed the links in a post to this page:[http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Creative+Labs&card=Sound+Blaster+Audigy4+Pro.&chip=emu10k2%2C+CA0151%2FP16V&module=emu10k1]("http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Creative+Labs&card=Sound+Blaster+Audigy4+Pro.&chip=emu10k2%2C+CA0151%2FP16V&module=emu10k1").

I didn't understand all this was telling me, but I followed the directions as best I could.

I don't have the Pro version but I thought it might work. The instructions said to modinfo soundcore:

kelly@ubuntu:~$ sudo modprobe
Usage: modprobe [-v] [-V] [-C config-file] [-n] [-i] [-q] [-o <modname>] <modname> [parameters...]
modprobe -r [-n] [-i] [-v] <modulename> ...
modprobe -l -t <dirname> [ -a <modulename> ...]
kelly@ubuntu:~$ modinfo soundcore
filename:       /lib/modules/2.6.12-10-386/kernel/sound/soundcore.ko
description:    Core sound module
author:         Alan Cox
license:        GPL
alias:          char-major-14-*
vermagic:       2.6.12-10-386 386 gcc-3.4
depends:
srcversion:     E11490DC3F523551C4C2A6D

Per the directions, I didn't need to recompile the kernel. (Thank heaven) 

I pasted the following to my /etc/modules.conf file, then logged in and out. No luck and no sound.

# ALSA portion
        alias char-major-116 snd
        alias snd-card-0 snd-emu10k1
	# module options should go here

        # OSS/Free portion
        alias char-major-14 soundcore
        alias sound-slot-0 snd-card-0
	
	# card #1
	alias sound-service-0-0 snd-mixer-oss
	alias sound-service-0-1 snd-seq-oss
	alias sound-service-0-3 snd-pcm-oss
	alias sound-service-0-8 snd-seq-oss
	alias sound-service-0-12 snd-pcm-oss

The rest of the page might as well have been written in another language, so I didn't do anything else.

I decided to see if I could get my onboard sound working at least. I enabled the card in BIOS, and now in Volume Control, As well as the Audigy and SigmalTeL entry, there's now an entry for VIA 8237 (Alsa Mixer), and Realtek ALC655 rev 0 (OSS Mixer). I chose the VIA entry and then re-ran lspci and got the following:

kelly@ubuntu:~$ lspci
0000:00:00.0 Host bridge: VIA Technologies, Inc.: Unknown device 0238
0000:00:00.1 Host bridge: VIA Technologies, Inc.: Unknown device 1238
0000:00:00.2 Host bridge: VIA Technologies, Inc.: Unknown device 2238
0000:00:00.3 Host bridge: VIA Technologies, Inc.: Unknown device 3238
0000:00:00.4 Host bridge: VIA Technologies, Inc.: Unknown device 4238
0000:00:00.5 PIC: VIA Technologies, Inc.: Unknown device 5238
0000:00:00.7 Host bridge: VIA Technologies, Inc.: Unknown device 7238
0000:00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI bridge [K8T800 South]
0000:00:02.0 PCI bridge: VIA Technologies, Inc.: Unknown device a238
0000:00:03.0 PCI bridge: VIA Technologies, Inc.: Unknown device c238
0000:00:03.1 PCI bridge: VIA Technologies, Inc.: Unknown device d238
0000:00:03.2 PCI bridge: VIA Technologies, Inc.: Unknown device e238
0000:00:03.3 PCI bridge: VIA Technologies, Inc.: Unknown device f238
0000:00:05.0 VGA compatible controller: nVidia Corporation: Unknown device 0343 (rev a1)
0000:00:09.0 Multimedia audio controller: Creative Labs: Unknown device 0008
0000:00:0f.0 RAID bus controller: VIA Technologies, Inc. VIA VT6420 SATA RAID Co ntroller (rev 80)
0000:00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT82 3x/A/C PIPC Bus Master IDE (rev 06)
0000:00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Contr oller (rev 81)
0000:00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Contr oller (rev 81)
0000:00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Contr oller (rev 81)
0000:00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Contr oller (rev 81)
0000:00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
0000:00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [K8T800 South]
0000:00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8 237 AC97 Audio Controller (rev 60)
0000:00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
0000:00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge

After restarting no sound.



I've tried to solve this problem on my own, but I'm at a loss as to what to do next. If I can get this problem fixed I can ditch XP forever, but I listen to music constantly when I'm on my computer, and no sound means no Linux. I'm really desperate to fix this, and I would love some help here.

---

### Post by veganalex on 2005-12-18
on the site that i looked at it said you needed to add the:

#ALSA portion
alias char-major-116 snd
alias snd-card-0 snd-emu10k1
#module options should go here

#OSS/free portion
alias char-major-14 soundcore
alias sound-slot-0 snd-core-0

#card #1
alias sound-service-0-0 snd-mixer-oss
alias sound-service-0-1 snd-seq-oss
alias sound-service-0-3 snd-pcm-oss
alias sound-service-0-8 snd-seq-oss
alias sound-service-0-12 snd-pcm-oss

to a file in /etc/modutils (i.e. /etc/modutils/alsa) - it says that you have to do this, if your distro is debian based - which ubuntu is.

veganalex

---

### Post by KittyCat on 2005-12-18
Veganalex, thanks for responding. 

I did sudo gedit /etc/modutils/ directory, and got this error - Could not open the file "/etc/modutils/ directory." The file you are trying to open is not a regular file.

The sentence also says "(Eg. /etc/modutils/alsa)". I don't know if this means I should add it to this file, but that's what I did. It then said to update modules. Per the instructions, I ran sudo update-modules and restarted. No sound... Any other ideas?

---

### Post by cvmostert on 2005-12-31
Hi there, i also have a VIA sound card onboard and dont have sound... 

i have heard of someone who by playing around with alsamixer have solved the problem for the 8237, i have the 8235 and still have nosound :-(

looks like you have a VIA and creative labs sound card installed, make sure that your onboard card is deactivated in the BIOS, will probably work.

---

### Post by handy on 2006-01-01
After killing on board sound, & using the info here: 

[http://ubuntuforums.org/showthread.php?t=44753](http://ubuntuforums.org/showthread.php?t=44753)

No prob's :KS 

handy

---

