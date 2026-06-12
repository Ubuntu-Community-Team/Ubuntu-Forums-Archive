---
title: "No sound in Ubuntu 9.10"
date: 2010-02-27
forum: Multimedia Software
---

### Post by lazyworkhorse on 2010-02-27
I tried the Karmic Caveats wiki and I read through the general sound wiki. I have the latest kernel and alsa drivers, and I have no sound. I have an HP a1100y with intel HD Audio, and I have no idea what else to try.

---

### Post by lazyworkhorse on 2010-03-01
*bump

---

### Post by sturunner on 2010-03-02
Same problem.

---

### Post by cph05a on 2010-03-02
run
```
gnome-alsamixer
```
and just double check that none of your speakers are muted and that the sound is turned up. It may sound silly, but sometimes the front speakers are muted by default (this was the case on my mac).

---

### Post by Miki800 on 2010-03-05
> **cph05a said:**
> run
```
gnome-alsamixer
```
and just double check that none of your speakers are muted and that the sound is turned up. It may sound silly, but sometimes the front speakers are muted by default (this was the case on my mac).

thank you so much, the default speakers icon on the ubuntu panel showed me that the only option was unmute
but after doing what you said - installing and running gnome-alsamixer I saw that everything else (not skipping one thing) was muted, this has fixed everything!

I read somewhere else that I should've upgrade my sound drivers which is just garbage speak sadly I did what they told me and even restarted, what a waste of my time.

thank you your way worked!

---

### Post by lazyworkhorse on 2010-05-08
I discovered that my sound "works" in that I can plug devices into the back audio ports, however the headphone and mic jack on the front do not work. If there is a way to get them to work, that would be great, otherwise I will survive.

---

### Post by lidex on 2010-05-08
> **Miki800 said:**
> 
I read somewhere else that I should've upgrade my sound drivers which is just garbage speak sadly I did what they told me and even restarted, what a waste of my time.


Every situation is different and an alsa upgrade is sometimes essential to enable sound as on my HP laptop. Sorry you wasted your time, but maybe you should have checked the basics first.

---

### Post by lidex on 2010-05-08
> **lazyworkhorse said:**
> I discovered that my sound "works" in that I can plug devices into the back audio ports, however the headphone and mic jack on the front do not work. If there is a way to get them to work, that would be great, otherwise I will survive.

Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
cat /proc/asound/version
head -n 1 /proc/asound/card*/codec#* 
```
Terminal="Applications->Accessories->Terminal"
Please post text output using code tags. Also helpful is the make/model of your PC/Laptop.

---

### Post by lazyworkhorse on 2010-05-09
> **lidex said:**
> Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
cat /proc/asound/version
head -n 1 /proc/asound/card*/codec#* 
```Terminal="Applications->Accessories->Terminal"
Please post text output using code tags. Also helpful is the make/model of your PC/Laptop.

MY computer is an HP a1100y

```

chris@hp1ubuntu:~$ uname -a
Linux hp1ubuntu 2.6.31-21-generic #59-Ubuntu SMP Wed Mar 24 07:28:56 UTC 2010 i686 GNU/Linux
chris@hp1ubuntu:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC880 Analog [ALC880 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC880 Digital [ALC880 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
chris@hp1ubuntu:~$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.20.
chris@hp1ubuntu:~$ head -n 1 /proc/asound/card*/codec#*
Codec: Realtek ALC880

```

---

### Post by lidex on 2010-05-09
I would suggest updating your alsa install. Use the upgrade-script link in my sig.

---

### Post by enchesss on 2010-05-09
my sound was muted by default on new install

fix:

left click on sound/speaker icon next to network icon in top right of desktop

click on unmute

unmute/mute is the first menu item when you click on the speaker.

(yes i have read the thread)

---

### Post by lidex on 2010-05-09
> **enchesss said:**
> my sound was muted by default on new install

fix:

left click on sound/speaker icon next to network icon in top right of desktop

click on unmute

unmute/mute is the first menu item when you click on the speaker.

Awesome. Did you actually read the thread?

---

### Post by lazyworkhorse on 2010-05-09
> **lidex said:**
> I would suggest updating your alsa install. Use the upgrade-script link in my sig.

I downloaded the script, extracted it, chose run in terminal, and the terminal window flashed, but the script did not run.

---

### Post by lidex on 2010-05-11
You followed these directions:
> Short Alsa-Upgrade script install instructions:

1. download the script and save it somewhere
2. cd <your-download-dir>
3. tar xvf AlsaUpgrade-1.0.23-2.tar
4. sudo ./AlsaUpgrade-1.0.23-2.sh -d
5. sudo ./AlsaUpgrade-1.0.23-2.sh -c
6. sudo ./AlsaUpgrade-1.0.23-2.sh -i
7. sudo shutdown -r 0

---

### Post by lazyworkhorse on 2010-05-15
Make compile error 2

what does that mean?

---

### Post by lidex on 2010-05-16
You may be missing some necessary packages. Try this:
```
sudo apt-get install build-essential
```

---

