---
title: "no video hardware acceleration/Vsync"
date: 2009-11-01
forum: Multimedia Software
---

### Post by onemanclapping on 2009-11-01
Hi.

I just freshly installed Ubuntu 9.10.

I used to have video hardware acelleration with xvideo in VLC when I was at fullscreen mode. If I right-clicked the video, the VSync would be lost, so I could always be sure it was activated.

Now, I don't have anything! The video has no Vsync, as I can see lots of horizontal lines from bad syncing, even with Xvideo output activated...

Btw, before, the video used to show on a separate window, now it appears "normal".

What happened? Can someone solve this problem?

Thanks in advance!

- onemanclapping

---

### Post by onemanclapping on 2009-11-01
I would appreciate if, at least, someone could tell me if they have or do not have the same problem. Thanks again.

---

### Post by onemanclapping on 2009-11-01
I found out that if I shut Compiz down (System->preferences->Appearance->Visual Effects->None) the video plays well!

So, any thoughts? I would like to keep running compiz as I used to...

---

### Post by Lisio on 2009-11-08
onemanclapping, I have the same damn problem.
Using Ubuntu 9.10, nVidia driver (v.185) with both VSync options on I don't see it working in Totem video player. But switching the visual effects off makes it work. Both Standard and Extra options in Compiz affects on VSync in wrong way.

---

### Post by doixanh on 2009-11-17
try this out guys:
- turn on desktop effects
- open Compiz Config Settings Manager -> Display Settings
- tick "Sync to VBlank" at the end of the form

GL :D

---

### Post by onemanclapping on 2009-12-07
> **doixanh said:**
> try this out guys:
- turn on desktop effects
- open Compiz Config Settings Manager -> Display Settings
- tick "Sync to VBlank" at the end of the form

GL :D

I tried that, naturally :/

I guess this is one of so many problems of this new ubuntu version... I watch videos all the time, so I actually installed Windows 7 so I can watch them nicely... It's a real shame tho, because i've been using ubuntu fulltime for the past year and now had to stop doing it :(

But now with dxva, nvidia cuda, corecodec, etc, it doesn't make sense for linux not to be up to date with these awesome technologies... :/

For example, I absolutely can't watch a 1080p movie on ubuntu, while in windows I only use about 5% of CPU...

I know it's nobody's fault, but it's a real shame to release a version worst than the previous one...

---

### Post by rossmoore on 2009-12-08
Have you tried compiling mplayer for vdpau? There are a few guides around ([http://blog.avirtualhome.com/2009/02/10/compile-mplayer-with-vdpau-support-on-ubuntu/](http://blog.avirtualhome.com/2009/02/10/compile-mplayer-with-vdpau-support-on-ubuntu/) for example, but there are better ones I think). It's hardly easy though, and it's a pity everyone's favourite player, vlc, hasn't got a good patch yet. I saw some French students were working on it this summer, but they don't seem to have created a production-quality patch that has made it into any release.

People (I have yet to succeed on my atom+ion machine) have been viewing 1080p with that, with < 25% CPU I think. And SMplayer gives you a reasonably good interface for your mplayer build if you succeed in building it, then running with the right options...

Re: VBlank, I haven't got it work properly in Karmic yet. Have you tried Fusion-icon yet to control Compiz a bit more easily? You can turn it off with one-click there, and apparently "direct rendering" and "loose binding" can impact VBlank too. As I said, I haven't fixed the problem myself yet (and haven't tried everything I can think of yet since I can't work for long on it) - just ideas that I have seen work in the past.

---

### Post by rossmoore on 2009-12-14
Just an update: I have got SMplayer up and working on an atom+ion machine now. The nvidia team ppa has the latest drivers and a version of mplayer with vdpau support.
[https://launchpad.net/~nvidia-vdpau/+archive/ppa](https://launchpad.net/~nvidia-vdpau/+archive/ppa)

Follow the instructions here:
[http://ubuntuforums.org/showthread.php?t=1037625](http://ubuntuforums.org/showthread.php?t=1037625)
to call mplayer with the right options, or to set up SMplayer correctly.

Hopefully your faith in linux and video will be restored, onemanclapping.

---

