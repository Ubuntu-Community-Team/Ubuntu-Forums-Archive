---
title: "Hardy not working out, can't get sound to work"
date: 2008-06-25
forum: Multimedia Software
---

### Post by jukingeo on 2008-06-25
Hello all, 

I am new to Ubuntu (and Linux in general).  The reason I began to investigate Linux in the first place is because of the current future of Windows and Microsoft.   As of now I feel that Windows is a very overbloated OS and that MS has too much control over it.  I grew tired of the constant updates and more and more space is required of Windows on my hard drive.

Now that Vista is out, I been hearing the many problems with it.  I also hear it is so bloated that many people were forced to update their machines and you pay over $100 for that.  So I made the decision to look into Linux.  Not necessarily just for the fact that it is open source and free but I wanted to see what the alternative to Windows is like.  So the free aspect was an added bonus.  The fact that I have two additional mouths to feed and the increasing costs of gas and oil (and a decrease in pay), welcomes this aspect of Linux with open arms.

I did have some requirements in that I do like to play games and I am very much into audio editing work and I do dabble with video editing.  So I wanted to check these features out mainly.

I am very much into audio editing and my favorite program right now is Ableton's Live.  However, it too has become a very expensive program to buy.

After hearing the alternatives in Linux: Ardour, Audacity, Rosegarden, Hydrogen.  I decided to make the jump into Linux.

I chose Ubuntu because it was touted as the easier of the Linux distributions to get into.   I bought a "Linux for Dummies" book and it came with Ubuntu version 6.10.  And loaded it on directly from the Live CD.

I had trouble with this version with mounting my drives and was told it was an old and outdated version.  So I updated to version 7.10 and my drives mounted OK and I was able to play around with it.  It looked/worked well enough that I wanted to go further and then I did a full install of Hardy with a dual boot to Windows XP.

Right off the bat I had no sound.  I found out that my sound card, the Sound Blaster X-Fi isn't completely supported in Ubuntu.  The choices were the hard road...to try and get the ALSA driver to work, or the easy way, load up the OSS drivers.  I opted for the latter.

Ok, so now I had partial sound.  Internet was working, Totem Player was working, Audacity worked, and so did Cinelerra, but I had no sound in my games.  I was told to install Pulse Audio as an overlay.  That did work, but not very well.  The GENS (Sega Genesis) emulator had distorted audio no matter what I set the settings to.  It took a LONG time to get ZSNES to work right.  But then I made a discovery that my audio/video was choppy on the internet. Streaming audio/video was no longer working.

I followed a guide to fix this problem, but unfortunately the guide was for ALSA users and not OSS.  So I ended up blasting out my sound completely.  Yep, no sound.

So I removed both Pulse and OSS from my system and began to do a reinstall.  However since I wanted to upgrade to Ubuntu Studio, I figured now would be the time to do so.  I did that.  Next I proceeded to reinstall OSS.  Lucky for me OSS had an update of their driver in the interim.  So I loaded that back on and low and behold, I had sound with all my games and even the Ubuntu system sounds now work.  However, none of the applications that came with Ubuntu Studio worked.  Audacity, which worked before the sound blow out, wasn't working.  Ardour wasn't working, Hydrogen wasn't working, etc.  While the streaming video on the internet has been restored, I still have no sound there.

I tried many fixes and was convinced that perhaps I should look into a different audio device.  The dilema I have now is that I am on a dual boot machine and I do not want to disturb the X-Fi sound card settings for Windows.  So right there, I do not want to replace the X-Fi card or install another one next to it in fear of ruining my Windows sound configuration (which is currently working perfectly).

I figured the only way I would use a fully supported ALSA sound device is to go external via the USB or Firewire port.

Today I was trying to find out what USB sound devices are fully compliant with Ubuntu/ALSA when I came across a whole host of posts in regards to the Hardy (current) version of Ubuntu.  Supposedly this current version is riddled with massive problems.  The evidence that supports this is the mass amount of updates I have been downloading to my machine the past couple weeks.  I said to myself that these updates are WORSE than what I had with Windows?  Way too many.  

I read that people's systems got whacked out because of updates.  So I am not sure whether I should continue to do the updates because of that.  I spent a good portion of the afternoon reading many of these posts as to the problems with Hardy and how the prior version, Gutsy (7.10) was so much better.

The past couple days I was re-evaluating my current position with Ubuntu and Hardy and I came to a decision.

My tasks are mostly multi-media based, hence the reason I am posting under this category.  If I cannot get my sound or the Ubuntu Studio applications to work in Hardy, then I am going to seek out a different version of Ubuntu or even a totally different distribution.

This is what I would like to do with Linux:

1) Audio and Video editing (Ardour, Rosegarden, Hydrogen, Jack, Audacity, Open Movie Editor, Cinelerra)
2) Games, try out Linux based games, mostly play emulations of the Atari 2600, NES, SNES, Sega Genesis and old DOS abandonware games (DosBox).   I want sound to work with all of these.
3) Do general emailing, web browsing, and internet surfing (streaming audio and video must work).

Cruising around the internet I found this site:

[http://linuxrockstar.blogspot.com/2006/08/quick-linux-audio-distribution-guide.html](http://linuxrockstar.blogspot.com/2006/08/quick-linux-audio-distribution-guide.html)

So far these other distro's:

OpenSUSE: Jack Lab
Musix.

They don't even list Ubuntu Studio (but a post does mention it).

I also have thought of going back to a prior version of Ubuntu such as Gutsy (7.10).   But I do want to try out Ubuntu Studio...however, I don't see a version (7.10) for that.  Granted I could download a real time kernel and all the applications manually.  But that will take much time.

So my question is this:

Reading everything I wrote above, what is the best recommendation for someone that uses their machine mainly for audio/video editing and playing games?

Should I stay with Hardy and try to fix the problems?  Should I revert back to an older, more stable version of Ubuntu?  Should I abandon Ubuntu altogether and try one of the other distributions I mentioned?

I am mostly looking for responses from those who have successfully set up a Linux based system that handles Audio/Video editing and perhaps those who have used both Ubuntu and the other distributions I mentioned.

Any advice would be appreciated.  And for the record, I have tried numerous attempts and followed many guides to try to get my X-Fi sound card to work.  It just seems like it is one headache after another.

I am hoping there is a better solution in Linux, otherwise I may be still using Windows for a very long time.

Thanx,

Geo

---

