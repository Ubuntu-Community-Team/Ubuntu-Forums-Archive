---
title: "GStreamer cannot read audio .mov file"
date: 2020-02-15
forum: Multimedia Software
---

### Post by kschiff on 2020-02-15
[COLOR=#000000]I am using software to playback audio/video for guitar lessons that allow one to slow down the playback without changing the pitch: Transcribe! Great software, but for some reason my set up is choking on .mov files. The developer told me to update the restricted codes etc.. which I did, to no avail. They also said that I should explore other codes that might be missing. I am running 19.10.


Here's the error message:

[IMG]https://i.imgur.com/A5f24UF.png[/IMG]



The file originated on a Mac and the audio is MPEG4-AAC

[IMG]https://i.imgur.com/6A86CS1.png[/IMG]




Any ideas?

[/COLOR]

---

### Post by SeijiSensei on 2020-02-15
First, I suggest trying to play the file. I'd use mpv for this task. "sudo apt update; sudo apt install mpv".  If you want a GUI interface, install SMPlayer as well.

One thing you could try is converting the file with ffmpeg to another format like .mp4.  Something like
```
ffmpeg -i input.mov -vcodec copy -acodec copy output.mp4
```
replacing input.mov and output.mp4 with the appropriate names.

---

### Post by Yellow Pasque on 2020-02-16
Make sure gstreamer1.0-libav is installed.

---

