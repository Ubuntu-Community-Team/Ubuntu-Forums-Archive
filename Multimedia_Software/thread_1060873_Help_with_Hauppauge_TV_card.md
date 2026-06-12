---
title: "Help with Hauppauge TV card"
date: 2009-02-05
forum: Multimedia Software
---

### Post by Deltalima on 2009-02-05
Hi

This is my first post and I am very new to Ubuntu.  I have a Hauppauge TV card and have somehow downloaded V4L-DVB but I still can't get it to work the device does not appear to recognise the driver.  I dmesg I get this

[   10.094621] cx88[0]: Your board isn't known (yet) to the driver.  You can
[   10.094623] cx88[0]: try to pick one of the existing card configs via
[   10.094624] cx88[0]: card=<n> insmod option.  Updating to the latest
[   10.094625] cx88[0]: version might help as well.
[   10.094629] cx88[0]: Here is a list of valid choices for the card=<n> insmod option:

Can anyone tell me how to use this insmod option so that I can connect my card to option 37

Really appreciate any help but if you do please can you spell out in detail what I need to do

Many thanks in advance

---

### Post by Deltalima on 2009-02-11
Well in the end I sorted this out myself - so feeling pretty pleased. Just in case anyone else want any help this is what to do.

Go to this website

[http://wiki.linuxmce.org/index.php/Hauppauge_Nova-HD-S2](http://wiki.linuxmce.org/index.php/Hauppauge_Nova-HD-S2)

Follow precisely the instructions for Installing The Drivers and Firmware

Thats it!  After that Kaffein could talk to the card and scan for the channels

---

