---
title: "CUPS Server, Windows Woes"
date: 2011-10-07
forum: Networking &amp; Wireless
---

### Post by lethallines on 2011-10-07
Okay, so I've got CUPS set up to print to the local Brother HL-2140 connected via USB.  Great!

I can print from the server that is hosting the printer.

I can see the printer from my wireless Windows laptop, I can print to the printer.

SOMETIMES I go to print something on the laptop and the printer just isn't there.  I can access Samba shares on the server machine, but my printer doesn't show up at all.  

FURTHERMORE when I AM able to see the printer, I look in the job queue and there is every document I've ever printed.  I have tried removing the jobs from the spooler --> /var/spool/cups, but to no avail.

WHAT is going on? Can someone at the very least tell me how to clear the job queue?! It says it is clear when viewed from the server, but not from the clients.

---

### Post by drdos2006 on 2011-10-07
When you type [http://localhost:631](http://localhost:631)  in your browser, can you see the printer queue name in the Printers section ?

Which version of Ubuntu is hosting the printer ?

regards

---

