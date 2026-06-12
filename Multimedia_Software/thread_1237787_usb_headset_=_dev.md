---
title: "usb headset = /dev/???"
date: 2009-08-11
forum: Multimedia Software
---

### Post by b3nw on 2009-08-11
Hello,

I am trying to get a usb headset working with a softphone called sjphone.

The softphone gives me the ability to put in /dev/??? for both input and output.

When I use /dev/dsp (for both settings) I get output to my internal speakers, but no input.
When I use /dev/dsp1 (for both settings) I get output to my headset, but no input.

I can't seem to find any informative posts about where the usb headset goes /dev/ wise.

I am able to use the headset without issue for Skype, but I need the /dev/device for this softphone solution.

Any help would be appreciated.

-Ben

---

### Post by burkas on 2009-08-12
Would you put your "lsusb" result ;) ...

---

### Post by b3nw on 2009-08-12
msi@msi-test:~$ lsusb
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 046d:c016 Logitech, Inc. M-UV69a Optical Wheel Mouse
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 047f:d055 Plantronics, Inc. 
Bus 001 Device 001: ID 0000:0000  
msi@msi-test:~$ 


The d055 is the headset.

Thanks

---

