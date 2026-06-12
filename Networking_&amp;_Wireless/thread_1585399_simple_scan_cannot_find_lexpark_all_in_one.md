---
title: "simple scan cannot find lexpark all in one"
date: 2010-09-30
forum: Networking &amp; Wireless
---

### Post by windig on 2010-09-30
Hi,

I have UBUNTU 10.04 LTS- the Lucid Lynx and I am new to Ubuntu. I have a Lexmark interpret S405 all in one. I got it to work as a wireless printer with the downloads provided by Lexmark. I installed simple-scan (sane) to enable scanning. Simple scan works, since it sees another all in one printer in our house and is able to scan.  In addition, simple-scan does work on the Lexmark when I hook it up with a USB cable. HOWEVER, for some reason simple-scan does not see my Lexmark, despite the fact that it is seen as a wireless printer. So, the following discrepancy is present
a) My Lexmark is recognized by my computer as a wireless printer
b) Simple-scan does work, since it recognizes and scans another all in one and it does work with my Lexmark when connected with a USB cable
c) Nevertheless Simple-scan does not recognize my Lexmark all in one wirelessly.
My question to this distinguished form is: How can I make simple-scan recognize my Lexmark wireleslsy?

Willem

---

### Post by donlinux on 2010-09-30
I have the same issue.  I've tried setting ip address of the printer in xsane settings to the ip address as noted by the s405 but I still get wrong ip address specified.  When I set it up I got a "you have a firewall running which may not see printer.  Check your distro to see how to enable mdns"  but... i don't have a firewall running, unless it's the one my router has.
Edit:  After spending 3/4 of an hour with Lexmark tech support which was very polite but not too intelligent, they told me that the Lexmark Interpret S-405 wireless printer was certified for linux, but ONLY for wireless printing, not scanning or accessing memory cards or usb.  I even asked them about downloading their network-scan-linux-glibc2-x86.deb file to make it work and that it still wasn't working but they had no idea what that even was...
So... back to the store it goes as the scan function is not even close to my hp photosmart and if I have to have it wired, might as well have the good quality scanning.

---

### Post by adlerhn on 2010-11-04
Is still not possible to scan wirelessly in this printer from Linux, either with any kernel or firmware update? Maybe it is planned in the near future?

I am considering which All-In-One printer to buy, but I use Ubuntu as my main OS, so this could be a major drawback for buying this model.

---

### Post by adlerhn on 2010-11-04
windig: Are you able to scan directly from the printer to a memory card inserted in the printer, without using the computer at all?

---

### Post by adlerhn on 2010-11-08
I have contacted Lexmark Technical Support and this is the response I have got:

> Thank you for contacting Lexmark Technical Support. The Linux driver available for this printer will only work with wireless printing and scanning will work using USB connection. I'll pass on your concern to our development team who makes Linux driver for this printer. We have every desire to address your needs and provide the best solution available.

Maybe/hopefully in a few months there will exist a Lexmark Linux driver available that can scan over wifi?

---

