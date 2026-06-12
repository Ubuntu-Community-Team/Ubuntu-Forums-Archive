---
title: "How to speed up mp3 files"
date: 2009-09-06
forum: Multimedia Software
---

### Post by goodrench on 2009-09-06
I have been looking for a way to speed up some mp3 files. I have a list of files to listen to and they could be sped up quite a bit and still be audible. I used to use sox to do this but now that I have upgraded to karmic, sox does not support mp3 files anymore.
Is there another program that will do this. I don't care if it is command line or gui.

---

### Post by ad_267 on 2009-09-06
There should be mp3 support for sox in Karmic: [http://packages.ubuntu.com/karmic/libsox-fmt-mp3](http://packages.ubuntu.com/karmic/libsox-fmt-mp3)

```
sudo apt-get install libsox-fmt-mp3
```
or
```
sudo apt-get install libsox-fmt-all
```

---

### Post by goodrench on 2009-09-06
```
sudo apt-get install libsox-fmt-all
```
That did it. I should have looked harder.
Thanks ad_267.

I used sox in a nautilus-script to speed up podcasts that I listen to. Some of them are just too long.

If anyone wants to use it, here is the script.
Just drop it into ~/.gnome2/nautilus-scripts/ and chmod +x to make it executable.

Just alter the settings as you need to.

```
#! /bin/bash

# this script will speed up audio using sox.
# speed up is 1.5  and pitch is lowered by -700 to try to keep the original voice
# This will keep the original and put the new one in a new folder called audio

# Check for and create audio directory if necessary

if test ! -d audio
      then
      mkdir audio
fi
input=$1
terminator -e "sox --show-progress ${input} audio/${input} speed 1.5 pitch -700"


```

---

### Post by andrew.46 on 2009-09-07
Hi goodrench,

You might be interested to have a look the scaletempo audio filter from the svn MPlayer which offers the ability to dynamically alter speed without altering pitch. It is tip no.1 on this page:

Top 10 Tricks and Tips for the svn MPlayer
[http://ubuntuforums.org/showthread.php?t=1154431](http://ubuntuforums.org/showthread.php?t=1154431)

All the best,

Andrew

---

### Post by goodrench on 2009-09-07
Can mencoder do this and output to a new file? I tried passing these options to mencoder and it did not work.
I did use mplayer with ```
> song.mp3
``` but it works in real time with the song playback. 
The reason I am doing this is for my mp3 player. I will not be listening to them on my pc. Otherwise the mplayer solution works very well.

---

### Post by andrew.46 on 2009-09-07
Hi goodrench,

> **goodrench said:**
> The reason I am doing this is for my mp3 player. I will not be listening to them on my pc. Otherwise the mplayer solution works very well.

I am not aware of any easy way to save the scaletempo changes to a new file, sorry! But I shall be storing your SoX script away for my own personal use... thanks for making it available :-).

Andrew

---

### Post by goodrench on 2009-09-25
```
libsox-fmt-mp3
```
is broken for me now in karmic, on both my desktop and my laptop.
Sox tells me that it does not support mp3 format.
Is there a way to trick sox?

---

### Post by sgosnell on 2009-09-26
Have you tried Audacity?  I'm not on Karmic, but it works well in Jaunty.

---

### Post by Jose Catre-Vandis on 2009-09-26
You can do this using Andrew.46's tips 1 and 3 :)

Increase playback speed and output to wav using mplayer, and then convert back to mp3 using ffmpeg

1st Run - change playback speed and convert to wav
```
mplayer -af scaletempo -speed 1.5 input.mp3 -vc null -vo null -ao pcm:fast:waveheader:file=output.wav
```
2nd Run - convert back to mp3 using ffmpeg
```
ffmpeg -i output.wav -acodec libmp3lame -ab 96k output.mp3
```

I used 96k bitrate for final output which would be good enough for speech, but you can use 128k or 192k instead.

These commands could be thrown together in a script to make the process easier, or in order to act on multiple input files
```
#!/bin/bash
# mp3speed.sh

#Script to speed up playback

####LOOP FOR EACH SELECTED FILE#######

FILES="*.mp3"

for f in $FILES

do

AR=96k
SP=1.5

echo Encoding $f


mplayer -af scaletempo -speed $SP $f -vc null -vo null -ao pcm:fast:waveheader:file=$f.wav

ffmpeg -i $f.wav -acodec libmp3lame -ab $AR $f.mp4
(Note output to mp4 extension to prevent looping as output is in the same directory!)

done
```

Enjoy :)

---

### Post by goodrench on 2009-09-26
> **sgosnell said:**
> Have you tried Audacity?  I'm not on Karmic, but it works well in Jaunty.

No. I haven't. Do you know the command line options so I can script it?

---

### Post by sgosnell on 2009-09-27
No, I've never tried scripting it.  I don't use it a lot, mostly for converting files and a little editing.

---

