---
title: "Mplayer svn compile errors"
date: 2008-10-05
forum: Multimedia Software
---

### Post by bobbob1016 on 2008-10-05
I'm having problems compiling mplayer from svn.  I managed to do it earlier today, but then I realized since I didn't include --enable-x264 in my ./configure, mencoder couldn't use it.  So I redownloaded svn, with 
"svn checkout svn://svn.mplayerhq.hu/mplayer/trunk mplayer"
and my ./configure was
"./configure --enable-gui --enable-xvid --enable-x264 --disable-dvdread-internal"
I've played with the options a lot, trying different things, such as --prefix=/usr and things.  I also have to apply this patch to make sure I can use xv with ati, otherwise I can't resize the video window.
[http://www.fileden.com/files/2007/12/10/1637237/mplayrepatch.patch](http://www.fileden.com/files/2007/12/10/1637237/mplayrepatch.patch)
Which I wget into mplayer/libvo/ then run 
"patch -p0 vo_xv.c mplayrepatch.patch"
I've tried with and without this, and still get an error compiling.
Lastly, here is the entire compile on pastebin (as much as I can get)
[http://pastebin.ca/1220039](http://pastebin.ca/1220039)

I'd appreciate any help, thanks in advance.

Edit:  I did try compiling with these directions, and no luck. [http://ubuntuforums.org/showthread.php?t=558538&highlight=mplayer+svn](http://ubuntuforums.org/showthread.php?t=558538&highlight=mplayer+svn)
These are the directions that worked for me once, but they don't work with --enable-x264.  And then it can't play some videos I have, it just says "Failed to open /path/to/file"

Edit Edit:  When I did the directions above, I managed to get it to compile, turns out I didn't need --enable-x264, it detected it anyways.  But I can't get mplayer to play a video if I right click the file, and click other than mplayer, but it does play when I launch it via terminal, so I'm not sure how to get the error output from a gui launched program.

---

### Post by andrew.46 on 2008-10-30
Hi bob,

You have a few options that are best dropped:

```
--enable-xvid --enable-x264
```

as you have found can and in fact *should* be omitted. The other option has left me a little puzzled:

```
--disable-dvdread-internal
```

This is normally done in the svn MPlayer if you wish to use the MPlayer fork of libdvdread and libdvdnav. If this is not the case you might be better to omit this option as well. If this option is omitted you will still be able to watch DVDs but you will have no access to the initial menus.

I note your pastebin shows a compile failure related to x264. Ensure that you have the current git x264 when you compile rather that the Ubuntu libx264-dev, directions are on the [MPlayer guide]("http://ubuntuforums.org/showthread.php?t=558538") you referred to.

I am not familiar with the patch for ATI that you refer to but I would definitely try and compile without this patch to start with.

Hopefully a few of these things will get you back on the road?

  Andrew

---

