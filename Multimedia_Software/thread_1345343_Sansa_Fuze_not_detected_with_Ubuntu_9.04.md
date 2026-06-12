---
title: "Sansa Fuze not detected with Ubuntu 9.04"
date: 2009-12-03
forum: Multimedia Software
---

### Post by daimyo505 on 2009-12-03
Hello, I thought I would post my problem and also my solution to my newly acquired media player.

Problem:
My Sansa Fuze would not be detected by Ubuntu 9.04.

Attempts:
On my media player I switched the USB mode to from autodetect to "MSC". nope
I unplugged the music player and plugged it back in again several times. nope
I attempted to find the device with the command 'lsusb'. the device was not found.
I attempted to jiggle the wire and push it around. I read that sometimes the USB connector does not make contact. nothing
I made sure I was not connected into any USB fanning devices. It was not.
I made sure the connector was not in any USB extension cables. It was not.
I tried another USB port. That did not work either.

EDIT: 
No Solution:
I turned on my Windows XP laptop, waited for the 7 minutes it takes to startup, then plugged the device into the laptop. It detected on Windows.

I then removed the device and plugged it into linux. Then it autodetected. I was able to transfer music!

The solution I found didn't work the second or third time I tried it. It seems I was a little pre-emptive in my post.

---

### Post by daimyo505 on 2009-12-06
I've also tried these commands:

sudo rmmod ehci-hcd. Produces an 'ERROR' message. No success.

sudo modprobe ehci-hcd. Produces a 'FATAL' message. No success.

---

### Post by daimyo505 on 2009-12-06
I recently (Dec 6,2009) upgraded to Ubuntu 9.10, and still no connection to the Sansa Fuze.

---

### Post by cpeachey on 2009-12-09
On my Sansa Clip I had to change the settings to "MSC" (on the clip not in Ubuntu). Perhaps yours requires something similar.
On the Creatuve Zen Mozaic I had to upgrade the firmware (via Windows!)
Hope this helps
Chris

---

### Post by daimyo505 on 2009-12-13
Hello again,

I've been working trying to find a solution to autodetect my Sansa Fuze. I believe I found the solution this time (fingers crossed).

Solution:
I went into the BIOS and disabled the "USB 2.0".

After saving the settings and restarting the Sansa autodetected! I hope this helps others.

---

