---
title: "HD Video issue."
date: 2007-04-22
forum: Multimedia &amp; Video
---

### Post by BriGaid on 2007-04-22
Does anyone know why smaller sized videos play in VLC and MPlayer but any video that is an HD resolution like 1280x720p, will just close the program.  I just installed feisty and have all of the video codecs installed.

---

### Post by BriGaid on 2007-04-22
it seems like it just can't handle the large videos and it doesn't even give me time to resize them smaller.

---

### Post by superm1 on 2007-04-22
I would launch a player from the command line and see what it is spitting back at the terminal regarding this.

---

### Post by BriGaid on 2007-04-22
Could you tell me how I would go about doing that? thanks

---

### Post by superm1 on 2007-04-23
Click accessories and choose terminal.  Launch vlc or mplayer like this:

vlc /home/supermario/Desktop/movie.avi

where /home/supermario/Desktop is the path to the movie, and movie.avi is the name of the movie.

---

### Post by BriGaid on 2007-04-23
thanks, this is what i got out of it.
```

brian@brian-ubuntu-desktop:~$ vlc /home/brian/Desktop/Dirt HD Trailer.wmv
VLC media player 0.8.6 Janus
libdvdnav: Using dvdnav version 0.1.10 from http://dvd.sf.net
libdvdread: Encrypted DVD support unavailable.
libdvdread: Can't stat /home/brian/Desktop/Dirt
No such file or directory
libdvdnav: vm: faild to open/read the DVD
[00000290] main input error: no suitable access module for `/home/brian/Desktop/Dirt'
libdvdnav: Using dvdnav version 0.1.10 from http://dvd.sf.net
libdvdread: Encrypted DVD support unavailable.
libdvdread: Can't stat HD
No such file or directory
libdvdnav: vm: faild to open/read the DVD
[00000304] main input error: no suitable access module for `HD'
libdvdnav: Using dvdnav version 0.1.10 from http://dvd.sf.net
libdvdread: Encrypted DVD support unavailable.
libdvdread: Can't stat Trailer.wmv
No such file or directory
libdvdnav: vm: faild to open/read the DVD
[00000308] main input error: no suitable access module for `Trailer.wmv'
[00000281] main playlist: nothing to play
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  141 (XVideo)
  Minor opcode of failed request:  19 ()
  Serial number of failed request:  82
  Current serial number in output stream:  83

```

i guess the comp just isn't powerful enough.  they do play in xp though albeit a little shaky.

---

### Post by superm1 on 2007-04-23
> **BriGaid said:**
> thanks, this is what i got out of it.
```

brian@brian-ubuntu-desktop:~$ vlc /home/brian/Desktop/Dirt HD Trailer.wmv
VLC media player 0.8.6 Janus
libdvdnav: Using dvdnav version 0.1.10 from http://dvd.sf.net
libdvdread: Encrypted DVD support unavailable.
libdvdread: Can't stat /home/brian/Desktop/Dirt
No such file or directory
libdvdnav: vm: faild to open/read the DVD
[00000290] main input error: no suitable access module for `/home/brian/Desktop/Dirt'
libdvdnav: Using dvdnav version 0.1.10 from http://dvd.sf.net
libdvdread: Encrypted DVD support unavailable.
libdvdread: Can't stat HD
No such file or directory
libdvdnav: vm: faild to open/read the DVD
[00000304] main input error: no suitable access module for `HD'
libdvdnav: Using dvdnav version 0.1.10 from http://dvd.sf.net
libdvdread: Encrypted DVD support unavailable.
libdvdread: Can't stat Trailer.wmv
No such file or directory
libdvdnav: vm: faild to open/read the DVD
[00000308] main input error: no suitable access module for `Trailer.wmv'
[00000281] main playlist: nothing to play
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  141 (XVideo)
  Minor opcode of failed request:  19 ()
  Serial number of failed request:  82
  Current serial number in output stream:  83

```i guess the comp just isn't powerful enough.  they do play in xp though albeit a little shaky.
Well, Actually you have an error with the way you are launching this file.
It should be like this:
```
 brian@brian-ubuntu-desktop:~$ vlc /home/brian/Desktop/Dirt\ HD\ Trailer.wmv
```

Notice the two '\'s.  Spaces need to be escaped from when using a command line.

---

### Post by BriGaid on 2007-04-23
It works now! thanks for the help and speedy replies.

---

