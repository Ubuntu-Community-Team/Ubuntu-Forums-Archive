---
title: "Creative Blaster X-Fi surround 5.1 soundcard"
date: 2010-09-02
forum: Multimedia Software
---

### Post by axel22 on 2010-09-02
Hello.

I own an external usb soundcard: Creative Blaster X-Fi Surround 5.1. After some tweaking around Multimedia Settings, (K)Ubuntu 9.10 successfully detected the card. I can now use it.

However, setting the sound level in KMixer does not work at all - KMixer now only contains a Microphone channel.

[LIST=1]
[*] Using hotkeys, I can still turn volume from 0 to 100%, but that has no effect on the volume produced by the soundcard.
[*] The sound card comes with a sound joggle, but turning it left or right has no effect whatsoever on the volume level.
[/LIST]

Is there a way to solve either of these issues?

Thanks

p.s. Also, the card came with a Windows app and driver cd.

---

### Post by axel22 on 2010-09-04
Just for the record.

After tweaking and tweaking, I've encountered popping and screeching sound all of a sudden (particularly in flash videos on websites).

I solved this by starting PulseAudio Volume Control, clicking Configurations Tab, and setting SB_X-Fi_Surround_5.1 profile to Digital Stereo Duplex.

(this didn't solve the issue for XBMC, Skype and some Flash players on websites, though, these still screech)

---

### Post by axel22 on 2011-01-15
I appreciate that pulseaudio is an open source project done by enthusiasts. However, with all due respect to everybody, I also think it's a real concern that Linux people are unable to make a decent sound system that could work. Whenever I turn on either skype, a flash video, or vlc, switching desktops results in the most annoying crackling sound in the universe.

How difficult can this be to fix? I have no idea, but sound capabilities are a pretty basic thing for a modern OS. One would imagine that in this modern times Ubuntu that boasts user friendliness could at least have that sorted out properly.

Don't get me wrong. I admire Linux. I love Ubuntu. I appreciate the effort of the people working on PulseAudio. But it still doesn't work well.

---

### Post by axel22 on 2011-01-15
The crackling has become unbearable.

---

