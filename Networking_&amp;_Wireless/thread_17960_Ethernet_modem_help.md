---
title: "Ethernet modem help"
date: 2005-03-03
forum: Networking &amp; Wireless
---

### Post by bulio on 2005-03-03
Hi everyone,

I recently got my ubuntu cds in the mail, and I was wondering how to setup ubuntu live for dsl internet. I have a dsl modem wich connects to my pc using pppoe internet authentication. The setup is like this:

Computer-Ethenet cable-->Modem-->Phone Jack

The modem is an efficient networks speedstream 5200 usb/ethernet modem. I use ethernet to connect the modem to my pc. I've been told that ubuntu is great at recognizing modems, and I have had no luck connecting to the net. How can I set it up so it will work on the internet?

Thanks

---

### Post by svg on 2005-03-03
Hi,

just try 

# pppoeconf 

(or  sudo pppoeconf)

works fine...

---

### Post by bulio on 2005-03-04
I tried that, still didn't work. Gave me this error:

/usr/sbin/ppd: in file /etc/ppp/peers/provider unrecognized option /dev/modem

What is wrong here?

---

### Post by az on 2005-03-04
Are you using pppoeconf, and not pppconfig?  They are two different things.

---

