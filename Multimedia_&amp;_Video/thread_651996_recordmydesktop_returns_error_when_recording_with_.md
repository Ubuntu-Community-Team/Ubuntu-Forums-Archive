---
title: "recordmydesktop returns error when recording with audio"
date: 2007-12-28
forum: Multimedia &amp; Video
---

### Post by vvoois on 2007-12-28
I downloaded and installed recordmydesktop.
It records fine as long as i don't check the audio option. It does not matter wether i select the DEFAULT (ALSA) driver or Jack, both errors indicate that the audio device is somehow locked or not loadable (dlopen/dlsym error on libjack.so and could not open or configure soundcard in ALSA mode).
Yes i've played with the recorder tab in the mixer to attempt having any recorder getting going, but no, it keeps returning these errors.
Also tried changing the DEFAULT into front, internal and wavetable but no luck either.
It happens with the latest edition of recordmydesktop and the ubuntu supported edition (which is older)
I got a terratec dmx 6fire, i know this card is not easy to share hardware wise but had no problems routing jack with other apps. (recordmydesktop does not appear in the jack patchpanel or connection panel which i find strange as well.)

I am not able to record video and audio with Istanbul either:resource busy or not available. So this has to be a driver issue or something...

Anyone who can help me out with this matter?

---

### Post by theorganloft on 2007-12-28
I am having the same problem with it.  I get an error that says it cannot load the Jack Library.  I think that the Ubuntu version does not have Jack compiled correctly.

Here is what I get:
[IMG]http://theorganloft.googlegroups.com/web/Screenshot-gtk-recordMyDesktop.png?gda=yzgdNlMAAACp-nT8DqtreQQBe2CjPKkp09Rn-zCDzBNnUYhwE9kJ7GG1qiJ7UbTIup-M2XPURDQ5YzrLGfcTcX3xVxYi5tGrlfENx29VZCXHgTXXibbDCAKOZFcal87Qff7gkugrF_g[/IMG]

---

### Post by vvoois on 2007-12-29
If it is not compiled correctly, i wonder why Jack does work with other applications?
Istanbul and RMD are the only two capture applications i tried so far, yet both don't offer client patches for Jack while RMD makes me assume it can hack in on Jack by just tapping in on its audio streams.
For as far as i could get Jack going i had to patch the clients together in the patchpanel prior to use both clients. But RMD doesn't simply show up in the clients list of Jack's patchpanel, neither its connection panel.

---

### Post by theorganloft on 2007-12-30
> **vvoois said:**
> If it is not compiled correctly, i wonder why Jack does work with other applications?
Istanbul and RMD are the only two capture applications i tried so far, yet both don't offer client patches for Jack while RMD makes me assume it can hack in on Jack by just tapping in on its audio streams.
For as far as i could get Jack going i had to patch the clients together in the patchpanel prior to use both clients. But RMD doesn't simply show up in the clients list of Jack's patchpanel, neither its connection panel.

I did not mean to say Jack, I meant to say recordmydesktop was not compiled for Jack and the repository version is not compiled to support Jack.  

It looks like we have to do it (compile) manually or get the repository fixed. Maybe if one of us gets it working, we can submit it to the repository. 

We are having the same problem so I think our systems are fine.  I would really like to use this software but if I cannot get it to work, I will simply record the video through my video mixer.   That way I can save CPU resources for the apps. 

 

Sorry for the Typo.

---

### Post by vvoois on 2008-02-24
I updated jack recently, it seems that if i want to have the software with jack-support, i have to recompile it including the latest version of jack so that the client protocol matches the server protocol.
But i doubt if i can manage to insert the jack client protocol API routines.

---

