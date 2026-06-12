---
title: "c-media usb headset problems in wine"
date: 2007-04-30
forum: Multimedia &amp; Video
---

### Post by dfreer on 2007-04-30
hey everyone,

 so I have this c-media usb headset I got from the local radio shack. I am trying to get it to work in wine, so that I can chat on Counter-strike. When I go to System > Preferences > Sound, and I set all the options to use USB Audio, I can press the "Test Sound" button and hear a beep in my headphones. I go to the volume mixer and set it to use C-Media USB Headphone Set (Alsa Mixer). Opening a movie on my computer in totem and I can hear the movie playing in my headphones, as well as mp3's in rhythmbox! So far, so good.

 But when I go to Counter-Strike, all sounds are playing through my laptop speakers. Also, ZSNES and pSX both use laptop speakers. When I log in and out, all system sounds go through the laptop speakers. I can't seem to figure out why some sounds use the laptop and some use the headset. Here's some useful info (in particular, it seems alsamixer is configuring the wrong sound card (my intel card instead of the c-media usb headset):

```
$ lsusb
Bus 004 Device 002: ID 03f0:171d Hewlett-Packard 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 045e:00e1 Microsoft Corp. 
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 003: ID 0d8c:000c C-Media Electronics, Inc. Audio Adapter
Bus 002 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 0c45:62c0 Microdia 
Bus 001 Device 001: ID 0000:0000  

```

```
$ dmesg | tail
[  228.360000] usb 2-1: new full speed USB device using uhci_hcd and address 3
[  228.576000] usb 2-1: configuration #1 chosen from 1 choice
[  228.660000] input: C-Media USB Headphone Set   as /class/input/input9
[  228.660000] input: USB HID v1.00 Device [C-Media USB Headphone Set  ] on usb-0000:00:1d.0-1

```

```
$ alsamixer
&#9474; Card: HDA Intel                                                                                                                
&#9474; Chip: **[B]Conexant CX20549 (Venice) **[/B]  #WRONG CARD!!                                                                                                                     
&#9474; View: [Playback] Capture  All                                                                                                                             
&#9474; Item: Master  
```

---

