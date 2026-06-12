---
title: "Longinsound repeating"
date: 2007-04-01
forum: Multimedia &amp; Video
---

### Post by blackslash on 2007-04-01
Hey, my sound if ****** up :)

Ok, so. Atm i get the login sound repeated about every one sec, so i hear the first two drumes, then it starts over again. And it never stops.

This started when my gnome wouldnt start, so i reconfigure gnome. The sound worked after that. Then it stoped working, but comes back after a reboot. Then, when im listening to music it suddenly sounds like when a computer crashes. The last thing that was played is played over and over again. At this point i reinstall ALSA, followed some guide i found, dont remember what i did. And now im here, with the loginsound drumes on repeat. This happend during one day.

Everything else works, just not the sound.

Im not sure what you guys what to know, so ill just give you some info:

OS: Ubuntu 6.10, 64bit
Soundcard: Creative Labs SB Audigy LS

lspci:
```
00:00.0 Host bridge: VIA Technologies, Inc. VT8385 [K8T800 AGP] Host Bridge (rev 01)
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI bridge [K8T800/K8T890 South]
00:07.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80)
00:09.0 Multimedia audio controller: Creative Labs SB Audigy LS
00:0e.0 Ethernet controller: Marvell Technology Group Ltd. 88E8001 Gigabit Ethernet Controller (rev 13)
00:0f.0 IDE interface: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: nVidia Corporation Unknown device 00f5 (rev a2)
```

modinfo soundcore
```
filename: /lib/modules/2.6.17-11-generic/kernel/sound/soundcore.ko
description: Core sound module
author: Alan Cox
license: GPL
alias: char-major-14-*
vermagic: 2.6.17-11-generic SMP mod_unload gcc-4.1
depends:
srcversion: C2D094BCAA551D6738DF488
```

Error when trying to test sound under System => Preferences => Sound:
```
audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink profile=music: Could not open resource for writing.
```

On another forum someone asked for lsmod, so here it is:
```
blackslash@blackslash-desktop:~$ lsmod
Module Size Used by
snd_rtctimer 5408 0
binfmt_misc 16012 1
rfcomm 51360 0
l2cap 31744 5 rfcomm
bluetooth 64644 4 rfcomm,l2cap
xt_limit 4608 8
xt_tcpudp 5376 15
iptable_mangle 4736 0
ipt_LOG 9216 8
ipt_MASQUERADE 5888 0
ip_nat 25260 1 ipt_MASQUERADE
ipt_TOS 3968 0
ipt_REJECT 7680 1
ip_conntrack_irc 9424 0
ip_conntrack_ftp 10704 0
xt_state 4096 6
ip_conntrack 66340 5 ipt_MASQUERADE,ip_nat,ip_conntrack_irc,ip_conntrack_ftp,xt_state
nfnetlink 10312 2 ip_nat,ip_conntrack
iptable_filter 4992 1
ip_tables 26024 2 iptable_mangle,iptable_filter
x_tables 22792 8 xt_limit,xt_tcpudp,ipt_LOG,ipt_MASQUERADE,ipt_TOS,ipt_REJECT,xt_state,ip_tables
cpufreq_userspace 6560 0
cpufreq_stats 9312 0
freq_table 7104 1 cpufreq_stats
cpufreq_powersave 3456 0
cpufreq_ondemand 10928 0
cpufreq_conservative 11272 0
video 22920 0
tc1100_wmi 10632 0
sbs 20928 0
sony_acpi 7704 0
pcc_acpi 19968 0
i2c_ec 7808 1 sbs
hotkey 14536 0
dev_acpi 17540 0
button 9888 0
battery 14088 0
container 6656 0
ac 8328 0
asus_acpi 21924 0
ipv6 334432 59
af_packet 29452 2
sbp2 29448 0
lp 16584 0
snd_ca0106 45828 4
snd_ac97_codec 127064 1 snd_ca0106
snd_pcm_oss 57344 0
snd_pcm 108168 4 snd_ca0106,snd_ac97_codec,snd_pcm_oss
snd_mixer_oss 22784 1 snd_pcm_oss
snd_seq_dummy 6020 0
snd_seq_oss 45824 0
snd_seq_midi 12160 0
snd_seq_midi_event 11520 2 snd_seq_oss,snd_seq_midi
nvidia 5444468 12
sg 44584 0
snd_mpu401 12200 0
snd_mpu401_uart 12928 1 snd_mpu401
snd_rawmidi 34432 3 snd_ca0106,snd_seq_midi,snd_mpu401_uart
psmouse 51088 0
tsdev 11136 0
evdev 14592 1
analog 14048 0
snd_seq 77344 6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer 31112 5 snd_rtctimer,snd_pcm,snd_seq
snd_seq_device 12180 5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd 79016 17 snd_ca0106,snd_ac97_codec,snd_pcm_oss,snd_pcm,snd_mixer_oss,snd_seq_oss,snd_mpu401,snd_mpu
401_uart,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore 14112 1 snd
serio_raw 10244 0
parport_pc 43560 1
parport 49932 2 lp,parport_pc
snd_ac97_bus 4352 1 snd_ac97_codec
gameport 21008 1 analog
shpchp 49068 0
pci_hotplug 38912 1 shpchp
i2c_viapro 11928 0
i2c_core 29312 3 i2c_ec,nvidia,i2c_viapro
snd_page_alloc 13200 2 snd_ca0106,snd_pcm
skge 47888 0
floppy 76648 0
pcspkr 5248 0
ext3 164880 2
jbd 74024 1 ext3
usbhid 51360 0
ehci_hcd 40456 0
uhci_hcd 30096 0
usbcore 167840 4 usbhid,ehci_hcd,uhci_hcd
ohci1394 40776 0
ieee1394 387704 2 sbp2,ohci1394
ide_generic 2944 0
ide_cd 39584 0
cdrom 43816 1 ide_cd
ide_disk 21248 0
via82cxxx 11780 0 [permanent]
sd_mod 25728 5
generic 7940 0
sata_via 12548 3
libata 88984 1 sata_via
scsi_mod 181424 4 sbp2,sg,sd_mod,libata
thermal 19472 0
processor 38280 1 thermal
fan 7432 0
vesafb 11048 0
capability 7304 0
commoncap 10752 1 capability
vga16fb 16656 1
cfbcopyarea 5376 2 vesafb,vga16fb
vgastate 10368 1 vga16fb
cfbimgblt 4352 2 vesafb,vga16fb
cfbfillrect 6272 2 vesafb,vga16fb
fbcon 45824 72
tileblit 4736 1 fbcon
font 10240 1 fbcon
bitblit 8064 1 fbcon
softcursor 3968 1 bitblit
```

Im new to ubuntu and linux, so basic things can be the problem. And please tell me if you want some other info.

Thx :)

---

### Post by blackslash on 2007-04-02
No one got an idea?

---

### Post by blackslash on 2007-04-12
Ok, so I got my sound working after copying back a esd.conf backup. (Followed [this guide.]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_configure_sound_to_work_properly_in_GNOME") ) After rebooting my sound was back. That was about one week ago.

Yesterday, when I booted my computer, I got the same problem as the first post. So now Im again sitting here with drums... So I still need help! :)

I got two new files where you might find something wrong? :)

/etc/esound/esd.conf:
```
auto_spawn=1
spawn_options=-terminate -nobeeps -as 5
spawn_wait_ms=100
# default options are used in spawned and non-spawned mode
default_options=
```

And /etc/asound.conf:
```
pcm.card0 {
type hw
card 0
}

pcm.!default {
type plug
slave.pcm "dmixer"
}

pcm.dmixer {
type dmix
ipc_key 1025
slave {
pcm "hw:0,0"
period_time 0
period_size 2048
buffer_size 32768
rate 48000
}
bindings {
0 0
1 1
}
}

```

Hope someone can help me :)

---

### Post by blackslash on 2007-04-19
Feels like im talking to myself here... Anyway. I got my sound back.... for one week. So I still got no sound atm...

Is it really no one who know what I can do? Or can tell me if it is a way to get all setting back to default?

EDIT: Ive just changed from gnome to KDE, if that matters...

Oh nvm, ill just install 7.04 -.-

---

### Post by beniro on 2007-04-28
Hello.

No, you're not talking to yourself.  I have the same issue.  I also get repeating noises when using other applications, too.  (Flash doesn't work well, either...has similar sound issues...not sure it's the same issue)

Wish I had a solution, though.

---

### Post by beniro on 2007-04-29
Try adding:

pnpbios=off

to the line you boot with in your Grub menu.lst.  That worked for me.

---

