---
title: "HVR-950 Setup Help For a Newbie; DESPERATE!!"
date: 2008-08-19
forum: Multimedia Software
---

### Post by Starbuck13 on 2008-08-19
Hi, I've got an HVR-950 USB tv-tuner. I'd like to use it to watch OTA digital broadcasts in Champaign, Il. I went thru this setup tutorial:

[http://u32.net/MythTV/WinTV-HVR-950/index.html](http://u32.net/MythTV/WinTV-HVR-950/index.html)

When I got to the part I scan for channels, and the watch some TV using mplayer to check that things work ok, I got nothing! 

The channels.conf.atsc is empty, and as I watched "scan" try to tune to different channels, I kept seeing "failed to tune" over and over. 

I've search a while online for a solution, but can't find a clear one and don't want to screw things up. I'd actually like to use Me-TV once the tuner is setup. 

Can anyone start me down the road to fixing this? Thanks in advance!

---

### Post by Erlander on 2008-08-19
How is your signal strength?

What are you using for an antenna?

---

### Post by Starbuck13 on 2008-08-19
I don't really know how to check signal strength, but it should be great---there are at least 2 stations withing 13 miles of my building.

For the antenna, I'm using an old big rooftop that got great analog reception and is pointing at those 2 tv stations in town.

---

### Post by virtualXTC on 2008-09-22
You need to populate that list to be able to watch tv.  Unfortunately, I'm in the same boat as far as getting that scan command to write a proper channels.conf.atsc
To get a signal strength readout use the command ```
femon
```

However, I'm not certain what the output means or that it has anything to do with it.  Erlander may, however, be able to tell that our cards aren't properly configured by our lack of signal.

Anyway, running femon gave me this:
> 
 status 00 | signal 0000 | snr 0000 | ber 00000000 | unc 00002871 |



I think the modules aren't loading properly.  When I run ```
dmesg | less
``` I get:
> [   29.020514] Table at 0x24, strings=0x1e82, 0x186a, 0x0000
[   29.028329] tveeprom 0-0050: Hauppauge model 65201, rev A1C0, serial# 2138522
[   29.028334] tveeprom 0-0050: tuner model is Xceive XC3028 (idx 120, type 71)
[   29.028337] tveeprom 0-0050: TV standards PAL(B/G) PAL(I) PAL(D/D1/K) ATSC/DVB Digital (eeprom 0xd4)
[   29.028340] tveeprom 0-0050: audio processor is None (idx 0)
[   29.028342] tveeprom 0-0050: has radio
[   29.064012] tuner' 0-0061: chip found @ 0xc2 (em28xx #0)
[   29.107429] xc2028 0-0061: creating new instance
[   29.107434] xc2028 0-0061: type set to XCeive xc2028/xc3028 tuner
[   29.921464] xc2028 0-0061: Error: firmware xc3028-v27.fw not found.
[   30.013249] tvp5150 0-005c: tvp5150am1 detected.
[   30.201782] em28xx #0: V4L2 device registered as /dev/video0 and /dev/vbi0
[   30.201786] em28xx #0: Found Hauppauge WinTV HVR 950
[   30.201810] usbcore: registered new interface driver em28xx
[   30.377727] xc2028 0-0061: attaching existing instance
[   30.377732] xc2028 0-0061: type set to XCeive xc2028/xc3028 tuner
[   30.377734] em28xx #0/2: xc3028 attached
[   30.377736] DVB: registering new adapter (em28xx #0)
[   30.377740] DVB: registering frontend 0 (LG Electronics LGDT3303 VSB/QAM Frontend)...
[   30.377944] Successfully loaded em28xx-dvb
[   30.377946] Em28xx: Initialized (Em28xx dvb Extension) extension


My guess is that it may have something to do with the "Error: firmware xc3028-v27.fw not found"

There is some sort of extract_xc3028.pl script you are suppose to run after installing video4linux.  It doesn't exist on my machine and I'm working on figuring out how to install / re-install it.

- virtualxtc

---

### Post by Erlander on 2008-09-22
Sorry, I'm all new at this too and to make matters worse in terms of being helpful I'm not in ATSC land.

However this page on the LinuxTV site gives some clues.

[http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-900]("http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-900")

Rob

---

