---
title: "Help with webcam"
date: 2007-06-09
forum: Multimedia &amp; Video
---

### Post by bennykenkireth on 2007-06-09
I have purchased a new webcam. I couldn't get in working on my machine.
lsusb returns
Bus 004 Device 004: ID 0c45:6270 Microdia
Bus 004 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 002: ID 413c:3010 Dell Computer Corp. Optical Wheel Mouse
Bus 002 Device 001: ID 0000:0000

My cam has a chip from Microdia. I have no idea of how to get it working.
ANy help will be appreciated. Thank you.

---

### Post by ciumbuntu on 2007-06-11
up

---

### Post by Lex Luthor on 2007-08-01
Hello !


I have the same camera, and I cannot make it work... please, if you could manage do make it work, tell me !!!

I've tried to install the sn9cxxx_2.05-1ubuntu1_i386.deb package, but it shows me: 

> [  760.421413] sn9c20x: V4Lx driver for SN9C20x PC Camera Controllers v2:2.05
[  760.421419] sn9c20x: (C) 2007 Luca Risolia
[  760.421424] sn9c20x: By using this software, you declare that you have read and accepted the LICENSE included in the 'copyright' file accompanying this software.If not, stop using this software.
[  760.479630] usb 5-2: SN9C20X PC Camera Controller detected (vid 0x0C45)
[  760.501098] usb 5-2: Sorry, your webcam is not supported at the moment.
[  760.501104] usb 5-2: For more informations, please send an email to the author: <name@domain.com> , together with the output of the command 'lsusb -v' and, if possible, a link to the reseller
[  760.501131] usbcore: registered new interface driver sn9c20x
 and does not work. 
I've also tried to compile gspca module, but it did not work....

Anybody... please....

---

### Post by Flyvapnet on 2007-08-02
**Lex**, I'm very sorry but I can't help you.  I just wanted you to know you're not alone in being either ignored or given the run-around when it comes to web cameras.

If you ever get a straight answer, regarding how to get webcams to work with Ubuntu or any Linux system, consider yourself very lucky indeed.  I just purchased a webcam which supposedly works with Linux, only to discover that in fact it doesn't.

Linux's true believers are, generally speaking, friendly and helpful folk; but they make an exception when it comes to webcams.  No straight-answer documentation exists, not in the Wiki and not on this board; so you may draw your own conclusions regarding whether or not Linux operating systems are truly viable.

:(

=^..^=

P.S.:  In spite of my rant, I've just now managed to get my web camera to work -- thanks to help from fellow board members.  I've an Intel CS430 which it turns out wasn't recognized by the operating system until I plugged it into a different uniform serial bus socket.  I'd also installed Camstream from the Synaptic Package Manager; and after taking those two steps Camorama decided to work at last -- which is a good thing because my patience was literally at an end!

---

