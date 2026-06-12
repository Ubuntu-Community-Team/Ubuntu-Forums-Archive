---
title: "Problems with Ardour / Jack"
date: 2010-05-23
forum: Multimedia Software
---

### Post by rainjam on 2010-05-23
Apologies in advance if this has a trivial answer... I've had a look but can't see anything that seems to help.

I just installed the Ubuntu Studio packages on "normal" Ubuntu, 10.04 -
```
sudo apt-get install ubuntustudio-audio
```

- and I can't get Ardour working. It complains that "Ardour could not start JACK". On running JACK on its own, I get the following:

```
20:50:15.010 Startup script...
20:50:15.013 artsshell -q terminate
sh: artsshell: not found
20:50:15.418 Startup script terminated with exit status=32512.
20:50:15.419 JACK is starting...
20:50:15.422 /usr/bin/jackd -r -dalsa -r44100 -p1024 -n2 -D -Chw:1 -P/dev/audio -Xraw
jackd 0.118.0
Copyright 2001-2009 Paul Davis, Stephane Letz, Jack O'Quinn, Torben Hohn and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
20:50:15.481 JACK was started with PID=8175.
no message buffer overruns
JACK compiled with System V SHM support.
loading driver ..
apparent rate = 44100
creating alsa driver ... /dev/audio|hw:1|1024|2|44100|0|0|nomon|swmeter|-|32bit
ALSA lib control.c:902:(snd_ctl_open_noupdate) Invalid CTL /dev/audio
control open "/dev/audio" (No such file or directory)
ALSA lib pcm.c:2211:(snd_pcm_open_noupdate) Unknown PCM /dev/audio
ALSA: Cannot open PCM device alsa_pcm for playback. Falling back to capture-only mode
cannot load driver module alsa
20:50:15.673 JACK was stopped successfully.
20:50:15.675 Post-shutdown script...
20:50:15.677 killall jackd
jackd: no process found
20:50:16.106 Post-shutdown script terminated with exit status=256.
20:50:17.580 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.

```
Any ideas? I'm trying to run this on a Dell Mini 10v netbook. (I'm expecting it to be underpowered, but it would be nice if it at least started.)

---

### Post by rainjam on 2010-05-24
*bump*

any ideas anyone?

---

### Post by cchhrriiss121212 on 2010-05-25
What do you have set to use /dev/audio in the setup window? It should not be there. I also notice you are using hw:1 as your interface, what device is this?

---

### Post by rainjam on 2010-05-25
I don't have anything "special" set up as far as I know, so if it shouldn't be there, I guess I need to get rid of it (not sure how though!). I have installed Spotify under Wine, although that doesn't work at the moment either (it did at one point).

All the hardware is what came with the machine, so I guess hw:1 would be the onboard sound card - how would I check?

---

### Post by cchhrriiss121212 on 2010-05-25
Open the setup window in jack and look at the devices listed under interface. Hw:0 is normally the onboard sound, so you might be using another audio device.
Could you also post the result of putting "aplay -l" into a terminal?

Regarding the netbook, you should be able to run a few audio apps comfortably if you switch to a lighter desktop environment.

---

### Post by rainjam on 2010-05-25
Thanks so much for this. Here's the output of aplay -l:

~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC272 Analog [ALC272 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

I can't find any list of interfaces in Jack Control - attached are two screengrabs, I'm probably looking in the wrong place?

---

### Post by cchhrriiss121212 on 2010-05-25
This is the right place to look. On the first screenshot you can see that input is set to hw:1, and output is set to /dev/audio. Set both of those to default and then try starting jack again.

---

### Post by rainjam on 2010-05-26
You are awesome and I am an idiot. It now works! Thanks so much.

---

