---
title: "Help HDA-Intel Realtek ALC883 SPDIF Problems"
date: 2007-02-12
forum: Multimedia &amp; Video
---

### Post by Trippen Out on 2007-02-12
okay so im new and i want to use my spdif with my HDA-Intel Realtek ALC883 its from a gigabyte 965p s3 motherboard and i cant seem to get it to turn on .. i understand there is an alsa patch from the reading ive done on the forums but they seem to pertain to laptops this is not a laptop and im to new to understand how to apply the patch anyway so what do i do and how do i do it.. yes feel free to break it down to the most simple commands because im .99% ignorant thanks

---

### Post by Trippen Out on 2007-02-12
bump

---

### Post by Trippen Out on 2007-02-14
another bump.. still looking for help

---

### Post by Trippen Out on 2007-02-14
??? maybe the ubuntu community isnt as helpful as everyone says

---

### Post by freddyg on 2007-02-14
assuming your sound works normally, have you tried  AndyC_772's suggestion here [http://ubuntuforums.org/showthread.php?t=88203](http://ubuntuforums.org/showthread.php?t=88203) ?

---

### Post by Trippen Out on 2007-02-15
no i dont have the option under alsa mixer that will turn on the sdpif port .. it wont light up or anything

---

### Post by penakoski on 2007-03-01
I have Gigabyte GA-965P-DS3 motherboard with same Realtek ALC883 chip.
I have almoust same problem, audio from analag output works exellent
but digital sounds dont work correctly.
AC3 sounds from movies (with pass-through setting in
mplayer) cames out from optical-output. 
I have activated IEC958 digital output in alsa mixer.
Problem is that I want other sounds as well to came out optical output to my amp.

---

### Post by Vincent_Lin on 2007-03-01
Hi,

checek out this link [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)
and look up the place that says to modify "/etc/modprobe.d/alsa-base" with line "options snd-hda-intel model=ref" added in this file.    Exact model to use can be looked up in the documentation mentioned in that Howto.  Or, try "ref" first as it is recommended.

Don't forget to use alsamixer to crank up the volumes and use "alsactrl store 0" to save the settings as default, afterwards.  Then reboot.  spdif output should be there, along with regular analogue audio out and front headphone jack out, if the machine you built has all the wires connected correctly.

Cheers,

Vincent Lin

---

### Post by penakoski on 2007-03-01
that did'nt   help, but now I looked in aplay -L and there was this
plugin spdif 'cards.pcm.iec958' .
I putted that in amarok config and now there comes some sound out of my 
digital output. Music plays only left channel and there is loud high
pitched noise.
Should I update my driver or what?

---

### Post by penakoski on 2007-03-01
Now I have newest drivers and I putted that "options snd-hda-intel model=3stack-dig"
in "/etc/modprobe.d/alsa-base" like ALSA-Configuration.txt says. 
Digital output still don't work . :(

---

### Post by Vincent_Lin on 2007-03-01
3stack-dig is the model I use as well.

You still have to run alsamixer and crank up all volumes, especially that IEC958 thingy.  After that, run alsactrl store 0 to save this volume settings as default, which will enable your sound/volumes setting to survive reboot.

Cheers,

Vincent

---

### Post by penakoski on 2007-03-02
Alla sounds are on in alsamixer but still don't work.
But thanks for your help anyway.

---

