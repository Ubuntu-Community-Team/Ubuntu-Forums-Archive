---
title: "[SOLVED] Brother MFC-685CW + CUPS"
date: 2008-12-27
forum: Networking &amp; Wireless
---

### Post by xHero on 2008-12-27
I am using ubuntu 8.10 and have installed the drivers found on the Brother drivers page.

When I check to make sure they are installed, I get the following:

```
~/Desktop$ dpkg  -l  |  grep  Brother
ii  mfc685cwcupswrapper                       1.0.1-1                                 Brother CUPS Inkjet Printer Definitions
ii  mfc685cwlpr                               1.0.1-1                                 Brother lpr Inkjet Printer Definitions
```

In the CUPS web control panel, I have it installed and set the Device URI to lpd://192.168.1.101/binary_p1 as instructed by Brother.

When I print a test page, the LCD on the front of the printer lights up, but it does not display the receiving data screen, nor does it print anything.  What am I doing wrong here?

Ross

---

### Post by xHero on 2008-12-31
Driver versions:

mfc685cwcupswrapper-1.0.1-1.i386
mfc685cwlpr-1.0.1-1.i386

These appear to be the newest.  The printer is connected via wired network.

---

### Post by bluplanet on 2009-10-31
I have Ubuntu 9.10.  
I cant connect to my Brother MFC-685CW.

Another post says the problem is solved and the printer is on a WIRED NETWORK.
That can't be true.  This printer is WI-FI only.  There is no Ethernet port on this machine and the only USB port is for a thumb drive.

I originally had this printer connected when I had Vista.  When I switched to Ubuntu 8.04, it found and installed the MFC-685CW with less effort than Vista did when I first installed the printer.  

I believe Ubuntu stopped connecting to the printer after one of the updates.
I'm using MAC address filtering on my router.  The printer's MAC address is in the list of accepted devices in the router.

Update:  I just connected to the printer.  I have no idea if I did anything different.  I don't think I did.  My problem was  that the printer wasn't connecting to the network.  This time, I simply went through the printer's set up menu to confirm what the settings were.  As I was exiting the menu cascade, the printer's screen said "Connected." as I was exiting the authentication screen.  
I don't know what, if anything, was changed.

---

### Post by bluplanet on 2011-01-02
OOPS!
I said there was no wired network connections on the machine.  My Bad!
There's none visible from the outside, but if I open it up as though I want to clear a paper jam. there's a USB and an Ethernet port inside with channels to lay the wire in to run it out under the hinged backside.

---

