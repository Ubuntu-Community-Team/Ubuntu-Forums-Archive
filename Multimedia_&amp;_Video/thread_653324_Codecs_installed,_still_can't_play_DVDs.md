---
title: "Codecs installed, still can't play DVDs"
date: 2007-12-29
forum: Multimedia &amp; Video
---

### Post by chocolatetoothpaste on 2007-12-29
Hey gang,
  I have install all the necessary codecs, etc to play dvds, but when I try to play a dvd, I get a few errors.  The console in the background says: 
```

libdvdnav: Using dvdnav version 0.1.10 from http://vd.sf.net
libdvdread: Using libdvdcss version 1.2.9 fro DVD access
libdvdread: Can't stat
No such file or directory
libdvdnav: vm: failed to open/read the DVD
[00000292] dvdread demuxer error: DVDRead cannot open source:
ioctl(): Input/output error
[00000295] vcdx access error: error reading Info sector (150)
[00000290] main input error: no suitable access module for `dvd://'
[00000281] main playlist: nothing to play

```
Then, the error list for vlc opens and says: 
Unable to open 'dvd://'

Has anyone any idea what the issue could be?  I don't think it's my dvd drive, however, I won't rule it out completely.  Is there any diagnostic tool I could use to check my dvd drive, as a last resort?

Any suggestions would be appreciated.  I'm just a few steps away from being satisfied with ubuntu as a sole OS, I'd really hate to turn back now.  Thanks in advance.

---

### Post by disturbed1 on 2007-12-29
Looks like the symlink DVD:// isn't pointing to your DVD-ROM. I've seen this happen in my systems that have more than one optical drive.

Try pointing VLC the direct device (/dev/whatever)


Love Lucky Number Slevin BTW :D

---

### Post by chocolatetoothpaste on 2007-12-30
> **disturbed1 said:**
> Looks like the symlink DVD:// isn't pointing to your DVD-ROM. I've seen this happen in my systems that have more than one optical drive.

Try pointing VLC the direct device (/dev/whatever)


Love Lucky Number Slevin BTW :D

Thanks loads!  Is there a way I can create some symlink that will let VLC find the device automatically?  I only ask because I imagine other programs may have a similar hang up.
  Well, I got DVD's to read, but for some reason, they won't unscramble.  I have installed libdvdcss 2 methods, the medibuntu repos and also the script that is with the libdvdread.  Do I need to link VLC to this somehow, as it seems VLC can't find it?

---

### Post by disturbed1 on 2007-12-30
*ln -s /dev/scd0 /dev/dvd*
The above will create a symlink between /dev/scd0 and /dev/dvd. Any program that look to /dev/dvd will be pointed to /dev/scd0. So replace /dev/scd0 with what ever you DVD-ROM actually is.

libdvdcss only removes css protection. Some/many newer discs have different types of encryption (Sony's ARCOS, RIPGAURD and so on). This could be the issue, or something else. Easy way to test is to try an old DVD (3-5 years?). If the content is still scrambled, perhaps your installation of libdvdcss is corrupt. I personally don't have an issue with libdvdcss and CSS encrypted discs, however I use this version/package [http://www.videolan.org/developers/libdvdcss.html](http://www.videolan.org/developers/libdvdcss.html) <- You can drill through to the .deb packages or the source tarball and build yourself.

The only solution I've found to playing newer types of encryption is to run the free DVDFabDecrypter ([link](http://www.dvdfab.com/free.htm) <- NOT DVDFREE)  through wine, and decrypt the disc to the hard drive :(

---

### Post by chocolatetoothpaste on 2007-12-30
> **disturbed1 said:**
> *ln -s /dev/scd0 /dev/dvd*
The above will create a symlink between /dev/scd0 and /dev/dvd. Any program that look to /dev/dvd will be pointed to /dev/scd0. So replace /dev/scd0 with what ever you DVD-ROM actually is.

libdvdcss only removes css protection. Some/many newer discs have different types of encryption (Sony's ARCOS, RIPGAURD and so on). This could be the issue, or something else. Easy way to test is to try an old DVD (3-5 years?). If the content is still scrambled, perhaps your installation of libdvdcss is corrupt. I personally don't have an issue with libdvdcss and CSS encrypted discs, however I use this version/package [http://www.videolan.org/developers/libdvdcss.html](http://www.videolan.org/developers/libdvdcss.html) <- You can drill through to the .deb packages or the source tarball and build yourself.

The only solution I've found to playing newer types of encryption is to run the free DVDFabDecrypter ([link]("http://www.dvdfab.com/free.htm") <- NOT DVDFREE)  through wine, and decrypt the disc to the hard drive :(
Tried creating the symlink.  It was created successfully, yet I still had to type in the device in VLC.  Not a big deal though, I can deal with that.
  I downloaded libdvdcss from the videolan website, installed it, and I still have a scrambled dvd.  I used one from 2001.  This situation is just insane because not all that long ago, I had a successful dvd playing experience with all dvds.  If  I remember right, it may have been with 7.04.  I just might have to down grade for the time being.  Seems like gutsy has been met with it's fair share of issues.  Unless anyone has some other ideas for decrypting dvds...?  
Thanks a load anyway!

---

### Post by disturbed1 on 2007-12-30
Can you post a screen shot of what the scramble looks like? 

Also try changing the Video Output options in VLC (Xv, X11, OpenGL) some programs will kill Xv overlay and not release for another program to use.

I've attached 2 screen shots. One of what Xv Overlay corruption looks like, and another where to change the settings (put a check in the advanced-options box ;) ) My Xv is corrupted because of 2 Xephyr sessions, 1 VNC session, and 1 RDP session. *I'm pretty one or a combination of those is causing it?* Without the remote sessions, my Xv is not corrupted.

---

### Post by hhhhhx on 2007-12-30
get automatix and then install ubuntu restricted extras, that did it for me:)

---

### Post by chocolatetoothpaste on 2007-12-30
Interestingly enough, I installed mplayer (to see if it was a problem with VLC), and I get the same results when trying to play a .mpg file.  I tried playing a .mpg in VLC, and all I get is vertical lines, no clear picture.  I'm going to guess it is an issue with X,  but I honestly haven't got a clue.  I am somewhat unable to post a screen shot at the moment.  I'm building an openbox system from scratch (command-line up), and I am making sure I can get video playback before I do much else.  I've been fighting with this laptop for about 6 months, trying to get some kind of use out of it.  XP and Vista had their shot and blew it, and I've given Ubuntu a lot more effort than both combined.  I'm ready to give up and buy a Mac.  Call me crazy...  I'll see if I can find a program to take a screen shot with though.

Here is a shot of the player window playing the movie (menu)

---

### Post by Sef on 2007-12-30
> get automatix and then install ubuntu restricted extras, that did it for me

Automatix is [not recommended]("http://mjg59.livejournal.com/77440.html").  It has messed up a number of systems.

---

### Post by chocolatetoothpaste on 2007-12-30
Well, I was finally able to see the movie, however playback is really choppy.  I am going to downgrade to 7.04, since these problems were non-existent.  Crossing my fingers that 8.04 will be a lot better.  Thanks to all who helped.  I sure hope Ubuntu continues to evolve and become a serious contender with windows.  Many users would have given up when faced with the issues I have.  A small price to pay, if you ask me.  I love not worring about viruses and spyware.  Thanks!

PS: I never use automatix.  I prefer to do stuff manually, in hopes that one day I'll understand more of what goes on under the hood with linux.

---

