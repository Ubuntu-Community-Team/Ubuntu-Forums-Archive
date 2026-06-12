---
title: "Trying to connect to the web through my HTC Touch HD"
date: 2009-07-03
forum: Networking &amp; Wireless
---

### Post by Manthis on 2009-07-03
Hi,

I'm presently trying to use my phone, a HTC Touch HD as a USB modem to connect to the web.

When I plug my phone in a USB slot, my system creates an eth1 interface.

Then I initialize this interface using:
sudo dhclient eth1

I get an IP address for this interface which is 192.168.0.102, and then I'm stuck. No way to ping any address except for 192.168.0.1 which appears to be my phone.

Does somebody have an idea about how to fix this issue? I would really appreciate...

Thx

---

### Post by computer13137 on 2009-07-03
You may try this tutorial, as it mentions similar phones.  However, I've never tethered a phone, nor have I used an HTC Touch HD, I'm just a little better at Googling than you are. :P

[http://peterchuang.com/blog/2008/11/124/](http://peterchuang.com/blog/2008/11/124/)

-Kirk

---

### Post by superprash2003 on 2009-07-03
you want to share your pc's internet connection with your HTC?

---

### Post by Manthis on 2009-07-03
> **computer13137 said:**
> You may try this tutorial, as it mentions similar phones.  However, I've never tethered a phone, nor have I used an HTC Touch HD, I'm just a little better at Googling than you are. :P

[http://peterchuang.com/blog/2008/11/124/](http://peterchuang.com/blog/2008/11/124/)

-Kirk

Ok, I know this method but it's useless. I should be able to connect through the eth1 interface.

I made a test today with one of my friend's laptop running under ubuntu and it's working fine by running dhclient eth1 on the interface created when plugging the HTC phone.

What I don't understand is why it doesn't work for me. I do exactly the same thing. I checked /etc/resolv.conf and it is ok...

> you want to share your pc's internet connection with your HTC?

No, the opposite, I want to connect to internet through my HTC phone

---

### Post by Manthis on 2009-07-03
Ok, I just managed to connect through my HTC phone by removing wicd and installing knetworkmanager instead.

I'm gonna test this procedure further and see what is the good thing to do...

I'll post the exact solution here...

---

### Post by Manthis on 2009-07-03
Ok, I was right apparently, and I don't know why, it's working fine with network-manager and not with wicd.

I'll try to figure out why...

Thanks for the help guys ;)

---

### Post by Manthis on 2009-07-03
Well, I correct, it works with wicd too but you have to change the preferences: you need to specify eth1 instead of eth0.

Then it works... which makes me think about something: is there any way to add eth1 to wicd in parallel of eth0???

---

