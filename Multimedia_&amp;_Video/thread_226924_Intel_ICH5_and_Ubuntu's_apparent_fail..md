---
title: "Intel ICH5 and Ubuntu's apparent fail."
date: 2006-07-31
forum: Multimedia &amp; Video
---

### Post by ritontor on 2006-07-31
I have no idea how this keeps happening, but apparently it happens all of its own accord, even with a default Dapper install. Each and every time I start the machine, the initial bits of sound will play (the beeps and bloops of the login, the swirly start up noise), but then, silence. I try and fire up an mp3 player? Nada. Not a thing. 

Now... I have come up with a solution! If it type this: 

```

sudo fuser -v /dev/dsp

```

And then kill whatever task it lists, the sound works again! Well, in some mp3 players at least. It doesn't work in Quark, but XMMS seems to work. So! It seems that when I'm turning on my computer, it is choosing (as this is what has been the task at fault for the past two times) FIREFOX as the evil software package to steal my sound device. Why would Ubuntu do this? I don't understand. What has firefox got to do with sound? You know what's even more crazy? Sometimes it isn't firefox. 

Yesterday, during the middle of the day, sound stopped working again. Guess what it was this time? A task called "gnome-help". A *HELP* program! How on earth does that use sound? What the hell is going on here? Why does the entire underlying sound system in Linux suck so badly? This is AWFUL. Why should I have to hunt through my computer's task list every now and then to find what task has latched on to the sound device? How is it even allowed to do that? Why is this happening? Why can't someone make the decision once and for all as to how sound is meant to work on Linux and then just make it work? I've never once had anything like these sorts of issues with Windows. 

If anyone has any idea how I'm meant to solve this, I'd love to hear about it. Maybe we can collectively solve the sound on Linux problem once and for all.

---

### Post by ritontor on 2006-08-03
I think I have this one sorted! One must install the alsa-oss package, and then vi /etc/firefox/firefoxrc and change the "none" to "aoss". Quite why Ubuntu didn't just do this in the first place shall probably remain forever unknown.

*Edit*: I never once had to install a "sound package" and edit my browser's configuration on Windows! Sound always just worked. Does this mean Windows is better than Linux, at least when it comes to sound?

---

### Post by zaroff on 2006-08-17
I've had almost the same problem since Dapper came out and I installed it on my laptop (Sager 8890 also with ICH5 onboard sound).  This did not fix it unfortunately.  Running 'sudo fuser -v /dev/dsp' gives no output so no other programs would seem to be using the sound card.

When trying to play sound I usually get what sounds like the first quarter-second or so of sound repeated twice in rapid succession, then nothing.  For example, if I try to play an MP3 with XMMS, I get about the first quarter-second repeated twice and then silence and the elapsed time hangs at 00:00.  XMMS stays responsive the whole time (ie. no crashing) but no sound ever plays apart from that initial little bit.  In the case of trying to play video with VLC, the video plays fine but there's no sound at all.

This problem is NOT unique to Ubuntu Dapper.  I've had the EXACT same problem with a Knoppix V5 CD.  The sound always worked fine in Breezy.  As far as I can tell from experimenting with different versions of Ubuntu and different live CDs, ALSA is the problem.  For ALSA >= 1.0.10 I have no sound.  For ALSA < 1.0.10 I do have sound.  For reference, here is the relevant section of output from lspci -vv:


0000:00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
        Subsystem: CLEVO/KAPOK Computer: Unknown device 0800
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Interrupt: pin B routed to IRQ 193
        Region 0: I/O ports at 1400 [size=256]
        Region 1: I/O ports at 1c80 [size=64]
        Region 2: Memory at e8000c00 (32-bit, non-prefetchable) [size=512]
        Region 3: Memory at e8000800 (32-bit, non-prefetchable) [size=256]
        Capabilities: [50] Power Management version 2
                Flags: PMEClk- DSI- D1- D2- AuxCurrent=375mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-


Any suggestions would be greatly appreciated.

---

### Post by loa on 2007-05-31
You could try
sudo fuser -v /dev/snd/*

It might help for some applications (those who are set to use ALSA sound). Ignore the applet using /dev/snd/controlC0, it should be there.

I also use to have problems with my sound, sometimes it just mysteriously fails, it's very annoying, and I have not yet found out why. Most of the time it works good though. I also has this Intel ICH5 audio, on a ASUS P4C800 motherboard.

Pär

---

### Post by zaroff on 2007-07-08
I finally figured out my problem after a year of messing with it on and off. In case anyone else needs it, the trick that worked for me was to add 'irqpoll' as an option to the kernel on boot up. I've tested it successfully with Ubuntu Feisty and Knoppix. Just wanted to pass this along in case anyone else is still struggling with a similar problem.

---

### Post by tfarinella on 2007-07-20
me me i need help BADLY with this same problem

---

