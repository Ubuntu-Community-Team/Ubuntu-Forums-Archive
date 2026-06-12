---
title: "[lubuntu] XBMC tearing"
date: 2014-05-06
forum: Multimedia Software
---

### Post by KillEmAllx on 2014-05-06
Hi guys,
I've installed Lubuntu 14.04 + XBMC 13 on my Compaq Mini laptop and I'm facing video playback tearing on XBMC. Vsync is enabled on XBMC, as well as "synd video to display" among other settings I found could help, but nothing.
The CPU is a dual core Intel Atom N455 and the graphics are Intel Graphics Media Accelerator 3150 (I think).
I read somewhere something abouy enabling TearFree but couldn't find a way to do it.
All suggestions are welcome! Thanks in advance.

---

### Post by P-I H on 2014-05-11
I am using XBMCbuntu 13 and have no problem with tearing.
I have not used the fix proposed in this thread, but it may help.
[https://bbs.archlinux.org/viewtopic.php?id=176651](https://bbs.archlinux.org/viewtopic.php?id=176651)

---

### Post by WigginsACK on 2014-05-11
Tearfree is an option in the catalyst control centre. You would need to install the fglrx driver package. 

Try this first,  I had tearing in xbmc too. 

Nano this file

 /usr/share/lightdm/lightdm.conf.d/50-xserver-command.conf

Edit the xserver command line and add a - bs
 
xserver-command=X -bs -core

Let us know if that fixes it

---

### Post by KillEmAllx on 2014-05-14
I've solved the problem! (I think). I added the "-bs" line to the .conf file but it didn't work, so I tried the following instructions from this post: [http://ubuntuforums.org/showthread.php?t=2219091&page=2](http://ubuntuforums.org/showthread.php?t=2219091&page=2)
```
[COLOR=#000000]*sudo apt-add-repository ppa:timo-jyrinki/ppa*[/COLOR]
[COLOR=#000000]*sudo apt-get update*[/COLOR]
[COLOR=#000000]*sudo apt-get install libsdl1.2debian*[/COLOR]
```
And it worked! No more tearing, at least for now.
Thanks for the help. Marking this as solved!

---

