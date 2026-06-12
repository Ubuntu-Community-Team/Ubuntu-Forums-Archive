---
title: "VA Api Problem"
date: 2010-06-30
forum: Multimedia Software
---

### Post by Musturd on 2010-06-30
I am trying to get mplayer-vaapi working on my system, so I can watch 1080p videos with hardware acceleration (and to remove the tear effect).

Anyway I am having trouble getting VA Api to work correctly. I have extensively google-ed around, and I cannot find a way to fix this problem.

Here is the output for vainfo (the error from vainfo is the same as mplayer-vaapi):
```
libva: libva version 0.31.1-sds1
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
libva: va_getDriverName() returns 0
libva: Trying to open /usr/lib/va/drivers/fglrx_drv_video.so
libva error: dlopen of /usr/lib/va/drivers/fglrx_drv_video.so failed: libva-0.31.0.5.so.1: cannot open shared object file: No such file or directory
libva: va_openDriver() returns -1
vaInitialize failed with error code -1 (unknown libva error),exit

```

Please correct me if I am wrong, but I have found that:
1. The Xlib error shouldn't matter
2. I do have an fglrx_drv_video.so file in /usr/lib/va/drivers
3. I have installed the latest libva amd64 deb package
4. I have installed the latest xvba amd64 deb package

I am running Lucid on 2.6.34-020634-generic kernel (with a patched fglrx module). I have an ATI Mobility Radeon HD 5800 Series card.
Please tell me if I need to share any more information.

Also before I found the deb package for libva I followed this tutorial to compile it (some things had to be tweaked for it to compile successfully) ( [http://www.drupal4hu.com/node/244](http://www.drupal4hu.com/node/244) ). But I did reinstall libva when I found the .deb package.

Please help me, I am very confused. :confused:

---

### Post by csaratchand on 2010-07-04
Since you already have fglrx and xvba installed:
1. Add this PPA to your list of sources: [https://launchpad.net/~falk-t-j/+archive/lucid](https://launchpad.net/~falk-t-j/+archive/lucid). 
2. And install the mplayer-vaapi package. Other dependencies will also get installed. Package available only for amd64!
3. This mpalyer executable, unfortunately called mplayer and not mplayer-vaapi is located at /opt/mplayer-vaapi/bin.
4. If you are using SMplayer, you can choose this mplayer executable and apply.
5. Restart SMplayer and you should be able to start using mplayer-vaapi. 
6. If you don't want to add the entire PPA then download the deb packages along with dependencies and install them.

---

### Post by Musturd on 2010-07-05
> **csaratchand said:**
> Since you already have fglrx and xvba installed:
1. Add this PPA to your list of sources: [https://launchpad.net/~falk-t-j/+archive/lucid](https://launchpad.net/~falk-t-j/+archive/lucid). 
2. And install the mplayer-vaapi package. Other dependencies will also get installed. Package available only for amd64!
3. This mpalyer executable, unfortunately called mplayer and not mplayer-vaapi is located at /opt/mplayer-vaapi/bin.
4. If you are using SMplayer, you can choose this mplayer executable and apply.
5. Restart SMplayer and you should be able to start using mplayer-vaapi. 
6. If you don't want to add the entire PPA then download the deb packages along with dependencies and install them.

Thank you.
It installed successfully, but the mplayer binary in /opt/mplayer-vaapi/bin/ doesn't recognize the -va option. I thought that in order to get video acceleration I would have to do something like ./mplayer -vo vaapi -va vaapi movie.avi . Is there some other syntax? (`man ./mplayer` shows what looks like corrupted text)

---

### Post by Musturd on 2010-07-06
OK so apparently recently the Lucid Repos have been updated and now have the libva1 package. So I tried installing libva1 from there (after removing xvba-video and libva1-dev)
I then reinstalled the latest xvba-video and libva1-dev.

vainfo no longer exists.
`/usr/lib/ | grep libva` is missing a bunch of .so files. (and mplayer-vaapi complained (I'm using my install that understands the -va option))
I found these shared object files in another folder (probably from the source install I tried to do), so I copied them all into my /usr/lib folder.
Then following this example (post: #1507 [http://bbs.archlinux.org/viewtopic.php?pid=729735](http://bbs.archlinux.org/viewtopic.php?pid=729735) ) I created symlinks to the old .so files mplayer-vaapi wanted with the new ones.

Now I get the following error message
```
libva: libva version 0.31.1-sds1
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
libva: va_getDriverName() returns 0
libva: Trying to open /usr/lib/va/drivers/fglrx_drv_video.so
libva error: /usr/lib/va/drivers/fglrx_drv_video.so has no function __vaDriverInit_0_31
libva: va_openDriver() returns -1
[vo_vaapi] vaInitialize(): unknown libva error
Error opening/initializing the selected video_out (-vo) device.

```

So basically, I still need help.
Thanks.

---

