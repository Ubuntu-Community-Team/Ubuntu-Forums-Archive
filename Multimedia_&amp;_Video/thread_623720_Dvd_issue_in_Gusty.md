---
title: "Dvd issue in Gusty"
date: 2007-11-26
forum: Multimedia &amp; Video
---

### Post by jinxs1591 on 2007-11-26
I just install gusty on a presario 5000 and got all the needed codecs but for some reason I get this error from all player

totem
Totem cannot play this type of media (DVD) because it does not have the appropriate plugins to be able to read from the disc.
Please install the necessary plugins and restart Totem to be able to play this media.

Gxine wizard : some please explain what Im suppose to do here
FAILED - could not access dvdrom: /dev/dvd

Either create a symbolic link /dev/dvd pointing to your cdrom device or set your cdrom device in the preferences dialog.

FAILED - Could not read stats for /dev/dvd.

If you are using the ide-cd module ensure
that you have the following entry in /etc/modules.conf:
options ide-cd dma=1
Reload ide-cd module.
otherwise run hdparm -d 1 on your dvd-device

No input plugin was found.
Maybe the file does not exist or cannot be accessed, or there is an error in the URL.

when I run totem from the command line I get this
jinx@jinx-desktop:~$ totem
sh: jackd: not found
Gxine from the command line
jinx@jinx-desktop:~$ gxine
lirc: cannot initialise - disabling remote control
lirc: maybe lircd isn't running or you can't connect to the socket?
Fragment program only supported for YV12 data
Please remember I'm a noob that trying to move away from windows

---

### Post by human-ness on 2007-11-26
After I uninstalled KDE from my main machine, all types of evil visited the CPU and memory banks of my once innocent computer.  Including DVD access.  I went hunting for ages and followed every instruction about DVD playback until I was blue in the face.  Until I found a page that finally worked.

Check this one out and see if it helps you out with your problem.

[Click here.](http://phorolinux.com/five-tips-for-ubuntu-710-gutsy-gibbon.html)

Hope it helps.

---

