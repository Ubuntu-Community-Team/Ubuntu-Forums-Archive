---
title: "Youtube in Totem - New User problems"
date: 2010-03-11
forum: Multimedia Software
---

### Post by Gerbilkit on 2010-03-11
Hi all, I am a new Linux user. I finally reformatted my laptop two days ago and wiped windows clean off the machine, and I am now running the newest version of Ubuntu which I think is version 9.10? Anyway one of the big problems I was having with windows was extreme lag when using any flash content, and I found that the Totem movie player is capable of playing youtube videos without flash.  I was really excited to hear this, but when I try this I get "GStreamer has encountered a general supporting library error".  I'm really not sure what this means, like I said I'm new to linux so I don't know if this means a library is missing, or if a library is corrupted, or even something else. I've just been following links from google searches installing things from tutorials, but I'm not too confident on what's what yet, so if anyone has some advice and instructions that would be appreciated.

---

### Post by Yellow Pasque on 2010-03-11
Make sure you have the gstreamer plugins:
```
sudo apt-get install gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-plugins-ffmpeg
```

If you're still having issues, I'd recommend this PPA to get the latest stable gstreamer (I use it myself): [https://launchpad.net/~gstreamer-developers/+archive/ppa](https://launchpad.net/~gstreamer-developers/+archive/ppa)

EDIT: Typo in command

---

### Post by Gerbilkit on 2010-03-11
Well it seems I only have problems with certain youtube videos. I looked at what you posted, and I even ran it to be sure and I already have all of those.  The problem now is that while I am watching a video, it may all of a sudden grow really choppy, laggy, and basically unwatchable. Mostly just the video lagging not the audio, but this isn't the case all the time because I just watched a segment of the lion king in HD with no problems, but then the second segment started out fine and then got really choppy. Is there anything I can change to improve this? Do I potentially have a bad plugin or outdated libraries? Just wondering if this is a really common issue that just requires a few quick lines on the terminal.

Thanks for the help!

---

