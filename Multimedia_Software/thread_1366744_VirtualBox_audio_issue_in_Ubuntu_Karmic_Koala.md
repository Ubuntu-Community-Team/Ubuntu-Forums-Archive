---
title: "VirtualBox audio issue in Ubuntu Karmic Koala"
date: 2009-12-28
forum: Multimedia Software
---

### Post by Welcomed Rain on 2009-12-28
I am running VirtualBox version 3.1.2 r56127 within Ubuntu Karmic Koala as the host and Windows Vista as the guest. I'm using PulseAudio to handle the sound. Sometimes it works perfectly and sometimes it crackles when playing audio (any kind of audio in any kind of player, whether it is guest system sounds or streaming audio, etc.) in the guest OS (it always plays perfectly in Ubuntu, the host,... never any issues).

I can't for the life of me figure out why it works sometimes perfectly and other times I get the crackling sound and poor quality audio. 

The last time I had this issue I deselected a Bluetooth device in the USB setup of the guest and it instantly resolved the audio for the remainder of the session. I thought I had solved the problem and identified to culprit but the next day the problem returned and checking or unchecking the Bluetooth device did nothing to resolve the problem, nor did multiple restarts of the guest (Windows Vista) system.

Any ideas? I have searched the Internet for the problem and possible solutions but don't find anything related to the issue.

---

### Post by Welcomed Rain on 2009-12-30
Through research, I found that the only work around for this problem I described, is to install PulseAudio Volume Control and then open it (minimize with the program open is the best so it's window isn't in the way). Can't explain why this is but nothing else I tried worked and it was recommended to me by a moderator of the PulseAudio Forum site and it works. Open the PulseAudio Volume Control... no crackling... close it... crackling, and minimally invasive. Hope you find this post useful.

---

### Post by slaamer on 2010-01-01
Hi, for me this fixed the audio with Windows Media Player in Vista running in VirtualBox 3.1.2 however, it did not fix the audio with iTunes 9 which uses QuickTime Player to play music.
If you play music with QuickTime Player do you have the same problem?
Thanks, Slaamer

---

### Post by Uncle Spellbinder on 2010-01-01
> **Welcomed Rain said:**
> ...install PulseAudio Volume Control and then open it (minimize with the program open is the best so it's window isn't in the way). Can't explain why this is but nothing else I tried worked and it was recommended to me by a moderator of the PulseAudio Forum site and it works. Open the PulseAudio Volume Control... no crackling... close it... crackling, and minimally invasive. Hope you find this post useful.
Wow. I'm glad I ran across this thread. Works like a charm. THANKS!



> **slaamer said:**
> Hi, for me this fixed the audio with Windows Media Player in Vista running in VirtualBox 3.1.2 however, it did not fix the audio with iTunes 9 which uses QuickTime Player to play music.
If you play music with QuickTime Player do you have the same problem?
Thanks, Slaamer
Using iTunes 8.2.1.6 and and the method Welcomed Rain explained above, iTunes plays like a champ. No crackling at all.

---

### Post by james_xxx on 2010-01-03
Installing and running Pulse Audio Volume Control greatly improved the sound quality in VMs running in VirtualBox for me as well, but did not completely take care of the crackling in many cases.

So far, in a Windows Vista SP2 32-bit guest (with a Kubuntu Karmic 64-bit host), it seems that audio from streams using Adobe's Flash plug-in play without noticeable crackling and popping, but audio from  many other apps (such as Foobar 2000 or Winamp) still have these issues, although with much improvement over how they sounded without Volume Control running.

My machine uses this Audio Controller:
Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)

---

### Post by addisu on 2010-01-12
Installing the latest pulseaudio from launchpad seems to fix the problem.  I still have to have the volume controller running though.

To install pulseaudio from launchpad:
```

sudo add-apt-repository ppa:ubuntu-audio-dev/ppa
sudo apt-get dist-upgrade

```

---

### Post by danatup on 2010-01-17
The PPA-packages with "pulse audio volume control" running, as hinted at above, helped immensely for me. Now the audio and video of Youtube, for example, is out of sync. Any suggestions with that?

---

### Post by jsa13 on 2010-03-07
Choppy audio solved by installing "libsdl1.2debian-pulseaudio"!

---

### Post by jac_tict on 2011-03-14
I switch Audio Controller from AC97 to Intel HD Audio and I solve choppy audio problem.

---

