---
title: "Audio only works during login, sound test"
date: 2008-08-10
forum: Multimedia Software
---

### Post by marioallstar on 2008-08-10
A friend of mine made a fresh Ubuntu installation. We have adjusted the volume levels to the point where sound is able to be heard, but it only works with gdm, or during a privileged sound test (for example, it works in the hardware troubleshooting program after escalating to root).

This makes me think that for some reason only root can play sound, but running a program like Firefox under sudo, the problem persists--no sound.

I have tried clearing out all hidden directories in his user account (~/.*) in case a bad setting was the culprit, but this is not the case.

According to the user settings dialog, he has audio privileges on his normal user account.

Edit: I've also used chmod to give 666 permissions on /dev/snd/* and /dev/dsp*

Any ideas? I tried checking past threads on this web site and others, but there has been no luck.

---

### Post by kuamudhan on 2009-01-05
The same thing happensto me too.
I tried disabling the login sound and then the sound test worked, as well as the login sound.
But now nothing works. Maybe it is because of the new restricted drivers i tried installing.
Will get back as soon as I know.

---

### Post by markbuntu on 2009-01-05
If you have just installed Intrepid 8.10 or Hardy 8.04 you should go here so you can get all the missing parts so you can control your sound properly:

[http://ubuntuforums.org/showthread.php?t=997506](http://ubuntuforums.org/showthread.php?t=997506)

If that does not fix you up and you need more help go here

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

