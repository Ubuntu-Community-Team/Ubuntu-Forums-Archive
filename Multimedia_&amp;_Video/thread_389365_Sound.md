---
title: "Sound"
date: 2007-03-20
forum: Multimedia &amp; Video
---

### Post by davholla on 2007-03-20
I had sound and everything working on Ubuntu 6.0.6 and it has all stopped.
I get "can not establish connection to the server".  Any ideas ?

---

### Post by eggdeng on 2007-03-20
Did you update your kernel? If so, try booting into an earlier kernel by choosing from the list on the grub boot screen.

---

### Post by davholla on 2007-03-21
No I did not.

---

### Post by eggdeng on 2007-03-21
Can you hear the login sound when you boot? 

You've probably done most of these already, but just to eliminate possibilities. 

In ->System ->Preferences->Sounds, the box 'enable sound mixing' should be unchecked & the Default sound card should coincide with your card. If you don't know what card you have, run ```
lspci | grep Audio
``` from a terminal.

Check that your user is a member of the audio group. System ->Users and groups->on the groups tab, select audio->properties & group members.

You can get more data about your current set up from the output of
```
cat /proc/asound/cards
```, ```
cat /proc/asound/modules
``` and ```
cat /proc/asound/version
```.

---

### Post by davholla on 2007-03-26
```
lspci | grep Audio
0000:00:1f.5 Multimedia audio controller: Intel Corporation 82801BA/BAM AC'97 Audio (rev 12)

```


```
cat /proc/asound/cards
cat /proc/asound/cards
0 [U0x46d0x8d9    ]: USB-Audio - USB Device 0x46d:0x8d9
                     USB Device 0x46d:0x8d9 at usb-0000:00:1f.2-2, full speed
1 [UART           ]: MPU-401 UART - MPU-401 UART
                     MPU-401 UART at 0x330, irq 10
2 [I82801BAICH2   ]: ICH - Intel 82801BA-ICH2
                     Intel 82801BA-ICH2 with ALC200,200P at 0xdc00, irq 193

```


```
cat /proc/asound/modules
0 snd_usb_audio
1 snd_mpu401
2 snd_intel8x0

```


```
cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.10rc3 (Mon Nov 07 13:30:21 2005 UTC).

```

---

### Post by eggdeng on 2007-03-28
From the output you posted, it looks as if alsa is detecting 3 sound devices on your system: a usb audio device (have you got usb speakers?) plus another device (a modem?) in addition to your real sound card. As the usb device is listed first in /asound/cards and /asound/modules, this is probably the default device. So you probably need to change settings to get alsa to use your Intel device as the default.

Try ```
sudo asoundconf set-default-card Intel
``` & reboot.

---

### Post by davholla on 2007-03-28
Thanks for that.

Since my original post I have rebooted and bizarely that solved the problem !!

---

