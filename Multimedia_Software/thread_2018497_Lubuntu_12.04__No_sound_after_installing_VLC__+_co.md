---
title: "Lubuntu 12.04 : No sound after installing VLC  + codecs"
date: 2012-07-06
forum: Multimedia Software
---

### Post by uncle-c on 2012-07-06
I'm running lubuntu (12.04) with Fluxbox window manager. Sound was working fine and and could view and hear all streaming content on Youtube and the news media sites. Decided to install VLC and its associated codecs so followed  steps 10,12 and 13 on this page :

[http://www.unixmen.com/201204-top-things-to-do-after-installing-ubuntu-2/]("http://www.unixmen.com/201204-top-things-to-do-after-installing-ubuntu-2/")

After re-booting I found that there was no sound. On previous installations I had got over the problem by adding myself to the associated audio group. This time however, even though I've added myself to audio,  pulse and pulse-access groups there is still no sound.I've checked the alsamixer settings and their is nothing untoward there. I feared  it could be pulseaudio causing problems. I uninstalled pulseaudio and the problem still exists.

```
unclec@Ubuntu-12:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 0: Intel ICH [Intel 82801DB-ICH4]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 4: Intel ICH - IEC958 [Intel 82801DB-ICH4 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
unclec@Ubuntu-12:~$

```

It's taken me two days to get the system up and running and properly configured and I really do want to avoid a clean re-install so any pointers would be appreciated.

---

### Post by ron999 on 2012-07-06
> **uncle-c said:**
> ...install VLC and its associated codecs so followed  steps 10,12 and 13 on this page :

[http://www.unixmen.com/201204-top-things-to-do-after-installing-ubuntu-2/]("http://www.unixmen.com/201204-top-things-to-do-after-installing-ubuntu-2/")

Hi
**Step 12** looks suspicious.:mad:
Those things aren't just "a few common codecs".

---

### Post by Rodney9 on 2012-07-06
```
sudo apt-get install pavucontrol
```


PulseAudio Volume Control (pavucontrol) is a simple GTK+ based volume control tool (mixer) for the PulseAudio sound server. 

In contrast to classic mixer tools this one allows you to control both the volume of hardware devices and of each playback stream separately. It also allows you to redirect a playback stream to another output device without interrupting playback.

Rodney

---

### Post by Cybernetic1 on 2013-06-23
> **Rodney9 said:**
> ```
sudo apt-get install pavucontrol
```


PulseAudio Volume Control (pavucontrol) is a simple GTK+ based volume control tool (mixer) for the PulseAudio sound server. 

In contrast to classic mixer tools this one allows you to control both the volume of hardware devices and of each playback stream separately. It also allows you to redirect a playback stream to another output device without interrupting playback.

Rodney

That looks nice, but the entire program has no place where you can "test hear" the sound.  Seems like an obvious flaw... :(

I'm using Lubuntu, sometimes when my login session gets timed out and I have to type a password to log in again, then after the re-login my sound is lost (I'm using a USB speaker).  It seems that this program does not solve the problem, and I have to log out of Lubuntu and then log into Ubuntu to get the sound, and then log into Lubuntu again.  Still don't know what's the problem....

---

