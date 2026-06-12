---
title: "FLAC to MP3: GStreamer Error: Gstreamer encountered a general stream error"
date: 2016-04-22
forum: Multimedia Software
---

### Post by scottbomb on 2016-04-22
Running Kubuntu 14.04. I'm seeing multiple threads on this topic, some old, some new, all closed, no real answers either.

I just installed soundconverter and all I get is this error when trying to convert FLAC to MP3. Resample is checked. gstreamer1.0-libav is installed, LAME is installed. Is there something else that may be missing?

Is there another way to convert FLAC To MP3 besides soundconverter??

[Please spare me the lecture on FLAC quality... I want to make these songs MP3.]

---

### Post by QDR06VV9 on 2016-04-22
> **scottbomb said:**
> Running Kubuntu 14.04. I'm seeing multiple threads on this topic, some old, some new, all closed, no real answers either.

I just installed soundconverter and all I get is this error when trying to convert FLAC to MP3. Resample is checked. gstreamer1.0-libav is installed, LAME is installed. Is there something else that may be missing?

Is there another way to convert FLAC To MP3 besides soundconverter??

[Please spare me the lecture on FLAC quality... I want to make these songs MP3.]

No lecture from me..:D
Have you tried WinFF 
[https://launchpad.net/ubuntu/trusty/+source/winff](https://launchpad.net/ubuntu/trusty/+source/winff)
> WinFF is a graphical user interface for FFmpeg or avconv. It will convert
 almost any video file that FFmpeg or avconv will convert. WinFF does multiple
 files in multiple formats at one time. You can, for example, convert
 mpeg's, flv's, and mov's into avi's (or DVD/VCD format or MPEG or 3gp
 etc.) all at once.
 .
 This package provides a variety of preset conversion settings for
 common formats and devices. These presets are intended to hit the
 "sweet spot" for each individual codec. They have been written with a
 tip of the balance to quality.
 .
[U][B] For most presets to work, it is necessary to have the unstripped version
 of the libavcodec package, which can be obtained by installing
 libavcodec-extra as suggested by this package. It might be necessary
 to enable additional repositories to find that package.[/B][/U]

Kind regards

---

### Post by mc4man on 2016-04-23
Soundconverter in 14.04 does not use gstreamer1.0*, it uses gstreamer0.10
Whether the ffmpeg plugin is needed to do flac > mp3 I can't say atm as only have 16.04 avail. (could ck. tonight

If it needs the ffmpeg plugin you can get here - 
[https://launchpad.net/~mc3man/+archive/ubuntu/gstffmpeg-keep](https://launchpad.net/~mc3man/+archive/ubuntu/gstffmpeg-keep)

Otherwise many ways, one is you could use a simple script to decompress with flac & pipe to lame using the flac tags to re-tag with id3v2 or as mentioned winff may work.
If you want a script & short instructions, ask.

---

### Post by QDR06VV9 on 2016-04-23
Yes mc4man's scripts are very nice I have saved a lot of his scripts and what I have learned from him.
The WinFF is also a nice GUI for that.
I have included a screen shot of a conversion from Flac to MP3 and dose it very fast... well at least for me.
Kind Regards

---

### Post by speartip on 2016-04-24
If you're running Kubuntu, soundKonverter with a "K" is probably your best choice. Make sure you have the kubuntu-restricted-extras package installed as well, & as mentioned the mc3man multimedia ppa is well worth adding. Tested here & no problems converting flac to mp3.

---

### Post by scottbomb on 2016-04-26
SoundKonverter works perfectly, thank you!

---

