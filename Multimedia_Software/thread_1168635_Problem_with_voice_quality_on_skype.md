---
title: "Problem with voice quality on skype"
date: 2009-05-24
forum: Multimedia Software
---

### Post by ismialexis on 2009-05-24
I use skype for voice and video calling.  The voice quality is bad for the other person.  They say they can barely understand me and they are also hard for me to understand.  Also when I use video.  MY webcam always zooms in on me and I don't want it to.  How can i fix all this?

thanks in advance

---

### Post by ismialexis on 2009-05-24
also how do I use a plug in microphone on my computer instead of the built in one.  I have a dell mini inspiron 9

---

### Post by fatigue on 2010-02-24
I have same exact problem. Could anyone help us?

---

### Post by fatigue on 2010-02-24
any one please

---

### Post by Sven6210 on 2010-02-25
Can you identify the sound chip your computer has? Something like 'alc268' or whatever. If you can give me the sound chip I might be able to help you to try some new settings in the ALSA configuration file.

---

### Post by fatigue on 2010-02-25
my sound chip is HDA intel
realtek ALC 268

Thank you so much for help

---

### Post by Sven6210 on 2010-02-27
[COLOR=black][FONT=Verdana]I recommend to adjust the ALSA  configuration file (/etc/modprobe.d/alsa-base.conf)[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]The detailed steps:[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]1. sudo gedit  /etc/modprobe.d/alsa-base.conf[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]2. Search in the file whether a  line including 'snd-hda-intel' exists, if so please delete that line[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]3. Add the following two lines  to the configuration file:[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]===start here===[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]# eeePC 900a  patch[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]options snd-hda-intel index=basic[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]===end here===[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]4. Restart the system

Before you do that please save the old version of the ALSA configuration file. I am not sure whether it will work.


If this doesn't work for you I suggest you look here in the forum about other potential settings for the line 'options snd-hda-intel' suitable for the ALC268.

I have the ALC269 and need the following setting for my EeePC 900a:
[/FONT][/COLOR][COLOR=black][FONT=Verdana]options snd-hda-intel index=0  model=quanta

Good luck
[/FONT][/COLOR]

---

### Post by fatigue on 2010-03-13
Thanks
but seems like Pulse audio and Ubuntu 8.10 with skype has some serious problem.
Ive been looking aroudn but still no solution. Anyone else has good idea?

---

### Post by Sven6210 on 2010-03-14
Why don't you update to Ubuntu 9.10 KK? Alsa and Puseaudio work much better in 9.10.

---

### Post by fatigue on 2010-05-03
Thank you guys.
I gave up with 8.10 9.04 and 9.10

I upgraded to 10.04 today and skype works perfect now.
It was definately Pulse Audio issues.

---

