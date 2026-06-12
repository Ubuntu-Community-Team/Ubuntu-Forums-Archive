---
title: "CUPS &amp; Windows printing"
date: 2009-09-20
forum: Networking &amp; Wireless
---

### Post by cowboy_mcd74 on 2009-09-20
I have a printer hooked up to my ubuntu 9.04 desktop. I can print, no problem, from the desktop. I've shared it over my network, and can view it from my laptop running Windows, both in an explorer window, and by connecting to the CUPS browser page. 

I cannot, however, print to the printer. If I add it through Windows Explorer (by browsing to \\server\printers and clicking on the printer), and try to print to it, nothing happens. If I try to add the printer manually (by going to add printer->network printer->and type in 'http://server:631/printers/printername'), it cannot find it. But, if I type in 'http://server:631/printers/printername' into the browser, it displays the printer's page.

Anyone else have this problem? Or know of any ideas on how to solve it? Thanks.

---

### Post by khelben1979 on 2009-09-20
Give us the exact model of the printer. Also, are you trying to print pages through Wine or what do you mean?

---

### Post by cowboy_mcd74 on 2009-09-20
sorry, yeah, I should have made it more clear.

It's an HP Officejet 4200. It's connected to a desktop running Ubuntu 9.04. I and my roommates have laptops that we use, each of which run Windows. All of them are connected over a wireless network.

I can connect to the desktop, view the printer, even connect to the printer (using windows explorer), but cannot print to it. If I try to use the 'add printer' wizard, it doesn't even detect the printer. But I can bring up a browser on my laptop and view the printer's CUPS page.

Do you need any other information?

---

### Post by jonallport on 2009-09-20
I seem to remember something like you need the .printer in the URL for Windoze, CUPS to CUPS seems to know that this is implied.

That'd be:
[http://server:631/printers/printername/.printer](http://server:631/printers/printername/.printer)

---

### Post by cowboy_mcd74 on 2009-09-20
Thanks for the idea, but I tried that, and it still comes up with the same error that Windows can't find the printer...

---

### Post by cowboy_mcd74 on 2009-09-20
Nevermind! I figured it out. It didn't occur to me right away cause XP's firewall sucks, but the newer Windows versions block outgoing connections. Windows wouldn't let me connect to the printer!

Still couldn't find it by manually putting in the address, but now when I navigate to \\server\printers I can connect to it and print to it =D

---

