---
title: "Fiesty &amp; DVB-T problem!"
date: 2007-08-19
forum: Multimedia &amp; Video
---

### Post by Jose Catre-Vandis on 2007-08-19
I currently run Edgy Eft and my hybrid dvb analog tv card works beautifully, giving clear uncorrputed digital viewing on all freeview channels. I am about 40 miles from the transmitter which works best for me (oddly, the nearest 10 miles away does not give such good reception). I have an ASUS P7131 hybrid card, which uses the Philips Semiconductor and SAA7134 modules.

On upgrading to Fiesty (having safely backed up my edgy installation using part image) I find that although the card is recognised and the modules load, it fails to scan for or tune to dvb channels on the same transmitter/settings as before. ( I had to edit the tvtime.xml file to get analog tv going again, changing from /dev/video to /dev/video0, so analog is not a problem). I also get this problem with a clean install of Fiesty on the same machine, and again with an install of Linux Mint. I have tried mplayer and kaffiene to get this working so it is not an application thing.

Something has changed inside the kernel, but I do not know where to start looking. Can anyone shed any light on what has happened to the v4l-dvb modules that might be causing this, in the shift from Edgy to Fiesty?

---

### Post by Jose Catre-Vandis on 2007-08-20
More info:

Please note this info refers to two separate installs in the same machine, with the same hardware, and loaded modules, so from what I can tell, everything is "the same" apart from the kernel version and ubuntu type.

Here is the tzap output from my working Edgy Eft installation:
```
tzap -r BBC1
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
tuning to 489833330 Hz
video pid 0x0258, audio pid 0x0259
status 01 | signal a2a2 | snr d9d9 | ber 0001fffe | unc 00000013 | 
status 1f | signal a2a2 | snr fefe | ber 00000000 | unc 00000010 | FE_HAS_LOCK
status 1f | signal a2a2 | snr fefe | ber 00000000 | unc 00000000 | FE_HAS_LOCK
status 1f | signal a2a2 | snr fefe | ber 00000000 | unc 00000000 | FE_HAS_LOCK
status 1f | signal a1a1 | snr fefe | ber 00000000 | unc 00000000 | FE_HAS_LOCK
status 1f | signal a1a1 | snr fefe | ber 00000000 | unc 00000000 | FE_HAS_LOCK
status 1f | signal a1a1 | snr fefe | ber 00000000 | unc 00000000 | FE_HAS_LOCK
status 1f | signal a1a1 | snr fefe | ber 00000000 | unc 00000000 | FE_HAS_LOCK
status 1f | signal a1a1 | snr fefe | ber 00000000 | unc 00000000 | FE_HAS_LOCK
status 1f | signal a1a1 | snr fefe | ber 00000000 | unc 00000000 | FE_HAS_LOCK
status 1f | signal a1a1 | snr fefe | ber 00000000 | unc 00000000 | FE_HAS_LOCK
status 1f | signal a1a1 | snr fefe | ber 00000000 | unc 00000000 | FE_HAS_LOCK
status 1f | signal a1a1 | snr fefe | ber 00000000 | unc 00000000 | FE_HAS_LOCK
status 1f | signal a1a1 | snr fefe | ber 00000000 | unc 00000000 | FE_HAS_LOCK
status 1f | signal a1a1 | snr fefe | ber 00000000 | unc 00000000 | FE_HAS_LOCK
status 1f | signal a1a1 | snr fefe | ber 00000000 | unc 00000000 | FE_HAS_LOCK
status 1f | signal a1a1 | snr fefe | ber 00000002 | unc 00000000 | FE_HAS_LOCK
status 1f | signal a1a1 | snr fefe | ber 00000000 | unc 00000000 | FE_HAS_LOCK
status 1f | signal a0a0 | snr fefe | ber 00000000 | unc 00000000 | FE_HAS_LOCK
status 1f | signal a1a1 | snr fefe | ber 00000000 | unc 00000000 | FE_HAS_LOCK
```
and here is the tzap output from my Fiesty installation:
```
tzap -r BBC1
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
tuning to 489833330 Hz
video pid 0x0258, audio pid 0x0259
status 00 | signal 0000 | snr 7373 | ber 0001fffe | unc 00000000 | 
status 00 | signal 0000 | snr 8383 | ber 0001fffe | unc ffffffff | 
status 1f | signal 0000 | snr 8b8b | ber 0001b844 | unc ffffffff | FE_HAS_LOCK
status 01 | signal 0000 | snr 6969 | ber 0001fffe | unc ffffffff | 
status 1f | signal 0000 | snr 8a8a | ber 0001c1e2 | unc ffffffff | FE_HAS_LOCK
status 1f | signal 0000 | snr a3a3 | ber 0001bf68 | unc ffffffff | FE_HAS_LOCK
status 00 | signal 0000 | snr 6262 | ber 0001fffe | unc 00000000 | 
status 1f | signal 0000 | snr 4141 | ber 0001cc40 | unc ffffffff | FE_HAS_LOCK
status 01 | signal 0000 | snr 8a8a | ber 0001fffe | unc ffffffff | 
status 1f | signal 0000 | snr 8181 | ber 0001b7ce | unc ffffffff | FE_HAS_LOCK
status 07 | signal 0000 | snr 7777 | ber 0001770e | unc ffffffff | 
status 01 | signal 0000 | snr 7d7d | ber 0001fffe | unc ffffffff | 
status 1f | signal 0000 | snr 8e8e | ber 0001b764 | unc ffffffff | FE_HAS_LOCK
status 1f | signal 0000 | snr 5050 | ber 0001966a | unc ffffffff | FE_HAS_LOCK
```

and this is the output mplayer gives on Fiesty:
```
mplayer dvb://BBC1
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.
dvb_streaming_read, attempt N. 6 failed with errno 0 when reading 1484 bytes
dvb_streaming_read, attempt N. 5 failed with errno 0 when reading 544 bytes
dvb_streaming_read, attempt N. 6 failed with errno 0 when reading 900 bytes
dvb_streaming_read, attempt N. 6 failed with errno 0 when reading 2008 bytes
dvb_streaming_read, attempt N. 5 failed with errno 0 when reading 1256 bytes
dvb_streaming_read, attempt N. 6 failed with errno 0 when reading 1800 bytes
dvb_streaming_read, attempt N. 5 failed with errno 0 when reading 1800 bytes
dvb_streaming_read, attempt N. 4 failed with errno 0 when reading 672 bytes
```

Also some edited output from /var/log/messages, showing the card and firmware loaded
```
saa7133[0]: found at 0000:01:06.0, rev: 208, irq: 201, latency: 32, mmio: 0xe8000000
saa7133[0]: subsystem:1043:4857, board: ASUSTeK P7131 Dual [card=78,insmod option]
saa7133[0]: board init: gpio is 0
saa7133[0]: i2c eeprom 00:43 10 57 48 54 20 1c 00 43 43 a9 1c 55 d2 b2 92
saa7133[0]: i2c eeprom 10:00 01 20 00 ff 20 ff ff ff ff ff ff ff ff ff ff
saa7133[0]: i2c eeprom 20:01 40 01 02 03 01 01 03 08 ff 00 cb ff ff ff ff
saa7133[0]: i2c eeprom 30:ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
saa7133[0]: i2c eeprom 40:ff 21 00 c2 96 10 03 32 15 00 ff ff ff ff ff ff
saa7133[0]: i2c eeprom 50:ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
saa7133[0]: i2c eeprom 60:ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
saa7133[0]: i2c eeprom 70:ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
tuner 2-004b: chip found @0x96 (saa7133[0])
tuner 2-004b: setting tuner address to 61
tuner 2-004b: type set to tda8290+75a
saa7133[0]: registered device video0 [v4l2]
saa7133[0]: registered device vbi0
saa7133[0]: registered device radio0
saa7134 ALSA driver for DMA sound loaded
saa7133[0]/alsa: saa7133[0] at 0xe8000000 irq 201 registered as card -1
DVB: registering new adapter (saa7133[0]).
DVB: registering frontend 0 (Philips TDA10046H DVB-T)...
tda1004x: setting up plls for 48MHz sampling clock
tda1004x: found firmware revision 29 -- ok
```

---

### Post by Jose Catre-Vandis on 2007-08-20
We have a resolution, many thanks to Hermann Pitton, linux dvb guru.

With my particular card, the change up in kernels means it behaves in a different way. You have two antenna inputs at the back of the card, one for TV and one for FM radio. With the later Fiesty kernel, you need to plug the TV antenna into the FM radio input to get dvb working (this provides for FM radio reception too) and a second antenna is needed for analog TV in the TV input. (This works with a splitter off one antenna to the two inputs both for the Edgy and Fiesty kernels). So all in all pretty well made up and good to go for the upgrade permanently. Note that at first, the dvb card may refuse to tune to all channels, or demonstrate poor reception, don't know why. Following a hard reboot (perhaps a couple of times) or doing that turn off and walk away for half an hour! thing, all the channels returned crystal clear. Also device names appear to change on my machine. /dev/video changed to /dev/video0 and /dev/radio to /dev/radio0.

Note: before trying to change the connections around, switch off your PC, otherwise you  can bork your CMOS/BIOS. I did, but resetting the CMOS by switching the pins sorted this out. (scary moments when your PC doesn't even get to POST!)

Hermann has offered up some edits and a patch for the v4l-dvb files, but as this cables switching and splitting seems to do the trick, I'm leaving well alone :)

---

