---
title: "can't see videos, sound plays OK"
date: 2010-03-18
forum: Multimedia Software
---

### Post by tubunu on 2010-03-18
I have come up against a problem I cannot solve on my own. Until a few days ago I could watch avi, mpeg files fine. Now, however, I can only hear the sound of the videos being played, but there's no picture (just black screen). I wonder if there's any way to check what files/libraries I am missing as I've already made sure I have all the prerequisites for playing movies on Ubuntu. 

A couple of days ago I successfully managed to install my webcam, so I figure it must be the reason. Could someone knowledgeable point me in the right direction? THANKS!

---

### Post by Mia1990 on 2010-03-18
You may want to see if these are installed but if you missing one movie player should find and install it for you i think here is the list

> gstreamer0.8-plugins gstreamer0.8-lame gstreamer0.8-ffmpeg w32codecs lame sox ffmpeg mjpegtools vorbis-tools libdvdcss2 gstreamer0.8-plugins-multiverse avifile-divx-plugin avifile-mad-plugin avifile-mjpeg-plugin avifile-vorbis-plugin avifile-win32-plugin avifile-xvid-plugin libdvdnav4 libdvdplay0 libdvdread3

This page should take you through installing all the codecs you'll need.

> [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by ramjitmyrtle on 2010-03-18
try this
 
>  
$sudo apt-get ubuntu-restricted-extras


---

### Post by tubunu on 2010-03-18
> **Mia1990 said:**
> gstreamer0.8-plugins gstreamer0.8-lame gstreamer0.8-ffmpeg gstreamer0.8-plugins-multiverse

Thanks, Mia1990, I don't have these, but aren't they too old by now? I have 0.10 version of gstreamer plugins installed. Double checked restricted formats and have all the prerequisites for playing videos in Ubuntu. I can only hear the sound, no picture. :( 
Any other advice would be much appreciated.

---

### Post by Yellow Pasque on 2010-03-18
Start your player in the terminal, for example if you use "Movie Player":
```
totem
```
Also, you might want to make sure gstreamer video works correctly, especially if you use movie player/totem:
```
gstreamer-properties
```

---

### Post by tubunu on 2010-03-21
I checked that. I still can't see video, just black screen and audio.

---

### Post by tubunu on 2010-04-09
I still haven't been able to resolve this issue. :confused:

I know I will be able to see the videos once Lucid comes out on the 29th, but it's not really fixing the problem... Sadly, I find that most of the ***serious*** problems I've had with Ubuntu for the past 5 years or so, could only be resolved with a fresh install. It's something the community should work towards changing. Just a thought. 

Waiting impatiently for Lucid.. :P

---

### Post by lidex on 2010-04-09
Temüjin asked you to start your video app in a terminal, that is a troubleshooting step. Start your player in a terminal, play a video file, post the error output here.

What players have you tried, BTW? And what video formats?

---

### Post by tubunu on 2010-04-13
> **lidex said:**
> Temüjin asked you to start your video app in a terminal, that is a troubleshooting step. Start your player in a terminal, play a video file, post the error output here.

I did that, but there are no errors whatsoever. Why should there be any errors if the file plays correctly BUT for the picture? The only output is BLACK screen, the sound is OK. 

> **lidex said:**
> What players have you tried, BTW? And what video formats?

I've tried VLC, totem, Gnome Mplayer, with the same result. Video format - .avi

---

### Post by soniakhan33 on 2010-04-13
There is a codec for it,install klcodec,then you can wath all types of videos in your player......

---

### Post by lidex on 2010-04-13
> **tubunu said:**
> I did that, but there are no errors whatsoever. Why should there be any errors if the file plays correctly BUT for the picture? The only output is BLACK screen, the sound is OK. 



I've tried VLC, totem, Gnome Mplayer, with the same result. Video format - .avi

Sounds like gstreamer. Work through this howto:
[http://ubuntuforums.org/showthread.php?t=766683]("http://ubuntuforums.org/showthread.php?t=766683")

---

### Post by andrew.46 on 2010-04-14
A simple thing to try is to change the video out device selected by your media player. Try using SMPlayer:

```
sudo apt-get install smplayer
```

and then alter the video out device by looking in:

Options --> Preferences --> General --> Video --> Output Driver

and select something like gl or x11.

All the best,

Andrew

---

### Post by BJ_Covert_Action on 2010-04-14
I had a similar issue as this happening on one of my boxes that was attached to a TV. I never did troubleshoot it successfully, but, a couple days later I stumbled upon _[this thread](http://ubuntuforums.org/showthread.php?t=606624)_. Apparently this issue could be caused by Xv overlays having issues. In the linked to thread, there is a discussion about an app that can be used to switch the proper Xv overlaying behavior between multiple screens. I don't know if that set up would apply to you or not. However, you may try doing some digging on properly configuring your Xv overlay setup in X and Xrandr for whatever your setup is if you exhaust all other options. Also, found on the ubuntu wiki, there is this little bit:

 _[X/Config/SVideo](https://wiki.ubuntu.com/X/Config/SVideo)_ 

...which has some interesting info about video corruption in the second section. I doubt this is your problem in particular since you never mentioned outputting over an S-video cable, but it may give you some clues on stuff to play with to get your videos playing correctly. Also, for reference, Totem uses the gstreamer video stuff if I remember correctly, so that's the stuff you probably want to be tweaking.

---

### Post by tubunu on 2010-04-14
Thank you to everyone who contributed to this thread. This is what fixed it for me. Thanks again. 


> **andrew.46 said:**
> A simple thing to try is to change the video out device selected by your media player. Try using SMPlayer:

```
sudo apt-get install smplayer
```

and then alter the video out device by looking in:

Options --> Preferences --> General --> Video --> Output Driver

and select something like gl or x11.

All the best,

Andrew

---

