---
title: "karmic and sound"
date: 2009-11-05
forum: Multimedia Software
---

### Post by ezacon on 2009-11-05
I have previously posted a similar question, but this is a more general question.

I have an asus mainboard with NVIDIA 8300 chipset. I have just reinstalled mi HTPC with 9.10 and most of thigs are now working.
It is connected througt HDMI to a philips LCD TV. The HDMI sound is now working, after some adjustements to the sound controls, and unmuting some channels in "alsamixer".
In another disk, i have installed WIN7 and it is playing sount througt optical port to the audio amplifier, so i know cable and port is working.

In karmic i want to play sound througt optical port (no success until now).

aplay -l shows 1 card, 3 devices:
tarjeta 0: NVidia [HDA NVidia], dispositivo 0: ALC1200 Analog [ALC1200 Analog]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0
tarjeta 0: NVidia [HDA NVidia], dispositivo 1: ALC1200 Digital [ALC1200 Digital]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0
tarjeta 0: NVidia [HDA NVidia], dispositivo 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0


Device number 3 is HDMI and i can set some programs to play using this port number. I have tryed with port 0 and 1 with no success.

In sound config, i can only chose HDMI an lots of variations of analog output.

Is it possible that ubuntu detects the card but dont detect all available ports? (i have ports 0,1 and 3 but not 2)
The module used is snd_hda_intel.

With mutiple output harware, is it possible to play a sound in HDMI port AND another sound with another aplicacion in optical port?.

Thanks

---

### Post by ezacon on 2009-11-06
Lots of things have changed with sound in 9.10.
Is there any document about how all this is assembled?
I know where to look for alsa and pulse but i am searchig a more general picture to clarfy what is happening with sound.

Thanks

---

### Post by Pipistrelle on 2009-11-06
Not an answer for you, but I'm getting a hang when I try to go into the volume control: "waiting for sound to respond" ad infinitum. No more sounds, except for screen-reader speech, thankfully for that anyway. :> I just installed Karmic three days ago.

Teresa

---

### Post by ezacon on 2009-11-07
Finaly i have configured everithing as i want:
I put here all relevant info for reference.

Mainboard: M3N78-EM
System: fresh install Ubuntu 9.10

By default, in alsamixer, chanels IEC958, IEC958 D and IEC958 1 are muted. Unmuting them and choosing the right device in sound applet enable sound in HDMI, but not in optical digital port.
I have found that for digital out to work, you need to mute "Headfone".

Now, you can play in HDMI with hw:0,3 and in digital out in hw:0,1.

To play MPD in digital out, simply enable the alsa output section with hw:0,1 in /etc/mpd.conf.

I can play at the same time different sounds in HDMI and digital output.

---

