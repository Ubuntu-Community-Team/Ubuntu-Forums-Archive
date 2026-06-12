---
title: "Trying to share a printer between 2 Linux machines"
date: 2011-01-07
forum: Networking &amp; Wireless
---

### Post by norm.h on 2011-01-07
Two machines, each running Ubuntu 10.10.
Desktop is wired to the router, and laptop is wireless.
Printer is an HP Photosmart C4400 All in One series, and is connected to the desktop via USB.Prints OK from desktop.
I have CUPS set up on both machines, and the laptop can see the printer.
Desktop firewall allows CUPS in on port 631.
Printer properties are set to enabled and shared
Desktop is set to publish printers, and laptop is set to show printers from other systems.
Fine until I try to print from laptop, when print job is shown as sent, but printer remains idle.
Another thing is that on the laptop, the "enabled" setting drops off.
I think this must be a configuration issue, but cannot find an answer anywhere.
File sharing using Nautilus works fine.

---

### Post by PatchesTheCaveman on 2011-01-07
What driver did you configure on the laptop?  You must choose the Generic > PostScript Printer driver on the laptop because CUPS on the desktop will use its driver to prepare the print job.  If you set the HP driver on both machines it will try and convert the print job twice and won't work.

---

### Post by norm.h on 2011-01-08
> **PatchesTheCaveman said:**
> What driver did you configure on the laptop?  You must choose the Generic > PostScript Printer driver on the laptop because CUPS on the desktop will use its driver to prepare the print job.  If you set the HP driver on both machines it will try and convert the print job twice and won't work.

Thanks for that.
In my ignorance, I did actually choose the HP driver, so will have to have a play, but possibly not till after the weekend.

---

### Post by chili555 on 2011-01-08
> **PatchesTheCaveman said:**
> What driver did you configure on the laptop?  You must choose the Generic > PostScript Printer driver on the laptop because CUPS on the desktop will use its driver to prepare the print job.  If you set the HP driver on both machines it will try and convert the print job twice and won't work.That's not my experience. Here is my perfectly operating setup. This is on my laptop. A desktop upstairs hosts the printer. As you can see, the printer is set up on the laptop with the actual printer drivers.

Is there something unique about HP printers?

---

### Post by norm.h on 2011-01-08
Yes, it all looks so simple, doesn't it?
My settings look similar, and I think for some reason the client isn't seeing the host.
Did you have to set anything in your firewall(s)?

---

### Post by chili555 on 2011-01-08
> **norm.h said:**
> Yes, it all looks so simple, doesn't it?
My settings look similar, and I think for some reason the client isn't seeing the host.
Did you have to set anything in your firewall(s)?Nothing special. Did you confirm the IP address of the host? Is it static or by guess and by golly? Are you using IPP? What does it say the printer state is? 'Idle' means, I believe, I can see you and I see you are ready to print.

---

### Post by norm.h on 2011-01-08
Will have to answer that tomorrow when I'm at home.
Many thanks for your interest

---

### Post by PatchesTheCaveman on 2011-01-08
Maybe it's not necessary for Linux->Linux printing.  I know it's necessary for Windows->Linux printing:
[http://www.owlfish.com/thoughts/winipp-cups-2003-07-20.html](http://www.owlfish.com/thoughts/winipp-cups-2003-07-20.html)

I've always done Linux printing that way too just out of habit, at least when I had a machine with a local printer so I couldn't just point */etc/cups/client.conf* at the server.

---

### Post by norm.h on 2011-01-09
Got it working OK.
Printed 2 test pages and 2 pages from Open Office.
I had already allowed 631 in through the desktop (host) firewall, so I allowed 631 in & out on the laptop (client) firewall. Don't really know if that mattered, but then IPP showed up, and hadn't before.
Beyond that, I just had several tries at adding the printer to the laptop. 
Thanks to all for your interest and suggestions.

---

### Post by norm.h on 2011-01-14
For anyone who may have been following this thread, this is what I've found:

All my previous checks had been done switching the desktop on after the laptop had been on for a couple of hours, which produced a time lag.

[i]**From CUPS on-line help**:

Automatic Configuration using CUPS Browsing

CUPS browsing works by periodically broadcasting information about printers that are being shared to client systems on the same subnet..... 

To configure printers on the same subnet, do nothing. Each client should see the available printers within 30 seconds automatically. 
[/i]
My server (desktop) and laptop (client) have the same subnet mask - 255.255.255.0

So for a change, and just to see if it made any difference, I switched the desktop on a couple of minutes before the laptop.
The laptop "saw" the printer almost immediately.

Solved, with thanks for the interest and help

---

