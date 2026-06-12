---
title: "Onboard Sound won't work"
date: 2009-01-11
forum: Multimedia Software
---

### Post by rogval on 2009-01-11
Im trying to get my onboard sound to work with my Ubuntu 8.10.  I have an N2PAP-LITE mobo with nVidia chipset which has nVidia nForce2 onboard sound.  Nothing fancy, just audio out, mic, and audio in.  So I cruise through the comprehensive sticky at the top of this forum and it still doesn't work...nothing is muted (at least as I can tell...the ALSA mixer isn't the most user friendly thing in the world!!) and according to aplay -l, It shows the following...

**** List of PLAYBACK Hardware Devices ****
card 0: nForce2 [NVidia nForce2], device 0: Intel ICH [NVidia nForce2]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: nForce2 [NVidia nForce2], device 2: Intel ICH - IEC958 [NVidia nForce2 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

So like I said above...I don't think anything is muted from what I could tell and if I do a test in sound preferences, then I get nothing...needless to say I don't get anything from youtube or whatever.

I am using an Altec Lansing speaker setup, which worked just fine 10 mins ago when windows was on this system...here is a link to show you what model speakers I have...

[http://www.alteclansing.com/index.php?file=north_product_detail&iproduct_id=vs4221](http://www.alteclansing.com/index.php?file=north_product_detail&iproduct_id=vs4221)

Any help is appreciated...I'm pretty good with PC's and hardware, but I'm just not much of an audio buff, so some of this mixer and audio terminology is over my head!!

Thanks
Roger

---

### Post by rogval on 2009-01-12
New Update, if this helps anyone...

After a bag full of system updates...I noticed the test in sound preferences produces a slight, faint tone when turned on, and as soon as I hit OK, it would go away...so that leads me to believe that maybe something is wrong with the speakers.  So I grab some rinky-dink pc speakers from the spare parts tub and plug them in and....NOTHING!!

So that leaves me to believe there is something not lining up between the onboard audio hardware and Linux!!

Hope someone has something soon, cause this is driving me crazy!!

Thanks
Roger

---

### Post by linux_tech on 2009-01-12
In terminal type-
```
gksudo alsamixer
```

then check volume settings

---

### Post by rogval on 2009-01-12
> Re: Onboard Sound won't work
In terminal type-
Code:

gksudo alsamixer

then check volume settings 

That's the funny/confusing thing.  I've done all this simple stuff...and it still doesn't work!!

Thanks
Roger

---

### Post by rogval on 2009-01-17
I just find it odd that ubuntu doesn't automatically recognize familiar sound cards like AC97 onboard and/or soundblaster for that matter!!

---

