---
title: "HD Tracks in Ubuntu 12.04.4 LTS AMD64"
date: 2014-05-10
forum: Multimedia Software
---

### Post by frogotronic on 2014-05-10
Hello,

   Using the latest WINE HQ (Beta) on Ubuntu 12.04.4 LTS AMD 64 (all 32 bit libraries installed).  Downloaded the HD Tracks downloader (ver 19.06) and installed into my WINE directory.  Downloaded and installed crypt32.dll via winetricks. 

  Problem:  Cannot login to HD Tracks from the HD Tracks Downloader.  

  Any Suggestions?

Thanks,
CH

---

### Post by ronalde@launchpad.net on 2014-08-30
I've used the jriver hdtracks downloader for windows for a while using a hack I described in [http://lacocina.nl/hdtracks-downloader-on-linux](http://lacocina.nl/hdtracks-downloader-on-linux). I don't know what change (in wine or the hdtracks downloader) caused it to stop working. 

I've even made a script to try older and newer versions than the one published by hdtracks ([https://github.com/ronalde/hdtracks-downloader](https://github.com/ronalde/hdtracks-downloader)), but that doesn't help either.

Please contact hdtracks to share our concerns. I've already done that a few times in the past, but they don't seem to care enough. In the mean time, I've remove Linux from the supported platforms on their Wikipedia page ([https://en.wikipedia.org/wiki/HDtracks](https://en.wikipedia.org/wiki/HDtracks)) and added the following entry to its timeline:
[COLOR=#252525][FONT=sans-serif]
"On January 23, 2013, HDtracks replaced it's multiplatform Java Network Launching Protocol (JNLP) downloader application to native applications for Windows and Mac created by [/FONT][/COLOR][JRiver]("https://en.wikipedia.org/w/index.php?title=JRiver&action=edit&redlink=1")[COLOR=#252525][FONT=sans-serif], thereby making it impossible for users of other platforms like Linux to download their purchases."[/FONT][/COLOR]

Regards,
Ronald

---

