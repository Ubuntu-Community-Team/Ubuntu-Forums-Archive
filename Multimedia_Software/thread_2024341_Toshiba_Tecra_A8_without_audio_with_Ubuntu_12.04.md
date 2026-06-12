---
title: "Toshiba Tecra A8 without audio with Ubuntu 12.04"
date: 2012-07-13
forum: Multimedia Software
---

### Post by LubnaH on 2012-07-13
Hi all!

 My problem is this:
 No sound on a Toshiba Tecra A8 with this information about audio:
 [B]Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
0 [[/B] [B]Intel]: HDA-Intel - HDA Intel
HDA[/B] [B] Intel at 0x42080000 irq 44
Advanced Linux[/B] ** Sound Architecture Driver Version 1.0.24.**

 I tried for weeks all the solutions that provide some forums and any of them have worked (reinstalling alsa, modifying the file alsa-base.conf on many ways, etc).

 The only solution that i found in some forums and I haven't tried is to install windows and from there up the volume controls and then reinstall Ubuntu on a partition. This "solution" seems a bad one for me, basically because it's more than 7 years that I only work with ubuntu and I don't know from where can I start with installing windows.

 If someone can help me I would be very grateful. I don't think on windows as a solution to solve a problem on linux, it would be almost as an exorcism to this poor Toshiba that on the rest of the things works perfectly.

 Thank you in advance, 
Salud!
 Lubna

---

### Post by Vakman on 2012-07-21
> **lidex said:**
> First. Check your levels in alsamixer.
```
 alsamixer 
```
Press F6 to select the correct soundcard.
Press F3 to show playback levels. F4 selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels.
Go to "System>Preferences>Sound" and make sure the correct soundcard is default.

Next. Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
cat /proc/asound/version
head -n 1 /proc/asound/card*/codec#*
```
Terminal="Applications->Accessories->Terminal"
Please post text output using code tags.

Not that I think I can help you but perhaps some others can if you also post the output of those. Through the help of the function button in Windows does appear to be a good solution if you had it installed, sadly.

---

### Post by LubnaH on 2012-07-31
Hey! Thank you very much for trying to help me. 

Here is the output of the commands you told me

pornoterrorista@pornoterrorista:~$ uname -a
Linux pornoterrorista 3.2.0-26-generic #41-Ubuntu SMP Thu Jun 14 16:26:01 UTC 2012 i686 i686 i386 GNU/Linux
pornoterrorista@pornoterrorista:~$ aplay -l
**** Lista de PLAYBACK dispositivos hardware ****
tarjeta 0: Intel [HDA Intel], dispositivo 0: ALC262 Analog [ALC262 Analog]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0
tarjeta 0: Intel [HDA Intel], dispositivo 6: Si3054 Modem [Si3054 Modem]
  Subdispositivos: 0/1
  Subdispositivo #0: subdevice #0
pornoterrorista@pornoterrorista:~$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.24.
pornoterrorista@pornoterrorista:~$ head -n 1 /proc/asound/card*/codec#*
==> /proc/asound/card0/codec#0 <==
Codec: Realtek ALC262

==> /proc/asound/card0/codec#1 <==
Codec: LSI Si3054


When I go to alsamixer all the level are up (but marking 00) except the "speaker", that is on 00 and there's not possibility of moving it up (or I don't know how to do it). 
I have the right card selected on alsamixer but on Ubuntu 12 System>Preferences>Sound there's no way to select the card, there's no option for it.

Thanks for your help, I would love to try to arrange this without privative software help!

Diana

---

