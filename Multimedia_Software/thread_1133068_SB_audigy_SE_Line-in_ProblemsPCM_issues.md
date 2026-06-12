---
title: "SB audigy SE Line-in Problems/PCM issues"
date: 2009-04-22
forum: Multimedia Software
---

### Post by tywashere on 2009-04-22
Okay, Heres my problem, the line-in on my sb audigy SW is horrible in ubuntu.. aka cracking/popping and such. Now, in windows it's just fine.
High pitched sounds are iffy too. So It was sugested to adjust my "PCM" But. It isnt an option in 'alsamixer' Any help would be greatly apreciated. As this is one of the only things stopping me from removing windows :confused:

---

### Post by tywashere on 2009-04-22
Bump D:

---

### Post by tywashere on 2009-04-22
Any help really would be appreciated...

---

### Post by tunin on 2009-04-22
If yours is the same as mine, open your volume control (alsa mixer) and click on edit->preferences.  That should bring up a window that allows you to select which sliders are present on the main control window.  Hopefully pcm is listed but not checked.  Hope that gets you going.

---

### Post by tywashere on 2009-04-22
unfortunately Ive tried that, It isn't there. And it isn't under 'alsamixer' -c 1 when I enter it in terminal =(

---

### Post by tywashere on 2009-04-23
bump... again.  :\

---

### Post by tywashere on 2009-04-23
Anyone?... at all? I really need my line-in to work...

---

### Post by tunin on 2009-04-23
Which version of ubuntu are you using?  I'm pretty much a newbie at this, so maybe someone else will step in.  They would probably want to know.

---

### Post by tywashere on 2009-04-25
ubuntu 9.04, but it happened in 8.10 if I recall. But not in XP :\

---

### Post by wbee on 2009-04-25
Hello,

I've seen your thread now twice and was hesitant to answer before,hoping someone who was sure would answer.

**That said,if it turns out I'm wrong,remember where you were,what the settings were,so you can get back.

I also have the Soundblaster Audigy SE card. Mine(if there is a variation) has one physical jack for both the mic/line in.

The impedances differ.<p>(Remembering how you had it set up),double click the speaker icon in the system tray,and then preferences. Check and un check microphone and line in,in all combinations,to see if the distortion clears up.

I had an issue getting sound from the output of a TV tuner card to the line in on the card. With the microphone setting,it was simply awful. With the line in,it was acceptable.

If that does not fix it,someone else should mosey along who knows more about this than I do.

-------------

W

---

### Post by tywashere on 2009-04-25
Didnt work, Dunno if this is relivent. but In alsamixer it says something about DB gain...

---

### Post by tywashere on 2009-04-26
buuuuuuump

---

### Post by tywashere on 2009-04-26
I really hate bumping threads, So hey. Heres some useful information.

Module                  Size  Used by
cdc_acm                23712  0 
binfmt_misc            16776  1 
bridge                 56340  0 
stp                    10500  1 bridge
bnep                   20224  2 
video                  25360  0 
output                 11008  1 video
input_polldev          11912  0 
lp                     17156  0 
tuner_simple           22544  1 
tuner_types            22400  1 tuner_simple
tda9887                18564  1 
snd_ca0106             39968  3 
tda8290                20740  0 
snd_hda_intel         435636  2 
snd_ac97_codec        112292  1 snd_ca0106
snd_pcm_oss            46336  0 
snd_mixer_oss          22656  1 snd_pcm_oss
wm8775                 13740  0 
snd_pcm                82948  5 snd_ca0106,snd_hda_intel,snd_ac97_codec,snd_pcm_oss
cx25840                35632  0 
tuner                  32836  0 
snd_seq_dummy          10756  0 
snd_seq_oss            37760  0 
snd_seq_midi           14336  0 
snd_rawmidi            29696  2 snd_ca0106,snd_seq_midi
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29704  2 snd_pcm,snd_seq
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
ivtv                  150340  0 
compat_ioctl32          9344  1 ivtv
i2c_algo_bit           14084  1 ivtv
cx2341x                20996  1 ivtv
v4l2_common            20992  5 wm8775,cx25840,tuner,ivtv,cx2341x
videodev               41600  2 tuner,ivtv
snd                    62628  20 snd_ca0106,snd_hda_intel,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
lirc_mceusb2           20100  0 
fglrx                2082308  33 
v4l1_compat            21764  1 videodev
soundcore              15200  1 snd
intel_agp              34108  0 
ac97_bus                9856  1 snd_ac97_codec
ppdev                  15620  0 
snd_page_alloc         16904  3 snd_ca0106,snd_hda_intel,snd_pcm
tveeprom               20100  1 ivtv
iTCO_wdt               19108  0 
iTCO_vendor_support    11652  1 iTCO_wdt
pcspkr                 10496  0 
psmouse                61972  0 
agpgart                42696  2 fglrx,intel_agp
lirc_dev               19892  1 lirc_mceusb2
serio_raw              13316  0 
parport_pc             40100  1 
parport                42220  3 lp,ppdev,parport_pc
usbhid                 42336  0 
r8169                  40836  0 
mii                    13312  1 r8169
vesafb                 13828  1 
fbcon                  46112  72 
tileblit               10752  1 fbcon
font                   16384  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit

---

### Post by tywashere on 2009-04-26
Needs moar halp

---

### Post by tywashere on 2009-04-27
Bump

---

### Post by tywashere on 2009-04-27
bump

---

### Post by tywashere on 2009-04-28
bump

---

### Post by tywashere on 2009-04-29
Bump

---

### Post by tywashere on 2009-04-29
help, please? D:

---

### Post by tywashere on 2009-05-01
Thanks for the help :D

---

### Post by tywashere on 2009-05-01
Seriously, you guys ROCK

---

### Post by Coded1 on 2009-05-12
I feel sorry for you tywashere especially since I'm having the same problem as you are.  For me audio was good on 8.04 but Intrepid started giving me this snap,crackle,pop the moment the audio was initialized on boot up and it's killing me, slowly.  I have an audigy2 OEM that I had connected via coax to my Sony receiver and it worked fine for a long time till I made the plunge to Intrepid.  It starts off pretty bad and sometimes tapers off for a while but it always comes back.  I would describe it as clipping (when the frequency goes higher then the card / output can handle). Since then I have tried listening to audio via headphones and I get the same thing so hopefully this will bring some interest back to this issue cause it's bad enough I'm in fear of popping my speakers or my ear drums :(

Here's the data!!!

#lspci 
boss@boss:~$ lspci
00:00.0 Host bridge: Intel Corporation 82850 850 (Tehama) Chipset Host Bridge (MCH) (rev 04)
00:01.0 PCI bridge: Intel Corporation 82850 850 (Tehama) Chipset AGP Bridge (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 04)
00:1f.0 ISA bridge: Intel Corporation 82801BA ISA Bridge (LPC) (rev 04)
00:1f.1 IDE interface: Intel Corporation 82801BA IDE U100 Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 82801BA/BAM SMBus Controller (rev 04)
01:00.0 VGA compatible controller: nVidia Corporation NV44A [GeForce 6200] (rev a1)
02:01.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 50)
02:01.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 50)
02:01.2 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 51)
02:02.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 50)
02:02.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 50)
02:02.2 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 51)
02:07.0 USB Controller: NEC Corporation USB (rev 43)
02:07.1 USB Controller: NEC Corporation USB (rev 43)
02:07.2 USB Controller: NEC Corporation USB 2.0 (rev 04)
02:08.0 Ethernet controller: Atheros Communications Inc. Atheros AR5001X+ Wireless Network Adapter (rev 01)
02:09.0 Multimedia audio controller: Creative Labs SB Audigy (rev 04)
02:09.2 FireWire (IEEE 1394): Creative Labs SB Audigy FireWire Port (rev 04)
02:0c.0 Ethernet controller: Intel Corporation 82557/8/9/0/1 Ethernet Pro 100 (rev 10)

boss@boss:~$ lsmod
Module                  Size  Used by
isofs                  39844  1 
nls_iso8859_1          12032  2 
nls_cp437              13696  2 
udf                    87716  0 
crc_itu_t              10112  1 udf
vfat                   18816  2 
fat                    58272  1 vfat
binfmt_misc            16776  1 
bridge                 56340  0 
stp                    10500  1 bridge
bnep                   20224  2 
vboxnetflt             91016  0 
vboxdrv               117544  1 vboxnetflt
video                  25360  0 
output                 11008  1 video
input_polldev          11912  0 
sbp2                   30476  0 
lp                     17156  0 
snd_emu10k1_synth      14336  0 
snd_emux_synth         40832  1 snd_emu10k1_synth
snd_seq_virmidi        13440  1 snd_emux_synth
snd_seq_midi_emul      14592  1 snd_emux_synth
snd_emu10k1           144288  3 snd_emu10k1_synth
snd_ac97_codec        112292  1 snd_emu10k1
ac97_bus                9856  1 snd_ac97_codec
snd_pcm_oss            46336  0 
snd_mixer_oss          22656  1 snd_pcm_oss
snd_pcm                82948  4 snd_emu10k1,snd_ac97_codec,snd_pcm_oss
snd_page_alloc         16904  2 snd_emu10k1,snd_pcm
snd_util_mem           12288  2 snd_emux_synth,snd_emu10k1
snd_hwdep              15108  2 snd_emux_synth,snd_emu10k1
snd_seq_dummy          10756  0 
snd_seq_oss            37760  0 
snd_seq_midi           14336  0 
snd_rawmidi            29696  3 snd_seq_virmidi,snd_emu10k1,snd_seq_midi
snd_seq_midi_event     15104  3 snd_seq_virmidi,snd_seq_oss,snd_seq_midi
snd_seq                56880  9 snd_emux_synth,snd_seq_virmidi,snd_seq_midi_emul,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29704  3 snd_emu10k1,snd_pcm,snd_seq
snd_seq_device         14988  8 snd_emu10k1_synth,snd_emux_synth,snd_emu10k1,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
wlan_scan_sta          20480  1 
iTCO_wdt               19108  0 
iTCO_vendor_support    11652  1 iTCO_wdt
ath_rate_sample        19840  1 
ppdev                  15620  0 
dcdbas                 15264  0 
psmouse                61972  0 
snd                    62628  16 snd_emux_synth,snd_seq_virmidi,snd_emu10k1,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
nvidia               7233756  36 
ath_pci                99224  0 
intel_agp              34108  1 
pcspkr                 10496  0 
serio_raw              13316  0 
soundcore              15200  1 snd
ndiswrapper           193436  0 
wlan                  210288  4 wlan_scan_sta,ath_rate_sample,ath_pci
ath_hal               198864  3 ath_rate_sample,ath_pci
agpgart                42696  2 nvidia,intel_agp
intel_rng              12672  0 
parport_pc             40100  1 
parport                42220  3 lp,ppdev,parport_pc
shpchp                 40212  0 
ohci1394               38576  0 
e100                   41740  0 
mii                    13312  1 e100
ieee1394               94660  2 sbp2,ohci1394
floppy                 64324  0 
usb_storage            82880  2 
fbcon                  46112  0 
tileblit               10752  1 fbcon
font                   16384  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit

boss@boss:~$ sudo dpkg -l *pulse*
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Cfg-files/Unpacked/Failed-cfg/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name                 Version              Description
+++-====================-====================-========================================================
un  flashplugin-nonfree- <none>               (no description available)
ii  gstreamer0.10-pulsea 0.10.14-1            GStreamer plugin for PulseAudio
un  libao-pulse          <none>               (no description available)
ii  libpulse-browse0     1:0.9.14-0ubuntu20.1 PulseAudio client libraries (zeroconf support)
ii  libpulse0            1:0.9.14-0ubuntu20.1 PulseAudio client libraries
rc  libpulsecore5        0.9.10-2ubuntu9      PulseAudio sound server core
un  libpulsecore8        <none>               (no description available)
ii  libpulsecore9        1:0.9.14-0ubuntu20.1 PulseAudio sound server core
un  libsdl1.2debian-puls <none>               (no description available)
ii  pulseaudio           1:0.9.14-0ubuntu20.1 PulseAudio sound server
ii  pulseaudio-esound-co 1:0.9.14-0ubuntu20.1 PulseAudio ESD compatibility layer
ii  pulseaudio-module-gc 1:0.9.14-0ubuntu20.1 GConf module for PulseAudio sound server
ii  pulseaudio-module-ha 1:0.9.14-0ubuntu20.1 HAL device detection module for PulseAudio sound server
un  pulseaudio-module-ja <none>               (no description available)
un  pulseaudio-module-li <none>               (no description available)
ii  pulseaudio-module-x1 1:0.9.14-0ubuntu20.1 X11 module for PulseAudio sound server
un  pulseaudio-module-ze <none>               (no description available)
ii  pulseaudio-utils     1:0.9.14-0ubuntu20.1 Command line tools for the PulseAudio sound server


--- This looks like the issue here now that I look at it, I will fix this and get back to you.  I get the following repeated many times (>50) through my log.  Maybe it will help for you to check this out as well.


# sudo cat /var/log/messages | grep pulse 
May 12 16:36:08 boss pulseaudio[5900]: main.c: For enabling real-time/high-priority scheduling please acquire the appropriate PolicyKit privileges, or become a member of 'pulse-rt', or increase the RLIMIT_NICE/RLIMIT_RTPRIO resource limits for this user.
May 12 16:36:08 boss pulseaudio[5903]: alsa-util.c: Cannot find fallback mixer control "PCM" or mixer control is no combination of switch/volume.
May 12 16:36:08 boss pulseaudio[5903]: alsa-util.c: Cannot find fallback mixer control "Mic" or mixer control is no combination of switch/volume.
May 12 16:39:46 boss pulseaudio[6214]: main.c: Called SUID root and real-time and/or high-priority scheduling was requested in the configuration. However, we lack the necessary privileges:
May 12 16:39:46 boss pulseaudio[6214]: main.c: We are not in group 'pulse-rt', PolicyKit refuse to grant us the requested privileges and we have no increase RLIMIT_NICE/RLIMIT_RTPRIO resource limits.

-- Also 'sudo cat /var/log/messages | grep alsa' gives over 200 lines of this ...

May 12 16:13:35 boss pulseaudio[4389]: alsa-util.c: Cannot find fallback mixer control "PCM" or mixer control is no combination of switch/volume.
May 12 16:13:35 boss pulseaudio[4389]: alsa-util.c: Cannot find fallback mixer control "Mic" or mixer control is no combination of switch/volume.



Will keep you posted here of my results!

---

