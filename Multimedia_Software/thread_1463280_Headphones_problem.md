---
title: "Headphones problem"
date: 2010-04-26
forum: Multimedia Software
---

### Post by sigurnjak on 2010-04-26
Am i not looking hard enough , or answers are too obvious or it is just not possible   but for the life of me i can not figure out my headphones problem . 
I do not think i am asking too much from pulse audio . When i listen to do music , which sounds and plays just fine , sometimes i wish to switch to headphones , adjust the volume  , chill out . 
What happens is i loose sound at the speakers and nothing comes out from the headphones . I try changing output to analog headphones and nothing comes out and after changing back to analog output i get sound coming from both . 

Needles to say i am frustrated . 
Btw  i am trying front headphone output .

Anybody got any suggestions ???

---

### Post by lidex on 2010-04-26
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

### Post by sigurnjak on 2010-04-26
andrey@andrey-desktop:~$ uname -a
Linux andrey-desktop 2.6.31-21-generic #59-Ubuntu SMP Wed Mar 24 07:28:56 UTC 2010 i686 GNU/Linux
andrey@andrey-desktop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: VT1708S Analog [VT1708S Analog]
  Subdevices: 1/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
card 0: SB [HDA ATI SB], device 1: VT1708S Digital [VT1708S Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
andrey@andrey-desktop:~$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.22.1.
Compiled on Mar 25 2010 for kernel 2.6.31-21-generic (SMP).
andrey@andrey-desktop:~$ head -n 1 /proc/asound/card*/codec#*
Codec: VIA VT1708S

I hope this helps  . 
Thanks for taking your time  to help me out .

---

### Post by lidex on 2010-04-27
What is the make/model of this computer?

---

### Post by sigurnjak on 2010-04-28
I built it my self  . 
Asus  M2A74-AM mobo  in a coolemaster Elite case  with Zotac GT9400 DP  pci-e video card .  Wd 360 adfd  HD for  root  Seagate 250 GIG SATA for home and Vista on WD JB 250 .

---

### Post by lidex on 2010-04-28
Not a lot of solutions for that chipset out there. Try using gnome-alsamixer and if not installed use this command:
```
sudo apt-get install gnome-alsamixer
```

---

### Post by sigurnjak on 2010-04-28
Hi there Lidex ! I got Gnome-alsa mixer  . I was just hopeful  for something more automated . 
Thanks for your time . :)

---

