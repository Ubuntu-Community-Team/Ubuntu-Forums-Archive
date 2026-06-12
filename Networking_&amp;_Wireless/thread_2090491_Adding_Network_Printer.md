---
title: "Adding Network Printer"
date: 2012-12-02
forum: Networking &amp; Wireless
---

### Post by Orcris on 2012-12-02
I have a printer on my Windows workgroup that I want to be able to print from. I went in the printers section, but there are only options for local printers. I have SAMBA configured and working, so how do I add a network printer?

---

### Post by Hadaka on 2012-12-02
Hi, try this
[http://askubuntu.com/questions/153517/ubuntu-12-04-network-printing-through-windows-samba-server](http://askubuntu.com/questions/153517/ubuntu-12-04-network-printing-through-windows-samba-server)

---

### Post by SeijiSensei on 2012-12-02
I always find it easier to configure printers through the CUPS web interface.  Open a browser and point to [http://localhost:631/](http://localhost:631/).  You'll be prompted to log in if you execute a task that requires root privileges like installing a printer.

---

