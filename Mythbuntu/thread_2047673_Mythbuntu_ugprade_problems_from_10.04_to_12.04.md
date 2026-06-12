---
title: "Mythbuntu ugprade problems from 10.04 to 12.04"
date: 2012-08-25
forum: Mythbuntu
---

### Post by samihs72 on 2012-08-25
Hi,

I have problems after upgrade from 10.04 to 12.04 Mythbuntu.

- recordings playback are playing faster like fast forward with 2x speed without sound.
- sounds are not working anymore with my ALSA config (asound.conf file in /etc/ directory. How can I get this working again in 12.04? Do I still need my asound.conf?
I have tried to setup voice settings as they were in 10.04, dmix HDMI device 3 chosen..

- Soundgraph iMON (lsusb 15c2:0038) does not work properly anymore, I haven't investigate this more deeply yet.

Here is my aplay -l output:

sami@sami-htpc:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC1200 Analog [ALC1200 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: ALC1200 Digital [ALC1200 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
sami@sami-htpc:~$

---

### Post by PhilWig on 2012-08-26
I did this only yesterday in my upgrade from 9.04!  
I'm using mythbuntu 12.04 on a combined fe/be. Nvidia 8300 on-board graphics (asus m3n78em mobo) and HDMI to TV.  Stereo sound through TV speakers.  This is what worked for me but not all steps may be necessary.
 
In Mythbuntu control centre, graphics, use recommend nidia drivers.
Reboot (I did cold reboot ie close down, power off at wall, press start button to fully discharge any capacitors, start up again)

In alsamixer, unmute the s/pdif controls, set output controls to max.
  
In frontend there is a brilliant new section in setup > setup wizard > audio configuration (also in setup > audio).  Change audio device and test until it hisses at you.  

Sound then working fine with Mythtv.

To get sound with mythnetvision I needed to create /etc/asound.conf to match the audio settings:
> pcm.!default {
      type plug
      slave.pcm {
              type hw
              card 0
              device 3
      }
 }


Best wishes!

Phil

---

