---
title: "nVidia Corporation CK804 AC'97 Audio Controller"
date: 2008-10-28
forum: Multimedia Software
---

### Post by JobVI on 2008-10-28
I am having some problems getting my sound to work on a fresh install of Mythbuntu 8.04.1.  I have tried following the steps provided in the 'Comprehensive Sound Problem Solutions Guide v0.5e' (all the way up to the 'Getting the ALSA drivers from a *fresh* kernel')and still no luck.  I have zero sound.

I have a Asus A8N-SLI Premium and the sound card identified at install is nVidia Corporation CK804 AC'97 Audio Controller (rev a2).  I have tried using the Optical S/PDIF out and the line out and I do not have any sound.

I ran alsa-info.sh to see if the data would help ([http://pastebin.ca/1238197](http://pastebin.ca/1238197)).

I am relatively new to Linux, but I am learning fast.  Any help troubleshooting this would be appreciated.

---

### Post by mike909 on 2008-11-09
Exact same issue here (same board/hw info). I have the following which, do you see this as well? I could try to run that script that you ran, though it doesn't seem to have helped?
```
mike@mike-desktop:~$ lspci | grep audio
00:04.0 Multimedia audio controller: nVidia Corporation CK804 AC'97 Audio Controller (rev a2)
mike@mike-desktop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: CK804 [NVidia CK804], device 0: Intel ICH [NVidia CK804]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CK804 [NVidia CK804], device 2: Intel ICH - IEC958 [NVidia CK804 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```
I had this spdif out working in Vista, but noticed that before I had drivers installed the spdif out was 'dark', ie no red light coming out of port. Once drivers were installed you could visibly see the light coming out the spdif port. And now, I have no light.

---

### Post by illwill on 2008-12-28
Did you ever figure this out? I'm having the same issue.

---

### Post by mike909 on 2008-12-29
Yes, though i'm on vacation now and won't be in front of the machine for another week so I can't tell you exactly. From what I remember, you go into the setup and in the audio part you change one of the output options to 'default'. I would have to look again to be sure though.

---

### Post by illwill on 2009-01-05
I noticed that the sound worked perfectly fine on a fresh install of Ubuntu 8.10, but not on a fresh install of Mythbuntu 8.10

So it got me thinking what is running on Ubuntu that wasnt on Myth, and it turns out all I had to do was apt-get install pulseaudio and bam, in business.

---

