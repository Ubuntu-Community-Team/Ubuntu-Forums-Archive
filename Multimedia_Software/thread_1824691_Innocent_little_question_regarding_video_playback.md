---
title: "Innocent little question regarding video playback?"
date: 2011-08-14
forum: Multimedia Software
---

### Post by eddie3000 on 2011-08-14
After reading many many threads on various forums about the issue, and realizing that I have the same problem with all my 5 computers, the oldest being about 10 years old and the newest only a few months, I thought I might ask this little innocent question.

When is Ubuntu going to playback videos as well as most video programs in Windows?

All my computers play videos perfectly using media player classic in wondows. I have never been able to play videos in Ubuntu as well as in windows. I've had this problem for years. I haven't managed to solve it myself. 

When am I going to be able to completely ditch MS Windows?

---

### Post by JRV on 2011-08-14
What is wrong with your video playback?

What Program are you using?

Some play best in mplayer and some are best in VLC.  In Windows I used to have to switch between Media Player Classic and VLC.

Do you have all the proper codecs loaded?

```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by CatKiller on 2011-08-14
> **eddie3000 said:**
> When is Ubuntu going to playback videos as well as most video programs in Windows?

Never, probably. As long as mathematics is illegal in the US, the pool of developers able to work on the problem and the techniques they can use are limited. Lots of things are prevented from working out-of-the-box because everyone is precluded from the possibility of distributing that software from people in the US and Australia. You pay your tithe with your Windows licence fee.

I've never had any problems playing videos on Linux, however, and I did used to have videos that didn't play well in Windows.

---

### Post by eddie3000 on 2011-08-14
Thank you JRV for your interest. Yes, I have gone through all these things, tried all possibilities available in Ubuntu Software Center, different players, codecs, configurations, different versions of graphics drivers, and so on. I just can't get it to play right. 
And yes Catkiller, it could be it's a licencing issue.
To be honest, some friends and family members don't even notice that the video playback isn't ok. 
I've got intel and amd processors, ati and nvidia graphics cards, tried various setups, and none of them play videos well. But they do with windows.
Basically, I got up this morning wanting to argue and here I am. Spitting out a bit of fire. :evil:
I would also like to ditch windows for good too, but until ubuntu  doesn't solve this little issue, I don't think I will completely get rid  of it.

When will ubuntu playback videos as well and smoothly and easily as in windows??? 

The basic problem I tend to get is image tearing specially with fast video movements.

---

### Post by CatKiller on 2011-08-14
> **eddie3000 said:**
> 
The basic problem I tend to get is image tearing specially with fast video movements.

You probably want to be using vertical sync.

---

### Post by eddie3000 on 2011-08-15
I have tried that already, thank you. Doesn't work. Nothing seems to work. Whatever I do, the video isn't right, in fact sometimes it gets worse!
I was impatient for the 11.04 release hoping that they solved the issue. It was a huge dissapointment, not just because of the video still playing badly, but they incorporated a new layout that I did not like. It gave me more problems than solutions, so I went back to 10.10.
I think Ubuntu has to address this problem because it is a very big one for me and many people. I run ubuntu on all my computers, and until now I have just put up with the video tearing issue, but I have decided install windows on one computer just to watch videos. It's a pitty.

---

### Post by BicyclerBoy on 2011-08-15
...

---

### Post by eddie3000 on 2011-08-15
Ok! Let's assume I am doing something wrong. 
I hardly play HD video at all, I get the video tearing with standard definition video.
Lets use te weakest computer I have, my acer aspire one, with an atom n270. Yes, it's a tatty little bugger, but it plays standard definition video flawlessly with WinXP. What settings would I have to tweak for perfect reproduction in Ubuntu 10.10?

---

### Post by BicyclerBoy on 2011-08-15
..

---

### Post by aeiah on 2011-08-15
> **eddie3000 said:**
> Ok! Let's assume I am doing something wrong. 
I hardly play HD video at all, I get the video tearing with standard definition video.
Lets use te weakest computer I have, my acer aspire one, with an atom n270. Yes, it's a tatty little bugger, but it plays standard definition video flawlessly with WinXP. What settings would I have to tweak for perfect reproduction in Ubuntu 10.10?

my acer aspire one works fine for 480p video and below. i run xbmc on it occasionally when plugging it into a tv, or mplayer on the normal desktop.

this is with lubuntu though, and just the usual default video settings.

---

### Post by drawkcab on 2011-08-15
I think one of the problems for me was randomly following people's advice until my config files and settings were irredeemable!

In this last round I did this:

1.  reinstalled ubuntu 11.04 x64 with restricted extras
2.  disabled unity, enabled classic w/compiz
3.  installed x264 with this guide:  [http://ubuntuforums.org/showthread.php?t=786095&highlight=howto+x264](http://ubuntuforums.org/showthread.php?t=786095&highlight=howto+x264)
4.  installed smplayer (for .mkv), enabled vdpau and set threads to 2 and expanded cache 
5.  installed vlc (for .avi)
6.  installed x64 flash beta (huge improvement)
7.  installed xbmc

Video quality across the board on my nettop (atom 330) is just as good as windows if not better.  I'm sitting in front of a nearly perfect 720p picture as we speak.

---

### Post by eddie3000 on 2011-08-16
Thanks guys for your patience. I was already losing mine.
I tried editing the /etc/X11/xorg.conf file in the past, and have really cocked things up. I really need the time to mess with these files just in case I need to fix the messed up by myself installation.
I will try what drwakcab suggests in that particular order when I have some time, maybe this evening, that seems pretty straightforward. I'll keep my fingers crossed. If that doesn't work I'll just stick with windows for video playback until Ubuntu 12.04 maybe.
Thanks everybody for your advice and patience. I've been trying to get good video from ubuntu for years now without luck, but I am no expert, and that complicates things.

---

### Post by BicyclerBoy on 2011-08-16
x264 is an encoder only.
Pointless running this on an atom & for video playback.

VDPAU is only available to nVidia GPU h/w..
Do you have nVidia GPU or just intel chipset like the OP ?

1. is almost mandatory..how can you not have this..
6. will help if you use flash

The OPs problem with the netbook could just be sync with vertical blank setting..
Easy to check with glxgears.

---

### Post by lhnitz on 2011-08-17
Not so innocent!  I have installed all available movie players on an Ubuntu 64 bit installation.  I cannot see more than the black screen and the error notice in utube, and the same in trying to play videos--a black screen.  I am completely beyond guessing any more.  Is there any package for which I can do a one-time install and get utube and video pictures?

---

### Post by Duncan Williams on 2011-08-17
My video reproduction is the same in windows and linux.
It never used to be though.
The main things that resolved this and improved general responce.

Make sure all window manager settings are correct.
Using latest nvidia drivers (280 for this card)
Settings in nvidia xserver settings 
(ie/quality not high-quality and no fixed anti-aliasing and no blank to vsync)

---

### Post by eddie3000 on 2012-07-05
It's been a looong time since I started this thread. Just wanted to let you know that now, I have installed ubuntu 12.04 on one of my computers with an amd processor and ati graphics, and this time (for whatever the reason) I get perfect video playback straight out of the box. I dunnow why. I also have a new laptop with an i7 processor and ubuntu studio12.04 and perfect playback too. I guess I was having problems maybe due to hardware combinations and/or not well developed software. Just guessing though.
Cheers!

---

### Post by wildmanne39 on 2012-07-05
Old thread closed.

---

