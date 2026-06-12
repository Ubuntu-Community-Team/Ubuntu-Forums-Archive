---
title: "Newbie dial-up question"
date: 2005-03-03
forum: Networking &amp; Wireless
---

### Post by simdiab on 2005-03-03
I'm more or less a complete noob when it comes to linux, and I've recently installed Ubuntu on my pc. I've used SuSE 9.1 on another pc before though and, I used YAST and KInternet to configure my dial-up internet connection. How do I configure dial-up in Ubuntu? With the network settings option in the menu? Do I then use wvdial to dial-up? I have a feeling Ubuntu does not auto-detect my modem(Duxbury V.92) as I cannot find /dev/modem.

---

### Post by landotter on 2005-03-03
try "sudo pppconfig" in a terminal, it's the most reliable way to create a ppp account with Ubuntu.

Not finding /dev/modem is ominous though. Is the Duxbury a "soft" modem?

---

### Post by simdiab on 2005-03-03
I'll try sudo pppconfig next time I reboot into linux. Please explain the term "soft". I can take the modem out and kick it, if thats what you mean.

---

### Post by landotter on 2005-03-03
[QUOTE=simdiab]I'll try sudo pppconfig next time I reboot into linux. Please explain the term "soft".[/QUOTE]

Soft meaning that the modem isn't a "hard"ware modem and requires drivers.

Most modems these days are softmodems unfortunately. A few do work well with linux, but they're a pain to set up. I used to use one with Fedora, but the drivers were too much of a pain to install w/Ubuntu, so I just got a used external hardware modem from ebay for 10usd. ;)

---

