---
title: "Convert m2p Video"
date: 2014-10-28
forum: Multimedia Software
---

### Post by Quarkrad on 2014-10-28
Newbie posting here(!)   I have a number of family videos that a long time ago, during the conversion to DVD, I landed up with m2p files.  At the moment most players do not play the audio properly - it's just loud clicks.  However, I can play the video, and audio, ok using smplayer.  I am not familiar with smplayer but I think(?) it uses a *dvdpcm - uncompressed* codec to output the audio.  I have read on the web that a lot of players do not support m2p audio and that it is better to convert the audio to AC3.  Assuming my video is called test.m2p  is there a way of converting the audio part of my file to AC3?  Many thanks.

---

### Post by andrew.46 on 2014-10-28
A modern FFmpeg can decode pcm_dvd audio:

```

 A....D pcm_dvd              PCM signed 16|20|24-bit big-endian for DVD media

```

which is why SMPlayer and other media players that use libavcodec can playback your files. (A=Audio and D=Decode)  It would be interesting if you could run an application like *mediainfo* against your file?

---

### Post by Quarkrad on 2014-10-29
Andrew - thank you for your help.  However, I'm afraid I need a little/more help with your code above - sorry.  Assuming my file is called test.m2p what do I do re the terminal and your command?

---

### Post by Quarkrad on 2014-10-29
I installed mediainfo and got the following output against my file:

[B]General
Complete name                            : /home/dad/Desktop/test/test.m2p
Format                                   : MPEG-PS
File size                                : 290 MiB
Duration                                 : 5mn 15s
Overall bit rate                         : 7 730 Kbps

Video
ID                                       : 224 (0xE0)
Format                                   : MPEG Video
Format version                           : Version 2
Format profile                           : Main@Main
Format settings, BVOP                    : Yes
Format settings, Matrix                  : Custom
Format settings, GOP                     : M=3, N=15
Duration                                 : 5mn 15s
Bit rate                                 : 6 000 Kbps
Width                                    : 720 pixels
Height                                   : 576 pixels
Display aspect ratio                     : 4:3
Frame rate                               : 25.000 fps
Standard                                 : PAL
Color space                              : YUV
Chroma subsampling                       : 4:2:0
Bit depth                                : 8 bits
Scan type                                : Interlaced
Scan order                               : Bottom Field First
Compression mode                         : Lossy
Bits/(Pixel*Frame)                       : 0.579
Time code of first frame                 : 00:00:00:00
Time code source                         : Group of pictures header
Stream size                              : 227 MiB (78%)

Audio
ID                                       : 189 (0xBD)-160 (0xA0)
Format                                   : PCM
Format settings, Endianness              : Big
Format settings, Sign                    : Signed
Muxing mode                              : DVD-Video
Duration                                 : 5mn 15s
Bit rate mode                            : Constant
Bit rate                                 : 1 536 Kbps
Channel(s)                               : 2 channels
Sampling rate                            : 48.0 KHz
Bit depth                                : 16 bits
Stream size                              : 57.7 MiB (20%)[/B]

I intend to keep this file 'as is' so in the future I can use it (and others) to create a DVD.  However, I need to do a 'one off' with this specific file to be able to send it to family members to play on their (various OSs) PCs so I am happy to change it to a general format that they will be able to play.  This is where I 'fall off the cliff' - not knowing how/the best conversion to make.   (note - I will make this file a **lot** smaller and post it on some like Dropbox for them to download).

---

### Post by andrew.46 on 2014-10-29
Perhaps try with avconv which is command line application but might be good for at least a test? Install it with:

```

sudo apt-get install libav-tools libavcodec-extra-53

```

and perhaps as an initial experiment change the audio to mp3, the video to h.264 and the container to mp4. Copy the entire code block below into a terminal window, press enter and cross your fingers:

```

avconv -i /home/dad/Desktop/test/test.m2p \
          -c:v libx264 -preset slow -crf 22 \
          -c:a libmp3lame -q:a 4 \
          /home/dad/Desktop/test/another_test.mp4

```

If all goes well this should produce a much smaller file with decent quality and better portability for your family members. There are various gui options that no doubt others can help out with, I am more of a command line sort of guy :). Let me know how this turns out for you, command line options can vary a little bit and I have tested this sort of syntax using FFmpeg rather than avconv...

---

### Post by Quarkrad on 2014-10-29
The sound is still not right but the file has changed from 304.5mb  .m2p  to 164.7mb  .mp4    I have attached two files - a text output of the terminal and an mp3 file giving you some idea of what I hear.  (I have had to convert the mp3 file to zip - not allowed to attach mp3 files.  Also - in the text doc I have had to delete many lines of[B] [pcm_s16be @ 0x2441e80] Invalid PCM packet, data has size 3 but at least a size of 4 was expected
Error while decoding stream #0:[/B]1  inorder to get the file size to a size that I could attach).

---

### Post by andrew.46 on 2014-10-29
That sound was pretty bad at this end :). Did the video look ok?

**Edit**: It is an outside chance but we could try to force the correct decoder, I suspect this will not work:

```

avconv -**[COLOR="#FF0000"]c:a pcm_dvd[/COLOR]** -i /home/dad/Desktop/test/test.m2p \
          -c:v libx264 -preset slow -crf 22 \
          -c:a libmp3lame -q:a 4 \
          /home/dad/Desktop/test/yet_another_test.mp4

```

Interestingly a modern FFmpeg has no such trouble with this audio codec. For those who are interested here is a sample:

```
wget samples.mplayerhq.hu/archive/audio/pcm_dvd/mpeg+mpeg2video+pcm_dvd+dvdsub+pcm_dvd.mpeg
```

which converts cleanly utilising the* correct* decoder...

---

### Post by Rob Sayer on 2014-10-29
Well, I've never tried to convert that type of file but it's mpeg-2 video and raw WAV audio.  That doesn't sound too exotic.  Two linux converters I'd try are avidemux and handbrake, which are both in the tested ubuntu repos.  I'd avoid 3rd party untested ppa's for encoders because they may mess with your codec libraries.  I avoid untrusted ppa's anyway unless I can't avoid it.

Whether you want to convert the audio to ac3 depends upon what output video format you want.  For h.264, generally used in .mkv or .mp4 files, it's OK.  I'd probably choose aac though.  For mpeg-4 ASP or mpeg-4 Visual I'd convert to mp3.

What video format you want depends upon what type of device the recipients are using.  Xvid or h.264 are generally best.   A lot of handheld devices can't play high profile video.

According to your mediainfo report the video is interlaced.  That's OK for old TVs with a CRT but will look like crap on a digital display.  You'll want to use a deinterlacing filter.  Handbrake and avidemux support this ... any useable converter does.

Sorry to make this more complex, but digital video is complex, and you can't simplify it that much.  The people who designed all those video formats were professionals and those standards were written for professionals.  They didn't have average users like you and me backing up their dvds in mind.

There are "one click" converters available for windows but they're useless (I don't know of any for linux but I wouldn't be interested).  As usual, the way they make them that simple is to omit almost all the settings.  Which ultimately makes them harder to use than more powerful programs.  Avidemux and handbrake have the best balance of power and ease of use I've seen in video encoders.  They should work.  I hope.

---

### Post by Quarkrad on 2014-10-30
I did not have much luck with the second command - the video was OK (as was the first conversion) but the audio was the same (bad).  In the attached teminal output I got many lines of [B]Error while decoding stream #0:1
[pcm_dvd @ 0x1f71d60] codec ids mismatch[/B].  However, I did have some success with avidemux - I got an output with good video and audio.  I will now play with various options to get the best option.  Many thanks for your help.

---

