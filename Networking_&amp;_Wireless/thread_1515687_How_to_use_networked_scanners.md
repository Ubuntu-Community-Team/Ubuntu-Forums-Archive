---
title: "How to use networked scanners?"
date: 2010-06-22
forum: Networking &amp; Wireless
---

### Post by jgaines on 2010-06-22
I have a networked all-in-one copier/printer/scanner (Epson TX550W).

Printing works fine via CUPS - just point at the IP address of the Epson.

How can I get scanning to work over the network?  The scanner is not hooked up to any computer whatsoever, so I can't (AFAIK) use the sane daemon.

I've thought of using an SSH tunnel to trick sane (either client or server) into thinking the scanner's actually connected to localhost, but I'm under the impression that sane doesn't use TCP to communicate with the scanner.

Any suggestions?

---

### Post by desertdog on 2010-06-24
Epson linux drivers:
[http://avasys.jp/eng/linux_driver/](http://avasys.jp/eng/linux_driver/)

How to set up network scanner:
[http://penguin-breeder.org/sane/saned/](http://penguin-breeder.org/sane/saned/)

---

### Post by jgaines on 2010-06-24
Thanks for your reply desertdog.  In the end it solved my problem.

The sane link seems to confirm that sane is for making a scanner *connected to a computer* available to other computers on the network.  This excerpt for instance:

"make sure user and group saned exist and they have appropriate access rights to your SCSI, parallel port, and USB devices. If your scanner is attached to /dev/sga for example"

I interpret as meaning that the scanner needs to be hooked up to a port on the computer that is running sane.

My case, however, is different.  The scanner is *not connected to any computer*; it's a standalone device on my network.

Your second link bore fruit.  From there I found [this page]("http://avasys.jp/eng/linux_driver/faq/id000652.php") with detailed instructions on what to do.

For the record:

1.  Install the iscan and iscan-network-nt packages from avasys (link from the above page).  (Note there is at least one non-free part to this install).

2.  Edit /etc/sane.d/epkowa.conf to add the IP address of your scanner.

3.  Run iscan from the command line or Xsane Image Scanner from the menu.

And that's it!

Thanks very much.

---

