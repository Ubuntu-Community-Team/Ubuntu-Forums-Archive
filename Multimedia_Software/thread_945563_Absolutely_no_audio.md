---
title: "Absolutely no audio"
date: 2008-10-12
forum: Multimedia Software
---

### Post by thequark on 2008-10-12
Hey everyone, I'm having trouble getting my sound card to work.  I've been all over the forums and internet to no avail.  My audio information is

> 
00:1b.0 Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller
01:00.1 Audio device: ATI Technologies Inc RV620 Audio device [Radeon HD 34xx Series]


Furthermore, whenever I try to play say an mp3 in totem I get the error:

Failed to connect stream: Invalid argument.

Also, when I test the sound in System > Preferences > Sound, I get the same error.  In the same page, there are 3 devices available under "Device Mixer Tracks" and they are:

HDA Intel (Alsa mixer)
HDA ATI HDMI (Alsa mixer)
Realtek ALC888 (OSS mixer).

The default is "HDA Intel (Alsa mixer)".  If anyone knows what to do, let me know.

Thanks.

---

### Post by markbuntu on 2008-10-12
Look in here:

[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

You can also look here (look through the entire thread if the OP does not fix your problem , people have posted solutions for many specific machines). You should look at the options for the ALC888:

[http://ubuntuforums.org/showthread.php?t=616845](http://ubuntuforums.org/showthread.php?t=616845)

[http://ubuntuforums.org/showthread.php?t=820959](http://ubuntuforums.org/showthread.php?t=820959)

---

### Post by thequark on 2008-10-16
Thanks! I'll take a look and see if this works.

---

