---
title: "aircrack-ng on emachines e720"
date: 2009-06-10
forum: Networking &amp; Wireless
---

### Post by mikesi on 2009-06-10
Hi I was trying to set up aircrack-ng on an emachines 720 and I wanted to know how would I find out what wireless card am I using and how would I know if its supported?

---

### Post by pedja_portugalac on 2009-06-10
Open your PC with screwdriver and inside you'll find wifi card. It's all writen on it.

---

### Post by LMZKJ on 2009-06-10
Maybe this is over simplifying it, but couldn't you go to the eMachines web site and go to the driver download page and see what wireless card driver they are supplying?;)

---

### Post by mikesi on 2009-06-10
> **pedja_portugalac said:**
> Open your PC with screwdriver and inside you'll find wifi card. It's all writen on it.
 
I don't want to take apart my laptop, I might not be able to put it back together, isnt there a way to do it from the terminal?

> **LMZKJ said:**
> Maybe this is over simplifying it, but couldn't you go to the eMachines web site and go to the driver download page and see what wireless card driver they are supplying?;)

Good idea. I see WLAN_Atheros and WLAN_FoxConn, I'm not sure which one is the driver I'm currently using.

---

### Post by Randabis on 2009-06-11
> **mikesi said:**
> I don't want to take apart my laptop, I might not be able to put it back together, isnt there a way to do it from the terminal?



Good idea. I see WLAN_Atheros and WLAN_FoxConn, I'm not sure which one is the driver I'm currently using.
If your driver for linux is the Broadcom restricted driver, then you are using the Foxconn one. I have the same notebook. There are a few variants of this model. I believe most of them use the foxconn chipset.

---

### Post by pedja_portugalac on 2009-06-11
> **mikesi said:**
> I don't want to take apart my laptop, I might not be able to put it back together, isnt there a way to do it from the terminal?
Yes there is.
> # mail neighbour  
Subject: your internet bandwidth
Hi neighbour, can you give me password for your WIFI?
alse=I'll use aircrack on you!!!

Thanks,
your cracker

.

EOT 

---

### Post by mikesi on 2009-06-11
I wasn't looking for help so I can crack my neighbors WEP key as they don't use WEP. I however set my router up so I can try and crack my own, I don't fully understand how this works but I'm thinking if I use a complicated and long enough key they wouldn't be able to crack it? thanks for the help guys(joking, you guys were pretty useless.)

don't assume everyone looking for help is a cracker looking to own their neighbors.

---

### Post by kevdog on 2009-06-11
lshw -C network
lspci -nnm

Post these and we can see what chipset you have as your wireless device.

---

