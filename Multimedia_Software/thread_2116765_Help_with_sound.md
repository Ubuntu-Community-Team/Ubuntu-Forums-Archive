---
title: "Help with sound"
date: 2013-02-16
forum: Multimedia Software
---

### Post by francovilar on 2013-02-16
Hello. I'm a new user of Linux.

I  had alot of trouble adding sound to ubuntu but I did it, searching  lot's of forum and tutorials and I was certain that was by adding to  /etc/modprobe.d/alsa-base.conf these two lines:
alias snd-card-0 snd-hda-intel
options snd-hda-intel model=generic

I had to reinstall and I changed that file and don't get any sound. the first install, before changing that file I tried lots of stuff and I don't  remember all, it must have been something else.

I still have the files from old ubuntu on a disk (not bootable), can somebody tell me wich files should I look to get sound again?

I have integrated audio - Realtek ALC888.

---

### Post by Yellow Pasque on 2013-02-16
[https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

### Post by francovilar on 2013-02-17
> **Temüjin said:**
> [https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

[http://www.alsa-project.org/db/?f=510975b6e45968ca3b7794fcd413b91b0dd90b6e](http://www.alsa-project.org/db/?f=510975b6e45968ca3b7794fcd413b91b0dd90b6e)

I'm trying linux Mint because I've read that it comes with proprietary driver's but it doesn't fix my problem also...

I will reinstall Ubuntu and post the log, but do you have any idea?

thank you

---

### Post by mike acker on 2013-02-17
[IMG]http://ubuntuone.com/2XFn7ygpPzE5t5v6gnH9c1[/IMG]
Ubuntu Sound Control
accessed from System Settings / Sound

notes

1. make sure the proper device is selected. notice I have a CODEC as well as built in sound
2. make sure amp is connected to device you want to use lime green jack is stereo L-R
3. watch the output volume . mine like to reset itself to the on-board port and sets the audio codec to zero .  ( why doesn't software do what it's told ? ) .
4. press the sound test to check things out
5. check your playback software: som always play thru the default device; others allow you to select an output device .

---

### Post by francovilar on 2013-02-17
> **mike acker said:**
> [IMG]http://ubuntuone.com/2XFn7ygpPzE5t5v6gnH9c1[/IMG]
Ubuntu Sound Control
accessed from System Settings / Sound

notes

1. make sure the proper device is selected. notice I have a CODEC as well as built in sound
2. make sure amp is connected to device you want to use lime green jack is stereo L-R
3. watch the output volume . mine like to reset itself to the on-board port and sets the audio codec to zero .  ( why doesn't software do what it's told ? ) .
4. press the sound test to check things out
5. check your playback software: som always play thru the default device; others allow you to select an output device .

I only have a dummy output in sound control

---

### Post by mike acker on 2013-02-17
> **francovilar said:**
> I only have a dummy output in sound control

that be the problem

do you have a sound card or does your motherboard have sound jacks like this

[IMG]http://ubuntuone.com/79uiM6OEMqqUghW1YaBmth[/IMG]

if you don't have sound then for stereo i'd suggest a Bheringer UCA202 -- USB interface

---

### Post by francovilar on 2013-02-17
I don't have a sound card only onboard sound

---

### Post by mike acker on 2013-02-17
> **francovilar said:**
> I don't have a sound card only onboard sound

ok

then here is the dox to look at:

[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

start with
```

sudo aplay -l

```

that's a lowercase L not a 1

let's see if your system is finding the sound hardware

---

### Post by francovilar on 2013-02-18
Fixed. Thank you.
sudo aplay -l didn't detect any soundcard so I did two things, don't know what fixed:
1-From the soundTroubleshooting:
**Loading a working sound configuration**

 If  you can find someone with similar hardware as yours and has working  sound, you could take their settings and try them on your hardware. 

[LIST=1]
[*]Get a working /var/lib/alsa/asound.state from someone who has similar hardware
[*]Save it as /tmp/asound.state
[*]alsactl -F -f /tmp/asound.state restore
[/LIST]

2-Change the onboard audio on bios from "auto" to "on". If somebody have he same problem try this.

Thank you again.

---

