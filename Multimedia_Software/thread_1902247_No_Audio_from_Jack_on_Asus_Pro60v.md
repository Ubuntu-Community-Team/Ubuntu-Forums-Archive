---
title: "No Audio from Jack on Asus Pro60v"
date: 2011-12-30
forum: Multimedia Software
---

### Post by utillich on 2011-12-30
Hi 

I recently installed Ubuntu 11.10 on a friends old Laptop (ASUS PRO60V). Everything is running great except I cant get any audio output from the output jack.

Audio works fine through the internal speakers, but once I plug in speakers or headphones into the jack (combined SPDIF & Analog) the internal speakers are muted but there is no output on the external speakers. My guess is it is trying to output through SPDIF instead of analog...


I tried different outputs settings in the sound setting menu and also looked at alsa mixer, but couldn't get it to work. 

Any help would be much apreciated!

#Kernel: 
3.0.0-14-generic

#ASound: 
Advanced Linux Sound Architecture Driver Version 1.0.24.

#Codec: 
==> /proc/asound/card0/codec#0 <==
Codec: Realtek ALC880

==> /proc/asound/card0/codec#1 <==
Codec: Conexant ID 2bfa


#Alsa Info at: 
[http://www.alsa-project.org/db/?f=7590b06a4745e0bdea6473579541253eb29d79bd](http://www.alsa-project.org/db/?f=7590b06a4745e0bdea6473579541253eb29d79bd)


(I also asked this at ask ubuntu: [http://askubuntu.com/questions/91539/no-audio-from-jack-on-asus-pro60v](http://askubuntu.com/questions/91539/no-audio-from-jack-on-asus-pro60v))

---

### Post by lidex on 2011-12-31
> **utillich said:**
> Hi 

I recently installed Ubuntu 11.10 on a friends old Laptop (ASUS PRO60V). Everything is running great except I cant get any audio output from the output jack.

Audio works fine through the internal speakers, but once I plug in speakers or headphones into the jack (combined SPDIF & Analog) the internal speakers are muted but there is no output on the external speakers. My guess is it is trying to output through SPDIF instead of analog...


I tried different outputs settings in the sound setting menu and also looked at alsa mixer, but couldn't get it to work. 

Any help would be much apreciated!

#Kernel: 
3.0.0-14-generic

#ASound: 
Advanced Linux Sound Architecture Driver Version 1.0.24.

#Codec: 
==> /proc/asound/card0/codec#0 <==
Codec: Realtek ALC880

==> /proc/asound/card0/codec#1 <==
Codec: Conexant ID 2bfa


#Alsa Info at: 
[http://www.alsa-project.org/db/?f=7590b06a4745e0bdea6473579541253eb29d79bd](http://www.alsa-project.org/db/?f=7590b06a4745e0bdea6473579541253eb29d79bd)


(I also asked this at ask ubuntu: [http://askubuntu.com/questions/91539/no-audio-from-jack-on-asus-pro60v](http://askubuntu.com/questions/91539/no-audio-from-jack-on-asus-pro60v))

Try going into alsamixer and unmuting the line element:
```
Simple mixer control 'Line',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 65
  Mono:
  Front Left: [COLOR="Red"]Playback 0 [0%] [-35.00dB] [off][/COLOR]
  Front Right: [COLOR="Red"]Playback 0 [0%] [-35.00dB] [off][/COLOR]
```
You'll also need to raise the levels and perhaps even mute the IEC958 elements.

---

### Post by utillich on 2012-01-01
lidex, thank you for your help!

I raised line & cd to max and also tryed muting both IEC958 elements, but it still doesn't work.

([http://www.alsa-project.org/db/?f=4ceb896d6b3b4db2652e9412b29071f587d0cb3d](http://www.alsa-project.org/db/?f=4ceb896d6b3b4db2652e9412b29071f587d0cb3d))

If you have any other suggestion what I could try, I'd appreciate it!

---

### Post by lidex on 2012-01-01
> **utillich said:**
> lidex, thank you for your help!

I raised line & cd to max and also tryed muting both IEC958 elements, but it still doesn't work.

([http://www.alsa-project.org/db/?f=4ceb896d6b3b4db2652e9412b29071f587d0cb3d](http://www.alsa-project.org/db/?f=4ceb896d6b3b4db2652e9412b29071f587d0cb3d))

If you have any other suggestion what I could try, I'd appreciate it!

Its still muted:
```
Simple mixer control 'Line',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 65
  Mono:
  Front Left: Playback 65 [100%] [30.00dB] [COLOR="DarkRed"][off][/COLOR]
  Front Right: Playback 65 [100%] [30.00dB] [COLOR="DarkRed"][off][/COLOR]
```

Use the M key to unmute - should change from MM to 00

---

### Post by utillich on 2012-01-02
Thanks again for your help!

Sadly it is still not working... If you have any other ideas I would appreciate it.

[http://www.alsa-project.org/db/?f=4453e97899ebe07020e1ceb7317de991ad43ad3f](http://www.alsa-project.org/db/?f=4453e97899ebe07020e1ceb7317de991ad43ad3f)
(It was already unmuted, I must have uploaded the wrong file before)

---

### Post by lidex on 2012-01-03
Try this using a Terminal
```
echo "options snd-hda-intel model=z71v position_fix=1" | sudo tee -a /etc/modprobe.d/alsa-base.conf
``` **Reboot**

---

### Post by utillich on 2012-01-03
It worked!
Thank you very much, you rock!

If its fine with you I'll post the solution on Ask Ubuntu (linking to this thread), unless you have an account and want to post the solution yourself.

---

### Post by lidex on 2012-01-03
> **utillich said:**
> It worked!
Thank you very much, you rock!

If its fine with you I'll post the solution on Ask Ubuntu (linking to this thread), unless you have an account and want to post the solution yourself.

Go for it. Would help also to mark the thread solved - use 'thread tools' near the top.

---

