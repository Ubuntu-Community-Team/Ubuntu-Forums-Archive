---
title: "Can't hear my mic in 10.04"
date: 2010-05-17
forum: Multimedia Software
---

### Post by PoopLoops on 2010-05-17
Okay, so it's not so much a mic as me plugging my guitar into my input port. Just upgraded from 8.10 a few days ago. My "mic" worked fine there, works fine in Vista, and even now I can tell it is working fine because when I hook up my guitar to the comp to tune it, it is detected and displays the frequency when I play a note (on a tuning program I use) and in the Sound Preferences thing it also displays an intensity. I just can't *hear* what I am inputting, which is the entire point, since I want to play along with songs and junk.

I have played around with alsamixer to no avail.  Everything is unmuted and at 100 volume and I still can't hear anything.  Music and games sound just fine.  It's only the mic I can't hear.

I have an Alienware "laptop" (it's 10lbs!), here are my sound specs:

```

tomek@tomek:~$ uname -a
Linux tomek 2.6.32-22-generic #33-Ubuntu SMP Wed Apr 28 13:27:30 UTC 2010 i686 GNU/Linux
tomek@tomek:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC269 Analog [ALC269 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC269 Digital [ALC269 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
tomek@tomek:~$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.21.
tomek@tomek:~$ head -n 1 /proc/asound/card0/codec#0 
Codec: Realtek ALC269

```

HALP??? :(

---

### Post by webified on 2010-05-17
try the suggestions in this thread: [Mic Doesn't work in 10.04]("http://ubuntuforums.org/showthread.php?t=1466096")

It worked for me. After upgrading to 10.04 I was getting no sound from my mic, or seriously distorted/crackling sound, and simply reinstalled alsa.

Good luck

---

### Post by PoopLoops on 2010-05-17
> **webified said:**
> try the suggestions in this thread: [Mic Doesn't work in 10.04]("http://ubuntuforums.org/showthread.php?t=1466096")

It worked for me. After upgrading to 10.04 I was getting no sound from my mic, or seriously distorted/crackling sound, and simply reinstalled alsa.

Good luck

Tried it, but no dice. :(  

Thanks anyway, though. :)

---

### Post by lidex on 2010-05-17
Yeah, not always the best answer. I would suggest upgrading alsa via the alsa-upgrade link in my sig.

---

### Post by PoopLoops on 2010-05-17
> **lidex said:**
> Yeah, not always the best answer. I would suggest upgrading alsa via the alsa-upgrade link in my sig.

I upgraded as per your instructions. Sound still works fine, but still can't hear my mic. It still records, though, as in Preferences -> Sound the levels go up as I use the mic in the input tab. Unfortunately I didn't log the upgrade.  Though after installation it said it was successful, and it never ran into any errors. Checking the version gives me 

Advanced Linux Sound Architecture Driver Version 1.0.22.1.
Compiled on Apr 29 2010 for kernel 2.6.32-22-generic (SMP).

which I'm guessing isn't what I should be getting?

Wait, I just noticed something.  I did the hardware test from the System menu and *both* mics ended up using my internal mic and not the one I connected to the laptop.  So now I am completely clueless... :(

---

### Post by lidex on 2010-05-17
> **PoopLoops said:**
> I upgraded as per your instructions. Sound still works fine, but still can't hear my mic. It still records, though, as in Preferences -> Sound the levels go up as I use the mic in the input tab. Unfortunately I didn't log the upgrade.  Though after installation it said it was successful, and it never ran into any errors. Checking the version gives me 

Advanced Linux Sound Architecture Driver Version 1.0.22.1.
Compiled on Apr 29 2010 for kernel 2.6.32-22-generic (SMP).

which I'm guessing isn't what I should be getting?

No, should be 1.0.23

---

### Post by PoopLoops on 2010-05-17
I think I'll just do a clean install of 8.10 on a separate partition to have a safe place to go when s**t hits the fan and then do a clean install of 10.04 on the current one.

---

### Post by PoopLoops on 2010-05-22
I tried upgrading ALSA again and it's just not working. I would really rather not do a clean install, especially since there's no telling if it will work properly once I'm done. One thing I found out, though, is that in the "sound prefrences" menu I can only start up Sound Recorder if I'm set to Digital Duplex.  However, adjusting master volume on DD doesn't do anything to any songs I'm playing. And I don't have an "Analog Out + Digital In" option under the "hardware" tab.

It seems like there were a lot more options in the previous versions of Sound Preferences.  Why did they dumb it down like that?

Nevermind. I just turned off all hardware audio (for some reason my Radeon card is listed as an audio card wtf?) and I can still play music. I have no idea what to do anymore.

---

### Post by lidex on 2010-05-22
If you have alsa-backports installed, it will interfere with an upgrade.

---

### Post by PoopLoops on 2010-05-23
Okay yes, I had the backports installed. I took those out and now the installation worked. Sound works fine, but still can't hear my mic, although it can be recorded still. I don't know what else to try. Any slider I could find I maxed out, I tried all the various options in Sound Preferences under "hardware". This is just redonkulus.

Thanks for trying to help, though. I appreciate it. :)

---

### Post by lidex on 2010-05-23
Try gnome-alsamixer.
**Gnome-alsamixer**
Using Alt+F2 run dialog
```
 gnome-alsamixer 
```
**Use 'Edit -> Sound Card Properties' menu to enable elements.**
Soundcard tab to select / adjust levels.

Then use pulseaudio volume control (pavucontrol), input devices tab, to select mic. paprefs may be useful as well. Need to install?
```
sudo apt-get install pavucontrol paprefs pavumeter
```

---

### Post by PoopLoops on 2010-05-23
Played around with those programs for a bit, but nothing I tried worked.

---

### Post by lidex on 2010-05-23
Try this in paprefs:
[http://0pointer.de/lennart/projects/paprefs//screenshot.png]("http://0pointer.de/lennart/projects/paprefs//screenshot.png")

---

### Post by PoopLoops on 2010-05-23
That didn't work either. :(

---

### Post by killmess on 2010-11-26
_Install "gnome-alsamixer", and "pavucontrol"(the Pulseaudio Volume Control)
_in alsamixer:
_Edit-Sound Card Properties
_enable everything and close.
_down, tick the following: mic boost, analog capture boost, and whatever boost you may find.
_In Pulseaudio Volume Control:
_go to configuration
_In the dropdown menu, try differents profiles until you hear the sound of the mic. You should hear sound clearly; 

In my Audigy 2 value, if I don't make noise I hear a soft white sound. And the last options(the "profile" in Pulseaudio Volume Control) are: 

"Analog Stereo Output + Analog Mono Input."

Hope this serves, bye KM :)

---

### Post by bcschmerker on 2010-12-18
> **lidex said:**
> Try gnome-alsamixer....I found that I can control more components of my own Creative Laboratories® SB0350 PCI audio card (CA0102 chipset, emu10k1 drivers) from the Curses-based ALSAMixer binary (via GNOME Terminal).  In addition to the Primary stereo mix bus (which, on my own hybrid Everex® under Ubuntu® 10.04.1-LTS, drives both the rear line outs on the card plus an integrated headphone amplifier in an Audigy 2 I/O Drive), I can control the component gains (except PCM, whose signal absence from Capture I am still investigating, as of 18 December 2010) into the Capture stereo bus for recording locally and/or streaming to a remote server.

ALSAMixer can control multiple devices; F6 accesses the Device Select function.

---

