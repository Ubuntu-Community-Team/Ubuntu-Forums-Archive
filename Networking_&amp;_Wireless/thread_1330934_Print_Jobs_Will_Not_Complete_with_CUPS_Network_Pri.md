---
title: "Print Jobs Will Not Complete with CUPS Network Printer"
date: 2009-11-18
forum: Networking &amp; Wireless
---

### Post by dbsoundman on 2009-11-18
I have a HP Laserjet 1100 connected to an always-on server in my living room which, among other things, acts as the print server for that printer. I have 2 computers connected to the printer, one running Ubuntu 9.04 and the other running Windows Vista. The server runs Ubuntu 8.10. At first the server worked fine, but now the printer is having all sorts of problems. Mainly, when I print something, the little printer icon comes up on my computer, and then I get a message saying that the printer may not be connected. Eventually it prints, but only part of the document prints. For example, I was printing a 4 page PDF, and after several tries I only got up to 3.5 pages printed before it stopped printing. I finally got the document out by printing two pages at a time, but now the print status on my computer says the job is still processing even though it finished a while ago, and lpstat -p -d returns the same information. I have to cancel the print jobs, which then causes the printer to show an error, which basically means I have to press the front panel button which causes it to print some random information on the top of an otherwise blank page. Needless to say I'm wasting a lot of paper here. Can anyone help me diagnose and repair these problems? Any suggestions would be greatly appreciated.

-Dan

---

### Post by dbsoundman on 2009-11-18
This is the contents of the CUPS error log as accessed through the web interface:

```
E [18/Nov/2009:08:10:03 -0500] PID 26770 (/usr/lib/cups/backend/hp) crashed on signal 9!
E [18/Nov/2009:20:06:58 -0500] Cancel-Job: Unauthorized
E [18/Nov/2009:20:07:00 -0500] Cancel-Job: Unauthorized
E [18/Nov/2009:20:07:03 -0500] PID 18654 (/usr/lib/cups/filter/pstopdf) stopped with status 1!

```

I was doing most of my printing attempts around 20:00 this evening, for reference.

The other odd thing I noticed is that my roommate with the Vista machine is somehow configured to print to the printer via my computer - his print jobs show up with the IP 192.168.1.100, which is my computer. The server is 192.168.1.101. My computer used to be the print server, but isn't anymore. What setting do I need to change to get rid of this broadcast on my computer?

Thanks,
Dan

---

