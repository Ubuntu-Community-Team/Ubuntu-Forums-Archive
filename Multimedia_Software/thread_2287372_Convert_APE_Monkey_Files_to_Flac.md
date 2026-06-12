---
title: "Convert APE Monkey Files to Flac"
date: 2015-07-18
forum: Multimedia Software
---

### Post by mooreted on 2015-07-18
I upgraded Soundconverter to 2.14 but I cannot convert APE audio files. I get the following error:

"Python (v2.7) requires to install plugins to play media files of the following type: APE tag demuxer"

I have installed everything I can find online. Tried CLI scripts. I can't seem to find a way to do it.

---

### Post by mc4man on 2015-07-19
Install the gstreamer plugin from here, then soundconverter should do .ape
(assuming you mean sc-2.1.4 or sc-2.1.5, never seen 2.14
[https://launchpad.net/~mc3man/+archive/ubuntu/gstffmpeg-keep](https://launchpad.net/~mc3man/+archive/ubuntu/gstffmpeg-keep)

---

### Post by mooreted on 2015-07-19
Well, getting closer. Now I get:

"GSstremer encountered a general stream error."

At least that helps me look up more information.

Command-line reports the following:

Error: <b>GStreamer Error:</b>
GStreamer encountered a general stream error.
<i>(King Crimson - Discipline.ape)</i>
Queue done in 1.630s (1 tasks)
Queue start: 1 tasks, 8 thread(s).

---

### Post by PhilGil on 2015-07-19
I haven't had good luck with APE files and Sound Converter, but ffmpeg always worked for me.

```
$ ffmpeg -i input_file_name.ape output_file_name.flac
```

---

### Post by mc4man on 2015-07-19
Can assure you works fine here in both 14.04 & 15.04 (sc- 2.0.4 & 2.1.5 respectively.
How did you install sc in whatever release of Ubuntu you are using?
Maybe try deleting this folder,  ~/.gstreamer-0.10

---

### Post by mooreted on 2015-07-19
Running Ubuntu 14.04 x64.

I installed Soundconverter 2.1.4 from the following source:

[http://ubuntuhandbook.org/index.php/2014/08/gnome-sound-converter-214-released/](http://ubuntuhandbook.org/index.php/2014/08/gnome-sound-converter-214-released/)

I am now running Soundrecorder 2.1.5.
---------------------------------

$ ffmpeg -i "King Crimson - Discipline.ape" "King Crimson - Discipline.flac"
ffmpeg: command not found

I wonder if libav can do it.

---------------------------------------

Deleted: ~/.gstreamer-0.10

No change.

---

### Post by mooreted on 2015-07-19
I found a script that works:

CODE:

#!/bin/bash
 
find "$1" -type f -iname "*.ape" -print0 | while read -d $'\0' song
 
do
    output=${song%.ape}.mp3
    cue=${song%.ape}.cue
    avconv -i "$song" -b 192k "$output"
    if ls "$cue" &> /dev/null; then
        mp3splt -a -c "$cue" "$output"
        rm "$output"
    else
        echo "no need to split"
    fi
done

---

### Post by shantiq on 2015-07-21
you can also go to the folder ```
cd
``` you wish to convert and run this

```
 for f in *.ape  ; do avconv -i "$f"  "${f%.*ape}.flac"; done
```

or if you have ffmpeg

```
 for f in *.ape  ; do ffmpeg -i "$f"  "${f%.*ape}.flac"; done
```

---

### Post by mooreted on 2015-07-21
That's nice and short. I'll had that to my script notes. 

Thanks.

---

