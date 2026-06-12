---
title: "newbie w/ a wireless problem"
date: 2006-06-21
forum: Networking &amp; Wireless
---

### Post by tunads on 2006-06-21
I've can't seem to connect to my wireless lan using ubuntu.  I have also tried to connect to public lans and that has not worked as well.  the first thing i tried is in thread 185174, How to: Broadcom Wireless cards without Ndiswrapper.  It seemed like the install went ok, but I still can't get a connection.  Did I install the wrong software?

in thread 185174 it says to type this into the terminal to see if you have a Broadcom wireless card:

lspci | grep Broadcom\ Corporation

when I do this, it returns the following:

0000:05:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

I don't know if this unveils a problem or not, I just though it would be helpful :-)

thanks for any help in advance, and remember that i'm a newbie, and I need things explained in simple language.

---

### Post by the slayer on 2006-06-21
Have u configurede ur network card?
System-administration-network
Try that and come back if it aitn work.

---

### Post by tunads on 2006-06-21
i'm not sure what your asking me to check, but the device is active and i have typed in the net id and my wep (64bit hex) password and set the configuation to DHCP (which is the way the router is set up).

---

### Post by the slayer on 2006-06-22
And nothing works?

Try turning, the wpa off, and then test again.

---

### Post by MarkSheely on 2006-06-23
Hi tunads,

Many people with a BCM4318 (myself included) have had a lot of success using the method laid out here:

[http://www.ubuntuforums.org/showthread.php?t=197102](http://www.ubuntuforums.org/showthread.php?t=197102)

My advice:  Read through the entire thread, and then try the method linked to above (preferably with a clean install, if that is at all possible).  

If it doesn't work, post in that thread - those using the same wireless card as you are doing their best to help each other out there.  If you post in this thread, people might not see it, and you may miss out on the help you need.  

Good luck, and feel free to contact me if I can be of help,
Mark 
[email]marksheely@gmail.com[/email]

---

