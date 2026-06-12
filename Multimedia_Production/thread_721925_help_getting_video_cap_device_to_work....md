---
title: "help getting video cap device to work..."
date: 2008-03-11
forum: Multimedia Production
---

### Post by phoenix_fire2005 on 2008-03-11
I have a Kworld "DVD Maker USB 2.0" or something like that (model number VS-USB2800D). I believe it uses a em2800 chipset or something like that (windows detects it as USB 2860 Device).

anyway, when i plug the device in, Ubuntu says nothing, and as far as i can tell, never recognizes the device. i installed tvtime, and it loads but says it cannot find a video device. i also tried xawtv, but when i try to start it, nothing happens at all. im under the impression that ubuntu never recognizes the device... according to Hardware Informaiton, there is an unknown USB device that appears when I connect my device. supposedly, linux has support for em28xx devices, but it won't recognize my device, so what could I do to fix this?

anyway, im pretty much a linux/ubuntu noob, so go easy on me with the commands and stuff (i dont mind the idea using the terminal (as i used DOS a lot), but i hardly have a clue how to use it). thanks.

---

### Post by bandit36 on 2008-03-16
I'm in the same boat.  Here's what I've come up with so far:

When I plug in the USB2800D nothing appears to happen. No blinking lights, no windows popping up, nothing.

However, the device will mount to /dev/video1 (I have another webcam at /dev/video0).

Ucview & Skype will recognize the device on video1 as "v4l2 Unknown EM2800 video grabber".  When I try to run any (VLC, ucview, skype, kaffiene) off of video1 I get various error messages to the effect of:> $ sudo ucview

** (ucview:7103): WARNING **: Could not initialize DBUS connection :-(

enumerate: 8000000
Total count method 1: 2
Total count method 2: 0

** (ucview:7103): WARNING **: Failed to start video capture

enumerate: 8000000
Total count method 1: 2
Total count method 2: 0


Anyone smarter than I have any ideas?

---

### Post by bandit36 on 2008-03-17
Doh! I was following a guide ([http://www.2nrds.com/digital-tv-in-linux-with-em28xx-devices](http://www.2nrds.com/digital-tv-in-linux-with-em28xx-devices)) and now neither my camera or my video grabber are listed in /dev/video* ACK!

> 
hg clone [http://mcentral.de/hg/~mrec/v4l-dvb-kernel](http://mcentral.de/hg/~mrec/v4l-dvb-kernel)
cd v4l-dvb-kernel
make
sudo make install
#reboot here
sudo modprobe em28xx


my best guess for bringing my /dev/video* devices back to life is to get updated v4l drivers installed.  Anyone have any other ideas?

---

### Post by phoenix_fire2005 on 2008-03-17
interesting... in my case, it wouldn't even mount in the first place. perhaps i need newer vfl drivers or something... what did you do to get yours to mount in the first place?

---

### Post by mrbandersnatch on 2008-04-21
I got the kworld usb dvd maker 2.0 (em2860 based device?) working by more or less following the same procedure as above but with 2 important notes :

1) This was using Hardy.
2) I was using the experimental branch of v4l.

I'm not at my PC atm where I have a good link for this but, more or less, follow the above instructions but use v4l-dvb-experimental I'll try and post that link later.

---

### Post by Canezila on 2008-06-12
Thank you for the info above.  I now have my Kworld usb working... BUT ... it is only working in Black and White.  I have tried using the svideo and also the composite to see if I had a bad cable but the checked out fine.  

I am using  TVtime Television Viewer to watch my input... but it is also happening (the B&W video) with Mythtv....

I am running Ubuntustudio 8.06 86_64, 4 gigs of ram, AMD x2 4600, Nvidia 9600GT.. any thoughts?

I have the expermintal version of v4l.... I am probably missing something simple.  Is there a codec that I need to fix/adjust?

Brian:guitar:

---

### Post by heffo_j on 2008-07-01
Hi folks,

I'm no expert but I have been trying for weeks to get my em2860 based chipset to work on an analog UTV3 box.

In another thread I read that the current Hardy kernel does NOT accommodate the em28xx driver. Here is the thread:

[http://ubuntuforums.org/showthread.php?t=740473&highlight=usb+VHS+TV]("http://ubuntuforums.org/showthread.php?t=740473&highlight=usb+VHS+TV")They get their TV working after a kernel upgrade and some fiddling.

Regards
John

---

