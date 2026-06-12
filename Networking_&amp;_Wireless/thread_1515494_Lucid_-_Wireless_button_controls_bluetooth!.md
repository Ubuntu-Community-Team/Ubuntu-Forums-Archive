---
title: "Lucid - Wireless button controls bluetooth!?"
date: 2010-06-22
forum: Networking &amp; Wireless
---

### Post by SupaRice on 2010-06-22
So, after installing Lucid wireless doesn't work for me.  When I click on the network icon on the status bar, it shows "wireless is disabled".

With that message, I press the wifi button on my HP laptop and it turns off my blue-tooth, without changing the status of my wifi.

What gives?

I found this rfkill command in another thread:

Before doing anything, after bootup:

```
$ rfkill list
0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes
```

After pressing the wifi button (light goes out):
```
$ rfkill list
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes
```

Pressing wifi button again (light comes back on):
```
$ rfkill list
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes
2: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
```


lspci:
```
08:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
```

---

### Post by SupaRice on 2010-06-22
If I need to gather more info from my system I can, this is all I knew how to do.  Any help is appreciated.  Thanks

---

### Post by SupaRice on 2010-06-23
Doh!  It was somehow disabled in BIOS!?

---

