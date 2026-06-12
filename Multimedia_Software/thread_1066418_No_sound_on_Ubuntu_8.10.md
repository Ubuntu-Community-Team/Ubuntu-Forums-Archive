---
title: "No sound on Ubuntu 8.10"
date: 2009-02-10
forum: Multimedia Software
---

### Post by avrilrox on 2009-02-10
This is the first time i try Ubuntu on this computer and I've been having some problems.

I don't get any audio output, all of the sound bars are set to the maximum and not muted. When i test the sound output, i get an error. I can't play any mp3s and no sounds can be heard.

I've followed some guides, recompiled ALSA (with some errors). At first, the version of ALSA on my ubuntu was 1.0.15 and the audio wouldn't work even though my card runs perfect with ALSA 1.0.13 and above.

I edited asoundrc, both my home file and the one located in /etc. Restarted my computer a million times, still no luck. I have two pairs of speakers connected and none of them work.

I've completely run out of ideas, as i have followed every guide i could find on the internet and my sound still doesn't work.

I'm running a 64bit version, could that the reason why my card doesn't work? It's not a hardware issue, since it works perfectly on Windows Vista X64 (which i don't like and that's why i want to use Ubuntu).

Please help, I really want to get this working on Ubuntu.

Thanks in advance.

---

### Post by avrilrox on 2009-02-15
Can anyone please help me? I still can't get it to work :(

---

### Post by markbuntu on 2009-02-15
have you been here?


[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

### Post by avrilrox on 2009-03-02
> **markbuntu said:**
> have you been here?


[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

That's a really good guide but it didn't seem to help.

---

### Post by markbuntu on 2009-03-03
It is difficult to help people with hardware problems when they are not being very specific about what hardware they have. Go here, get the info and post it back here in this thread and we will see what we can do for you

[http://ubuntuforums.org/showthread.php?p=6628921](http://ubuntuforums.org/showthread.php?p=6628921)

---

### Post by BLTicklemonster on 2009-03-03
Mine didn't work at all, either. amd 64 bit system. I had to go to system, preferences, sound, and change all to my sound card ALSA, closed then it worked. Suddenly, later, (which isn't sudden at all now, is it? never mind, just follow me here, mkay?) it all stopped working again. I changed all to pulse, still nothing, changed all back to my previous settings, then viola, it worked again. NO idea what was up with that, what with the latent suddenness of it all and everything...

Probably not going to help you, but maybe it will?

---

### Post by avrilrox on 2009-03-03
> **BLTicklemonster said:**
> Mine didn't work at all, either. amd 64 bit system. I had to go to system, preferences, sound, and change all to my sound card ALSA, closed then it worked. Suddenly, later, (which isn't sudden at all now, is it? never mind, just follow me here, mkay?) it all stopped working again. I changed all to pulse, still nothing, changed all back to my previous settings, then viola, it worked again. NO idea what was up with that, what with the latent suddenness of it all and everything...

Probably not going to help you, but maybe it will?

Okay. What sound chip are you currently using?


Here are my Outputs:

```
asd@x2:~$ lspci
00:00.0 Memory controller: nVidia Corporation CK804 Memory Controller (rev a3)
00:01.0 ISA bridge: nVidia Corporation CK804 ISA Bridge (rev f3)
00:01.1 SMBus: nVidia Corporation CK804 SMBus (rev a2)
00:02.0 USB Controller: nVidia Corporation CK804 USB Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation CK804 USB Controller (rev a3)
00:06.0 IDE interface: nVidia Corporation CK804 IDE (rev f2)
00:07.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
00:08.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
00:09.0 PCI bridge: nVidia Corporation CK804 PCI Bridge (rev f2)
00:0a.0 Bridge: nVidia Corporation CK804 Ethernet Controller (rev f3)
00:0b.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev f3)
00:0c.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev f3)
00:0d.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev f3)
00:0e.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:01.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev c0)
05:00.0 VGA compatible controller: nVidia Corporation Geforce 9600 GT 512mb (rev a1)

```

My sound chip in bold:
```
asd@x2:~$ lsusb
**Bus 002 Device 003: ID 0d8c:0201 C-Media Electronics, Inc.** 
Bus 002 Device 002: ID 046d:c042 Logitech, Inc. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 002: ID 0bda:8189 Realtek Semiconductor Corp. 
Bus 001 Device 001: ID 0000:0000  

```

```
asd@x2:~$ cat /proc/asound/cards
 0 [default        ]: USB-Audio - PnP Audio Device        
                      PnP Audio Device         at usb-0000:00:02.0-7, full speed

```

```
asd@x2:~$ cat /proc/asound/modules
 0 snd_usb_audio

```

```
asd@x2:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: default [PnP Audio Device        ], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

```
asd@x2:~$ arecord -l
**** List of CAPTURE Hardware Devices ****
card 0: default [PnP Audio Device        ], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

Thanks for help! :D

---

### Post by avrilrox on 2009-03-03
Also, when i do **cat ****/proc/asound/devices**:
```

asd@x2:~$ cat /proc/asound/devices
  0: [ 0]   : control
  1:        : sequencer
 16: [ 0- 0]: digital audio playback
 24: [ 0- 0]: digital audio capture
 33:        : timer

```

---

### Post by BLTicklemonster on 2009-03-03
Sound Blaster live 5.1 pci card. Sorry I wasn't any help.

---

### Post by BLTicklemonster on 2009-03-03
Oh, and try this, see if it helps any

[http://ubuntuforums.org/showthread.php?t=997506](http://ubuntuforums.org/showthread.php?t=997506)

---

### Post by markbuntu on 2009-03-03
So, you have a c-media usb sound something or other.
What is it connected to besides the usb port?

---

### Post by avrilrox on 2009-03-04
> **markbuntu said:**
> So, you have a c-media usb sound something or other.
What is it connected to besides the usb port?

No no. It is an onboard device on my M2N-SLI motherboard and happens to be an usb device.

I have a couple speakers connected to it.

---

### Post by avrilrox on 2009-03-04
> **BLTicklemonster said:**
> Oh, and try this, see if it helps any

[http://ubuntuforums.org/showthread.php?t=997506](http://ubuntuforums.org/showthread.php?t=997506)

Oh. The guide didn't help at all :(

Thanks, though.

---

