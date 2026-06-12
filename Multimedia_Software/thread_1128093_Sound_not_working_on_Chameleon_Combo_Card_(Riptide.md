---
title: "Sound not working on Chameleon Combo Card (Riptide)"
date: 2009-04-17
forum: Multimedia Software
---

### Post by Jaguarandine on 2009-04-17
Hi, this is a repost of my problem in another thread [here]("http://ubuntuforums.org/showthread.php?t=1087229"). I figured this is a more appropriate forum. 

My system is a [HP Pavilion 8760c desktop]("http://h10025.www1.hp.com/ewfrf/wc/document?docname=bph05813&cc=us&lc=en&dlc=en&product=59299") running the same Rockwell Chameleon Combo Card as the OP. I've made significant changes to my system since the last time I replied:

[LIST=1]
[*] I updated the BIOS to 2.02 (latest version). 

[*] Reverted ALSA drivers to the Ubuntu defaults using the "Refreshing/Reinstalling the drivers" section of the [SoundTroubeshooting]("https://help.ubuntu.com/community/SoundTroubleshooting?action=fullsearch&context=180&value=linkto%3A%22SoundTroubleshooting%22") guide. I then manually loaded the riptide module using ```
sudo modprobe snd-riptide
``` as per the guide's instructions.

[*] Installed new version of ALSA via the [ALSA upgrade Script]("http://ubuntuforums.org/showthread.php?p=6589810#post6589810").

[*] I upgraded the memory from 256MB to 1.1GB of RAM. But alas, I did not get the OP's magical results, and I still have no sound.
[/LIST]

Here's my system info:
```
marcus@marcus-desktop:~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. VT82C693A/694x [Apollo PRO133x] (rev c4)
00:01.0 PCI bridge: VIA Technologies, Inc. VT82C598/694x [Apollo MVP3/Pro133x AGP]
00:04.0 ISA bridge: VIA Technologies, Inc. VT82C596 ISA [Mobile South] (rev 23)
00:04.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 10)
00:04.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 11)
00:04.3 Host bridge: VIA Technologies, Inc. VT82C596 Power Management (rev 30)
00:0a.0 Ethernet controller: Accton Technology Corporation SMC2-1211TX (rev 10)
00:0b.0 Multimedia audio controller: Rockwell International Unknown device 4310
00:0b.1 Communication controller: Rockwell International Riptide HSF 56k PCI Modem
00:0b.2 Input device controller: Rockwell International Unknown device 4312
00:0c.0 Ethernet controller: Atheros Communications Inc. AR5212/AR5213 Multiprotocol MAC/baseband processor (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation NV6 [Vanta/Vanta LT] (rev 15)
```
```

marcus@marcus-desktop:~$ lsusb
Bus 001 Device 002: ID 058f:9254 Alcor Micro Corp. Hub
Bus 001 Device 001: ID 0000:0000
```
```

marcus@marcus-desktop:~$ cat /proc/asound/cards
 0 [Riptide        ]: RIPTIDE - Riptide
                      Riptide at 0xb800, irq 11 mpu 0x330 opl3 0x388 gameport 0x200
```
```

marcus@marcus-desktop:~$ cat /proc/asound/modules
 0 snd_riptide
```
```

marcus@marcus-desktop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Riptide [Riptide], device 0: RIPTIDE [RIPTIDE]
  Subdevices: 3/3
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
```
```

marcus@marcus-desktop:~$ arecord -l
**** List of CAPTURE Hardware Devices ****
card 0: Riptide [Riptide], device 0: RIPTIDE [RIPTIDE]
  Subdevices: 1/1
  Subdevice #0: subdevice #0 
```

At this point I'm seriously thinking about switching to a better supported sound card. I've spent countless hours on this with much frustration and no results. The only thing keeping me from removing the sound card and smashing it to bits is that this experience may benefit other users and maybe the ALSA project. So, does anyone have any suggestions? I appreciate any help you can give. Thanks! ;)

---

### Post by MS_free on 2010-07-31
I might have the answer for you.
Sorry, Jaguarandine, it took quite awhile :)
A little history. Well, it all started when I got a really old computer hp pavilion 6653c. I decided to do a routine thing with it, namely, kill Windoze and install Ubuntu. Since it has only 128mb RAM, i wanted to give a try to fluxbox and lubuntu. Just to prove that Linux with a modern kernel can be fun on such archaic hardware, and, voila QED!

Things flowed flawlessly, except for the sound -no matter what I did. I even custom built two kernels (cross compiled on a faster 64bit machine -2hours, while on the host machine it took 16 whole hours!!!) I did this to get SMP turned off, since the riptide driver people from here [http://www.linuxant.com/drivers/riptide/index.php](http://www.linuxant.com/drivers/riptide/index.php) mentioned that it wouldn't work with CONFIG_SMP=y kernel option. However, that all was futile, even though, snd_riptide was loaded ... until I looked in the kern.log which and found this:

ul 28 23:17:04 ubuntu kernel: [   12.390143] RIPTIDE 0000:01:09.0: firmware: requesting riptide.hex
Jul 28 23:17:04 ubuntu kernel: [   12.445789] Riptide: Firmware not available -2
Jul 28 23:17:04 ubuntu kernel: [   12.446371] RIPTIDE: probe of 0000:01:09.0 failed with error -5

so the system could not find the firmare file for the module. This very file turned out to be riptide.hex. That I found in two places in the system, however not in the right one. I fter I put in the /lib/firmware/ directory the sound finally started to work.
Ok, here's what you can try: download , e.g., from [http://www.linuxant.com/drivers/riptide/downloads-license.php](http://www.linuxant.com/drivers/riptide/downloads-license.php) ,
untar and locate  riptide.hex there . Then copy it to /lib/firmware/ . Then, issue 
killall pulseaudio
sudo alsa force-reload
pulseaudio -D

Or simply reboot the machine

I hope it will work.
As a matter of fact, the best (or just good) quality is done without pulseaudio, or by using "mplayer -ao sdl"
Hopefully, it helps
good luck!

---

### Post by MS_free on 2010-07-31
'd like to  clarify correcting myself about the option "-ao sdl" given to mplayer to produce a good output. It actually turns out that two yet better options exist, such as "-ao alsa" and/or "-ao oss". The latter would be available if you installed alsa-oss-compat or something like that.
The difference is the cpu time which get 3 times lower with those options, although the quality does not seem to differ that much.

---

