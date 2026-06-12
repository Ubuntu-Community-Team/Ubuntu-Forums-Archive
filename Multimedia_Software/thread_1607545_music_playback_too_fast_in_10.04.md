---
title: "music playback too fast in 10.04"
date: 2010-10-27
forum: Multimedia Software
---

### Post by tunzo on 2010-10-27
Hi there.  I am having music playback issues in lucid right now.  When I try to play music through any player, the music plays at a slightly higher speed - roughly 10% faster (a 3:17 song finishes in 2:58).  I tried installing 10.10 and had the same problem, and I just went back to 10.04 with a fresh install and still seeing the issue.  Is this a common problem for people?  My sound hardware is the following as reported by lspci

00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)

For reference, I also have 2 other boxes in the house running 10.04 with different sound hardware with no issues.  Their hardware are:

00:06.1 Audio device: nVidia Corporation MCP55 High Definition Audio (rev a2)

00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)

if anyone has any advice i would greatly appreciate it

-tunzo

---

### Post by tunzo on 2010-10-29
Does anyone have any ideas on this issue?
 
edit:
original post automatically interpreted some characters as a smiley face thing.  Sentence should read that a 3:17 song finishes in 2:58

---

### Post by Jormeliini on 2010-10-29
> **tunzo said:**
> Hi there.  I am having music playback issues in lucid right now.  When I try to play music through any player, the music plays at a slightly higher speed - roughly 10% faster (a 3:17 song finishes in 2:58).

Could be a sample rate problem. Playing 44.1 kHz audio at 48 kHz sample rate would cause that. PulseAudio should handle sample rate conversions. Hopefully someone can help you.

---

### Post by tunzo on 2010-10-29
Hi thanks for the reply.  I installed the pulse audio utilities and it appears that my rate is 44100.  i am assuming that is the correct frequency, but i don't know how to tell for sure, or how to change it if i needed to.

---

### Post by tunzo on 2010-11-04
update:  i recently installed a fresh 10.04 mythbuntu on this machine, and the music plays at normal speed in vlc under xfce.  are the codecs that come with xfce different than those that come with gnome?  

this is speculation on my part here, but perhaps the codecs under gnome (is it gstreamer) don't deal with the via sound devices quite right?

anyway, while i don't have a root cause, my issue is resolved for now.

tunzo

---

