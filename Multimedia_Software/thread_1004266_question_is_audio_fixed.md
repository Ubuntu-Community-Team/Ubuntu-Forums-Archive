---
title: "question: is audio fixed?"
date: 2008-12-07
forum: Multimedia Software
---

### Post by spandanj on 2008-12-07
Throughout my experience with Ubuntu since 7.10, I have had to struggle with the audio/sound working in rhythmbox/banshee, flash 9, flash 10, mplayer, vlc, etc....in terms of audio conflicts, or no sound, or freeze.

Over the year, I came to understand that it's because Ubuntu is trying to implement "pulse" audio system, and not all programs are designed to work with it. And, over the year, I had to fix (temporarily, without understanding of what I was doing) the audio ... by trying to set up properly between alsa, and pulse. 

In fact, my recent back install to 8.04 a month ago, after 8.10 failed my wireless internet by freezing every time I tried to use it, I still had to "properly set up" my audio system ***again*** using the "perfect setup for pulse" guide and getting help on this forum.

I am not saying that audio doesn't work in Ubuntu. Yes, It can work perfectly if its set up perfectly!

But, I DO NOT want to have to set it up myself, and waste time doing that. Sound for all programs should work out of the box flawlessly. 

[COLOR="Green"]_**My Question is:_**[/COLOR] [COLOR="Blue"]**are all the sound conflicts in terms of software conflicts, and alsa vs. pulse conflicts solved, and it works flawlessly with a fresh ubuntu install???**[/COLOR] [COLOR="SlateGray"](of course I am not refering to any problems related to the audio driver/hardware itself)[/COLOR]

I like to know this since I am not an expert in anything Ubuntu, and don't aspire to be either.

---

### Post by gandaran on 2008-12-07
audio or pulseaudio works perfectly for most people, I have never had a audio problem in ubuntu 8.04 and 8.10 (ubuntu 8.04 I installed in 6 different computers), but there are some unlucky users that get pulseaudio issues, this depends on your hardware/drivers, thinks are better in intrepid 8.10, but still some users of 8.10 still have problems
well the fix is easy if you have the right guide [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

and the answer to your question is no, you'll have to apply the fix, maybe it'll be fixed for you in next ubuntu 9.04

---

### Post by spandanj on 2008-12-08
> **gandaran said:**
> 

and the answer to your question is no, you'll have to apply the fix, maybe it'll be fixed for you in next ubuntu 9.04

But,

It's already fixed in fedora 10 as per: [https://fedoraproject.org/wiki/Features/GlitchFreeAudio](https://fedoraproject.org/wiki/Features/GlitchFreeAudio)

and

follwing planned for fedora 11: [https://fedoraproject.org/wiki/Features/VolumeControl](https://fedoraproject.org/wiki/Features/VolumeControl)

THAT is exactly what I want for Ubuntu as well. and ASAP. This, in fact, shouldn't even be considered as a 'feature' !!! It's just how it's suppose to work in an OS -- "Glitch-Free"

I chose Ubuntu for it's reputation as "glitch-free". I am afraid it's not. I just hope it get's there fast since it's a very old problem still not fixed. 

In retrospect, Why did Ubuntu not do the following since 8.04:

1) make alsa use pulse 
2) run most programs on pulse directly --those which can and other on alsa, however running to pulse eventually.

I HAD TO DO THAT myself using perfect setup for Pulse. I am going to be saying this 100th time but WHY do I - the user - have to do that? Just make it work. All I want to see regarding audio is the volume control and/or any other "feature" not manual labor of configuration!

---

### Post by gandaran on 2008-12-08
> I chose Ubuntu for it's reputation as "glitch-free". I am afraid it's not. I just hope it get's there fast since it's a very old problem still not fixed.
are you serious? if you want a "glitch-free" linux operating system then install mandriva, on this computer I'm writing from the only operating system that works perfectly out of the box is mandriva, could never install fedora here and ubuntu I have to fix grub resolution every-time I reinstall, but for some reasons I still prefer ubuntu, running ubuntu 8.10 here, no audio problems but I can count five bugs I'm still waiting to be fixed with updates (I don't believe they will be!) I think the problem with ubuntu is the release of a new version every sixth month, it's a very short time for testing, but we still love ubuntu with all it's bugs!

---

### Post by spandanj on 2008-12-08
> **gandaran said:**
> are you serious? I still prefer ubuntu, running ubuntu 8.10 here, no audio problems but I can count five bugs I'm still waiting to be fixed with updates (I don't believe they will be!) I think the problem with ubuntu is the release of a new version every sixth month, it's a very short time for testing, but we still love ubuntu with all it's bugs!

I wouldn't try mandriva because I have already gotten used to Ubuntu...

However, I do agree with you that the lack of "glitch-freeness" in ubuntu can be partially attributed to its 6-month release cycle which is quite fast. Although I don't agree that a fast release cycle should spawn new bugs because the principle behind Upgrades is to make it better not make it worse by introducing new features/codes that break a previously working piece of software. Ubuntu broke my system with a fresh 8.10 install due to wireless internet not working, so I am back to 8.04. If anything, there should be less bugs with new releases! (of course I exclude bugs relating to hardware support)

I don't love Ubuntu. I wanted to, but I don't. I love compiz though. It has never failed me!

---

