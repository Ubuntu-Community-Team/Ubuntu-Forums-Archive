---
title: "Sharing Zebra - Configuration"
date: 2010-09-29
forum: Networking &amp; Wireless
---

### Post by ftanguay on 2010-09-29
Hello,
 
I have a Zebra TLP 2844 Printer installed on Ubuntu 10.04. Locally, everything is fine. But what I'm trying to do is to be able to print to the printer from a Windows OS.
 
I have install CUPS and SAMBA. I can see and connect the printer by typing [\\mylinux\myprinter]("file://\\mylinux\myprinter") etc.. but the result on the label is not what I'm expecting.
 
Even from a simple test file from notepad, the label is printed with code like :
 
I8, A 001
 
Q406, 024
q831
rN
S4
.....
 
Is anyone have an idea why it is doing this ?

---

### Post by otter9099 on 2010-09-29
Could you please detail how you were able to get your zebra printer working under ubuntu 10.04. I have searched tried everything with no luck at all.

Thank you in advance

---

### Post by ftanguay on 2010-09-30
With CUPS, I have use the zebraep2.ppd driver located here:
 
[http://www.opensource.apple.com/source/cups/cups-136/cups/ppd/](http://www.opensource.apple.com/source/cups/cups-136/cups/ppd/)

---

### Post by christopher.ellis on 2010-10-06
I have had partial success setting up a Zebra TLP 2844 on Ubuntu 10.04.

- Used the zebra2.ppd for CUPS (as from the link you suggested)
- Added the line "application/vnd.cups-raw priority(1000) string(0,"*PB USB001")" to the /etc/cups/raw.types file
- Successfully printed Ubuntu test page

BUT

Can NOT for the life of me send the printer a *.prn file (text fille essentially) with EPL comands to create the barcode/text that WORKS from Windows (although NOT from within VirtualBox curiously..)

The printer simply feeds out two blank labels.

---

### Post by christopher.ellis on 2010-10-06
Correction. The printer prints our the raw text of the file (ie NOT the formatted barcode/text). :(

---

### Post by heryatmadja on 2011-05-12
ftanguay,

Any luck in resolving the remote printing to Zebra?

---

### Post by ftanguay on 2011-05-14
Sorry, no luck for this one. I never been able to solve this problem. I have use a DLINK print server (USB and ethernet) to attach the zebra printer to the network and shared it to another computer on Windows OS.
 
So the Ubuntu computer is printing using the share and it's OKAY.

---

