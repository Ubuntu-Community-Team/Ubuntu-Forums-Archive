---
title: "AC3 passthough problems on Shuttle SN95G5 v1.2"
date: 2006-06-06
forum: Multimedia &amp; Video
---

### Post by zoeloe on 2006-06-06
Hi,

Anyone running this distro on a Shuttle SN95G5 v1.2 ? 
aplay -l says:
**** List of PLAYBACK Hardware Devices ****
card 0: CK8S [NVidia CK8S], device 0: Intel ICH [NVidia CK8S]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CK8S [NVidia CK8S], device 2: Intel ICH - IEC958 [NVidia CK8S - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


Am having trouble getting the AC3 passthrough working with the Kaffeine mediaplayer (using xine) on the optical spdif on this machine 
Although e.g. streaming mp3 audio works with the Amarok media player (a 48 kHz PCM stream goes to my external Sony amp), somehow when using Kaffeine (with the passthrough option on for xine) for DVD’s with Dolby Digital 5.1 streams or DTS stream, the external amp shows a “decoder error” (which means that the amp is receiving something, but the format is wrong)
So my guess is that something is modifying the AC3 stream.. but what !?

I searched high and low and can’t seem to find a workable solution. 
(tried several alsa sound configurations etc,.. to no avail)

Anyone having a working alsa config for this machine or other suggestions (mixer settings, iec958 registers,...?)

TIA for any pointers.

---

### Post by zoeloe on 2006-06-09
Well, folks,...  further digging didn't get me any closer to a solution.
From what I see is that something has to put the spdif chip/output (a.k.a. "iec958") is the right mode to stream a raw DVD ac3 stream to ones external amp.

It seems that the wrong values for this hardware's iec958 registers are set 
in xine.

Did even some reverse engineering by booting Windoze, running PowerDVD with SPDIF passthrough (which works BTW) rebooting without powering down in kubuntu and reading the iec958 registers with "iecset -x",... (result: first AES0=0x07 the rest is 0x00) 
(It has something to do with "Professional/Consumer" modus and  "Audio/Non-Audio" modus)
well,... these params are not the same as the default xine iec958 parameters for the alsa passthrough device.

For as far as I remember, setting these iec958 values in xine doesn't get the job done either in kubuntu.

Am at a loss here...](*,) 

TIA for any pointers.

---

