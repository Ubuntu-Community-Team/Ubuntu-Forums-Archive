---
title: "MPEG4IP problem"
date: 2008-04-12
forum: Multimedia &amp; Video
---

### Post by Disco0101 on 2008-04-12
Hallo,

I have a problem.
I want to install mpeg4ip, but when i do make then i get 2 errors...
can somebody tell me whats the problem?

ffmpeg.cpp:217: warning: 'avcodec_decode_audio' is deprecated (declared at /usr/include/ffmpeg/avcodec.h:2791)
ffmpeg.cpp:218: warning: 'avcodec_decode_audio' is deprecated (declared at /usr/include/ffmpeg/avcodec.h:2791)
make[3]: *** [ffmpeg.lo] Fehler 1
make[3]: Leaving directory `/home/SF/Desktop/mpeg4ip-1.4.1/player/plugin/audio/ffmpeg'
make[2]: *** [all-recursive] Fehler 1
make[2]: Leaving directory `/home/SF/Desktop/mpeg4ip-1.4.1/player/plugin/audio'
make[1]: *** [all-recursive] Fehler 1
make[1]: Leaving directory `/home/SF/Desktop/mpeg4ip-1.4.1/player/plugin'
make: *** [all-recursive] Fehler 1


help me please:confused:

---

### Post by Disco0101 on 2008-04-13
Nobody any idea?????

help me please, its very important...

---

### Post by xc3RnbFO8P on 2008-04-13
Read this (if you haven't) :
[http://packages.ubuntu.com/source/hardy/mpeg4ip]("http://packages.ubuntu.com/source/hardy/mpeg4ip")

---

### Post by Disco0101 on 2008-04-13
thank you for this site, but with this version i get the same problems:

 g++ -DHAVE_CONFIG_H -I. -I. -I../.. -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12 -I../../include -I../../lib/ffmpeg -I../../lib/mp4v2 -I../../lib/mp4av -I../../lib/msg_queue -I../../lib/rtp -I../../lib/sdp -I../../lib/utils -I../../lib -I../../lib/mpeg2ps -I../../lib/srtp -I../../player/lib -I../../player/src -I./h261 -D_REENTRANT -DNOCONTROLS -fexceptions -Wall -Wno-char-subscripts -Woverloaded-virtual -Wno-unknown-pragmas -Wno-deprecated -Wformat=2 -Wpointer-arith -Wsign-compare -fno-strict-aliasing -g -O2 -DUSE_MMX -DMPEG4IP -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT -MT video_x264.lo -MD -MP -MF .deps/video_x264.Tpo -c video_x264.cpp  -fPIC -DPIC -o .libs/video_x264.o
video_x264.cpp: In member function 'virtual bool CX264VideoEncoder::Init()':
video_x264.cpp:257: error: 'x264_motion_est_names' was not declared in this scope
video_x264.cpp:316: error: 'struct x264_param_t::<anonymous>' has no member named 'b_ssim'
make[4]: *** [video_x264.lo] Fehler 1
make[4]: Leaving directory `/home/SF/Desktop/mpeg4ip-1.6dfsg/server/mp4live'
make[3]: *** [all-recursive] Fehler 1
make[3]: Leaving directory `/home/SF/Desktop/mpeg4ip-1.6dfsg/server/mp4live'
make[2]: *** [all-recursive] Fehler 1
make[2]: Leaving directory `/home/SF/Desktop/mpeg4ip-1.6dfsg/server'
make[1]: *** [all-recursive] Fehler 1
make[1]: Leaving directory `/home/SF/Desktop/mpeg4ip-1.6dfsg'
make: *** [all] Fehler 2

help me please...

---

### Post by mc4man on 2008-04-13
see here
[http://ubuntuforums.org/archive/index.php/t-471978.html](http://ubuntuforums.org/archive/index.php/t-471978.html)

---

### Post by Disco0101 on 2008-04-13
this article i know, 

i commended out, but the command checkinstall does not exist...

what i should do?

---

### Post by xc3RnbFO8P on 2008-04-13
Did you check if got all the package installed,** Other Packages Related to mpeg4ip**

---

### Post by Disco0101 on 2008-04-13
so, no i made make install without errors, but now i started the mp4player and get errors again:

[root@localhost mpeg4ip-1.6dfsg]# mp4player
17:21:22.308-plugin-6: Adding video plugin MPEG4 ISO /usr/local/lib/mp4player_plugin/mpeg4_iso_plugin.so
17:21:22.309-plugin-6: Adding RTP plugin rfc-2429 /usr/local/lib/mp4player_plugin/rfc2429_rtp_plugin.so
17:21:22.309-plugin-6: Adding audio plugin aac /usr/local/lib/mp4player_plugin/aac_plugin.so
17:21:22.309-plugin-6: Adding RTP plugin isma-href /usr/local/lib/mp4player_plugin/href_rtp_plugin.so
17:21:22.309-plugin-6: Adding text plugin href /usr/local/lib/mp4player_plugin/href_text_plugin.so
17:21:22.311-plugin-3: Can't dlopen plugin /usr/local/lib/mp4player_plugin/mpeg2dec_video_plugin.so - /usr/local/lib/mp4player_plugin/mpeg2dec_video_plugin.so: cannot restore segment prot after reloc: Permission denied


What i have to do, please help me, it is very very very important for me and my job
Speicherzugriffsfehler

---

### Post by xc3RnbFO8P on 2008-04-13
Try to find this in your computer: mp4player_plugin/mpeg2dec_video_plu gin.so

---

### Post by Disco0101 on 2008-04-13
i found this plugin here:

/usr/local/lib/mp4player_plugin/mpeg2dec_video_plugin.so

---

### Post by xc3RnbFO8P on 2008-04-13
In Synaptic Package Manager search **dlopen**

---

### Post by Disco0101 on 2008-04-13
i cant found this paket dlopen...

what is it?

help me please???

---

### Post by xc3RnbFO8P on 2008-04-13
I dont know how do this, maybe someone can help you solve this problem,
and how to use this command: > chcon
This is what I found:
[http://support.wolfram.com/mathematica/systems/linux/general/selinux.html]("http://support.wolfram.com/mathematica/systems/linux/general/selinux.html")
[http://www.ittvis.com/services/techtip.asp?ttid=3092]("http://www.ittvis.com/services/techtip.asp?ttid=3092")

---

### Post by Disco0101 on 2008-04-14
i dont understand it...

anybody other ideas to this?

is it a problem of mpeg4ip code or of FC6???

---

### Post by mc4man on 2008-04-14
here's a little explanation of error

> It means that you have a read-only section (like text) that contains
relocs that require modifying the read-only section.  This requires a
mprotect call before we can modify it, and a second mprotect call after
the fact to make the section read-only again after we change it.  The
second mprotect call failed.

Of course, if you have a proper shared library, you should not have any
relocs against the text section.
Maybe there is a problem with the way mpeg4ip created the libs/plugins  or a SLElinux issue
I think it's more likely the former than latter
here's an example use of chcon
[http://www.easysoft.com/support/kb/kb00976.html](http://www.easysoft.com/support/kb/kb00976.html)

---

### Post by Disco0101 on 2008-04-14
iam a newbi, so your informations dont help me very much.
can somebody explain me what i have to do, that i can use mpeg4ip?

---

### Post by Disco0101 on 2008-04-14
Hello to everybody,

i had done this:

./boostrap --disabled x264
make

and now, no error!

had anybody an idea, whats the problem with the x264 codec???

---

