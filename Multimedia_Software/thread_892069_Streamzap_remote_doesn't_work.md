---
title: "Streamzap remote doesn't work"
date: 2008-08-16
forum: Multimedia Software
---

### Post by josesanders on 2008-08-16
I bought a new Streamzap remote because people have said it works well in Linux.  I plugged it in and installed lirc with the following command:

$ sudo apt-get install lirc

In the setup, I chose the Streamzap remote.  When the installation finished, it tried to start the process, but it failed.  I tried rebooting, but the remote still didn't work.  I then tried just restarting lirc:

$ sudo /etc/init.d/lirc restart

There were no errors displayed on the screen, but the remote still didn't work.  I can see the light go on on the receiver, but key presses have no effect.  I'm running Hardy, and I'm trying to use this with MythTV.

---

### Post by josesanders on 2008-08-17
Ok, solved the problem.  I was just missing the .lircrc file.  I downloaded the file from here:

[http://ubuntuforums.org/showthread.php?t=639072](http://ubuntuforums.org/showthread.php?t=639072)

It is in response #5 by nida79.  I just copied the file to ~/.lircrc and ~/.mythtv/.lircrc

---

