---
title: "Adding a network printer with CUPS"
date: 2010-06-16
forum: Networking &amp; Wireless
---

### Post by NMFTM on 2010-06-16
I'm trying to add a network printer with CUPS instead of using the  Administration > Printing.

I did "**lpinfo -v**" and found  the printer on the network. It was:
"**network  dnssd://Canon%20MP500%20%40%20name%20of%E2%80%99s%20computer._ipp._tcp.local/cup**s".

So,  I entered the command: " **                                 lpadmin -p UpstairsPrinter -E -v //Canon%20MP500%20%40%20name%20of%E2%80%99s%20computer._ipp._tcp.local/cups**"

And all I got was: "lpadmin: File device URIs have been disabled! To enable, see the FileDevice directive in "/etc/cups/cupsd.conf".

I navigated to that config file. But I didn't see anything relating to FileDevice in there.

What am I doing wrong?

(obviously I changed the name of the computer to protect my privacy. It's running OSX, if that helps)

---

### Post by NMFTM on 2010-06-16
Never mind, apparently there is no FileDevice option in cupsd.conf. You have to add one yourself.

Source: [http://www.cups.org/documentation.php/ref-cupsd-conf.html](http://www.cups.org/documentation.php/ref-cupsd-conf.html)

---

