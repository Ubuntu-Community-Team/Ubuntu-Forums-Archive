---
title: "Extract all frames from video into images"
date: 2009-01-17
forum: Multimedia Software
---

### Post by yengamatic on 2009-01-17
Hello,

I have a video recorded from my camera (encoded in mp4) and I want to convert it into a series of png images that I need to process separately.

Is there any software that I can use in order to do this? I have tried with winff and avidemux, looking at its options, but I haven't found anything related.

At my best guess, I think I first need one of both apps mentioned to convert mp4 to raw avi video or something. Then another app should convert raw avi to image sequence (in png format i.e.), but I don't know of any app like that.

Another thing related with winff is that it says it has no decoder for audio track, but i don't want it though, how can i ignore audio from winff (or the other app)?


Thanks in advance.

---

### Post by jmorth on 2009-08-09
I had the same question. However my source file was a FLV. I would think that this would work with any kind of video file.

There is probably a quicker and easier way to do this in terminal, I just don't know it. Anyway, this is what I did.

First off, I loaded my clip into avidemux and used the A-B markers to select the section I wanted. Then I used avidemux to save the clip as an AVI.

Then I loaded up VLC and selected the convert/save in the media menu. Navigate to your AVI file and click the convert/save button. Then click the file box and name your clip. In the box by Profile, select MPEG4-Divx. Then click save.

Now, it saved the file in your home folder. Using the terminal type in```
ffmpeg -i Video.mpg Pictures%d.jpg
```

You can probably change the JPG to PNG. If it doesn't work using PNG, then use JPG. Just fire up GIMP and save the JPGs as PNGs.

I hope that helps.

And if anybody more experienced in the art of ubunt-fu (*nix-fu, cli-fu, etc.), sees this and knows a quicker way, please post the magic commands.

EDIT: turns out I didn't look hard enough at avidemux. It appears that avidemux actually has an option to save your selection as JPEGs. So that is a LOT faster and easier than my way. Thanks to this website: [http://nativeraving.blogspot.com/2007/11/creating-animated-gif-files-with-ubuntu.html]("http://nativeraving.blogspot.com/2007/11/creating-animated-gif-files-with-ubuntu.html")

---

### Post by andrew.46 on 2009-08-10
Hi yengamatic,

> **yengamatic said:**
> I have a video recorded from my camera (encoded in mp4) and I want to convert it into a series of png images that I need to process separately.

MPlayer has a png output that should do what you are after. You can see if your version of MPlayer has this capability as follows:

```

andrew@skamandros~$ **[COLOR="Red"]mplayer -vo help | grep png[/COLOR]**
	png	PNG file

```

Just be a little careful to put some time limits in place or your disk will fill vey quickly:

```
mplayer *[COLOR="Red"]inputfile[/COLOR]* -vo png:z=8 -endpos 5 -ao null
```

This command stops after 5 seconds of playback but still generated an impressive number of images :-). To start a little way into your video use the *-ss* option.

All the best,

Andrew

---

### Post by ketom2000 on 2009-08-12
Avidemux (GTK+) has this if you want something that has a GUI.

---

### Post by dryphi on 2011-01-09
The Totem Movie Player that comes packaged with Ubuntu does this as well, quite easily I might add.
Just open the video in Totem, and go to Edit - Create Screenshot Gallery or Edit - Take Screenshot (or press Ctrl + S).

One thing I might mention is in the Create Screenshot Gallery dialog, it gives you the option to set the pixel width. The default is set at 128. I would imagine this should be set to the resolution of your camera (ie if the video is shot in 640x480, maybe this should be set to 640). Totem tells you the dimensions of the video in the menu to the right.

---

