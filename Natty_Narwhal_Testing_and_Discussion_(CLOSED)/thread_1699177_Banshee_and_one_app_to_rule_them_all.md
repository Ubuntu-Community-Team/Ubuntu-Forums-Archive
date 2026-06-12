---
title: "Banshee and one app to rule them all?"
date: 2011-03-03
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by taavikko on 2011-03-03
Evening all,

This is driving me crazy, why does banshee lists Videos as well?
There's no option to turn it off.
It makes the browsing of artists a pain, cause their unknown status. Not about to start naming them... I know what they are, I just wish that this feature of banshee would be optional and not shoved upon me...

gnomeuser, comment?

---

### Post by Harry33 on 2011-03-03
> **taavikko said:**
> Evening all,

This is driving me crazy, why does banshee lists Videos as well?
There's no option to turn it off.
It makes the browsing of artists a pain, cause their unknown status. Not about to start naming them... I know what they are, I just wish that this feature of banshee would be optional and not shoved upon me...

gnomeuser, comment?

Banshee has been like this quite some time now.
I do not use it anymore, but did with Lucid.
I did not like that feature either, there is VLC for videos IMO.
There were a lot of issues which made me dump it at last, one of them was never-working lyrics plugin.

---

### Post by taavikko on 2011-03-03
> **Harry33 said:**
> 
I did not like that feature either, there is VLC for videos IMO.


Dumbing some app because there are multiple choices available isn't an option. For one reason, they're not included in the default installation. I judge the apps and behaviour of them, included in the release. That's why we're here. Not just because of the new and shiny, but testing of something that evolves to new release with it's default apps.

There's totem media player installed by default, for viewing videos. It plays music too, but then, why include banshee that does the same things?

Personally i use mplayer + smplayer frontend for my video use.

---

### Post by zekopeko on 2011-03-03
The Video section in Banshee is being turned into a plugin (so you will be able to turn it off). I doubt it's going to make it in Natty though.

---

### Post by Simian Man on 2011-03-03
Can't you just not add any videos to the library?

---

### Post by Harry33 on 2011-03-03
> **taavikko said:**
> Dumbing some app because there are multiple choices available isn't an option. For one reason, they're not included in the default installation. I judge the apps and behaviour of them, included in the release. That's why we're here. Not just because of the new and shiny, but testing of something that evolves to new release with it's default apps.

There's totem media player installed by default, for viewing videos. It plays music too, but then, why include banshee that does the same things?

Personally i use mplayer + smplayer frontend for my video use.

Now that is my personal choice to dumb an applications or not.
We are here also for the freedom of choice.
Please read more carefully, that was **only one of** the reasons.

About Totem. Yes I now very well that gstreamer application.
VLC is the option for me.

---

### Post by taavikko on 2011-03-03
> **zekopeko said:**
> The Video section in Banshee is being turned into a plugin (so you will be able to turn it off). I doubt it's going to make it in Natty though.

Thanks for the info.

> **Simian Man said:**
> Can't you just not add any videos to the library?

The thing is that banshee reads automatically files in $HOME/Videos/
and adds them to it's library

---

### Post by VMC on 2011-03-03
> **Harry33 said:**
> Now that is my personal choice to dumb an applications or not.
We are here also for the freedom of choice.
Please read more carefully, that was **only one of** the reasons.

About Totem. Yes I now very well that gstreamer application.
VLC is the option for me.

VLC is my choice as well. I've had problems with others in the past, but VLC works for me using both video and music. 

I did try Banshee for the first time using natty. Works well, just not sure if it will ever replace VLC for me.

---

### Post by MadMan2k on 2011-03-03
> **taavikko said:**
> 
The thing is that banshee reads automatically files in $HOME/Videos/
and adds them to it's library
but you can configure that location ;)

---

### Post by Harry33 on 2011-03-03
> **VMC said:**
> VLC is my choice as well. I've had problems with others in the past, but VLC works for me using both video and music. 

I did try Banshee for the first time using natty. Works well, just not sure if it will ever replace VLC for me.

Banshee is quite a heavy application, based on gstreamer.
VLC is a light-weight application, based on qt.

But, Banshee is actually no video player at all, it replaced Rhythmbox in Ubuntu and as such, is music player, which can also rip and burn CD's.
Perhaps there was more reasons then to stick to the controversial mono.

VLC is really a superior video player, which can of course play sound files too.
VLC will be even better when the GPU acceleration gets better (still quite experimental now).
And one more thing i like in VLC, it is highly customizable.

---

### Post by directhex on 2011-03-03
> **Harry33 said:**
> Banshee is quite a heavy application, based on gstreamer.
VLC is a light-weight application, based on qt.

You're comparing apples & oranges a little there. Qt and gStreamer are not directly comparable - one is a GUI toolkit, the other is a media framework.

Banshee's toolkit is GTK. VLC's media framework is a mix of things, mostly FFmpeg.

As to the light-vs-heavy question, not sure about that either. Banshee on a bare Ubuntu system (i.e. no Mono already there, so this number includes Mono just for Banshee) is 31 meg. VLC weighs in at more than that without Qt factored in, mostly due to the 24 meg vlc-data package.

> VLC is really a superior video player, which can of course play sound files too.
VLC will be even better when the GPU acceleration gets better (still quite experimental now).
And one more thing i like in VLC, it is highly customizable.

File players and library players really have entirely different usage scenarios. VLC is an extremely functional, if occasionally overwhelming and unintuitive, file player, something to compete with mplayer or totem. Banshee is a library player, and really isn't appropriate for use as a file player - it has more in common with Amarok or Clementine than VLC, even though it has video support through gStreamer.

---

### Post by Harry33 on 2011-03-04
> **directhex said:**
> 
...
File players and library players really have entirely different usage scenarios. VLC is an extremely functional, if occasionally overwhelming and unintuitive, file player, something to compete with mplayer or totem. Banshee is a library player, and really isn't appropriate for use as a file player - it has more in common with Amarok or Clementine than VLC, even though it has video support through gStreamer.

When I compared Banshee with the former Ubuntu default music player, Rhythmbox (both based on GTK+2 and gstreamer) I have often found Rhytmbox more usable, depending on the fact that it has far less bugs and that it works faster). Banshee may have a little better gui, but actually I do not find so many differencies in there. Both are very far away from the Windows MediaPlayer (outlook only).

Then choosing a video player, I would only compare VLC and Mplayer (possibly with Smplayer interface).
There again, VLC is faster and much more customizable.
Totem is absolutely out of the question.
I would immediately uninstall the whole totem, but I cannot, because then the thumbnailing does not work anymore (in Nautilus).

---

### Post by gnomeuser on 2011-03-04
> **taavikko said:**
> Evening all,

This is driving me crazy, why does banshee lists Videos as well?
There's no option to turn it off.
It makes the browsing of artists a pain, cause their unknown status. Not about to start naming them... I know what they are, I just wish that this feature of banshee would be optional and not shoved upon me...

gnomeuser, comment?

I am happily using the current Banshee Video implementation to manage some 700GB of content. It works very well for me though I do wish the metadata writeback and file/folder name reflection of changes to it worked on the Video source. Also this would be greatly aided by increased support for video container formats in taglib-sharp.

Though specifically to address your question:

[http://www.omgubuntu.co.uk/2011/01/banshee-video-tv-shows-windows-and-hackfest-oh-my/](http://www.omgubuntu.co.uk/2011/01/banshee-video-tv-shows-windows-and-hackfest-oh-my/)

However the video extension and TV show support (basically the same git branch for reviewing and merging purposes) as well as DVD support are all feature which are far too invasive and have too great a regression risk (especially worries are that importing will become less reliable). These along with the dbus-sharp port which will add stability (and likely help us take back that ½ sec we are forced to spend on start up currently) are only likely to be merged post 2.0 (meaning they will miss the release of Banshee which will ship with Natty though as usual our excellent PPAs will likely to provide these to users soon).

The problem is the lack of qualified reviewers for the code currently and the late stage at which we find ourselves in terms of development. It is simply to risky to merge now. However the code all works really well, I have been testing it for a while.

So if this really annoys you, enable the daily ppa and wait. The functionality you request is present and will arrive in a Banshee near you soon.

Similarly the genre browser changes have not yet made it into Banshee. The developer responsible has not had time to finish the feature. I will poke him again.

Finally, in the future, if anyone wants comments on a Banshee thread please do poke me via pm. I don't have time to monitor the forums for Banshee threads.

---

### Post by seeker5528 on 2011-03-04
> **Harry33 said:**
> I would immediately uninstall the whole totem, but I cannot, because then the thumbnailing does not work anymore (in Nautilus).

What's *so* wrong with Totem that would make you want to completely get rid of it?

I get rid of the whacky 'play everything full screen even if it is the size of a postage stamp' totem-mozilla thing and install gecko-mediaplayer for that part of the equation.

Outside of that while Totem is not my preferred player it seems to work reasonably well, and with my current hardware setup it handles playing the mpeg stream from my video card more reliably than the others. 

Mplayer just doesn't seem to be able to keep the audio and video in sync when playing the mpeg stream from the TV card, in the past I was able to increase the buffer and for some issues that seemed to help, but there is already a delay because of the time it takes the TV card to produce the mpeg stream and increasing the buffer means increasing the delay even more, not so nice if you are watching something on the VCR and wanting to fast forward through commercials.

In the case of VLC it seems there are two issues, one the ability to play from /dev/whatever and some times the ability to even use VLC seems more likely to break during a development cycle than Totem or Mplayer, second my video card also has TV capability, which I have not got to work, but it still creates a /dev/videoX device, and I never know which card will be video0 and which will be video1. If the TV card gets the video0 slot VLC usually works, if the TV card gets the video1 slot it's less reliable and if I have tried to play from the video device taken by the video card first, playing from the TV card almost always fails no matter which order they were detected in.

As far as video in Banshee goes, I can understand the attraction from the standpoint that some people have a lot of music videos and want to be able to be able to play/manage both the audio and video music files from a single application, but outside of the music video case that I'm not real big on applications that want to manage your entire music and video library. This won't keep me from looking at Banshee to see what it's current state is because my resistance is more about what these applications don't do than what they do, as in if they don't provide a mechanism to play files from their existing location without adding them to your library, don't let you specify more than one location for your library, don't work simply and efficiently when you specify a file to play from the command line or when you right click in the file manager and use the 'Play with' option on the context menu, etc...  

Later, Seeker

---

### Post by Harry33 on 2011-03-04
> **seeker5528 said:**
> What's *so* wrong with Totem that would make you want to completely get rid of it?
...


It is just my way of personalizing Ubuntu.
I've removed meta packages to be able to uninstall applications I do not use.
A number of packages in default setup I cannot even use
(like ~20 or so xserver-xorg-video-* packages).

For me VLC really works fine.
I use it to watch music videos (HD) etc... and also to watch DVD's (from /dev/sr0). All works.
Totem just is not my type of application. It is not able to play high bitrate HD's. The gui is extremely poor ... there are a lot of reasons.
But I like Nautilus thumbnails :P.

---

### Post by seeker5528 on 2011-03-04
> **Harry33 said:**
> It is just my way of personalizing Ubuntu.

That I can understand.

> Totem just is not my type of application. It is not able to play high bitrate HD's.

High bit rate?

I don't know what the bit rate of the HD TV stuff is, but I'm pretty sure I have played stuff I have recorded in MythTV with Totem without any issues.

Seeking seems to be more of an issue some times with totem, not really a bit rate of HD issue, more to do with gstreamer+encoding.

Don't have any mpeg 4 stuff to see how that works, but that also would be more of a format issue than a bit rate or HD issue.

If you have an nVidia card, use vdpau, and have an older CPU that may make a difference between being able to play HD content or not. 

My guess would be that just being able to play or not would almost always have more to do with video format rather than bit rate.

But if it doesn't work and something else does, people usually probably don't care why.

>  The gui is extremely poor

That's a whole other can of worms. Often I either specify a file to play at the command line or browse with the file manger and use double click or 'right click'+'Open with'. Often my only interaction with the player is using the wheel on the mouse or the cursor keys on the keyboard to skip forward or backward, 'F' key or double click in main video window to change to/from full screen, etc.... :P

I do prefer VLC for DVD playback whether I'm in Linux or Windows, but the GUI never factored into that decision in any way, I don't find the GUI in any of the players to be all that great.

Later, Seeker

---

### Post by Harry33 on 2011-03-05
> **seeker5528 said:**
> That I can understand.
...
Later, Seeker

Thanks for your comments and views.

**High bit rate, HD (1920x1080 or higher)**
With this I mean 10.000 bps or higher
And it is true (like you said) that playing it well is an issue for gstreamer-encoding.
But in case of Totem, that is an limitation itself (meaning it depends on gstreamer).
Ffmpeg handles HD (1080i) fine.

File formats I use most are:
- mp4 (H.264/MPEG-4 AVC)
- windows media file (WMF)
- hd flash (FLV)

**NVidia and vdpau**
Yes I have Nvidia card (285GTX) and I need vdpau to play HD files well, even I have AMD Phenom II X4 955 (3.2 Ghz) CPU.
I know VLC is still experimental in vdpau handling, but it works anyway.

**GUI**
I also use Nautilus for file choosing. That is why I like thumbnails.

---

### Post by seeker5528 on 2011-03-05
I don't deal with anything that large. I occasionally come across an HD file on the internet I want to watch, which would most often be .flv or mp4, which I am assuming is encoded with h264 for mp4, don't know about .flv.

I don't come accross all that many HD things around places I would normally go. Most that I do come across would be between at 720 or somewhere midway between 720 and 1080. More often I come across videos that might have the resolution, but are not at a quality level you could really consider to be HD.

Don't know how the i versus p factors in, from one standpoint you are only writing half of the lines at a time so it's tempting to think 'it's half the work', but I don't know that it really makes that much difference in the decoding part of the equation.

Looks like vdpau is possible with gstreamer.....

[http://gstreamer-devel.966125.n4.nabble.com/vdpauh264dec-plugin-not-recognized-by-playbin-td3320184.html](http://gstreamer-devel.966125.n4.nabble.com/vdpauh264dec-plugin-not-recognized-by-playbin-td3320184.html)

But I don't see any indication that the necessary support is enabled in any packages available in Ubuntu.

If it was I think typing 'gst-inspect | grep vdp' at the command line would produce a result.

Later, Seeker

---

### Post by cariboo on 2011-03-05
We had a discussion about [high bit-rate video in Maverick]("http://ubuntuforums.org/showthread.php?t=1516670"). I know my system had a hard time with all of the 40Mbps videos I tried. I've got a fairly average system, dual-core AMD cpu, 210GT Nvidia graphics card and 2 GB ram, from experiments it looks like you needed a quad-core cpu to play high bit-rate content smoothly. I'm in the midst of downloading a 40Mbps video, once it's done, I'll see if better drivers make a difference.

BTW [Elephants Dream]("http://www.elephantsdream.org/"), still seems to be a good test of your systems capabilities.

---

