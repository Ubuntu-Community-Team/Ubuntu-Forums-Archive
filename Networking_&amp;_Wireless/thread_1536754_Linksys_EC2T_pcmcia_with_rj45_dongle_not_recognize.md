---
title: "Linksys EC2T pcmcia with rj45 dongle not recognized"
date: 2010-07-22
forum: Networking &amp; Wireless
---

### Post by Sefianix on 2010-07-22
I have a friend with an old, still-working laptop that wants to switch to linux.  (Dell Inspiron 7000 PII)  I loaded Lubuntu because it's an old machine and has only 512MB of memory.  The laptop has no built-in ethernet or wireless.  As the title says, he has an EC2T card with it.  I've tried to get lubuntu to recognize the card but it's a no-go.  I tried the EC2T card on a Windows laptop at my workplace and Windows recognized the card immediately; I was able to surf the web with it.

It looks like at one time it worked with linux ([http://tuxmobil.org/pcmcia_ci10157.html]("http://tuxmobil.org/pcmcia_ci10157.html")).  I can't find any threads on this card except back from 2007 ([http://ubuntuforums.org/showthread.php?t=428870]("http://ubuntuforums.org/showthread.php?t=428870")) and that individual didn't get an answer.

Other troubleshooting I've done:
[LIST=1]
[*]I've ran the 'Hardware Drivers' utility and it found no drivers.
[*]I tried lspci and the EC2T card isn't listed.
[*]I tried a wireless pcmcia card from my workplace and it worked so the laptop's card slot is functioning; lspci does list the wireless card.
[/LIST]

Does anyone have any idea how to get this card working in (l)ubuntu??  Help would be appreciated.  Thanks.

---

### Post by cavalier911 on 2010-07-23
According to [http://tuxmobil.org/pcmcia_ci10157.html](http://tuxmobil.org/pcmcia_ci10157.html) :
"uses standard pcnet_cs module

> sudo apt-get install pcmciautils

Follow this thread: 
[http://www.uluga.ubuntuforums.org/showthread.php?p=8427818](http://www.uluga.ubuntuforums.org/showthread.php?p=8427818)

---

### Post by Sefianix on 2010-07-25
Thank you very much cavalier911!  That thread and command to install pcmciautils did it.  My card is working.

Much appreciated!

---

