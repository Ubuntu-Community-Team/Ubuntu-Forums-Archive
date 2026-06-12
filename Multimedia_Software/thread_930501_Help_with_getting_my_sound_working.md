---
title: "Help with getting my sound working"
date: 2008-09-26
forum: Multimedia Software
---

### Post by dannybolabo on 2008-09-26
Hi all. I recently purchased a Dell Mini 9 and installed ubuntu on it. All works perfectly, except for the sound - there isn't any.

I've been through the steps at [this sticky]("http://ubuntuforums.org/showthread.php?t=205449") but it seems like it should be working. When I type aplay -l, it comes up with the right sound card. The mixer shows all volume levels at full and not muted. Being relatively new to linux, I'm not sure how to procede.

Any help will be greatly appreciated!

---

### Post by dannybolabo on 2008-09-26
Ok stop the search party people. Apparently I had to [configure alsa-base]("http://ubuntuforums.org/showpost.php?p=5131958&postcount=2"). This gave me an extra volume slider for the speakers, which was on 0. It's now working properly.

---

### Post by adc_mario on 2008-10-07
Glad you got yours fixed, I tried the alsa configure thing but i must not be doing something right..

do you add this:

options snd-hda-intel model=dell

any info would be appreciated, thanks!

--UPDATE--
Ok I figured it out, I just needed to reboot. If anyone else is stuck, heres what to do:

Open the Terminal and type:

gksudo gedit /etc/modprobe.d/alsa-base

(your password will be required)

Then a edit window will open, scroll to the bottom and add this to the options list and add this line:

options snd-hda-intel model=dell

I put mine under "options snd-usb-caiaq index=-2"

Then reboot your system, and double-click on the speaker icon at the top, and a "Speaker" option should be listed, turn it up to get sound. And your done. YAY!

Thanks for the direction on this one Danny!

---

### Post by Denny Johnson on 2008-10-07
Thanks to you both.
Mario, your post was a most helpful clarification for a neewb

---

### Post by Denny Johnson on 2008-10-08
mmmmmm................seems that since adding this line, I no longer have a working mic.
Before adding the "options snd-hda-intel model=dell" line, I had sound and mic in kernel 2.6.22-15.
The addition of the line in kernel 2.6.24-19 got sound working there.
But, now there is no mic in either kernel.
I changed the line to "options snd-hda-intel model=STAC9228" and it didn't change anything.
Removed the line and still have sound in both kernels but no mic in either kernel.
When I say no mic........neither of 2 mics work and in system/preferences/sound/ when testing SOUND CAPTURE w TEST SOUND, there is crackling and test sound at first [1 -2 sec], then silence w an occasional crackle.
Perhaps it's just coincidence and unrelated to the above sound fix????????????
Any suggestions appreciated, thanks.

---

### Post by adc_mario on 2008-10-10
Yikes that doesn't sound good, I haven't tested the mic at all yet, I will check mine out when I get home and see whats going on. I haven't checked the mic or the camera yet, but so far everything else seems to work just fine after all the updates are ran. 

And you say both the internal, and external mic dont work? How about external speaker?

---

### Post by Denny Johnson on 2008-10-12
Don't have an internal mic, but problem occurs w 2 different jacked mics and also TEST SOUND.
Occurs w all speaker setups.
I have my doubts that it's related to the fix you suggested as I may have changed other things, don't remember what, before finding the mic problem.

---

