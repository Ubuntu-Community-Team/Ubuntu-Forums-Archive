---
title: "Pulseaudio doesn't work"
date: 2010-09-11
forum: Multimedia Software
---

### Post by frostig on 2010-09-11
I have a big problem in my system, this time it's the audio.

When I installed my 64 bit system of Ubuntu 10.04 the sound worked very well and I were very happy. The problem started however when I installed Skype which uses pulseaudio. As soon as I start skype (or any other application that uses pulse, HoN for example) the applications sound output or input does not work at all.

If I have pulseaudio started in some way, applications that I suppose do not use it like spotify or flash player stops to produce sounds. And when I type "pulseaudio" in the terminal it gives me this: 
> 
[EMAIL="markus@kvant:%7E/.pulse"]markus@kvant:~/.pulse[/EMAIL]$ pulseaudio
E: pid.c: Daemon already running.
E: main.c: pa_pid_file_create() failed.
Recently I tried to solve this problem by searching for answers, and I've tried many solutions as downloading pulseaudio device chooser to change default server and stuff like that.

Nothing has worked tho except making the daemon auto respawn (which I turned off by writing a small config in the ~./pulse/ folder). When pulse is active, my sound controller disappears and when I try to open the volume controller it says: "Waiting for the sound system to respond". The funny thing is, before some recently installed packages that someone at the forums suggested someone else to try, I've had this problem that it autorespawn and I don't know what package it was. All tho, I can enter alsamixer in the terminal and everything seems to be normal.

This is my hardware:

> markus@kvant:~$ lspci | grep Audio
02:00.1 Audio device: nVidia Corporation High Definition Audio Controller (rev a1)
80:01.0 Audio device: VIA Technologies, Inc. VT1708/A [Azalia HDAC] (VIA High Definition Audio Controller) (rev 10)
markus@kvant:~$ I am not currently using the nvidia audio controller and might that be the problem? I have really no idea how to solve this problem or how to even start solving it. The nvidia audio controller is on a newly purchased graphic card and I had no problems with pulse before that (of what I can remember).

Please help!


Update:

Messing around in the Preferences->Sound while running pulse in the terminal made it output some strange stuff. And I changed some device and the sound started to work somehow for a short period of time in spotify. But when I tried to restart the application it failed as usual, and no other sound like in flashplayer was availble.

This is the output:

> W: ratelimit.c: 23 events suppressed
E: alsa-source.c: snd_pcm_avail: Device or resource busy

---

### Post by frostig on 2010-09-13
Anyone? Please I really need to use skype and other applications :/

---

### Post by frostig on 2010-09-13
Updates:

Now I booted up my system and no sound could be heard. I typed Pulseaudio in the terminal to check if it was running and for some output and I got this:

> markus@kvant:~$ pulseaudio
E: module-alsa-card.c: Failed to find a working profile.
E: module.c: Failed to load  module "module-alsa-card" (argument: "device_id="0" name="pci-0000_02_00.1" card_name="alsa_card.pci-0000_02_00.1" tsched=yes ignore_dB=no card_properties="module-udev-detect.discovered=1""): initialization failed.

Help me please! It's very frustrating to not be able to hear anything :S

---

### Post by Bucky Ball on 2010-09-13
Pulse Device Chooser, playback streams. Open Skype and make a test call. The moment you see a playback stream(s) come up, right click and choose 'Move Stream' and move the stream to the device of your choosing eg. your headset or speakers.

This worked for me (and should work with any other audio app; you change stream the same way) but I could never get Skype ringing through the speakers and everything else coming through the headset. Seemingly impossible. I much preferred ALSA where you could choose devices right there in Skype->Options->Audio Devices.

Good luck.

ps: It took me forever and a day to find this solution. Absurd really.

---

