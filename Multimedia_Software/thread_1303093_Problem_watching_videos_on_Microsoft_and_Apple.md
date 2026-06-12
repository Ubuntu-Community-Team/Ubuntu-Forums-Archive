---
title: "Problem watching videos on Microsoft and Apple"
date: 2009-10-27
forum: Multimedia Software
---

### Post by rmcellig on 2009-10-27
I am using 9.10 but have the same problem under 9.04

I have the following installed on both systems:

win32codecs
medibuntu
mplayer
ubuntu-restricted-extras



I can't watch the videos on Apple's site as well as Microsoft's site.

What am I missing?

Thanks,

Randy

---

### Post by sliketymo on 2009-10-27
> **rmcellig said:**
> I am using 9.10 but have the same problem under 9.04

I have the following installed on both systems:

win32codecs
medibuntu
mplayer
ubuntu-restricted-extras



I can't watch the videos on Apple's site as well as Microsoft's site.

What am I missing?

Thanks,

Randy

:popcorn:Quicktime,Silverlight.

---

### Post by rmcellig on 2009-10-27
Where do I locate these and how do I install them?

---

### Post by entikryst on 2009-10-27
On the Apple website you can right click on the thumbnail and save link as and you will be downloading the .mov file

---

### Post by sliketymo on 2009-10-27
> **rmcellig said:**
> Where do I locate these and how do I install them?

:popcorn:Moonlight(an open source alternative for Silverlight) is available through synaptic.I am not sure about the Quicktime situation,as I do not bother with Apple,or for that matter,m$ video's.

---

### Post by HappyFeet on 2009-10-27
Install mozilla-mplayer, gstreamer bad and ugly codecs. They can be found in synaptic.

---

### Post by alexnikle100 on 2009-10-28
need to install quicktime web player, then you can play apple videos. when you try to play videos on apple's site, the install dialog box will pop-up

---

### Post by Allen3 on 2009-10-28
I have not experienced a problem running *Quicktime* video at our art department's website at the college campus. This worked okay in both *Hardy Heron* and now *Jaunty*. However I just downloaded *Moonlight* and this may solve a few problems running some of my *Microsoft* stuff. It may also restore the game graphic on _nfl.com_ which I've not been able to get to run correctly at all. We'll have to see if *Moonlight* fixes that.
> **sliketymo said:**
> :popcorn:Moonlight(an open source alternative for Silverlight) is available through synaptic.I am not sure about the Quicktime situation,as I do not bother with Apple,or for that matter,m$ video's.

---

### Post by vinutux on 2009-10-28
1. Apple using Quicktime [.mov or m4v] for its video

2. Microsoft using Windows Media Video [.wmv] integrated silverlight plugin

Both mov,m4v and wmv playable in ubuntu 

For apple site try various plugins for firefox from players like vlc,mplayer,totem [gstreamer] etc | You can enable and diable it from addon options in tools menu | you can even download .mov files with download mangers like Multiget or uget

There is a Silverlight equel plugin from novell:mono called Moonlight available....(but don't expect it works completely like silverlight)

---

### Post by rmcellig on 2009-10-28
alexnikle100

Where can I download/install the quicktime web player for Ubuntu?

---

### Post by vinutux on 2009-10-28
> **rmcellig said:**
> alexnikle100

Where can I download/install the quicktime web player for Ubuntu?

As far i know there is no such thing like that Apple not making any of its apps for linux platform

Instead you can install plgins of players like mplayer-mozilla plugin from mplayer vlc mozilla plugin from vlc amd totem plugin from totem-gstreamer [pre-installed]

---

### Post by rmcellig on 2009-10-28
So far I am SOL but I will keep looking and trying. I am using a pre release of 9.10 so tomorrow I will install the official release of 9.10 and try again. So far I really like 9.10!

---

### Post by directhex on 2009-10-28
apple.com videos should work FINE via the default media plugin (totem-mozilla) on Karmic and earlier versions. At a push, you may not have the required codec package installed (e.g. gstreamer0.10-plugins-bad or gstreamer0.10-plugins-ugly-multiverse)

---

### Post by HappyFeet on 2009-10-29
> **Allen3 said:**
> It may also restore the game graphic on _nfl.com_ which I've not been able to get to run correctly at all.

Installing moonlight will not fix that. It should work with only java and flash installed. Game graphics work fine for me without moonlight.

---

