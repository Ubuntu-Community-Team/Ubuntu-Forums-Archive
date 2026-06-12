---
title: "microphone does  not work"
date: 2009-12-19
forum: Multimedia Software
---

### Post by edmurper on 2009-12-19
Hello all, 
my microphone is not working.  I have a intel corporation 82801G (ICH7 Family) High Definition Audio Controller on the karmic ubuntu version. My laptop is a  dell inspiron 9400.

I noticed that the mic was not working when I was trying to use skype. The funny thing is that the previous version(of ubuntu) allowed me to use the mic, and this current version is not working. 

I checked the microphone and it should be working, it is fine.
I don't know if I have a software related problem or maybe its a hardware issue(a false or something else). 

Or maybe I dont have the ALSA stuff? [http://www.alsa-project.org/main/index.php/Matrix:Vendor-Intel](http://www.alsa-project.org/main/index.php/Matrix:Vendor-Intel)

Anyone else having problems with skype and their mics?

Thanks

---

### Post by Tricity on 2009-12-19
If you are unsure whether you have Alsa, check /proc/asound, for example

$ cat /proc/asound/cards

That will give you a list of your sound devices (if /proc/asound does not exist, you don't have Alsa). It is very likely that you *do* have Alsa, though.

About the microphone - did you check the mixer application for zero-volume sliders or muted inputs? I found it helpful to troubleshoot problems with the text-mode `alsamixer' utility.

Let us know if this did not solve your problems.

---

### Post by gradinaruvasile on 2009-12-19
This version of Ubuntu has both ALSA and PulseAudio installed. Your mic should work. There might be some problems with the settings though.

Right-click on the sound icon in the taskbar and open the preferences. Go to the input tab, and select from the connector section the mic you want. Also check its levels. Testing is easy: tap your mic and you have there a real time input level indicator - that should move.

---

### Post by ajgreeny on 2009-12-19
Also have a look in **alsamixer** in terminal.  That may show something is muted or set too low.

---

### Post by edmurper on 2009-12-19
problem solved, it was the damn microphone(it was on mute... I feel totally stupid!!!) thanks anyway!!!:lolflag:

---

### Post by ajgreeny on 2009-12-19
> **edmurper said:**
> problem solved, it was the damn microphone(it was on mute... **I feel totally stupid!!!**) thanks anyway!!!:lolflag:
No need.  I had the same problem when I tried karmic.  alsamixer is your friend in this situation quite often, as it shows you settings that seem difficult to find any other way.

---

