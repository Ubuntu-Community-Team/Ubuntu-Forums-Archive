---
title: "ethernet Printer and Wifi PC's problem"
date: 2013-06-22
forum: Networking &amp; Wireless
---

### Post by feardotcom on 2013-06-22
As the title says, i have a problem with my network. All of the PC's in my house are wifi, except 1. My printer is connected via RJ-45 CAT-5. the one computer that is not wifi is also connect RJ-45 CAT5. The pc that is wired has access to the printer, and is a ubuntu 12.04 machine. Laptop 1 is windows 8, laptop 2 is ubuntu 12.04, and desktop 1 with wifi is ubuntu 12.04, and desktop 2 with wifi is windows 7. None of the wifi computers can find the printer. How do i get it to work. I was thinking of setting up a file/print server to achieve this, because i read in a article somewhere that was the only solution, and i intend on setting a file server anyway.

Edit: Solved

---

### Post by scbingham on 2013-06-22
First of all it will help if you tell people what the make & model of your printer is.

Something needs to serve your printer & as you plan on building a file server anyway, it may as well be that. Probably slightly easier if it was directly connected to your file & print server but certainly not necessary.

---

### Post by feardotcom on 2013-06-22
It's been so long since we got it i dont really remember what model it is. It is made by HP, which isn't helpful, i know. It's like when someone says "well what kind of computer do you have" ... "ummm....a dell?"  :-P but i will have to look at it when i get home. I'm almost 100% positive i can connect it directly to said would-be server via usb. In the mean time till i get the model number... Is there a package of software specifically for a print server to install on, say, ubuntu server? or do i have to install some service? Whats the lowdown on print servers?

---

### Post by scbingham on 2013-06-22
You will need the printer model number so you can get the windoze & Ubuntu drivers. HP play nicely with Ubuntu.

I've never set up a print or file server but Ubuntu server is the way to go.

I setup a completely wireless scanner/printer, which was fun, by searching the forums for info; many have gone before you.

You will be better off asking specific questions in their own threads but do some searching first.

Have fun!

---

### Post by feardotcom on 2013-06-22
well see, thats the weird thing. Even in windows when you goto add printer and it searches the network for it, it doesn't show up. But on my desktop that is wired (dual boot with W7 and ubuntu 12.04) the windows partition sees the printer right off the bat.

---

### Post by scbingham on 2013-06-22
You would need to install CUPS (Common Unix Printing System) & drivers for your printer.

I haven't a clue about why your wired desktop can see your printer.

Here's info on CUPS:

[https://help.ubuntu.com/community/NetworkPrintingWithUbuntu](https://help.ubuntu.com/community/NetworkPrintingWithUbuntu)

---

### Post by SeijiSensei on 2013-06-22
You can use CUPS to communicate with the printer using HP's native "JetDirect" protocol.

On your Ubuntu computer, navigate with a browser to [http://localhost:631/](http://localhost:631/) and click the Administration button.  You'll be prompted for your username and password.  Then choose "Add Printer" and pick the "AppSocket/HP JetDirect" method.  

Windows should offer JetDirect support as well.

---

### Post by feardotcom on 2013-06-22
Now it working fine. I figured out my problem. It was DHCP. The printer was set up for my old network at a different home on a different router. This was before i went wireless. But, windows 8 and 7 was still a pain in the butt to install the drivers.

---

### Post by feardotcom on 2013-06-22
Now its working fine. I figured out my problem. It was DHCP. The printer was set up for my old network at a different home on a different router. This was before i went wireless. But, windows 8 and 7 was still a pain in the butt to install the drivers.

---

