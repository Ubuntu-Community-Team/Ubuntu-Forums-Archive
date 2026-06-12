---
title: "Audigy 2 ZS - Unable to record just the line input."
date: 2009-12-20
forum: Multimedia Software
---

### Post by GiveLove on 2009-12-20
Hello People, :)

So I've been recording my bass guitar into my computer through the line input of my Creative Labs Audigy 2 ZS (SB0350) sound card using Audacity and Ardour since Ubuntu 8.10 with no problems. Mind you the mixer settings were not obvious(more on this later), but I was able to get it to work properly. 

So I've been running Ubuntu 9.04 for many months now. And used to be able to successfully record my bass guitar tracks from the line input into Ardour with no problems. But at the end of November, something changed where the line input no longer worked. I believe it coincided with a software update of Alsa around that same time. (These were Ubuntu Update Manager provided updates, it was nothing I did myself.)

What I found out is that something definitely changed for what I assume is the driver and/or mixer settings and preferences for my Audigy 2 ZS. It used to be both from within Ubuntu 8.10 and 9.04, that to record from the line input and monitor it through the line output at the same time while listening to other tracks being played back from within Ardour, that the "Analong Mix" preference setting both for playback and recording had to be check marked, unmuted, and the levels brought up. This is what I meant earlier about the mixer settings not being obvious. 

Technically, there should be a "Line Input" setting for both playback and recording to allow recording and monitoring of the line input signal. But there never has been. Only a "Line2", or "Aux2", which I have neither of those jacks on my sound card. So using the "Analog Mix" settings has been baffling, as technically this should be recording everything you hear in the line outputs of the sound card. But it previously worked correctly, so I didn't question it too much once I got it to work correctly. 

Since this software update occurred. The line input no longer worked. And through my own poor luck I happened to misdiagnose the problem as a broken line input jack. I later found out it was because now there is a "Line-in" setting for playback. But using that alone, I was not able to monitor/hear the signal from the line outputs. I had to also enable the "Analog Mix" setting in playback. So there is definitely a bug. As these two settings should not be intertwined. Now the other thing, is there is no corresponding "Line-in" setting in the recording section of preferences. Which I found odd. Why would the programmers add one but not the other? So I figured the "Analog Mix" setting for recording would work as it used to. 

But alas...  No.
Now this setting works as it really should. Which is to record the outputs of the sound card. So as I record my bass guitar track, the other track(s) being played back in Ardour also get recorded onto my track, which is a no-no. 

So what do I do?
I want to record audio in Linux as I have always done. Why would this update break the functionality so badly? 

Please help, I have the creative itch to record music, but obviously am currently unable to do so. 

GiveLove

---

### Post by GiveLove on 2009-12-27
Hello People, :)

I fixed this problem by updating Alsa, using the Alsa upgrade script created by "soundcheck". Thank you sir!
[http://ubuntuforums.org/showthread.php?p=6589810](http://ubuntuforums.org/showthread.php?p=6589810)

The interesting thing is, that the "Line-in" playback and "Analog Mix" playback controls are stilled intertwined. They must both be enabled and the levels moved the first time they are enabled to hear sound from the line input of my sound card. 

There is still no "Line-in" recording control. But the good thing is that the "Analog Mix" recording control works as it used to, which is to just record the line input level and nothing else. 

So I've already been able to record my bass guitar again! Yay!!! :D

---

