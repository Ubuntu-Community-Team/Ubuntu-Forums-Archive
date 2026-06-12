---
title: "Internet printing"
date: 2010-12-28
forum: Networking &amp; Wireless
---

### Post by riseringseeker on 2010-12-28
I have been able (with some hair pulling and gnashing of teeth) to print from outside the LAN to the printer connected via USB to the desktop computer at home, until the last upgrade.

The laptop will forst say the printer may not be connected, but eventually (usually) after a while says the job was sent to the printer.

The log files on the desktop - serving as the printer server have an error message in cups/error_log that I am not familiar with, and don't believe I have seen before.  I am sure if I could decipher that error and figure out how to change the behavior to get rid of it, it would once again work.

Printing from within the LAN is a no-brainer as it has been for the last several releases.

The error that I get when trying to print outside the LAN (via the internet) is:

cupsdAcceptClient: 12 from <WAN IP>:631 (IPv4)
Unable to encrypt connection from <WAN IP> - GnuTLS internal error.

Apparently I am missing something as far as authentication from the laptop to the desktop, but googling for hours gives me no clue how to fix it. 

Any ideas?

---

### Post by riseringseeker on 2010-12-30
Bump

---

