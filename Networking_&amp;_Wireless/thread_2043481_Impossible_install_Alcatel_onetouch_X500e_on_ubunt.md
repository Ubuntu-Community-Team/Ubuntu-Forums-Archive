---
title: "Impossible install Alcatel onetouch X500e on ubuntu 12, maybe using Wine?"
date: 2012-08-16
forum: Networking &amp; Wireless
---

### Post by pierpier on 2012-08-16
Hi All,

I've just installed Ubuntu 12.04 on a partition of my macbook. I use an alcatel X500e usb modem to surf on the web with mac 10.5 and 10.6 but it doesn't work on Ubuntu 12.04.
If i launch sudo dmesg in terminal system detect it, so i filled ISP settings in network - mobile broadband section but I cannot surf on the web anyway.

Is possible install the mpkg package of mac os x version on Ubuntu? If yes, how?
Is possible use the usb modem installing Wine and the Windows Software for the usb modem?

I've already written to Alcatel email support (in English and in my local language) but they didn't reply.

:cry::cry:


I'm sure ubuntu community is better than Alcatel ;)

Thanks in advance,
Cheers,
Pier

---

### Post by morphet on 2012-09-20
Before trying Wine, try this:
open /etc/modules and add these two lines at the end:

usbserial
option

reboot, and enjoy. I'm writing from a Bouygues Alcatel onetouch X230L, linux mint. The distros usually have the right drivers, it's just a matter of telling linux to expect dual devices (modem/storage). I found this at: [http://askubuntu.com/questions/130295/alcatel-modem-compatibility-on-ub-12-04](http://askubuntu.com/questions/130295/alcatel-modem-compatibility-on-ub-12-04)

You'll then have to go to "networks", and follow the "broadband connections"-> "add new connection" wizard. On my system it takes about 20 seconds after I plug the modem in to recognize it.
Let me know how it went...

---

