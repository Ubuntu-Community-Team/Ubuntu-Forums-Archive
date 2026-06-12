---
title: "Flash player headaches."
date: 2009-11-09
forum: Multimedia Software
---

### Post by hbpapa on 2009-11-09
I am a recent convert to Ubuntu and after getting everything setup and updated I decided to check out some videos on YouTube.  Well, I get to point where the page tells me that I need to install the latest version of Flash Player.  I follow the link and download the .deb for Ubuntu 8.04+, extract the file...and all heck breaks loose.  

When I try to use Synaptic Package Manager I get:
[I]E: The adobe-flashplugin needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.[/I]

So I tried to use Computer Janitor to see if I could remove the software package.  When I run it I come back with:
*E: Sub-process /usr/bin/dpkg returned and error code (2).*

Lastly, I tried to use Terminal:

First Try....(remove)
sudo apt-get remove flashplayer-mozilla[sudo]  
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package adobe-flashplugin needs to be reinstalled, but I can't find an archive for it.

Second Try...(purge)
sudo apt-get remove --purge flashplugin-nonfree
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package adobe-flashplugin needs to be reinstalled, but I can't find an archive for it.

Last Try...(force)
sudo dpkg --remove --force-remove-reinstreq flashplugin-nonfreedpkg: 
warning: ignoring request to remove flashplugin-nonfree which isn't installed.

Soooo, I can't install Flash...I can't uninstall Flash.  I can't use the Software Center either (this is the route I probably should have taken to get flash in the first place).  

What am I missing?  There has to be a step in here I either messed up or missed that will correct this.

---

### Post by gordintoronto on 2009-11-09
Install the restricted extras.

---

### Post by hbpapa on 2009-11-09
I just tried that via the Ubuntu website and received this:

E: The package adobe-flashplugin needs to be reinstalled, but I can't find an archive for it.

---

### Post by Lucky75 on 2009-11-09
You added the medibuntu repository for karmic?

[http://packages.medibuntu.org/](http://packages.medibuntu.org/) karmic free non-free

---

### Post by wojox on 2009-11-09
[http://ubuntuforums.org/showthread.php?t=1305829&page=3](http://ubuntuforums.org/showthread.php?t=1305829&page=3) Scroll down to #23

---

### Post by RedRat on 2009-11-09
Which version of ubuntu are you running. You seem to imply that you are running 8.04, yet someone else here asked about Karmic. Are you running karmic?

---

### Post by mac9416 on 2009-11-11
There are two possible fixes that I know of. The first is to run these commands...

```
$ sudo rm /var/lib/dpkg/info/adobe-flashplugin.prerm  # Deletes a troublesome config file
$ sudo dpkg-reconfigure adobe-flashplugin --force  # Force-reconfigures adobe-flashplugin
$ sudo dpkg --purge --force-all adobe-flashplugin  # Force-removes adobe-flashplugin
$ sudo apt-get install flashplugin-nonfree  # Installs flashplayer the easy way
```

...the second is to enable "partner" repositories in System->Administration->Software Sources->Other Software.

> [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner
[http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner (Source Code)

Hope one of those works!

---

