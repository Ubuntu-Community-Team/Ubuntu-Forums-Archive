---
title: "sound recording"
date: 2008-08-05
forum: Multimedia Software
---

### Post by th1bill on 2008-08-05
[COLOR="DarkRed"]I need to cut a vocal only mp3 track for a demo and I can not seem to turn the mike on.  I'm using onboard AC97 because the quality is a moot issue.  I need the group to practice their rifs and backup before Sunday.[/COLOR]

---

### Post by markbuntu on 2008-08-05
Have you tried unmuting and turning up the capture slider in the mixer?
If it is a usb mic, you need to go to the usb section of the mixer.
You need to have capture on and turned up to record.

---

### Post by th1bill on 2008-08-06
> **markbuntu said:**
> Have you tried unmuting and turning up the capture slider in the mixer?
If it is a usb mic, you need to go to the usb section of the mixer.
You need to have capture on and turned up to record.

Yes and I can hear my voice in the speakers but when I try to record in Audacity all I get is a flat line.  And thanks for replying.

---

### Post by markbuntu on 2008-08-06
Ahhhh, Audacity. You need to kill PulseAudio to get Audacity to work. There is a note in here about how to set that up:


[http://pulseaudio.org/wiki/PerfectSetup](http://pulseaudio.org/wiki/PerfectSetup)

---

### Post by AgentZ86 on 2008-08-31
Hi
Sorry break in, 

I have a related mic/sound issue, I have a Logitech Pro 4000, and it works well on Ubuntu 7.10 and 8.04 32 bit versions, however I've noticed that it works well with things like wengophone and other online flash AV and even audacity works great, however in audacity I have to select my AlSA USB device, and for my channels I have to select Mono (stereo will not work with my USB webcam devise etc.
Note my sound card is Asus / AC97 onboard type sound system.

Anyhow I cannot get the mic working for any voice recording applications such as: Sound Recorder, or gtk-RecordMyDesktop. I believe it use to work with 7.10, but I can't get the settings right for it now int 8.04

I'm sure it's some setting or combination of settings since it does work with other applications.

Here is the gtk-recordMyDesktop-crash.log regarding sound:

Initializing...
Buffer size adjusted to 4096 from 4096 frames.
Couldn't open PCM device hw:0,0
Error while opening/configuring soundcard hw:0,0
Try running with the --no-sound or specify a correct device.


Additionally:
I plugged an external mic thru a mixer, and into the line-in port and all works well including sound recorder etc. 
I wonder why sound recorder and gtk-recordMyDesktop does not like my USB webcam mic ?
Oh well, I can use it like this for now, but if anyone has any idea, would be great.

Please advise
Thanks

---

### Post by fauzie on 2008-09-13
use alsamixer (type in alsamixer in the terminal)

Go to recording Tab

Make sure BOTH mic capture and master capture is on and set to capture (press Spacebar)
This is most likely your problem if you can get sound from mic through the speaker but no recording.

---

### Post by markbuntu on 2008-09-14
> **AgentZ86 said:**
> Hi
Sorry break in, 

I have a related mic/sound issue, I have a Logitech Pro 4000, and it works well on Ubuntu 7.10 and 8.04 32 bit versions, however I've noticed that it works well with things like wengophone and other online flash AV and even audacity works great, however in audacity I have to select my AlSA USB device, and for my channels I have to select Mono (stereo will not work with my USB webcam devise etc.
Note my sound card is Asus / AC97 onboard type sound system.

Anyhow I cannot get the mic working for any voice recording applications such as: Sound Recorder, or gtk-RecordMyDesktop. I believe it use to work with 7.10, but I can't get the settings right for it now int 8.04

I'm sure it's some setting or combination of settings since it does work with other applications.

Here is the gtk-recordMyDesktop-crash.log regarding sound:

Initializing...
Buffer size adjusted to 4096 from 4096 frames.
Couldn't open PCM device hw:0,0
Error while opening/configuring soundcard hw:0,0
Try running with the --no-sound or specify a correct device.


Additionally:
I plugged an external mic thru a mixer, and into the line-in port and all works well including sound recorder etc. 
I wonder why sound recorder and gtk-recordMyDesktop does not like my USB webcam mic ?
Oh well, I can use it like this for now, but if anyone has any idea, would be great.

Please advise
Thanks

USB mics are separate individual DEVICES in alsa and so must be explicitly chosen, both in their own mixer section and in System/Prefeerences/Sound/Capture and in the volume control. If you are also using Pulse Audio, you need to choose them as default in the PA Volume Control.

---

