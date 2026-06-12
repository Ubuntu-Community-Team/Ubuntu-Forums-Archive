---
title: "AR9287 RF-Kill/Disabled?"
date: 2011-08-18
forum: Networking &amp; Wireless
---

### Post by cengbrecht on 2011-08-18
I am not exactly sure whats wrong here, but Ubuntu 11.04 reports that the Atheros card for my laptop ( AR9287) is disabled. When I try to turn it on using fn+F3 it does not do anything. 
I looked around and found out about RF-Kill, tried doing the sudo rfkill unblock 0 and it did not work, I attempted that with both 1 and 0 as I also have a gigabit lan card. Though I could see the block status of the eth0 card changing, the Soft block of the wireless card did not.

I have also tried unblocking the pci_ath card in modprobe.d and that also did not work after restarting.

If someone could help me, I am using a Acer Aspire 7551g with a Atheros wireless controller. Running Ubuntu 11.04 x64 AMD

Thanks for your time. :)

---

### Post by cengbrecht on 2011-08-18
Addendum.

```

0: acer-wireless: Wireless LAN
	Soft blocked: yes
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

```
```

craig:~$ sudo rfkill unblock 0
craig:~$ sudo rfkill list
0: acer-wireless: Wireless LAN
	Soft blocked: yes
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
craig:~$ 

```

---

### Post by cengbrecht on 2011-08-18
Alright, so after quite a lot of searching, and a lot of google'ing.

I have tried many methods.

From what I can tell, the addition of the file /etc/modprobe.d/ath9.conf with the single line:
```
options ath9k nohwcrypt=1
```

And secondly running this:
```
sudo modprobe -r acer-wmi
```

This alone does not fix the issue,
I have also run:
```
sudo ifconfig wlan0 up
```

This seem's to have activated my wireless card. I am not sure if it is going to keep being active after a restart, but some more testing shall see...

Then to see if things are working run:
```
iwlist scan
```

Although I did not receive any replies, I would like to thank the community for helping so many other people in so many ways. I can usually pull together what I need from that help. :)

So after a restart, you do have to reapply the second and third fixes again. I don't know how to write scripts yet, or how to make the Acer-wmi permanent.

---

