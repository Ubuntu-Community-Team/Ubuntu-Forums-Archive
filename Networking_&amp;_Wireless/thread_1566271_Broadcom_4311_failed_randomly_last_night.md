---
title: "Broadcom 4311 failed randomly last night"
date: 2010-09-02
forum: Networking &amp; Wireless
---

### Post by night_fox on 2010-09-02
Hello!!!!!!

Overnight, my wifi stopped working. In the GNOME network manager applet, the "Enable wireless" option is greyed out, and it tells me that wireless is disabled. When I tried doing sudo ifconfig wlan0 up, I get:

```
SIOCSIFFLAGS: Unknown error 132
```

My wireless card is a Broadcom 4311, on a dell laptop.

I found some stuff in a somewhat related post which told me to do:

```

#rfkill list

0: dell-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: yes
2: phy1: Wireless LAN
	Soft blocked: no
	Hard blocked: yes

```

I've tried doing "rfkill unblock all" with the b43 kernel module loaded and unloaded and nothing happens. What is the problem? If someone could help me out, it would be much appreciated!

---

### Post by Tracy177 on 2010-09-02
> **night_fox said:**
> Hello!!!!!!

Overnight, my wifi stopped working. In the GNOME network manager applet, the "Enable wireless" option is greyed out, and it tells me that wireless is disabled. When I tried doing sudo ifconfig wlan0 up, I get:

```
SIOCSIFFLAGS: Unknown error 132
```My wireless card is a Broadcom 4311, on a dell laptop.

I found some stuff in a somewhat related post which told me to do:

```

#rfkill list

0: dell-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
2: phy1: Wireless LAN
    Soft blocked: no
    Hard blocked: yes

```I've tried doing "rfkill unblock all" with the b43 kernel module loaded and unloaded and nothing happens. What is the problem? If someone could help me out, it would be much appreciated!


can u paste your dmesg ? or just check up on the bottom if there is anything missing for your card

---

### Post by night_fox on 2010-09-02
Ah. thats embarrassing. While playing GTA San andreas I accidentally pressed the wifi on/off key. Sorry!

---

### Post by Tracy177 on 2010-09-02
> **night_fox said:**
> Ah. thats embarrassing. While playing GTA San andreas I accidentally pressed the wifi on/off key. Sorry!


hehehhehehehehehehheeh

---

