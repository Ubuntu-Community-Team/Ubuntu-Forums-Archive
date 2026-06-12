---
title: "how to trouble shoot USR 5610 modem"
date: 2006-06-26
forum: Networking &amp; Wireless
---

### Post by wordamus on 2006-06-26
I have downloaded and installed successfully Ubuntu 6.06. Being a first time ubuntu user I think everything is working fine except my modems. I have two USR 5610 performance pro modems in my box. Ubuntu sees neither of them. Device manager does. There they are listed as /dev/ttys4 and 5. I tried those settings in the network box but no go. Auto detect will not find either modem. The modems work both in windows and red hat 7.2 or is it 3. I am not at home but the modems did work in red hat. What do I do now?

wordamus

---

### Post by zxee on 2006-06-27
These are pci slot modems? I don't know but maybe this USR model is a winmodem i.e. a controllerless modem that relies on windows to operate. There are drivers in linux for some winmodems hence the functioning with redhat. If it worked in RH you should be able to get it working in ubuntu. Go to [http://linmodems.org/](http://linmodems.org/) download the scanmodem tool and follow their guide(s).

---

### Post by stlscriptmeister on 2006-09-22
I am very glad that I found your post, because I was about to run out and purchase a USR 5610 modem myself!

By the way, have you checked out these URLs:

[www.tldp.org/HOWTO/Hardware-HOWTO/](www.tldp.org/HOWTO/Hardware-HOWTO/)
[www.linuxcompatible.org/](www.linuxcompatible.org/)

Also, you might need to do a "setserial" command to point (link) your modem's actual com# to one of the "recognized" com#s (tty0 thru tty3). I remember seeing something about that in one of the online doc files...

...can't remember which one it was!     :(

---

### Post by stlscriptmeister on 2006-09-22
Oh yes,...

USR 5610 PCI modems are supposed to be "real" ("hardware" or "controller-based") modems. Would probably work fine in Ubuntu 5.10 or some other linux distro. Ubuntu 6.06 (Dapper Drake) has issues with dialup modems! Do a search on "dialup modem" in this forum and I think you will see what I"m talking about.

Good luck!     ;)

---

### Post by PHLAKcede on 2006-10-07
Hi 

I've been playing with the same usr5610 modem project. I also saw the "setserial" reference that you mentioned and I'm quoteing it below here.  
Let me know if it works for you.
=====================================================================
Boot up in Linux after the card has been installed and the  Windows 
initialization has occured.

In a terminal window, type

cat /proc/pci

Scroll down until you find the data for the serial controller. The response should looked like:

-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*
Bus  0, device  15, function  0:
    Serial controller: Unknown vendor Unknown device (rev 1).
      Vendor id=12b9. Device id=1008.
      Medium devsel.  IRQ 10.  
      I/O at 0x1890 [0x1891].

-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*


Make a note of the values for IRQ and I/O port. In my case they were 
10 and 0x1890 respectively.

Then in the terminal window type

setserial /dev/ttyS1 irq 10 port 0x1890 autoconfig 
==================================================================

Good Luck

---

### Post by sp4rd on 2006-10-08
These are pci hardware modems and they work with Ubuntu 6.06.1 (Dapper Drake).  Just follow the instructions PHLAKcede posted and you should be good to go.  You might want to test if you got it setup right by running
sudo wvdialconf
in a terminal.  If your setserial commands are correct wvdial should pickup your serial port and configure all the AT command settings for you.  Try the gnome-ppp package too if you decide to use wvdial.  I have 2 of these modems and they work well in Dapper and debian.

---

