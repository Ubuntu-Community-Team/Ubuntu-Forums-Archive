---
title: "PCI Soundcard no audio"
date: 2009-10-22
forum: Multimedia Software
---

### Post by fiver22 on 2009-10-22
"lspci -v" lists my soundcard (C-Media Electronics Inc CM8738  ) but I'm still not able to get any sound out of it. Does the fact that it's listed there mean that the driver/module is installed? Any ideas why I can't get sound out of it? Sound off the motherboard does work. This is a PCI card. I have tried the 'Comprehensive Sound Problem Solution Guide'. Thanks.
--
OS:          Ubuntu 9.04 Jaunty Jackalope   
MOBO:        Intel D865GLC
BIOS:        Intel Corp. version BF86510A.86A.0077.P25.0508040031 (08/04/2005)
CPU:         Intel P4 2.8GHz
RAM:         1GiB (4X256MiB) DDR 320MHz
VIDEO:       ATI Radeon 9600 (RV350)
AUDIO:       Intel 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (trying to get C-Media Electronics Inc CM8738 to work)
NETWORK:     82547EI Gigabit Ethernet Controller 
HDD:         Seagate ST340810A 37GiB
             volume:0 EXT3 /dev/sda1 35GiB
                    1 Extended partition /dev/sda2 1608MiB
                    logicalvolume Linux swap /dev/sda5 1608MiB
CDROM:       HL-DT-ST DVD-RAM writer: cd-r cd-rw dvd dvd-r dvd-ram
USB STORAGE: Maxtor 114GiB 
             EXT3 /dev/sdb
             (/media/disk)

---

### Post by markbuntu on 2009-10-22
cat /proc/asound/cards
cat proc/asound/modules

Those commands will tell you if the card is found and the driver loaded. The c-media 8738 card should be no problem though. if it is not listed in those commands try it in another slot.

You should try this before doing anything drastic

[http://ubuntuforums.org/showthread.php?t=1130384](http://ubuntuforums.org/showthread.php?t=1130384)

---

### Post by fiver22 on 2009-10-22
Thanks for the response. Output:

:~$ cat /proc/asound/cards
 0 [ICH5           ]: ICH4 - Intel ICH5
                      Intel ICH5 with AD1981B at irq 17
 1 [CMI8738        ]: CMI8738 - C-Media CMI8738
                      C-Media CMI8738 (model 37) at 0xc800, irq 22
:~$ cat proc/asound/modules
cat: proc/asound/modules: No such file or directory

I take it that means that the slot is functioning but the driver isn't loaded? -If so I haven't a clue where to get it -or how to properly install it. The card is showing in my sound preferences -but there's no sound whatsoever when I try to use it. 
Thanks again. 


> **markbuntu said:**
> cat /proc/asound/cards
cat proc/asound/modules

Those commands will tell you if the card is found and the driver loaded. The c-media 8738 card should be no problem though. if it is not listed in those commands try it in another slot.

You should try this before doing anything drastic

[http://ubuntuforums.org/showthread.php?t=1130384](http://ubuntuforums.org/showthread.php?t=1130384)

---

### Post by fiver22 on 2009-10-25
Just an update: I think I'm abandoning this particular card. For whatever reason I just can't get it to function properly. 
I went so far as trying a fresh install of 9.04 as I had *some* success with trying the card  with the Live CD. 
The card would produce sound when I manually switched to OSS but then would not play online audio from Flash videos -more aggravating is that it wouldn't play audio from more than one application at a time, ex: If I was watching something in VLC and I wanted to pause it and listen to a tune through Rhythmbox I would have to close VLC to to hear any audio from the other app -simply pausing one app didn't work. I haven't a clue why it wouldn't work at all with ALSA or PulseAudio. 
It is an old card and I've found alot of people that have had difficulty with it. I've spent enough time with this and I think it's time to try a different card -as soon as I can spare the money.

---

