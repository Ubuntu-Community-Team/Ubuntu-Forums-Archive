---
title: "Ripping CD's to Mp3 using ffmpeg"
date: 2007-07-13
forum: Multimedia &amp; Video
---

### Post by bennyj on 2007-07-13
I have a couple of questions about converting music from cd's to mp3 using ffmpeg.I have sound juicer installed and configured to rip to mp3.I am how ever getting wierd track length results.Some of the songs have huge track lengths of like 23mins and I know for a fact the song is only 4:30 second long wich leads to problems trying to burn them to cd using serpentine.By the time I finish adding the songs I want I have exceeded the maximu capacity of the cd even though they should fit onto an 80 min cd no problem.wich leads me to my next question.

Has anyone used ffmpeg to convert their music cd's to mp3? If so is thier a gui for ffmpeg that one could use to accomplish this as easy as it is to use sepentine?And is one(ffmpeg vs gstreamer)better than the other for doing this?

thanks

---

### Post by Major_Kong on 2007-07-13
The problem is xingmux is broken. It writes a xing header into a mp3-vbr so that it can be properly read. It's not a new problem apparently, but for some strange reason it's not getting fixed. Other than the file is properly encoded.

Personally i've never tried to use ffmpeg to that effect, I gave up and just use the CLI lame encoder. 

PS: Be sure to use the latest lame encoder and ugly plugins, you'll get better compression/quality.


EDIT: Got around to try what you suggested, using ffmux_mpeg instead of xingmux, it didn't work. 

You can try it. just change the pipeline to for e.g.: audio/x-raw-int,rate=44100,channels=2 ! lame quality=0 vbr=4 vbr-quality=3 ! ffmux_mpeg ! id3v2mux

---

### Post by bennyj on 2007-07-13
> **Major_Kong said:**
> The problem is xingmux is broken. It writes a xing header into a mp3-vbr so that it can be properly read. It's not a new problem apparently, but for some strange reason it's not getting fixed.

Personally i've never tried to use ffmpeg to that effect, I gave up and just use the CLI lame encoder. 

PS: Be sure to use the latest lame encoder and ugly plugins, you'll get better compression/quality.

Thanks for the reply.I did see where it was a bug xingmux but I was hoping someone found a work around for it..I have the latest lame and I also compiled the lates ffmpeg wich I have ripped to mp3.I was just hoping maybe for a program like soundjuicer but for ffmpeg instead of gstreamer.

---

### Post by Major_Kong on 2007-07-13
Well there's Grip, it doesn't rely on gstreamer, but the gui is not as good.

---

### Post by Major_Kong on 2007-07-13
[http://bugzilla.gnome.org/show_bug.cgi?id=397759](http://bugzilla.gnome.org/show_bug.cgi?id=397759) - There's a proposed patch to fix the problem !

---

### Post by stchman on 2007-07-13
> **bennyj said:**
> I have a couple of questions about converting music from cd's to mp3 using ffmpeg.I have sound juicer installed and configured to rip to mp3.I am how ever getting wierd track length results.Some of the songs have huge track lengths of like 23mins and I know for a fact the song is only 4:30 second long wich leads to problems trying to burn them to cd using serpentine.By the time I finish adding the songs I want I have exceeded the maximu capacity of the cd even though they should fit onto an 80 min cd no problem.wich leads me to my next question.

Has anyone used ffmpeg to convert their music cd's to mp3? If so is thier a gui for ffmpeg that one could use to accomplish this as easy as it is to use sepentine?And is one(ffmpeg vs gstreamer)better than the other for doing this?

thanks

If you are getting weird stuff with ripping to MP3s with Juicer then your GStreamer is wrong.  First you need the proper codecs installed.  Refer here:

[http://www.stchman.com/cd_rip.html](http://www.stchman.com/cd_rip.html)

If you are using Feisty then as soon as you install the proper codecs then the VBR MP3 stuff works fine.

---

### Post by Major_Kong on 2007-07-13
No it doesn't. The gstreamer plugins that come with Feisy (or the latest release of the plugins for that matter) all have the same broken xingmux problem.

EDIT: Made the change to the source sugested in the bug report and recompiled. As far as i can tell it works now. At least in totem and in other gstreamer based players.

---

### Post by stchman on 2007-07-13
> **Major_Kong said:**
> No it doesn't. The gstreamer plugins that come with Feisy (or the latest release of the plugins for that matter) all have the same broken xingmux problem.

Works fine on my system.  I just install the codecs and I can start ripping to MP3 without modifying the gstreamer.

---

### Post by Major_Kong on 2007-07-13
Mp3-vbr ?

---

### Post by stchman on 2007-07-13
> **Major_Kong said:**
> Mp3-vbr ?

The codecs that Ubuntu installs use LAME to rip to MP3.  VBR stands for variable bitrate.  The LAM encoder varies the bitrate of the mp3 depending upon the song.

---

### Post by Major_Kong on 2007-07-13
Not sure if i follow what you wrote...

In this case the program that's used to rip is SoundJuicer, which is a gstreamer frontend. It's gstreamer thru the installed gstreamer plugins (codecs) that do the encoding. And i don't know how far they rely on external LAME libraries to do the encoding (i know the gstreamer encoder plugin is essentialy the LAME encoder, but the use of external libraries is a different matter).

Now, you can choose the encoding profile. You can choose CBR or VBR or ABR if you like and the quality setting. 
The encoder has some  preset settings but i don't know if the preset is vbr-new. 

But moving forward to the xingmux problem.... Gstreamer plugins encode to mp3 properly, they just don't (or at least without the patch to xingmux) add suitable headers to an mp3-vbr. If it's cbr the problem doesn't exist.

EDIT: As i wrote earlier, it's a know bug - [http://bugzilla.gnome.org/show_bug.cgi?id=397759](http://bugzilla.gnome.org/show_bug.cgi?id=397759)

---

### Post by bennyj on 2007-07-13
> **Major_Kong said:**
> Not sure if i follow what you wrote...

In this case the program that's used to rip is SoundJuicer, which is a gstreamer frontend. It's gstreamer thru the installed gstreamer plugins (codecs) that do the encoding. And i don't know how far they rely on external LAME libraries to do the encoding (i know the gstreamer encoder plugin is essentialy the LAME encoder, but the use of external libraries is a different matter).

Now, you can choose the encoding profile. You can choose CBR or VBR or ABR if you like and the quality setting. 
The encoder has some  preset settings but i don't know if the preset is vbr-new. 

But moving forward to the xingmux problem.... Gstreamer plugins encode to mp3 properly, they just don't (or at least without the patch to xingmux) add suitable headers to an mp3-vbr. If it's cbr the problem doesn't exist.

EDIT: As i wrote earlier, it's a know bug - [http://bugzilla.gnome.org/show_bug.cgi?id=397759](http://bugzilla.gnome.org/show_bug.cgi?id=397759)

This is correct.I can use CBR and have no problems.But I set my gstreamer pipeline using VBR and i get the funky time lengths on the tracks.I am realy surprised that no one has fixed this yet. Is there a patch available to fix this?Your post suggests that there is?
thanks

---

### Post by Major_Kong on 2007-07-13
Yes i was also very surprised... but at least a possible fix is now avaliable. 

Well, you'll have to recompile from source and change a 418 to a 417 - it looks like this was the problem.

Go to the console and type:

apt-get source gstreamer0.10-plugins-bad         (will download the source files)
dpkg-source -x "name of the dsc file"                 (will extract the files and make some changes)

Now in the source directory find gst/xingheader/gstxingmux.c , open it and change:

-static const int XING_FRAME_SIZE = 418;

to

+static const int XING_FRAME_SIZE = 417;

Save, and then using the console in the source directory type:

dpkg-buildpackage -rfakeroot  (this will compile the plugins and create the debian packages)

You just have to install the packages afterwards.

---

### Post by bennyj on 2007-07-13
> **Major_Kong said:**
> Yes i was also very surprised... but at least a possible fix is now avaliable. 

Well, you'll have to recompile from source and change a 418 to a 417 - it looks like this was the problem.

Go to the console and type:

apt-get source gstreamer0.10-plugins-bad         (will download the source files)
dpkg-source -x "name of the dsc file"                 (will extract the files and make some changes)

Now in the source directory find gst/xingheader/gstxingmux.c , open it and change:

-static const int XING_FRAME_SIZE = 418;

to

+static const int XING_FRAME_SIZE = 417;

Save, and then using the console in the source directory type:

dpkg-buildpackage -rfakeroot  (this will compile the plugins and create the debian packages)

You just have to install the packages afterwards.

After following your instructions(Thank you) I get the following errors.Do I need to install all these dev files to successfully compile this?
```
benny@benny-desktop:~/gst-plugins-bad0.10-0.10.4$ dpkg-buildpackage -rfakerootdpkg-buildpackage: source package is gst-plugins-bad0.10
dpkg-buildpackage: source version is 0.10.4-1ubuntu1
dpkg-buildpackage: source changed by Sebastien Bacher <seb128@canonical.com>
dpkg-buildpackage: host architecture i386
dpkg-buildpackage: source version without epoch 0.10.4-1ubuntu1
dpkg-checkbuilddeps: Unmet build dependencies: libgstreamer0.10-dev (>= 0.10.10.1) libgstreamer-plugins-base0.10-dev (>= 0.10.10.1) gstreamer-tools (>= 0.10.11cvs20070110) cdbs (>= 0.4.32) check gtk-doc-tools liboil0.3-dev (>= 0.3.2) libbz2-dev libmms-dev (>= 0.2) libmpcdec-dev libwavpack-dev (>= 4.32-1) libswfdec0.3-dev (>= 0.3.6) libsoundtouch1-dev libneon25-dev (>= 0.25.5) libmusicbrainz4-dev (>= 2.1.0) libasound2-dev (>= 0.9.1) libcdaudio-dev libjack0.100.0-dev (>= 0.99.10) ladspa-sdk
dpkg-buildpackage: Build dependencies/conflicts unsatisfied; aborting.
dpkg-buildpackage: (Use -d flag to override.)
benny@benny-desktop:~/gst-plugins-bad0.10-0.10.4$ 

```

---

### Post by Major_Kong on 2007-07-14
Yes, you'll have to install them. But after that it's safe and even good to remove them.

---

### Post by bennyj on 2007-07-14
> **Major_Kong said:**
> Yes, you'll have to install them. But after that it's safe and even good to remove them.

 I think That this may be a little over my head :) But thank you for your help.Hopefully soon they will get this fixed.

---

