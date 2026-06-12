---
title: "How to printer wirelessly"
date: 2008-12-08
forum: Networking &amp; Wireless
---

### Post by dmroberson on 2008-12-08
I've got a Lexmark X7675 4-in-1 printer, and it has wireless built in.  It is connected, via wireless, to my Linksys wireless router.  

I've got Ubuntu 8.10 on my notebook, and am trying to print to that printer, over the network.  How do I do this?  Thanks.

---

### Post by felker2 on 2008-12-08
The Lexmark has no Linux from Lexmark, and little open source support. I guess you didn't consult this information *before* buying the printer? ;-)

Question: is the printer already operational for / from Windows computers? If so, the printer is configured and indeed connected to the network.

According to [http://support.lexmark.com/perl/support/support.cgi?ccs=229:1:0:111:0:0&docid=enus26160](http://support.lexmark.com/perl/support/support.cgi?ccs=229:1:0:111:0:0&docid=enus26160) you access the printer via the webinterface. According to [http://support.lexmark.com/perl/support/support.cgi?ccs=229:1:0:111:0:0&docid=ENUS26004](http://support.lexmark.com/perl/support/support.cgi?ccs=229:1:0:111:0:0&docid=ENUS26004) , you can find the printer's IP address via the menu of the printer. 

So:
Can you find the IP address? 
Can you access the printer via your webbrowser using that IP address?

---

### Post by dmroberson on 2008-12-08
Yes, the printer is operational.  It's on the network, and has a valid IP.

I can find the IP address, and access the IP from my browser.

---

### Post by felker2 on 2008-12-09
Can you access the printer via webinterface http://<hostname>:631/printers/ too? Can you click to something like http://<hostname>:631/printers/<printername> ?

Can you see the printer in the Windows network environment as a windows shared printer?

If you add the printer to a (2nd, 3rd, 4th) Windows computer, can you do that without installing software on the Windows computer? So just by going into Control Panel / Add Printer etc? If so, do you know the URL / UNC of the printer?

Can you connect the printer directly to your Linux system (via USB?)? If so, can you print?

OK, now back to Linux printing via the network: SYstem -> Administration -> Printing. Click New. Then try the last three options: LPD/LPR, Windows Printer and Other. Yes, you will need the URL / UNC here. Use the information you found out earlier. 
If your exact model is not available, choose something close or generic.

Post the results back here.

---

### Post by spegru on 2009-01-12
bump

---

