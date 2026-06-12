---
title: "Getting wireless to work in 9.10"
date: 2009-11-28
forum: Networking &amp; Wireless
---

### Post by stigb on 2009-11-28
I just helped a friend install Ubuntu 9.10 on his laptop (Lenovo S10e) alongside Windows XP. The installation went fine as far as I could tell, and now he is logged on i Ubuntu, but the wireless menu only says "Disconnected" and none of the available networks show up. I'm sitting one metre away from him with my own laptop right now, and everything works fine.
I tried adding his network in "Configure VPN connections" and just copied the information from my own connection, but nothing happened.

Question mark is set.

---

### Post by stigb on 2009-11-28
It works fine on a wired network, but it appears that connecting to a wireless network is not even an option, although it works fine under Windows. Does this mean that Ubuntu is unable to communicate with the hardware, and what should we do then?

---

### Post by pdc124 on 2009-11-28
whats the card ? 
try sudo lspci and pick out the wireless card ?

---

### Post by stigb on 2009-11-28
Allright:
```
02:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express (rev 02)
05:00.0 Network controller: Broadcom Corporation BCM4312 802.llb/g (rev 01)
```These seem to be the only ones related to networking.

---

### Post by bkratz on 2009-11-28
> **stigb said:**
> Allright:
```
02:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express (rev 02)
05:00.0 Network controller: Broadcom Corporation BCM4312 802.llb/g (rev 01)
```These seem to be the only ones related to networking.

This page is worth looking at to see what driver supports your card.

[http://linuxwireless.org/en/users/Drivers/b43#Known_PCI_devices](http://linuxwireless.org/en/users/Drivers/b43#Known_PCI_devices)

---

### Post by stigb on 2009-11-28
Allright, I found out I had to activate a driver in order to get it to work. (Unfortunately a proprietary one, "Broadcom STA wireless driver")

The wireless receiver works now, but for some weird reason my friend's network does not show up in the list over networks, although a lot of his neighbours' do. I know the network is there, because I am myself connected to it right now.

The fact that you're reading this reply proves that the network is there. Why can't the other laptop access it?

---

### Post by bkratz on 2009-11-28
> **stigb said:**
> Allright, I found out I had to activate a driver in order to get it to work. (Unfortunately a proprietary one, "Broadcom STA wireless driver")

The wireless receiver works now, but for some weird reason my friend's network does not show up in the list over networks, although a lot of his neighbours' do. I know the network is there, because I am myself connected to it right now.

The fact that you're reading this reply proves that the network is there. Why can't the other laptop access it?

Is the 
ESSID (name) being transmitted or is it "hidden"?

---

### Post by ublintu on 2009-11-28
Hi, 
How did you install your broadcom driver? Did you try this guide? : [http://ubuntuforums.org/showthread.php?t=1288865](http://ubuntuforums.org/showthread.php?t=1288865)

---

### Post by stigb on 2009-11-28
> **bkratz said:**
> Is the 
ESSID (name) being transmitted or is it "hidden"?
>  How did you install your broadcom driver?

The name should be transmitted, and anyway we've tried to connect to it as a hidden network. It did not work.
It was installed through System -> Administration -> Hardware drivers. But the problem is now not that the wireless does not work at all, but rather that it somehow manages to ignore only the network I'd like it not to.

---

### Post by stigb on 2009-11-28
His network suddenly appeared in the list, and connected gracefully.

---

### Post by walt.smith1960 on 2009-11-28
> **stigb said:**
> His network suddenly appeared in the list, and connected gracefully.

P_F_M  (Pure freakin' magic):). Glad you got it working.

---

