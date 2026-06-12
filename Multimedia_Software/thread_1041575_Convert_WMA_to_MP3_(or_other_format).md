---
title: "Convert WMA to MP3 (or other format)"
date: 2009-01-16
forum: Multimedia Software
---

### Post by terry@softreq.com on 2009-01-16
I've downloaded a WMA file from my voice recorder. 

I'd like to edit it using either software in Ubuntu or via Garage Band.

Either way, I'd like to find some software that can either a) edit WMA or b) convert it to something like MP3 so that it's generally easily editable. 

Recommendations?

---

### Post by logos34 on 2009-01-16
ffmpeg

---

### Post by logos34 on 2009-01-16
> **logos34 said:**
> ffmpeg

i.e. 

ffmpeg -i file.wma -acodec mp3 -ab 128 file.mp3

(--> mp3 @ 128kbps CBR joint stereo)

---

### Post by FakeOutdoorsman on 2009-01-16
> **logos34 said:**
> i.e. 

ffmpeg -i file.wma -acodec mp3 -ab 128 file.mp3

(--> mp3 @ 128kbps CBR joint stereo)

This command is telling ffmpeg to encode at 128 bits/s.  You need to add a "k".  Also, if you are using Intrepid, you will need to install the package **libavcodec-unstripped-51** (or the ubuntu-restricted-extras metapackage) to use restricted encoders such as libmp3lame (-acodec mp3 is not a correct option):
```
ffmpeg -i file.wma -acodec libmp3lame -ab 128k file.mp3
```

---

### Post by logos34 on 2009-01-16
> **FakeOutdoorsman said:**
> This command is telling ffmpeg to encode at 128 bits/s.  You need to add a "k".  Also, if you are using Intrepid, you will need to install the package **libavcodec-unstripped-51** (or the ubuntu-restricted-extras metapackage) to use restricted encoders such as libmp3lame (-acodec mp3 is not a correct option):
```
ffmpeg -i file.wma -acodec libmp3lame -ab 128k file.mp3
```

yes, I left out the 'k' (in which case it reverts to default 128k)

actually, it does work:
> 
ffmpeg -i file.wma -acodec mp3 -ab 160k file.mp3

results in file @ 160kbps CBR, joint stereo (writing library: LAME3.97)

But apparently the issue involves more than just ubuntu-restricted-extras: the ubuntu .deb pkg in the repos is not compiled with mp3 support (wtf?), so I'm compiling mine from source and reinstalling following [this howto]("http://ubuntuforums.org/archive/index.php/t-815223.html").  Hope that gets it working like it should...

---

### Post by logos34 on 2009-01-17
ok, that worked (except had to drop configure option '--enable-liba52' - ??) 

So if you compile it yourself you can get lame mp3 **VBR** support too:
> 
ffmpeg -i file.wma -acodec libmp3lame -a**q** 2 file.mp3

--> mp3 @ ~192k/vbr-new V2 setting 

General #0
Complete name                : file.mp3
Format                       : MPA1L3
File size                    : 5.34 MiB
Writing library              : [COLOR="Red"]Lavf52.23.1[/COLOR]

Audio #0
Codec                        : MPEG-1 Audio layer 3
Codec profile                : Joint stereo
Bit rate mode                : [COLOR="Red"]VBR[/COLOR]
Channel(s)                   : 2 channels
Sampling rate                : 44.1 KHz
Resolution                   : 16 bits
Writing library              : [COLOR="Red"]LAME3.97[/COLOR]

---

### Post by mc4man on 2009-01-17
Actually in this case you don't need to specify an acodec at all, ffmpeg will work off of the format ext.

If it's a voice recording, I'd probably just do a quick run thru to ck. the bitrate, sample rate, mono or stereo of the source, then adjust as needed. (or ck. in something like mediainfo.
With no added parameters ffmpeg will use the same # of channels, samplerate and encode at 64k

> doug@doug-desktop:~$ ffmpeg -i foo.wma foo.mp3
................clipped
  built on Jan  8 2009 19:23:32, gcc: 4.3.2
Input #0, asf, from 'foo.wma':
  Duration: 00:07:58.90, start: 3.100000, bitrate: 277 kb/s
    Stream #0.0: Audio: wmav2, 44100 Hz, stereo, s16, 192 kb/s
Output #0, mp3, to 'foo.mp3':
    Stream #0.0: Audio: libmp3lame, 44100 Hz, stereo, s16, 64 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
Press [q] to stop encoding
...........



Note : all the commands shown presume your source file is loose in your home directory, if it's in a folder then cd to it first.

---

### Post by logos34 on 2009-01-17
hi mc4man,

Something like this came up recently in another thread (where you posted)...you know a ton more about audio than I do...why is it that they disabled mp3 in the ffmpeg deb?  Incomprehensible to me...

---

### Post by mc4man on 2009-01-17
> why is it that they disabled mp3 in the ffmpeg deb?
At the risk of off topic, from the ubuntu ffmpeg source

> Summary of the patent issues with ffmpeg
========================================

   The only patents related to ffmpeg which seem to be enforced against open
source software cover the following codec technologies and file formats:

   * MP3 encoding
   * AAC encoding
   * the ASF file format

   I did not activate MP3 encoding (through LAME) in libavcodec, nor AAC
encoding (through FAAC). However, since I have found no real enforcement
of the mysterious ASF file format patents, I did not deactivate ASF support in
libavformat. See more details in the patents.txt file.

It's actually a very long readme, if you want to ck. it out (for 8.10 or disable medibuntu in 8.04
apt-get source ffmpeg-debian

I tried your -aq, it works well as long as libmp3lame is available, did show a strange timeline in amarok..?

Remember I mentioned about the repo change in 8.10 - it's actually working out quite well, only one minor function lost (aac playback in gnome players, irrelevant here.

---

### Post by stderr on 2009-01-17
You could try a script like this. I knocked a few of them up for those times you just need a quick conversion. I'm sure they could be improved though. You will require 'mplayer' and 'lame' to convert to mp3.

```
#!/bin/bash
wmafile=$1
wavfile=$(echo $wmafile | sed -e s/wma$/wav/)
mp3file=$(echo $wmafile | sed -e s/wma$/mp3/)

# Converts the WMA to a WAV in same directory
mplayer -ao pcm:file="$wavfile" "$wmafile" 
# Encodes the WAV as MP3 in same directory
lame "$wavfile" "$mp3file"
# Removes the leftover WAV
rm "$wavfile"

```

You can then save that as e.g. convertWMAtoMP3, give it executable permissions (chmod +x convertWMAtoMP3) and ./convertWMAtoMP3 /path/to/file.wma

---

### Post by logos34 on 2009-01-17
> **mc4man said:**
> At the risk of off topic, from the ubuntu ffmpeg source

...

Remember I mentioned about the repo change in 8.10 - it's actually working out quite well, only one minor function lost (aac playback in gnome players, irrelevant here.

oh, patent issues--i should have known.  No wonder.

---

