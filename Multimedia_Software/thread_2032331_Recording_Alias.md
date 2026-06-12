---
title: "Recording Alias"
date: 2012-07-23
forum: Multimedia Software
---

### Post by RezPix on 2012-07-23
Hello, Currently I am using the following script to record my desktop.

```
ffmpeg -f alsa -ac 2 -i pulse -f x11grab -r 30 -s 1920z1080 -i :0.0 -acodec pcm_s16le -vcodec libx264 -preset ultrafast -threads 0 screencast.mkv
```Is it possible to create a alias so that when I run it, it starts the script and makes a new file name for each recording. Because at the moment if I tried to use the script twice it would ask me if I wanted to override it. Also it would save me copying the code every time.

Many Thanks.

---

### Post by papibe on 2012-07-23
Hi RezPix.

I would say you need to modify your script instead of an alias.

First, let's put this into a file:
```
#!/bin/bash
ffmpeg -f alsa -ac 2 -i pulse -f x11grab -r 30 -s 1920z1080 -i :0.0 -acodec pcm_s16le -vcodec libx264 -preset ultrafast -threads 0 screencast.mkv
```
Save it as myscrtipt.sh

Then create your personal ~/bin and move the script there:
```
mkdir ~/bin
mv myscript.sh ~/bin
```
Next time you restart your computer, ~/bin will be added to the PATH, so myscript.sh can be executed anywhere.

As for not overwrite the same file, I would add a command substitution with the date (using Unix epoch):
```
ffmpeg ... /path/to/screencast.$(date +%s).mkv
```
I hope that helps, and let us know how it goes.
Regards.

---

### Post by RezPix on 2012-07-23
Hello, Thanks a lot! The only issue I have now is when screen casting the video goes very quick and the audio is very out of sync. Any Ideas? Thanks.

---

### Post by papibe on 2012-07-23
My first guess would be to use a less intensive codec, and maybe a smaller screen.

Take a look at this thread [here]("http://ubuntuforums.org/showthread.php?t=1392026&highlight=proper+screencasting") (post #2).

Regards.

---

### Post by RezPix on 2012-07-23
Thanks, I do have a fairly powerful PC. Would this not help? Or is it software based? I have a ATI 6950 2GB Graphics card with a AMD Bulldozer 3.6GHZ cpu if that helps. Thanks.

---

### Post by FakeOutdoorsman on 2012-07-23
> **RezPix said:**
> ```
... -s 1920z1080 ...
```

Should be ```
... -s 1920x1080 ...
``` for others who may want to try this.

---

### Post by papibe on 2012-07-23
> **RezPix said:**
> Or is it software based?
Yes.

Although decoding HD video has became a 'commodity' (because of GPU acceleration), **encoding** video still depends on raw CPU power.

Just a thought.
Regards.

---

### Post by mc4man on 2012-07-24
A variation on this, noting I use unity here so a launcher icon makes sense.
Also the actual FFmpeg command should be whatever desired.
The terminal running FFmpeg has been made very small as I don't want to see my normal, it's just there to run a Q on when ending the recording, can be adjusted or eliminated altogether

So a simple .desktop in ~/.local/share/applications, the Exec= is a script in ~/bin so no need to path.
The Icon= is pathed to where stored though it could also be placed in /usr/share/pixmaps & then just Icon=ffmpeg would do.

```
[Desktop Entry]
Version=1.0
Type=Application
Exec=recorder1
Name=Desktop Recorder
Icon=/home/doug/Pictures/ffmpeg.png
```
Then just dragged on to the launcher from ~/.local/share/applications

Then an example script, the naming can be adjusted as desired, this one is fairly specific

```
#!/bin/bash
NOW=$(date +"%b-%d-%y-%H:%M")
gnome-terminal --geometry=20X4  -x ffmpeg -f x11grab -r 30 -s 1280x800 -i :0.0 -c:v libx264 -threads 0 ./Videos/screens/$NOW.mp4 
```

Icon used here attached

---

### Post by mc4man on 2012-07-24
inadvertent dupe

---

### Post by RezPix on 2012-07-24
So from all this, what can I do so my video does not go out of sync? thanks.

---

### Post by ron999 on 2012-07-24
> **RezPix said:**
> So from all this, what can I do so my video does not go out of sync? thanks.
Hi
Try it with a modified command like this:-
```
ffmpeg -f alsa -ac 2 -i pulse -f x11grab -r 30 -s 1920x1080 -i :0.0 -acodec pcm_s16le -vcodec libx264 -preset ultrafast -crf 0 ~/Desktop/$(date +"%Y-%m-%d-%Hh%Mm")-screencast.mkv
```

And if there are problems with sync try with lower frame rate (-r) ... 25 or 20 or 15 like this:-
```
ffmpeg -f alsa -ac 2 -i pulse -f x11grab -r 15 -s 1920x1080 -i :0.0 -acodec pcm_s16le -vcodec libx264 -preset ultrafast -crf 0 ~/Desktop/$(date +"%Y-%m-%d-%Hh%Mm")-screencast.mkv
```

---

### Post by RezPix on 2012-07-26
Thanks a lot, Really Helped!

---

