---
title: "smc91c92_cs not working for Ositech Seven of Diamonds"
date: 2005-12-21
forum: Networking &amp; Wireless
---

### Post by timknauf on 2005-12-21
I'm trying to get a PCMCIA 'Ositech Seven of Diamonds' network card working on my laptop. According to [the PCMICA-CS page]("http://pcmcia-cs.sourceforge.net/ftp/SUPPORTED.CARDS"), I need to use the smc91c92_cs driver.

Now, following [these instructions]("http://ubuntuforums.org/showthread.php?t=101550&page=2&highlight=smc91c92_cs"), I typed:
```
sudo modprobe smc91c92_cs
sudo /etc/init.d/networking restart
```

I then tested with ```
ifconfig
``` but only the 'Local Loopback' interface (lo) was listed.

I tried ```
ifconfig -a
``` but no 'eth0' was listed, just 'lo' and 'irda0' (for the infra-red port).

I should mention that cardmgr gives a **low** beep when I insert the card.

Has anyone got any ideas for getting the card working? (It works ok under Windows.)

Edit:
I just had a look in /var/log/syslog and see that I got this message from the card manager:
unsupported card in socket 1
product info: "Ositech", "Trumpcard:7oD-II Ethernet"

So is this card possibly a revised version (I'm assuming that's what the 'II' is for) that isn't supported by the driver?

---

