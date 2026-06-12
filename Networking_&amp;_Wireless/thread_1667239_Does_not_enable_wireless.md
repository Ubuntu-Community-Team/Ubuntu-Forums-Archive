---
title: "Does not enable wireless"
date: 2011-01-14
forum: Networking &amp; Wireless
---

### Post by ubunoob23 on 2011-01-14
Hi all,

I am a day old in ubuntu-world, and I am having internet issues. Yesterday, after i had installed ubuntu alongside windows 7. To begin with it did not detect wireless (not networks but wireless itself), so i figured it was something to do with the adapter and came to these forums where many things were suggested. none worked. So I restarted the system for good measure and lo and behold it detected wireless networks and connected to the internet almost immediately.

Now, after a day, when i have logged in to ubuntu again, there is no wireless detected. The same problem. When I right click on the network icon in the notification area i see that Enable Networking is checked but "Enable Wireless" is darkened. There is no way to check it. 

Can anybody please advise as to what to do next. I am using ubuntu 10.04 LTS (Lucid Lynx I believe).My system config is i7, 512MB ram. 

Thanks.

---

### Post by meufel on 2011-01-14
Hi,
checkout your network settings with
```
ifconfig
```
There should be something like: eth0, lo and maybe wlan0. If wlan is already there, try to activate it with 
```
sudo ifconfig wlan0 up
```
Replace wlan0 with the name of your wireless interface.


If the interface is not there, find out the name of your network card with
```
lspci | grep -i network
```
Before posting, search the forums for your network card, or use google with an additional linux/ubuntu to receive some relevant hits.

edit:
What is your hardware like anyway? Do you have an external button to switch on/off wireless? Or some of those function key combinations that enable you to switch on/off wireless?

---

