---
title: "recording from internet radio station"
date: 2012-04-02
forum: Multimedia Software
---

### Post by jpaulb on 2012-04-02
I came across a radio station  that was streaming an interview. I wanted to record it; but din´t know how.

Can any one help ?:confused:

Thanks

---

### Post by nd456 on 2012-04-02
A quick fix would be to hook the headphone jack to the mic. Then you could use audacity.
Sorry if it isn't a very formal fix...

---

### Post by jpaulb on 2012-04-02
> **nd456 said:**
> A quick fix would be to hook the headphone jack to the mic. Then you could use audacity.
Sorry if it isn't a very formal fix...

I sat my Archos mp3 player/recorder in front of a speaker and recorded the interview, plus all the ambient noise in the neighbourhood.

There must be some way of tapping into the sound card and sending the audio also to the hdd or usb stick.

---

### Post by Rodney9 on 2012-04-02
[http://www.ubuntugeek.com/how-to-recording-internal-audio-in-ubuntu.html](http://www.ubuntugeek.com/how-to-recording-internal-audio-in-ubuntu.html)

[http://ubuntuforums.org/showthread.php?t=1330728](http://ubuntuforums.org/showthread.php?t=1330728)

[http://ubuntuforums.org/showthread.php?t=1823866](http://ubuntuforums.org/showthread.php?t=1823866)

Rodney

---

### Post by Baldrick_NZ on 2012-04-03
google 'outrec', which installs a small app which can record whatever goes through your soundcard. Records as a .ogg or .mp3 file.

---

### Post by jpaulb on 2012-04-03
> **jpaulb said:**
> I came across a radio station  that was streaming an interview. I wanted to record it; but din´t know how.

Can any one help ?:confused:

Thanks

Thanks to everyone for the help.

The first thing I did was remove every thing of ALSA that I could. 
Then installed pulseaudio + pavucontrol
I removed all USB inputs that had any connection to sound, web-cam, turntable.
Set input in audacity to pulse: line:0 (stereo) input channels
Set output audacity to ALSA Default.
Next pavucontrol
	Playback: show applications
		ALSA plug-in [plugin container] ALSA Playback
	Recording: show applications
		ALSA plugin [audacity] ALSA Capture
	Input device: Show all input devices
		monitor of internal audio analogue stereo

	Configuration: Profile analog stereo output

At first this did not work, I did a reboot and I had it working, no idea why this would be.:D:D:D

---

### Post by andrew.46 on 2012-04-05
Just for curiosity could you give the address of the stream / radio station?

---

### Post by shantiq on 2012-04-06
> **jpaulb said:**
> I came across a radio station  that was streaming an interview. I wanted to record it; but din´t know how.

Can any one help ?:confused:

Thanks



you know there is a much easier way:KS


open vlc /play your station/click on view/advanced controls

now you have a red button at the bottom

click on it to start recording/click again to stop

find your recording in ~/Music


**PS**   if you want the same with video ditto    and file goes to ~/Videos

---

### Post by mc4man on 2012-04-06
Slightly OT, but an interesting app, especially for 12.04 (0.8.X version
[https://launchpad.net/~osmoma/+archive/audio-recorder](https://launchpad.net/~osmoma/+archive/audio-recorder)

---

