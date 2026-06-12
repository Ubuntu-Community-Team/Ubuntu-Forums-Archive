---
title: "Model: Easy TV capture, Chipset:saa7130"
date: 2007-05-08
forum: Multimedia &amp; Video
---

### Post by dazer26 on 2007-05-08
So i'm trying to get my tvcard to work in linux.  As the title suggests the chipset on my tvcard is the saa7130.  The card is called "EasyTV Capture" (it was cheap).  My exact card can be seen here: [http://tekgems.com/Products/la-tv01.htm](http://tekgems.com/Products/la-tv01.htm)

I was wondering if anyone else has this card and what setting they used to get it to work.  When I do a dmsg it can't identify my card, and lists it as card=0 (unkown/generic).  
nothing at all happens when I use "/sbin/modprobe saa7134 i2c_scan=1" or "/sbin/modprobe saa7134 card=X".
The next time I dmsg, it still shows up as card=0.

lspci gives

00:00.0 Memory controller: nVidia Corporation CK804 Memory Controller (rev a3)
00:01.0 ISA bridge: nVidia Corporation CK804 ISA Bridge (rev a3)
00:01.1 SMBus: nVidia Corporation CK804 SMBus (rev a2)
00:02.0 USB Controller: nVidia Corporation CK804 USB Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation CK804 USB Controller (rev a3)
00:04.0 Multimedia audio controller: nVidia Corporation CK804 AC'97 Audio Contro                                                              ller (rev a2)
00:06.0 IDE interface: nVidia Corporation CK804 IDE (rev f2)
00:07.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
00:08.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
00:09.0 PCI bridge: nVidia Corporation CK804 PCI Bridge (rev a2)
00:0a.0 Bridge: nVidia Corporation CK804 Ethernet Controller (rev a3)
00:0b.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0c.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0d.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0e.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTra                                                              nsport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address                                                               Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Con                                                              troller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscella                                                              neous Control
01:08.0 Multimedia controller: Philips Semiconductors SAA7130 Video Broadcast De                                                              coder (rev 01)
05:00.0 VGA compatible controller: nVidia Corporation NV43 [GeForce 6600 GT] (re                                                              v a2)

i'm trying to use tvtime or mythtv to watch tv.  I seem to remember getting my card to work with TVtime about a year and a half ago using supersuse.  I can't remember what I did though :P

---

### Post by tmdowner on 2007-08-28
by following the instructions at [http://www.linuxtv.org/v4lwiki/index.php/Kworld_NB-TV_100_(VS-NBTV100)_CardBus](http://www.linuxtv.org/v4lwiki/index.php/Kworld_NB-TV_100_(VS-NBTV100)_CardBus) but changing the card number to 17 when I call modprobe (and ignoring the sound redirction), I have been able to get this card *almost* working,  I can get video through both the s-video and composite cables.. but so far tvtime claims there isn't a signal from the cable (which there is).  

I'm going to try a few other things, and post the results here in a day or two.. if anyone knows why it isn't picking up the cable signal, please reply.. you'll save me a lot of time.

---

### Post by tmdowner on 2007-08-29
Update: I've gotten the tuner to work, but with no sound still.  After following the directions above, it's merely a matter of changing the /etc/modprobe.d/saa7134 file to:
```

options saa7134 card=17 tuner=10 i2c_scan=1
install saa7134 /sbin/modprobe --ignore-install saa7134; /sbin/modprobe saa7134-alsa

```

I'm still working on the sound, unfortunately.

---

