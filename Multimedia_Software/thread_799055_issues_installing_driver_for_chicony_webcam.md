---
title: "issues installing driver for chicony webcam"
date: 2008-05-18
forum: Multimedia Software
---

### Post by Deviantess on 2008-05-18
Hello,
      almost complete noob here.

I installed Hardy three days ago, and was really impressed at how easy it was, compared to when I tried Fedora a few years ago. (I tried hard but it made me cry).
 I do not have great computer skills, but I really want to try and make this work.

Most things I have solved by reading this forum, which has been great.

My webcam has become the sticking point.
I have a divio chicony twinklecam, which I cannot install.  From researching, I think the correct driver is sn9c1xx-1.48.tar.gz.  I have downloaded this and followed the instructions to install it.  I couldn't make it work.


the results of lsusb are:

Bus 002 Device 003: ID 07b2:5100 Motorola BCS, Inc. SurfBoard SB5100 Cable Modem
Bus 002 Device 002: ID 06a5:d800 Divio Chicony TwinkleCam
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 005: ID 04b8:0005 Seiko Epson Corp. Stylus Printer
Bus 001 Device 004: ID 04a5:20b0 Acer Peripherals Inc. (now BenQ Corp.) S2W 3300U/4300U
Bus 001 Device 003: ID 05e3:0606 Genesys Logic, Inc. D-Link DUB-H4 USB 2.0 Hub
Bus 001 Device 002: ID 04b4:6830 Cypress Semiconductor Corp. USB-2.0 IDE Adapter
Bus 001 Device 001: ID 0000:0000  

It is connected to the computer, not a hub.

When I get to the "make modules" point, I get a long list that looks like this sample.

/home/devi/sn9c1xx-1.48/sn9c102_core.c: In function ‘sn9c102_usb_probe’:
/home/devi/sn9c1xx-1.48/sn9c102_core.c:3302: error: ‘struct video_device’ has no member named ‘hardware’

The install text has this suggestion.
"If the commands fail, control the Makefile and change the path to the kernel
source tree or to any other files, according to your system configuration;
then run the previous commands again."

I don't know how to do this.

Any help would be greatly appreciated. :)
Thanks,
Devi

---

### Post by Deviantess on 2008-05-20
Ah, well, not to worry, for anyone who was thinking about this.

Last night, Ubuntu stopped connecting to the net, quite spontaneously.
I have no idea what I did, or how to fix it, so after several hours, out came the XP disk.

Devi

---

