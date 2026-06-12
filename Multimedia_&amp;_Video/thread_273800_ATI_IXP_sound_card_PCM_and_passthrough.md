---
title: "ATI IXP sound card PCM and passthrough"
date: 2006-10-08
forum: Multimedia &amp; Video
---

### Post by rkvj on 2006-10-08
Hello everyone,

I'm running Ubuntu 6.06(32-bit) on AMD64 processor. The motherboard has on board soundcard made by ATI. I had some trouble getting the sound routed out through the spdif header/connector, which was solved by adding the following lines in /etc/modutils/alsa as per ALSA-install:

# ALSA portion
alias char-major-116 snd
alias snd-card-0 snd-atiixp
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


I also had to change the mixer(GNOME) settings:
 -- for device ATI IXP (Alsa Mixer), set options->IEC958 to "PCM"
 -- for device Realtek-ALC655, enable Playback->Digital-1


With the above settings, I'm was and am able to listen to mp3s, watch TV and DVDs with stereo sound. I'm trying to get AC3/passthrough to work but haven't had luck in getting *both* PCM and passthrough to work together. I've tried playing around with alsa settings, particularly the "dmix" plugin but with no luck.

Here are the settings I tried:

---------------------------
%cat /etc/asound.conf
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
pcm "hw"
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

---------------------------

With the above settings only the passthrough works and my audio receiver reads "Dolby Digital" all the time after ALSA is initialized after boot-up. 

Please share your experience if you have a similar setup and have been able to get it to work. 

Here is the list of sound cards that are detected:

---------------------------
% aplay -l

**** List of PLAYBACK Hardware Devices ****
card 0: IXP [ATI IXP], device 0: ATI IXP AC97 [ATI IXP AC97]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: IXP [ATI IXP], device 1: ATI IXP IEC958 [ATI IXP IEC958 (AC97)]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


---------------------------



Thanks

--RKVJ

---

