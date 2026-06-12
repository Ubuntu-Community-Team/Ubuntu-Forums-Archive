---
title: "Difference in playing DVD on 2 Ubuntu computers (movieplayer vs. vlc)"
date: 2009-09-29
forum: Multimedia Software
---

### Post by mjp29 on 2009-09-29
Someone had commented that any video player can play DVD movies in Ubuntu, and that is probably true.  However, I've had different results with 2 different computers (movieplayer vs. VLC media player).

I installed ubuntu-unrestricted-extras and libdvdcss2 and medibuntu on both an old HP Pentium 4 desktop and on an old Dell Celeron laptop computer.

My results are (which are probably due to hardware like graphics cards/memory or something) are below:

The Dell laptop will play a DVD movie using Movieplayer or VLC mediaplayer (although Movieplayer did tend to pause out and go into a slow motion phase on the dvd I was trying to play - it paused out in the previews so i clicked the forward button and got the movie playing fine).

The HP desktop simply refused to play a DVD movie with Movieplayer but VLC mediaplayer played the same DVD movie perfectly.

Just an observation here and perhaps helpful to some that don't have 2 Ubuntu boxes.  Comments from forum members please.

---

### Post by Littleweseth on 2009-09-30
In general, I've always observed VLC to play anything I throw at it. MPlayer is also superb.

The problem with Movie Player (totem) is that it uses the modular gstreamer plugin framework, so you can install different codecs as you require them. Unfortunately, this also makes it very easy to 'miss' installing codecs, usually the codec you need *right now*. ;)

VLC brings all of its own codecs (as I understand it), so it's never missing any, and thus everything always works.

Viva la VLC!
- L.

---

