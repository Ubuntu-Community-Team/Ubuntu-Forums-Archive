---
title: "Asus n61VG wireless problem"
date: 2011-01-02
forum: Networking &amp; Wireless
---

### Post by deezel86 on 2011-01-02
Hello,

I am dual booting ubuntu with win 7 and about a couple of months ago, my wireless card stopped working. On windows the driver was recognized and installed, but I couldnt enable it, function keys didn't work on both OSes.

I thought I would try to fix it today. I followed this excellent guide:

[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)

to determine what seems to be the problem with my laptop and apparently there is a hardware block according to the command rfkill list:

```
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes
1: hci0: Bluetooth
	Soft blocked: yes
	Hard blocked: no

```

I am obviously a total newbie here so I would appreciate any kind of help. I tried searching around but doesn't seem I'm getting anywhere.

Thanks in advance.

---

### Post by PatchesTheCaveman on 2011-01-02
That usually means your wireless switch is off.  Flip it if you have a physical switch, or press the wireless button, which might require that you push an Fn key and a button on the top of your keyboard.  Look in your laptop's manual if you're not sure.

---

