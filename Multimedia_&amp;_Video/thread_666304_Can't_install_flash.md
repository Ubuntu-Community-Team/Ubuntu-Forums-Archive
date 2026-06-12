---
title: "Can't install flash"
date: 2008-01-13
forum: Multimedia &amp; Video
---

### Post by davbren on 2008-01-13
Hey I just did a fresh install of Gutsy on a desktop and I'm having some issues installing flash, which is odd coz it was working fine before hand, but now even after installing flash, when i go to websites that use flash it says i need to install it. I've tried Gnash, that gets rid of the message but doesn't show *any* flash at all. I've also tried Automatix and thats not helping eiter...

Any ideas?

---

### Post by gandaran on 2008-01-13
don't use gnash, it has many problems, make sure you uninstall mozilla-plugin-gnash, then install the flashplugin-nonfree, you can find it on synaptic if you have all the repositories enabled or better still go to add/remove programs or even synaptic and install the (ubuntu restricted extras) , which will install nearly everything you will  need on you computer.

---

### Post by flamelab on 2008-01-13
For now the flash plugin is "broken"

Go to Adobe , download the tar.gz file , untar it , cd to it and 

```
chmod +x flash-installer
```

and

```
./flash-installer
```

and do what it says

---

### Post by DecemberWinds on 2008-01-13
[http://www.howtoforge.com/forums/showthread.php?t=18529](http://www.howtoforge.com/forums/showthread.php?t=18529)

First uninstall your gnash flash:

sudo apt-get remove flashplugin-nonfree gnash

Install the GOOD flashplayer:

[http://fpdownload.macromedia.com/get/flashplayer/installers/archive/fp9_archive.zip](http://fpdownload.macromedia.com/get/flashplayer/installers/archive/fp9_archive.zip)

Unzip the archive and navigate to

/desktop/fp9_archive/9r48/install_flash_player_9_linux/flashplayer-installer

and run that program.

That's what worked for me. :)

---

### Post by gandaran on 2008-01-13
> **flamelab said:**
> For now the flash plugin is "broken"

Go to Adobe , download the tar.gz file , untar it , cd to it and 

```
chmod +x flash-installer
```

and

```
./flash-installer
```

and do what it says


I have done two recent ubuntu  installations and had no problems installing flashplugin-nonfree, I don't believe the flash plugin is "broken", yes I know many unfortunate users  experienced problems, I don't know why , I'm still intrigued, maybe they are using the wrong repository server (main server versus your local server) this is just a though!

---

