---
title: "Can't play DVD in Mplayer"
date: 2009-06-13
forum: Multimedia Software
---

### Post by irv on 2009-06-13
I know there are some older post on this, but I am looking for only two answers. First, I installed 9.04 from a cd a couple of days ago. I thought I had everything working OK until I went to play a DVD last night in Mplayer.
I can get DVD's to play in VLC and smplayer, but when I try to get them to play in Mplayer I get these error:
[ATTACH]117509[/ATTACH]

[ATTACH]117510[/ATTACH]

[ATTACH]117511[/ATTACH]
My first question is, What plugin am I missing? and where do I get it?

Also it will not play in Realplayer11 I get this message:
[ATTACH]117512[/ATTACH]
Second question, Is there a problem with Realplayer 11 that it will not play DVD's?

---

### Post by mc4man on 2009-06-13
By Mplayer assuming you're referring to totem(gstreamer) which needs some gstreamer plugins to be able to do just about anything including dvd playback. (which it does poorly at best.

The most common suggestion is to install ubuntu-restricted-extras which will install most of the plug-ins and a bunch of other stuff you may not want or need.

So you can install that or you can install the plug-ins manually from synaptic, search gstreamer

The more useful are
bad and bad multiverse (1st. and 4th listed
ugly and ugly multiverse (1st and 4th
gstreamer-pitfdll
gstreamer-ffmpeg
And any others you see fit

A more useful totem player is totem-xine, if installed then it needs to be added to menu (edit menus, add Movie player (xine)

Edit: totem-xine requires libxine1-ffmpeg for dvd's

---

### Post by irv on 2009-06-13
> **mc4man said:**
> By Mplayer assuming you're referring to totem(gstreamer) which needs some gstreamer plugins to be able to do just about anything including dvd playback. (which it does poorly at best.

The most common suggestion is to install ubuntu-restricted-extras which will install most of the plug-ins and a bunch of other stuff you may not want or need.

So you can install that or you can install the plug-ins manually from synaptic, search gstreamer

The more useful are
bad and bad multiverse (1st. and 4th listed
ugly and ugly multiverse (1st and 4th
gstreamer-pitfdll
gstreamer-ffmpeg
And any others you see fit

A more useful totem player is totem-xine, if installed then it needs to be added to menu (edit menus, add Movie player (xine)

Edit: totem-xine requires libxine1-ffmpeg for dvd's

Thanks for the help and the reply.
I forgot to install totem-xine. After do this it worked.
I am still not sure what going on with RealPlayer 11.

---

### Post by mc4man on 2009-06-13
> I am still not sure what going on with RealPlayer 11.

If your referring to dvd playback (commercial) with the linux realplayer, I don't see how that would be possible.

There's no way realplayer could use libdvdcss2 so it would need to have an internal decoder and be licensed like powerdvd for linux or lindvd. Even if it was (which it isn't), I can't see them giving that away for free.

---

### Post by irv on 2009-06-13
> **mc4man said:**
> If your referring to dvd playback (commercial) with the linux realplayer, I don't see how that would be possible.

There's no way realplayer could use libdvdcss2 so it would need to have an internal decoder and be licensed like powerdvd for linux or lindvd. Even if it was (which it isn't), I can't see them giving that away for free.

If you look at this screen shot: [ATTACH]117543[/ATTACH]
It says The following components are required: x-nautilus-desktop and 
URL: x-nautilus-desktop:///Signs.volume.
The Signs.volume is the DVD I was try to play with RealPlayer 11. From this message I thought it might work.

---

### Post by mc4man on 2009-06-13
[https://helixbeta.org/projects/player/forums/entry/1806](https://helixbeta.org/projects/player/forums/entry/1806)

I doubt anything has changed or will (unless they decide to build  realplayer for linux that's zipped up tight and costs $

---

### Post by irv on 2009-06-13
> **mc4man said:**
> [https://helixbeta.org/projects/player/forums/entry/1806](https://helixbeta.org/projects/player/forums/entry/1806)

I doubt anything has changed or will (unless they decide to build  realplayer for linux that's zipped up tight and costs $

Yes, I agree, I just had this thought that there might be a possibility  that they would support DVD playing. I get News clips that run in RealPlayer, but I only use it once in a while. One thing I wish was that Netflix would support Linux. (Their player is for Windows only). I watch a few flicks on the net, but I have to use Windows to do that. I can watch flicks from hulu.com in Linux and that nice.
Thanks for all the input.

---

