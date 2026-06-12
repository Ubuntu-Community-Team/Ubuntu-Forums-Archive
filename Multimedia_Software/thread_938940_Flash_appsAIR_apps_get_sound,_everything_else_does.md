---
title: "Flash apps/AIR apps get sound, everything else doesn't"
date: 2008-10-05
forum: Multimedia Software
---

### Post by EricJosepi on 2008-10-05
**[SIZE="4"]PLEASE DISREGARD! libflashsupport did solve my problem.  I just needed to restart Firefox first.  I apologize.[/SIZE]**

Hello,

Let me preface this first by saying I have gone through and followed the steps in the Comprehensive Sound Problems Guide and have updated to alsa version 1.0.17 and have alsa-oss and libflashsupport installed.  I am using an HDA Intel card with a Realtek ALC262 chipset.

I am having some problems with my sound card, or possibly with my installation of Adobe Flash/AIR.

When I use a Flash or AIR app, the sound works fine (I get my little ding noise in twhirl and Youtube sound).  The problem is, once I have used an AIR app or watched a flash video on youtube or anywhere else, I cannot use or access the sound card (or possibly my gstreamer codecs) with any other app.  For example, after watching a flash video I opened Songbird to play a .flac file and while the software would recognize something was supposed to be playing (i know this because the lyrics fetcher plugin went and found the lyrics) the indicator never left 0:00.  I could slide it around the bar just fine and yet nothing would play.  I tried it again in Totem and encountered the same issue.  I tried opening a video in VLC to see if there was the same problem and while I could get video playback, there was no audio.

Any advice on what I should do to try to fix this?  Should I dump Flash and AIR in favour of open source alternatives?

I've tried modprobe snd-hda-intel to no avail either.

---

