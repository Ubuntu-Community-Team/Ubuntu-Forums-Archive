---
title: "Another No Mic In Skype Thread"
date: 2010-08-21
forum: Multimedia Software
---

### Post by RevGross13 on 2010-08-21
I know you people probably get tired of seeing these threads pop up, but honestly, nothing else I've seen on it works. The problem's actually gotten worse.

Like, at first, it was just muted. So I told Skype not to adjust my mixer levels, I called the echo service and the mic worked. Fantastic.

Then I call someone, they can hear me, then I turn on my video. Suddenly, my mic's gone. I can't get it back. Even when I call the echo service, it doesn't even play back seconds of silence after I try to record a message.

(I've tried using the PulseAudio Volume Control and lowering one side of the input. That didn't do anything for me, by the way)

I'm running ubuntu 10.04, 32-bit, and I'm on an HP Pavilion Entertainment Notebook dv7-3165dx. It's the built-in webcam/mic that's messing up. Please help!

Oh, and trying to record video in Cheese freezes the entire thing up, if that matters.

---

### Post by RevGross13 on 2010-08-21
Bump, along with another tidbit:

If I completely reboot the system, the mic works on just a call. The MOMENT I try to add webcam video feed to it, the mic instantly goes away

---

### Post by RevGross13 on 2010-08-21
Re-bump, this is really an issue, I've gotten no closer to solving it, please help

I've gone step-by-step, and any time I try to run the webcam with sound and video both going at the same time, it doesn't work. The mic only stops working when I actually try to record something or webcam-chat with someone. Cheese just freezes up if I try to record, and I lose the mic then too. I lose the mic whenever I try to actually do anything with the video/audio going at the same time.

---

### Post by RevGross13 on 2010-08-21
And I looked through everything in the System Preferences / PulseAudio /  ALSA when the microphone worked and wrote it all down, then activated  the cam, then looked through everything and compared it to what was  written before. The only thing that was different was, in Preferences  > Input, the connector changed from 'microphone' to 'line-in', and  changing it back didn't help anything. Help!

---

### Post by thegitksan on 2010-08-28
Has anybody answered yet? I am having similar audio/video problems. I use a Microsoft Webcam 3000 on Ubuntu 8.0.4 (Hardy Heron).

Thx.

---

### Post by lidex on 2010-08-28
For the Dv7:
Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert this line at the bottom:
```
 options snd-hda-intel model=hp-dv5 enable_msi=1 
```
Save. Close. Reboot. 
Check your levels in alsamixer.
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default and adjust your profile on the hardware tab. 
On the output tab choose the correct device.

---

