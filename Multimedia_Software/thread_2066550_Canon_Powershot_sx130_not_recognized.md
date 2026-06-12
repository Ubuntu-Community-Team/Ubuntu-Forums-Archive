---
title: "Canon Powershot sx130 not recognized"
date: 2012-10-04
forum: Multimedia Software
---

### Post by elcapitankyle on 2012-10-04
Hi. When I plug my camera (canon powershot sx130) in via usb it doesn't get recognized by the system. In digikam the import menu remains grayed out and in picasa it does not show up on the import screen's list of devices. 

I'd love to troubleshoot this and track down the issue but I'm at a loss as to where to start. Can anyone give me some items to check that could get me in the right direction. I'm fairly comfortable with digging around via the terminal and making changes but I've never had to really track down or figure out a camera related issue before. Any help or advice would be greatly appreciated.

---

### Post by pwabrahams on 2012-10-14
Does **lsusb** from a terminal window show the camera?  The results of that test might guide your search for an answer.

I know there was a similar problem with the A1000 at one time, but I don't know it it was fixed.

You might try the following sequence, suggested by the A1000 manual:

1. Power off the camera.

2. Plug in the cable.

3. Press the right-arrow button near the place where you plug in the cable.  That is supposed to turn on the camera (the A1000, anyway) and connect it to the computer.  That supposes, of course, that the sx130 has a similar button.

This may or may not produce a different result than inserting the cable and then turning on the camera with the power button, or turning on the camera and then inserting the cable.

If you're still following this thread, please post the results you get even if they are negative.

---

