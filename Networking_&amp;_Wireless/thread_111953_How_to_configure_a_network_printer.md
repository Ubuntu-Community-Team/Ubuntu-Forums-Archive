---
title: "How to configure a network printer?"
date: 2006-01-03
forum: Networking &amp; Wireless
---

### Post by semaj on 2006-01-03
I have a MS windows network, which includes a Kyocera Mita printer KM2530, and I am trying to add it as a printer for use with Ubuntu.  I have given it a fixed IP address.  CUPS seems to want something other than the IP address to talk to it.  Guides I have found mention somehow registering it in etc/hosts, but I'm lost - can someone help me here?

thanks:confused:

---

### Post by mips on 2006-01-03
[http://www.linuxprinting.org/](http://www.linuxprinting.org/)
[http://mywebpages.comcast.net/heretrythis/hp3100/](http://mywebpages.comcast.net/heretrythis/hp3100/)
[http://www.linuxprinting.org/indexdoc.html](http://www.linuxprinting.org/indexdoc.html)
[http://www.linuxprinting.org/cups-faq.html](http://www.linuxprinting.org/cups-faq.html)

[http://ubuntuforums.org/showthread.php?t=106990](http://ubuntuforums.org/showthread.php?t=106990)
[http://ubuntuforums.org/showthread.php?t=92730](http://ubuntuforums.org/showthread.php?t=92730)
[http://ubuntuforums.org/showthread.php?t=108215](http://ubuntuforums.org/showthread.php?t=108215)

This should keep you busy for a while and solve your problem I hope.

---

### Post by semaj on 2006-01-03
Thanks for these, but they all seem to relate to a printer hanging off another computer.  My printer hangs of the network hub which also has a modem router attached that I use to connect to the internet.

This printer is used by 5 computers on the network (all windows machines including my new dual boot machine on which I am trialling Ubuntu)

[QUOTE=mips][http://www.linuxprinting.org/](http://www.linuxprinting.org/)
[http://mywebpages.comcast.net/heretrythis/hp3100/](http://mywebpages.comcast.net/heretrythis/hp3100/)
[http://www.linuxprinting.org/indexdoc.html](http://www.linuxprinting.org/indexdoc.html)
[http://www.linuxprinting.org/cups-faq.html](http://www.linuxprinting.org/cups-faq.html)

[http://ubuntuforums.org/showthread.php?t=106990](http://ubuntuforums.org/showthread.php?t=106990)
[http://ubuntuforums.org/showthread.php?t=92730](http://ubuntuforums.org/showthread.php?t=92730)
[http://ubuntuforums.org/showthread.php?t=108215](http://ubuntuforums.org/showthread.php?t=108215)

This should keep you busy for a while and solve your problem I hope.[/QUOTE]

In windows, the printer connection is via an IP port on each windows machine.  The printer has a static IP address - works like a dream!

I'm going nowhere with Ubuntu if I cant print (sorry)!

Very grateful for any help.

---

### Post by semaj on 2006-01-04
Problem solved!
Using System>Administration>Printing, Add printer, I selected network printer, then UNIX printer (LPD), then entered the static IP address that I'd assigned to the printer, left the queue field blank.  The driver came from Kyocera installation disk.

I just hadn't found any documentation about which 'backend' to use, or what syntax /  or information to insert into the required fields, so it was a case of experimentation.

Hope this will.  Should this go into the user guide?

---

