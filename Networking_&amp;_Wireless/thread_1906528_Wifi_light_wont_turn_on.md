---
title: "Wifi light wont turn on"
date: 2012-01-09
forum: Networking &amp; Wireless
---

### Post by ShaneOSDN on 2012-01-09
Hi I have an Acer Aspire 5742 series after updating to Ubuntu 11.10 the wifi light on my laptop fails to come on. Is there anything that can be done about this?  Wifi card is broadcom sta wirless driver if that helps at all. Any help would be appreciated.Thank You

---

### Post by jonobr on 2012-01-09
[Here]("http://knowledge76.com/index.php/Wireless_LED_on_Ubuntu") is a link which has a script .

I havent tried it but it looks good.

Hope it works

---

### Post by ShaneOSDN on 2012-01-09
Yeah no luck even after a restart but i appreciate you help greatly.

---

### Post by jonobr on 2012-01-09
Hello


Maybe try this.


before attempting make a backup of the file we are going to modify

```
sudo cp /etc/sysctl.conf sysctl.conf.bkup
```

in the /etc/sysctl.conf file add the following lines at the end

```
dev.wifi0.ledpin=3
dev.wifi0.softled=1
```

then restart your machine and connect to your network

---

### Post by wildmanne39 on 2012-01-09
Hi, do you mean that you also can not connect to the internet?
Thanks

---

### Post by jonobr on 2012-01-09
wildmanne39 excellent point, I read the post and took it at face value

I assume it was only a led issue, I didnt go down the road of troubleshooting internet connectivity.

---

### Post by wildmanne39 on 2012-01-09
Hi jonobr, either way I will let you handle it, I see a lot of people say the light will not come on when they mean the internet will not connect wirelessly.

---

### Post by jonobr on 2012-01-09
Cheers wildmanne39 ,

Thats my second resolution for the new year
#1 Dont take everything in life for granted
#2 No more Mr Nice Guy :-) <- I do this one every year



 Anyway , we will see what the OP has to say

cheers

---

### Post by ShaneOSDN on 2012-01-10
> **jonobr said:**
> Hello


Maybe try this.


before attempting make a backup of the file we are going to modify

```
sudo cp /etc/sysctl.conf sysctl.conf.bkup
```in the /etc/sysctl.conf file add the following lines at the end

```
dev.wifi0.ledpin=3
dev.wifi0.softled=1
```then restart your machine and connect to your network

ok so i tried but still no luck thank you very much for trying though. Maybe the led is just fried

---

### Post by ShaneOSDN on 2012-01-10
> **wildmanne39 said:**
> Hi, do you mean that you also can not connect to the internet?
Thanks

 no just led issues

---

### Post by jonobr on 2012-01-10
Good to hear its led issues.... sorry its not playing ball...

Mind you , it could be worse, there's a lot of people who complain about flickering leds that zombifies them

---

