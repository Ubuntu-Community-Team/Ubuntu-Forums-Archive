---
title: "Bluetooth KY-BT100 USB dongle..."
date: 2009-02-17
forum: Networking &amp; Wireless
---

### Post by grenadier32 on 2009-02-17
I've got a brand new KY-BT100 USB Bluetooth dongle, and it only partially works in Intrepid. I got Blueman working, but while that detects the hardware just fine, it can only scan and find devices--it can't connect to anything. Both my cellphone and audio headset (and a few other nearby computers with Bluetooth on) are scannable, but I can't connect to anything. It doesn't even get to the point where it asks me for a passcode.

I also tried BlueSoleil, which is supposed to be intended for this hardware, but it can't find it in Linux--the Windows one, however, works OK.

Is there a way to get either BlueSoleil to recognize the hardware, or to get Blueman/the software behind it to actually connect using the KY-BT100? Is there a driver I'm missing?

---

### Post by StephSD3 on 2009-02-20
Did you try BlueSoleil in wine? (btw: I hate BlueSoleil, even in Windows. It never works correctly and just sucks).
And in order for me to install Blueman correctly it took about 5 times reloading my apt manager (10 min space in between) after adding the repository. Maybe you can try to reinstall it?

---

### Post by CalvinK on 2009-02-22
> **grenadier32 said:**
> I've got a brand new KY-BT100 USB Bluetooth dongle, and it only partially works in Intrepid. I got Blueman working, but while that detects the hardware just fine, it can only scan and find devices--it can't connect to anything. Both my cellphone and audio headset (and a few other nearby computers with Bluetooth on) are scannable, but I can't connect to anything. It doesn't even get to the point where it asks me for a passcode.

I also tried BlueSoleil, which is supposed to be intended for this hardware, but it can't find it in Linux--the Windows one, however, works OK.

Is there a way to get either BlueSoleil to recognize the hardware, or to get Blueman/the software behind it to actually connect using the KY-BT100? Is there a driver I'm missing?

I have exactly the same problem with my Motorola S9 headset. It worked with a little tinkering with Hardy and Blueman. I'm unable to use it with Intrepid.

---

### Post by jrbenito on 2009-03-07
The same here.

I had the KY-BT100 USB working on Hardy now on intrepid it find all BT (another computer, celular and headset) but can't do paring with anyone.

Regards,

---

### Post by grenadier32 on 2009-06-16
This thread is old, but in case any of you are still watching for a solution: Blueman works and solves the problem.

[http://blueman-project.org/](http://blueman-project.org/)

It can be installed from a PPA.

---

