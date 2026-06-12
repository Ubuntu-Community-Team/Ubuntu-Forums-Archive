---
title: "LAN Printer setup"
date: 2010-10-20
forum: Networking &amp; Wireless
---

### Post by bill-lancaster on 2010-10-20
2 PCs, both running Ubuntu 10.10 and hard wired through a router.

The New Printer window has "Find Network Printer" option.  Have tried the remote computer's name and also its IP address.

The printer is "Shared" and works on the remote computer.

I only get "No Printer Was Found At that Address"

Can anyone help?

---

### Post by Morbius1 on 2010-10-20
You said that the printer has been marked "shared" but did you set it to be "published"?

Administration > Printing > Server > Settings > Check "Publish Shared Printers connected to this system"

And when you say yo tried to connect to it by ip address is this the format you used ( Select "Other" and enter in URI: ) :
[ipp://192.168.0.100:631/printers/Printer_Name]("http://192.168.1.2:631/printers/Printer_Name")

---

### Post by bill-lancaster on 2010-10-20
Thank you so much.  The "publishing" bit was new to me.

I also wasn't aware of the correct syntax for addressing the printer.

Then, having asked to have published printers shown - there it was!

Thanks again.

---

