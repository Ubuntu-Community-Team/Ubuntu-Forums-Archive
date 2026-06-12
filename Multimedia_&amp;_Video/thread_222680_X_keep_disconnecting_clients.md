---
title: "X keep disconnecting clients"
date: 2006-07-25
forum: Multimedia &amp; Video
---

### Post by m4rqz on 2006-07-25
Windows keep crashing due to disconnection from the X server, but I have no idea why.. I've had this problem for a week or so now and it starts to get reeaaaly annoying. 

From the start I thought it was a bug in firefox since it was just firefox that crashed, and I thought it was the old segfault-in-flashplayer stuff, but now every once in a while gaim, gnome-panel and gedit also dies.

When I start gedit or firefox from terminal and use it until it crashes I get this output:

```
The application 'gedit' lost its connection to the display :0.0;
most likely the X server was shut down or you killed/destroyed
the application.
```

I'm running newly updated Dapper Drake, GNOME, Metacity (2.14.5), without Compiz, XGL or AIGLX.  I use the fglrx drivers from ubuntu repos.

`Xorg -version` gives
```
X Window System Version 7.0.0
Release Date: 21 December 2005
X Protocol Version 11, Revision 0, Release 7.0
Build Operating System:Linux 2.6.15.7 i686
Current Operating System: Linux alpha 2.6.15-26-686 #1 SMP PREEMPT Mon Jul 17 20:14:14 UTC 2006 i686
Build Date: 16 March 2006
        Before reporting problems, check http://wiki.x.org
        to make sure that you have the latest version.
Module Loader present

```

---

### Post by tseliot on 2006-07-25
switch to the opensource driver until the you find a solution:
```
sudo dpkg-reconfigure xserver-xorg
```

and select the "ati" driver. Press ENTER whenever you don't know the answer to the other questions.

Then log out and press CTRL+ALT+Backspace

---

### Post by m4rqz on 2006-07-27
> **tseliot said:**
> switch to the opensource driver until the you find a solution:
```
sudo dpkg-reconfigure xserver-xorg
```

and select the "ati" driver. Press ENTER whenever you don't know the answer to the other questions.

Then log out and press CTRL+ALT+Backspace

Thanks, the problems are gone now. But if someone has a solution for this were I can use the fglrx drivers I would really like it. Our 3d programming project start this semester... Don't make me use Windows :(

---

### Post by tseliot on 2006-07-27
I don't use ATI cards therefore I can't help you.

Maybe you can try this guide:
[http://www.ubuntuforums.org/showthread.php?t=204910](http://www.ubuntuforums.org/showthread.php?t=204910)

---

