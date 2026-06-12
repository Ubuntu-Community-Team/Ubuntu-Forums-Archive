---
title: "Intel 3945ABG wireless driver"
date: 2013-01-09
forum: Networking &amp; Wireless
---

### Post by deadcat45 on 2013-01-09
I have an Intel 3945ABG wireless card in my laptop that I need a driver for. Could anyone help?

---

### Post by haqking on 2013-01-09
> **deadcat45 said:**
> I have an Intel 3945ABG wireless card in my laptop that I need a driver for. Could anyone help?

what Ubuntu version are you using ?

you could try the following:

```
sudo modprobe iwl3945 
dmesg | grep iwl 
lspci -nn | grep -i wireless
```

The last 2 commands are not required apart from for output, the first command loads the module

---

### Post by deadcat45 on 2013-01-09
When  I entered that I got this 




alex@Alex-backbox:~$ sudo modprobe iwl3945 
[sudo] password for alex: 
Sorry, try again.
[sudo] password for alex: 
alex@Alex-backbox:~$ sudo modprobe iwl3945 
alex@Alex-backbox:~$ dmesg | grep iwl 
[ 4613.066735] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, in-tree:s
[ 4613.066746] iwl3945: Copyright(c) 2003-2011 Intel Corporation
alex@Alex-backbox:~$ lspci -nn | grep -i wireless
alex@Alex-backbox:~$

---

### Post by haqking on 2013-01-09
> **deadcat45 said:**
> When  I entered that I got this 




alex@Alex-backbox:~$ sudo modprobe iwl3945 
[sudo] password for alex: 
Sorry, try again.
[sudo] password for alex: 
alex@Alex-backbox:~$ sudo modprobe iwl3945 
alex@Alex-backbox:~$ dmesg | grep iwl 
[ 4613.066735] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, in-tree:s
[ 4613.066746] iwl3945: Copyright(c) 2003-2011 Intel Corporation
alex@Alex-backbox:~$ lspci -nn | grep -i wireless
alex@Alex-backbox:~$

and now does wireless work ?

---

### Post by deadcat45 on 2013-01-09
No. I think it needs a driver but i can't find one and get it to work.

---

### Post by haqking on 2013-01-09
> **deadcat45 said:**
> No. I think it needs a driver but i can't find one and get it to work.
now try

```
sudo ifconfig wlan0 up 
```[FONT=arial][COLOR=#33FFFF][B]


[/B][/COLOR][/FONT]

---

### Post by deadcat45 on 2013-01-09
alex@Alex-backbox:~$ sudo ifconfig wlan0 up
[sudo] password for alex: 
wlan0: ERROR while getting interface flags: No such device
alex@Alex-backbox:~$

---

