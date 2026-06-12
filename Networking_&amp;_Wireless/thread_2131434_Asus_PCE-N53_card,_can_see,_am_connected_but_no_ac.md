---
title: "Asus PCE-N53 card, can see, am connected but no activity. terminal outputs"
date: 2013-04-01
forum: Networking &amp; Wireless
---

### Post by peterthinking on 2013-04-01
I have it installed, its seeing everything but the connection seems to work for a second or two then quits but it still says it's connected.

       System
Ubuntu 12.04 64 bit system, EVGA GT 520 2 Gig video card, 16 gigs Kingston 1600 DDR3 ram, 500 gig WD hard drive, i52500K processor, ASUS P8P67-M Motherboard, second drive 250 gig SSD with Windows 7, BitFenix Raider case full of NOCTUA NF-S12B fans, Seasonic X series fanless 460W 80 plus gold Modular power supply. Seperate boot managers. Either drive accessed thru the ASUS Bios boot menu.  

     Below are the outputs from the terminal I saw requested on a similar thread.

uname -a
lspci -nnk
lsusb
lsmod
iwconfig
rfkill list

          **Edit output not needed for solution.

---

### Post by chili555 on 2013-04-01
> ra0 Ralink STA ESSID:"TELUS2403" Nickname:"RT2860STA"
Mode:Managed Frequency=2.437 GHz Access Point: A8:39:44:54:A1:44
[COLOR="#FF0000"]Bit Rate=117 Mb/s[/COLOR]
RTS thrff Fragment thrff
Link Quality=72/100 Signal level:-63 dBm Noise level:-68 dBm
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0
Lots of Linux drivers (most??) are troubled with N speeds. Is the behavior improved at all if you set your router to use B and G only? Are there any interesting clues here?```
dmesg | grep rt5
```

---

### Post by peterthinking on 2013-04-01
here is the output from dmesg

[CODE]input/input0
**Edit, output not needed for solution.

the command grep rt5 seems to do nothing

---

### Post by peterthinking on 2013-04-01
I really dont have messing with the router itself as an option, too many folks using it for me to screw that up.
However I can say this card will connect to it, but only in windows on the other drive.

***NOTE*

the output from dmesg seems longer than what I can display on the terminal, the top part is missing in the output pasted here.

---

### Post by peterthinking on 2013-04-01
here is the output again, this is right after startup with only the wireless card hooked up and nothing running except the terminal.

Edit, output not needed for solve.

---

### Post by wildmanne39 on 2013-04-01
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by peterthinking on 2013-04-02
Problem solved,  Normally I would just slap myself and call myself stupid but hoping it helps someone else I'll share the solution.

The ASUS PCE-N53 Dual-Band Wireless-N600 PCI-E Adapter Has a SMALL BLACK BUTTON on the back of the card. Push the WPS Button on the router first, then press this tiny black button on the card (right between the lights and the first antenna).  This lets the router know that this is the wireless you are trying to hook into.

This button is not shown in the documentation in the box and since I was doing linux work I didn't read the windows instructions.

You still have to jump thru hoops to install the driver but I won't try to tackle that here.

Thanks for the help, sorry I pulled a brain fart there.

---

