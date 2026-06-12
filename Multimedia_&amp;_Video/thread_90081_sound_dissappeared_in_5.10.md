---
title: "sound dissappeared in 5.10"
date: 2005-11-14
forum: Multimedia &amp; Video
---

### Post by tidemann on 2005-11-14
I lost the sound on my Dell Inspiron 8600 when I upgraded to Ubuntu 5.10. The sound card is detected, it just isn't working.

In System -> Preferences -> Sound, the checked value in "General" is "enable sound server startup" the default sound card is Intel 82801DB-ICH4. I have also tried to install several different sound daemons through SPM, but none work so far.

In System -> Preferences -> Multimedia Systems Selector, I have the default sink and source set to ESD. But when performing the test, no sound can be heard. The same applies to the other options; ALSA and OSS. Although nothing works... 

This is really a pain in the ass at the moment... I would really appreciate any help on this. Thank you!

---

### Post by endokrin on 2005-11-21
bump

I have the same sound card, same problem, did the how-to troubleshoot and no sounds still... help would be appreciated!

---

### Post by endokrin on 2005-11-21
bump...


anybody wanna help me get my sound working?

the speakers are definitely not on mute.
i went through the how-to checklist word for word.

still no sound!

---

### Post by Tiede on 2005-11-21
Do this and tell me what happens
```
killall esd
esd
```
If you here a bunch of twinkly sounds, I might be able to help

---

### Post by darkmatter on 2005-11-21
[quote=tidemann]the default sound card is Intel 82801DB-ICH4[/quote]

Do you have more than one? A cheap "fix" for sound problems is to disable the secondary card if you have one.

---

### Post by endokrin on 2005-11-22
Well I don't have the same setup as the original poster but he has the same card as me so I figured not to start a new thread.

I did the 

```

killall esd
esd

```

and nothing happened.

In case it matters this is on a Gateway M320 laptop.  Any gurus out that have a magic fix for my sound?? I hope so!
 ;)

---

### Post by Tiede on 2005-11-23
you mean NOTHING at all, no sound and no error? well, give me the output of this: ```
lsof /dev/snd/*
lsof /dev/dsp

``` and also give me this one, so i can know what is your soundcard ```
lspci
``` and if I know more about it.

---

### Post by tidemann on 2005-11-24
I didn't hear any twinkly sounds either.

```

fredrik@ubuntu:~$ lsof /dev/snd/*
lsof: WARNING: can't stat() ext3 file system /dev/.static/dev
      Output information may be incomplete.
COMMAND    PID    USER   FD   TYPE DEVICE SIZE NODE NAME
mixer_app 9169 fredrik   36u   CHR  116,0      7084 /dev/snd/controlC0

```

```

fredrik@ubuntu:~$ lsof /dev/dsp
lsof: WARNING: can't stat() ext3 file system /dev/.static/dev
      Output information may be incomplete.

```

```

fredrik@ubuntu:~$ lspci
0000:00:00.0 Host bridge: Intel Corp. 82855PM Processor to I/O Controller (rev 03)
0000:00:01.0 PCI bridge: Intel Corp. 82855PM Processor to AGP Controller (rev 03)
0000:00:1d.0 USB Controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
0000:00:1d.1 USB Controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
0000:00:1d.2 USB Controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
0000:00:1d.7 USB Controller: Intel Corp. 82801DB/DBM (ICH4/ICH4-M) USB 2.0 EHCI Controller (rev 01)
0000:00:1e.0 PCI bridge: Intel Corp. 82801 PCI Bridge (rev 81)
0000:00:1f.0 ISA bridge: Intel Corp. 82801DBM LPC Interface Controller (rev 01)
0000:00:1f.1 IDE interface: Intel Corp. 82801DBM (ICH4) Ultra ATA Storage Controller (rev 01)
0000:00:1f.5 Multimedia audio controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
0000:00:1f.6 Modem: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 01)
0000:01:00.0 VGA compatible controller: nVidia Corporation NV34M [GeForce FX Go 5200] (rev a1)
0000:02:00.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01)
0000:02:01.0 CardBus bridge: Texas Instruments PCI4510 PC card Cardbus Controller (rev 02)
0000:02:01.1 FireWire (IEEE 1394): Texas Instruments PCI4510 IEEE-1394 Controller
0000:02:03.0 Network controller: Intel Corp. PRO/Wireless 2200BG (rev 05)

```

Hope it helps!

---

### Post by endokrin on 2005-12-01
[QUOTE=Tiede]you mean NOTHING at all, no sound and no error? well, give me the output of this: ```
lsof /dev/snd/*
lsof /dev/dsp

``` and also give me this one, so i can know what is your soundcard ```
lspci
``` and if I know more about it.[/QUOTE]

Hey sorry for the delay, busy with the holiday and school!!!
anyways, no sound at all!  when i adjust the volume the bar moves as if it were adjusting, but there is no sound.  no music, no system sounds, no sounds on startup, nothing at all!

```
ryan@endokrin:~$ lsof /dev/snd*
lsof: WARNING: can't stat() ext3 file system /dev/.static/dev
      Output information may be incomplete.
ryan@endokrin:~$ lsof /dev/dsp
lsof: WARNING: can't stat() ext3 file system /dev/.static/dev
      Output information may be incomplete.

```

```

ryan@endokrin:~$ lspci
0000:00:00.0 Host bridge: Intel Corp. 82852/855GM Host Bridge (rev 02)
0000:00:00.1 System peripheral: Intel Corp. 855GM/GME GMCH Memory I/O Control Registers (rev 02)
0000:00:00.3 System peripheral: Intel Corp. 855GM/GME GMCH Configuration Process Registers (rev 02)
0000:00:02.0 VGA compatible controller: Intel Corp. 82852/855GM Integrated Graphics Device (rev 02)
0000:00:02.1 Display controller: Intel Corp. 82852/855GM Integrated Graphics Device (rev 02)
0000:00:1d.0 USB Controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
0000:00:1d.1 USB Controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
0000:00:1d.2 USB Controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 03)
0000:00:1d.7 USB Controller: Intel Corp. 82801DB/DBM (ICH4/ICH4-M) USB 2.0 EHCI Controller (rev 03)
0000:00:1e.0 PCI bridge: Intel Corp. 82801 PCI Bridge (rev 83)
0000:00:1f.0 ISA bridge: Intel Corp. 82801DBM LPC Interface Controller (rev 03)
0000:00:1f.1 IDE interface: Intel Corp. 82801DBM (ICH4) Ultra ATA Storage Controller (rev 03)
0000:00:1f.3 SMBus: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 03)
0000:00:1f.5 Multimedia audio controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
0000:00:1f.6 Modem: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)
0000:02:07.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev a9)
0000:02:07.1 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev a9)
0000:02:07.2 FireWire (IEEE 1394): Ricoh Co Ltd R5C552 IEEE 1394 Controller (rev 01)
0000:02:08.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
0000:02:09.0 Network controller: Intel Corp. PRO/Wireless 2200BG (rev 05)
ryan@endokrin:~$


```

and again, sorry for taking so long to get back.
and tidemann, sorry for busting into your thread but we have the same sound cards so i didn't want to make a whole new thread.. some places chop your head of for that!!

thanks for the help!

---

### Post by FaBi3ttO on 2005-12-01
I've had the same problem.
Searching in the forum I've found this post.
[http://www.ubuntuforums.org/showthread.php?t=87849&highlight=ich4]("http://www.ubuntuforums.org/showthread.php?t=87849&highlight=ich4")
I just tried to enable/disable the "external amplifier" in alsamixer and restarting the sound server...it worked!! :D 

Hope it helps.

---

### Post by endokrin on 2005-12-01
Oh, if it were only that simple!!

The external amplifier selection was OFF.. I turned it ON, restarted.. and nothing!
:(

Thank you for the link though.

---

### Post by endokrin on 2005-12-01
also:

```

ryan@endokrin:~$ lsmod | grep snd
snd_intel8x0           30144  2
snd_ac97_codec         72188  1 snd_intel8x0
snd_pcm_oss            46368  0
snd_mixer_oss          16128  2 snd_pcm_oss
snd_pcm                78344  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              21764  1 snd_pcm
snd                    48644  8 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9184  2 snd
snd_page_alloc         10120  2 snd_intel8x0,snd_pcm
ryan@endokrin:~$

```

if that helps any...

---

### Post by endokrin on 2005-12-03
just bumping....

---

### Post by kaaskop on 2005-12-03
My Dell Dimension 8400 had the same problem, I turned off my onboard sound card in the BIOS and then there was sound!

---

### Post by tidemann on 2005-12-04
[QUOTE=kaaskop]My Dell Dimension 8400 had the same problem, I turned off my onboard sound card in the BIOS and then there was sound![/QUOTE]

Can you please tell me how? I have no clue how to even enter BIOS. Not my area of expertise :P Thank you!

---

### Post by kaaskop on 2005-12-05
Sure!
Press F2 during boot
Onboard Devices
Integrated Audio
Enter
toggle to Off
Enter
escape
Make sure you save when you leave your BIOS

---

