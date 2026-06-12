---
title: "Most compatible video format for all platforms"
date: 2011-10-21
forum: Multimedia Software
---

### Post by rmcellig on 2011-10-21
Which format should I save videos in that make them compatible among Mac, Windows and Linux. I have some .mov files that Avidemux won't open properly. Same goes for some mpeg format files. Would I be better to choose .avi format as the most compatible?

---

### Post by andrew.46 on 2011-10-22
I sense a small amount of confusion between container format and codecs here :). A container such as .mov, .mkv, .avi or .mp4 can contain a variety of audio and video codecs such as h.264 video, mp3 sound, aac sound etc. Perhaps the best compromise is an mp4 container with h.264 video and either aac or mp3 sound.

What software are you using to produce or transcode your media clips, always avidemux?

---

### Post by satanselbow on 2011-10-22
> **andrew.46 said:**
> I sense a small amount of confusion between container format and codecs here :). A container such as .mov, .mkv, .avi or .mp4 can contain a variety of audio and video codecs such as h264 video, mp3 sound, aac sound etc. Perhaps the best compromise is an mp4 container with h264 video and either aac or mp3 sound.

What software are you using to produce or transcode your media clips, always avidemux?

I don't think x264 has really hit that point where is universal yet. Many USB enabled TV (for example) throw a fit when you inadvertently put x264 mp4 on them :(

I would say - currently - mp4 containered xvid / mp3 avi's would still be the way to go. Using a "proper" framesize at 4:3 or 16:9 can help smooth the way too ;)

Getting down n dirty with ffmpeg on the command line will get you the best results :D

Purely "compatability" based observation and does not guarantee best quality etc

---

### Post by rmcellig on 2011-10-22
I know about the concept of consumer files but I have to tell you that for the average user, videos are not the easiest thing to understand.

I was really hoping that in Linux I would find something that was quick and easy to use to extract snippets of video from some videos I have. On my Mac I use moeg streamclip. It opens everything without choking. After all the positive stuff I read about avidemux I was hoping to use something that just worked. Doesn't seem to be the case. Is avidemux the only toil in Lunux that will quickly and easily allow a user to make video snippets and save them in whatever format they like. I really want to find a Linux solution that just works. I'm not giving up yet :) I'm too attached to Lunux now even though I still have my iMac I spend about 80% of my computer time in Linux.

---

### Post by satanselbow on 2011-10-22
So you are more looking for a video editor than a direct converter?

openshot is pretty sweet and opens/saves to a wide variety of formats.

Available in the (dreaded) software centre or:

```
sudo apt-get install openshot
```

---

### Post by rmcellig on 2011-10-22
I heard a lot of good things about Openshot. How can I quickly save snippets in Openshot? I know how to mark the areas to be snipped but I'm not sure how to save them quickly.

I'm curious now about the dreaded software center.What is it you don't like about it. I'm just curious because some people prefer using the command line to install apps.

---

### Post by satanselbow on 2011-10-22
> **rmcellig said:**
> How can I quickly save snippets in Openshot? I know how to mark the areas to be snipped but I'm not sure how to save them quickly.


Add the marked section to the timeline then export in format of choice ;)

> **rmcellig said:**
> 
I'm curious now about the dreaded software center.What is it you don't like about it. I'm just curious because some people prefer using the command line to install apps.

There are several threads on the forums but in a nutshell (and IMHBSBO <- humble but somewhat bias ;) ):

1) increased handholding and dumbing down
2) increasing inclusion of paid for apps in preference to comparable (sometimes superior) FOSS alternatives.
3) increasing numbers of dubious "reviews" as to some apps quality (see 2)
4) I personally just don't need it or wish to see it installed by default.
5) I'm a synaptic fanboy on the sly
6) Any other valid reason that has been brought/thought up in other discussions on the subject :D

---

### Post by rmcellig on 2011-10-22
Actually I think what you are saying is that there is too much noise in the Software Center. You are right because what's so hard about just typing in sudo apt-get install openshot or better yet and I, like you love the Synaptic Package Manager (I think it is more flexible)?

I am not a command type person having used Macs since 1988 but I think I am slowly changing. I have Linux to thank for this because I just can't seem to get away from it!!

At times I have considered moving 100% to Linux but I am still not convinced that I can do everything in Linux that I can do on my Mac. I'm not talking about all the Mac eye candy etc... I'm talking about using apps that work well in Linux and that are reliable. I'm almost there. Once I can find a way to do my video snippets in Linux as fast and efficiently as I do on the Mac, that would be a real big deal for me in terms of heading for the Linux side of things.

---

### Post by andrew.46 on 2011-10-22
> **satanselbow said:**
> I don't think x264 has really hit that point where is universal yet. Many USB enabled TV (for example) throw a fit when you inadvertently put x264 mp4 on them :(

I guess I was basing this on my own personal experience of playing h.264 and aac movies via usb on my wife's new TV, giving her the same movies to playback on a windows 7 computer and sharing similar files with my father who runs Apple OSX. I guess these are all relatively modern devices though so perhaps 'most compatible' might be a stretch....

---

