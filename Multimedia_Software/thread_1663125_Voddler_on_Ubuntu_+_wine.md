---
title: "Voddler on Ubuntu + wine"
date: 2011-01-09
forum: Multimedia Software
---

### Post by RikardSvenningsen on 2011-01-09
Hi
I have managed to install the Voddler on Ubuntu wine using Firefox.
I did it on Ubuntu 10.10, 32 bit.
Used this guide:
[http://ubuntuforums.org/showthread.php?t=1482388&highlight=voddler](http://ubuntuforums.org/showthread.php?t=1482388&highlight=voddler)
I have it running on Ubuntu 10.04.
On Ubuntu 10.10 32/64 bit I get this error:
7744 - 30 not a clue on what's wrong. The Voddler test goes fine.

---

### Post by d98jh on 2011-01-10
7744 is a DRM error because Adobe AIR detects that the installed version differs from the version number in the registry.
The only way I got it working was by starting with a clean wine installation (delete/rename .wine-folder)

---

### Post by RikardSvenningsen on 2011-01-10
Hi. d98jh
Are you using Ubuntu 10.10?
I have made the installation on 3 different computer now and if I use Ubuntu 10.04 32 Bit, it runs every time.
The last installation I did, was a clean 10.04 + wine, Firefox on Windows, Download the Voddler_installer.sh.
Run the installer script to time, change the registery as described previous, started the Voddler player watch a movie.
End of story...
It would bee nice if it would run on Ubuntu 10.10...

---

### Post by d98jh on 2011-01-11
Hi!

Yes, I'm running 10.10.

I used the guide in the comment from Dec 8th here: [http://geexercise.blogspot.com/2010/04/ubuddler.html](http://geexercise.blogspot.com/2010/04/ubuddler.html)

Haven't tried it since then though...

---

### Post by RikardSvenningsen on 2011-01-11
Hi
It's the same as I used to make a success full installation with Ububtu 10.04 and don't got to work on Ubuntu 10.10. 64 bit
But when the test is running everything checks out to be fine, but not movie..

---

### Post by d98jh on 2011-01-11
Ok, I thought you used the installer script. I just used the latest windows installer for Voddler, the latest firefox and Adobe AIR 2.5.1.deb and it worked. No registry changes needed.

---

