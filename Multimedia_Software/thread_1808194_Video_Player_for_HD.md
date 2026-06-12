---
title: "Video Player for HD?"
date: 2011-07-20
forum: Multimedia Software
---

### Post by Adrianzr1 on 2011-07-20
Hi everybody, I have an Acer Aspire One ZG5 with ubuntu and windows, i have an HD video camcorder, when i try to se a video recorded for this camera (that it's in HD 720p), the video looks laggy, i only can see some parts of the video, the audio is good but the video not much.

The camera comes with a CD and has a program that can be used in windows, with that program if i want to see a video of this camcorder i just open it whit that player and it looks good, but in Ubuntu i don't know any program that let me see my videos good without beeing laggy. Do you know any program that i could use?

I have tried VLC, Movie Player, Banshee, and have no luck.

Another question, which program i can use to edit videos? A good one.

---

### Post by foxmulder881 on 2011-07-20
Could be your video card driver.

---

### Post by Adrianzr1 on 2011-07-20
> **foxmulder881 said:**
> Could be your video card driver.

yeah i really think that is the problem, but i can't do something to fix that and was wondering if there were any program that automatically put down the quality of the video, like the one that i mention.

The program that i use in windows is "Total Media Extreme"

---

### Post by foxmulder881 on 2011-07-20
> **Adrianzr1 said:**
> yeah i really think that is the problem, but i can't do something to fix that and was wondering if there were any program that automatically put down the quality of the video, like the one that i mention.

Don't know. Video is not really my area of expertise. I was just pointing out what might be the source of the problem.

---

### Post by Adrianzr1 on 2011-07-20
> **foxmulder881 said:**
> Don't know. Video is not really my area of expertise. I was just pointing out what might be the source of the problem.

and i almost sure that you are right on that point.

---

### Post by lovinglinux on 2011-07-20
There are actually two problems. First the video card/driver, second the CPU processing power. When you play a video with 720p or 1080p, there is a lot of data to be decoded. If you have a good video card a video driver, most of the processing is done through the video card. However, if the card or the driver is not capable of video hardware acceleration, then the CPU needs to process a lot more information. If the CPU has not enough processing power, it chokes and the video stutters.

When you watch the videos on Windows, they work as expected, because the manufacturers of the video cards make decent drivers for Windows. Unfortunately, most video drivers are proprietary, so Ubuntu developers cannot tweak them to work better on Linux environment. I am not sure, but it seems your video card driver is in fact open source and can make use of hardware acceleration. You might want to try XBMC media center, since I have found some info about hardware acceleration on GMA chipset on [their page]("http://wiki.xbmc.org/index.php?title=Hardware_Accelerated_Video_Decoding_Developement#Hardware_Accelerated_Video_Decoding_under_Linux").

Before installing XBMC, make sure you have the latest driver for your video card installed. You can do that by launching "Additional Drivers" application, and activating the driver for your video card, if available.

If XMBC doesn't work for you, I would suggest SMPlayer. To improve performance with 720p videos, launch it, access the *Preferences* by hitting CTRL+P or from the menu "*Options >>> Preferences*". Then click the *General* option in the left panel, then select the *Video* tab on the right. In the *Output driver* option, make sure **xv** is selected. Then click *Performance* on the left panel, the select S*kip only on HD videos* in the *Loop filter* options. This only works for h264 videos, but most likely your videos are encoded with that codec.

About video editors, see [http://linuxappfinder.com/multimedia/videoeditors](http://linuxappfinder.com/multimedia/videoeditors)

---

### Post by Adrianzr1 on 2011-07-20
almost done "lovinglinux", i tried the SMPlayer and after moving some options i can play the video but it is look a little slower than the audio.

Just change the options of the "Performance" menu, removing the checkmark of the "Allow frame drop" option, other way it still looking laggy

---

### Post by lovinglinux on 2011-07-20
> **Adrianzr1 said:**
> almost done "lovinglinux", i tried the SMPlayer and after moving some options i can play the video but it is look a little slower than the audio.

Just change the options of the "Performance" menu, removing the checkmark of the "Allow frame drop" option, other way it still looking laggy

Without frame drop it works fine?

---

### Post by papibe on 2011-07-20
According to [this]("http://www.pcworld.idg.com.au/review/notebooks/acer/aspire_one_zg5_linux/255307") couple of [reviews]("http://www.ifixit.com/Device/Acer_Aspire_One_ZG5"). There's no way that that model can reproduce 720p video just using the CPU.

In order to play HD video you need video hardware acceleration. To accomplish that you'll need to:
[LIST]
[*]Identify your graphic card or integrated graphics.
[*]Research and confirm it supports acceleration.
[*]Install the proprietary driver that supports it.
[*]Install a video player that can use the graphic capabilities (either vdpau or VAAPI).
[/LIST]
Additionally, it may be necessary to transcode your videos to the supported CODECS.

Let's start with your graphic card. What is it?

Hope it helps,
Regards.

---

### Post by beew on 2011-07-20
> **Adrianzr1 said:**
> almost done "lovinglinux", i tried the SMPlayer and after moving some options i can play the video but it is look a little slower than the audio.

Just change the options of the "Performance" menu, removing the checkmark of the "Allow frame drop" option, other way it still looking laggy

As papibe's links show your laptop is probably just too weak.

But you may improve video playback somewhat by 1) using gnome-mplayer as your gui for mplayer instead of smplayer, it uses less resources 2) install mplayer from this ppa
[https://launchpad.net/~ripps818/+archive/coreavc]("https://launchpad.net/%7Eripps818/+archive/coreavc") 

It is actually mplayer2, it works a lot better than stock mplayer from the Ubuntu repo and mplayer from other ppas. Don't worry about the coreavc stuffs, the player has nothing to do with it. Just install the player would be fine.

---

