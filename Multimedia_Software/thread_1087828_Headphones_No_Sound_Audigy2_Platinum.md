---
title: "Headphones No Sound Audigy2 Platinum"
date: 2009-03-05
forum: Multimedia Software
---

### Post by Le-Dart on 2009-03-05
I know this 'problem' has other threads but none of the one's I've looked at or Googled have been of any help. Other than to make me more confused.
I'm running Ubuntu 8.10. My sound card is an Audigy 2 Platinum, with a front control/connection panel. 

When I installed 8.10 a couple of months ago I couldn't get any sound at all through my 5.1 speakers. I checked here and found a thread that advised removing pulseaudio and installing esound. I did this and immediately after had 5.1 sound with each speaker set, front, centre, surround, seperately controllable. Great!

I've just had a pair of headphones bought for me. I plugged them into the front headphone socket. No sound through them. The speakers continue to work ok.

When I used to run Windows on this hardware, a few years ago now, the speakers used to mute when I plugged in headphones.

I have tried some of the advice I've found without success. I've also checked all the relevant connections between the soundcard and front panel and confirmed the headphones work.

In the Volume control there isn't a headphone option and none of the other 'sliders' make any difference when I try them.

The motherboard onboard sound is disabled in the BIOS so there's no conflict from there.

From some of the other threads I've read people have asked for  more info so here we are:

lspci && lsmod 

00:00.0 Host bridge: nVidia Corporation nForce2 IGP2 (rev c1)
00:00.1 RAM memory: nVidia Corporation nForce2 Memory Controller 1 (rev c1)
00:00.2 RAM memory: nVidia Corporation nForce2 Memory Controller 4 (rev c1)
00:00.3 RAM memory: nVidia Corporation nForce2 Memory Controller 3 (rev c1)
00:00.4 RAM memory: nVidia Corporation nForce2 Memory Controller 2 (rev c1)
00:00.5 RAM memory: nVidia Corporation nForce2 Memory Controller 5 (rev c1)
00:01.0 ISA bridge: nVidia Corporation nForce2 ISA Bridge (rev a4)
00:01.1 SMBus: nVidia Corporation nForce2 SMBus (MCP) (rev a2)
00:02.0 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4)
00:02.1 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4)
00:02.2 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4)
00:04.0 Ethernet controller: nVidia Corporation nForce2 Ethernet Controller (rev a1)
00:08.0 PCI bridge: nVidia Corporation nForce2 External PCI Bridge (rev a3)
00:09.0 IDE interface: nVidia Corporation nForce2 IDE (rev a2)
00:0d.0 FireWire (IEEE 1394): nVidia Corporation nForce2 FireWire (IEEE 1394) Controller (rev a3)
00:1e.0 PCI bridge: nVidia Corporation nForce2 AGP (rev c1)
01:08.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 62)
01:08.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 62)
01:08.2 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 65)
01:09.0 Multimedia audio controller: Creative Labs SB Audigy (rev 04)
01:09.1 Input device controller: Creative Labs SB Audigy Game Port (rev 04)
01:09.2 FireWire (IEEE 1394): Creative Labs SB Audigy FireWire Port (rev 04)
02:00.0 VGA compatible controller: nVidia Corporation NV38 [GeForce FX 5950 Ultra] (rev a1)
Module                  Size  Used by
af_packet              25728  2 
binfmt_misc            16904  1 
rfcomm                 44432  0 
sco                    18308  2 
bridge                 56980  0 
stp                    10628  1 bridge
bnep                   20480  2 
l2cap                  30464  6 rfcomm,bnep
bluetooth              61924  6 rfcomm,sco,bnep,l2cap
ipv6                  263972  12 
vboxdrv                71576  0 
ppdev                  15620  0 
cpufreq_userspace      11396  0 
cpufreq_conservative    14600  0 
cpufreq_ondemand       14988  0 
cpufreq_stats          13188  0 
cpufreq_powersave       9856  0 
freq_table             12672  2 cpufreq_ondemand,cpufreq_stats
pci_slot               12680  0 
video                  25232  0 
output                 11008  1 video
wmi                    14504  0 
sbs                    19464  0 
sbshc                  13440  1 sbs
container              11520  0 
battery                18436  0 
iptable_filter         10752  0 
ip_tables              19600  1 iptable_filter
x_tables               22916  1 ip_tables
ac                     12292  0 
sbp2                   29324  0 
lp                     17156  0 
joydev                 18368  0 
snd_emu10k1_synth      14464  0 
snd_emux_synth         41344  1 snd_emu10k1_synth
snd_seq_virmidi        13568  1 snd_emux_synth
snd_seq_midi_emul      14592  1 snd_emux_synth
snd_emu10k1           146208  5 snd_emu10k1_synth
snd_ac97_codec        111652  1 snd_emu10k1
ac97_bus                9856  1 snd_ac97_codec
snd_pcm_oss            46848  0 
snd_mixer_oss          22784  1 snd_pcm_oss
snd_pcm                83204  5 snd_emu10k1,snd_ac97_codec,snd_pcm_oss
snd_page_alloc         16136  2 snd_emu10k1,snd_pcm
snd_util_mem           12416  2 snd_emux_synth,snd_emu10k1
snd_hwdep              15236  2 snd_emux_synth,snd_emu10k1
snd_seq_dummy          10884  0 
snd_seq_oss            38528  0 
snd_seq_midi           14336  0 
snd_rawmidi            29824  3 snd_seq_virmidi,snd_emu10k1,snd_seq_midi
snd_seq_midi_event     15232  3 snd_seq_virmidi,snd_seq_oss,snd_seq_midi
nvidia               7103300  24 
snd_seq                57776  9 snd_emux_synth,snd_seq_virmidi,snd_seq_midi_emul,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29960  3 snd_emu10k1,snd_pcm,snd_seq
snd_seq_device         15116  8 snd_emu10k1_synth,snd_emux_synth,snd_emu10k1,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    63268  19 snd_emux_synth,snd_seq_virmidi,snd_emu10k1,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
emu10k1_gp             10880  0 
soundcore              15328  1 snd
gameport               19468  2 emu10k1_gp
pcspkr                 10624  0 
shpchp                 38036  0 
pci_hotplug            34976  1 shpchp
evdev                  17696  9 
aiptek                 24320  0 
parport_pc             39204  1 
parport                42604  3 ppdev,lp,parport_pc
button                 14224  0 
i2c_nforce2            14468  0 
i2c_core               31892  2 nvidia,i2c_nforce2
nvidia_agp             14492  1 
agpgart                42184  2 nvidia,nvidia_agp
ext3                  133256  3 
jbd                    55828  1 ext3
mbcache                16004  1 ext3
usbhid                 35840  0 
hid                    50560  1 usbhid
usb_storage            82752  0 
libusual               30356  1 usb_storage
sr_mod                 22212  0 
cdrom                  43168  1 sr_mod
sd_mod                 42392  6 
crc_t10dif              9984  1 sd_mod
sg                     39732  0 
pata_acpi              12160  0 
pata_amd               18692  4 
ata_generic            12932  0 
ohci1394               37936  0 
libata                178208  3 pata_acpi,pata_amd,ata_generic
uhci_hcd               30736  0 
ieee1394               96324  2 sbp2,ohci1394
ohci_hcd               32016  0 
ehci_hcd               43788  0 
scsi_mod              155212  6 sbp2,usb_storage,sr_mod,sd_mod,sg,libata
dock                   16656  1 libata
forcedeth              61328  0 
usbcore               149360  8 aiptek,usbhid,usb_storage,libusual,uhci_hcd,ohci_hcd,ehci_hcd
thermal                23708  0 
processor              42156  1 thermal
fan                    12548  0 
fbcon                  47648  0 
tileblit               10880  1 fbcon
font                   16512  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
fuse                   60828  3 

 lspci | grep -i audio

01:09.0 Multimedia audio controller: Creative Labs SB Audigy (rev 04)


If anyone can point me in the right direction I'd appreciate it. I can't believe it's so difficult just to get sound through a set of headphones.

---

### Post by Le-Dart on 2009-03-06
Ah well, looks like the response/help I've had with this is the same as a lot of other people with similar problems have received. Zero.

Looks like Ubuntu doesn't "just work" after all. A little thing like headphones not working shouldn't even be an issue.

It's the little things that get people frustrated and make them give up. The sooner developers realise this the better chance Linux in general has of being taken seriously.

If I said to a Windows user, "Try Ubuntu, it's great. But be prepared for not having any sound and headphones probably won't work. Wireless is a bit hit and miss as well. However, you've got Compiz. Just spin that 3D cube and play around with all the other eye candy. It'll help take your mind off the real problems." Even a Vista user would laugh and rightly so! Oh yeh, I forgot, all those things are someone else's fault aren't they? That dear friends is a cop out excuse! 

Bye bye Ubuntu.

---

### Post by pcjunkie on 2009-03-06
Strange I am using 8.10 (fresh install) and the Audigy system has stoped working (It worked fine in 7.10) 

I have headphones but no speakers and no line in so I can't hear both computers at all through the speakers and only the Ubuntu master in the headphones, no line in.....

I might go back to 7.10 as 8.10 is thoroughly bugged.

> Audigy_Analog_Digital_Output_Jack": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/toggle_display_names/SigmaTel_STAC9750,51-External_Amplifier": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/display_toggles/SigmaTel_STAC9750,51-External_Amplifier": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/toggle_display_names/SigmaTel_STAC9750,51-HD_channel_Capture": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/display_toggles/SigmaTel_STAC9750,51-HD_channel_Capture": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/toggle_display_names/SigmaTel_STAC9750,51-HD_source_Capture": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/display_toggles/SigmaTel_STAC9750,51-HD_source_Capture": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/display_mixers/SigmaTel_STAC9750,51": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/display_names/SigmaTel_STAC9750,51": `,' is an invalid character in key/directory names

---

### Post by kirenpillay on 2009-04-22
I'm have the opposite issue. I have the Audigy ZS, but I get sound from the front only and not from the rear output for my speakers.

---

### Post by escozul on 2009-11-19
I have a similar issue with 9.10.

I have SB Audigy 2 Platinum EX and I cannot get sound to work from the rear (where my speakers are connected. I only get the front panel to work. No volume knob or anything. I guess that out of the box, ubuntu only supports one analog output. Is there a way to add a more complete set of drivers?

---

### Post by rongw on 2010-01-26
Has anyone got any new info on this?  I just ran into the same situation - Audigy 2 Platinum, Ubuntu Studio 9.10 - sound from headphone jack but not from speaker jack.

---

### Post by notbitmonk on 2010-07-03
Try alsamixer from the terminal. If any of the PCM, front, center, surround, side have an M at the bottom of the column, it means that is muted.  Select it (using the arrow keys) and click the M.  It should unmute.  If the column is empty, click the up arrow to increase the volume.

---

