---
title: "Does Ubuntu play fair with Ubuntu?"
date: 2010-01-16
forum: Networking &amp; Wireless
---

### Post by OSNoxious on 2010-01-16
I dual-boot Windows Vista and Ubuntu 9.10 on my desktop, with a wired connection to my Belkin Wireless N router. Xubuntu 9.10 is installed on my laptop, but if i'm on Ubuntu, Xubuntu can't connect to the network, and if I'm on Windows, it works like a charm. As soon as I log into Ubuntu, Xubuntu disconnects immediately. How do I fix this?

---

### Post by OSNoxious on 2010-01-16
Well... I figured out part of the problem. The network connection was Ad-Hoc for some reason... I changed it to Infrastructure, but it still won't connect if Ubuntu's online

---

### Post by coffeecat on 2010-01-16
Are either of Ubuntu or Xubuntu set up with static IP addresses for the local network? Check Network Manager in both. Make sure you have both set to DHCP. Or set static (and different) addresses for both.

---

### Post by OSNoxious on 2010-01-16
> **coffeecat said:**
> Are either of Ubuntu or Xubuntu set up with static IP addresses for the local network? Check Network Manager in both. Make sure you have both set to DHCP. Or set static (and different) addresses for both.

Automatic (DHCP) for both of them

---

### Post by Iowan on 2010-01-16
They shouldn't - but see if they're fighting over the same address (**ifconfig -a** from Xubuntu before, and Ubuntu after the "bump")

---

### Post by OSNoxious on 2010-01-16
> **Iowan said:**
> They shouldn't - but see if they're fighting over the same address (**ifconfig -a** from Xubuntu before, and Ubuntu after the "bump")

When I enter ifconfig -a, what am I looking for exactly?

---

### Post by Monotoko on 2010-01-16
Look for the connection you are using (eth for ethernet, wlan for wireless)
and check the IP's

---

### Post by OSNoxious on 2010-01-16
> **Monotoko said:**
> Look for the connection you are using (eth for ethernet, wlan for wireless)
and check the IP's

They're all totally different

---

### Post by CharlesA on 2010-01-16
Are the hostnames different?

---

### Post by OSNoxious on 2010-01-16
> **CharlesA said:**
> Are the hostnames different?

Which one is the hostname?

---

### Post by Iowan on 2010-01-16
> **OSNoxious said:**
> When I enter ifconfig -a, what am I looking for exactly?When Xubuntu is connected, use **ifconfig -a** to learn it's IP address. Check it after Ubuntu bumps it offline - then check the Ubuntu machine's IP address (also via **ifconfig -a**). I doubt they're trying to use the same address, but this should (dis)prove that.

---

### Post by CharlesA on 2010-01-16
> **OSNoxious said:**
> Which one is the hostname?

Type this in a terminal on both machines:

```
hostname
```

Post the output.

---

### Post by OSNoxious on 2010-01-16
I love how it doesn't want to disconnect now... The two hostnames are totally different by the way

---

### Post by OSNoxious on 2010-01-16
> **Iowan said:**
> When Xubuntu is connected, use **ifconfig -a** to learn it's IP address. Check it after Ubuntu bumps it offline - then check the Ubuntu machine's IP address (also via **ifconfig -a**). I doubt they're trying to use the same address, but this should (dis)prove that.

I did ifconfig -a on both computers, even though Xubuntu wouldn't disconnect this time. The information from eth0 (Desktop) and wlan0 (Laptop) are totally different, if that helps

---

### Post by CharlesA on 2010-01-16
Very strange indeed. Hopefully they won't disconnect when the other one is on now.

---

### Post by OSNoxious on 2010-01-16
Looks like they're playing nice... for now. I guess I'll just have to wait and see. If it starts up again, what should I do?

---

