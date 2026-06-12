---
title: "No sound in 10.04"
date: 2011-07-23
forum: Multimedia Software
---

### Post by snarus on 2011-07-23
I installed ubuntu 10.04 but no sound.
So i downloaded alsa source code, compiled
and make install. I run modprobe snd-es18xx
if I start alsamixer the soundcard is recognized as ESS AudioDrive ES1869.
I can adjust settings ..  But there is no sound, and
when I open sound preferences no sound card is recognized

Dont know what to do now...

---

### Post by BicyclerBoy on 2011-07-23
I would think you need to restart the pulseaudio server because the alsa devices changed after pa had started/tried to start.

The original problem was probably just config.
Often attempts to build alsa just causes more trouble.

Is your h/w some oddball laptop that needs a specific modprobe option ?

The lack of output sound is from trying to use what ?
speaker-test ?

There are a couple of good audio ppas if you need a later alsa.
[https://launchpad.net/~ubuntu-audio-dev/+archive/ppa?field.series_filter=lucid](https://launchpad.net/~ubuntu-audio-dev/+archive/ppa?field.series_filter=lucid)
(driver modules only)
[https://launchpad.net/~team-iquik/+archive/alsa?field.series_filter=lucid](https://launchpad.net/~team-iquik/+archive/alsa?field.series_filter=lucid)

---

### Post by lidex on 2011-07-23
> **snarus said:**
> I installed ubuntu 10.04 but no sound.
So i downloaded alsa source code, compiled
and make install. I run modprobe snd-es18xx
if I start alsamixer the soundcard is recognized as ESS AudioDrive ES1869.
I can adjust settings ..  But there is no sound, and
when I open sound preferences no sound card is recognized

Dont know what to do now...

Recompiling alsa probably not the best idea this early on. The alsa install is likely borked. Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.

---

### Post by snarus on 2011-07-24
Thanx for help..  
Here is the link:
[http://www.alsa-project.org/db/?f=493d5745ca7d19304c2e6947986e9250153d994a](http://www.alsa-project.org/db/?f=493d5745ca7d19304c2e6947986e9250153d994a)

---

### Post by lidex on 2011-07-24
```
!!ALSA Version
!!------------

Driver version:     1.0.21
Library version:    1.0.16
Utilities version:  1.0.16



```
As I suspected. Follow the alsa upgrade link in my sig and use the script there to update your drivers.

---

### Post by lidex on 2011-08-17
@snarus
I'm going to assume your problem is resolved. If you would be so kind as to provide some feedback, 
you can access the solved tag using 'Thread Tools' up top. Thanks.

---

