---
title: "Sound problems with new Pulse, solved - wants to know why"
date: 2008-04-24
forum: Multimedia Software
---

### Post by Gorgamel on 2008-04-24
When I upgraded to new Ubuntu, and thus getting new Pulse sound server, the sound died when I rebooted.
After a lot of searching and reading and testing, I saw one solution with installing a flashsupport deb (see [https://wiki.ubuntu.com/PulseAudio](https://wiki.ubuntu.com/PulseAudio) under "Firefox/Flash and PulseAudio"). After restarting FF and again trying MPlayer, both worked with ease.
The problems (what it seamed) that I had, was the inability to connect to the sound server/socket (see output belove).

Do anyone have any idea what was wrong?? I can understand that the lib would help for playing flash animations but making mplayer work seams odd :S

Output from MPlayer:
```
AO: [pulse] Failed to connect to server: Connection terminated
*** PULSEAUDIO: Unable to connect: Connection terminated
[AO_ALSA] Playback open error: Connection refused
[AO OSS] audio_setup: Can't open audio device /dev/dsp: Device     or resource busy
*** PULSEAUDIO: Unable to connect: Connection terminated
[AO_ALSA] Playback open error: Connection refused
[AO ARTS] loading the aRts backend "/usr/lib/libartscbackend.l    a" failed
[AO ESD] latency: [server: 0.28s, net: 0.00s] (adjust 0.28s)
AO: [esd] 44100Hz 2ch s16le (2 bytes per sample)
Video: no video
Starting playback...
A:  -0.0 (unknown) of 1.0 (01.0) ??,?%
```

---

### Post by andrebrait on 2008-04-24
Pulseaudio is pretty bugged for me

I wasn't successful to make any game play audio
That's because they use SDL. So I installed the package with all plugins for SDL, **libsdl1.2debian-all**.
After, I used 

```
export SDL_AUDIODRIVER=pulse
```

OR

```
export SDL_AUDIODRIVER=alsa
```

Any other option, including dma or oss wouldn't work.

I found this tip in Warsow's documentation about linux sound.

(Ubuntu 8.04LTS x86-64)

---

### Post by zman0900 on 2008-04-29
I had the same problem with no games playing audio.  Other than that, I really like pulse audio, so luckily I also found a similar fix.  I instead replaced libsdl1.2debian-alsa with libsdl1.2debian-pulseaudio and now everything works flawlessly.  (This is with padevchooser, pavucontrol, and the like all installed as well.)  I don't know why they didn't make that setup the default install for hardy...:confused:

Edit:  After some more testing, I've began to realize that most of the games that are using the sdl pulse driver are now getting very jerky, unsteady sound.

---

### Post by angrykeyboarder on 2008-04-30
I am totally baffeled as to why pavucontrol isn't instaleld by default. It is in fact, a default in Mandriva 2008.1 and Fedora 9.  You **need** it to to set default cards for PulseAudio **and** to adjust the for individual applications.

---

### Post by zman0900 on 2008-04-30
I seem to have solved my jerky audio problem by installing libsdl1.2debian-all and setting SDL_AUDIODRIVER=esd.  This seems to have solved the problem for numerous games.  This even allows them to play through pulse, because they do show up in the Pulse volume control.  If this works for you, you can add the following to ~/.profile to make it permanent:

```
# Make sdl audio work properly with Pulse
export SDL_AUDIODRIVER=esd
```

---

### Post by Benjamin_Vedder on 2008-04-30
I had a lot of trouble with pulseaudio and games. When i use export SDL_AUDIODRIVER=esd the sound gets almost one second delayed, export SDL_AUDIODRIVER=pulse makes the sound crackly and export SDL_AUDIODRIVER=alsa does not work when i play music at the same time. Can anyone confirm the delay, or even better, make the delay go away?

---

### Post by zman0900 on 2008-04-30
> **Benjamin_Vedder said:**
> I had a lot of trouble with pulseaudio and games. When i use export SDL_AUDIODRIVER=esd the sound gets almost one second delayed, export SDL_AUDIODRIVER=pulse makes the sound crackly and export SDL_AUDIODRIVER=alsa does not work when i play music at the same time. Can anyone confirm the delay, or even better, make the delay go away?

I can confirm all of those things.

I have started a new thread where I describe how to get all this Pulse stuff working at what I think is the best it can do:
[http://ubuntuforums.org/showthread.php?t=776739](http://ubuntuforums.org/showthread.php?t=776739)

---

