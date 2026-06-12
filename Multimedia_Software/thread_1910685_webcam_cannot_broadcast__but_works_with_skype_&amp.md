---
title: "webcam cannot broadcast  but works with skype &amp; cheese"
date: 2012-01-17
forum: Multimedia Software
---

### Post by nkbatsi on 2012-01-17
Hi again everybody.

I am trying a cheap camera (genius iLook 1321 V2 is the name), on a 64-bit system with 11.10 on it.
Unlike all the threads I read till now, I got it to work with cheese, and skype shows preview.
But I don't seem to be able to broadcast through aMsn and websites. 

The most annoying is that when I try lsusb I don't get anything about a cam

[HTML]Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 006: ID 0458:7061 KYE Systems Corp. (Mouse Systems) 
Bus 006 Device 002: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 006 Device 003: ID 046d:c31c Logitech, Inc. Keyboard K120 for Business
Bus 006 Device 004: ID 045e:0084 Microsoft Corp. Basic Optical Mouse [/HTML]Does anybody have an idea of what might be happening.
Thanks!

---

### Post by hansum_rahul on 2012-01-17
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
> Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
[COLOR="Red"]Bus 002 Device 006: ID 0458:7061 KYE Systems Corp. (Mouse Systems) 
[/COLOR]Bus 006 Device 002: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 006 Device 003: ID 046d:c31c Logitech, Inc. Keyboard K120 for Business
Bus 006 Device 004: ID 045e:0084 Microsoft Corp. Basic Optical Mouse

Your USB Webcam is listed!

Probably you have an issue with flash?

---

### Post by nkbatsi on 2012-01-17
Ok man, I'm sorry ,didn't see that, It was saying something about a mouse corporation.
Well I'm trying to figure out what adjustments the adobe flash player might need to make the cam work!
Thanks.

---

### Post by saneearth on 2012-01-17
If you are using Firefox, try Chromium for your broadcast. I have recently been having some Flash issues with Firefox that aren't apparent in Chromium. It would be something to try anyway.

---

### Post by nkbatsi on 2012-01-17
Just tried it, the same with chromium, which I' ve tried previously. As for the problems in firefox I used flash-aid and have no problems with flash anymore!

---

### Post by nkbatsi on 2012-01-17
Still adobe flash cannot use the webcam. Any ideas?

---

### Post by nkbatsi on 2012-01-20
Ok, I just found the solution. I'm sorry for getting some guys in trouble viewing this thread, but it still could give some ideas to people facing the same behaviour from ubuntu. 

What I had to do for the camera to turn on in chat websites was to :


Right click on the broadcast view of my cam.
Select "Global Settings" in the adobe pop-up window.
In this popup window Select the tab Camera and Mic.
Below this tab there's a button saying "Camera and Microphone Settings by site":
Clicked it, and in the popup window selected the preference site and clicked "Allow" for it.
Refreshed the page and then my camera started operating.

Take note that the mini popup window (when selecting just "Settings" in your view window) can only be navigated through <Tab> and <Return> button, not the mouse, (this took me some time to figure out)!

Have you ever heard of the phrase "getting drowned in a spoonfull of water"?

Well that's me. Just remember Linux and Ubuntu are just great - everything just works. 
Be patient the solutions are always just before our eyes!

---

