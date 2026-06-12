---
title: "Ubuntu 9.04:  Sound:  Have all audio, but not for DVD playback"
date: 2009-05-09
forum: Multimedia Software
---

### Post by tinker123 on 2009-05-09
Hi;

After I upgraded from Ubuntu 8.10 to 9.04 I lost all audio.  I tried sundry things I picked up from launchpad and I got all of my audio back except for DVD playbacks.

Using totem I can play music CDs just fine. Using totme I can play ripped MP3 music and AVI movies just fine.   Using totem I get video playback from DVDs, but no so sound.

Any ideas

Doing lspci -v this is what I got for my soundcard.  Getting my other audio working I learned that my installation is using pulseaudio.


> 
02:00.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 07)
	Subsystem: Creative Labs Device 8064
	Flags: bus master, medium devsel, latency 32, IRQ 21
	I/O ports at d880 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: EMU10K1_Audigy
	Kernel modules: snd-emu10k1


---

### Post by tractor on 2009-05-09
I'm having the exact same problem. Sound works for everything except playback in video DVD's

---

### Post by tinker123 on 2009-05-09
My motherboard has built in audio in addition to the computer having a sound card.  On a tip I went into my BIOS ( holding F2 down on a starting up the computer ) and disabled the audio.  It was confusing as the audio was listed as a "peripheral device", but I figured it was worth a shot as I could always undo it if took the sound I did have out.

It worked.  I even got some system sounds back.

---

### Post by dawson345 on 2009-05-12
I have a basic understanding of sound issues /DVD playback in Ubuntu. From personal experience I have found a few things out-

[LIST]
[*]Make sure you have the sound options set to the same audio device/playback method
[*]Some programs (such as VLC for myself) select a different audio device. I didn't find a software fix for this so I plugged my audio jack into the motherboards own I/O audio jack, then set the sound options to that/Sound card depending on your set-up
[*]Make sure your audio settings are all on?
[/LIST]

---

### Post by tractor on 2009-05-12
Hi,

Before this post showed up on Saturday, I had also posted a separate message for myself. then I saw this one also. Here is additional information:
1. I have tried the things suggested here.
2. I am a realtor and make DVD video tours of the properties I sell. These include narration and background music.
3. I have installed Ubuntu on 8 computers since I started with linux and Ubuntu about 2 months ago.
4. I have discovered that the more recent DVD's I've made will play back fine in Ubuntu and have the voice and background music. Older ones have no sound in Ubuntu, even though the play fine on Windows Vista and XP boxes and also a range of older and newer DVD players connected to TV's.
5. I'm presently using Corel's (formerly ULead) Video Studio 11 Plus. Prior to that I had version 10, and prior to that version 9. Prior to that Pinnacle Studio 9, 8, and 7.
6. It appears that there is something in the way the DVD's are formatted with respect to sound which causes some of them to be read in Ubuntu or possibly Linux as a whole, but not all of them. 
6. It would be nice if they all would work!

I do appreciate all of the suggestions which people have been kind enough to make!

---

### Post by stedevil on 2009-10-26
Goto 

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

and install.

---

### Post by tractor on 2009-10-26
Thank you. I actually had tried that. Here is some additional information that I've discovered since my original post. I've used ULead in Windows to make my DVD's. The most recent versions are rendering DVD's which are burned as DVD-Video on DVD-R discs. Older rendered versions when I was using windows, and I'm talking about discs created 2 years ago and further back, were rendered as DVD's, burned on DVD-R discs as data discs, are the ones which don't have sound now when I play them back in Ubuntu. They work fine in all DVD stand alone players for television playback, and also for playback on Windows machines. Linux DVD burning programs will not let me burn the older rendered versions to a disc as DVD-video, not will they let me burn them as a data disc either. Apparently there was something lost in backward compatibility between Ubuntu 8.10 and 9.04 since in 8.10 all of the older discs would play fine.

I am also a Webmaster. How do you get background music to play in Firefox in Ubuntu?

Thank you.

---

