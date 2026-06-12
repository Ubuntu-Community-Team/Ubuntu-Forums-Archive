---
title: "Terratec AV350 shows nothing"
date: 2019-01-20
forum: Multimedia Software
---

### Post by udippel on 2019-01-20
It is well recognized, though:

[  210.699857] usb 1-1.5.1: new high-speed USB device number 8 using ehci-pci
[  210.815379] usb 1-1.5.1: New USB device found, idVendor=0ccd, idProduct=0084
[  210.815383] usb 1-1.5.1: New USB device strings: Mfr=0, Product=1, SerialNumber=0
[  210.815385] usb 1-1.5.1: Product: Grabster AV 350
[  211.406110] em28xx 1-1.5.1:1.0: New device  Grabster AV 350 @ 480 Mbps (0ccd:0084, interface 0, class 0)
[  211.406119] em28xx 1-1.5.1:1.0: Video interface 0 found: isoc
[  211.406429] em28xx 1-1.5.1:1.0: chip ID is em2860
[  211.636986] em28xx 1-1.5.1:1.0: EEPROM ID = 1a eb 67 95, EEPROM hash = 0x618085a2
[  211.636989] em28xx 1-1.5.1:1.0: EEPROM info:
[  211.636991] em28xx 1-1.5.1:1.0:      AC97 audio (5 sample rates)
[  211.636992] em28xx 1-1.5.1:1.0:      500mA max power
[  211.636994] em28xx 1-1.5.1:1.0:      Table at offset 0x04, strings=0x226a, 0x0000, 0x0000
[  211.636997] em28xx 1-1.5.1:1.0: Identified as Terratec AV350 (card=68)
[  211.636999] em28xx 1-1.5.1:1.0: analog set to isoc mode.
[  211.637195] em28xx 1-1.5.1:1.1: audio device (0ccd:0084): interface 1, class 1
[  211.637209] em28xx 1-1.5.1:1.2: audio device (0ccd:0084): interface 2, class 1
[  211.637232] usbcore: registered new interface driver em28xx
[  211.669671] usbcore: registered new interface driver snd-usb-audio
[  211.671133] em28xx 1-1.5.1:1.0: Registering V4L2 extension
[  211.768477] tvp5150 10-005c: tvp5150 (4.0) chip found @ 0xb8 (1-1.5.1:1.0)
[  211.768481] tvp5150 10-005c: tvp5150am1 detected.
[  214.656228] em28xx 1-1.5.1:1.0: Config register raw data: 0x50
[  214.691997] em28xx 1-1.5.1:1.0: AC97 vendor ID = 0x83847650
[  214.707987] em28xx 1-1.5.1:1.0: AC97 features = 0x6a90
[  214.707991] em28xx 1-1.5.1:1.0: Empia 202 AC97 audio processor detected
[  220.975983] em28xx 1-1.5.1:1.0: V4L2 video device registered as video1
[  220.975986] em28xx 1-1.5.1:1.0: V4L2 VBI device registered as vbi0
[  220.975988] em28xx 1-1.5.1:1.0: V4L2 extension successfully initialized
[  220.975990] em28xx: Registered (Em28xx v4l2 Extension) extension

But it doesn't show neither video nor audio. When I reboot to Windows on the same drive, everything works okay. I have tried with VLC, SMPlayer, mplayer, Flowblade, Pitivi; nothing to be seen or heard. What can I do next to progress, please?

---

### Post by Autodave on 2019-01-21
I did a web search and found quite a few things.  However, some are rather old but seem to be mostly the same.  I'll give you the web page, but I honestly do not know if this will help you or not.  Hopefully someone else will jump in here.

[https://www.google.com/search?client=ubuntu&hs=6VH&channel=fs&ei=G8JFXLrTLcrM_Aa6jr3AAg&q=Terratec+AV350++and+linux&oq=Terratec+AV350++and+linux&gs_l=psy-ab.3...27217.31499..31781...0.0..0.138.1030.10j2......0....1..gws-wiz.......35i39j0i22i30j0i22i10i30j33i299j33i22i29i30.5PjOoer0oUo](https://www.google.com/search?client=ubuntu&hs=6VH&channel=fs&ei=G8JFXLrTLcrM_Aa6jr3AAg&q=Terratec+AV350++and+linux&oq=Terratec+AV350++and+linux&gs_l=psy-ab.3...27217.31499..31781...0.0..0.138.1030.10j2......0....1..gws-wiz.......35i39j0i22i30j0i22i10i30j33i299j33i22i29i30.5PjOoer0oUo)

---

