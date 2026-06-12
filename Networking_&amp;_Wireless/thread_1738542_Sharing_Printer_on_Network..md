---
title: "Sharing Printer on Network."
date: 2011-04-24
forum: Networking &amp; Wireless
---

### Post by _albino_ on 2011-04-24
Guys, is it possible to share my Printer on network. I have two versions of ubuntu, a 9.10 and 10.04. The Printer is installed at ubuntu 10.04 workstation. Well it is functioning properly.
My problem is when sharing the Printer to ubuntu 9.10. Is it possible to share it, the Printer, even if the versions of ubuntu is not the same??

I have tried the simple sharing of printer. However the version 9.10 could not detect the Printer on 10.04.
In addition to it. I Also installed HPlip toolbox and driver same thing happens the Printer was not detected on version 9.10.

My Printer Model is HP Laserjet P1102.

thanks.. gbu..

---

### Post by uncaspi on 2011-04-24
You must use cups. Open a browser window and type localhost:631 in the address bar. Now you are in cups GUI.Add the printer and use the 10.04 ip address i.e [http://192.168.0.100/hp](http://192.168.0.100/hp)
hp is the name you give your printer in the GUI.

---

### Post by _albino_ on 2011-04-24
I have also tried it. I configured the cups on the web browser. It has the same configuration on simple printer sharing, on system -> administration -> Printing

On my observation. It has the same configuration on the web browser. I also had the same output, the printer was not deteced on version 9.10.

Any other suggestion???
gbu.

---

### Post by _albino_ on 2011-04-24
I believe I overlooked some configuration. I will try your suggestion first. I will install the cups on the web browser, again. 
thanks...

---

### Post by _albino_ on 2011-05-03
Thanks for the help. I now can access my network printer...
God Bless and More Power...

---

