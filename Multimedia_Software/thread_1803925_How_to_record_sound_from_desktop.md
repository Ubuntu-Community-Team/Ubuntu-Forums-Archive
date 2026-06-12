---
title: "How to record sound from desktop?"
date: 2011-07-14
forum: Multimedia Software
---

### Post by orange2k on 2011-07-14
Im trying to record sound comming from firefox, but I dont seem to be able to find a right application for that purpose...

Any ideas how I could accomplish this?

Cheers...

---

### Post by An Sanct on 2011-07-14
You can record audio/video with VLC, its even simpler, if that thing from Firefox is a stream, then you can capture the whole stream with VLC.

But you can also use the default Sound Recorder, that should be already installed on your system.

command: gnome-sound-recorder

---

### Post by iiiears on 2011-07-14
Hello,

I used this link.

[http://www.youtube.com/watch?v=8o-swehxoyI](http://www.youtube.com/watch?v=8o-swehxoyI)


The next one is nerdy.
[http://wiki.oz9aec.net/index.php/High_quality_screen_capture_with_Ffmpeg](http://wiki.oz9aec.net/index.php/High_quality_screen_capture_with_Ffmpeg)

"I'm too nerdy for my shirt too nerdyy for my shirt
So nerdy it hurts
And I'm too nerdy for Milan too nerdy-y for Milan
New York and Japan" -apologies to you and Right Said Fred. 

(Maybe, i got a day off, a day too late, from my crappy job??!)
Anyway.. That link is an eleven on the nerdy scale.

Best Wishes.

---

### Post by orange2k on 2011-07-14
I just wanted to record audio, not video, so I had to use Windows to do that... :(

I wanted to record sound from Firefox, just some songs that couldn't be downloaded but played from inside Firefox...

Gnome soundrecorder didn't do the trick...

I just wonder how hard would it be to write a program that does just that: record audio thats being played on the computer...

---

### Post by jerrrys on 2011-07-14
there are many ways to do this

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=record+internet+audio&sa=Search&cof=FORID:9#911](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=record+internet+audio&sa=Search&cof=FORID:9#911)

for my own needs, i use this script

&#65279;#!/bin/bash
# Copyright 2008-2009, Kees Cook <kees@outflux.net>
#
# Records the PulseAudio monitor channel.
# [http://www.outflux.net/blog/archives/2009/04/19/recording-from-pulseaudio/](http://www.outflux.net/blog/archives/2009/04/19/recording-from-pulseaudio/)
#
#This script require sox
#sudo apt-get install sox

if [ -n "$1" ]; then
    OUTFILE="$1"
else
    TIME=$(date +%d-%b-%y_%H%M-%Z)
    OUTFILE="recording_$TIME.wav"
fi

# Get sink monitor:
MONITOR=$(pactl list | grep -A2 '^Source #' | grep 'Name: .*\.monitor$' | awk '{print $NF}' | tail -n1)

# Record it raw, and convert to a wav
echo "Recording. Ctrl-C or close window to stop"
parec -d "$MONITOR" | sox -t raw -r 44100 -sLb 16 -c 2 - "$OUTFILE"

# End of sound_cap.sh

---

### Post by ron999 on 2011-07-14
Hi
I also have problems with Gnome Sound Recorder.:(

But I can record using '**arecord**'.:)

```
sudo apt-get install alsa-utils
```

Then to record:-

```
arecord -f cd output.wav
```

It's useful to pipe the output, like this:-

```
arecord -f cd - | lame -b 128 - output1.mp3
```

```
arecord -f cd - | oggenc -q 4 - -o output1.ogg
```

```
arecord -f cd - | faac -q 100 - -o output1.m4a
```

And with FFmpeg:-

```
arecord -f cd - | ffmpeg -i - output.flac
```

```
arecord -f cd - | ffmpeg -i - -acodec libmp3lame -ab 128k output2.mp3
```
```
arecord -f cd - | ffmpeg -i - -acodec libvorbis -aq 4 output2.ogg
```
```
arecord -f cd - | ffmpeg -i - -acodec libfaac -aq 100 output2.m4a
```

---

### Post by lalitha niharika on 2011-07-14
The easiest way is, install Audacity(its a freeware) from either ubuntu software centre or synaptic or deb package.Then install pulse audio volume control.Now start recording in audacity, keep it aside.While audacity is recording Open pulse<recording<choose monitor of CM8738...that's it!!its done.
If you want to export your recordings as mp3 files, just install lame along with Audacity.

---

### Post by orange2k on 2011-07-14
> **lalitha niharika said:**
> The easiest way is, install Audacity(its a freeware) from either ubuntu software centre or synaptic or deb package.Then install pulse audio volume control.Now start recording in audacity, keep it aside.While audacity is recording Open pulse<recording<choose monitor of CM8738...that's it!!its done.
If you want to export your recordings as mp3 files, just install lame along with Audacity.

Hey, this really works, thanks...:)

The other ways to do this are way too complicated...

---

### Post by samigina on 2011-07-14
This is easiest.

Outrec ([http://outrec.sourceforge.net/](http://outrec.sourceforge.net/))

---

### Post by irv on 2011-07-14
> **orange2k said:**
> Hey, this really works, thanks...:)

The other ways to do this are way too complicated...

One Nice thing about using Audacity is you can edit the sound file after you record it. I use Audacity for pod casts and the sound system at the church. I do all the recording via Audacity because I have the PA system ported to a laptop via a analog/digital converter. It is a very user friendly program.

---

### Post by lalitha niharika on 2011-07-15
welcome:D.You can even make wonders using audacity!!you can even remove vocals from songs,..etc.Its one of the best free-wares.You can just refer online audacity guide.
[http://audacity.sourceforge.net/manual-1.2/](http://audacity.sourceforge.net/manual-1.2/)

---

### Post by shantiq on 2011-07-16
audacity with this [info]("http://ubuntuforums.org/showthread.php?t=1705651") should do it--although it can be a hit and miss experience with audacity

---

### Post by shantiq on 2011-07-16
> **ron999 said:**
> Hi
I also have problems with Gnome Sound Recorder.:(

But I can record using '**arecord**'.:)

```
sudo apt-get install alsa-utils
```

Then to record:-

```
arecord -f cd output.wav
```

It's useful to pipe the output, like this:-

```
arecord -f cd - | lame -b 128 - output1.mp3
```

```
arecord -f cd - | oggenc -q 4 - -o output1.ogg
```

```
arecord -f cd - | faac -q 100 - -o output1.m4a
```

And with FFmpeg:-

```
arecord -f cd - | ffmpeg -i - output.flac
```

```
arecord -f cd - | ffmpeg -i - -acodec libmp3lame -ab 128k output2.mp3
```
```
arecord -f cd - | ffmpeg -i - -acodec libvorbis -aq 4 output2.ogg
```
```
arecord -f cd - | ffmpeg -i - -acodec libfaac -aq 100 output2.m4a
```



thanx this works really well but you still need to **make sure it is picked up**


i find using   ```
sudo apt-get install pavucontrol

``` and 


1. bringing it up ```
pavucontrol
``` then running say 

2. ```
arecord -f cd - | lame -b 128 - output1.mp3
```

3. click on recording on pavucontrol and pick " monitor of internal analog audio stereo " ensures it is picked up
 Stop recording and start again now you have the correct sound monitoring


4. then to return to internal audio stereo when finished


**May be** useful to add  


 **[Also]("http://ubuntuforums.org/showpost.php?p=11053351&postcount=9")** same technique but using SoX instead



================================================

---

### Post by teique on 2012-12-19
> **shantiq said:**
> thanx this works really well but you still need to **make sure it is picked up**


i find using   ```
sudo apt-get install pavucontrol

``` and 


1. bringing it up ```
pavucontrol
``` then running say 

2. ```
arecord -f cd - | lame -b 128 - output1.mp3
```

3. click on recording on pavucontrol and pick " monitor of internal analog audio stereo " ensures it is picked up
 Stop recording and start again now you have the correct sound monitoring


4. then to return to internal audio stereo when finished


**May be** useful to add  


 **[Also]("http://ubuntuforums.org/showpost.php?p=11053351&postcount=9")** same technique but using SoX instead



================================================

thx!! works great on 12.04
also if you need to check if it is making any sound (like if game sound was properly initialized) we can use this:
```
arecord -d 1 -f S16_LE |sox -t .wav - -n stat 2>&1
```
and then check if "Maximum amplitude" is greater than 0.0!

---

### Post by lisati on 2012-12-19
I think the sound's too loud for this old thread, which wants to go back to sleep.

---

