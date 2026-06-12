---
title: "Cannot get the wifi working on my DELL Latitude 430 using Ubuntu Netbook Remix 9.10"
date: 2010-02-28
forum: Networking &amp; Wireless
---

### Post by HerveNY on 2010-02-28
Hi, 

I'm new to this forum.

I've installed successfully the ubuntu 9.10 netbook remix on my DELL Latitude 430.
Everything work out of the box except the wifi, I cannot find a way to get working.

Using the lshw command, I can see that the interface is listed, but status is disabled.

On the Network Manager, status I get is device not ready.

As a FYI, bluetooth seems working perfect (I've not tried to pair with any device).

Help would be welcome, as this is the only roadblock I face before enjoying Ubuntu on my laptop.

Thanks in advance

---

### Post by spiky001 on 2010-02-28
I dont know if you have tried this but is wireless turned on, on the laptop, on mine it's Fn+f2 is only a thought

---

### Post by chili555 on 2010-02-28
Please look all over that laptop and make sure all the switches and key combinations (Fn+F2, perhaps??) are activated. See if the wireless LED is winking or glowing. Please open a terminal and do:```
rfkill list
```Is the wireless blocked in any way? Next try:```
sudo rmmod -f dell-laptop
```Does your interface still show as Disabled?

---

### Post by makaveli94303 on 2010-02-28
hey

im new to ubuntu need help 

i have an inspiron  E1405 ive been having problems for like the past week trying to connect to my wireless network ive done all the recent ubgrades but i still cant get it working. i cant click the anable wireless button dnt kno if im doing anything wrong pleaseany advise would be helpful thanks

---

### Post by chili555 on 2010-02-28
> **makaveli94303 said:**
> hey

im new to ubuntu need help 

i have an inspiron  E1405 ive been having problems for like the past week trying to connect to my wireless network ive done all the recent ubgrades but i still cant get it working. i cant click the anable wireless button dnt kno if im doing anything wrong pleaseany advise would be helpful thanksPlease start a new thread and, from the terminal, post:```
lspci -nn
iwconfig
sudo lshw -C network
```Thanks.

---

### Post by HerveNY on 2010-03-06
Hi, 

I've tried all possible key combinations without success.
The blue WiFi led is off (the bluetooth one is on)

I've checked the BIOS: WIFI is on 
The result for the rfkill list is that wifi is no soft, or hard blockage. (same status than for Buletooth)

Thanks

---

### Post by chili555 on 2010-03-06
> **HerveNY said:**
> Hi, 

I've tried all possible key combinations without success.
The blue WiFi led is off (the bluetooth one is on)

I've checked the BIOS: WIFI is on 
The result for the rfkill list is that wifi is no soft, or hard blockage. (same status than for Buletooth)

ThanksDid you try this?```
sudo rmmod -f dell-laptop
```

---

