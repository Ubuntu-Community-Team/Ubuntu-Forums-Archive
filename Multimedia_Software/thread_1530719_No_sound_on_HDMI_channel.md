---
title: "No sound on HDMI channel"
date: 2010-07-14
forum: Multimedia Software
---

### Post by defaria on 2010-07-14
I was hoping that upgrading to 10.04 would fix my problems with sound and HDMI but alas it doesn't. I have an HP dv7 that I wish connect via an HDMI cable to my HDTV and play things like Hulu, Boxee, etc. with the sound coming out of my home theater system. I know that the hardware is capable of doing this because I have Windows 7 installed in a dual boot and it has no problems with pumping sound down the HDMI channel. 

I've upgraded to Alsa 1.0.23 freshly compiled. With 1.0.23 I see HDMI settings in Pulse Audio Volume Control. However if I start say VLC and play a video, check pavucontrol and make sure the Playback is set to the HDMI channel. I can hook up the HDMI cable and I can see the video playing - but no audio.

I've been in and out of all kinds of things like alsamixer, gnome-alsamixer, sound preferences, etc. and I've toggled things on and off in an attempt to get HDMI sound working but nothing works. 

In alsamixer if I hit f6 I see my 0 card as HDA Intel and my 1 card as NDA NVidia. If I select NVidia I see only S/PDIF, S/PDIF 1, S/PDIF 2, S/PDIF 3. I can only mute or unmute these. I've tried both - nothing works.

Let me know what sort of output/info you need and I'll post it. Here's some info I've seen others post:

```
Mars:uname -a
Linux mars 2.6.32-23-generic #37-Ubuntu SMP Fri Jun 11 08:03:28 UTC 2010 x86_64 GNU/Linux
Mars:aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 7: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 8: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 9: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
Mars:cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.23.
Compiled on Jul 13 2010 for kernel 2.6.32-23-generic (SMP).
Mars:head -n 1 /proc/asound/card*/codec#*
==> /proc/asound/card0/codec#0 <==
Codec: IDT 92HD75B3X5

==> /proc/asound/card1/codec#0 <==
Codec: Nvidia GT220 HDMI

==> /proc/asound/card1/codec#1 <==
Codec: Nvidia GT220 HDMI

==> /proc/asound/card1/codec#2 <==
Codec: Nvidia GT220 HDMI

==> /proc/asound/card1/codec#3 <==
Codec: Nvidia GT220 HDMI
Mars:cat /etc/modprobe.d/alsa-base.conf
# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-ioctl32 ; /sbin/modprobe --quiet --use-blacklist snd-seq ; }
#
# Workaround at bug #499695 (reverted in Ubuntu see LP #319505)
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; /sbin/modprobe --quiet --use-blacklist snd-seq-oss ; : ; }
#
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist saa7134-alsa ; : ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2

# Added by Andrew@DeFaria.com
options snd-hda-intel model=hp-dv5 enable_msi=1

```

---

### Post by lidex on 2010-07-14
Have you seen this:
[http://wiki.xbmc.org/index.php?title=HOW-TO_set_up_HDMI_audio_on_nVidia_GeForce_G210,_GT220,_or_GT240]("http://wiki.xbmc.org/index.php?title=HOW-TO_set_up_HDMI_audio_on_nVidia_GeForce_G210,_GT220,_or_GT240")
More:
[http://linux.aldeby.org/howto-ubuntu-linux-on-hp-pavilion-dv2000-dv6000-dv9000-series-laptops.html/6#vga]("http://linux.aldeby.org/howto-ubuntu-linux-on-hp-pavilion-dv2000-dv6000-dv9000-series-laptops.html/6#vga")

---

### Post by defaria on 2010-07-14
> **lidex said:**
> Have you seen this:
[http://wiki.xbmc.org/index.php?title=HOW-TO_set_up_HDMI_audio_on_nVidia_GeForce_G210,_GT220,_or_GT240]("http://wiki.xbmc.org/index.php?title=HOW-TO_set_up_HDMI_audio_on_nVidia_GeForce_G210,_GT220,_or_GT240")

As usual this page talks about a lot of similar things, most of which I have done. However it's descriptions don't exactly match my stuff leaving me scratching my head. The closest hardware listed is GT220 HP Pavilion Elite HPE-141F - yet my machine is a HP dv7. 

Wow! That worked. Well sorta. I managed to actually get sound out of my HDMI channel. I don't know if it was the change to /etc/modprobe.d/sound.conf or the change to /etc/pulse/default.pa (suspect the later but it might be the combination).

I say sorta because while output on HDMI now works for things like VLC, Movie Player and Banshee, it doesn't work for Hulu Desktop which is a real shame as that would be my replacement for Playon (and the need for the Windows dual boot which is my ultimate goal).

Also Boxee's not starting stating a problem with a library but there's a new version of Boxee out anyway. I'll need to reinstall that and see if that works.

Could it be that Hulu Desktop is using Flash and thus it's a flash problem? What Flash runs on 10.04? 10.1 I hope? Also, WRT Flash, I'm 64 bit and last I heard there was no Flash 10.1 for 64 bit.

> 
More:
[http://linux.aldeby.org/howto-ubuntu-linux-on-hp-pavilion-dv2000-dv6000-dv9000-series-laptops.html/6#vga]("http://linux.aldeby.org/howto-ubuntu-linux-on-hp-pavilion-dv2000-dv6000-dv9000-series-laptops.html/6#vga")

This didn't really tell me anything I didn't already know. It seems to only address setting NVidia resolution, etc. The nvidia-settings app has changed somewhat and quite frankly is acting differently and oddy compared to how it used to work. For example there's an Fn button combination to change output to the "projector" meaning the HMDI output. This no longer does anything. Instead I have to run nvidia-settings. I then have to detect displays to discover my Mitsubishi screen. 

If I turn on the Mitsubishi display then the resolution of my laptop display gets messed up and I can no longer see the bottom bar with the minimized apps. I also can't get my Mitsubishi display resolution set right - the edges are also off and things get cut off. Ugh.

Well at least I'm starting to get somewhere. Why must this be so hard and so flaky and temperamental?

---

### Post by lidex on 2010-07-14
I'm not a HULU user but did notice if you google hdmi + audio + hulu there seem to be some inherent issues with the platform. Perhaps you can get a jump on it there. I don't think it's related to this:
[http://ubuntuforums.org/showthread.php?t=1455816]("http://ubuntuforums.org/showthread.php?t=1455816")
but I've been wrong en masse, so have a look ;)

---

### Post by defaria on 2010-07-15
Once again your advice seems to have paid off! Thanks. Am I supposed to award you coffee beans or something? I even got Hulu Desktop and Boxee working now!

Now it's on to figuring out how to get my little IR remote working under Ubuntu. The setup seems to work but sloppily. By that I mean that for one whenever I unplug the laptop from the HDMI cable it seems to loose the configuration of my Mitsubishi HDTV. When I replug it in I need to go into nvidia-settings and detect display again. Kinda a pain.

Plus I need to run pavucontrol and change the output devices often as they don't appear to stick either (haven't played with this a lot yet to properly characterize it).

But by far, to get that "sit back in the easy chair" experience going I need to get this little IR remote that came with the laptop working so I can control things like Boxee and Hulu Desktop without having to get up and walk over to the laptop ever 2-4 minute clip. I know the IR remote works - again it works on my dual booted Windows 7.

OK, well that and maybe work on TV Time to get it working under Ubuntu with my TV tuner card.

If I can these things working well enough then I can remove that Windows 7 install as I've already created a VMWare image of that should I need to use Windows 7 and finally rid myself totally of Windows (at least physically running Windows)!

---

### Post by lnthai2002 on 2010-10-15
hey defaria,
can u post how u make boxee output sound though your hdmi ? I have GT240 on kernel 2.6.31 (karmic) with alsa 1.0.23, nvidia 256 but i cant make the sound come out from hdmi in boxee although my xbmc does produce sound correctly. 
Thanks in advance

---

