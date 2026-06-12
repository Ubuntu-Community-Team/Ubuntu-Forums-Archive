---
title: "problem with soundblaster audigy 2 - just playing two speakers"
date: 2008-10-05
forum: Multimedia Software
---

### Post by smasho on 2008-10-05
Hello all, 

I have a big problem with my sound card playing in 5.1 mode. After installing ubuntu was sound card correctly installed but it can played only with 2 speakers. Please can anybody help me to solve this issue?

Thanks. :)

---

### Post by markbuntu on 2008-10-05
If you are not getting surround sound but have some sound then try this:
Open etc/pulse/daemon.conf in an editor as root. In a terminal type:
```

 sudo gedit /etc/pulse/daemon.conf 

```
find the line:
```

default=sample=channels-2

```
change the 2 to 5, for 4.1, 6 for 5.1, 8 for 7.1. Save the file and restart the pulseaudio daemon. (See below for instructions on restarting pulseaudio)

If you have 2.1, 4.1. or 6.0 Surround Sound, or a custom configuration, or the above did not work properly for you, try this guide:

[http://ubuntuforums.org/showthread.php?t=795525](http://ubuntuforums.org/showthread.php?t=795525)

If that doesn't work for you, you can try editing your ~/.asoundrc file like this:

[http://ubuntuforums.org/showthread.php?t=899139](http://ubuntuforums.org/showthread.php?t=899139)

Be sure to enable and turn up the extra surround sound sliders in your volume controls!!

---

