---
title: "Netgear WNDA3100v2 not connecting"
date: 2012-04-01
forum: Networking &amp; Wireless
---

### Post by ammmg on 2012-04-01
Hi all,
I have netgear adapter and it's not connecting.I have managed to install software with ndiswrapper but it's not connecting.I have upgraded ubuntu to 12.04 thinking that it may solve my problem but it's not connecting still.I can see all networks around but when I'm entering the password it's not taking it.When I've removed password it connected straight away.
Please help me.This is my another attempt to replace windows and this time I do not want to give up.
I've read posts(that way I've managed to install software for Netgear)but I don't know what to do.
My security setting on router:WPA-PSK Version:WPA+WPA2 and my own WPA-PSK Encryption Key.
I have no IT background so it takes some time before I manage to fix some issue and not always I understand what I'm doing.:lolflag:

---

### Post by praseodym on 2012-04-01
Hi,

ndiswrapper is the right way, because there is no Broadcom Linux USB driver available (its a Broadcom chipset). Driver for 32 and 64 bit attached.

IMHO N-mode does not work, you may change the router settings to b+g mode only.

---

### Post by ammmg on 2012-04-01
What do you mean "change the router settings to b+g mode only"?what is b+g mode?

---

### Post by praseodym on 2012-04-01
Can you connect via cable to the router? If yes, type in the IP address of the router into the browser and change the wireless settings of the radio mode from b+g+n to b+g

---

### Post by ammmg on 2012-04-01
I have managed to change to b/g but it's not working.This time is different,after attempt to connect it's just saying that my network is offline,before it was asking me to re-enter the password.
:confused:

---

### Post by ammmg on 2012-04-01
Yeessssssssssss!!!!It's working!!Thank you very much praseodym! After changing to 801.11b/g mode it did not connect at first time but it looks after first attempt it connected on second attempt :)
I have checked 801.11b and it worked , g mode and b/g/n is not working,not connecting.I'm happy again :popcorn:

---

