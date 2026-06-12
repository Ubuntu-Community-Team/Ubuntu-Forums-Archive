---
title: "Error:  MPC cannot open audio output.  Help please"
date: 2018-12-22
forum: Multimedia Software
---

### Post by jjhudak on 2018-12-22
I’ve been working at this for a while and I am out of ideas.  On Ubuntu server 16.04 I installed from the ubuntu repository using apt-get:  mpd and companion client mpc.  
  I launch mpd by:

  ```

sudo systemctl start mpd

```
  I get no errors and it shows up in the process table.

I run mpc by
  ```

mpc

```

  And it get the following:

  ```

jjh@pluto-server:~$ mpc
Glenn Miller - Sleigh Ride
[paused]  #7/7   0:00/3:46 (0%)
volume: n/a   repeat: off   random: on    single: off   consume: off
ERROR: Failed to open audio output 

```

I get sound out of the analog speaker jack:
  ```

jjh@pluto-server:speaker-test –l5

```

  The hardware devices are:
  ```

  jjh@pluto-server:~$ aplay -l
  **** List of PLAYBACK Hardware Devices **** 
card 0: Intel [HDA Intel], device 0: ALC662 rev1 Analog [ALC662 rev1 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC662 rev1 Digital [ALC662 rev1 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

I am at a loss as to how to fix the "Failed to open audio output" problem…Any suggestions welcome.
Ty

  J

---

### Post by CatKiller on 2018-12-23
> When run as its own user as per the wiki instructions, mpd will be  unable to send sound to another user's pulseaudio server. Rather than  setting up pulseaudio as a system-wide daemon, a practice strongly  discouraged by upstream, you can instead configure mpd to use  pulseaudio's tcp module to send sound to localhost:

[https://wiki.archlinux.org/index.php/Music_Player_Daemon](https://wiki.archlinux.org/index.php/Music_Player_Daemon)

---

### Post by jjhudak on 2018-12-23
I am not using PulseAudio server. It is not installed and it is commented out in mpd.conf.  I am using ALSA.
i looked through the doc from the pointer ypo provided. It is for arch and I am using Ubuntu.  Does it still apply?

---

### Post by CatKiller on 2018-12-23
> **jjhudak said:**
> I am not using PulseAudio server. It is not installed and it is commented out in mpd.conf.  I am using ALSA.
i looked through the doc from the pointer ypo provided. It is for arch and I am using Ubuntu.  Does it still apply?

The Arch wiki is really good for nitty gritty stuff. Sometimes config files are in a different place between Ubuntu and Arch, but it generally explains the overall structure of things well.

I've not configured ALSA directly for a long time. It's a complete pain, and applications have a habit of claiming the audio device and not giving it back, as I recall.

Since your user can use ALSA OK, the configuration of ALSA must be more or less OK. The Arch wiki has some stuff on including details about your ALSA configuration in your mpd.conf if autodetect didn't work, which it seems it hasn't. You might need to make sure that your mpd user has permission to use the sound device, and that nothing else is claiming it.

---

### Post by jjhudak on 2018-12-23
> **CatKiller said:**
> 
Since your user can use ALSA OK, the configuration of ALSA must be more or less OK. The Arch wiki has some stuff on including details about your ALSA configuration in your mpd.conf if autodetect didn't work, which it seems it hasn't. You might need to make sure that your mpd user has permission to use the sound device, and that nothing else is claiming it.

Thanks for the input.  Ill review the doc.  
Would you explain how to make sure that mpd user has permission to use sound device and nothing else is claiming It?

i did associate the audio with the user.  I did check to make sure that the sound card was the default device e.g a ‘0’ ( I forget where I looked at that).

When I run mpc ( the local client app) itt says that the audio is “paused”.......I don’t understand the meaning of that word I this context.

---

### Post by CatKiller on 2018-12-23
> **jjhudak said:**
> Would you explain how to make sure that mpd user has permission to use sound device and nothing else is claiming It?

It's normally just a case of putting the mpd user in the right groups. It's probably already happened automatically, but if mpd doesn't have permission to use the sound device, it won't work.

I *think* that ```
fuser -v /dev/snd/*
``` will see who's using the device, but I could be wrong. As I said, it's a long time since I played with this stuff.

---

