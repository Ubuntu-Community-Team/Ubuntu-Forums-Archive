---
title: "VLC slow load from file manager"
date: 2014-12-17
forum: Multimedia Software
---

### Post by dangillmor on 2014-12-17
Ubuntu 14.10 (64-bit), VLC 2.2.0-rc1 Weatherwax:

The first time I launch a video from the file manager all is well. But when I close it and launch another, there's a long delay before the new file launches -- 15-20 seconds or so.

Another user posted a video of this behavior: [https://www.youtube.com/watch?v=OKYPb7sKzIo](https://www.youtube.com/watch?v=OKYPb7sKzIo)

However, if VLC is open and I select another file from the application's menu, it opens immediately.

I ran it from the command line and got this repeated error message (though it didn't seem to interfere with the video):

Failed to open VDPAU backend libvdpau_i965.so: cannot open shared object file: No such file or directory

---

### Post by quillerszasza on 2014-12-18
Same thing here. I figured out that if I create a totally irrelevant, empty testfile, and try to delete it after I closed a video in VLC, than nautilus greys out for about 20 seconds before actually deleting the file. This happens with all GTK based file managers under Unity. Deleting from the command line works perfectly.
Totem player seems to not cause this issue, probably a library causes this weird stall.

---

### Post by monkeybrain20122 on 2014-12-18
vlc-2.2.0-rc2 works fine here.

---

### Post by monkeybrain20122 on 2014-12-18
> **dangillmor said:**
> 
Failed to open VDPAU backend libvdpau_i965.so: cannot open shared object file: No such file or directory

Looks like vlc is somehow configured to use vdpau but it is not supported by your grapic driver. Turn of vdpau in vlc from Tools > Preferences > Input/Codecs > hardware acceleration decoding and Tools > Preferences > Video > Output

What is your graphic card? It is kind of weird error as i965 is intel and uses vaapi for hardware decoding rather than vdpau.

---

### Post by dangillmor on 2014-12-18
$ lspci | grep VGA

VGA compatible controller: Intel Corporation Haswell-ULT Integrated Graphics Controller (rev 09)

How can I get it to use vaapi instead of vdpau? Is there a way to uninstall vdpau?

Thanks for your help!

---

### Post by monkeybrain20122 on 2014-12-18
In  Tools > Preferences > Input/Codecs > hardware acceleration decoding and Tools > Preferences > Video > Output both choose automatic should use vaapi if you have i965-va-driver installed

---

### Post by dangillmor on 2014-12-18
It does appear to be doing that, but is still looking for VDPAU. The super-slow load time has not changed. 

Terminal output:

$ vlc
VLC media player 2.2.0-rc1 Weatherwax (revision 2.2.0~pre2+git20141011+r57575+24+12~ubuntu14.10.1)
[0000000001f18118] core libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
libva info: VA-API version 0.35.1
libva info: va_getDriverName() returns 0
libva info: Trying to open /usr/lib/x86_64-linux-gnu/dri/i965_drv_video.so
libva info: Found init function __vaDriverInit_0_35
libva info: va_openDriver() returns 0
[00007f0ddf70e578] avcodec decoder: Using Intel i965 driver for Intel(R) Haswell Mobile - 1.3.2 for hardware decoding.
Failed to open VDPAU backend libvdpau_i965.so: cannot open shared object file: No such file or directory
libva info: VA-API version 0.35.1
libva info: va_getDriverName() returns 0
libva info: Trying to open /usr/lib/x86_64-linux-gnu/dri/i965_drv_video.so
libva info: Found init function __vaDriverInit_0_35
libva info: va_openDriver() returns 0
[00007f0ddf70e578] avcodec decoder: Using Intel i965 driver for Intel(R) Haswell Mobile - 1.3.2 for hardware decoding.
libva info: VA-API version 0.35.1
libva info: va_getDriverName() returns 0
libva info: Trying to open /usr/lib/x86_64-linux-gnu/dri/i965_drv_video.so
libva info: Found init function __vaDriverInit_0_35
libva info: va_openDriver() returns 0
[00007f0ddf70e578] avcodec decoder: Using Intel i965 driver for Intel(R) Haswell Mobile - 1.3.2 for hardware decoding.
libva info: VA-API version 0.35.1
libva info: va_getDriverName() returns 0
libva info: Trying to open /usr/lib/x86_64-linux-gnu/dri/i965_drv_video.so
libva info: Found init function __vaDriverInit_0_35
libva info: va_openDriver() returns 0
[00007f0ddf70e578] avcodec decoder: Using Intel i965 driver for Intel(R) Haswell Mobile - 1.3.2 for hardware decoding.
libva info: VA-API version 0.35.1
libva info: va_getDriverName() returns 0
libva info: Trying to open /usr/lib/x86_64-linux-gnu/dri/i965_drv_video.so
libva info: Found init function __vaDriverInit_0_35
libva info: va_openDriver() returns 0
[00007f0da9008398] avcodec decoder: Using Intel i965 driver for Intel(R) Haswell Mobile - 1.3.2 for hardware decoding.
dan@dan-T440s:~$ vlc
VLC media player 2.2.0-rc1 Weatherwax (revision 2.2.0~pre2+git20141011+r57575+24+12~ubuntu14.10.1)
[0000000001463118] core libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
Failed to open VDPAU backend libvdpau_i965.so: cannot open shared object file: No such file or directory
Failed to open VDPAU backend libvdpau_i965.so: cannot open shared object file: No such file or directory

---

### Post by monkeybrain20122 on 2014-12-18
Hmm.. Instead of using 'automatic' maybe just choose vaapi explicitly in Tools > Preferences > Input/Codecs > hardware acceleration decoding (both x11 and DRM should work) and choose xvideo in Tools > Preferences > Video > Output

I think the slow load time of the second video maybe due to vlc not quite quitting the first one when you stop it. Try disable hd acceleration if the above doesn't fix it (or you can try update your graphic driver with a ppa)

---

### Post by dangillmor on 2014-12-18
Done (changed settings).

Re load time, VLC is still running in system monitor after I close the window. If I kill the process, I can immediately start a new file. What I can't figure out is why is hangs on for so long. This isn't happening to everyone, apparently, but for some of us it's pretty annoying. The workaround -- not closing the window and doubleclicking on a different file in the file manager -- is fine for now, however.

---

### Post by monkeybrain20122 on 2014-12-18
Maybe try updating vlc to 2.2.0-rc2 if you don't mind compiling it.

The latest nightly tarball for 2.2.0 [http://nightlies.videolan.org/build/source/?C=M;O=D](http://nightlies.videolan.org/build/source/?C=M;O=D)

---

### Post by mc4man on 2014-12-18
> **dangillmor said:**
> Done (changed settings).

Re load time, VLC is still running in system monitor after I close the window. If I kill the process, I can immediately start a new file. What I can't figure out is why is hangs on for so long. This isn't happening to everyone, apparently, but for some of us it's pretty annoying. The workaround -- not closing the window and doubleclicking on a different file in the file manager -- is fine for now, however.
If inclined test in 15.04, if still an issue file a bug. If not then you'll be using 15.04 at some point anyway.
(- non security related bugs in 14.10 are not likely to be addressed in any meaningful manner

---

### Post by monkeybrain20122 on 2014-12-18
I think your problem may be solved by disabling hardware acceleration in Tools > Preferences > Input/Codecs > hardware acceleration decoding. Trade off is high cpu for hd videos.

Seems to be a recurring problem with vlc and vaapi. They blame it on intel drivers. I have updated my driver massively and now it happens much less (14.04). mpv works a lot better on this intel machine (but vdpau works beautifully with vlc 2.2.0 on amd machines and open drivers)

---

### Post by quillerszasza on 2014-12-18
I can reproduce this error without VLC: same effect whan I see a video on Youtube (html5), close tab, then try to delete a random testfile. Nautilus greys out for like 20 seconds.

---

### Post by dangillmor on 2014-12-18
Will give it a try...

---

### Post by carrington2 on 2014-12-19
My vlc had also same problem. I did checking another setting option. After sometime i see it's automatically solved.. !! thanks

---

### Post by Ko_Char on 2014-12-19
"VLC media player 2.2.0-pre2 Weatherwax" works fine on 14.10 - 64 bit
And I have the same error, "Failed to open VDPAU backend libvdpau_i965.so: cannot open shared object file: No such file or directory".
So I think libvdpau_i965.so is not the real problem. 
How do you install vlc?

---

### Post by quillerszasza on 2014-12-19
From official repository, also 64 bit, 14.10 here.

---

### Post by pnashdc on 2015-02-02
I have the same problem, but it seems that the problem is nautilus, not (only) VLC. If I open files through thunar, there is no problem. Also, with limited testing, no combination of the non-VPDAU options (h/w decoding or video output) seemed to make any difference from nautilus.

---

### Post by klarkent911 on 2015-03-12
I have the same issue on 14.10. Had this with Linux 3.16, 3.17, 3.19. I have intel 4000 igp and this happens both with VLC, mplayer and deleting files with nautilus or even opening a terminal... it's a strange issue like something that locks and is released after some seconds. Moreover if I press CTRL+ALT+T (to terminal) more and more and then wait after some time all the terminals open at the same time! It's like a system wide problem... not happening often but often appears when managing videos...

---

