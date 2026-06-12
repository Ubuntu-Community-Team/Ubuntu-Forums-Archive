---
title: "Ffmpeg Ubuntu 8.10"
date: 2009-01-09
forum: Multimedia Software
---

### Post by Quiane on 2009-01-09
So i've tried many different guides, uninstalled and recompiled ffmpeg many times over the last week.  I've installed from the synaptic but still this problem persists.

I cannot get anything (winff, thinliquidfilm et-all) to even start encoding .avi videos to ipod format.  
Thinliquidfilm can't even open the .avi file saying that it's not a vaild file and may be corrupted.  winff shows up with errors and says that xvid isin't installed.  I'm sure i went through that section of the guid many times to ensure that it's installed (i'm not at my cpu right now to post the screen shot, but i can do that a little later). 
h264 is installed, that doesn't seem to be the problem.

Any help would be greatly apprecated.

---

### Post by FakeOutdoorsman on 2009-01-09
You can enable xvid support in the repository ffmpeg by installing **libavcodec-unstripped-51**.  This should let WinFF do its work (if the presets are correct).  Alternatively, you can follow this guide:
[HOWTO: Compile the latest ffmpeg and x264 from source](http://ubuntuforums.org/showthread.php?t=786095)

---

### Post by Quiane on 2009-01-09
Thanks for the reply.  SO i followed the instructions above, got to step 5 and started running into errors.

Here is the output after running ./config in step 5

Installing with make install...
> 
========================= Installation results ===========================
install -d "/usr/local/lib"
install -m 644 libpostproc/libpostproc.a "/usr/local/lib"
ranlib "/usr/local/lib/libpostproc.a"
install -d "/usr/local/lib"
install -m 644 libavdevice/libavdevice.a "/usr/local/lib"
ranlib "/usr/local/lib/libavdevice.a"
install -d "/usr/local/lib"
install -m 644 libavformat/libavformat.a "/usr/local/lib"
ranlib "/usr/local/lib/libavformat.a"
install -d "/usr/local/lib"
install -m 644 libavcodec/libavcodec.a "/usr/local/lib"
ranlib "/usr/local/lib/libavcodec.a"
install -d "/usr/local/lib"
install -m 644 libavutil/libavutil.a "/usr/local/lib"
ranlib "/usr/local/lib/libavutil.a"
install -d "/usr/local/include/libpostproc"
install -d "/usr/local/lib/pkgconfig"
install -m 644 "/home/mark/ffmpeg/libpostproc"/postprocess.h "/usr/local/include/libpostproc"
install -m 644 "/home/mark/ffmpeg"/libpostproc/libpostproc.pc "/usr/local/lib/pkgconfig"
install -d "/usr/local/include/libavdevice"
install -d "/usr/local/lib/pkgconfig"
install -m 644 "/home/mark/ffmpeg/libavdevice"/avdevice.h "/usr/local/include/libavdevice"
install -m 644 "/home/mark/ffmpeg"/libavdevice/libavdevice.pc "/usr/local/lib/pkgconfig"
install -d "/usr/local/include/libavformat"
install -d "/usr/local/lib/pkgconfig"
install -m 644 "/home/mark/ffmpeg/libavformat"/avformat.h "/home/mark/ffmpeg/libavformat"/avio.h "/home/mark/ffmpeg/libavformat"/rtsp.h "/home/mark/ffmpeg/libavformat"/rtspcodes.h "/usr/local/include/libavformat"
install -m 644 "/home/mark/ffmpeg"/libavformat/libavformat.pc "/usr/local/lib/pkgconfig"
install -d "/usr/local/include/libavcodec"
install -d "/usr/local/lib/pkgconfig"
install -m 644 "/home/mark/ffmpeg/libavcodec"/avcodec.h "/home/mark/ffmpeg/libavcodec"/opt.h "/home/mark/ffmpeg/libavcodec"/vdpau.h "/usr/local/include/libavcodec"
install -m 644 "/home/mark/ffmpeg"/libavcodec/libavcodec.pc "/usr/local/lib/pkgconfig"
install -d "/usr/local/include/libavutil"
install -d "/usr/local/lib/pkgconfig"
install -m 644 "/home/mark/ffmpeg/libavutil"/adler32.h "/home/mark/ffmpeg/libavutil"/avstring.h "/home/mark/ffmpeg/libavutil"/avutil.h "/home/mark/ffmpeg/libavutil"/base64.h "/home/mark/ffmpeg/libavutil"/common.h "/home/mark/ffmpeg/libavutil"/crc.h "/home/mark/ffmpeg/libavutil"/fifo.h "/home/mark/ffmpeg/libavutil"/intfloat_readwrite.h "/home/mark/ffmpeg/libavutil"/log.h "/home/mark/ffmpeg/libavutil"/lzo.h "/home/mark/ffmpeg/libavutil"/mathematics.h "/home/mark/ffmpeg/libavutil"/md5.h "/home/mark/ffmpeg/libavutil"/mem.h "/home/mark/ffmpeg/libavutil"/random.h "/home/mark/ffmpeg/libavutil"/rational.h "/home/mark/ffmpeg/libavutil"/sha1.h "/usr/local/include/libavutil"
install -m 644 "/home/mark/ffmpeg"/libavutil/libavutil.pc "/usr/local/lib/pkgconfig"
gcc -fPIC -DHAVE_AV_CONFIG_H -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -I. -I"/home/mark/ffmpeg" -D_ISOC99_SOURCE -D_POSIX_C_SOURCE=200112 -std=c99 -fomit-frame-pointer -pthread -g -Wdeclaration-after-statement -Wall -Wno-switch -Wdisabled-optimization -Wpointer-arith -Wredundant-decls -Wno-pointer-sign -Wcast-qual -Wwrite-strings -Wtype-limits -O3 -fno-math-errno -fno-signed-zeros `imlib2-config --cflags` `freetype-config --cflags`  -c -o vhook/fish.o vhook/fish.c
In file included from vhook/fish.c:48:
./libavformat/framehook.h:25:2: warning: #warning VHOOK is deprecated. Please help finishing libavfilter instead of wasting your time writing new filters for this crappy filter system.
vhook/fish.c: In function ‘Configure’:
vhook/fish.c:130: warning: assignment discards qualifiers from pointer target type
vhook/fish.c: In function ‘Process’:
vhook/fish.c:371: warning: ignoring return value of ‘fwrite’, declared with attribute warn_unused_result
gcc -rdynamic -export-dynamic -Wl,--warn-common -Wl,--as-needed -Wl,-rpath-link,"/home/mark/ffmpeg"/libpostproc -Wl,-rpath-link,"/home/mark/ffmpeg"/libswscale -Wl,-rpath-link,"/home/mark/ffmpeg"/libavfilter -Wl,-rpath-link,"/home/mark/ffmpeg"/libavdevice -Wl,-rpath-link,"/home/mark/ffmpeg"/libavformat -Wl,-rpath-link,"/home/mark/ffmpeg"/libavcodec -Wl,-rpath-link,"/home/mark/ffmpeg"/libavutil -Wl,-Bsymbolic -o vhook/fish.so -shared -Wl,-soname,fish.so vhook/fish.o  
gcc -fPIC -DHAVE_AV_CONFIG_H -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -I. -I"/home/mark/ffmpeg" -D_ISOC99_SOURCE -D_POSIX_C_SOURCE=200112 -std=c99 -fomit-frame-pointer -pthread -g -Wdeclaration-after-statement -Wall -Wno-switch -Wdisabled-optimization -Wpointer-arith -Wredundant-decls -Wno-pointer-sign -Wcast-qual -Wwrite-strings -Wtype-limits -O3 -fno-math-errno -fno-signed-zeros `imlib2-config --cflags` `freetype-config --cflags`  -c -o vhook/null.o vhook/null.c
In file included from vhook/null.c:23:
./libavformat/framehook.h:25:2: warning: #warning VHOOK is deprecated. Please help finishing libavfilter instead of wasting your time writing new filters for this crappy filter system.
gcc -rdynamic -export-dynamic -Wl,--warn-common -Wl,--as-needed -Wl,-rpath-link,"/home/mark/ffmpeg"/libpostproc -Wl,-rpath-link,"/home/mark/ffmpeg"/libswscale -Wl,-rpath-link,"/home/mark/ffmpeg"/libavfilter -Wl,-rpath-link,"/home/mark/ffmpeg"/libavdevice -Wl,-rpath-link,"/home/mark/ffmpeg"/libavformat -Wl,-rpath-link,"/home/mark/ffmpeg"/libavcodec -Wl,-rpath-link,"/home/mark/ffmpeg"/libavutil -Wl,-Bsymbolic -o vhook/null.so -shared -Wl,-soname,null.so vhook/null.o  
gcc -fPIC -DHAVE_AV_CONFIG_H -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -I. -I"/home/mark/ffmpeg" -D_ISOC99_SOURCE -D_POSIX_C_SOURCE=200112 -std=c99 -fomit-frame-pointer -pthread -g -Wdeclaration-after-statement -Wall -Wno-switch -Wdisabled-optimization -Wpointer-arith -Wredundant-decls -Wno-pointer-sign -Wcast-qual -Wwrite-strings -Wtype-limits -O3 -fno-math-errno -fno-signed-zeros `imlib2-config --cflags` `freetype-config --cflags`  -c -o vhook/watermark.o vhook/watermark.c
In file included from vhook/watermark.c:63:
./libavformat/framehook.h:25:2: warning: #warning VHOOK is deprecated. Please help finishing libavfilter instead of wasting your time writing new filters for this crappy filter system.
gcc -rdynamic -export-dynamic -Wl,--warn-common -Wl,--as-needed -Wl,-rpath-link,"/home/mark/ffmpeg"/libpostproc -Wl,-rpath-link,"/home/mark/ffmpeg"/libswscale -Wl,-rpath-link,"/home/mark/ffmpeg"/libavfilter -Wl,-rpath-link,"/home/mark/ffmpeg"/libavdevice -Wl,-rpath-link,"/home/mark/ffmpeg"/libavformat -Wl,-rpath-link,"/home/mark/ffmpeg"/libavcodec -Wl,-rpath-link,"/home/mark/ffmpeg"/libavutil -Wl,-Bsymbolic -o vhook/watermark.so -shared -Wl,-soname,watermark.so vhook/watermark.o  
gcc -fPIC -DHAVE_AV_CONFIG_H -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -I. -I"/home/mark/ffmpeg" -D_ISOC99_SOURCE -D_POSIX_C_SOURCE=200112 -std=c99 -fomit-frame-pointer -pthread -g -Wdeclaration-after-statement -Wall -Wno-switch -Wdisabled-optimization -Wpointer-arith -Wredundant-decls -Wno-pointer-sign -Wcast-qual -Wwrite-strings -Wtype-limits -O3 -fno-math-errno -fno-signed-zeros `imlib2-config --cflags` `freetype-config --cflags`  -c -o vhook/ppm.o vhook/ppm.c
In file included from vhook/ppm.c:29:
./libavformat/framehook.h:25:2: warning: #warning VHOOK is deprecated. Please help finishing libavfilter instead of wasting your time writing new filters for this crappy filter system.
vhook/ppm.c: In function ‘rwpipe_open’:
vhook/ppm.c:59: warning: ignoring return value of ‘pipe’, declared with attribute warn_unused_result
vhook/ppm.c:60: warning: ignoring return value of ‘pipe’, declared with attribute warn_unused_result
vhook/ppm.c: In function ‘rwpipe_read_ppm_header’:
vhook/ppm.c:163: warning: ignoring return value of ‘fgets’, declared with attribute warn_unused_result
vhook/ppm.c: In function ‘Process’:
vhook/ppm.c:236: warning: ‘out_height’ may be used uninitialized in this function
vhook/ppm.c:235: warning: ‘out_width’ may be used uninitialized in this function
gcc -rdynamic -export-dynamic -Wl,--warn-common -Wl,--as-needed -Wl,-rpath-link,"/home/mark/ffmpeg"/libpostproc -Wl,-rpath-link,"/home/mark/ffmpeg"/libswscale -Wl,-rpath-link,"/home/mark/ffmpeg"/libavfilter -Wl,-rpath-link,"/home/mark/ffmpeg"/libavdevice -Wl,-rpath-link,"/home/mark/ffmpeg"/libavformat -Wl,-rpath-link,"/home/mark/ffmpeg"/libavcodec -Wl,-rpath-link,"/home/mark/ffmpeg"/libavutil -Wl,-Bsymbolic -o vhook/ppm.so -shared -Wl,-soname,ppm.so vhook/ppm.o  
gcc -fPIC -DHAVE_AV_CONFIG_H -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -I. -I"/home/mark/ffmpeg" -D_ISOC99_SOURCE -D_POSIX_C_SOURCE=200112 -std=c99 -fomit-frame-pointer -pthread -g -Wdeclaration-after-statement -Wall -Wno-switch -Wdisabled-optimization -Wpointer-arith -Wredundant-decls -Wno-pointer-sign -Wcast-qual -Wwrite-strings -Wtype-limits -O3 -fno-math-errno -fno-signed-zeros `imlib2-config --cflags` `freetype-config --cflags`  -c -o vhook/imlib2.o vhook/imlib2.c
In file included from vhook/imlib2.c:48:
./libavformat/framehook.h:25:2: warning: #warning VHOOK is deprecated. Please help finishing libavfilter instead of wasting your time writing new filters for this crappy filter system.
vhook/imlib2.c: In function ‘Configure’:
vhook/imlib2.c:149: warning: initialization discards qualifiers from pointer target type
vhook/imlib2.c:161: warning: assignment discards qualifiers from pointer target type
vhook/imlib2.c:162: warning: assignment discards qualifiers from pointer target type
vhook/imlib2.c:168: warning: suggest parentheses around assignment used as truth value
vhook/imlib2.c:282: warning: passing argument 7 of ‘ff_parse’ from incompatible pointer type
vhook/imlib2.c:286: warning: passing argument 7 of ‘ff_parse’ from incompatible pointer type
vhook/imlib2.c:290: warning: passing argument 7 of ‘ff_parse’ from incompatible pointer type
vhook/imlib2.c:297: warning: passing argument 7 of ‘ff_parse’ from incompatible pointer type
vhook/imlib2.c:320: warning: passing argument 7 of ‘ff_parse’ from incompatible pointer type
vhook/imlib2.c:325: warning: passing argument 7 of ‘ff_parse’ from incompatible pointer type
vhook/imlib2.c: In function ‘Process’:
vhook/imlib2.c:420: warning: assignment discards qualifiers from pointer target type
vhook/imlib2.c:428: warning: assignment discards qualifiers from pointer target type
gcc -rdynamic -export-dynamic -Wl,--warn-common -Wl,--as-needed -Wl,-rpath-link,"/home/mark/ffmpeg"/libpostproc -Wl,-rpath-link,"/home/mark/ffmpeg"/libswscale -Wl,-rpath-link,"/home/mark/ffmpeg"/libavfilter -Wl,-rpath-link,"/home/mark/ffmpeg"/libavdevice -Wl,-rpath-link,"/home/mark/ffmpeg"/libavformat -Wl,-rpath-link,"/home/mark/ffmpeg"/libavcodec -Wl,-rpath-link,"/home/mark/ffmpeg"/libavutil -Wl,-Bsymbolic -o vhook/imlib2.so -shared -Wl,-soname,imlib2.so vhook/imlib2.o  `imlib2-config --libs`
gcc -fPIC -DHAVE_AV_CONFIG_H -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -I. -I"/home/mark/ffmpeg" -D_ISOC99_SOURCE -D_POSIX_C_SOURCE=200112 -std=c99 -fomit-frame-pointer -pthread -g -Wdeclaration-after-statement -Wall -Wno-switch -Wdisabled-optimization -Wpointer-arith -Wredundant-decls -Wno-pointer-sign -Wcast-qual -Wwrite-strings -Wtype-limits -O3 -fno-math-errno -fno-signed-zeros `imlib2-config --cflags` `freetype-config --cflags`  -c -o vhook/drawtext.o vhook/drawtext.c
In file included from vhook/drawtext.c:48:
./libavformat/framehook.h:25:2: warning: #warning VHOOK is deprecated. Please help finishing libavfilter instead of wasting your time writing new filters for this crappy filter system.
gcc -rdynamic -export-dynamic -Wl,--warn-common -Wl,--as-needed -Wl,-rpath-link,"/home/mark/ffmpeg"/libpostproc -Wl,-rpath-link,"/home/mark/ffmpeg"/libswscale -Wl,-rpath-link,"/home/mark/ffmpeg"/libavfilter -Wl,-rpath-link,"/home/mark/ffmpeg"/libavdevice -Wl,-rpath-link,"/home/mark/ffmpeg"/libavformat -Wl,-rpath-link,"/home/mark/ffmpeg"/libavcodec -Wl,-rpath-link,"/home/mark/ffmpeg"/libavutil -Wl,-Bsymbolic -o vhook/drawtext.so -shared -Wl,-soname,drawtext.so vhook/drawtext.o  `freetype-config --libs`
install -d "/usr/local/lib/vhook"
install -m 755 vhook/fish.so vhook/null.so vhook/watermark.so vhook/ppm.so vhook/imlib2.so vhook/drawtext.so "/usr/local/lib/vhook"
gcc -L"/home/mark/ffmpeg"/libpostproc -L"/home/mark/ffmpeg"/libavdevice -L"/home/mark/ffmpeg"/libavformat -L"/home/mark/ffmpeg"/libavcodec -L"/home/mark/ffmpeg"/libavutil -rdynamic -export-dynamic -Wl,--warn-common -Wl,--as-needed -Wl,-rpath-link,"/home/mark/ffmpeg"/libpostproc -Wl,-rpath-link,"/home/mark/ffmpeg"/libswscale -Wl,-rpath-link,"/home/mark/ffmpeg"/libavfilter -Wl,-rpath-link,"/home/mark/ffmpeg"/libavdevice -Wl,-rpath-link,"/home/mark/ffmpeg"/libavformat -Wl,-rpath-link,"/home/mark/ffmpeg"/libavcodec -Wl,-rpath-link,"/home/mark/ffmpeg"/libavutil -Wl,-Bsymbolic -o ffmpeg_g ffmpeg.o cmdutils.o -lpostproc -lavdevice -lavformat -lavcodec -lavutil -lz -pthread -lm -lfaac -lfaad -lmp3lame -lm -ltheora -logg -lx264 -lm    -ldl -ldl
ffmpeg.o: In function `do_video_out':
/home/mark/ffmpeg/ffmpeg.c:912: undefined reference to `sws_scale'
ffmpeg.o: In function `av_encode':
/home/mark/ffmpeg/ffmpeg.c:2213: undefined reference to `sws_freeContext'
/home/mark/ffmpeg/ffmpeg.c:1815: undefined reference to `sws_getContext'
ffmpeg.o: In function `main':
/home/mark/ffmpeg/ffmpeg.c:3884: undefined reference to `sws_getContext'
collect2: ld returned 1 exit status
make: *** [ffmpeg_g] Error 1

****  Installation failed. Aborting package creation.


(i think i did that right....put it into a box i mean...)

anyway..thanks again...does this give anyone an idea where i'm going wrong?

---

### Post by Quiane on 2009-01-09
okay, so i've been doing some reading, and here is the output when i run ./configure in ffmpeg
[PHP]
mark@mark-desktop:~$ ./configure --enable-gpl --enable-pp --enable-libvorbis --enable-libogg  --enable-liba52 --enable-libmp3lame --enable-libfaad --enable-libfaac
bash: ./configure: No such file or directory
mark@mark-desktop:~$ cd ffmpeg
mark@mark-desktop:~/ffmpeg$ ./configure --enable-gpl --enable-pp --enable-libvorbis --enable-libogg  --enable-liba52 --enable-libmp3lame --enable-libfaad --enable-libfaac
Unknown option "--enable-pp".
See ./configure --help for available options.
mark@mark-desktop:~/ffmpeg$ 
[/PHP]

SO i'm missing the "--enable-pp" but i have no idea how to fix that. i know i need to download the rpm and install it, but i'm just not sure how to go about that?

---

### Post by wolfen69 on 2009-01-09
would you like a 1 click solution to convert to ipod format? use [Handbrake]("http://handbrake.fr/rotation.php?file=HandBrake-0.9.3-Ubuntu_GUI_i386.deb"). just click to install. when you open the app, you will see "presets" on the right. just choose ipod.

---

### Post by andrew.46 on 2009-01-10
Hi Quiane,

> **Quiane said:**
> SO i'm missing the "--enable-pp" but i have no idea how to fix that. i know i need to download the rpm and install it, but i'm just not sure how to go about that?

This was altered to --enable-postproc a while back. To see available options change to the source directory of ffmpeg and type:

```
$ ./configure --help
```

Andrew

---

### Post by Quiane on 2009-01-10
thanks for the replys guys, i didn't realize that handbreak had a linux gui released...
I'm still working on the ffmpeg, but handbreak is a nice program!

Regards

---

### Post by FakeOutdoorsman on 2009-01-10
> **Quiane said:**
> 
SO i'm missing the "--enable-pp" but i have no idea how to fix that. i know i need to download the rpm and install it, but i'm just not sure how to go about that?
Why don't you just use the configure line from the guide linked above?  Are you using Ubuntu?  RPM is generally for Red Hat based distributions.  If you're uncomfortable compiling your own ffmpeg, then I recommend installing the version from the official Ubuntu repository:
```
sudo apt-get install ffmpeg libavcodec-unstripped-51
```

---

### Post by Quiane on 2009-01-11
Alright,

I have downloaded and used handbreak to transfer my files.  They transfer successfully into the directory i specify, and they go into banshee. i can play them in banshee, and their extention is .mp4.  I transfer them to my ipod, and when i go to that file (any of the files recently encoded) the ipod freezes, and pushes me out to the main menu if left long enough. 

I tried installing ffmpeg with the apt-get listed above, and then tried reencoding with winff (and handbreak), and got the same result / error that i got before (with winff and handbrake respectively). I had this working in 7.10 with no problems with thinliquid film, but that just isin't seeming possible at the moment! i apprecate all the responses up to now..any other ideas?

Also, i can't post the output of winff's error because it wont let me cut and paste the output (not sure why, and i even ran it in terminal), but when i fired it up in terminal it came up with these errors...could this have something to do with it?
[PHP]
mark@mark-desktop:~$ winff

(winff:24309): Gtk-WARNING **: Unable to locate theme engine in module_path: "ubuntulooks",
[WARNING] Out of OEM specific VK codes, changing to unassigned
[WARNING] Out of unassigned VK codes, assigning $FF

(winff:24309): Gtk-CRITICAL **: gtk_tree_view_set_cursor_on_cell: assertion `tree_view->priv->tree != NULL' failed
[/PHP]

---

### Post by paul.gevers on 2009-01-24
> **Quiane said:**
> 
Also, i can't post the output of winff's error because it wont let me cut and paste the output (not sure why, and i even ran it in terminal), but when i fired it up in terminal it came up with these errors...could this have something to do with it?
```

mark@mark-desktop:~$ winff

(winff:24309): Gtk-WARNING **: Unable to locate theme engine in module_path: "ubuntulooks",
[WARNING] Out of OEM specific VK codes, changing to unassigned
[WARNING] Out of unassigned VK codes, assigning $FF

(winff:24309): Gtk-CRITICAL **: gtk_tree_view_set_cursor_on_cell: assertion `tree_view->priv->tree != NULL' failed

```
Is WinFF running when you get these errors, or does it just terminate?

What version of WinFF and where did you get it?

---

