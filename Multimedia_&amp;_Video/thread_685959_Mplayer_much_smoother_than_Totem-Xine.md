---
title: "Mplayer much smoother than Totem-Xine"
date: 2008-02-02
forum: Multimedia &amp; Video
---

### Post by sirzepp on 2008-02-02
I've got DVD's playing just fine on my system...at least from a reliability standpoint.  I've noticed that Totem-Xine is choppier than Mplayer.  However, I am annoyed by Mplayer's lack of support for DVD menus and it's randomness(track forward and you are suddenly listening to the commentary...or subtitles are turned on).  Totem-Xine is awesome for DVD compatibility, but it is noticeably choppy on my system.  I assume this is because of the difference in "backend" libraries(xine vs. gstreamer).  My problem is, I can't get Totem gstreamer to work with my setup.  And besides, isn't it actually the gstreamer setup that is incompatible with the DVD menus and extra features?  Is there a way to "smooth out" the playback on Totem-xine?

I've got an older system, but it seems like it should be up to the task:

Athlon 64 2800+
1.5 GB of RAM
Geforce 440MX 64 MB AGP card.
Pioneer 112 DVD burner/player.

---

### Post by ubuntu-freak on 2008-02-02
Use VLC for DVD's (best menu support, smooth playback). Follow Part 1 & 3 of my [how-to](http://ubuntuforums.org/showthread.php?t=661833) and you will be a very happy bunny.
 
Nathan

---

### Post by disturbedite on 2008-02-02
try smplayer, its an extremely nice mplayer frontend.

---

### Post by ubuntu-freak on 2008-02-02
> **disturbedite said:**
> try smplayer, its an extremely nice mplayer frontend.

 
A frontend won't improve menu support. VLC is best for DVD's anyway. I'm not the only one to think that.
 
Nathan

---

### Post by sirzepp on 2008-02-03
Hey Nathan,
  Thanks for the Howto.  I did all of that...and now I have a REALPLAYER!!  Cool.  Anyway, there is still some tearing of the bottom 1/3 of the video on both VLC and Totem-Xine.  This doesn't happen in Mplayer.  Is there a reason?  Is this something that can be fixed or do you think it's just the age of my computer?

:)

Jimmy

---

### Post by ubuntu-freak on 2008-02-03
Hmm. That's odd. The fact MPlayer is okay. When desktop effects are off totem and vlc play fine yeah (no tearing)? Is there a difference between windowed and fullscreen? Is it only with DVD's you see the tearing?
 
Nathan

---

### Post by disturbedite on 2008-02-03
> **reassuringlyoffensive said:**
> A frontend won't improve menu support. VLC is best for DVD's anyway. I'm not the only one to think that.
 
Nathan
i never said it would.  its simply the best mplayer frontend there is imo.  i know mplayer doesn't have menu support.  thats why i use kaffeine to play dvds with menus.

---

### Post by ubuntu-freak on 2008-02-03
> **disturbedite said:**
> i never said it would.  its simply the best mplayer frontend there is imo.  i know mplayer doesn't have menu support.  thats why i use kaffeine to play dvds with menus.

 
So you weren't trying to help with his issue. Strange.

---

### Post by sloggerkhan on 2008-02-03
It might be that they are using different video overlays.

Maybe one is using xv, another is using opengl, or something?

---

### Post by ubuntu-freak on 2008-02-03
> **sloggerkhan said:**
> It might be that they are using different video overlays.

Maybe one is using xv, another is using opengl, or something?

 
Yeah it's strange that MPlayer doesn't have the artifacts. Thing is, totem and vlc are xv by default, and so is MPlayer. Also, gl is inferior to xv. Odd. 
 
Nathan

---

### Post by disturbedite on 2008-02-04
> **reassuringlyoffensive said:**
> So you weren't trying to help with his issue. Strange.
no.  i was making a recommendation as to an mplayer frontend, duh.

---

### Post by ubuntu-freak on 2008-02-04
> **disturbedite said:**
> no.  i was making a recommendation as to an mplayer frontend, duh.

 
Don't 'duh' me. You're the one who answered a question nobody asked.
 
Nathan

---

### Post by andrew.46 on 2008-02-17
Hi,

Can I politely disagree about the menus:

> **disturbedite said:**
> i never said it would.  its simply the best mplayer frontend there is imo.  i know mplayer doesn't have menu support.  thats why i use kaffeine to play dvds with menus.

Mplayer *does* support menus in dvds, although it is still early days and as Nathan suggested vlc might be a better option. But for fanatical mplayer users (= me) a quick runthrough:

1. Download and install libdvdread and libdvdcss

2.Download the svn libdvdnav source:

```
$ svn co svn://svn.mplayerhq.hu/dvdnav/trunk/libdvdnav libdvdnav
```

and install it:

```
$ cd libdvdnav
$ ./autogen.sh
$ ./configure
$ make
$ make install
```

3. [Download and install the svn mplayer]("http://ubuntuforums.org/showthread.php?t=558538") and make sure to add the following option to configure:

```
$ ./configure --disable-dvdread-internal
```

along with whatever other options you wish to use.

4. Add the following to ~/.mplayer/config:

```
mouse-movements=yes
```

5. Use the following to see the movie:

```
$ mplayer dvdnav://
```

Not exactly straightforward I realise but is effective and under active development at the moment :-) Hopefully libdvdnav will be integrated into the svn mplayer tree soon and then some of the hassle will be gone.

             Andrew

---

