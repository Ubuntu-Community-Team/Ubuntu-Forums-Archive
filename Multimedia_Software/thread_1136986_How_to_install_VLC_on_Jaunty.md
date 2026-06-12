---
title: "How to install VLC on Jaunty?"
date: 2009-04-25
forum: Multimedia Software
---

### Post by willybk3 on 2009-04-25
I keep getting cannot install VLC because of dependency issues - use synaptic pack mgr to resolve.  When I try to use synaptic I get libcaca0 not supported - will not install VLC.  I just want to put a commercial DVD in and watch - like in 8.04!

---

### Post by kpkeerthi on 2009-04-27
Install it from PPA.

[https://launchpad.net/~kow/+archive/ppa]("https://launchpad.net/~kow/+archive/ppa")

---

### Post by lindsay7 on 2009-04-27
Look in add/remove programs.

---

### Post by Arup on 2009-04-27
The repos install version 1.00 alpha and it solves the problem of the double screen. I have installed it via this method on my Jaunty x64 and it works out fine.

---

### Post by willybk3 on 2009-04-27
I have tried all responses to no avail!  I guess I shall have to wait for an official VLC player 1.0 to be released.  My system (which worked perfectly before jaunty) will no longer play a DVD!  Price paid for early adopter.  Tired of getting broken package or library libcaca0 not found or cannot be installed.

---

### Post by hotweiss on 2009-04-27
[http://www.videolan.org/vlc/download-ubuntu.html](http://www.videolan.org/vlc/download-ubuntu.html)

The above worked for me.

I just removed the mozilla totem plugin so that the vlc plugin would work:

> sudo apt-get remove totem-mozilla

---

### Post by mc4man on 2009-04-27
Go into synaptic, search libcaca0 and post what version is installed and or available.

Also go to System -> Admin... -> Software Sources and make sure first 4 boxes are checked for ubuntu and under the updates tab the first 2. (if any aren't then enable, click close and reload

If you *upgraded vs. a fresh install* post your sources.list and also search vlc in synaptic and remove all packages with vlc in name if installed (vlc, vlc-nox, vlc-data, libvlccore0, any vlc plugins

```
cat /etc/apt/sources.list
```

---

### Post by willybk3 on 2009-04-30
My thanks to mc4man for the suggestion that was offered - it worked.  I did the upgrade via the alternate cd (which worked just fine).  I did not double check the sources, which I then did and make the appropriate changes; then I could install the pre-release of VLC 1.0, this version has a few bugs, but in general I now can play a commercial DVD.  Once again thanks to everyone for their suggestions and especially to the team that is keeping the Ubuntu name advancing.

---

