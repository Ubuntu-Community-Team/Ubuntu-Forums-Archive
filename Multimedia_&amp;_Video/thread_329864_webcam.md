---
title: "webcam"
date: 2007-01-02
forum: Multimedia &amp; Video
---

### Post by Nim on 2007-01-02
Hiya,

I'm a really really basic linux (ubuntu) user.

I just bought a logitech quickcam for notebooks pro (as it said it was compatible on [www.linux.com/howtos/Webcam-HOWTO/devices.shtml)](www.linux.com/howtos/Webcam-HOWTO/devices.shtml)).

However, I'm trying to work out how to install it and don't really understand the jargon - could someone please (please please please) explain it to me in layman terms?? 

Thank you,
Naomi

---

### Post by OffHand on 2007-01-02
> **Nim said:**
> Hiya,

I'm a really really basic linux (ubuntu) user.

I just bought a logitech quickcam for notebooks pro (as it said it was compatible on [www.linux.com/howtos/Webcam-HOWTO/devices.shtml)](www.linux.com/howtos/Webcam-HOWTO/devices.shtml)).

However, I'm trying to work out how to install it and don't really understand the jargon - could someone please (please please please) explain it to me in layman terms?? 

Thank you,
Naomi

What's the output of 'lsusb'?  (without quotes)
Do you get any image from your cam at all if you use Camorama Webcam Viewer?

---

### Post by Nim on 2007-01-03
I typed lsusb into terminal and it said:

Bus 004 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000

I haven't plugged the webcam in yet ( I was going to use ekiga - is this wrong?) as I thought you had to configure things first?

Thanks,
Naomi

---

### Post by OffHand on 2007-01-03
> **Nim said:**
> I typed lsusb into terminal and it said:

Bus 004 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000

I haven't plugged the webcam in yet ( I was going to use ekiga - is this wrong?) as I thought you had to configure things first?

Thanks,
Naomi

Shut it down, plug it in, boot up and run lsusb again.

---

### Post by Nim on 2007-01-03
ok, it says:

Bus 004 Device 002: ID 046d:08cb Logitech, Inc.
Bus 004 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000

---

### Post by OffHand on 2007-01-03
Do you get an image from your cam if you open Camorama Webcam Viewer from 'Applications>Graphics'

---

### Post by Nim on 2007-01-03
I don't have that in my applications.

I assume I can get it from add/remove, however, can't get wireless on my laptop right now, so I'll try tonight/tomorrow to find a wifi cafe and check it out.

thank you so much :-)

---

### Post by OffHand on 2007-01-03
> **Nim said:**
> I don't have that in my applications.

I assume I can get it from add/remove, however, can't get wireless on my laptop right now, so I'll try tonight/tomorrow to find a wifi cafe and check it out.

thank you so much :-)

Alright. I'll check this thread.

---

### Post by Nim on 2007-01-11
Hey!

Sorry it's taken me so long to reply - I've been in the process of moving. I downloaded camorama but when I try to open it, it says:

 "could not connect to video device (dev/video0/). Please check connection."

Any suggestions?

---

### Post by nico-ar on 2007-02-26
the same problem here!


Bus 002 Device 004: ID 05e3:0710 Genesys Logic, Inc. USB 2.0 33-in-1 Card Reader
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 093a:2468 Pixart Imaging, Inc. Easy Snap Snake Eye WebCam
Bus 001 Device 003: ID 046d:c01d Logitech, Inc. 
Bus 001 Device 001: ID 0000:0000  

but in camorama not found..

any help?

---

### Post by nalmeth on 2007-02-26
Sure, have you done this?
[https://wiki.ubuntu.com/Webcam](https://wiki.ubuntu.com/Webcam)

---

### Post by Doug11 on 2007-02-27
i had to manually install the spca5xx driver to get my logitech quickcam working. Just click on the howto link in the above thread for it and it should go for you.

---

