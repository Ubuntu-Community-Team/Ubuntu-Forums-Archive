---
title: "Wireless not working Intel 3945ABG Ubuntu 11.04"
date: 2011-09-29
forum: Networking &amp; Wireless
---

### Post by alvaroducas on 2011-09-29
this is my first time running ubuntu on my hp dv2120 and i can't use my wireless card, i can't even activate de switch of my laptop
i've been reading some post but i think i have a different problem, i opened the terminal and typed "rfkill list all" and receive the following answer
0: hp-wifi: Wireless LAN
    Soft blocked: yes
    Hard blocked: yes
1: phy0: Wireless LAN
    Soft blocked: yes
    Hard blocked: yes
any idea?
thanks!

---

### Post by bkratz on 2011-09-29
> **alvaroducas said:**
> this is my first time running ubuntu on my hp dv2120 and i can't use my wireless card, i can't even activate de switch of my laptop
i've been reading some post but i think i have a different problem, i opened the terminal and typed "rfkill list all" and receive the following answer
0: hp-wifi: Wireless LAN
    Soft blocked: yes
    Hard blocked: yes
1: phy0: Wireless LAN
    Soft blocked: yes
    Hard blocked: yes
any idea?
thanks!


this is probably worth a try (it won't hurt anything either it will just go back to the current status at the next boot up). If it does work we can make it permanent. Anyway,

```
sudo rmmod -f hp-wmi
sudo rfkill unblock all
rfkill list all
```

and see if the block are removed and if wireless works.

---

### Post by KishanSL on 2011-09-30
I am having a similar problem. I am using Compaq Presario V3000, and I am new to Ubuntu (11.04), had used 9.04 for a few days, but had no wireless related problem.

Using command "rfkill list all", it shows:---

0: hp-wifi: Wireless LAN
    Soft blocked: yes
    Hard blocked: no
1: hp-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: phy0: Wireless LAN
    Soft blocked: yes
    Hard blocked: yes
4: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

Tried 
sudo rmmod -f hp-wmi sudo rfkill unblock all rfkill list all
but it dint help, and rebooting made it the same again. (It dint work for before rebooting also). Please halp.

---

