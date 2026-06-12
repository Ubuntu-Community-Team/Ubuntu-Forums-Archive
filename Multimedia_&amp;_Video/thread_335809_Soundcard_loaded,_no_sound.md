---
title: "Soundcard loaded, no sound"
date: 2007-01-10
forum: Multimedia &amp; Video
---

### Post by bergsore on 2007-01-10
I have been following the_[ comprehensive sound problems solutions guide](http://www.ubuntuforums.org/showthread.php?t=205449)_ and I have a strange problem.  Everything looks like it should work... but it doesn't.

Info:
Toshiba Satellite laptop
Ubuntu 6.10 (sound did not work in Breezy either)
Intel I82801CAICH3 (soundcard)
snd-intel8x0 (driver)

**soren@ANGER:~$ aplay -l**
**** List of PLAYBACK Hardware Devices ****
card 0: I82801CAICH3 [Intel 82801CA-ICH3], device 0: Intel ICH [Intel 82801CA-ICH3]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

**soren@ANGER:~$lspci -v**
. . .
00:1f.5 Multimedia audio controller: Intel Corporation 82801CA/CAM AC'97 Audio Controller (rev 02)
        Subsystem: Toshiba America Info Systems Unknown device ff00
        Flags: bus master, medium devsel, latency 0, IRQ 10
        I/O ports at 1c00 [size=256]
        I/O ports at 1840 [size=64]
. . .

**soren@ANGER:~$ lsmod | grep snd**
snd_intel8x0           34844  1 
snd_ac97_codec         97696  1 snd_intel8x0
snd_ac97_bus            3456  1 snd_ac97_codec
. . .



I tried re-installing the drivers but there was an error.

I am worried that it might be a hardware problem because I went to the BIOS and turned on "Enable system beep" which is supposed to beep on startup but it still doesn't.  If it is the hardware I'm in trouble because the laptop is about 4 years old and far out of warranty.  However, I belive I remember windows audio working before I installed Ubuntu last summer (this is a backup PC.)

Is there any point working on driver installs if step one was successful?

Am I using the right driver?

Do you know of any way other than a service station to see if hardware is the problem?

What do you suggest I do next?

Please let me know if I have left out any useful information, your comments and advice are greatly appreciated.

---

### Post by scrooge_74 on 2007-01-10
If you boot from a Live CD do you get sound?

A few people had a problem with somethings in ALSA mixer been in mute or very low sound

Check those

---

### Post by BARTIST on 2007-01-16
Hello everybody,

I do have the same sound card and I am having problems with it too.
It worked fine on windows, it worked fine on Ubuntu Dapper.

It worked a few days on Kubuntu Edgy, and suddenly it never worked again.
I have spent days on google to try how to fix it, but I had no success.

If you have any idea, please let us know.

Regards.

---

### Post by gravies on 2007-05-05
I too have this problem with the same card on a Toshiba Satellite 3000 514.  All the signs are that the card should be working but there is no sound and no amount of altering the mixers helps produce sound.  Let me know if you ever found a solution!

---

### Post by davidmcq on 2007-05-18
I spent over an hour struggling with this problem before I realised that the keyboard mute was on! Call me stupid if you like... it wouldn't be anything like as bad as the things I called myself :mad:

---

### Post by gravies on 2007-05-18
I too stumbled across a solution.  I installed the latest alsa drivers from the tar ball but that didn't seem to fix it.  Then I set alsa-mixer to run in r2.d and upon next boot I had sound.  It was quite a surprise as I was in a quiet zone of a train and everyone was rudely awaken by the Ubuntu noise!

---

