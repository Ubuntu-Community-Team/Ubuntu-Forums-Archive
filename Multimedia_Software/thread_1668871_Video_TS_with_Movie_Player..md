---
title: "Video_TS with Movie Player."
date: 2011-01-16
forum: Multimedia Software
---

### Post by Roasted on 2011-01-16
This may be a stupid question, but with Movie Player, how do I play a video_ts video? In VLC under media it has the option to open a directory, which is self explanatory that the video_ts option falls under. What about Movie Player?

---

### Post by inobe on 2011-01-16
i would imagine clicking media/ file/ movie will reveal a file manager to select a dvd or ts folder containing vob's.

---

### Post by mc4man on 2011-01-16
> What about Movie Player?
I believe it will only open as a playlist of the files in the VIDEO_TS

In that case it will fail on the .ifo's and .bub's but you could play thru the .vobs, though no disk navigation 
( and no choice of streams, not that Movie Player (totem) can do that anyway.

You may or may not be able to play it directly as an .iso w/ Movie Player, it doesn't here on maverick, though Movie Player (Xine) does. (the old totem-xine

What does work here with Movie Player (totem) is to mount the .iso, though again here I use cdemu which mounts it just like a cd/dvd drive - even pops up the autorun box. Don't know if a cli mount will work

---

### Post by Roasted on 2011-01-16
Well, that sucks. VLC is having poor audio playback (a split second mute every 20-30 seconds) so I wanted to use Movie Player instead.

Gah...

---

### Post by mc4man on 2011-01-17
Well a quick test - mounting an .iso w/ the typical sudo mount -o loop will allow Movie Player to play it as a dvd movie (to the extent Movie Player (totem) can.

Does vlc 'skip' on all files or just your VIDEO_TS ones?

---

### Post by Roasted on 2011-01-17
> **mc4man said:**
> Well a quick test - mounting an .iso w/ the typical sudo mount -o loop will allow Movie Player to play it as a dvd movie (to the extent Movie Player (totem) can.

Does vlc 'skip' on all files or just your VIDEO_TS ones?

Video_TS, AVI, and MKV are all that I've tried. They're live concerts, so it's obvious when you have a Pink Floyd song cranked and you hear an instant stop in the audio that is clearly not part of Gilmour's solo... 

This really only happens on my netbook as well, but when I look at the resources used I have a hard time thinking it's bottlenecked anywhere. Likewise, Movie Player works great with the AVI files where there's no audio skip at all...

---

### Post by BicyclerBoy on 2011-01-17
Excellent musical taste by the way..
You did not say what DVD.
"Pulse" is one of best live multi-channel concert recordings ever.

I only play video in MythTV so can not help.

Would not think a netbook would do any concert the audio justice deserved.
Buy it should handle MPEG-2

Is this streaming from server over wifi ?

---

### Post by Roasted on 2011-01-17
I know that a netbook doesn't scream quality, but it would be nice to have because I often work out in the garage, and I would like to plug in the netbook (as it is my only laptop) to my stereo there and at least have a (relatively small, but still viewable) screen of the concert.

Yes - The live concert in question by Pink Floyd is Pulse. I rarely listen to many other concerts by them because Pulse is just *that* good, in my opinion.

I've also noticed this with Pearl Jam's 2003 performance @ Madison Square Garden which is an AVI, and Candlebox's 2008 Seattle concert which is Video_TS, and lastly Oasis in 2008 Wembley which is an MKV. All of these exhibited similar characteristics, but only with VLC. Movie Player was fine, though I'm not sure I used Movie Player with ALL of them. I know I used Movie Player with the Pearl Jam concert, which is an AVI, and had ZERO skip whereas VLC gave me periodic audio skips every 20 seconds or so.

Either way, it's isolated to being a netbook thing, but only with the netbook/VLC combo. VLC on my desktop with the exact same concerts gives me no issues. But like I said when I check things out in the system monitor, I just don't think the processor or memory or anything else is bottlenecking it.

And no - all of this playback is done locally. I am streaming nothing at all.

---

### Post by mc4man on 2011-01-18
While probably ineffectual you could try upping the cache for various access modules
(tools - pref's - 'show settings - all' - Input/Codecs - Access Modules.

If inclined and on maverick+ maybe try the 1.2+ version of vlc - there have been some changes to pulse. (plus it's a superior version.

An easy way if not inclined to build is to add this ppa, updates every few days
[https://launchpad.net/~videolan/+archive/master-daily](https://launchpad.net/~videolan/+archive/master-daily)
(note - only for maverick and natty

If trying and not happy - to revert just disable the ppa and remove vlc-data which will remove all vlc packages. Then re-install

---

### Post by Roasted on 2011-01-23
Well I gave up on the VLC thing for now, however I'm still curious about playing a video_TS with movie player just for sake of knowing. Is there any way to do this? I'm getting nothing but errors. :(

---

### Post by akand074 on 2011-01-23
> **Roasted said:**
> Well I gave up on the VLC thing for now, however I'm still curious about playing a video_TS with movie player just for sake of knowing. Is there any way to do this? I'm getting nothing but errors. :(

I love VLC. I use it primarily for videos. But you could use mplayer. I've used [this]("http://ubuntuforums.org/showthread.php?t=1542240") method to compile mplayer with like all the libraries/codecs in the world and using smplayer as a GUI Front-end. It's my backup source for if something doesn't work with VLC everything runs on that.

---

### Post by Roasted on 2011-01-23
Okay. I'm getting a little tired of going back and forth. Here's what I've found so far...

VLC - works great, unless it's an AVI. AVI files skip for some reason.
Totem - works great, unless it's video_TS. Even when I convert the video_TS to MKV using Handbrake, it'll freeze at random times when playing the MKV. Useless program at this point.
MPlayer - same behavior with the MKV's as Totem has.

Is there a player that works better for lower performing hardware? Or is there a way to make VLC not skip in the way it does? I find it frustrating to see that this netbook can't do video playback worth a **** when I talk to others that play back in 1080p with zero issues using VLC.

ANY feedback?? Should I just accept that netbook video playback (despite some people claiming they can get 1080 on netbooks) is just... not great??

---

### Post by akand074 on 2011-01-23
> **Roasted said:**
> Okay. I'm getting a little tired of going back and forth. Here's what I've found so far...

VLC - works great, unless it's an AVI. AVI files skip for some reason.
Totem - works great, unless it's video_TS. Even when I convert the video_TS to MKV using Handbrake, it'll freeze at random times when playing the MKV. Useless program at this point.
MPlayer - same behavior with the MKV's as Totem has.

Is there a player that works better for lower performing hardware? Or is there a way to make VLC not skip in the way it does? I find it frustrating to see that this netbook can't do video playback worth a **** when I talk to others that play back in 1080p with zero issues using VLC.

ANY feedback?? Should I just accept that netbook video playback (despite some people claiming they can get 1080 on netbooks) is just... not great??

That's odd. VLC has always played everything without a problem on any system I've used in the past. All I do is install the VLC from the repositories with no changes/extra downloads and then build mplayer as backup.

If I were you, I would most definitely not just accept that your netbook is having trouble with video playback.

---

### Post by Roasted on 2011-01-24
> **akand074 said:**
> That's odd. VLC has always played everything without a problem on any system I've used in the past. All I do is install the VLC from the repositories with no changes/extra downloads and then build mplayer as backup.

If I were you, I would most definitely not just accept that your netbook is having trouble with video playback.

Well, I'd been in the IRC chat for quite a while, googled, made changes, and tried other applications. No dice.

Not sure what else I can do.

---

