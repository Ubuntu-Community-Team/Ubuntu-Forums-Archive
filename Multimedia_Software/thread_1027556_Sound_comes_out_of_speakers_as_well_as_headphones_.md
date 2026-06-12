---
title: "Sound comes out of speakers as well as headphones while headphones are plugged in"
date: 2009-01-01
forum: Multimedia Software
---

### Post by Shpongle on 2009-01-01
my sound is working fine bt when i plug my headphones in the sound still comes out of the speakers im using a toshiba equium a200-1ac laptop with a realtek ALC861 audio card, any help is welcomed

thanks

---

### Post by gender on 2009-01-01
Maybe you could open Volume Control and mute the appropriate things? Whenever I plug in my headphones, I mute the speaker, but that might not work for you exactly.

---

### Post by Shpongle on 2009-01-01
ive tried that man, i tried all the different devices and the options for them, the only option to do with headphones is the switches option and i have that enabled. . .

---

### Post by Shpongle on 2009-01-03
bump

---

### Post by chalewa on 2009-01-03
there was a thread about this issue a while back. i will try and find it.

---

### Post by AlanR8 on 2009-01-03
Had a similar issue with my Sony Vaio. After searching these forums I found this fix that did the biz:

> Now for the audio-jack problem (sound refuses to come out trough the headphones-jack.)

Edit /etc/modprobe.d/alsa-base (sudo gedit /etc/modprobe.d/alsa-base) and add this in the bottom of it

options snd-hda-intel model=vaio

then do this:

sudo apt-get install linux-backports-modules-$(uname -r)


do these things and enjoy your fz21m


I'm sure you could modify the code to sort your machine.

---

### Post by Shpongle on 2009-01-07
i tried that there and it didn't work, i changed the code too, thanks any way tho, iv been searchin all over the place tryna fix this???

---

### Post by IQRules on 2009-01-07
Open the speaker icon, click Preference, select Headphone Jack sense switches.
Or try with "$ gnome-alsamixer".

---

### Post by Shpongle on 2009-01-07
> **IQRules said:**
> Open the speaker icon, click Preference, select Headphone Jack sense switches.
Or try with "$ gnome-alsamixer".

iv already tried that , but still no joy:(

---

### Post by IQRules on 2009-01-07
Did not see "Headphone Jack Sense" switch in the image. Are you in 8.04 version?

---

### Post by Shpongle on 2009-01-08
> **IQRules said:**
> Did not see "Headphone Jack Sense" switch in the image. Are you in 8.04 version?

no im on 8.10, theres a switch for headphones which i have enabled

---

### Post by Shpongle on 2009-01-28
iv looked around the net and it just seems to be a problem with this sound card, realtek alc 861-vd , if ny one happens to get this workin could you please let me know ,

thanks 

Dill

---

### Post by neu2buntu on 2009-01-28
google this ```
realtek alc 861-vd snd-hda-intel model=
```

there are some fixes similar to yours ,so maybe one of these will do,

---

### Post by Shpongle on 2009-04-30
i finally fixed it, by changing the /ect/modprobe.d/alse-base file

and changing the model to lenovo

snd-hda-intel model=lenovo

now ubuntu is perfect!! ahhhh

---

### Post by yoasif on 2009-04-30
> **DillByrne said:**
> i finally fixed it, by changing the /ect/modprobe.d/alse-base file

and changing the model to lenovo

snd-hda-intel model=lenovo

now ubuntu is perfect!! ahhhhhey, could you do everyone else with your machine by [reporting the bug]("https://bugs.launchpad.net/ubuntu/+source/linux/+filebug") and your "fix"? 

post the url that you get when you do ```
wget http://alsa-project.org/alsa-info.sh -O alsa.sh && bash alsa.sh
```to provide the information that developers will need.

You can use my bug report for a similar issue as an [example]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/360181").

---

### Post by Shpongle on 2009-05-01
i reported the bug and the fix :) , hope it helps others!

---

