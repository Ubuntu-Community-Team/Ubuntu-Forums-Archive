---
title: "Wifi help :("
date: 2013-07-05
forum: Networking &amp; Wireless
---

### Post by Nw1801 on 2013-07-05
Hi i have a compaq presario C500 laptop and since installing ubuntu 12.04 i cannot turn my wireless on with the button. I have had a look through the threads and dont understand so if someone can explain how i can get wireless to work so i can connect to internet would be a great help :)

---

### Post by grahammechanical on 2013-07-05
The wireless adapter needs to be switched on by the button before Ubuntu starts to load. And you should not use Windows to switch off the wireless adapter and then load Ubuntu.

In Ubuntu open a terminal and run

```
rfkill list
```

What do you see? If you see this

> 0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

Then the problem lies eslewhere. But if you see this

> 0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes


Then the wireless adapter is switched off by a hardware switch. Run

```
 rfkill unblock wifi
```

If you see this

> 0: phy0: Wireless LAN
    Soft blocked: yes
    Hard blocked: no




Then the wireless adapter is switched off by software. You need to enable Networking or Enable WiFi or both. You do that by clicking on the network icon in the top panel. It will looks like an inverted cone.

Regards.

---

### Post by Nw1801 on 2013-07-06
Hi just tried what you said. And when i first turn on the laptop, i pushed the wifi button b4 ubuntu loaded but the button would not turn on. Then after opening a terminal i typed in rfkill list and it says soft blocked no. Hard blocked yes so then i did rfkill unblock wifi but hasnt done anything. Am i doing anything wrong?

---

### Post by Nw1801 on 2013-07-06
Ok i have managed to get it to softblock - no and hardblock - no but cant pick up my internet in the network settings

---

### Post by ghsxscar on 2013-11-29
Does the wifi button light up? 
If not try to:
1. install the driver from additional drivers, (and make sure to activate it)
2. > sudo apt-get remove bcmwl-kernel-source in terminal
3. > sudo apt-get install firmware-b43-installer in terminal
4. reboot and try to press the button and turn it on

---

### Post by Bucky Ball on 2013-11-29
*Thread moved to **Networking & Wireless**.*

---

