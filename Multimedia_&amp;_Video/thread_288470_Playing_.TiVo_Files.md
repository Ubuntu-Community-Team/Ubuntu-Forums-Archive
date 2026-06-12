---
title: "Playing .TiVo Files"
date: 2006-10-29
forum: Multimedia &amp; Video
---

### Post by zavius on 2006-10-29
Any one know what I can use to play the .TiVo files I download from my TiVo? They won't seem to play properly in mplayer and I don't want to modify my Tivo at all. 

Any help would be greatly appreciated

---

### Post by bmillsap on 2006-10-29
I'm not sure on Ubuntu.  On Windows, Direct Show Dump can use Direct Show to dump the .tivo file out to an unprotected .mpg file, but I don't know if there's a similar utility for linux.  I haven't looked into doing that on linux since my wife's laptop (she's the viewer of .tivo files) runs WinXP.

---

### Post by davebgimp on 2006-12-04
> **bmillsap said:**
> I'm not sure on Ubuntu.  On Windows, Direct Show Dump can use Direct Show to dump the .tivo file out to an unprotected .mpg file, but I don't know if there's a similar utility for linux.  I haven't looked into doing that on linux since my wife's laptop (she's the viewer of .tivo files) runs WinXP.

I'm trying to install DSD with Wine, but without any luck. Is anyone converting the files on Ubuntu?

---

### Post by artships on 2006-12-04
> **davebgimp said:**
> I'm trying to install DSD with Wine

Try the [TiVo File Decoder]("http://tivodecode.sourceforge.net/").  Where Direct Show needs the tivo dll installed, this is a C program that just does it all, judging by the documentation.  No need for Wine at all.

---

### Post by SonicJMC on 2007-12-28
> **artships said:**
> Try the [TiVo File Decoder]("http://tivodecode.sourceforge.net/").  Where Direct Show needs the tivo dll installed, this is a C program that just does it all, judging by the documentation.  No need for Wine at all.

Can't get it to
./configure
make
make install

It fails. I don't know linux enough to get any further!

---

### Post by mb125 on 2008-01-09
Anyone get this working yet???
I downloaded and ran it but with no luck
are there any details on how to install properly?

---

### Post by solarlore on 2008-01-15
I was searching to see if its worth getting a tivo (don't have one so i can't say i've gotten it working) and found this blog.

[http://apt-get.biffster.org/2007/03/18/play-tivotogo-files-in-linux/](http://apt-get.biffster.org/2007/03/18/play-tivotogo-files-in-linux/)

Looks really promising!

---

### Post by blh1983 on 2008-04-10
Did anyone help you yet??  I'm really trying to like linux ubuntu, but it certainly isn't user friendly compared to (and I'm sure this a bad word here) Microsoft.  I'm hoping that some nice people on here will make a self installing deb file from the source code for Tivo MPlayer.  I'm having the same problem trying to get configure to do anything.  Someone please help!!!
> **mb125 said:**
> Anyone get this working yet???
I downloaded and ran it but with no luck
are there any details on how to install properly?

---

