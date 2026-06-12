---
title: "Can't get my Broadcom wireless card to work"
date: 2011-09-16
forum: Networking &amp; Wireless
---

### Post by xdyldogx on 2011-09-16
So I recently found my old laptop and decided to install Ubuntu on it to speed it up. For the past couple hours I've been pulling my hair out trying to get this wireless card to work. I am connected through an ethernet cable right now. I have looked at the topics here and I keep getting errors when following their steps, so I have made a topic for some help.

I have a Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 03).

Thanks! ):P

---

### Post by Pariah819 on 2011-09-16
I have a Broadcom BCM4313 and it requires a proprietary driver to work properly, did you see if a proprietary driver is available for your device?

---

### Post by xdyldogx on 2011-09-16
> **Pariah819 said:**
> I have a Broadcom BCM4313 and it requires a proprietary driver to work properly, did you see if a proprietary driver is available for your device?

Whenever I go to "Additional Drivers" it says "No proprietary drivers are in use on this system"

---

### Post by wildmanne39 on 2011-09-16
Hi, are you using 11.04?

---

### Post by xdyldogx on 2011-09-16
> **wildmanne39 said:**
> Hi, are you using 11.04?

Yes I am.

---

### Post by wildmanne39 on 2011-09-16
Hi, I have that same card and when I tried to install the firmware I found out that there is a bug in the process for installing it in 11.04 so I did it this way thanks to chili555.

Down load the b43 zip file then drag and drop the file to your desktop. Right-click it and select Extract Here, then disconnect your wired connection. Open a terminal and do:
```
sudo mkdir /lib/firmware/b43
sudo cp Desktop/b43/*  /lib/firmware/b43
sudo rmmod -f b43
sudo rmmod -f ssb
sudo modprobe b43
```
run these commands one at a time.

If you installed other drivers you need to remove them or blacklist them for this to work properly, if you need help with that we will work on it after you install this driver.
Thank you

---

### Post by xdyldogx on 2011-09-16
Ahh! It works! Thank you so much!

Yes, I would like help removing the other drivers I installed, linux noob here :P

Once again, thank you so much,

---

### Post by wildmanne39 on 2011-09-16
Hi, that was quick, post the results of:
```
lsmod
``` 
here by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by xdyldogx on 2011-09-16
```
Module                  Size  Used by
b43                   296610  0 
ssb                    45942  1 b43
sha256_generic         20911  2 
cryptd                 19801  0 
aes_i586               16956  432 
aes_generic            38023  1 aes_i586
binfmt_misc            13213  1 
dm_crypt               22463  1 
snd_intel8x0           33213  2 
snd_ac97_codec        105614  1 snd_intel8x0
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80042  2 snd_intel8x0,snd_ac97_codec
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    55295  11 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
arc4                   12473  2 
soundcore              12600  1 snd
snd_page_alloc         14073  2 snd_intel8x0,snd_pcm
mac80211              257001  1 b43
cfg80211              156212  2 b43,mac80211
pcmcia                 39671  0 
joydev                 17322  0 
ppdev                  12849  0 
yenta_socket           27230  0 
pcmcia_rsrc            18292  1 yenta_socket
parport_pc             32111  1 
dell_laptop            13515  0 
pcmcia_core            21505  3 pcmcia,yenta_socket,pcmcia_rsrc
psmouse                73312  0 
serio_raw              12990  0 
dcdbas                 14054  1 dell_laptop
lp                     13349  0 
parport                36746  3 ppdev,parport_pc,lp
radeon                900494  3 
ttm                    65184  1 radeon
drm_kms_helper         40745  1 radeon
drm                   184164  5 radeon,ttm,drm_kms_helper
tg3                   131476  0 
video                  18951  0 
i2c_algo_bit           13184  1 radeon
```

---

### Post by wildmanne39 on 2011-09-16
Hi, good news I do not see any other drivers loaded for your card so you are good, if I helped you even a little bit would you click on the link in my signature and support me for ubuntu membership also, would you please go to the top of the page and mark this thread solved by clicking on thread tools. Thank you so much.

---

