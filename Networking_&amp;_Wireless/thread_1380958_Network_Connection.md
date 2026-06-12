---
title: "Network Connection"
date: 2010-01-14
forum: Networking &amp; Wireless
---

### Post by emma00 on 2010-01-14
Hi,

I am new to Ubuntu almost installed it after windows showd blue screen 4 ever n ever.... However after installing ubuntu whenever i log in windows it doesnt detect any network connection but when i use Ubuntu it automatically does can it be that Ubuntu is causing any problem???
And how to check how many packets are being sent and received through my wired network and do i have to install any drivers for my modem in Ubuntu.

Thanks 4 your time :P

---

### Post by pricetech on 2010-01-14
Ubuntu shouldn't be causing your winders network problems.  You say it was blue screening, my guess is that your network drivers or your IP stack are corrupt in winders.  Try reinstalling your NIC drivers and that should rebuild the IP stack for you.  If that doesn't fix it, try a winders forum for your winders issues.

---

### Post by Iowan on 2010-01-14
**ifconfig -a** will provide a snapshot of interface status - including packets sent/received, errors, and overruns.

Dial-up or DSL modem?

---

### Post by emma00 on 2010-01-15
> **Iowan said:**
> **ifconfig -a** will provide a snapshot of interface status - including packets sent/received, errors, and overruns.

Dial-up or DSL modem?

Its a cable net connection so don't know about dsl modem but its not a dial up modem,and how to check my packet status in ubuntu dont want to go to windows its now only reserve for my sister thats why i have to do it and one thing more torrent ubuntu transmission is very slow in ubuntu.How to make it better???

Thanks to both of you for your reply.;)

---

### Post by changingstate on 2010-01-15
I'm guessing you have a cable modem, then, yes? Assuming it's hooked in using the ethernet cable rather than the USB cable ( ethernet looks like a big phone wire ), you won't need any modem drivers.

> And how to check how many packets are being sent and received through my wired network
I'm a little confused as to your exact aims here. Mind telling us a little more about your network and why this interests you?

---

### Post by emma00 on 2010-01-16
> **changingstate said:**
> I'm guessing you have a cable modem, then, yes? Assuming it's hooked in using the ethernet cable rather than the USB cable ( ethernet looks like a big phone wire ), you won't need any modem drivers.

I'm a little confused as to your exact aims here. Mind telling us a little more about your network and why this interests you?

I connect through usb cable and i think my downloading speed was a bit fast in windows and i can change settings of bit torrent easily,but in Ubuntu i don't how to optimize it.just in learning process.;)

---

