---
title: "Anyone get HD movie files to playback in Ubuntu without Skipping"
date: 2008-02-06
forum: Multimedia &amp; Video
---

### Post by jimmah6786 on 2008-02-06
Anyone get HD movie files to play back without skipping. I cannot get any of my HD .mkv files to playback without skipping.
I know the machine can play them back becasue I did the dreaded act of reformatting it with WinXP and it plays back fine after I install K-Codec Pack.

Please see my other thread.

[http://ubuntuforums.org/showthread.php?t=688486](http://ubuntuforums.org/showthread.php?t=688486)

HELP PLEASE I don't want to lose Ubuntu to XP :( :(

P.S. I have all the codecs need installed under Ubuntu. I believe, including w32codecs, libcss2, Also tried using Mplayer, Xine, GStreamer, and VLC with no luck

---

### Post by shirilover on 2008-02-06
Playing HD H.264 video is processor intensive. In your other thread, you stated that you have a Xeon; however, this is not enough information to make a definitive conclusion.
So, is this a multi-core Xeon? Does it run at >2.0 GHz?
Have you tried using the following switches with mplayer: -framedrop -lavdopts fast:skiploopfilter=all ?
Are you using mplayer from the repos or compiling from SVN source? I get better performance by compiling mplayer myself.

---

### Post by jimmah6786 on 2008-02-06
> **shirilover said:**
> Playing HD H.264 video is processor intensive. In your other thread, you stated that you have a Xeon; however, this is not enough information to make a definitive conclusion.
So, is this a multi-core Xeon? Does it run at >2.0 GHz?
Have you tried using the following switches with mplayer: -framedrop -lavdopts fast:skiploopfilter=all ?
Are you using mplayer from the repos or compiling from SVN source? I get better performance by compiling mplayer myself.
Using MPlayer from Repos. While playing Matrix HD CPU1 runs at 90% CPU2-4 run under 20% Also sometimes get error message that says "To many Video Packets in the buffer:ERROR"

My Machine SPecs are:

2x Xeon 2.8Ghz Multi-core processors
3GB DDR Ram
200GB 7200rpm IDE Hard Drive
.

Is this a known problem with Ubuntu. Becasue it seems that every computer that I have ever installed Ubuntu on, cannot playback HD .mkv or avi files, even when the machine could in windows.

Sorry, just very frustrating.

---

### Post by jimmah6786 on 2008-02-06
:(

---

### Post by falkona on 2008-02-07
Hi,
I download SMPlayer and HD movies playback very fine.
Here is the way to download and install it:

1 Open console
2 Write "sudo apt-get update" without commas
3 Write "sudo apt-get install smplayer" without commas

Now you have smplayer who playback HD movies very well
I hope be useful for you.
:)

---

### Post by jimmah6786 on 2008-02-07
> **falkona said:**
> Hi,
I download SMPlayer and HD movies playback very fine.
Here is the way to download and install it:

1 Open console
2 Write "sudo apt-get update" without commas
3 Write "sudo apt-get install smplayer" without commas

Now you have smplayer who playback HD movies very well
I hope be useful for you.
:)

Alright so we are making progress :). It is skipping a lot less. Now I did notice that on the 720p mkv files I have skipping rarely occurs, only during things like fight scenes bla bla. However 1080p is still very choppy, although SMPLAYER did help improve this a little. Thank You Falkona.

Anyway I noticed that WHen i am playing movies my CPU is going up to 91-99 %. It is a 2.8GHz Xeon with 3GB of RAM so i dont see that to the be the issue.

Ideas?

Thank YOu

---

### Post by bsmith1051 on 2008-02-08
> **jimmah6786 said:**
> 2x Xeon 2.8Ghz Multi-core processors
Aren't these Pentium-4 generation processors?  Since there's no h.264 hw-acceleration in Linux you need to do everything on the general CPU, and I've often heard 2.8 GHz *Core2 Duo* (or Athlon64 X2) as the minimum for 1080p h.264.  Personally, I've got a 1.9 GHz X2 and I can barely play 720p h.264.

---

### Post by mad_max0204 on 2008-02-08
Is there anyone who is able to play HD movies in Ubuntu ??
This is gonna be really frustrating if its true that u cant. I even got me Nvidia for everything to work in Ubuntu. Hope theres some help on this subject.

EDIT: Did you install matroska libs from their site ?

---

### Post by clicq on 2008-02-08
I have a 1.8gz core2duo (e2160), overclocked to 2.7ghz, with 4gb of ram and a 500gb SATA hardrive, and I can play 1080p h264 videos fine (~80% max usage), so it is possible. I do think you need a CPU from the core/core2 line though to have any chance of playing it, so if your Xeon is from the p4 era you're going to have some trouble (mplayer and the like can't really utilize multiple processors, so having lots of cores that are idle doesn't mean anything).

(Though, for what it's worth, I don't watch videos under Ubuntu because of the ATI video tearing issues.)

When you say the videos "skip", do you mean they drop frames, or that the audio and video lose sync?

If you run "xvinfo" from a terminal, is your adapter listed? Are you using the xv output plugin for mplayer? (It's default, I think). Are you running compiz (sometimes disabling it helps)? You don't have any special mplayer config file do you? (it would be in ~/.mplayer/config).

---

### Post by PinkFloyd102489 on 2008-02-08
I play HD avi's on my 10 year old computer just fine in Totem. Albeit I have a CRT monitor, so it doesnt make a difference, but they're still HD episodes. My machine is a P3 450Mhz, 380MB RAM.

---

### Post by mad_max0204 on 2008-02-08
hehe nice work

---

