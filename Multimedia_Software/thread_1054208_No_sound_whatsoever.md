---
title: "No sound whatsoever"
date: 2009-01-29
forum: Multimedia Software
---

### Post by darkzeus85 on 2009-01-29
I have looked on the forums and tried everything but I still have no sound at all, no login/logout sounds no video and the problem that started it all no sound in internet flash videos. I had sound for the most part but I was trying to get sound for sites like youtube and followed a howto something about getting pulseaudio working.

I followed the posts completly as far as i know and now there is no sound at all.

I can post any info anyone needs just ask.

---

### Post by darkzeus85 on 2009-01-29
Please help

---

### Post by darkzeus85 on 2009-01-29
i have tried everything and looked at all relevant threads and tried their solutions nothing happens sound card is recognized. I followed the instructions on this howto [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578) and that is when everything stopped working posted my problem there and no response.

---

### Post by darkzeus85 on 2009-02-09
Any one please help I would love to have even some sound back

---

### Post by darkzeus85 on 2009-02-18
Please help I have no sound. I have looked on the forums and tried everything and still no luck at all. pulse audio (i believe it's pulse) says there is a sound stream and nothing in muted anywhere and the sound wheel on my laptop is turned all the way up still no sound through the speaker or headphone jack. all volume is turned all the way up. there is not even login or logout sounds even though they are turned on.

this all started when I followed directions from a how to fix pulse audio problems and after that I had no sound at all. Before that the reason I wanted to fix it was that there was no sound or bad sound in flash videos online.

If asked I can supply any info needed to further diagnose the problem. Please help my last thread in general help went unanswered for like a month even with me bumping it back up and numerous people looked at it.

---

### Post by mikewhatever on 2009-02-19
Which guide did you follow? Which part exactly?

---

### Post by darkzeus85 on 2009-02-20
I followed this how to [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578) 

the parts i used were part A and B and I did not use the 64bit instructions. I do not recall there being any errors during the install/fix. I also looked at appendix A and my problems comply with part c of that appendix. I posted a reply to that how to and there was no reply to my post.

---

### Post by darkzeus85 on 2009-02-20
I am currently watching the pulse audio volume meter and it is bouncing the way it should with the movie that is playing and when mute is used in the pulse audio volume control the meter gos blank the way it should. the volume wheel on the outside of my laptop is all the way up. and using headphones that I know work great are plugged in there is still no sound. Just thought that info might help.

---

### Post by darkzeus85 on 2009-02-22
Please someone actually help instead of blowing me off

---

### Post by darkzeus85 on 2009-03-05
bump

---

### Post by darkzeus85 on 2009-03-05
bump

---

### Post by bapoumba on 2009-03-05
Threads merged.

---

### Post by Dr.Suave on 2009-03-05
Try this: [http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

Also, people will be able to help if you post the outcome of these commands: [http://ubuntuforums.org/showthread.php?p=6628921](http://ubuntuforums.org/showthread.php?p=6628921)

I'm sorry it's so hard to get help for a soundless ubuntu on this forum, I'm having the problem too.

---

### Post by avrilrox on 2009-03-05
I used to have this problem until yesterday. You need to provide additional information, just like Suave said, if you want people to help you.

---

### Post by darkzeus85 on 2009-03-13
wow I actually lost faith that I was going to receive any help so I stopped checking this thread. 

First of all I want to thank you two for trying to help. here is the first bit of info. 

```
:~$ lspci
00:00.0 Host bridge: Intel Corporation 82855PM Processor to I/O Controller (rev 21)
00:01.0 PCI bridge: Intel Corporation 82855PM Processor to AGP Controller (rev 21)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation NV34M [GeForce FX Go5200 32M/64M] (rev a1)
02:05.0 Network controller: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection (rev 05)
02:08.0 Ethernet controller: Intel Corporation 82801DB PRO/100 VE (MOB) Ethernet Controller (rev 83)
02:0b.0 CardBus bridge: Toshiba America Info Systems ToPIC100 PCI to Cardbus Bridge with ZV Support (rev 33)
02:0d.0 System peripheral: Toshiba America Info Systems SD TypA Controller (rev 05)


:~$ lsusb
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


:~$ cat /proc/asound/cards
 0 [I82801DBICH4   ]: ICH4 - Intel 82801DB-ICH4
                      Intel 82801DB-ICH4 with AD1981B at irq 11


:~$ cat /proc/asound/modules 
 0 snd_intel8x0



:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 0: Intel ICH [Intel 82801DB-ICH4]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 4: Intel ICH - IEC958 [Intel 82801DB-ICH4 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0



:~$ arecord -l
**** List of CAPTURE Hardware Devices ****
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 0: Intel ICH [Intel 82801DB-ICH4]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 1: Intel ICH - MIC ADC [Intel 82801DB-ICH4 - MIC ADC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 2: Intel ICH - MIC2 ADC [Intel 82801DB-ICH4 - MIC2 ADC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 3: Intel ICH - ADC2 [Intel 82801DB-ICH4 - ADC2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


```

---

### Post by markbuntu on 2009-03-13
Well, if you can see the levels moving when playing something then try this.
In the pulseaudio volume control right click on a playing stream and choose move stream and move it to another output device. In the panel volume control make sure that everything is turned up and not muted and that any box labelled IEC958 is not checked. In system preferences sound make sure you have either alsa or pulseaudio selected for playback.

---

### Post by kfenton on 2009-03-13
Okay so, i have a similar problem... whereas music IS playing yet i still have no sound.. all preferences are set to pulseaudio, alsamixer levels cranked, everything seems as though it should be working as far as i can tell... but all i ever hear is the little 1 second drum bit on the login screen(sometimes)... something isn't right.. ive just got to grips with my effing video card and would love some sound to run on top of it! wouldn't mind a bit of assistance.. heres a bit of info for yous guys...

lspci
```

kyle@kyles-laptop:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc RS300 Host Bridge (rev 02)
00:01.0 PCI bridge: ATI Technologies Inc Radeon 9100 IGP AGP Bridge
00:13.0 USB Controller: ATI Technologies Inc OHCI USB Controller #1 (rev 01)
00:13.1 USB Controller: ATI Technologies Inc OHCI USB Controller #2 (rev 01)
00:13.2 USB Controller: ATI Technologies Inc EHCI USB Controller (rev 01)
00:14.0 SMBus: ATI Technologies Inc SMBus (rev 17)
00:14.1 IDE interface: ATI Technologies Inc Dual Channel Bus Master PCI IDE Controller
00:14.3 ISA bridge: ATI Technologies Inc Unknown device 434c
00:14.4 PCI bridge: ATI Technologies Inc IXP200 3COM 3C920B Ethernet Controller
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP150 AC'97 Audio Controller
00:14.6 Modem: ATI Technologies Inc IXP AC'97 Modem (rev 01)
01:05.0 VGA compatible controller: ATI Technologies Inc RS300M AGP [Radeon Mobility 9100IGP]
02:02.0 Ethernet controller: Atheros Communications Inc. AR5212/AR5213 Multiprotocol MAC/baseband processor (rev 01)
02:03.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:04.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)
03:00.0 USB Controller: NEC Corporation USB (rev 43)
03:00.1 USB Controller: NEC Corporation USB (rev 43)
03:00.2 USB Controller: NEC Corporation USB 2.0 (rev 04)
kyle@kyles-laptop:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc RS300 Host Bridge (rev 02)
00:01.0 PCI bridge: ATI Technologies Inc Radeon 9100 IGP AGP Bridge
00:13.0 USB Controller: ATI Technologies Inc OHCI USB Controller #1 (rev 01)
00:13.1 USB Controller: ATI Technologies Inc OHCI USB Controller #2 (rev 01)
00:13.2 USB Controller: ATI Technologies Inc EHCI USB Controller (rev 01)
00:14.0 SMBus: ATI Technologies Inc SMBus (rev 17)
00:14.1 IDE interface: ATI Technologies Inc Dual Channel Bus Master PCI IDE Controller
00:14.3 ISA bridge: ATI Technologies Inc Unknown device 434c
00:14.4 PCI bridge: ATI Technologies Inc IXP200 3COM 3C920B Ethernet Controller
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP150 AC'97 Audio Controller
00:14.6 Modem: ATI Technologies Inc IXP AC'97 Modem (rev 01)
01:05.0 VGA compatible controller: ATI Technologies Inc RS300M AGP [Radeon Mobility 9100IGP]
02:02.0 Ethernet controller: Atheros Communications Inc. AR5212/AR5213 Multiprotocol MAC/baseband processor (rev 01)
02:03.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:04.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)
03:00.0 USB Controller: NEC Corporation USB (rev 43)
03:00.1 USB Controller: NEC Corporation USB (rev 43)
03:00.2 USB Controller: NEC Corporation USB 2.0 (rev 04)
```

lsusb

```
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 002: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 059f:1018 LaCie, Ltd 
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
```

cat /proc/asound/cards

```
kyle@kyles-laptop:~$ cat /proc/asound/cards
 0 [IXP            ]: ATIIXP - ATI IXP
                      ATI IXP rev 0 with ALC202 at 0xd0004400, irq 17
 1 [Modem          ]: ATIIXP-MODEM - ATI IXP Modem
                      ATI IXP Modem rev 1 at 0xd0004800, irq 17

```

cat /proc/asound/modules

```
kyle@kyles-laptop:~$ cat /proc/asound/modules
 0 snd_atiixp
 1 snd_atiixp_modem

```


aplay -l

```
**** List of PLAYBACK Hardware Devices ****
card 0: IXP [ATI IXP], device 0: ATI IXP AC97 [ATI IXP AC97]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 1: Modem [ATI IXP Modem], device 0: ATI IXP MC97 [ATI IXP MC97]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```


arecord -l

```
**** List of CAPTURE Hardware Devices **help**
card 0: IXP [ATI IXP], device 0: ATI IXP AC97 [ATI IXP AC97]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Modem [ATI IXP Modem], device 0: ATI IXP MC97 [ATI IXP MC97]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

lots of gibberish to me... hope someone can help me out!

---

### Post by darkzeus85 on 2009-03-15
@ markbuntu 

I did as you said and it did not work as far as changing output devices, I could not find any IEC958 checkbox. any other ideas? because I have been fresh out for a long time.

---

### Post by red13 on 2009-03-15
Try going system>preference>sound and test out the sound options.
For example scroll through the options for sound events and music and movies test each one. I'll wait for reply to continue not sure if I can help but I will give it a shot.

---

### Post by red13 on 2009-03-15
Also try this post  [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)
I have messed with the sound system before and found that through my tweaking I disabled or removed some key components.
Then goto [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683) and follow that.
I also use pulseaudio device chooser so I can switch sound devices for what current program I am using.

---

### Post by kfenton on 2009-03-15
got it working! only had to switch to fedora 9 haha... sorry ubuntu, but it just works better for me!

---

### Post by darkzeus85 on 2009-03-16
I have tried everything you suggested but to no avail. I think instead of wasting more time troubleshooting I am going to start fresh with a new install of 8.10 since my /home is on separate partitions.

What file system is recommended for 8.10? Since my brother convinced me to use Riserfs for / and ext3 for /home and I am not convinced RiserFS is the best for ubuntu's /

---

### Post by nelskurian on 2009-03-16
Checkout Below.It helped me very much.
Before that you must chek your system settings by all means.
1)System--administration--hardware drivers.Check your sound driver.
2)System--preference--sound.check all the defaults.
Do you got the volume control as muted in the menu panel, and got the 'no driver found' msg.

[http://ubuntuforums.org/showthread.php?t=205449]("http://ubuntuforums.org/showthread.php?t=205449")

 After all you take steps with hiphop.;)

---

