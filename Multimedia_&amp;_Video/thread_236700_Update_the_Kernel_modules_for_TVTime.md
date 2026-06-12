---
title: "Update the Kernel modules for TVTime"
date: 2006-08-15
forum: Multimedia &amp; Video
---

### Post by derby007 on 2006-08-15
Q. How do i update the Kernel modules to change the TV card type, ie. i've used : modprobe saa7134 card=2, etc.
But.... after i do a 'modprobe ...' & then i do 'dmesg' I don't see a change in the o/p, the card still reads 'autodetected'.
Is there another command that i should be doing, like 'rmmod' etc. Pls help as i am getting a black screen but no pic.
I also see i don't have a 'tuner' loaded in 'dmesg', as i have seen on other posts.

Note: see below for: ~ 'dmesg', ~ 'lspci -v' &  ~ modules file (relevant bits).
>> i also noted that the irq is different in 'dmesg' & lspci, ie. 217 versus 201 !!!!

**************

#dmesg :>

[4294689.446000] saa7130[0]: found at 0000:01:00.0, rev: 1, irq: 217, latency: 64, mmio: 0xfeafec00
[4294689.446000] saa7130[0]: subsystem: 18d0:2100, board: UNKNOWN/GENERIC [card=0,autodetected]
[4294689.446000] saa7130[0]: board init: gpio is 38000
[4294689.829000] saa7130[0]: i2c eeprom 00: d0 18 00 21 10 28 ff ff ff ff ff ff ff ff ff ff
[4294689.829000] saa7130[0]: i2c eeprom 10: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[4294689.829000] saa7130[0]: i2c eeprom 20: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[4294689.829000] saa7130[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[4294689.829000] saa7130[0]: i2c eeprom 40: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[4294689.829000] saa7130[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[4294689.829000] saa7130[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[4294689.829000] saa7130[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[4294689.829000] saa7130[0]: registered device video0 [v4l2]
[4294689.829000] saa7130[0]: registered device vbi0
[4294689.845000] saa7134 ALSA driver for DMA sound loaded
[4294689.845000] saa7130[0]/alsa: saa7130[0] at 0xfeafec00 irq 217 registered as card -1
**************

#lspci -v :>

0000:01:00.0 Multimedia controller: Philips Semiconductors SAA7130 Video Broadcast Decoder (rev 01)
Subsystem: Unknown device 18d0:2100
Flags: bus master, medium devsel, latency 64, IRQ 201
Memory at feafec00 (32-bit, non-prefetchable) [size=1K]
Capabilities: [40] Power Management version 1

**************

Modules file:

....
video 16260 0 - Live 0xe0ac4000
....
snd_intel8x0 33692 0 - Live 0xe0a77000
snd_ac97_codec 92704 1 snd_intel8x0, Live 0xe0ad7000
snd_ac97_bus 2304 1 snd_ac97_codec, Live 0xe0911000
snd_pcm_oss 53664 0 - Live 0xe0aaa000
snd_mixer_oss 18688 1 snd_pcm_oss, Live 0xe0a71000
saa7134_alsa 13408 1 - Live 0xe0a47000
..
snd_pcm 89864 4 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,saa7134_alsa, Live 0xe0a82000
snd_timer 25220 1 snd_pcm, Live 0xe0a5f000
e100 40580 0 - Live 0xe0a54000
serio_raw 7300 0 - Live 0xe0a44000
snd 55268 9 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,saa7134_alsa,snd_pcm,snd_timer, Live 0xe0a17000
soundcore 10208 1 snd, Live 0xe097c000
snd_page_alloc 10632 2 snd_intel8x0,snd_pcm, Live 0xe0906000
...
saa7134 115936 1 saa7134_alsa, Live 0xe0a26000
video_buf 22148 2 saa7134_alsa,saa7134, Live 0xe0975000
v4l2_common 6016 1 saa7134, Live 0xe0957000
v4l1_compat 14468 1 saa7134, Live 0xe0968000
ir_kbd_i2c 8460 1 saa7134, Live 0xe0953000
i2c_core 21904 3 i2c_acpi_ec,saa7134,ir_kbd_i2c, Live 0xe095b000
ir_common 9988 2 saa7134,ir_kbd_i2c, Live 0xe094f000
videodev 9856 1 saa7134, Live 0xe090d000
...
pci_hotplug 29236 1 shpchp, Live 0xe08b2000
...
vga16fb 13704 1 - Live 0xe083f000
vgastate 10368 1 vga16fb, Live 0xe0827000
...

---

### Post by derby007 on 2006-08-16
:p 
Fixed : ....some days it just happens. (after some blood, sweat, tears, no fingernails, frustrated wives, etc)
It all clicked last nite, it was all my fault with bad commands in the 1st place, it wasn't the fecin Ubuntu....

1st:  open /.tvtime/tvtime.xml & change 'V4L2' line from '0' > '2'  
    (this part may or may not be needed, i'll check again tonite)
2nd:  rmmod saa7134-alsa  
    (remove sound 1st)
3rd:  rmmod saa7134
4th:  modprobe saa7134 card=3 tuner=2
5th:  modprobe saa7134-alsa   
    ( -v : verbose option can be used on any of these to give a debug/description o/p)
6th:  dmesg
    ( see o/p below: look for added * lines)
    ( I set my Mercury 7130 card to card 3, from reading other posts; tuner is 2; there are lists for these )
7th:  run 'tvtime-scanner' from /etc/bin/ in a Terminal (may need 'sudo' aswell)
8th:  this runs the scanner: from 44MHz >> 958MHz in ~ 1MHz per sec intervals, have a cup of tea/guinness !
9th:  channels are saved, see below:
10th: run 'tvtime', window comes up with blue screen, ie. no signal
11th: 'right-click' and go thru menus to auto-scan, this shoud find ure channels
12th: Note: if there is an error running 'tvtime' at the prompt or selecting shortcut in 'Applications',
> run 'tvtime --inputwidth=400' at the prompt, as there could be an error with higher resolutions.
Reset this in 'menus' in Tvtime.

Now I must fix the sound (see 'card -1' below; & get it to load on 'boot-up'...... back to the Guinness....  :tongue: 

~~~~   solution o/p : ~~~~
saa7134 ALSA driver for DMA sound unloaded
saa7130/34: v4l2 driver version 0.2.14 loaded
ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 21 (level, low) -> IRQ 209
saa7130[0]: found at 0000:01:00.0, rev: 1, irq: 209, latency: 64, mmio: 0xfeafec00
*saa7130[0]: subsystem: 18d0:2100, board: LifeView FlyVIDEO2000 [card=3,insmod option]
saa7130[0]: board init: gpio is 38000
saa7130[0]: there are different flyvideo cards with different tuners
saa7130[0]: out there, you might have to use the tuner=<nr> insmod
saa7130[0]: option to override the default value.
*input: saa7134 IR (LifeView FlyVIDEO20 as /class/input/input3
saa7130[0]: i2c eeprom 00: d0 18 00 21 10 28 ff ff ff ff ff ff ff ff ff ff
saa7130[0]: i2c eeprom 10: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
saa7130[0]: i2c eeprom 20: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
saa7130[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
saa7130[0]: i2c eeprom 40: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
saa7130[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
saa7130[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
saa7130[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
*tuner 0-0061: chip found @ 0xc2 (saa7130[0])
*tuner 0-0061: type set to 37 (LG PAL (newer TAPC series))
saa7130[0]: registered device video0 [v4l2]
saa7130[0]: registered device vbio
*saa7130[0]: registered device radio0
saa7134 ALSA driver for DMA sound loaded
saa7130[0]/alsa: saa7130[0] at 0xfeafec00 irq 209 registered as card -1


:/etc/tvtime# tvtime-scanner
Reading configuration from /etc/tvtime/tvtime.xml
Reading configuration from /root/.tvtime/tvtime.xml
Scanning using TV standard PAL.
/root/.tvtime/stationlist.xml: No existing PAL station list "Custom".
Scanning from  44.00 MHz to 958.00 MHz.
Found a channel at 519.00 MHz (518.50 - 519.25 MHz), adding to channel list.
Found a channel at 841.75 MHz (841.50 - 841.75 MHz), adding to channel list.
Found a channel at 847.25 MHz (846.25 - 848.25 MHz), adding to channel list.

---

