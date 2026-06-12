---
title: "No sound in Lucid"
date: 2010-05-02
forum: Multimedia Software
---

### Post by petru.marginean on 2010-05-02
Hi,

The sound doesn't work. It looks very similar with this:
[http://en.gentoo-wiki.com/wiki/PulseAudio#Locked_sound_device](http://en.gentoo-wiki.com/wiki/PulseAudio#Locked_sound_device)
(just the Dummy Output available in pavucontrol...)

However the it seems no other process locks the sound.

I can see this error when manually starting pulse audio:
"Failed to open module "module-alsa-card": file not found"

```
$> pulseaudio
//...
D: cli-command.c: Checking for existance of '/usr/lib/pulse-0.9.21/modules/module-udev-detect.so': success
D: module-udev-detect.c: /dev/snd/controlC0 is accessible: yes
D: module-udev-detect.c: /devices/pci0000:00/0000:00:1b.0/sound/card0 is busy: no
D: module-udev-detect.c: Loading module-alsa-card with arguments 'device_id="0" name="pci-0000_00_1b.0" card_name="alsa_card.pci-0000_00_1b.0" tsched=yes ignore_dB=no card_properties="module-udev-detect.discovered=1"'
E: module.c: Failed to open module "module-alsa-card": file not found
I: module-udev-detect.c: Card /devices/pci0000:00/0000:00:1b.0/sound/card0 (alsa_card.pci-0000_00_1b.0) failed to load module.
I: module-udev-detect.c: Found 1 cards.

```The file actually exists:
```
$> ls -l /usr/lib/pulse-0.9.21/modules/module-alsa-card.so
-rw-r--r-- 1 root root 17940 2010-03-26 19:40 /usr/lib/pulse-0.9.21/modules/module-alsa-card.so
```Completely reinstalled pulseaudio, but the error still persists.

Please help,
Petru

---

### Post by lidex on 2010-05-02
What is the output of this command:
```
sudo fuser -v /dev/dsp* /dev/snd/* /dev/seq*
```

---

### Post by petru.marginean on 2010-05-02
Thanks for reply.
This is the output:
```
$> sudo fuser -v /dev/dsp* /dev/snd/* /dev/seq*
                     USER        PID ACCESS COMMAND
/dev/snd/seq:        timidity   7656 F.... timidity

```I solved it by getting the source code for pulseaudio-0.9.21, and install it in /usr/local/bin:

```
$> /usr/local/bin/pulseaudio --version
pulseaudio 0.9.21
```I've deleted the one that comes from Synaptic:

```
$> /usr/bin/pulseaudio --version
pulseaudio 0.9.21-63-gd3efa-dirty
$> sudo rm -fr /usr/bin/pulseaudio  

```and it works fine now!
The fuser command returns now:

```
 $> sudo fuser -v /dev/dsp* /dev/snd/* /dev/seq*
                     USER        PID ACCESS COMMAND
/dev/snd/controlC0:  petrum    16857 F.... pulseaudio
/dev/snd/seq:        timidity   7656 F.... timidity

```

Regards,
Petru

---

### Post by lidex on 2010-05-03
Good work! Please mark the thread as solved using 'Thread Tools' up top.

---

### Post by petru.marginean on 2010-05-11
Hi,

I'm reopening this thread, since the issue is not completely solved. I've figured out that two users logged in at the same time cannot both have the sound working!

In order to reproduce it, I follow these steps:
1. first I login as user A ('lori' in the example below) and the sound is working for this user
2. then I login as user B ('petrum' in the example), but the user A stays logged in; there is no sound for user B. I noticed at this point that starting pulseaudio manually produces the error:
```
$> pulseaudio -v
...
I: core-util.c: Failed to acquire high-priority scheduling: Permission denied
...
```Also:

```
$> sudo fuser -v /dev/snd/*
                     USER        PID ACCESS COMMAND
/dev/snd/controlC0:  gdm       21721 F.... pulseaudio
                     lori      26228 F.... pulseaudio
/dev/snd/pcmC0D0p:   lori      26228 F...m pulseaudio
/dev/snd/seq:        timidity   7603 F.... timidity
```Then if I kill the other pulseaudio:
```
$> sudo kill 26228
```pulseaudio starts fine, and the sound starts working for user B:

```
$> sudo fuser -v /dev/snd/*
                     USER        PID ACCESS COMMAND
/dev/snd/controlC0:  petrum    18948 F.... pulseaudio
                     gdm       21721 F.... pulseaudio
/dev/snd/pcmC0D0p:   petrum    18948 F...m pulseaudio
/dev/snd/seq:        timidity   7603 F.... timidity

```Is it possible to have the sound working for both users?
(w/o logging out)

Regards,
Petru

---

### Post by Popaul on 2010-05-12
Have you checked the extensive:
[http://ubuntuforums.org/showthread.php?t=205449&highlight=no+sound+lucid](http://ubuntuforums.org/showthread.php?t=205449&highlight=no+sound+lucid)

I always forgot one or 2 things, and this is the source... well worth a 'favorite' link. Almost everytime I upgrade to a new version of Ubuntu, the sound goes off... and I was always able to restore it with simple tricks from this comprehensive guide.
Not very good for Ubuntu, but a lot of thanks for the guys who put this guide up.

---

### Post by petru.marginean on 2010-05-13
Ok, thanks to Daniel Chen I found the solution: "Neither of the users should be in the audio group."

```

gnome-system-tools (2.29.91-0ubuntu2) lucid; urgency=low

  * debian/patches/26_user_profiles_conf.patch:
    - Don't add users to the audio group. This is consistent with
      user-setup and fixes an issue with sound device permissions when
      switching between users. Thanks to Igor Wojnicki for spotting
      this (LP: #433654)

 -- Chris Coulson <[EMAIL="chris.coulson@canonical.com"]chris.coulson@canonical.com[/EMAIL]>   Sun, 07 Mar 2010 11:56:59 +0000
```I can confirm that now it is working for both users!

```
$> sudo fuser -v /dev/dsp* /dev/snd/* /dev/seq*
                     USER        PID ACCESS COMMAND
/dev/snd/controlC0:  gdm         369 F.... pulseaudio
                     lori      22330 F.... pulseaudio
                     petrum    23521 F.... pulseaudio
/dev/snd/pcmC0D0p:   petrum    23521 F...m pulseaudio
/dev/snd/seq:        timidity   6566 F.... timidity

```Regrads,
Petru

---

