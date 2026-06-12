---
title: "Stuttering sound with an AVI file"
date: 2009-04-14
forum: Multimedia Software
---

### Post by Psyphre on 2009-04-14
HI,

I have an avi file which sutters (only the audio) in totem. The video plays fine, its just the audio that stutters and stops and skips etc. I dont have a problem with any other avi files, or any files in general.

I tried using vlc and that too suffers the same, however if I set the cache to 1second, then it seems to solve the issue.

Now as I said its just this file. I have no issues at all with other avi files, or other video files (even 720p or 1080p resolutions - so its not my hardware). At first I thought maybe it was a corrupt file, but it works perfectly in windows.

What could be the problem?

Thanks.

---

### Post by zero777zero on 2009-04-15
do you know what audio codec is in the AVI container?

i suggest you download VLC and give it a try

if you are still having the issue in VLC, go to the vlc menu->tools->codec information and tell us what you see.

---

### Post by Psyphre on 2009-04-15
Thanks for the reply. Ive already tried VLC as mentioned in the first post.

It says the codec is mpga.

---

### Post by zero777zero on 2009-04-16
that should just be an mp3 audio file then, if you have restricted codecs installed, such as the [medibuntu repository]("https://help.ubuntu.com/community/Medibuntu"), then i cant see what the problem is

---

### Post by Psyphre on 2009-04-16
Yeh i cant figure it out either. I do have the codecs installed. Its really strange as it plays fine in windows, or in ubuntu with VLC WITH a 1second cache.  Vlc normally or totem stutter.

---

### Post by zero777zero on 2009-04-16
you might want to try to remux the file

---

### Post by Psyphre on 2009-04-16
does that mean converting it into another format?
I tried that and was semi-succesful. The sound was fine, with no stuttering but it has odd glitchy sounds every few seconds or so.

Really strange isnt it :S

---

### Post by zero777zero on 2009-04-16
.avi is a 'container format' that holds video and audio stream. remuxing means just 'redoing' the container format, you can do it into .avi or [.mkv]("http://www.bunkus.org/videotools/mkvtoolnix/downloads.html")

i've never remuxed a avi file but i think you can do it in avidemux (in add/remove programs)

btw when you remux you aren't losing any quality, its just like putting the files into

---

### Post by Psyphre on 2009-04-17
thanks for continuing to reply, i appreciate it.

I actually tried avidemux when i converted it to mkv which i mentioned in my last post. Sound works (no stutering) but alot of audio glitches.

---

