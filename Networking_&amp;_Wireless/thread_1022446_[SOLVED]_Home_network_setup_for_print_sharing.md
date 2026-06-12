---
title: "[SOLVED] Home network setup for print sharing"
date: 2008-12-26
forum: Networking &amp; Wireless
---

### Post by relambert on 2008-12-26
Hello all,

I've got a question about my home network. I'm have one pc that's running Linux Mint that is hard wired to my router. The other pc is one running Hardy Heron that connects via  wireless. Both machines will access the internet. I can also ping one computer from the other with no apparant issues. The problem is, I can't see the other computer if I look at the network. Is there something else I have to do set up a network? I'm wanting to share a printer that's connected to one of the boxes.

---

### Post by AlexBellisBrown on 2008-12-26
Your computers dont emit a SSID because they are not access points, they are just computers. You would need to set up an ad-hoc network in order to get them to "talk" to eachother, however you should be able to send files between them via the router. 

Also, what make and model is the printer?

---

### Post by relambert on 2008-12-26
Thanks for the reply. Although I'm not quite sure what all of it meant. The printer is an HP deskjet 5550. Most of my networking experience, what little there is,  has been with Windows, and I'm not sure how to set up an ad-hoc network. I'll try to find some info on that procedure, but if you could explain, that would be a big help.
Thanks again.

---

### Post by AlexBellisBrown on 2008-12-26
Well basically a ad-hoc network means you have for instance, 2 computers, and a router, but the second computer is too far away from the router, and has no signal, thus, you change the computer in the middle to be a ad-hoc network, make it act like a router, or an "access point".

Now i gather you want to print with both computers off that one printer. How do you have the printer already connected? Via Wifi already? It says above you have "it connected to one of the boxes"....

Also, well done for buying HP, very Linux friendly :)

---

### Post by relambert on 2008-12-26
Yes, I want to print from both printers. It's connected to the parallel port of the box that's hard wired to the router. It is not set up wireless.

---

### Post by superprash2003 on 2008-12-26
you could do this via samba.. connect the printer to one pc and share it over samba.. hope this helps
1)samba setup - [http://www.prash-babu.com/2008/05/how-to-setup-samba-in-linux.html](http://www.prash-babu.com/2008/05/how-to-setup-samba-in-linux.html)
2)printer sharing  - [http://www.prash-babu.com/2008/05/how-to-setup-network-printer-or-share.html](http://www.prash-babu.com/2008/05/how-to-setup-network-printer-or-share.html)

---

### Post by relambert on 2008-12-27
Thanks for the input. I think I've gotten samba set up on one pc so far, ( the one that has the printer connected to it). I'm assuming that I have to enable samba on both computers on the network? I started the tutorial on printer sharing and I see a difference in the part about "print cup" compared to what came up on my computer. This is what the instructions read

Step 1: Go to the terminal(Applications->Accessories->Terminal) and type sudo gedit /etc/samba/smb.conf
Step 2: TextEditor should open with the smb.conf file. now find the following lines

# printing = cups
# printcap name = cups


and replace them with

printing = cups
printcap name = cups

You are basically uncommenting the two lines , i.e. removing the #

This is what mine reads

# If you want to automatically load your printer list rather
# than setting them up individually then you'll need this
#   load printers = yes

# lpr(ng) printing. You may wish to override the location of the
# printcap file
;   printing = bsd
;   printcap name = /etc/printcap

# CUPS printing.  See also the cupsaddsmb(8) manpage in the
# cupsys-client package.
;   printing = cups
;   printcap name = cups

Notice the semi colons instead of the number symbol.
Also, the client setup part of that talks about adding printer in Windows. Is this step the same if I'm doing it in Ubuntu?

---

### Post by relambert on 2008-12-27
Wanted to update this post. Have now run samba on both computers. Wireless computer recognised the network, (other pc was booted into Windows at the time), half way home:P. I'm still unclear as how to add the printer to the wireless pc. 
So do I need to remove the semi colons from
; printing = cups
; printcap name = cups
and leave them blank as the instructions state, or am I looking at the wrong entry?

---

### Post by relambert on 2008-12-27
OK, I've found and added the printer off the network to the pc. I've loaded the drivers and it appears to be installed correctly, but it won't print a test page!?

---

### Post by relambert on 2008-12-28
Now have Linux Mint on  both computers and all networking issues are resolved. I must say, even though this distro is Ubuntu underneath, it seems to be easier to work with for noobs like myself.

---

