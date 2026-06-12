---
title: "ALSA dies randomly in Jaunty Jackalope 9.04"
date: 2009-07-30
forum: Multimedia Software
---

### Post by crates on 2009-07-30
Hey, guys. I hope I'm not asking a stupid question here, because I tried my best to search the forums for a resolution and couldn't fix this. I've been using Linux for twelve years now as my primary operating system, running Jackalope both at home and at work presently, and this is the first time I've encountered this kind of issue.

Basically what happens is that ALSA works fine for a while, and then when specific programs run, my sound drivers get glommed and die. If I run Audacity, my sound dies. If I run Movie Player, my sound dies. Running VLC usually works and doesn't kill the sound, but occasionally it will.

Whenever this happens, I have to restart Firefox, which is a real pain because it means that I have to reload some 100+ odd tabs, often many of which are YouTube videos that try to create the world's most cacophonous symphony of din when they all load at the same time. If I've closed the offending program and restart Firefox, the sound returns.

I've tried a few different resolutions from searching, like adding the "options snd-hda-intel model=3stack-6ch-dig" or whatever it was to the configuration files and then restarting ALSA, but alas, it was all to no avail. I'm running an HP m9520f PC at home, where the problem occurs. I don't have this problem at work, nor have I ever had it on any other PC I use.

Oh, and I'm using a direct digital wire from my sound card to the 6.1 channel Dolby surround sound audio system in my apartment.

This problem is driving me Hannelore "Hanners" Bananers. In pajamers. Please help!

Love,
-- Crates
[http://tinyurl.com/socr8s](http://tinyurl.com/socr8s)

---

### Post by crates on 2009-08-15
So this problem happens with great frequency (thanks for all the replies and helpful comments, by the way)... but today, there was a new development. My sound cut out as usual when I loaded Audacity; however, after closing Audacity, I went to load a YouTube video, and I heard a tinny version of the audio from it, as if heard from a cell phone.

Turns out, it was playing from my microphone. So now it appears that the problem is that whenever I load the wrong sort of application, my audio-out is routed to the microphone port instead of the digital output port.

Could someone-- ANYONE-- offer input on this? I honestly don't even care if it's helpful input at this point; I'd just like to know that I'm not wasting my time on these forums.

---

