---
title: "Ubuntu 10.0.04 &amp; Logitech USB Headset: Very Low Volume"
date: 2010-05-21
forum: Multimedia Software
---

### Post by therabyte on 2010-05-21
It was working just fine with 9.10. After upgrading to 10.0.0.4 I' m getting a very low output, almost inaudible.

[HTML]
daniel@daniel-linux:~$ uname -a
Linux daniel-linux 2.6.32-22-generic #33-Ubuntu SMP Wed Apr 28 13:27:30 UTC 2010 i686 GNU/Linux
daniel@daniel-linux:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Headset [Logitech USB Headset], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: Audio [Samsung UC Audio], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
daniel@daniel-linux:~$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.21.
daniel@daniel-linux:~$ head -n 1 /proc/asound/card*/codec#*
Codec: Realtek ALC883
daniel@daniel-linux:~$ 

[/HTML] 

I' ll appreciate any help.

---

### Post by therabyte on 2010-05-22
Fixed this problem with alsamixer.

---

### Post by curiousmonk on 2010-05-28
I have the same issue - 10.04 + Logitech USB headset = low volume.  Could you explain how you fixed this using alsamixer?

---

### Post by curiousmonk on 2010-05-28
n/m... just had to hit F6 to change soundcard to Logitech USB Headset.  Speaker gain had been set to 0.

---

### Post by hantms on 2010-06-01
Excellent, this worked for me too.. Had this issue ever since I upgraded to Lucid.

Would be great if it could be fixed for other people in an update?   Almost nobody would expect to use a command line tool to fix this. (Or it could be added to the Sound control panel)

---

### Post by hachre on 2011-04-03
Thanks for posting this. I also have this problem in 11.04 b1... Incredible how such a bug can stay around for so long... I'm gonna report this now on launchpad...

I've reported it here:
[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/749856](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/749856)

---

### Post by anto27373 on 2011-07-19
thx solved for my Clear Chat Comfort USB on ubtu11.04

oh and for complete newbs:
find "terminal" in prog menu
type alsamixer
hit F6 and choose your USB headset
use the up arrow to crank it up to the top

---

### Post by rafaelbrandao on 2011-08-03
Thanksss!! That solved my problem with a cheap "3D Sound" USB adapter... those blue ones... lol

Excellent sound now in my netbook with a bad p2 output working in only one channel. Now I can enjoy my new Bose headphones!

Running Ubuntu Natty 11.04

Cheers from Brasil

---

### Post by Ashrael on 2011-09-08
Worked for my sennheiser pc36 on Natty! Great headphones for skype b.t.w. 

If you are looking for a howto on installing usb headsets or want you skype ringing sound to go through your speaker while your conversation goes to the headset? Then look at: 

[http://ubuntuforums.org/showthread.php?t=1839994&highlight=skype+ringing](http://ubuntuforums.org/showthread.php?t=1839994&highlight=skype+ringing)

Ubuntu: it really kicks the donkeys 4ss! :lolflag:

---

