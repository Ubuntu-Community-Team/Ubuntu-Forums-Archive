---
title: "Non-HP LAN Printing"
date: 2006-06-13
forum: Networking &amp; Wireless
---

### Post by Tonren on 2006-06-13
Hey guys.  I have an Epson Stylus Color 740 plugged into my SMC Barricade G Wireless Router's USB print server.  My Windows XP boxes successfully connect and print to this printer using the following configuration:

Printer Type: **Local** (NOT network)
Port Type: **Standard TCP/IP Port**
Port Name: IP_192.168.2.1 (this seems to be inconsequential)
Printer Name or IP Address: 192.168.2.1
Protocol: LPR (as opposed to "Raw")
LPR Settings - Queue Name: LPT1

I have enabled "Detect LAN Printers" in my global printer settings, and I've screwed around with cupsd.conf but to no avail.  When I use the Add Printer Wizard and select "Local Printer", the only port I'm allowed to "specify" is "hp no_device_found", which obviously isn't what I want.

I think the problem here is that this printer is connected to a Wireless router, **NOT** a Windows XP box.  I can't connect to it using SMB for that reason.  Even if it WAS on a Windows XP box, it's still a LAN printer, **not** a network printer.  However, Ubuntu will not detect it!

I feel like the solution lies in cupsd.conf, but I don't know what to do with it.  I've been Googling, searching the forums and asking in #ubuntu for three hours.  Can anyone help?

---

### Post by johnc4510 on 2006-06-13
I think if you click on forward when you get the "hp no_device_found", the next screen will allow you to choose a printer. Just click on the drop down bar and select the manufacturer. This will bring up all the printers Ubuntu has supported for that manufacturer. IE Epson or whoever.

---

### Post by Tonren on 2006-06-13
John - Clicking forward with "hp no_device_found" doesn't generate an error message, but it still won't print.  The client hangs on "Printing 1 job", and the printer (which I'm sitting right next to) doesn't even flinch.  I'm pretty sure that the solution is to somehow specify the port it should be searching in.

---

### Post by johnc4510 on 2006-06-13
Well, I do know that cups, which I don't use, accesses through port 631. Here is a web site for printing with Linux:
[http://www.linuxprinting.org/](http://www.linuxprinting.org/)
Maybe that will help.

---

### Post by ali_bongos_dad on 2006-06-13
I had similar problems some time ago with Hoary and an SMC wireless printer with USB port. The way I connected to the printer was 

System > Administration > Printing
Select New Printer
Select Network Printer in the Add Printer window
Scroll to UNIX Printer (LPD)
in Host: type 192.168.2.1
in Queue: type lpt1
Press Forward and select your printer details.

---

### Post by Tonren on 2006-06-13
ali - 

I had already written off that suggestion because I had tried reconfiguring the printer to work that way before, after creating it initially.  On a whim I decided to try it that way from the start... and it worked!

It's worth mentioning that there's (eerily) no "Apply" or "OK" button in the Printer Properties window; only Close and Print Test Page.  It wasn't actually applying my changes when I altered the printer's properties.

---

