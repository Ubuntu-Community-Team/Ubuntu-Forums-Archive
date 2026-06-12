---
title: "Serial connections don't work"
date: 2013-01-20
forum: Networking &amp; Wireless
---

### Post by RogerDavis on 2013-01-20
This problem  has been recognized as a bug ( [https://bugs.launchpad.net/ubuntu/+bug/1087519](https://bugs.launchpad.net/ubuntu/+bug/1087519) ), but it is unassigned, and there is NO apparent action on it.

If no one has any power to get this assigned to someone to fix it, maybe someone has an idea of how I can work around it?  A patch?  Some other way to override the system and make it work?  ANYTHING?!?

---

### Post by gordintoronto on 2013-01-20
What makes you believe the serial port is on IRQ 17? Decimal or hex?

BTW, a 16550 is a normal serial port, unless one is stuck in the 1980s.

Does the modem have switches you could flip to put it on ttyS1 or ttyS2?

---

### Post by RogerDavis on 2013-01-21
"What makes you believe the serial port is on IRQ 17? Decimal or hex?"

Modem info:
description: Serial controller product: 56K FaxModem Model 5610
vendor: 3Com Corp, Modem Division
physical id: 1 bus info: pci@0000:04:01.0
version: 01 width: 32 bits clock: 33MHz
capabilities: pm 16550 cap_list
configuration: driver=serial latency=0
resources: irq:17 ioport:d000(size=8 )
-----------------------------------------------
I know the 16550 is a normal serial port, it is built into the modem.  There are no switches.  This is an INTERNAL modem, and NOT a winmodem.    Please see [http://www.usr.com/support/product-template.asp?prod=5610c](http://www.usr.com/support/product-template.asp?prod=5610c) , [http://www.usr.com/products/modem/modem-product.asp?type=specs&sku=USR5610C](http://www.usr.com/products/modem/modem-product.asp?type=specs&sku=USR5610C), and  [http://www.usr.com/products/modem/modem-product.asp?sku=USR5610c](http://www.usr.com/products/modem/modem-product.asp?sku=USR5610c)  for  modem info.

---

### Post by gordintoronto on 2013-01-21
This might get you somewhere:
[http://ubuntuforums.org/showthread.php?t=1200996](http://ubuntuforums.org/showthread.php?t=1200996)

Once upon a time I was a modem master, but it's been nine years. Even internal modems often had switches in those days.

Wow, I went to the 3Com (U.S. Robotics) web site, and grabbed the manual. It had instructions for installing the modem in Windows 95 and Windows 98.

Do you want Internet via dial-up, or the ability to send and receive faxes?

---

### Post by RogerDavis on 2013-01-22
Yeah, times have changed.  I used to run a BBS of of modems, wrote some of my own code, especially the modem handling stuff.  

The USR site cites compatibility with everything from 95 ~ Windoze 8 to Linux.

What I want now is (in order) :
- Send and receive faxes - this is the big one
- Backup internet connection
- Be able to work with modems in my Linux system for fun and a few practical things, like maybe dialers
- Want things to work like they are supposed to

Thanks!

---

