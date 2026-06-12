---
title: "How to setup a VOIP phone[Skype alternative] in Ubuntu 9.04"
date: 2010-04-11
forum: Multimedia Software
---

### Post by meka4996 on 2010-04-11
How to setup a VOIP phone[Skype alternative] in Ubuntu 9.04.
I tried Skype in Ubuntu, but quite often the other side cannot hear me or I cannot hear them... recently, even I cannot hear anything from the echo testing service! Personally, I think the Linux version of Skype sucks!

And the solution is...
Make sure you get the order of actions correct first...
1. Check & Adjust Sound Panel/Volume Control in Ubuntu Linux
for example:
#Device= HDA ATI SB(Alsa Mixer) 
HDA ATI SB (Alsa Mixer)
Master= Max
PCM   = Max
Line-in= muted
CD    =  muted
Microphone= min + muted
Mic Boost=  min + muted ... but it unmutes itself
PC Speaker= min + Muted
Switches-Headphone= Checked
... at Recording Tab...
  Capture= max, sound out: enabled, toggle audio recording from Capture: disabled
  
"Device= Capture AK5370 USB Audio (PulseAudio Mixer): 
  Master= high, sound enabled, toggle audio recording from Capture: enabled... but it lowers the volume by itself!!

Device= AK5370 (Alsa mixer): 
  Microphone=max, sound enabled, toggle audio recording: disabled

Realtek ALC883 (OSS Mixer) ...

Playback: HDA ATI SB - ALC883 Analog (PulseAudio Mixer)
Master= Max

Capture: Monitor of HDA ATI SB - ALC883 Analog (PulseAudio Mixer)
Master= Max

Capture: HDA ATI SB - ALC883 Analog (PulseAudio Mixer)
Master= Max

2.Test your microphone using "Sound Recorder" in Ubuntu under Applications-> Sound&Video
Check if Ubuntu can at least work with your microphone... by checking if the received sound volume goes up and down as you speak, and by playing the recorded sound.

3.Find a program that can be installed on Ubuntu or your distro, and the program can work/detect your hardware[USB headset or microphone]... use their echo test to see if you can hear echo sound.

4.Choose a good quality & low rate company for calling out to landlines.

--==
Conclusion[for Ubuntu 9.04]: my solution is Twinkle with Gizmo5 or [www.diamondcard.us](www.diamondcard.us).
Twinkle detects my Logitech USB Desktop Microphone AK5370 without any volume adjustment! 

Install Twinkle of the latest version from their PPA! Don't waste time on compiling!
Thanks to akolahi from the post [http://ubuntu-utah.ubuntuforums.org/showthread.php?t=1211615&page=2](http://ubuntu-utah.ubuntuforums.org/showthread.php?t=1211615&page=2)
quote "You can add a line to your software source and update ubuntu...
[https://launchpad.net/~gnutelephony/+archive/ppa](https://launchpad.net/~gnutelephony/+archive/ppa)
this will upgrade Twinkle to 1.4.2..." end of quote

Gizmo5(Google)'s calling out quality is great! Although I haven't tried [www.diamondcard.us](www.diamondcard.us)

References:
Best SIP Softphones for VOIP on Linux 
[http://voipguides.blogspot.com/2009/07/best-sip-softphones-for-voip-on-linux.html](http://voipguides.blogspot.com/2009/07/best-sip-softphones-for-voip-on-linux.html)

And follow guide below for setting up your VOIP phone step by step !
Twinkle: My favorite SIP program
[http://www.freesoftwaremagazine.com/columns/twinkle_my_favorite_sip_program](http://www.freesoftwaremagazine.com/columns/twinkle_my_favorite_sip_program)

Have fun!

---

