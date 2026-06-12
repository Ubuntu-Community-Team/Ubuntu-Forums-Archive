---
title: "Unable to install codecs - broken source"
date: 2008-04-18
forum: Multimedia &amp; Video
---

### Post by Stason on 2008-04-18
In Gutsy:


```

sudo wget http://www.medibuntu.org/sources.list.d/gutsy.list -O /etc/apt/sources.list.d/medibuntu.list

wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```

Second line hangs the terminal, when trying to install those w32 codec pack, it says something like there is no source. 

All this hassle to make mplayer to play WMV files. So far no luck. Manual codec install also no good, since instructions refer to /codecs directory, which is not present in my system. Something definitely wrong here. Any help would be appreciated.

---

### Post by Kevbert on 2008-04-18
Try installing codecs via Quickstart.  See [http://ubuntuforums.org/showthread.php?t=613462&highlight=quickstart]("http://ubuntuforums.org/showthread.php?t=613462&highlight=quickstart")

---

### Post by Stason on 2008-04-18
Surely Quickstart does same thing I fail to do manually. For some reasons, when checking repositories it gives me an error for the archive.ubuntu.com link as well, which is added through the first line of the script. Weird.

---

### Post by Kevbert on 2008-04-18
Try this link:[http://www.mplayerhq.hu/MPlayer/releases/codecs/]("http://www.mplayerhq.hu/MPlayer/releases/codecs/")
There seems to be a win32 codec tar file.

---

### Post by mc4man on 2008-04-18
> Manual codec install also no good, since instructions refer to /codecs directory
you could create that dir. , the default that mplayer looks for is /usr/share/mplayer/codecs - that's where I put the essential codecs - though I'm using self built ver. not repo.
If you can't square up sources you can always get w32codecs deb from here
[http://debian-multimedia.org/pool/main/w/w32codecs/](http://debian-multimedia.org/pool/main/w/w32codecs/)

---

