---
title: "No hdmi sound (nvidia gt430)  Need an expert"
date: 2012-07-28
forum: Multimedia Software
---

### Post by iitywygms on 2012-07-28
Hi all.

I posted up in the mythbuntu thread, but no one was able to help me figure out what is going on.  (several tried and I am appreciative)
I need an EXPERT here, which is why I am posting up in this portion of the forums.
I am running mythbuntu.

I have 

kernel = 3.2.0-27-generic
Processor = Intel(R) Core(TM) i3-2100 CPU @ 3.10GHz
video = gt430
mythbuntu = .25 latest fixes
alsa = 1.0.25
nvidia driver = 295.40

the hdmi is recognized and works if I use mythtv.
Set up as ALSA:hdmi:CARD=NVidia.DEV=1

Problem is, it will not work anywhere else. (youtube, xbmc, anything other than mythtv)  
Even running speaker-test produces no sound.

I have tried every asound.conf.  I have rebooted after every change.  Everything is unmuted in alsamixer.

Why cant I get sound over hdmi outside of mythtv????  
So strange.

Here is the output of alsainfo script.

[http://pastebin.com/r7V1PMFh](http://pastebin.com/r7V1PMFh)

If anyone has some ideas on what to try, I am all ears.  I do not want to do a reinstall unless absolutly necessary.

---

### Post by efflandt on 2012-07-28
While I have not done this since 10.10 and am no longer using a GT 430, see if this works:

With **alsamixer** in a terminal, make sure that the S/PDIF devices for HDA Nvidia are not muted (should be 00 not MM).  There should be 4 of them.

See if **aplay -l** lists the 4 HDA NVidia devices (besides your analog sound or phantom HDMI) like:

```
card 1: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 7: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 8: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 9: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```And note card#'s and device#'s

In this example try: **aplay -D plughw:1,3 /usr/share/sounds/alsa/Front_Center.wav** and the other combinations 1,7 1,8 1,9 until one of those makes HDMI sound

Then with **gksu gedit /etc/pulse/default.pa** (or sudo nano) find the commented line below replicate and uncomment it and set it to what worked for aplay above (for my GT 430 it was 1,9)

```
#load-module module-alsa-source device=hw:1,0
load-module module-alsa-source device=hw:1,9
```Reboot and see what shows up for Output devices in Sound Settings.  Back in 10.10 it was an NVidia device that did NOT say HDMI.  And Test Sound did not work then, but HDMI sound worked in Rythmbox, etc.

---

### Post by iitywygms on 2012-07-28
Thank you for the reply.

The hdmi is unmuted in alsamixer.  
I KNOW which device is my hdmi, because hdmi works while using mythtv.

aplay -D plughw:1,3 /usr/share/sounds/alsa/Front_Center.wav gives no sound.
It says it is playing, but no sound.
same for 1,7 8 or 9

here is aplay-l

**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: ALC892 Analog [ALC892 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 1: ALC892 Digital [ALC892 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 7: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 8: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 9: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

What gets me is that if I mute the spdif in alsamixer, it mutes the sound in mythtv.  So I KNOW it is working.

Its just that it does not produce sound outside of mythtv.

Also, please note I do not have pulse installed.

---

### Post by iitywygms on 2012-07-30
Bump

---

### Post by b0l0bun on 2012-07-30
Same very problem as described above here too: HDMI video to the TV sitting in a living room (laptop is in the office) is fine, no audio.
Except I use Ubuntu 12.04, not a Mythbuntu and use slightly different Nvidia card with nouveau driver.
I don't believe no one knows the answer....
Funny thing is that HDMI audio device hasn't been even shown in UNITY, only in Gnome classic.
My gosh, Linux is a mess...

---

### Post by iitywygms on 2012-07-30
Not exactly the same problem.
I HAVE hdmi audio in mythtv.  Just no audio outside of mythtv.

---

### Post by iitywygms on 2012-08-01
Calling all asla experts.

I KNOW, that the hdmi is card 1 device 7.

If I run aplay -D plughw:1,7 /usr/share/sounds/alsa/test.wav while mythtv is up, it says the device is not available.
If I run aplay -D plughw:1,7 /usr/share/sounds/alsa/test.wav after exiting mythtv, it runs, but still no sound through the speakers.

I have configured asound.conf as follows with no sound outside of mythtv.
Yes, I reboot after every change.

pcm.!default { 
      type hw 
      card 1 
      device 7 
}

---

### Post by iitywygms on 2012-08-07
Okay, I have new information.
I DO get some sound.  If I setup vlc audio options to use the correct card, it works. (I get stereo sound)
Now, I KNOW KKNNOOWW! that the correct sound card for hdmi sound is card 1 device 7.  
So if I set up asound.conf to use that, I should get sound right?  Well, I don't.  ???

no sound if I use flash over the internet,

Another thing is.
I have xbmc installed.  If I set the output to custom device, and use card 1 device 7, I get sound in movies that use 5.1 sound.  But music, 2.0 stereo, and movies that are encoded in stereo do not play.

So, I can conclude that I do not have stero sound over hdmi.
How do I set up alsa so I can have stereo sound play through hdmi??

---

### Post by iitywygms on 2012-08-21
I installed 11.04 and all is back to normal.

---

