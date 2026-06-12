---
title: "tv tuner / kworld pc150-u ... need help on getting it to work"
date: 2011-02-19
forum: Multimedia Software
---

### Post by jrob15 on 2011-02-19
I recently built a computer and put Ubuntu on it. Everything works except that I can not get the tv tuner going (Kworld pc150-u). I have tried doing everything I have seen on this forum and others that relates to other cards with the same chipset. I am stilling getting my board as "board: UNKNOWN/GENERIC"

here is the lspci -vv: 
04:05.0 Multimedia controller: Philips Semiconductors SAA7131/SAA7133/SAA7135 Video Broadcast Decoder (rev d1)
	Subsystem: KWorld Computer Co. Ltd. Device a134
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64 (21000ns min, 8000ns max)
	Interrupt: pin A routed to IRQ 20
	Region 0: Memory at febff800 (32-bit, non-prefetchable) [size=2K]
	Capabilities: <access denied>
	Kernel driver in use: saa7134
	Kernel modules: saa7134

here is dmesg | grep saa7133
[    9.267718] saa7133[0]: found at 0000:04:05.0, rev: 209, irq: 20, latency: 64, mmio: 0xfebff800
[    9.267725] saa7133[0]: subsystem: 17de:a134, board: UNKNOWN/GENERIC [card=0,autodetected]
[    9.267761] saa7133[0]: board init: gpio is 100000
[    9.460370] saa7133[0]: i2c eeprom 00: de 17 34 a1 54 20 1c 00 43 43 a9 1c 55 d2 b2 92
[    9.460377] saa7133[0]: i2c eeprom 10: ff ff ff ff ff 20 ff ff ff ff ff ff ff ff ff ff
[    9.460382] saa7133[0]: i2c eeprom 20: 01 40 01 03 03 ff 01 03 08 ff 01 7e ff ff ff ff
[    9.460387] saa7133[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    9.460392] saa7133[0]: i2c eeprom 40: ff 1c 00 c0 ff 1c 01 00 ff ff ff ff ff ff ff ff
[    9.460397] saa7133[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    9.460402] saa7133[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    9.460407] saa7133[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    9.460412] saa7133[0]: i2c eeprom 80: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    9.460417] saa7133[0]: i2c eeprom 90: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    9.460422] saa7133[0]: i2c eeprom a0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    9.460427] saa7133[0]: i2c eeprom b0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    9.460432] saa7133[0]: i2c eeprom c0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    9.460437] saa7133[0]: i2c eeprom d0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    9.460442] saa7133[0]: i2c eeprom e0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    9.460447] saa7133[0]: i2c eeprom f0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    9.461021] saa7133[0]: registered device video0 [v4l2]
[    9.461089] saa7133[0]: registered device vbi0
[    9.466365] saa7133[0]/alsa: saa7133[0] at 0xfebff800 irq 20 registered as card -2

here is dmesg | grep saa7134
[    9.267711] saa7134 0000:04:05.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    9.466331] saa7134 ALSA driver for DMA sound loaded

right now a lot of the stuff I am doing I don't understand 100%, any help would be greatly appreciated

if I can't get it to work, I am going to order a different one - suggestions of tuners that work in Ubuntu for both analog and digital are welcomed also

---

### Post by Laytos on 2011-07-20
I'm bumping this, because I have the exact same card and I'm having issues. Mainly with w_scan... it keeps telling me no suitable DVB card is found. I've tried specifying different cards when loading the module with modprobe, same error. 

I know the PC-110 needs firmware in addition to the right card being specified on modprobe. With that, I know the PC-110 firmware doesn't work with the PC-150 (since I'm getting the same error). I've tried other programs (Kaffeine, TV Time) both of them can't use video0 or don't get a signal from it. And since the card is being registered as video0 from the dmesg, this also tells me it's something to do with the driver/firmware. 

I think I'm going to try to extract the windows firmware for the PC-150 and see if I get anywhere with that.

Anyone else had any experience with this?

my dmesg and lspci are the same, btw

---

### Post by Laytos on 2011-07-20
Ok, well I've had some success with the Kworld PC-150U. I can say that it does work with Ubuntu, well the analog side so far. I used the Kworld PC-110 firmware, and specified card=65 when loading saa7134 through modprobe. Doing some digging I found [http://www.avsforum.com/avs-vb/showthread.php?t=863782](http://www.avsforum.com/avs-vb/showthread.php?t=863782) .
I used the mplayer test not just for channel=7, but also did 8 and 9. It worked on all of them and was able to give me analog video and audio. I am still looking for a scanning program, and I still need to set it up with MythTV, but I'm still going to put this one in the win column, since I now know that the card works with Linux. It is now just a matter of setting it up with MythTV...

---

### Post by Laytos on 2011-07-22
So, I figured I should give a quick update with this card. I was able to get the analog side working. I was able to get picture and sound on the OTA side. However, the ATSC side of things is a bit different. I wasn't ever able to get picture or sound. The end result that I was going for was to use the card with MythTV. Since Myth won't/can't use the analog side of the card (something about having to encode the video and audio stream), it depends on the digital or ATSC side. I tried as many things as I could find and Myth wouldn't ever record the cable feed. So, I'm going to get an HD STB, connect it to MythTV via firewire and use that. 

So, after playing with it for a few days I've found, you can watch TV using TV Time or mplayer. But to record, well, I wasn't able to get it to work. I just want MythTV to work, and for me, using firewire is much easier. Even if I do need to spend the $10 a month to get it from the cable company.

---

