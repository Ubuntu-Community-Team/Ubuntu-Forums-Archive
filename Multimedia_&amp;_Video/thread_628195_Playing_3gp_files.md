---
title: "Playing 3gp files"
date: 2007-12-01
forum: Multimedia &amp; Video
---

### Post by acl123 on 2007-12-01
Hi,
I am trying to play 3gp files with sound but encountering many many problems with everything I try.

* First I tried converting it to an avi with mencoder -
> mencoder Video008.3gp -ovc lavc -lavcopts vcodec=msmpeg4v2 -oac mp3lame -lameopts vbr=3 -o Video008.avi
The quality of the picture is terrible though and there is no sound.

* Then I tried downloading Mobile Media Converter. I unzipped the package but when I run
> ./Mobile\ Media\ Converter  I just get a segmentation fault.

* I tried downloading RealPlayer10 but the link seems to be broken on the real player site.

* I tried to download Real Player again from [https://player.helixcommunity.org/2005/downloads/](https://player.helixcommunity.org/2005/downloads/). It ran through the installer fine but I couldn't work out how to run it once it was installed. I tried running realplay.bin but got a segmentation fault.

Does anyone have any ideas?

---

### Post by stooshbunutu on 2008-03-11
just use VLC Player

---

