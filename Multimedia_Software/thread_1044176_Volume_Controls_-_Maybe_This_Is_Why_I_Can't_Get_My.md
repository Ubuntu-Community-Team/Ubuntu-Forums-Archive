---
title: "Volume Controls - Maybe This Is Why I Can't Get My Sound To Work"
date: 2009-01-19
forum: Multimedia Software
---

### Post by umechanism on 2009-01-19
I'm still trying to get my sound to work on my new Dell Desktop.  I 've searched the forums back to front and have tried many things.  I'm not giving up yet but one of my biggest hurdles is actually understanding **WHICH** volume settings to adjust.  Why do we have so many to choose from when I only have one sound card and one set of speakers.:(

See Image (if it actually posted correctly).

[IMG]http://tinyurl.com/a2orkl[/IMG]
[http://tinyurl.com/a2orkl](http://tinyurl.com/a2orkl)

---

### Post by markbuntu on 2009-01-19
The alsa mixer and the volume control mixer do the same thing. If you adjust one you can see the other one change. The Volume Control Preference is which item you would like the little speaker icon to control. 

System/Preferences/Sound is where you choose the sound for your applications, OSS, alsa and pulseaudio are soundservers or you can choose the hardware directly or use autodetect which will direct the sound however your application wants. The Default Mixer Tracks is where you set what your multimedia keys control.

As you can see these are not all the same thing except the mixers and the panel mixer is easier to access and use than the command line alsa mixer.

There is more here, and plenty of links to even more info

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

### Post by umechanism on 2009-01-19
Thank you for the explanation and the link.  I have never heard sound from my brand new Dell Desktop and I have searched this forum over and over but have never seen the link you sent me.  I will pour over those details and see if I can get sound to work.

Thanks again.

---

