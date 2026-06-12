---
title: "wireless connectivity"
date: 2012-05-18
forum: Networking &amp; Wireless
---

### Post by xjunkyardx on 2012-05-18
seems that like a lot of people, i'm having problems with my broadcom wireless drivers.

I have looked through the sticky, and tried as many solutions as i could find, b43, b43legacy, sta... nothing shows up in my additional drivers menu, and being new to ubuntu i'm hoping someone can help or point me to a more detailed tutorial to fix this.

at one point it would say connected just fine to my wireless network, but none of my browsers would go to any websites. now when i click on the wireless dropdown, there isn't even an option for wireless networking.

Thanks in advance.

Adam.

---

### Post by xjunkyardx on 2012-05-18
I am using a wired connection now, and i believe i have a BCM4306 - and research led me to believe i needed the b43legacy driver but to no avail.

again, thanks in advance.

Adam.

---

### Post by josephmills on 2012-05-18
please open terminal and enter in 
```
lspci -nn | grep 14e4 
```
and paste here thanks

---

### Post by xjunkyardx on 2012-05-18
> **josephmills said:**
> please open terminal and enter in 
```
lspci -nn | grep 14e4 
```and paste here thanks

yeilded

```

02:06.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 03)

```

---

### Post by xjunkyardx on 2012-05-20
bump. please and thank you

---

### Post by xjunkyardx on 2012-05-21
after making sure that all the drivers were gone, and re-installing firmware-b43-installer and b43-fwcutter, it seems i am back in the boat where my wireless network is discoverable and connectable, yet whenever i go to a web page it will not connect. Chrome gives me DNS errors, so maybe it's something besides my wireless drivers now?

---

