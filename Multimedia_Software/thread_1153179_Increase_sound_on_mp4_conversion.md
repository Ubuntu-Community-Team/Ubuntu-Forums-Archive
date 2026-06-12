---
title: "Increase sound on mp4 conversion"
date: 2009-05-08
forum: Multimedia Software
---

### Post by Voorhees1979 on 2009-05-08
Hi all

I have a few mp4's on my HD that I play on my PSP. We all know the PSP isnt great for its volume, is there away to boost the volume of the mp4's with some kind of conversion program? Just to try to make it a little bit louder from the output?

I have tried PSPVC, Handbrake, Avidemux

Many Thanks

---

### Post by Kareeser on 2009-05-08
Have you tried Audacity?

Always remember the rule: Garbage in, garbage out.

If you have a low volume mp4, you can't make it louder without introducing some noise.

---

### Post by FakeOutdoorsman on 2009-05-08
Looks like FFmpeg can increase the volume (assuming this file contains video as well):
```
$ ffmpeg -h | grep volume
-vol volume         change audio volume (256=normal)
$ ffmpeg -i input.mp4 -vn -vol 300 audio.mp4
$ ffmpeg -i input.mp4 -i audio.mp4 -map 0:0 -map 1:0 -acodec copy -vcodec copy newoutput.mp4
```
You can also try sox:
```
$ ffmpeg -i input.mp4 ffmpegoutput.wav
$ sox -h | grep volume
-v|--volume FACTOR       Input file volume adjustment factor (real number)
$ sox -v 1.5 ffmpegoutput.wav soxoutput.wav
$ ffmpeg -i input.mp4 -i soxoutput.wav -map 0:0 -map 1:0 -acodec libfaac -ab 96k -vcodec copy newoutput.mp4

```

---

### Post by andrew.46 on 2009-05-08
Hi FakeOutdoorsman,

> **FakeOutdoorsman said:**
> 
You can also try sox:
```
$ ffmpeg -i input.mp4 ffmpegoutput.wav
$ sox -h | grep volume
-v|--volume FACTOR       Input file volume adjustment factor (real number)
$ sox -v 1.5 ffmpegoutput.wav soxoutput.wav
$ ffmpeg -i input.mp4 -i soxoutput.wav -map 0:0 -map 1:0 -acodec libfaac -ab 96k -vcodec copy newoutput.mp4

```

The newest version of SoX:

```

andrew@skamandros~$ sox --version
sox: SoX v14.1.0

```

has a very nice feature that will calculate the greatest possible volume increase that can be made *without introducing distortion*. An interesting set of stats can be generated including the required volume number as follows:

```

andrew@skamandros~/music/ftgws$ **[COLOR="Red"]sox ftgws.wav -n stat[/COLOR]**
Samples read:         633503744
Length (seconds):   7182.582132
Scaled by:         2147483647.0
Maximum amplitude:     0.427795
Minimum amplitude:    -0.479950
Midline amplitude:    -0.026077
Mean    norm:          0.028307
Mean    amplitude:    -0.000001
RMS     amplitude:     0.042574
Maximum delta:         0.568573
Minimum delta:         0.000000
Mean    delta:         0.032071
RMS     delta:         0.047818
Rough   frequency:         7883
**[COLOR="Red"]Volume adjustment:        2.084[/COLOR]**

```

and the volume increased using '-v 2.084' using the standard SoX syntax. I note the [online documentation]("http://sox.sourceforge.net/sox.html") speaks of a neater 'one-liner' for pcm files:

```
sox infile outfile vol `sox infile -n stat -v 2>&1`
```

which I have not experimented with.

Andrew

---

### Post by FakeOutdoorsman on 2009-05-11
> **andrew.46 said:**
> The newest version of SoX has a very nice feature that will calculate the greatest possible volume increase that can be made *without introducing distortion*.
...


That's good to know.  Thanks, Andrew.

---

### Post by Halfling Rogue on 2010-08-06
Just used Sox with the instructions here to increase the volume of a really quiet sound recording. Worked like a charm. Thanks!

---

### Post by helpdeskdan on 2010-08-15
Once again, I find myself thanking andrew.46 for posting instructions!

---

### Post by FakeOutdoorsman on 2010-08-15
I forgot to mention *normalize-audio*. It accepts .wav and .mp3 as inputs. Example:
```
$ normalize-audio audio.mp3 
Computing levels...
 audio.mp3         100% done, ETA 00:00:00 (batch 100% done, ETA 00:00:00) 
Applying adjustment of -7.51dB to audio.mp3...
 audio.mp3         100% done, ETA 00:00:00 (batch 100% done, ETA 00:00:00) 
```

---

### Post by andrew.46 on 2010-09-16
Hi helpdeskdan,

> **helpdeskdan said:**
> Once again, I find myself thanking andrew.46 for posting instructions!

My pleasure :). I have always meant to spend a bit more time with SoX, it is one of those programs that rewards some solid reading of the man pages and then a great deal of experimentation. Not a great deal in the way of online guides and discussions available either which is a great shame.

One limitation that people bump into very quickly under Ubuntu is that SoX has not been compiled against lame so mp3s will be read but not written.

Andrew

---

### Post by SethNewton on 2012-04-17
Andrew.46 was right... I did run into libmp3lame issues right away.  Luckily for us 1.5 years later though... libmp3lame seems to be compiled in sox now, which is really nice.  I had to increase the sound of a bunch of mp4s, so I wrote a script to do so.   I offer no warranty on this script and won't have time to answer questions about it, but when it's finished, all of your updated .mp4 files should be in a folder called "finished-audio-increase".  I just tested this and it worked for me.  

1) Make sure sox, ffmpeg are installed.  
2) Copy this into a file called "IncreaseAudio.sh" (or whatever you want)
    NOTE: This script expects to be in the same directory as all of the *.mp4 files.
3) chmod 700 IncreaseAudio.sh
4) ./IncreaseAudio.sh

```

#! /bin/bash

FILES=`ls *.mp4`

# Temporary folder to put the audio files
if [ ! -d "audio/increased" ] ; then
  mkdir -p "audio/increased"
fi

# Temporary folder to put the video files
if [ ! -d "finished-audio-increase" ] ; then
  mkdir "finished-audio-increase"
fi

for file in $FILES
do

  #Create the audio file if it doesn't exist
  FILENAME_NO_EXT=`echo $file | sed 's/.mp4//g'`
  if [ ! -f "audio/"$FILENAME_NO_EXT".wav" ] ; then
    ffmpeg -i $file audio/$FILENAME_NO_EXT".wav"
  else
    echo "Audio file already exists!... using existing file"
  fi

  #Increase the audio layer to maximum
  sox "audio/"$FILENAME_NO_EXT".wav" "audio/increased/"$FILENAME_NO_EXT".wav" vol `sox "audio/"$FILENAME_NO_EXT".wav" -n stat -v 2>&1`

  #Now put the audio layer back into the movie.
  ffmpeg -i $file -i "audio/increased/"$FILENAME_NO_EXT".wav" -map 0:0 -map 1:0 -acodec libmp3lame -ab 96k -vcodec copy "finished-audio-increase/"$file

done

```</paste>

Hope that helps someone!

---

### Post by bearblack on 2012-10-27
I use ddvideo video to mp4gain,it's a good mp4 converter,it can increase or decrease volume from 75db to 105db.support mp3gain,mp4gain.

---

### Post by wildmanne39 on 2012-10-27
Thanks for sharing and please do not post in threads that have not had activity for a year or longer, since this is an old thread it has been closed.

---

