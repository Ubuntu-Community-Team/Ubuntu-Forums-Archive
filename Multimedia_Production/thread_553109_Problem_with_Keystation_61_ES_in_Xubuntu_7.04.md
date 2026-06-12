---
title: "Problem with Keystation 61 ES in Xubuntu 7.04"
date: 2007-09-17
forum: Multimedia Production
---

### Post by hisaki on 2007-09-17
I've installed Xubuntu 7.04 a few days ago. I've had some problems getting my sound to work. I'm using a built in soundcard and a firewire solo. And I also have an Maudio keystation61 ES USB midi keyboard

I set up freebob / jack for use with the firewire solo which worked and I could record and use my midi keyboard.

Then I had some trouble getting the onboard soundcard to work. But I got there in the end following these instructions:
[http://ubuntuforums.org/showthread.php?t=455147](http://ubuntuforums.org/showthread.php?t=455147)

However, since I get my built in soundcard to work my midi keyboard refuses to work. Running lsusb I get the following output:
```
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 011: ID 0a4d:0091 Evolution Electronics, Ltd 
Bus 001 Device 002: ID 04fc:0003 Sunplus Technology Co., Ltd CM1092 Optical Scroller Mouse
Bus 001 Device 001: ID 0000:0000  

```

From previous google searches I know the device called evolution electronics should be the midi keyboard. If I then run qjackctl I get the following errors:
```
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device

```

Not sure if those are related but my keyboard is no longer listed in jack. After running jack if I list my USB devices the keyboard is no longer there either:
```
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 002: ID 04fc:0003 Sunplus Technology Co., Ltd CM1092 Optical Scroller Mouse
Bus 001 Device 001: ID 0000:0000 
```

Does anyone know what could be wrong?

---

### Post by hisaki on 2007-09-17
ok I've recompiled alsa with the usb-audio added as a switch and now my midi keyboard is there again if I type "amidi -l".

However, doing this seems to have broken something else midi related. I now get the following error when trying to start jack:

```
00:27:07.788 Could not open ALSA sequencer as a client. MIDI patchbay will be not available.
ALSA lib seq_hw.c:457:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory
```

Yes it's probably something very obvious and simple but I'm new at this. So please, could someone tell me how to fix this? Or at least point me in the right direction so I can continue trying to fix it for myself.

edit:
I fixed it :-D 
I'm so happy 

The last problem was easily fixed by adding "snd-seq-midi" at the end of /etc/modules

If anyone else has the same problem as me (I don't know how likely that is but when searching I found so many dead ends on forums) "sudo sh configure --with-oss=yes --with-cards=hda-intel,usb-audio --with-kernel=/usr/src/linux-headers-`uname -r`/" is how I configured alsa to work with both my onboard card and my midi keyboard.

---

