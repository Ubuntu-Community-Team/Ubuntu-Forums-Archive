---
title: "Please help with wireless"
date: 2006-05-20
forum: Networking &amp; Wireless
---

### Post by Okami on 2006-05-20
I have bought a D-Link DI-624 wireless router and a Belkin Wireless Notebook Network Card. However I cannot get it to work, using Ubuntu 6.06 right now. 
Usually I do not have any problem with the network.
I tried to configure the router and now it doesnt even work whitout the card!
Is there something missing?

Thanks in advance.

---

### Post by Fass on 2006-05-20
When you say "I can't get it to work," what have you done to try to make it work? IIRC, Belkin cards are often Broadcom based, and the only luck I've had with those is running them with ndiswrapper...

---

### Post by Okami on 2006-05-20
Thanks for the answer.
I have only tried to configure the router and also tried to configure the wireless card from "network settings". 
I will try ndiswrapper :)

Also the router doesnt seems to work anymore :???: , tried to reset it but it did not help...
But first ndiswrapper.

Thanks again.

Edit: did not find a sys or inf file on the driver cd so I could not try ndiswrapper. But I find something called atmel-firmware in the repositories. But it didnt help :(

---

### Post by Fass on 2006-05-20
You can use google to find the drivers for your card. Which card is it? Don't forget the model number.

---

### Post by Okami on 2006-05-20
Its Belkin F5D6020 v2. 802.11b
But this atmel-firmware, isnt that the driver? Im so confused... Im trying to read about atmel-firmware, seems that others has got it working. Also the cards "lamp" should be green when its on, but it isnt :???:

---

### Post by Fass on 2006-05-20
[http://wiki.linuxquestions.org/wiki/Belkin_F5D6020_ver.2](http://wiki.linuxquestions.org/wiki/Belkin_F5D6020_ver.2)

Tried what this page says?

---

### Post by Okami on 2006-05-20
Thanks but yes, it doesnt work. 
I must really be doing something wrong...

Edit: I knew there was something i missed >_< its not version 2 but version 3 of this card, I feel so stupid. Well, search around again, but I wonder if this card really will work...

Edit: just tried what it says in this thread [http://www.ubuntuforums.org/showthread.php?t=61717&highlight=belkin+F5D6020](http://www.ubuntuforums.org/showthread.php?t=61717&highlight=belkin+F5D6020)
but still not :(

Edit: its working! :) im still confused. But i changed to static ip in network settings and then the card lamp got green, but still it did not work. So I changed to dhcp again and now its working.

---

