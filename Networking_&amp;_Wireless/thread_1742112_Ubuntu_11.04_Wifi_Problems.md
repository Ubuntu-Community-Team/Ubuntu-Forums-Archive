---
title: "Ubuntu 11.04 Wifi Problems"
date: 2011-04-28
forum: Networking &amp; Wireless
---

### Post by hiever1 on 2011-04-28
I can't turn my wireless card on. I have a Dell Inspirion 6400 with 
intel 3945abg card. I tried turning it on Fn+F2. Nothing. It worked fine in 10.10. Help please?

---

### Post by chili555 on 2011-04-28
How about opening a terminal and showing us:```
rfkill list all
lsmod | grep dell
```Thanks.

---

### Post by hiever1 on 2011-04-28
> 

tristan@Tristan-Laptop:~$ rfkill list all
0: dell-wifi: Wireless LAN
	Soft blocked: yes
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes
tristan@Tristan-Laptop:~$ 
tristan@Tristan-Laptop:~$ lsmod | grep dell
dell_wmi               12601  0 
sparse_keymap          13666  1 dell_wmi
dell_laptop            13515  0 
dcdbas                 14054  1 dell_laptop
tristan@Tristan-Laptop:~$ 




Help me doc.

---

### Post by chili555 on 2011-04-28
Now do:```
sudo rmmod -f dell-laptop
sudo rfkill unblock all
```Any improvement? If so, we'll need to amend one file to make is permanent.

---

### Post by hiever1 on 2011-04-28
It works! Now how would we make this permanent? And how would I be able to do Fn+F2 to turn it off/on?

---

### Post by chili555 on 2011-04-28
> Now how would we make this permanent? ```
sudo su
echo "blacklist dell-laptop" >> /etc/modprobe.d/blacklist.conf
exit
```> And how would I be able to do Fn+F2 to turn it off/on? I don't know. It probably will just work; post back and let us know.

---

### Post by hiever1 on 2011-04-29
No dice. 

This scripts turns it on [http://dl.dropbox.com/u/2290825/wireless_script_1.2.sh](http://dl.dropbox.com/u/2290825/wireless_script_1.2.sh)

---

### Post by hiever1 on 2011-04-29
Now it works! But the Wifi Led is flashing how would I fix that?

---

### Post by chili555 on 2011-04-29
> **hiever1 said:**
> Now it works! But the Wifi Led is flashing how would I fix that?No idea; mine flashes on activity and I've learned to ignore it just like my ex-wife.

---

### Post by hiever1 on 2011-04-29
> **chili555 said:**
> No idea; mine flashes on activity and I've learned to ignore it just like my ex-wife.

Alright thanks for your help Chili :D

---

### Post by daddykevin13 on 2011-05-05
> **hiever1 said:**
> I can't turn my wireless card on. I have a Dell Inspirion 6400 with 
intel 3945abg card. I tried turning it on Fn+F2. Nothing. It worked fine in 10.10. Help please?

I have the same laptop Dell 6400 Inspiron. Same problem. Meerkat worked like a champ, never had an issue. Upgraded to Natty and no wifi. Can't turn on the adapter with Fn+F2 at all. Tried the steps you did and it unblocked the soft and hard, but still cannot get the wifi adapter to turn on. 
Any help would be greatly appreciated. I like the look of Natty, it looks promising. But if I can't get my wifi to work, I'm going back to Meerkat. Wait until they fix this problem. 

Thanks
Kevin

---

### Post by chili555 on 2011-05-05
> **daddykevin13 said:**
> I have the same laptop Dell 6400 Inspiron. Same problem. Meerkat worked like a champ, never had an issue. Upgraded to Natty and no wifi. Can't turn on the adapter with Fn+F2 at all. Tried the steps you did and it unblocked the soft and hard, but still cannot get the wifi adapter to turn on. 
Any help would be greatly appreciated. I like the look of Natty, it looks promising. But if I can't get my wifi to work, I'm going back to Meerkat. Wait until they fix this problem. 

Thanks
KevinPlease show us:```
sudo rmmod -f dell-laptop
sudo rfkill unblock all
sudo modprobe iwl3945
iwconfig
sudo iwlist wlan0 scan
```Some of the commands may produce no output; that's fine.

---

