---
title: "No audio analog, coax, or HDMI"
date: 2008-12-20
forum: Mythbuntu
---

### Post by korgman on 2008-12-20
New Mythbuntu build on a Asus M3N78 MOBO.  I cannot get any audio out of this box. Not analog, HDMI, or COAX dig. There was some sort of audio coming out of the analog port earlier, because if I ran that output into my Denon receiver RCA L/R in and max out the volume I could here the broadcast slightly.  After screwing around, I've lost that now too.

No signal at all out of the HDMI or Coax. The Denon doesn't show any bitstream coming in.


matt@mythbuntu:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC888 Analog [ALC888 Analog]
Subdevices: 0/1
Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC888 Digital [ALC888 Digital]
Subdevices: 1/1
Subdevice #0: subdevice #0

matt@mythbuntu:~$ lspci -v
...blah blah

00:07.0 Audio device: nVidia Corporation Realtek ALC1200 8-Channel High Definition Audio Codec (rev a1)
Subsystem: ASUSTeK Computer Inc. Device 82fe
Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 20
Memory at fe020000 (32-bit, non-prefetchable) [size=16K]
Capabilities: <access denied>
Kernel driver in use: HDA Intel
Kernel modules: snd-hda-intel

...blah

---

### Post by olddave on 2008-12-20
korgman.
Hi mate i am not an expert if you have a DVI out put on the computer then get a DVI to HDMI cable that should work for the picture. For the sound you can use your head phone socket to the rca input on you tv. 
Olddave

---

### Post by korgman on 2008-12-20
I don't have DVI.  Just VGA and HDMI and the picture is fine over the HDMI.  I also don't get any audio over any of the analog (speaker, headphones...) outputs either. I've tried it all. There is nothing sound wise coming out of this box, analog or digital bitstream.

---

### Post by dsbw on 2008-12-20
Have you fooled with alsamixer?

---

### Post by korgman on 2008-12-20
So I now have some success.  VLC can play CDs, and I can faintly hear the music with headphones plugged into the fron audio panel.  Still no DVD audio, or HDTV audio.  Alsamixer shows:

Card: HDA NVidia                                                             &#9474;
&#9474; Chip: Realtek ALC888                                                         &#9474;
&#9474; View: [Playback] Capture  All                                                &#9474;
&#9474; Item: Master [dB gain=-7.50]    

PCM and front levels are redlined at around 90.

---

### Post by dsbw on 2008-12-21
Is it just in mythtv that you can't hear?

---

### Post by korgman on 2008-12-21
Well, like I said, I can faintly hear a sound out of the front analog panel through headphones and the rear output.  The front audio is connected to the MOBO with an Azalia ribbon cable, and the rear audio is on board the mobo.  If I'm playing a CD or DVD through VLC from the Applications menu, I can hear the slightest bit of sound through the analog outs (both front and read).  No audio at all if I'm watching OTA TV or playing media from the Mythbuntu front end.  And never a digital bitstream.

---

### Post by dsbw on 2008-12-21
Make sure you've set the audio right in MythTV. That might at least get you to the faint sound in there, too.

The problems I've had in the analog area revolved around not having the plug in the right place. 

Digital I'm still working on.

---

### Post by dsbw on 2008-12-21
Make sure you've set the audio right in MythTV. That might at least get you to the faint sound in there, too.

The problems I've had in the analog area revolved around not having the plug in the right place. 

Digital I'm still working on.

---

