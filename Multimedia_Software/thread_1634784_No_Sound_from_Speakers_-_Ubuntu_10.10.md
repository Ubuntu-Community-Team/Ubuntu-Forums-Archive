---
title: "No Sound from Speakers - Ubuntu 10.10"
date: 2010-12-01
forum: Multimedia Software
---

### Post by JPS913 on 2010-12-01
Hey everyone,

Just installed Ubuntu 10.10 with Wubi (took forever to figure out how to get the wubi.exe to recognize the 10.10 iso) and I don't have sound coming from my speakers. Audio works fine with headphones, but output from speakers is non-existent.

I get sound when I boot into Windows 7, so I doubt it had something to be with the actual speakers. I'm really new to Ubuntu (but loving it!) so troubleshooting is a little difficult for me, especially with terminal commands.

I'm using a Samsung Q430, Core i5, GeForce 310m, and 4GB ram if that helps with the diagnosis. 

I appreciate any help I can get. 

Thanks and have a good one.

---

### Post by lidex on 2010-12-01
Click on your volume icon in panel. Select 'Sound Preferences' on the 'Output' tab, at the bottom, toggle the 'Connector' setting.

---

### Post by Legacybob on 2011-03-04
I have exactly the same problem, did you ever resolve it?

---

### Post by fjornada on 2011-04-06
I had this exact problem after I booted my laptop into Windows. I tried some solutions on the internet, like passing other options to the snd_hda_intel module (editing /etc/modprobe.d/alsa-base.conf), but that didn't help. However, the speakers magically went back after I removed the battery and power supply for ~1min. I guess the windows driver must have put the sound hardware in a non-default state...

---

### Post by Legacybob on 2011-04-26
I still have the same problem, boot from start in Ubuntu and the sound is fine.  Boot into Windows and then immediately into Ubuntu and no sound.  Shut down, leave it a short while and boot Ubuntu, sound fine again.  I just live with it now.

---

### Post by lidex on 2011-04-27
> **Legacybob said:**
> I still have the same problem, boot from start in Ubuntu and the sound is fine.  Boot into Windows and then immediately into Ubuntu and no sound.  Shut down, leave it a short while and boot Ubuntu, sound fine again.  I just live with it now.

You may want to look at a bios update. Yours is a little less common as the usual issue is resolved by rebooting from windows directly into ubuntu.

---

