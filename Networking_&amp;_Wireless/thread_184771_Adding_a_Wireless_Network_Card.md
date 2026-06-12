---
title: "Adding a Wireless Network Card"
date: 2006-05-30
forum: Networking &amp; Wireless
---

### Post by evandec on 2006-05-30
Hello, 

I have an Atheros wireless network card on my Toshiba laptop. I installed ubuntu and picked up internet with my ehternet card, but the wireless card was a no go. 

I looked in the settings and it does not apear to have been added. How can I go about adding the card and setting up the OS to use a wireless signal.

Thank you

Evan

---

### Post by patrick295767 on 2006-05-30
[QUOTE=evandec]Hello, 

I have an Atheros wireless network card on my Toshiba laptop. I installed ubuntu and picked up internet with my ehternet card, but the wireless card was a no go. 

I looked in the settings and it does not apear to have been added. How can I go about adding the card and setting up the OS to use a wireless signal.

Thank you

Evan[/QUOTE]
  
When you type : 
```
sudo bash 
network-admin
```
  
Do you see your wireless card ? 'cos It can be also a matter of enabling...
Don't know more.

---

### Post by evandec on 2006-05-30
[QUOTE=patrick295767]When you type : 
```
sudo bash 
network-admin
```
  
Do you see your wireless card ? 'cos It can be also a matter of enabling...
Don't know more.[/QUOTE]



When I do that all I get is > root@dhcp56:~# network -admin
bash: network: command not found


---

### Post by Tetchy Tony on 2006-05-31
He probably meant 'network-admin' without the space.  That works for me, but I get no further with the screen it generates.

---

