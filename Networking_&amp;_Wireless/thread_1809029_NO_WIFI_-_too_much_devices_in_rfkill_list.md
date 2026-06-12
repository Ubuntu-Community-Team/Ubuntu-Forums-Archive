---
title: "NO WIFI - too much devices in rfkill list"
date: 2011-07-21
forum: Networking &amp; Wireless
---

### Post by riso325 on 2011-07-21
hi, my problem is that wifi isnt working on my laptop problably because of some interference. Ive got a Broadcom BCM4313 chip on a Lenovo B560 notebook but as you can see in rfkill list, there is some acer wireless, which is probably causing the problem.
Thanks for your help :)


```
administrator@Lenovo-B560:~$ rfkill list
0: acer-wireless: Wireless LAN
	Soft blocked: yes
	Hard blocked: no
1: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
2: ideapad_wlan: Wireless LAN
	Soft blocked: no
	Hard blocked: no
3: ideapad_bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
4: brcmwl-0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

```

---

### Post by bkratz on 2011-07-21
Here is a good thread which explains how acer-wmi sometimes causes problems, esp see post 4.

[http://ubuntuforums.org/showthread.php?t=1790646&highlight=acer-wmi](http://ubuntuforums.org/showthread.php?t=1790646&highlight=acer-wmi)

[COLOR="Red"]just the first part of the post only![/COLOR]

---

### Post by riso325 on 2011-07-22
thanks ! **blacklisting acer-wmi** solved the problem !

---

### Post by bkratz on 2011-07-22
> **riso325 said:**
> thanks ! **blacklisting acer-wmi** solved the problem !



Glad to have helped--enjoy your wireless!

---

