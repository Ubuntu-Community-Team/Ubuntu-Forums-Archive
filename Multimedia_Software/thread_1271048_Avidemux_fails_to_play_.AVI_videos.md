---
title: "Avidemux fails to play .AVI videos"
date: 2009-09-20
forum: Multimedia Software
---

### Post by Chogogo on 2009-09-20
Hello, Im running Ubuntu Jaunty and I am trying to edit som videos recorded with my Dig camera, they come as .AVI videos. The point is that the videos can be played with no problems by other players (Dragon Player,MPlayer) , but when I try to open them with Avidemux I get an error message (the propper audio codec could not be found..." ) the Video is played with out audio. I Installed all the Codecs following Medibuntu's guide.  Avidemux can play other videos  format .avi though (I dont know the difference with those format .AVI)

What could be wrong and what can I do to fix it...the Idea is to edit them with out changing them to another format. I lost video quality when I change it to .mpeg with ffmpeg

Thanks and may God bless you!

---

### Post by cor2y on 2009-09-20
What are the properties of the videos that cant play in avidemux?
To find out either right click on the video file, select properties to see the video and audio codecs of the video, play it with mplayer via the terminal or install the mediainfo app [http://mediainfo.sourceforge.net/en](http://mediainfo.sourceforge.net/en) my guess is its an audio codec not supported by vanilla avidemux and you may need to compile your own version of avidemux with the needed audio codec support.
If there is no support then you could try transcoding the audio to pcm lossless with mencoder then running the video through avidemux again.

---

### Post by Chogogo on 2009-09-20
It Cannot play the sound.  The video codec is Motion-JPEG and the audio codec is Mu-Law audio


I would like to know both options. How to install an avidemux that can play this codec and how to transcode the video's audio to another format without touching the video format, using mencoder or ffmpeg

I played a Video using Mplayer and this the cosole output that I got...

Thanks for help 

May God bless you..!

===========Console output==========================================
Playing Julian1.AVI.
AVI file format detected.
[aviheader] Video stream found, -vid 0
[aviheader] Audio stream found, -aid 1
VIDEO:  [MJPG]  640x480  24bpp  30.000 fps  10686.1 kbps (1304.5 kbyte/s)
Clip info:
 Software: 
xscreensaver_disable: Could not find XScreenSaver window.
GNOME screensaver disabled
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
[mjpeg @ 0x8972350]mjpeg: using external huffman table
[mjpeg @ 0x8972350]mjpeg: error using external huffman table, switching back to internal
Selected video codec: [ffmjpeg] vfm: ffmpeg (FFmpeg MJPEG decoder)
==========================================================================
==========================================================================
Forced audio codec: mad
Opening audio decoder: [alaw] aLaw/uLaw audio decoder
AUDIO: 8000 Hz, 1 ch, s16le, 64.0 kbit/50.00% (ratio: 8000->16000)
Selected audio codec: [ulaw] afm: alaw (uLaw)
==========================================================================

---

### Post by cor2y on 2009-09-20
Well good news you can get the audio decoded in avidemux, it requires libmad-dev library if you plan to compile it yourself.
For the latest version of avidemux (version 2.5.1) regarding ubuntu follow this tutorial but make sure libmad-dev is installed first via synaptic (search for libmad0-dev) or the terminal
```
 sudo apt-get install libmad0-dev
```
If you get a message that no such library exists or synaptic doesnt find it then you will have to enable your universal repos, i dont recall if libmad is in the universe repos or not.
Next up compiling avidemux 2.5.1 see [this]("http://www.avidemux.org/admWiki/index.php?title=Install_2.5")

---

### Post by Chogogo on 2009-09-21
Hello, Thanks for the response.
I installed libmad0-dev and then I installed Avidemux 2.5.1 (Autoinstall) files from GetDeb's website. But it didn't work, I get the same error message. Should I Install it manually instead ? or what should I've done?. the point is I tryed to follow the tutorial in the link you sent, but it doesn't work with .deb files...It seems that I need another type files...Or not?

Thanks for your help...And God bless you!

---

### Post by cor2y on 2009-09-21
In General because of legal issues the getdeb version of avidemux does not support all the plugin decoders/encoders,
Which is why you need to compile it yourself, now i am not sure if libmad falls into this category.
But a good way to discover this is to check the audio plugin decoders to see if libmad is listed if not then you will need to build avidemux yourself using the link i provided.
Launch Avidemux go to Help->Plugins , look at the first tab the one that says Audio see if libmad is listed.
Should look like this [[img]http://www.ubuntu-pics.de/thumb/25375/screenshot_002_4n67uT.png[/img]](http://www.ubuntu-pics.de/bild/25375/screenshot_002_4n67uT.png)
Dont mind if yours may be missing some of the decoders my version of avidemux is custom compiled and not from getdeb

If LibMad is listed and still the same audio problem then you will need to use another app to convert say mencoder or ffmpeg which does have support for the audio decoding.

---

### Post by Chogogo on 2009-09-23
Hello
First thanks for the info. Unfortunately , libMad is listed but still the same problem. I learned how to change the audio codec with ffmpeg, But I would like to know from where can I download another version of Avidemux that I would be able to compile my self (following your instructions) because I couldn't use the one I download from getdeb.

Thanks and God bless you!!

---

### Post by cor2y on 2009-09-23
you can get avidemux from the official site [www.avidemux.org](www.avidemux.org)  also  in the official forums i found this over there about your problems maybe it can shine a light on it.
> 
I own a Kodak "EasyShare" digicam myself and it *can* capture video clips.
IMHO the quality of the video clips is surprisingly good for a cheap photo camera like that.
The container format is MOV, the video format is MPEG-4 (DIVX) and the audio format is ULAW.
I have converted some of those videos with Avidemux in the past and it worked fine so far.
Note: You can set Video to "Copy" and Format to "AVI" and it will convert just fine!
Only the "ULAW" audio did *not* work in the "Copy" mode, but setting audio to "MP3" fixed it.


My apologies its the ULaw codec thats in use but avidemux by defualt supports it for decoding not encoding to another container though so perhaps as a test you can try setting the audio output to something else other than COPY and see if the saved file as audio after you compile your version

---

### Post by Chogogo on 2009-09-24
Hello, I tryed the method sugested and followed installations instructions from [This site]("http://www.avidemux.org/admWiki/index.php?title=Compiling_Avidemux"). Everything ok until I got to the point " make -f Makefile.dist " then I got this:
*** Creating aclocal.m4
configure.in:1522: error: `config.h' is already registered with AC_CONFIG_HEADERS.
../../lib/autoconf/status.m4:709: AC_CONFIG_HEADERS is expanded from...
/usr/share/aclocal-1.9/header.m4:12: AM_CONFIG_HEADER is expanded from...
configure.in:1522: the top level
/usr/bin/m4: cannot remove temporary directory /tmp/m4-hzA9lV: Directory not empty
autom4te: /usr/bin/m4 failed with exit status: 1
aclocal: autom4te failed with exit status: 1
make[1]: *** [cvs] Error 1
make: *** [all] Error 2
==========================================

Then I tried next step "make" and this is what i got:

omar@Hogar:~/avidemux/avidemux_2.4_branch$ make
make: *** No se especificó ningún objetivo y no se encontró ningún makefile.  Alto.
 Translation: *** No objective was specified and no makefile was found. Stop. 

Do you know whats happening??  ...Please help!

Thanks and may God bless you!!

---

### Post by cor2y on 2009-09-24
Which version of avidemux are you trying to build?
For the newer 2.5 version avidemux now compiles with cmake. so its recommended you use this [method]("http://www.avidemux.org/admWiki/index.php?title=Install_2.5#Example_Ubuntu_Compilation")
The later 2.4 versions also graduated to using cmake as the compiler as the configure script was notoriously buggy and outdated.
Make should only be used if its the old 2.3 version of avidemux thats probably why you got that error.

---

