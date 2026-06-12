---
title: "Newbee stuck with no power to wireless card :("
date: 2013-03-18
forum: Networking &amp; Wireless
---

### Post by linuxlunatics on 2013-03-18
Hello everybody.

I'm sorry for posting about something that has so many posts already, but I think my problem is somewhat specific/rare.

I have read quite a bit, and tried a few remedies, with no solution as yet.

After installing Ubuntu 12.04 on my HP Pavilion dv5000, my wireless card has no power running to it. I have pressed the button over and over again without it turning on. I have also installed the necessary drivers, as I tested all this before through a Wubi semi install before getting rid of Windows.

My wireless card is BCM4318 Airforce 1 54g if that helps.

I really really want to get better at using Linux but am becoming so frustrated! Why can't it just work??!!! hahaha 

If anyone can help, I will be eternally grateful!!!

Thanks in advance.

---

### Post by varunendra on 2013-03-18
Hi,

Please post outputs of -
```
lspci -nnk | grep -iA2 net
dmesg | grep -i firm
```

And can you get a temporary cable connection on the system ?

---

### Post by Yellow Pasque on 2013-03-18
Check rfkill too:
```
rfkill list
```

---

### Post by linuxlunatics on 2013-03-18
> **varunendra said:**
> Hi,

Please post outputs of -
```
lspci -nnk | grep -iA2 net
dmesg | grep -i firm
```

And can you get a temporary cable connection on the system ?

Thanks for your reply.

I typed the code suggested into the terminal and got this -

[HTML]lenny@lenny-System-Product-Name:~$ lspci -nnk | grep -iA2 net
06:02.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)
	Subsystem: Hewlett-Packard Company Broadcom 802.11b/g WLAN [103c:1356]
	Kernel driver in use: wl
--
06:06.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
	Subsystem: Hewlett-Packard Company Device [103c:30a4]
	Kernel driver in use: 8139too
lenny@lenny-System-Product-Name:~$ dmesg | grep -i firm
lenny@lenny-System-Product-Name:~$ 
[/HTML]

Thanks for taking the time to help this utter noob out!

And I do have the machine connected to the internet via ethernet cable.

---

### Post by wildmanne39 on 2013-03-18
Hi, please do:
```
sudo apt-get purge bcmwl-kernel-source broadcom-sta-common broadcom-sta-source
```
Then:
```
sudo apt-get install linux-firmware-nonfree
```
Reboot
Thanks

---

### Post by varunendra on 2013-03-18
> **Wild Man said:**
> Hi, please do:
```
sudo apt-get purge bcmwl-kernel-source broadcom-sta-common broadcom-sta-source
```
Then:
```
sudo apt-get install linux-firmware-nonfree
```
Reboot
..and do this ^^ while being connected to the wired connection.

---

### Post by linuxlunatics on 2013-03-18
Everybody, THANK YOU!!!

Your above solutions have worked a treat, and like I said, I am eternally grateful!!

Nice one!!!

---

### Post by varunendra on 2013-03-18
Credit goes to Wild Man :)

Please mark the thread as [Solved] now. Follow the link in my signature to see how.

---

