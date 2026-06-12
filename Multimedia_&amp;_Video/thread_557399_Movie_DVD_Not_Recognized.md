---
title: "Movie DVD Not Recognized"
date: 2007-09-22
forum: Multimedia &amp; Video
---

### Post by Baufo on 2007-09-22
I tried to play a movie DVD ("The Simpsons"). Well, it did not work. First t I thought the DVD might be broken but when I tried to play it in Windows, again with VLC, it worked just fine.

Here is the console output of VLC attempting to run the DVD:

```
thomas@thomas-laptop:~$ vlc /media/cdrom0
VLC media player 0.8.6 Janus
libdvdnav: Using dvdnav version 0.1.10 from http://dvd.sf.net
libdvdread: Encrypted DVD support unavailable.
libdvdread: Attempting to use device /dev/scd0 mounted on /media/cdrom0 for CSS authentication
libdvdnav: Can't read name block. Probably not a DVD-ROM device.
libdvdnav: Unable to find map file '/home/thomas/.dvdnav/.map'
libdvdread: Invalid main menu IFO (VIDEO_TS.IFO).
libdvdnav: vm: faild to read VIDEO_TS.IFO

```

---

### Post by Crenfinkle on 2007-09-22
Search google for "how to add the medibuntu repository in ubuntu" or something like that. Once you have added the medibuntu repository to your apt sources, search for "libdvdcss2." Install that and you should have commercial (encrypted) dvd support.

Another option is to search for an rpm package for intervideo's LinDVD. Convert this to a .deb package using alien, and install as normal. It works great, and offers a (sorry folks) Windows-like DVD experience. Most of the time I don't support this type of solution, but I think it is far superior to the libdvdcss/* combination.

---

### Post by Gremlinzzz on 2007-09-22
smplayer plays all my DVDs
[http://wesley.debianbox.be/packages/](http://wesley.debianbox.be/packages/)

---

