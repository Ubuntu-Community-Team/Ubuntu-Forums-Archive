---
title: "PXE and TFTP doenst work on 9.04"
date: 2009-06-26
forum: Networking &amp; Wireless
---

### Post by ronnys on 2009-06-26
Hi!
Im trying to set up a Fog-server on Ubuntu 9.04 Desktop 64bits

Everything seems fine, but i cant do PXE-boot from this.
Fog set up TFTP (tftpd-hpa) and it works local on Ubuntu.

I test this localy:
#>tftp <ip-address or localhost>
#>binary OK
#>verbose OK
#>get pxelinux.0 OK! File is received and stored.

If i try this from network then it fails:
#>tftp <ip-address> OK
#>binary OK
#>verbose OK
#>get pxelinux.0 Not-ok! Time-out!

I sit on the same subnet and same switch. I tried portscan and only Apache2 port80 and ftp port21 shows up. Tftp listen to UDP 69

Since Ubuntu doesnt have any default active firewall or iptable, then there is nothing that can block tftp. So what can be wrong?

---

