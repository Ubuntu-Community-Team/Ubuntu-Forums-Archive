---
title: "Winamp on Ubuntu"
date: 2008-09-13
forum: Multimedia Software
---

### Post by dave1991 on 2008-09-13
I was wondering if there is a media player for ubuntu that has the same features as winamp. Also I need the codecs to play MP3 files on ubuntu. I don't have an active internet connection on my ubuntu PC. Any help will be much appreciated.

---

### Post by TenPlus1 on 2008-09-13
Audacious is a WinAMP clone for Linux, although you would have to download the .deb file and it's dependancies so that it will install on your system without a .net connection...

---

### Post by Mhawkins1 on 2008-09-14
> **dave1991 said:**
> I was wondering if there is a media player for ubuntu that has the same features as winamp. Also I need the codecs to play MP3 files on ubuntu. I don't have an active internet connection on my ubuntu PC. Any help will be much appreciated.

You can download and use WinAmp itself if you use Wine or Wine-Doors

---

### Post by cherva on 2008-09-14
XMMS  is a nice clone too ```
sudo apt-get install xmms
``` But I advice you to try banshee. [http://banshee-project.org/ ]("http://banshee-project.org/") ```
sudo apt-get install banshee
```

---

### Post by markbuntu on 2008-09-14
If you need a total multimedia overhaul follow this guide:

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

If you just want the plugins and w32codecs and libdvdcss2 to play restricted formats follow this guide:

[http://ubuntutip.googlepages.com/multimediaubuntustep1](http://ubuntutip.googlepages.com/multimediaubuntustep1)
[http://ubuntutip.googlepages.com/multimediaubuntustep2](http://ubuntutip.googlepages.com/multimediaubuntustep2)

xmms is the closest thing to winamp but is not available from the regular repositories for Hardy (unless that has changed very recently) so you need to get the debs from launchpad:
i386:

[https://launchpad.net/ubuntu/hardy/i386/xmms/1:1.2.10+20070601-1build2](https://launchpad.net/ubuntu/hardy/i386/xmms/1:1.2.10+20070601-1build2)

amd64:

[https://launchpad.net/ubuntu/hardy/amd64/xmms/1:1.2.10+20070601-1build2](https://launchpad.net/ubuntu/hardy/amd64/xmms/1:1.2.10+20070601-1build2) 

Beware of dependency problems with libglib1.2 and libglib1.2dbl on the amd64 build, i386 is no problem. You can read about that here:

[http://ubuntuforums.org/showthread.php?t=774461](http://ubuntuforums.org/showthread.php?t=774461)

Change the output plugin to alsa and you should be good to go.

audacious is also a winamp clone.

---

### Post by uvdevnull on 2008-10-09
> **TenPlus1 said:**
> Audacious is a WinAMP clone for Linux, although you would have to download the .deb file and it's dependancies so that it will install on your system without a .net connection...

Audacious is NOT a clone of Winamp!  It doesn't even come close.  At least not if you use the Media Library which is where Winamp's power lies imho.  I haven't been able to find a linux player that matches the implementation of the near-perfect ML manager in Winamp and I've tried about a dozen different players.

---

### Post by uvdevnull on 2008-10-09
> **Mhawkins1 said:**
> You can download and use WinAmp itself if you use Wine or Wine-Doors

Unfortunately, Winamp through Wine doesn't support the Media Library, which is why I love Winamp so much and why I'm having such a hard time with finding a linux player that would match it.

---

### Post by uvdevnull on 2008-10-09
> **cherva said:**
> XMMS  is a nice clone too ```
sudo apt-get install xmms
``` But I advice you to try banshee. [http://banshee-project.org/ ]("http://banshee-project.org/") ```
sudo apt-get install banshee
```

Same as above, XMMS is NOT a clone of Winamp and neither that nor Banshee come even close to Winamp's powerful ML.

---

