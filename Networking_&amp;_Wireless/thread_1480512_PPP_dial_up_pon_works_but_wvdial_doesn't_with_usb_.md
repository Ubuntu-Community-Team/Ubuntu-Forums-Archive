---
title: "PPP dial up pon works but wvdial doesn't with usb modem"
date: 2010-05-11
forum: Networking &amp; Wireless
---

### Post by sarpulhu on 2010-05-11
I'm having a few problems setting up my dial up on lucid lynx. I think they are all related somehow. I'm using a usb to serial adapter to connect an old external modem. lsusb lists the serial adaper. I used pppconfig to set the modem to: ttyUSB0. By using pon I can connect to the internet. I've downloaded wvdial and tried running wvdialconf but it doesn't find the modem? I don't mind connecting using pon but it appears that it is causing Ubuntu ONE to not be able to connect? I've wondered if network manager is not recognizing the connection and that makes ubuntu one think I'm offline. No matter what I do I can't get Ubuntu ONE to work and I'm guessing it has something to do with my PPP setup. Any help would be appreciated.

---

### Post by alexfish on 2010-05-11
hi 

can you post the results of this command from the terminal

Code:

dmesg | grep -e "modem" -e "tty" 

this will just give you the lines including **modem**. 

thanks in advance

alexfish

---

### Post by sarpulhu on 2010-05-11
all it said was:
[    0.000000] console [tty0] enabled

(not plugged in- I don't have it at the moment- will do it later if needed)

---

### Post by sarpulhu on 2010-05-11
when connecting to high speed everything works. Using PPP Ubuntu ONE won't work

---

### Post by alexfish on 2010-05-11
hi

one thing of note is to ensure the baud rates are correct for the modem

cross-reference the baud rates to the one that works

also same applies to the tty ports

if this does not work then I will need further info ; main one already mentioned

other possibility "permissions" but try the above first

regards

alexfish

---

### Post by sarpulhu on 2010-05-11
[    0.000000] console [tty0] enabled
[   23.663303] usb 4-1: MCT U232 converter now attached to ttyUSB0

with usb modem attached. How do I set baud rate? I just know how to wvdialconf. Usually everything is all done for me.

---

### Post by alexfish on 2010-05-12
hi

I am sitting here scratching my head !


  does your computer have a serial port although looking at the post you may not have, I could suggest using a computer  with a serial port may make a difference , but I could not say for sure

looking on the bright side you do have a connection and can browse the net and do downloads , and have succeeded where others may fail

at present I do not know the answer to the problem with ubuntu one

perhaps they may be able to help there

[Ubuntu One]("http://ubuntuforums.org/forumdisplay.php?f=367")


regards

alexfish

---

### Post by sarpulhu on 2010-05-12
Thanks for trying. My computer has no serial port and I didn't want to buy a new one so I just bought a usb-serial adapter. The only reason I knew pon worked was by reading instructions that wvdial doesn't come with ubuntu so I had to use it first. So I was kind of surprised that one worked while the other didn't. I've had ubuntu one problems and was trying to figure out what the deal was. I was guessing it was network manager but I thought perhaps fixing wvdial would be easier... I'll keep searching.

---

