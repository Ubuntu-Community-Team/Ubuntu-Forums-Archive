---
title: "no dialup modem support in Jaunty?"
date: 2009-07-20
forum: Networking &amp; Wireless
---

### Post by brog45 on 2009-07-20
Can someone explain to me why network-manager in Jaunty does not support ordinary dialup modems?  They may not be fashionable anymore but they are still quite common.

---

### Post by svaens on 2009-07-23
Yeah, I thought this a bit strange too.... meant I couldn't really install jaunty in the early days of my move (to my new house) that I didn't yet have broadband set up, and still needed to use dialup access. 

It might not be the greatest, but it is still a fall-back some of us have to rely on!

---

### Post by superprash2003 on 2009-07-24
you could install the old network manager and setup dialup through that

---

### Post by NoReflex on 2009-07-24
or you can use Gnome-PPP ...

NoReflex

---

### Post by urisc on 2009-07-24
> **NoReflex said:**
> or you can use Gnome-PPP ...

NoReflex
I tried to use Gnome ppp and it 
did't work. I still have the problem that my computer can not find the modem. Any ideas?
Tnx.
Uri.

---

### Post by NoReflex on 2009-07-24
What modem do you have? You must first try to see why Ubuntu doesn't detect your modem.
Helpful commands:
```

tail /var/log/messages # good after plugging in a modem
lsusb #if your modem is connected via a USB port
lspci # if your modem is connected via a PCI port

```

Good luck!

Best wishes,
NoReflex

---

### Post by salimzen on 2009-07-24
Hi eveybody,
i had a little a bit the same problem but with the version 8.04/
after i had install the packages relative to the modem the device had been still undetectable.so after some researches i succeed to surround the problem.
I hope that it can be of some help to you.
this is the solution:
1-debranch the modem.
2-change to the directory /etc/init.d/ by taping cd /etc/init.d/
3-now you will stop the kernel event manager that manages the drivers relatif to devices that can be mount on your system.
you tape   
$ sudo ./udev stop
4-now your start the kernel event manager (it reloads all the drivers needed to mount different devices on your system)
$ sudo ./udev start
5-branch your modem.
6-tape  sudo wvdial.
NB:I have LG LDU 1900 D modem.

---

### Post by Iowan on 2009-07-24
Dunno if [this]("https://help.ubuntu.com/community/DialupModemHowto") page will help...

---

### Post by brog45 on 2009-08-10
I got it working, but I think it's outrageous that it is not supported out of the box.

---

### Post by Iowan on 2009-08-10
Glad you got it working.  I doubt the 56K modem on my new laptop will ever see much/any use.

---

