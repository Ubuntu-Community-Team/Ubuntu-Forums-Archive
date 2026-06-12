---
title: "How to convert multiple files using ffmpeg from the command line or terminal"
date: 2011-03-13
forum: Multimedia Software
---

### Post by fixitdude on 2011-03-13
> can any body tell me how to convert multiple .wav files into .mp3. I want to convert whole folder. i am new to linux. can any body tell how to script it? thanks...

How to convert multiple files using ffmpeg and the command line or terminal.

In this case I'm converting .flv (adobe flash) to avi video formats and it's keeping the same quality if possible.

Just remember that the output file will be larger.

You can edit this command line and change the ".flv" to whatever type of input file you have and the ".avi" to your output format and ffmpeg will pick that up and use that instead. Change ALL occurrences in the line of course.

It's best if you stick all the files you want to convert into their own folder and "cd" into that folder before you use this.

It also uses the command "basename" which simply strips any leading directory names and the ".flv" suffix.

```

for f in *.flv; do echo "Converting $f"; g=`basename $f .flv`; ffmpeg -sameq -i $f $g.avi || echo FAILED; done

```

I also suggest you make a little text file that contains all these types of commands you have found on the net, you never know when this message or others will disappear.

You will also be limited by the number of files the shell commands can handle for "*.flv", but it should be in the 1000's.

You also want the win32 codecs installed
sudo apt-get install libdvdcss2 w32codecs

There's also a thread about this and a program called winff.

sudo apt-get install avidemux ffmpeg winff

"WinFF is probably the most user-friendly tool for converting videos and extracting audio from videos in Ubuntu. Avidemux is a popular and useful video editing application, which makes it quite simple to cut and crop videos to your liking - and much more."
[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

Other keywords for searching this message are xine codec vlc conversion mplayer win32 w32codecs media

---

### Post by rubylaser on 2011-03-13
This post is a bunch of statements, so I'm not really sure what you're asking.  So I'll answer the first one which is how to convert wavs into mp3s.

```
sudo apt-get install lame
```

Then, cd into the directory that has your wav files...
```
cd ~/wav_directory
```
Then create a script to use lame to convert the wavs to mp3.

```
gedit convertwavs_to_mp3.sh
chmod +x onvertwavs_to_mp3.sh
```
And, paste this in...
```
#!/bin/bash

for i in *.wav; do
 if [ -e "$i" ]; then
   file=`basename "$i" .wav`
   lame -h -b 256 "$i" "$file.mp3"
 fi
done
```
Set the -b (bitrate) to the bitrate you'd like.  Hope that helps.

---

### Post by FakeOutdoorsman on 2011-03-13
> **fixitdude said:**
> You also want the win32 codecs installed
```
sudo apt-get install libdvdcss2 w32codecs
```

FFmpeg doesn't use these packages.

---

### Post by Breambutt on 2011-03-13
If you use rubylaser's script, you could also do...

```
mv convertwavs_to_mp3.sh /home/$USER/.gnome2/nautilus-scripts/
```

...so you can just right-click anywhere in the wav folder in Nautilus and select *Scripts > convertwavs_to_mp3* from the dropdown menu.

---

### Post by shantiq on 2011-03-14
[B]simple way==>
[/B]
To mp3 320kbps (lossy) 



cd   change directory to where your files are then enter as one line 


```
for f in *.wav; do ffmpeg -i "$f" -ab 320k "${f%.wav}.mp3"; done
```


if you want to delete original wav as well go

```
for f in *.wav; do ffmpeg -i "$f" -ab 320k "${f%.wav}.mp3"[COLOR="Red"] && rm "$f"
[/COLOR] ; done
```




from my extensive research into **[the topic]("http://ubuntuforums.org/showthread.php?t=1609760")**

---

### Post by rubylaser on 2011-03-14
Those are some nice concise 1 liners you have there.  I don't convert audio very often, but thanks for sharing.

---

### Post by zer010 on 2011-07-09
Thank you so much for that shantiq!  That's exactly what I've been looking for.  Nice work in the other thread as well.  ^_^d

---

