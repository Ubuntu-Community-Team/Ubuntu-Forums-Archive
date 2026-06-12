---
title: "Printer Sharing"
date: 2009-05-11
forum: Networking &amp; Wireless
---

### Post by D-meist on 2009-05-11
Need some help setting up a network printer.  My HP is hooked up to my main machine running Windows 7 RC1.  My ubuntu laptop 9.04 can see my network shares via samba.  But when I try to browse for my printer which is shared it says There were no print shares found.  Please check that the Samba service is marked as trusted in your firewall configuration.

To do this, select System->Administration->Firewall from the main menu.

Of course there is no "Firewall" option in the menu at all.  Any ideas?

-Daniel

---

### Post by Sader on 2009-05-12
I second this.
Not sure how to resolve the issue without CLI

---

### Post by chili555 on 2009-05-12
I assume you both want to do more than 'browse' or 'see' your network printer; I assume you want to print. Did you try to set it up with System -> Administration -> Printing -> New Printer -> Network Printer -> Windows Printer via SAMBA?

---

