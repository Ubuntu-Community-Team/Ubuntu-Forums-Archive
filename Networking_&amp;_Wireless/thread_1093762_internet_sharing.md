---
title: "internet sharing"
date: 2009-03-11
forum: Networking &amp; Wireless
---

### Post by chmbrs on 2009-03-11
hello forum. im looking for some help with internet sharing.
i have a pc which i use to connect to various wireless networks around me.
thanks to backtrack and aircrack-ng i have many choices. my neighbor gave me an old laptop, 200mb ram, 6gb hdd, celeron 500mhz. i installed vector linux lite on it after trying:

dsl, puppy, feather, niblex and couple others. vector was the best for me.

now id like to share my connection with my laptop when im at home. i have a wifi card but signal sucks and it makes my head hurt. i have a regular ethernet cable and thats it. i read about the topic but havent found any solid answers. is there a way to share the internet without a router or a crossover cable. maybe apache server is the answer. im pretty much clueless about sharing i connection. any tips. Thanks in advance.:D

---

### Post by firefly2442 on 2009-03-12
I used firestarter in conjunction with a DHCP server to dole out IP addresses.  Firestarter is a firewall but it also has a handy configuration wizard to share your connection.  I never tried it with wireless but I was able to share my cable connection with the rest of the computers in my apartment.  Anyway, maybe this is something you could look in to?  Good luck.

---

### Post by Adina on 2009-03-12
[https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing)

---

### Post by nelskurian on 2009-03-12
You can setup one machine as gateway and another as client.You must configure iptables for forwarding the data packets.Also use  squid for proxy server setup.

---

### Post by xpod on 2009-03-12
> i have a pc which i use to connect to various wireless networks around me.thanks to backtrack and aircrack-ng i have many choices.

> now id like to share my connection with my laptop when im at home.

Is this your own connection your sharing or one of your neighbours?

Either way you`d need a crossover cable and a second NIC(normally) for ICS if you dont have a switch or router of some sort.

---

### Post by chmbrs on 2009-03-13
thank you for your replies i will look into them.

and of course its my connection. :)

---

