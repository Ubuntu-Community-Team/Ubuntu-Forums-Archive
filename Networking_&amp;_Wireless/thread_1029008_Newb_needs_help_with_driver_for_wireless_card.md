---
title: "Newb needs help with driver for wireless card"
date: 2009-01-02
forum: Networking &amp; Wireless
---

### Post by downhiller2010 on 2009-01-02
So i am brand new to linux and have a dlink DLW-520+ card. I have googled it a little but im not exactly sure where to get started. I really want to get this fixed so I can begin to explore the world of linux. Thanks in advance for any help.

---

### Post by Tim Sharitt on 2009-01-03
In a terminal run 
```
lspci
```
and
```
lshw -C network
```

and post the output of each.

---

### Post by downhiller2010 on 2009-01-03
I dont have an easy way to copy paste through different operating systems. From wat I know and running those commands it doesnt look like my card is recognized

---

### Post by melojo on 2009-01-03
If you have dual boot you can copy and paste to a text file then save it to your windows partition, then upload it from windows.

---

### Post by downhiller2010 on 2009-01-03
It seems like ndiswrapper is my best option

---

### Post by Tim Sharitt on 2009-01-03
Do you have any idea what chipset the card uses?

---

### Post by downhiller2010 on 2009-01-04
I believe its a texas instruments acx 100 or something like that

---

### Post by downhiller2010 on 2009-01-04
Alright I used a wired connection to install ndiswrapper and got to where I am on the screenshot

---

### Post by Tim Sharitt on 2009-01-04
You may need the firmware which is included in linux restricted modules. You'll need your wired conection to install it.
Open a terminal and enter
```
sudo apt-get install linux-restricted-modules-generic
```
That should solve your problem for if the chipset is a TI acx100.

---

### Post by downhiller2010 on 2009-01-04
> **Tim Sharitt said:**
> You may need the firmware which is included in linux restricted modules. You'll need your wired conection to install it.
Open a terminal and enter
```
sudo apt-get install linux-restricted-modules-generic
```
That should solve your problem for if the chipset is a TI acx100.

my problem that i had in the screen shot?

---

