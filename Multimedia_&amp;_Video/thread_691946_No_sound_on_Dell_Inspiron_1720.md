---
title: "No sound on Dell Inspiron 1720"
date: 2008-02-09
forum: Multimedia &amp; Video
---

### Post by viralbus on 2008-02-09
I just got myself a new laptop, a Dell Inspiron 1720, and I've installed Gutsy on it.
Everything seems to work well (after resolving some problems with the wireless card), except for the sound.  It doesn't seem to be finding my sound card:
```
viralbus@helianthus:~$ cat /proc/asound/cards 
--- no soundcards ---
```Although lspci seems to see something:```
viralbus@helianthus:~$ lspci |grep -i audio
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
```Vista reports the sound card as a "SigmaTel High Definition Audio CODEC".
I've searched the Ubuntu Forums and googled for it, but I haven't been able to find anything useful.  Any ideas?

---

### Post by linuxwizard on 2008-02-09
Look over this I see your computer model listed.

[https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller](https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller)

---

### Post by xc3RnbFO8P on 2008-02-09
The easy way is to install Backports:

> sudo aptitude install linux-backports-modules-generic

---

### Post by viralbus on 2008-02-09
I first tried to follow instructions B and D on the page listed in the first reply.  This gave me a beep sound, but nothing else.
Installing backports worked, however!  I now have sound, although it sounds very quiet and muted.  Much better than no sound at all, though.
Thanks a million!

---

### Post by xc3RnbFO8P on 2008-02-09
What is the output of **amixer** in terminal?

---

### Post by bluefrog on 2008-02-15
use [http://linux.dell.com/files/ubuntu/linux-backports-modules-2.6.22-14-generic_2.6.22-14.50_i386.deb](http://linux.dell.com/files/ubuntu/linux-backports-modules-2.6.22-14-generic_2.6.22-14.50_i386.deb)
It should fix your problem as it did for my Inspiron 1720.
It will allow you to enable the integrated mic as well if you change input to digital in alsamixer afterwards.

James Dupin

---

### Post by zerotwooneone on 2008-05-01
The backports works to give you sound, given that you have Dell i1720 and 7.10. If you have trouble with volume check the usual source of problems: Hardware (obviously), software (check the volume applet, note that PCM might also need to be increased) and the alsa mixer as previously stated.

Luckily, 8.04 fixes the sound trouble. Now if I could get wireless N to work...

---

