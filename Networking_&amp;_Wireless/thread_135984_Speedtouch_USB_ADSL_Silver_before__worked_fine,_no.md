---
title: "Speedtouch USB ADSL Silver: before  worked fine, now doesn't work"
date: 2006-02-25
forum: Networking &amp; Wireless
---

### Post by heri on 2006-02-25
Hi, 
I'm using the silver Speedtouch USB ADSL modem.

I followed the howto in the wiki
[https://wiki.ubuntu.com/UKSpeedtouchDSLHowTo?highlight=%28CategoryDocumentation%29](https://wiki.ubuntu.com/UKSpeedtouchDSLHowTo?highlight=%28CategoryDocumentation%29)

Usually this is what happened:
- during the boot the modem blinking 
- then in terminal I typed: pon adsl 
- the modem will connect without any problem

But now, it doesn't work anymore.
During boot the modem still blinking but when I type: pon adsl, the modem will not connect and there is error message like this

=======
Plugin pppoatm.so loaded.
Warning: couldn't open ppp database /var/run/pppd2.tdb
=======

Pls help,

---

### Post by heri on 2006-02-25
Solved using excellent script by Steve Parker:
[http://www.steve-parker.org/speedtouchconf/](http://www.steve-parker.org/speedtouchconf/)

But first I had to install build essential package from Ubuntu CD:

insert Ubuntu CD

type: 
sudo apt-cdrom add
sudo apt-get install build-essential

Then follow Steve Parker's instruction.
It works great.

Thank's

---

