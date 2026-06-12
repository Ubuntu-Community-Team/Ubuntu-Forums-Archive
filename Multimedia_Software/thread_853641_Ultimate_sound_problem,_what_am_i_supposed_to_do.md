---
title: "Ultimate sound problem, what am i supposed to do?"
date: 2008-07-08
forum: Multimedia Software
---

### Post by Nadine4 on 2008-07-08
Hey huys,

I am a completely newbie when it comes to ubuntu and i have a big problem- my sound does not work. 

I have tried the following guide ([http://ubuntuforums.org/showthread.php?t=205449)..but](http://ubuntuforums.org/showthread.php?t=205449)..but) i was not able to solve the problem. 

When i input the "aplay -l" command, i get the following message:

List of playback hardware devices
card 0 nvidia, device 0 alc861vd analog
subdevices...etc
card 0 nvidia, device 6 si3054
subdevices..etc

This means that it does recognize my soundcard and my drivers right?

Then i tried the alsamixer version as suggeste by the guide, and all my volume devices are setted to maxim, un muted, yet the sound still does not play.

Any idea what should i try next? At least to determine what s the error source...

Everything works perfect in vista by the way. 

Thanks for any input

---

### Post by Bubba64 on 2008-07-08
So your not getting any sound at all, in Ubuntu, you have opened the volume control-edit-preferences and added at the least main and pcm, these two are usually the controls. I would tick every single one on and make sure that something is not muted, I know you said you have done a check but you give no description in detail of what you did. The volume control in sound and video has never worked on any setup I have ever used in Ubuntu. I always use the volume control in the top panel. I can't personally tell if the read out with the code means that your sound drivers are working, I have old computers that use generic drivers that are in the repositories and always work without any downloads. In the alsa mixer you can choose the driver in the top left settings make sure it is looking at the right driver. Also look in system-preferences sounds and see if the sound device is set for the one your computer has actually in the alsa mixture this is what you can change the device.

---

