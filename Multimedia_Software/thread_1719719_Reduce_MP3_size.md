---
title: "Reduce MP3 size"
date: 2011-04-02
forum: Multimedia Software
---

### Post by garwoon on 2011-04-02
Hi

I am a newby and want a bit of help.

I have come from a windows background and within Windows Media player, when you move files to either a Media player or burn them to a MP3 CDRom, there is the option for media player to change the bit rate and reduce the files size on the fly. What is the best way to do the same thing in Ubuntu, is there an app that will do this for me ?

I have tried some conversion apps but they can get complicated and make the process long winded.

Any thoughts ?

Nigel:

---

### Post by Joe of loath on 2011-04-02
I am also looking for a similar solution. Rhythmbox and Banshee can do it, but only converts formats the player can't play.

---

### Post by An Sanct on 2011-04-02
Try using VLC and "Save as".

PS. Downsizing mp3 makes them low quality, IMHO I see no reason to do that.

---

### Post by Jose Catre-Vandis on 2011-04-02
```
ffmpeg -i old.mp3 -acodec libmp3lame -ac 2 -ab 64k -ar 44100 new.mp3
```

Change 64K to your preferred bitrate, e.g. 128K 192K.

You can easily script this for a bunch of files:

```
#!/bin/bash

#resize mp3

FILES="*.mp3"

for F in $FILES

do
newname=`basename "$F" -new.mp3`
echo $newname
ffmpeg -i "$F" -acodec libmp3lame -ac 2 -ab 64k -ar 44100 "$newname.mp3"

done
```

---

### Post by garwoon on 2011-04-10
Great, thanks for the replies that has sorted that.

Nigel

---

### Post by FakeOutdoorsman on 2011-04-10
Note that FFmpeg from the repository does not have the MP3 encoder enabled by default, but it's an easy fix:

[HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoders in FFmpeg](http://ubuntuforums.org/showthread.php?t=1117283)

---

### Post by Rytron on 2011-05-21
Excellent code there **[COLOR="DarkGreen"]Jose Catre-Vandis[/COLOR]**. Thank you.

---

### Post by Swagman on 2011-05-21
I'm trying to do the opposite... boost Sound Juicer default Mp3 up.

I've made a new field and copied over the command 

```
audio/x-raw-int,rate=44100,channels=2 ! lamemp3enc name=enc target=0 quality=6 ! xingmux ! id3v2mux
```

Boosting the **quality=6** to 8

Although when I check the files properties it still seems a bit low, but then my system always seems to report wrong Mp3 bitrate

---

### Post by careerspk on 2011-05-21
There are lot of alternatives available against Media Player you can try them.

---

