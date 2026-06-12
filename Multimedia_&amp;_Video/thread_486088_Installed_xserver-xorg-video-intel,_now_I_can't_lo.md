---
title: "Installed xserver-xorg-video-intel, now I can't log in"
date: 2007-06-27
forum: Multimedia &amp; Video
---

### Post by obiwaynekenobi on 2007-06-27
I just ran ```
sudo apt-get install xserver-xorg-video-intel
``` to try and make Ubuntu 7.0.4 recognize my graphics card so I could use a higher resolution than 1024x768; I'm on a Dell Inspiron B130.  The install went fine so I restarted the computer - whenever I try to log in with my username, the screen goes black, displays some command line text for about 2 seconds so I can't read what it's saying, and then kicks me back to the login screen.  It does this every time I try to log in.

I tried to start in recovery mode and ran ```
dpkg-reconfigure -phigh xserver-xorg
```, and I can boot to the GUI by typing "startx" from the console, however I'm unable to log in with my normal username/password combination; it keeps kicking me back to the login as I described above.  Anyone know how I can fix this and/or what I did wrong?  Also if it matters I'm using the GNOME desktop.

---

### Post by dabl on 2007-06-27
Among the possibilities, you might need to manually (in sudo mode) edit the /etc/xorg.conf file and change the driver name to "intel".

---

### Post by tseliot on 2007-06-27
Boot in **Recovery Mode **and type:
```
apt-get --purge remove xserver-xorg-video-intel
```

```
apt-get install --reinstall xserver-xorg-video-i810
```
```
apt-get install 915resolution
```

then type:
```
nano -w /etc/X11/xorg.conf
```

and set the driver to "i810" instead of "intel" in the Section Device of the file.

Then press CTRL+X to save and exit

then reboot by typing:
```
reboot
```

and boot Ubuntu as usual

---

### Post by obiwaynekenobi on 2007-06-27
Thanks for the reply.  When I try to run apt-get install --reinstall xserver-xorg-video-i810 it will not connect to us.archive.ubuntu.com (I get a message saying cannot resolve us.archive.ubuntu.com), but I just tested the site on a WinXP machine and it appears to be loading (and I can ping it successfully).  Any thoughts?  Should I just wait a while and try it again?

---

### Post by obiwaynekenobi on 2007-06-27
Well I figured out why it couldn't connect (no network connectivity in recovery mode).  So I created a new user and was able to boot and download xserver-xorg-video-i810 using the Synaptic manager.  I can now log in with my old account, but I still can't set my screen resolution to 1280x800 (the highest I can select is 1024x768) like I had initially wanted.

---

### Post by obiwaynekenobi on 2007-06-27
Okay I'm stupid.. it wasn't showing up because I forgot to add it to xorg.conf :-P  Looks like I need a refresher course in linux.

---

### Post by Fadsjeik on 2007-08-11
Good to see you got your system working again! It took me an hour or two to figure everything out as well, when I had the exact same problem. Does anybody know what causes this problem? And are the xserver-xorg-video-intel drivers better than the i810 drivers, or are we not missing out on any good stuff with our old drivers? What about the amount of shared memory allocated? I've been looking for a way to increase this from the 8mb it currently uses (the obvious solution of specifying the amount of shared memory to use in xorg.conf sadly doesn't work).

Any help and answers are greatly appreciated!

---

