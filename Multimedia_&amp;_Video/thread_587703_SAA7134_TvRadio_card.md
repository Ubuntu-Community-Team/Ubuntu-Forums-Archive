---
title: "SAA7134 Tv/Radio card"
date: 2007-10-23
forum: Multimedia &amp; Video
---

### Post by prshah on 2007-10-23
Hello All,

I have Mercury EZ View TV Tuner card which runs the Philips SAA7130/SAA7134 chipset (verified both physically and thru lspci).

The card was not recognized ("Huh, no EEPROM?"-type error message) initially. After visiting the forums, I finally got it recognized using "modprobe saa7134 card=2 tuner=3". Now, dmesg|grep saa lists:

====start
[   51.572449] saa7130/34: v4l2 driver version 0.2.14 loaded
[   51.572524] saa7130[0]: found at 0000:04:00.0, rev: 1, irq: 23, latency: 32, mmio: 0x49001000
[   51.572531] saa7130[0]: subsystem: 1303:2001, board: UNKNOWN/GENERIC [card=0,autodetected]
[   51.572542] saa7130[0]: board init: gpio is 40000
[   51.708001] saa7130[0]: i2c eeprom 00: 03 13 01 20 08 20 1c 55 43 43 a9 1c 55 43 43 a9
[   51.708012] saa7130[0]: i2c eeprom 10: ff ff 00 00 ff ff ff ff ff ff ff ff ff ff ff ff
[   51.708021] saa7130[0]: i2c eeprom 20: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   51.708030] saa7130[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   51.708039] saa7130[0]: i2c eeprom 40: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   51.708048] saa7130[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   51.708057] saa7130[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   51.708065] saa7130[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   51.708166] saa7130[0]: registered device video1 [v4l2]
[   51.708198] saa7130[0]: registered device vbi0
[   51.806220] saa7134 ALSA driver for DMA sound loaded
[   51.806476] saa7130[0]/alsa: saa7130[0] at 0x49001000 irq 23 registered as card -2
[  323.469562] saa7134 ALSA driver for DMA sound unloaded
[  379.872492] saa7130/34: v4l2 driver version 0.2.14 loaded
[  379.875809] saa7130[0]: found at 0000:04:00.0, rev: 1, irq: 23, latency: 32, mmio: 0x49001000
[  379.875823] saa7130[0]: subsystem: 1303:2001, board: LifeView FlyVIDEO3000 [card=2,insmod option]
[  379.875844] saa7130[0]: board init: gpio is 40000
[  379.875850] saa7130[0]: there are different flyvideo cards with different tuners
[  379.875852] saa7130[0]: out there, you might have to use the tuner=<nr> insmod
[  379.875854] saa7130[0]: option to override the default value.
[  379.877198] input: saa7134 IR (LifeView FlyVIDEO30 as /class/input/input6
[  380.007435] saa7130[0]: i2c eeprom 00: 03 13 01 20 08 20 1c 55 43 43 a9 1c 55 43 43 a9
[  380.007460] saa7130[0]: i2c eeprom 10: ff ff 00 00 ff ff ff ff ff ff ff ff ff ff ff ff
[  380.007473] saa7130[0]: i2c eeprom 20: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[  380.007485] saa7130[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[  380.007498] saa7130[0]: i2c eeprom 40: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[  380.007519] saa7130[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[  380.007535] saa7130[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[  380.007550] saa7130[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[  380.040288] tuner 0-0060: chip found @ 0xc0 (saa7130[0])
[  380.047416] tuner 0-0061: chip found @ 0xc2 (saa7130[0])
[  380.052951] saa7130[0]: registered device video1 [v4l2]
[  380.055294] saa7130[0]: registered device vbi0
[  380.057046] saa7130[0]: registered device radio0
[  380.074014] saa7134 ALSA driver for DMA sound loaded
[  380.074464] saa7130[0]/alsa: saa7130[0] at 0x49001000 irq 23 registered as card -2
==== end

In short, it finds the tv card, radio, ir remote and creates the devices as well.

BUT: 

1) gnomeradio can find a "stereo" signal, but no sound. Used the mixer, shows three devices, played around with everything, set all sliders to max, cleared all mutes.
2) xawtv shows only a blank black screen with "???" in the title bar
3) The remote is created at /dev/input/event6; so I type in a terminal, "cat /dev/input/event6" and then press a button on the remote; I get a lot of weird characters and the terminal screws up, so I assume that it is receiving signals from the remote

conclusion: 

I am missing something simple; the card is recognised, devices activated, but no sound, video or remote.

Nothing wrong with the hardware; works fine in Windoze.

System config:
Intel Core2 Duo / Intel 945 GCNL(?) / 1024 RAM / Intel HiDef audio (sigmatel chipset).
Ubuntu 7.10 (Also didn't work in 6.??, 7.04)

Note: Not made any custom kernel, using Ubuntu stock kernel 
(uname -a) gives "Linux prs-desktop 2.6.22-14-generic #1 SMP Sun Oct 14 23:05:12 GMT 2007 i686 GNU/Linux"

Cheers, Pl advise if you need more info:
PRS
PS: Any pointers appreciated, thanks in advance

---

### Post by studo77 on 2007-11-01
hmm, you might have a look here.

[http://gentoo-wiki.com/HARDWARE_saa7134](http://gentoo-wiki.com/HARDWARE_saa7134)
Cardlist is in the top of page, tunerlist is some scrolls down


There is lists of cards and tuners, so you can choose one that might work.

But beware, even though you have a card from the list, it does not mean that the corresponding card number will be the best/working.

And the i2cScan options i never got any good from. So changed my /etc/modprobe.d/options to include
```
options saa7134 card=XX tuner=XX
```

If you know what the card is recognized as in Windoze, that might help.

Also make a file saa7134 containing:
sudo gedit /etc/modprobe.d/saa7134
```

options saa7134 card=XX tuner=XX video_nr=0 vbi_nr=0
install saa7134 /sbin/modprobe --ignore-install saa7134; /sbin/modprobe saa7134-alsa
options saa7134-alsa index=1
```

most of this is for sound, even though i have not a working passthrough, i use a cable.

Remember to replace the XXs

---

### Post by proffit on 2007-11-19
Hi,
I have TV tuner Wayjet WT-853TF with chipset Philips SAA713X. It works fine in XP, but I can't watch TV in my Ubuntu Gutsy. I've TVtime installed and when I type ```
tvtime-scanner
``` in terminal I get this ```
No tuner found on input 0.  If you have a tuner, please select a different input using --input=<num>.
```.
Then I type ```
lshw
``` and after that I get this
```
*-multimedia
             description: Multimedia controller
             product: SAA7133/SAA7135 Video Broadcast Decoder
             vendor: Philips Semiconductors
             physical id: 6
             bus info: pci@0000:05:06.0
             version: d0
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=saa7134 latency=32 maxlatency=38 mingnt=15 module=saa7134
```
```
dmesg
``` report me this
```
[   47.807697] saa7130/34: v4l2 driver version 0.2.14 loaded
[   47.808017] ACPI: PCI Interrupt Link [APC1] enabled at IRQ 16
[   47.808025] ACPI: PCI Interrupt 0000:05:06.0[A] -> Link [APC1] -> GSI 16 (level, low) -> IRQ 21
[   47.808033] saa7133[0]: found at 0000:05:06.0, rev: 208, irq: 21, latency: 32, mmio: 0xd1001000
[   47.808039] saa7133[0]: subsystem: 1131:0000, board: UNKNOWN/GENERIC [card=0,autodetected]
[   47.808046] saa7133[0]: board init: gpio is 40
[   47.912408] saa7133[0]: Huh, no eeprom present (err=-5)?
[   47.912653] saa7133[0]: registered device video0 [v4l2]
[   47.912676] saa7133[0]: registered device vbi0
[   47.958529] parport_pc 00:09: reported by Plug and Play ACPI
[   47.958574] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   48.128815] Linux agpgart interface v0.102 (c) Dave Jones
[   48.159566] ACPI: PCI Interrupt Link [APCJ] enabled at IRQ 22
[   48.159571] ACPI: PCI Interrupt 0000:00:04.0[A] -> Link [APCJ] -> GSI 22 (level, low) -> IRQ 17
[   48.159589] PCI: Setting latency timer of device 0000:00:04.0 to 64
[   48.174005] saa7134 ALSA driver for DMA sound loaded
[   48.174030] saa7133[0]/alsa: saa7133[0] at 0xd1001000 irq 21 registered as card -2
```
I try ```
modprobe -v saa7134 i2c_scan=1
```
but the result is again
```
Reading configuration from /etc/tvtime/tvtime.xml
Reading configuration from /home/mecho/.tvtime/tvtime.xml
Scanning using TV standard PAL.
/home/mecho/.tvtime/stationlist.xml: No existing PAL station list "Custom".

    No tuner found on input 0.  If you have a tuner, please
    select a different input using --input=<num>.
```
Guys, I'm novice to Linux. Pls help me setup my tv-tuner step by step if possible:(
Thanks in advance

---

### Post by s.victor on 2007-11-19
In Terminal type:
```
sudo gedit /etc/modprobe.d/options
```

Enter your password.

Then add the following line to the bottom of the file:
```
options saa7134 card=81 tuner=54
```

Restart the computer. Then in Terminal type:
```
tvtime-scanner
```

You should be able to tune channels.

---

### Post by proffit on 2007-11-19
Thanks s.victor:) Now I'm working and when I go back home I'll try this
Regards

---

### Post by proffit on 2007-11-19
I have tune the channels, but haven't sound and remote control didn't work:(

---

### Post by s.victor on 2007-11-19
With that configuration I have both sound and picture working. Try if you have the sound working in some other TV program. Maybe you can do a fresh install.

For the remote control you have to install and configure "lirc", which is a bit complicated.

P.S. And by the way, I know it sounds stupid, but check if the sound in tvtime is increased with the left/right arrow keys (because I think it is set to 0 by default).

---

