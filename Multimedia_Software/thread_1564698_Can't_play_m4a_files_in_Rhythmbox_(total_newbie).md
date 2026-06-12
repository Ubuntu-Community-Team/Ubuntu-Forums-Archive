---
title: "Can't play m4a files in Rhythmbox (total newbie)"
date: 2010-08-30
forum: Multimedia Software
---

### Post by plaidling on 2010-08-30
Hiya.
I'm very very new to Ubuntu (I switched over less than a week ago.)
I'm just starting to get a feel for it, and learning about the software.  I can't get m4a files to play in Rhythmbox - it says it needs additional plugins, but I don't know where to find them.
Can anyone suggest a link for an m4a decoder plugin, or different software that can play m4a files?

---

### Post by Yellow Pasque on 2010-08-30
```
sudo apt-get install ubuntu-restricted-extras
```
or, more specifically,
```
sudo apt-get install gstreamer0.10-plugins-bad-multiverse
```

---

### Post by sti3 on 2010-09-30
I'm having a slightly different problem.  Some m4as import and play, others don't.

Specifically I'm having problems with the m4a podcasts from XlR8R.

Here is one: [http://www.xlr8r.com/podcast/2010/09/salem](http://www.xlr8r.com/podcast/2010/09/salem)

(Click Download M4A -- they don't allow direct linking)

Is it a container or codec issue?

---

### Post by mc4man on 2010-09-30
I'd say it's the format rhythmbox doesn't like, you may be able to force it to accept as a podcast, maybe not.

You should be able to play in totem, vlc would also work well and would recognize the chapter stops - see screen

Otherwise if you removed the 'video stream' the rhythmbox would play.

Ex. (dl to Downloads folder, saved new .m4a to Music folder

```
ffmpeg -i ~/Downloads/XLR8R_Podcast_Salem_2010_09_28.m4a -vn -acodec copy ~/Music/Salem_2010_09_28.m4a
```

Then rhythmbox will play as one continuous file.

=======================================================================
info> 
General
Complete name                    : /home/doug/Downloads/XLR8R_Podcast_Salem_2010_09_28.m4a
Format                           : MPEG-4
Format profile                   : Apple AAC audio with iTunes info
Codec ID                         : M4A 
File size                        : 50.1 MiB
Duration                         : 35mn 38s
Overall bit rate                 : 196 Kbps
Movie name                       : XLR8R Podcast: Salem - September 28, 2010
Album                            : XLR8R Podcast
Performer                        : Salem
Encoded date                     : 2010
Tagged date                      : UTC 2010-09-27 16:05:15
Writing application              : GarageBand 5.1
Cover                            : Yes
Comment                          : Check out XLR8R's weekly podcasts at xlr8r.com/podcast

Video
ID                               : 4
Format                           : M-JPEG
Codec ID                         : jpeg
Duration                         : 35mn 38s
Bit rate mode                    : Variable
Bit rate                         : 1 986 bps
Width                            : 300 pixels
Height                           : 300 pixels
Display aspect ratio             : 1.000
Frame rate mode                  : Variable
Frame rate                       : 0.003 fps
Minimum frame rate               : 0.001 fps
Maximum frame rate               : 0.017 fps
Bits/(Pixel*Frame)               : 7.356
Stream size                      : 566 KiB (1%)
Language                         : English
Encoded date                     : UTC 2010-09-27 22:30:37
Tagged date                      : UTC 2010-09-27 22:30:48

Audio
ID                               : 3
Format                           : AAC
Format/Info                      : Advanced Audio Codec
Format version                   : Version 4
Format profile                   : LC
Format settings, SBR             : No
Codec ID                         : 40
Duration                         : 35mn 38s
Bit rate mode                    : Constant
Bit rate                         : 192 Kbps
Channel(s)                       : 2 channels
Channel positions                : Front: L R
Sampling rate                    : 44.1 KHz
Stream size                      : 49.0 MiB (98%)
Language                         : English
Encoded date                     : UTC 2010-09-27 22:30:37
Tagged date                      : UTC 2010-09-27 16:05:15

Text #1
ID                               : 1
Format                           : Timed text
Codec ID                         : tx3g
Duration                         : 35mn 38s
Bit rate mode                    : Variable
Bit rate                         : 2 bps
Stream size                      : 405 Bytes (0%)
Language                         : English
Encoded date                     : UTC 2010-09-27 22:30:37
Tagged date                      : UTC 2010-09-27 22:30:48

Text #2
ID                               : 2
Format                           : Timed text
Codec ID                         : tx3g
Duration                         : 35mn 38s
Bit rate mode                    : Variable
Bit rate                         : 2 bps
Stream size                      : 521 Bytes (0%)
Language                         : English
Encoded date                     : UTC 2010-09-27 22:30:37
Tagged date                      : UTC 2010-09-27 22:30:48


---

