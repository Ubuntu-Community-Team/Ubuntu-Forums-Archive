---
title: "Can't setup network printer"
date: 2011-10-13
forum: Networking &amp; Wireless
---

### Post by MonocleMike2 on 2011-10-13
Ubuntu 11.04 with Classic interface.

I've added a newly built machine to my system.  In admin/printers I selected cups whereupon it "discovered" the printer however nothing gets through to it.  The job goes into the local print queue on the client but gets no further.
The print server appears to be ok as a different client machine that is using its IP address rather than its name can print to it ok.

What have I omitted to do?

---

### Post by kurt18947 on 2011-10-13
I've had good luck using this. I'm going from memory - using 11.10 & Gnome-Shell now - System -> Administration -> Printing -> Right click the printer icon, click "properties", find "Device URI". In the device URI box type: "socket://xxx.xxx.xxx.xxx" where "x"= i.p. address. The caveat here is I think that the printer must have a static i.p. address assigned. On Brother printers this is accomplished via the onboard control panel. If you're unable to assign a static i.p. to your printer I'm not sure this would work.

---

### Post by MonocleMike2 on 2011-10-13
Thank you very much for your help.  The printer is attached to my laptop USB which roams and so does not always get the same IP address from the ADSL router via WiFi.  I have one client working by editing in the current IP address but what I am trying to achieve is that the client uses the laptop's name rather than its IP address.  It is obviously nearly working because the client "discovers" it.

---

### Post by kurt18947 on 2011-10-13
Ah, the printer is plugged into the PC.  I have my networked printers attached to the router, 1 via an ethernet cable and one via WiFi.  I have no (recent) experience networking a printer attached to a PC.  I tried it years ago with Win98 I think and it didn't work well at all, of course that was Win98.  Perhaps someone with recent experience can help out.

---

