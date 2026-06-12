---
title: "rfkill no longer displays wireless"
date: 2012-08-27
forum: Networking &amp; Wireless
---

### Post by metra on 2012-08-27
Ages ago my wireless stopped showing on the Networking applet and no longer worked rfkill list displayed resulsrs for Bluetooth and WiFi. The WiFi was hard blocked, rfkill unblock all solved it.

After my laptop shutdown from running our of juice, oops, wireless doesn't even show.

Rfkill list returns nothing when the WiFi light is red and only returns results for Bluetooth when wireless is enabled. 

```
$ rfkill list
0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no

```

So, how can I find out what happened to my WiFi?

Thanks

Ubuntu 10.04 LTS on an HP HDX Premium Series

---

### Post by NikTh on 2012-08-27
Hi , 
please post the results of 
```
lspci -nnk | grep -iA2 net 
uname -r 
sudo lshw -C network
```also look for a combination keys switch like Fn+F1 ,F2 something, that turn on the wireless.
Maybe a hard switch exists also (button). 

Thanks

---

