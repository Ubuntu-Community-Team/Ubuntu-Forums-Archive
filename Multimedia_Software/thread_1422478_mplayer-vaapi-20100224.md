---
title: "mplayer-vaapi-20100224"
date: 2010-03-05
forum: Multimedia Software
---

### Post by coljohnhannibalsmith on 2010-03-05
I am trying to Install "mplayer-vaapi-20100224" and get the following error:

john@Laptop:~/Desktop/Extract/mplayer-vaapi-20100224$ ./checkout-patch-build.shERROR: you need VA API headers for this project
john@Laptop:~/Desktop/Extract/mplayer-vaapi-20100224$ 

I'm pretty sure I've already installed "libVA," so what else do I need?



Thanks, John

---

### Post by mc4man on 2010-03-05
make sure you have the headers installed - easiest way is to build libVa as a package set,then install libva and libva-dev 
(might as well also use the [latest sds]("http://www.splitted-desktop.com/~gbeauchesne/libva/") (feb. 23

Then just extract and something like this will do (referring to libva source
```
dpkg-buildpackage -rfakeroot -D -us -uc
```

---

### Post by coljohnhannibalsmith on 2010-03-06
I did what you said and it appeared to work.  See below:

Libraries have been installed in:
   /usr/local/lib/va/drivers

If you ever happen to want to link against installed libraries
in a given directory, LIBDIR, you must either use libtool, and
specify the full pathname of the library, or use the `-LLIBDIR'
flag during linking and do at least one of the following:
   - add LIBDIR to the `LD_LIBRARY_PATH' environment variable
     during execution
   - add LIBDIR to the `LD_RUN_PATH' environment variable
     during linking
   - use the `-Wl,--rpath -Wl,LIBDIR' linker flag
   - have your system administrator add LIBDIR to `/etc/ld.so.conf'

See any operating system documentation about shared libraries for
more information, such as the ld(1) and ld.so(8) manual pages.

But I'm still getting the same error:

john@Laptop:~$ cd /home/john/Desktop/Extract/mplayer-vaapi-20100224
john@Laptop:~/Desktop/Extract/mplayer-vaapi-20100224$ sudo ./checkout-patch-build.sh
ERROR: you need VA API headers for this project
john@Laptop:~/Desktop/Extract/mplayer-vaapi-20100224$ 

Any thoughts?

Thanks, Hannibal

---

### Post by Melcar on 2010-03-06
Make sure you're installing all three packages: libva1, libva1-dbg, libva-dev.  Use the latest version, which is sds10.

---

### Post by mc4man on 2010-03-06
I believe the .sh you're using is looking in /usr/include not /usr/local/include where you've indicated that libva was installed to

> if ! [ -f /usr/include/va/va.h ]; then

> Libraries have been installed in:
/usr/local/lib/va/drivers

If you build libva as described (using the included debian/rules) then it would install to /usr and would be found

Otherwise I guess you could open the .sh with a text editor and edit it to look in /usr/local instead, though I'd build libva as described previously and install to /usr.



Also you generally shouldn't build as root, only install (so lose the sudo
> [COLOR="Red"]sudo[/COLOR] ./checkout-patch-build.sh

screen shows libva built as .deb's (plus same for vdpau-video

---

### Post by coljohnhannibalsmith on 2010-03-07
It tried to rebuild the libraries but it wouldn't let me, so I edited the .sh, but the library path wasn't the only problem with the script.  See below:

if ! [ -d /usr/local/lib/va/drivers/ ]; then
    echo "ERROR: you need VA API headers for this project" > /dev/stderr
    exit 1
fi

I had to change the "-f" to "-d," since the libraries are stored in a directory, not a file.  It took over 10 minutes to compile.  What a complicated pos!

**Well it plays audio, but no video.  See below:

john@Laptop:~/Desktop/Extract/mplayer-vaapi-20100224/mplayer-vaapi$ ./mplayer -vo vaapi -va vaapi /home/john/Desktop/Desktop_Stuff/allgoodthings.AVI
MPlayer SVN-r30589-4.2.4 (C) 2000-2010 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing /home/john/Desktop/Desktop_Stuff/allgoodthings.AVI.
AVI file format detected.
[aviheader] Video stream found, -vid 0
[aviheader] Audio stream found, -aid 1
VIDEO:  [MPG4]  320x240  24bpp  14.985 fps  396.1 kbps (48.4 kbyte/s)
Xlib:  extension "XFree86-VidModeExtension" missing on display ":1.0".
libva: libva version 0.31.0-sds5
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
libva: va_getDriverName() returns -1
[vo_vaapi] vaInitialize(): unknown libva error
Error opening/initializing the selected video_out (-vo) device.
==========================================================================
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 22050 Hz, 1 ch, s16le, 88.8 kbit/25.17% (ratio: 11100->44100)
Selected audio codec: [ffadpcmimawav] afm: ffmpeg (FFmpeg WAV IMA ADPCM audio)
==========================================================================
AO: [oss] 22050Hz 1ch s16le (2 bytes per sample)
Video: no video
Starting playback...
A:  35.5 (35.4) of 194.7 (03:14.6)  0.1% 

Exiting... (End of file)
john@Laptop:~/Desktop/Extract/mplayer-vaapi-20100224/mplayer-vaapi$ 

**Thank you for your help so far.  It's been a crucible, but I think I'm making progress.  Any additional help greatly appreciated.

Thanks, Hannibal

---

