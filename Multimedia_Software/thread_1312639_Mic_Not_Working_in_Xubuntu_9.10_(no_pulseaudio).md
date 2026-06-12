---
title: "Mic Not Working in Xubuntu 9.10 (no pulseaudio)"
date: 2009-11-03
forum: Multimedia Software
---

### Post by MST3Kakalina on 2009-11-03
I did an upgrade to Karmic (through System -> Update Manager) and most everything else is going smoothly.  My big problem is that my mic no longer works, either in Skype or anything else (I tried recording in Audacity to see if it was Skype related or not; equally buggered there).

As soon as I upgraded I dumped pulseaudio because it's just been constantly buggy for me and has for quite a while.  I use alsa instead.  Here's the rundown:

1. The mic *hardware* works; I can hear in my headphones (it's a mic/headphone headset) when I blow or tap on the mic, there's feedback if I unplug the things the wrong way, etc.

2. The mic volume in alsamixer is cranked up to max, so is mic boost.

3. Trying pulseaudio and using padevchooser was a no-go.



 I *think* the issue is that Xubuntu is just not talking to the mic.  Frustrating, because in 9.04 it worked right out of the box.  I don't know what would have changed between the two.  But since I'm currently half the world away from my family and boyfriend, obviously being able to use my microphone is pretty essential! Anyone have any ideas?

---

### Post by himnosiss on 2009-12-12
I have the same problem too. How can be fixed, i need that microphone.
I used alsamixer to set mic volume to max and to set it as recording source. when i unmute microphone i hear what i talk in my speakers, so my sound card works. When i try to record something (and by the way, i can't set anything else but pulseaudio in each program for sources or playback), is not working. Playback works fine. If i have more than one application open that uses sound my processor goes up to 100% and the sound starts to contain gaps and is like trying to listen to on line radio on on a 5 KB/s modem.

I have Ubuntu not xubuntu.

---

