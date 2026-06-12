---
title: "Different frequency for SPDIF and HDMI in ALSA"
date: 2015-04-22
forum: Multimedia Software
---

### Post by klasw on 2015-04-22
Hey!


I wonder if it is possible to put out different frequency for SPDIF and HDMI in the alsa settings, and how to change that?


I changed the sample rate to 96000 Hz in pulsadio, but it seems to break through to hdmi too, and my TV can not receive the signal. My TV (HDMI) wants 48000 Hz.


I have an HDCP with Ubuntu at the bottom and Kodi (XBMC) and has previously managed to get pulseaudio and alsa in parallel configuration. That means I can choose in Kodi between the following alternative:


- pulsadio (defallt)


- HDMI out (ALSA)


- SPDIF (ALSA)


- HDMI and SPDIF (ALSA)


However, I do not remember how I managed it, which file I did the configuration for alsa in. Witch files is involve in alsa configuration? 


The reason I made this setup is that I want the best sound for music to separate DACs, stereo. For movies, I want to be able to have HDMI (to TV) and SPDIF at the same time and for late night viewing, I want only HDMI (for TV). I need pulseaudio because sometimes I use the computer as a workstation. 

Did search on goggle but can not find any good answere ore even witch file is involved for alsa and hardware configuration.
Grateful for any response on my question.

---

### Post by dino99 on 2015-04-22
here is a recent wiki, maybe it will brings you some ideas  [https://help.ubuntu.com/community/SoundTroubleshootingProcedure](https://help.ubuntu.com/community/SoundTroubleshootingProcedure)

---

### Post by klasw on 2015-04-22
No, there is nothing about  frequency for various audio devices in alsa configuration there. But if I  read all the pages of links at the end of that instruction page,  maybe so I'll find some information about it. But there is  a time aspect also, so I ask here.

---

### Post by klasw on 2015-04-22
I have figured out (by reading this: [http://unix.stackexchange.com/questions/74558/change-sampling-rate-in-alsa](http://unix.stackexchange.com/questions/74558/change-sampling-rate-in-alsa)) 
that the config file I did not remember (se main post above)  is [COLOR=#000000][FONT=Verdana].asoundrc.

I should have something like this in the file:

[/FONT][/COLOR]

pcm.iec958_24{
        type plug
        format S32_LE
        rate 96000
        type hw
        card 0
        device 1
}
pcm.!default{
    type plug
    slave.pcm "iec958_24"
}






-------------------------------------

This is the result from; aplay -L:

(after above config and restart, pcm.iec958_24 did not show up)

-------------------------------------


null
    Discard all samples (playback) or generate zero samples (capture)
pulse
    PulseAudio Sound Server
default
    Playback/recording through the PulseAudio sound server
sysdefault:CARD=Intel
    HDA Intel, VT1708S Analog
    Default Audio Device
front:CARD=Intel,DEV=0
    HDA Intel, VT1708S Analog
    Front speakers
surround40:CARD=Intel,DEV=0
    HDA Intel, VT1708S Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=Intel,DEV=0
    HDA Intel, VT1708S Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=Intel,DEV=0
    HDA Intel, VT1708S Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Intel,DEV=0
    HDA Intel, VT1708S Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=Intel,DEV=0
    HDA Intel, VT1708S Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=Intel,DEV=0
    HDA Intel, VT1708S Digital
    IEC958 (S/PDIF) Digital Audio Output
dmix:CARD=Intel,DEV=0
    HDA Intel, VT1708S Analog
    Direct sample mixing device
dmix:CARD=Intel,DEV=1
    HDA Intel, VT1708S Digital
    Direct sample mixing device
dsnoop:CARD=Intel,DEV=0
    HDA Intel, VT1708S Analog
    Direct sample snooping device
dsnoop:CARD=Intel,DEV=1
    HDA Intel, VT1708S Digital
    Direct sample snooping device
hw:CARD=Intel,DEV=0
    HDA Intel, VT1708S Analog
    Direct hardware device without any conversions
hw:CARD=Intel,DEV=1
    HDA Intel, VT1708S Digital
    Direct hardware device without any conversions
plughw:CARD=Intel,DEV=0
    HDA Intel, VT1708S Analog
    Hardware device with all software conversions
plughw:CARD=Intel,DEV=1
    HDA Intel, VT1708S Digital
    Hardware device with all software conversions
hdmi:CARD=HDMI,DEV=0
    HDA ATI HDMI, HDMI 0
    HDMI Audio Output
dmix:CARD=HDMI,DEV=3
    HDA ATI HDMI, HDMI 0
    Direct sample mixing device
dsnoop:CARD=HDMI,DEV=3
    HDA ATI HDMI, HDMI 0
    Direct sample snooping device
hw:CARD=HDMI,DEV=3
    HDA ATI HDMI, HDMI 0
    Direct hardware device without any conversions
plughw:CARD=HDMI,DEV=3
    HDA ATI HDMI, HDMI 0
    Hardware device with all software conversions


---------------------------------------------------

..and this is the result from; aplay --list-devices:

---------------------------------------------------


**** Lista över PLAYBACK hårdvaruenheter ****
kort 0: Intel [HDA Intel], enhet 0: VT1708S Analog [VT1708S Analog]
  Underordnade enheter: 1/1
  Underordnad enhet nr. 0: subdevice #0
kort 0: Intel [HDA Intel], enhet 1: VT1708S Digital [VT1708S Digital]
  Underordnade enheter: 0/1
  Underordnad enhet nr. 0: subdevice #0
kort 1: HDMI [HDA ATI HDMI], enhet 3: HDMI 0 [HDMI 0]
  Underordnade enheter: 1/1
  Underordnad enhet nr. 0: subdevice #0

-----------------------------------------------

What is wrong?






[COLOR=#000000][FONT=Verdana]
[/FONT][/COLOR]

---

### Post by klasw on 2015-04-22
Figured it out by my self.

What I did:
------------

Removed the alsa configuration in my home directory:

rm .asoundrc

Reinstalled alsa and pulseaudio:

sudo aptitude purge alsa-base  alsa-oss pulseaudio

sudo aptitude install alsa-base  alsa-oss pulseaudio

Reinstalled some other packeges (that was remed):

sudo aptitude install  kubuntu-desktop  libcanberra-pulse  paprefs  pulseaudio-module-bluetooth pulseaudio-module-gconf  pulseaudio-module-x11 pulseaudio-module-zeroconf

Changes in /etc/pulse/daemon.conf:


sudo nano /etc/pulse/daemon.conf



default-sample-format = s32le
 default-sample-rate = 96000
; alternate-sample-rate = 48000
 default-sample-channels = 2
 default-channel-map = front-left,front-right
resample-method = speex-float-5
default-fragments = 8
default-fragment-size-msec = 10 

(removed ";" infront off lines)


Changes in /etc/pulse/default.pa:


sudo nano /etc/pulse/default.pa


### Load audio drivers statically
### (it's probably better to not load these drivers manually, but instead
### use module-udev-detect -- see below -- for doing this automatically)
...


load-module module-alsa-sink device=hw:1,3 rate=48000

Changes in to pavucontrol:

Set HDMI out to 5.1 on both pulesadio default and new one (the alsa device=hw:1,3)

Checked alsa channels (in gnome alsa mixer).
 Main PCM, front channels and digital was muted, unmute them

Checked on the spdid (unmued it).

Rebooted

Done!

Hope this help some other people.

---

### Post by klasw on 2015-04-27
It was very unstable configuration, the sink in Pulseaudio for HDMI still falls out. I did this:


[COLOR=#000000][FONT=Verdana]I set pass through in pavucontroll for mpeg and dts (even if dts not function for my DAC).[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]I disabled Pulseaudio (I think) by changing in this file: /etc/pulse/client.conf[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana];autospawn = yes[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]to:[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]autospawn = no[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]And restarted my computer.[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]Now I can change everything directly in Kodi, passthrough, disable dts, oversampling optimized, best match ore static.[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]I have to change it to optimized ore best match for HDMI to my Tv every time though, but its stable know. Even change when I play music![/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]What I do not understand is what configuration that is bit perfect?[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]Optimized, 96 Hz highest sampling over spdif sounds best, at least on flac files.[/FONT][/COLOR]

---

### Post by dino99 on 2015-04-27
Great :p  only hope that upgrading will not reset your settings ;)

---

### Post by klasw on 2015-05-03
It use to ask when it upgrade, but your right dino99, the file to change should probably bee [COLOR=#333333] the [/COLOR]_[.pulse/client.conf]("file:///~/.pulse/client.conf")_[FONT=inherit][COLOR=#333333], in the home folder. Ore  more [/COLOR][/FONT][COLOR=#333333]exactly[/COLOR][FONT=inherit][COLOR=#333333], to first copy over [/COLOR][/FONT][COLOR=#000000][FONT=Verdana]/etc/pulse/client.conf[/FONT][/COLOR][COLOR=#333333][FONT=inherit] and change ownership on the file, and then change [/FONT][/COLOR][COLOR=#000000][COLOR=#000000][FONT=Verdana]to:[/FONT][/COLOR][/COLOR]

[COLOR=#000000][COLOR=#000000][FONT=Verdana]autospawn = no

(source for my conclusion: [/FONT][/COLOR][/COLOR]http://manpages.ubuntu.com/manpages/oneiric/man1/pulseaudio.1.html)

---

