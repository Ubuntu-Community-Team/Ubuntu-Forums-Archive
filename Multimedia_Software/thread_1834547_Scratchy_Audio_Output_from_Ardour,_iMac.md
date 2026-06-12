---
title: "Scratchy Audio Output from Ardour, iMac"
date: 2011-08-27
forum: Multimedia Software
---

### Post by paulbdavis on 2011-08-27
I have been trying to set up Ardour on my computer, but whenever I try to play anything back, I get a horribly static scratchyness, with a little bit of the proper audio coming through.

This happens if I record a new audio file, or import an existing one. The audio files play back fine in other applications, including Audacity.

I can;t seem to find anyone else with the problem (unfortunately) and I do not have the knowledge to figure out if it is a problem with JACK or Ardour, as I am just getting started with audio recording with Linux (I am a recent Mac/Logic user)

I am using Ubuntu 11.04 (64 bit) on a December 2010 iMac

---

### Post by Don-F on 2011-08-27
A couple of possibilities:

[LIST=1]
[*]You may not have sufficient privileges to run JACK in realtime mode.
[*]Your JACK latency setting may be too low for your hardware to cope with.
[/LIST]
The first thing I'd try is increasing the latency to something like 2048 samples. If the audio sounds good, decrease it in steps until you start having problems.

If you can't run JACK in realtime mode, first make sure you're a member of the audio group. Then, check to see that /etc/security/limits.d/audio.conf contains the following lines:

@audio   -  rtprio     99
@audio   -  memlock    unlimited

(If you add yourself to the audio group, or add/modify audio.conf, the changes won't take effect until the next time you log in.)

You can always try the Ardour IRC channel. During daytime hours on the US East Coast someone is usually available to help.

Regards,
Don

---

### Post by paulbdavis on 2011-08-28
I have tried all of those things to no avail. Headed to IRC, thanks.

EDIT: The IRC channel is pretty barren......

---

### Post by paulbdavis on 2011-08-28
I have determined that the problem is with JACK, not Ardour. I tried using ZynAddSubFX and it send out a horrible buzzing sound when it is idle, though it plays fine when pressing down keys on the virtual keyboard.

Anything? I am pulling my hair out over this.

---

### Post by Don-F on 2011-08-28
The problem is definitely with JACK, or with the ALSA backend (which is what I assume you're using).

It would be helpful if you could post the output from JACK. If you use QJackCtl (highly recommended), you can copy the output from the Messages window.

Here's what I see in my Messages window (just to give you an idea of what it looks like on a system that's working correctly):

```
15:05:21.039 Patchbay deactivated.
 15:05:21.066 Statistics reset.
 15:05:21.118 ALSA connection graph change.
 15:05:21.310 ALSA connection change.
 15:05:23.622 JACK is starting...
 15:05:23.623 /usr/bin/jackd -P89 -p2048 -dalsa -dhw:0 -r44100 -p2048 -n3
 jackd 0.118.0
 Copyright 2001-2009 Paul Davis, Stephane Letz, Jack O'Quinn, Torben Hohn and others.
 jackd comes with ABSOLUTELY NO WARRANTY
 This is free software, and you are welcome to redistribute it
 under certain conditions; see the file COPYING for details
 Memory locking is unlimited - this is dangerous. You should probably alter the line:
      @audio   -  memlock    unlimited
 in your /etc/limits.conf to read:
      @audio   -  memlock    2269818
 15:05:23.666 JACK was started with PID=2767.
 JACK compiled with System V SHM support.
 loading driver ..
 apparent rate = 44100
 creating alsa driver ... hw:0|hw:0|2048|3|44100|0|0|nomon|swmeter|-|32bit
 control device hw:0
 configuring for 44100Hz, period = 2048 frames (46.4 ms), buffer = 3 periods
 ALSA: final selected sample format for capture: 32bit integer little-endian
 ALSA: use 3 periods for capture
 ALSA: final selected sample format for playback: 32bit integer little-endian
 ALSA: use 3 periods for playback
 15:05:25.722 Server configuration saved to "/home/donf/.jackdrc".
 15:05:25.727 Statistics reset.
 15:05:26.173 Client activated.
 15:05:26.174 Post-startup script...
 15:05:26.175 cpufreq-selector -c 0 -g performance; cpufreq-selector -c 1 -g performance
 15:05:26.662 Post-startup script terminated successfully.
 15:05:26.663 JACK connection change.

```The bit about memlock being unlimited -- Ardour complains if it isn't unlimited, and JACK complains if it *is* unlimited. It's never caused a problem for me.

Don

---

### Post by Don-F on 2011-08-28
> **paulbdavis said:**
> The IRC channel is pretty barren......If you post your question when the lead developer, "las", is on, you'll probably get a pretty fast response. He's also the main developer of JACK, btw. You might see me ("DonF") on the channel once in a while.

In addition to #ardour, you might try #jack, #lau, or #ubuntustudio.

Don

---

### Post by paulbdavis on 2011-08-30
Here is the Message output. the line "Cannot connect to server socket err = No such file or directory" seems guilty to me, but I am still new to all this. Thanks for the help so far, I will check out the #jack channel too.


```
16:09:51.870 Patchbay deactivated.
16:09:51.872 Statistics reset.
16:09:51.927 ALSA connection change.
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
16:09:51.933 ALSA connection graph change.
16:10:07.390 JACK is starting...
16:10:07.390 /usr/bin/jackd -dalsa -dhw:0 -r44100 -p2048 -n3 -H -M
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
16:10:07.416 JACK was started with PID=17429.
no message buffer overruns
no message buffer overruns
jackdmp 1.9.7
Copyright 2001-2005 Paul Davis and others.
Copyright 2004-2010 Grame.
jackdmp comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK server starting in realtime mode with priority 10
control device hw:0
control device hw:0
audio_reservation_init
Acquire audio card Audio0
creating alsa driver ... hw:0|hw:0|2048|3|44100|0|0|hwmon|hwmeter|-|32bit
control device hw:0
Using ALSA driver HDA-Intel running on card 0 - HDA Intel at 0xd0500000 irq 41
configuring for 44100Hz, period = 2048 frames (46.4 ms), buffer = 3 periods
ALSA: final selected sample format for capture: 32bit float little-endian
ALSA: use 3 periods for capture
ALSA: final selected sample format for playback: 32bit float little-endian
ALSA: use 3 periods for playback
16:10:09.643 JACK connection change.
16:10:09.644 Server configuration saved to "/home/paul/.jackdrc".
16:10:09.645 Statistics reset.
16:10:09.668 Client activated.
16:10:09.724 JACK connection graph change.
```

---

### Post by Don-F on 2011-08-30
There's quite a bit of useful information there, believe it or not. Unfortunately, there is nothing that, by itself, would explain the problem you're having.
 
The "Cannot connect to server" messages are from QJackCtl itself, I think. QJackCtl connects as a client to the JACK server. It tries a few times before giving up. In your case, it looks like it succeeded on the third try, or so.
 
You aren't trying to run with an absurdly low latency setting. That answers one of my questions. You are also using "-n3", which is often helpful on Intel HDA hardware. Also, you haven't unchecked the Realtime option.
 
You can omit the -M and -H options (hardare metering/hardware monitoring) unless you're using hardware that supports it. As far as I know, this would be liminted to one of the fine (and pricey) soundcards in the RME Hammerfall line. It looks like you're using an Intel-HDA-type onboard sound system, so you can safely uncheck the "HW Monitor" and "HW Metering" boxes.
 
If you're running PulseAudio, you might try using **pasuspender** to temporarily suspend PA while JACK is running. JACK needs direct access to the audio hardware, and PA can get in the way.
 
Another thing you can try: Change the Audio setting from "Duplex" to "Playback only". Some Intel HDA hardware doesn't work well in duplex mode. I have no idea what's on the iMac.
 
Check here: [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto). About halfway down the page, there's a section called "Solution for Apple Macs" that might possibly be helpful.
 
Don

---

### Post by paulbdavis on 2011-08-30
Ok, so none of that has worked, except now I can't record anything, I can only hear scratchy audio now (I imported some .wav files to test it out)

I replaced the Server line in the settings with pasuspender -- jackd and it starts up, but still getting the scratchy audio.

I tried both of the fixes in the HDAIntelSoundHowTo as well.

Here is my message log now

```
23:08:02.294 JACK is starting...
23:08:02.295 /usr/bin/pasuspender -- jackd -dalsa -dhw:0 -r44100 -p2048 -n3 -P
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
23:08:02.351 JACK was started with PID=2508.
no message buffer overruns
no message buffer overruns
jackdmp 1.9.7
Copyright 2001-2005 Paul Davis and others.
Copyright 2004-2010 Grame.
jackdmp comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK server starting in realtime mode with priority 10
control device hw:0
control device hw:0
audio_reservation_init
Acquire audio card Audio0
creating alsa driver ... hw:0|-|2048|3|44100|0|0|nomon|swmeter|-|32bit
control device hw:0
Using ALSA driver HDA-Intel running on card 0 - HDA Intel at 0xd0500000 irq 41
configuring for 44100Hz, period = 2048 frames (46.4 ms), buffer = 3 periods
ALSA: final selected sample format for playback: 32bit float little-endian
ALSA: use 3 periods for playback
23:08:04.407 JACK connection change.
23:08:04.408 Server configuration saved to "/home/paul/.jackdrc".
23:08:04.408 Statistics reset.
23:08:04.440 Client activated.
23:08:04.444 JACK connection graph change.
```

Thanks for all the help and patience so far.

---

### Post by Don-F on 2011-08-31
Googling a little more, I found this: [https://help.ubuntu.com/community/Intel_iMac#Sound](https://help.ubuntu.com/community/Intel_iMac#Sound)

The gist of it is to add a "model=" option to the snd-hda-intel module. But I'm not sure which model is correct for you.

On my Acer laptop (which probably means it won't help you at all), I have "enable_msi=1 position_fix=1".

One thing I forgot to ask before: Are you getting xruns when you play sound?

Don

---

### Post by paulbdavis on 2011-08-31
Tried all of that, nothing seems to be working.

As for xruns, I am not quite sure how to identify them, but as I read it, they manifest in the form of popping or cracking, but periodic, not constant like I have. 

I should note, that simply playing sound without using JACK (just playing .mp3 files in Banshee) works just fine, it is only when I am using JACK that I have any issues with the sound.

---

### Post by paulbdavis on 2011-09-01
I can confirm now that I am not getting xruns, as I forced them by setting a really small buffer and saw them popping up in the JACK message window.

---

### Post by Don-F on 2011-09-01
I think you need help from someone more familiar with your hardware. The only other thing I can think to suggest is trying a realtime kernel, but that's really a longshot. Usually an RT kernel is only needed when you want to squeeze that last bit of performance out of a machine.

If you can't raise anyone on IRC, you might try the forums at ardour.org.

Don

---

