---
title: "strange audio feedback problem"
date: 2007-01-07
forum: Multimedia &amp; Video
---

### Post by eclectic4 on 2007-01-07
Hello,

This is a copy of a post I made to LinuxQuestions.org, which has gotten no response there after a week.  I also tried web searches and chatted with someone at qunu, to no avail.  I'm hoping someone here will be able to give me a clue.  

I installed Ubuntu Edgy a while ago, and ever since then I have been having a very strange problem, which is that I get audio feedback, which sounds exactly like there is a microphone sitting right in front of a speaker, but I have no microphone attached, and the sound seems to be a software glitch.

It happens with either of two different speaker systems, which work fine when attached to my other computer here (running Ubuntu Dapper).

It happens whenever the PCM level on my volume control is above 50-60%, even if the master volume level is turned down to about 20%. This makes it impossible to get an audible level for a sound file that is recorded with low volume.

It happens with any media player I use to play an audio or video file; XMMS, RealPlayer, Totem, VLC, etc., AND it happens if I raise the PCM level above that point with NO SOUND FILE playing.

I have a trial installation of Suse 10.1 on this computer, in dual boot mode. When I boot into Suse this problem DOES NOT happen. I can jack the (PCM) volume up and the sound is fine. I ran Mandriva before Edgy on this machine, and Windows before that, and never saw this problem before. No hardware was changed in all this time.

The on-board audio system is disabled in the bios.

My sound card is a Creative SB PCI512, and the sound module, emu10k1, is listed online as the right one for this card.

I hope someone can help; maybe I should study how alsa and such work in depth, but the demands of the rest of my life are such that I'd have to wait several months for such a project and just put up with the problem 'till then.

Thanks in advance!!

---

### Post by lakerssuperman on 2007-02-24
I have a Sb Live 5.1 running the same module and have noticed the same distortion.  At first I thought I had blown my headphones but it also comes through on my desktop speakers and  on my 5.1 system through the digital out.  I tried also switching sound cards, thinking mine was dying and got the same problem.  I can only hear the problem when certain music or sounds are being played, it is very annoying.  I'm currently running Edgy 6.10.

---

### Post by KevinCole on 2007-06-06
In my case, I didn't start having problems til Feisty.  It now randomly changes volume and occasionally attacks me with an ear-splitting blast of feedback.  I'm guessing that I have something sharing the audio that shouldn't be, but who knows what I've done to it?

---

### Post by tgyorgyi on 2008-06-14
I have this problem in Hardy, except my FSC Amilo L laptop does have built-in microphones, and it is feedback from the microphones (if I tap on the built-in, I can hear the taps coming out of the speakers or headphones). Disabling the microphone helps for me if I only need sound one-way (listening to music), but VOIP is out of question this way, the sound test gives very messy results. :-(

---

