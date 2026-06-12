---
title: "VLC stream capturing and Audacity"
date: 2012-03-16
forum: Multimedia Software
---

### Post by linuxhippy on 2012-03-16
I am running XUbuntu 11.10 64 bit and captured a streaming audio file which should have been saved as an ogg vorbis file. VLC and MPlayer can both play the file. MPlayer says it is using the mpeg2/4 codec (not ogg). The problem is that I want to edit the stream. Audacity won't open the file properly (it opens it as 30 seconds of silence) and when I try to import the file that doesn't work either.

So, any ideas how I could edit this file?


Here is the full output from mplayer so you can see what codec worked for audio:

mplayer: Symbol `ff_codec_bmp_tags' has different size in shared object, consider re-linking
MPlayer 1.0rc4-4.5.2 (C) 2000-2010 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing music.
libavformat file format detected.
[aac @ 0x9c3d4f0]channel element 1.0 is not allocated
[aac @ 0x9c3d4f0]More than one AAC RDB per ADTS frame is not implemented. Update your FFmpeg version to the newest one from SVN. If the problem still occurs, it means that your file has a feature which has not been implemented.
[aac @ 0x9c3d4f0]Error decoding AAC frame header.
[aac @ 0x9c3d4f0]channel element 0.14 is not allocated
[aac @ 0x9c3d4f0]channel element 2.6 is not allocated
[aac @ 0x9c3d4f0]channel element 1.5 is not allocated
[aac @ 0x9c3d4f0]More than one AAC RDB per ADTS frame is not implemented. Update your FFmpeg version to the newest one from SVN. If the problem still occurs, it means that your file has a feature which has not been implemented.
[aac @ 0x9c3d4f0]Error decoding AAC frame header.
[aac @ 0x9c3d4f0]Duplicate channel tag found, attempting to remap.
[aac @ 0x9c3d4f0]channel element 0.0 is not allocated
[aac @ 0x9c3d4f0]channel element 3.3 is not allocated
[aac @ 0x9c3d4f0]Reserved bit set.
[aac @ 0x9c3d4f0]More than one AAC RDB per ADTS frame is not implemented. Update your FFmpeg version to the newest one from SVN. If the problem still occurs, it means that your file has a feature which has not been implemented.
[aac @ 0x9c3d4f0]Error decoding AAC frame header.
[aac @ 0x9c3d4f0]channel element 2.1 is not allocated
[ogg @ 0x9c2c610]max_analyze_duration reached
[lavf] stream 0: audio (aac), -aid 0
==========================================================================
Opening audio decoder: [faad] AAC (MPEG2/4 Advanced Audio Coding)
AUDIO: 44100 Hz, 2 ch, s16le, 21.5 kbit/1.52% (ratio: 2686->176400)
Selected audio codec: [faad] afm: faad (FAAD AAC (MPEG-2/MPEG-4 Audio))
==========================================================================
AO: [pulse] 44100Hz 2ch s16le (2 bytes per sample)

---

### Post by ron999 on 2012-03-16
> **linuxhippy said:**
> The problem is that I want to edit the stream. Audacity won't open the file properly (it opens it as 30 seconds of silence) and when I try to import the file that doesn't work either.

So, any ideas how I could edit this file?

==========================================================================
Opening audio decoder: [faad] AAC (MPEG2/4 Advanced Audio Coding)


Hi
That file contains an aac track.
Maybe Audacity will accept it if you rename it :-
filename.**m4a**
or
filename.**mp4**

If not, convert it to wav then import it into Audacity.

---

### Post by shantiq on 2012-03-16
if you want to you can use commandline sox

**to cut sections**


> sox filename.ogg  -C 10 -V2 part1.ogg  --show-progress trim  0   02:00 && sox  filename.ogg  -C 10 -V2 part2.ogg  --show-progress trim 02:00 11:11

-V is for verbose   goes 1 to 6
-C 10 is for ogg bitrate of 499k  -C 5 for example give 160 kb   if you remove -C  the default will give you 112kb


**to cut sections and add effects to second section**


> sox filename.ogg  -C 10 -V6 part1.ogg  --show-progress trim  0   02:00 && sox  filename.ogg  -C 10 -V6 morevolumeandreverb.ogg  --show-progress trim 00:01:00 00:03:11  [COLOR="Red"]**gain  +10  reverb +10 **[/COLOR] CONVERT WITH SOX WITH EFFECTS [added at the end of command]


many more effects available

```
sox --help
```   probably best to google for more detailed instructions on effects

---

### Post by shantiq on 2012-03-16
**sorry ** did not see it was not an ogg i leave the info there in case or other use

also just tried an aac renamed it ogg and audacity did not apparently mind so ??

---

### Post by linuxhippy on 2012-03-16
got it by using mplayer to convert the file to a wav file and then edit in audacity.  Here's the command:

mplayer -ao pcm inputfile.m4a -ao pcm:file="outfile.wav"

---

### Post by BicyclerBoy on 2012-03-16
If you really want to know what files contain use:
mediainfo

VLC/mplayer etc sometimes have quirky names/abbreviations that may not actually be wrong but can be misleading.

Your file could have been latm aac which is supported by libfaad but not by old versions of ffmpeg/libav.

---

