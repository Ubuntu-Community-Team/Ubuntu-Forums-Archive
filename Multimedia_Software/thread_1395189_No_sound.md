---
title: "No sound"
date: 2010-01-31
forum: Multimedia Software
---

### Post by mepuka on 2010-01-31
Hello everyone,

So I recently installed Ubuntu 9.10 (karmic) on my laptop (I'm an utter noob if you can't tell.) Everything seems to be working fine except for sound. I cannot get any sound from anywhere, youtube, rythmbox, anything.

Here is what I've tried:

I reinstalled alsa using the apt-get purge command, then reinstalled and rebooted and still nothing. I checked alsamixer to make sure nothing was muted and put everything on full volume.

the aplay -l command returns:

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC663 Analog [ALC663 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC663 Digital [ALC663 Digital]
  Subdevices: 0/1
  Subdevice #0: subdevice #0


and lspci -v gives me this for the audio device:

 00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
    Subsystem: ASUSTeK Computer Inc. Device 19a3
    Flags: bus master, fast devsel, latency 0, IRQ 32
    Memory at f9ff8000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

I've checked the alsaproject website to see if they have any drivers but I couldn't find any that matched. Under System -->Preferences-->Sound and under the hardware tab the only thing that is displayed is:

Internal Audio
*1 Output* 
[I]Digital Stereo Duplex (IEC958)
[/I]
I'm pretty sure that's not my audio device. As of now I'm stumped as to what to do besides reinstalling. Thanks in advance.

---

### Post by mepuka on 2010-01-31
I don't know if bumping is appropriate but I really need help with this.

---

### Post by sports.car.guy on 2010-01-31
Your sound is detected fine. No need for drivers.

A lot of the time no sound is due to the volumes being set at 0. Open up alsamixer or another mixer and make sure the volumes are up and not muted.

Usually that solves the problem.

There is a lot of documentation and posts on not having sound. Google it or use the search engine of your choice.

---

### Post by mepuka on 2010-01-31
Volume is at a 100% in alsamixer, I've tried everything I'm capable of right now short of reinstalling which I'm beginning to think might be the best idea, but there has to be something I'm not understanding. Is it possible that the drivers are detected but not being used??

---

### Post by sports.car.guy on 2010-01-31
> **mepuka said:**
> Volume is at a 100% in alsamixer, I've tried everything I'm capable of right now short of reinstalling which I'm beginning to think might be the best idea, but there has to be something I'm not understanding. Is it possible that the drivers are detected but not being used??

Every channel is, not just the master volume? You need to check every channel. There could be a master, then PCM, then speakers if only two channels, plus i bet one for headphones.

The driver is detected and loaded. It is being used, or it would not list what your sound chip is.

---

### Post by mepuka on 2010-01-31
Everything is up to 100%. I attached a screenshot of the alsamixer. Although why isn't there a bar available for the headphones and the other things? Could that be the reason? 

Also is my alsa up to date? On the alsa main page here [http://www.alsa-project.org/main/index.php/Main_Page](http://www.alsa-project.org/main/index.php/Main_Page) it shows on the right side that the latest alsa-driver version is 1.0.22.1 on the top of my alsa mixer it shows that the version is 1.0.20. Maybe i'm not up to date?

---

### Post by sports.car.guy on 2010-01-31
I am assuming you are running Ubuntu, not say Kubuntu. The reason why I ask is because Ubuntu uses PulseAudio along with Alsa components, while Kubuntu does not. I wouldn't be surprised if it is PulseAudio causing your problems.

What I can suggest is checking to see if you call the device hardware directly through Alsa and see if it works that way. If it does then it is PulseAudio.

Here is how to test your speakers for output.

[http://alsa.opensrc.org/index.php/Speaker-Test](http://alsa.opensrc.org/index.php/Speaker-Test)

---

### Post by mepuka on 2010-01-31
Yes I'm on Ubuntu.

So I tried the speaker-test. 

Typing in 

```
speaker-test -Dsurround51:Intel -c6 -twav
```

returns

```
speaker-test 1.0.20

Playback device is surround51:Intel
Stream parameters are 48000Hz, S16_LE, 6 channels
WAV file(s)
Playback open error: -16,Device or resource busy
```

It just repeats the last line (playback open error) over until I stop it. So I guess something, maybe pulseaudio, is hogging the resource somehow?

---

### Post by sports.car.guy on 2010-01-31
> **mepuka said:**
> Yes I'm on Ubuntu.

So I tried the speaker-test. 

Typing in 

```
speaker-test -Dsurround51:Intel -c6 -twav
```returns

```
speaker-test 1.0.20

Playback device is surround51:Intel
Stream parameters are 48000Hz, S16_LE, 6 channels
WAV file(s)
Playback open error: -16,Device or resource busy
```It just repeats the last line (playback open error) over until I stop it. So I guess something, maybe pulseaudio, is hogging the resource somehow?

Does the computer have multiple sound devices, like with an HDMI connection on the system it would. I could be trying to use that as the default.

---

### Post by mepuka on 2010-01-31
No there is only one sound option according to alsaconf, nothing else is plugged into my computer. I've run out of ideas and will be reinstalling shortly. If that doesn't work I'll try upgrading to alsa to tits latest version and getting rid of pulseaudio. It seems that a lot of people with this sound card are having issues.

---

### Post by sports.car.guy on 2010-01-31
> **mepuka said:**
> No there is only one sound option according to alsaconf, nothing else is plugged into my computer. I've run out of ideas and will be reinstalling shortly. If that doesn't work I'll try upgrading to alsa to tits latest version and getting rid of pulseaudio. It seems that a lot of people with this sound card are having issues.

Try removing it before a reinstall. I would. Or honestly switch to Kubuntu. Gnome is so unpolished compared to KDE in my opinion anyways and Kubuntu does not adhere to having PulseAudio like the other derivatives of it.

---

### Post by mepuka on 2010-02-01
Well after a clean install I still have no sound. I purged pulseaudio, upgraded to alsa version 1.0.22.1 and I still have no sound. I don't know what else to try this is extremely frustrating. I was expecting ubuntu to just work like it often claims.

---

### Post by sports.car.guy on 2010-02-01
> **mepuka said:**
> Well after a clean install I still have no sound. I purged pulseaudio, upgraded to alsa version 1.0.22.1 and I still have no sound. I don't know what else to try this is extremely frustrating. I was expecting ubuntu to just work like it often claims.

System sounds at boot then nothing, or nothing at all?

If you purged PulseAudio with Gnome there needs to be another service like Gstreamer in it's place I believe. I hate Gnome btw. KDE is more refined, polished, robust, and the standards other OS's strive to have in their GUI. Every, and I mean every single thing new and innovative MS has introduced was in KDE way before. Hell MS might as well just put KDE on as their GUI with how they blatantly take things from it and call it their own. If Gates steals it, it has to be good right?

One thing better about it is that it has been designed to work without needing an intermediate between the interface and access to the sound card. Gnome since the days of being an environment on top of Enlightenment has always needed a service to send sounds to the sound card. It was never designed out of it as it developed into it's own windowing environment and that was bad design in my opinion.

It has led everyone to go to PulseAudio in place of the Enlightenment Sound Daemon. The developer of PulseAudio claims his code is perfect and it is the distributions who are implementing it wrong, but if every and I mean every one of them has issues then it can't be them. It is one reason why Kubuntu I am sure has not adopted it while other distros with KDE have.

Have you tried Kubuntu by chance? That way you make sure there is no signs of PulseAudio where you just wiped the computer already I figured I would ask.

---

### Post by mepuka on 2010-02-01
Ok I solved it (well not me really) but I did what was necssary to solve it (ostensibly.) 

This is what I did from [here]("http://ubuntuforums.org/showthread.php?t=1159334"). 

I don't have a ALC1200 but I do have a ALC663, which is a card not officially supported by alsa. Everything sounds great so far.

---

