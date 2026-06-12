---
title: "Network wireless adapter won't turn on"
date: 2011-02-05
forum: Networking &amp; Wireless
---

### Post by gufide on 2011-02-05
Hi, my network adapter won't turn on. It worked before. There's my card in the output of 
lspci -v | less

```
07:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)
        Subsystem: Hewlett-Packard Company Device 1381
        Flags: bus master, fast devsel, latency 0, IRQ 23
        Memory at c2000000 (64-bit, non-prefetchable) [size=64K]
        Capabilities: <access denied>
        Kernel driver in use: ath9k
        Kernel modules: ath9k
```and a screenshot:
[ATTACH]182789[/ATTACH]

anyone know how to solve it? My wireless light is alway red (off). When I click on the button off/on it does nothing...

---

### Post by gufide on 2011-02-06
please someone

---

### Post by gufide on 2011-02-06
this is my nm-tool output:
```
Device: wlan0
  Type:              802.11 WiFi
  Driver:            ath9k
  State:             unavailable
  Default:           no
  HW Address:        00:23:4D:A7:A7:9D

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 

```

his state is unavalable. I just want to know how to force it to be enable

---

### Post by gufide on 2011-02-06
finally, there's my rfkill list output:

```
0: hp-wifi: Wireless LAN
    Soft blocked: yes
    Hard blocked: no

```

it is soft blocked... so, I just want to know how to unblock it please, I don't found it on the web...

---

### Post by gufide on 2011-02-06
[http://ohioloco.ubuntuforums.org/showthread.php?t=1604665](http://ohioloco.ubuntuforums.org/showthread.php?t=1604665)

so... this thread is solved... damn! I'm alone in my own thread and I got a solution for myself... :cool:

---

### Post by mr_y82 on 2011-06-01
My wife has been using linux for a while now on her dell inspiron 1501 laptop... I convinced her to switch... so far both the b43 and STA driver have worked for linux mint 9 gnome and 10 lxde/xfce, xubuntu 10, bodhi, and prob. a couple others...

weird thing though... when we upgraded to 11, and after various fresh installs, including a trial with lubuntu, the STA driver would not work... I haven't checked to see if they offer the B43 driver on package manager, but it doesn't show up in "additional drivers" anymore... I know it worked with mint 10 lxde, but I don't want t use the B43 driver anyway... the STA is better...

anyway... the STA driver appears to be installed and active, but the wireless network is not detected and I have not been able to get it to work... switched back to mint 10 lxde and it runs like a charm again with either driver...

[SIZE=3]any clues on how to get the wireless network to show up on xubuntu 10 w/ STA driver on inspiron 1501?[/SIZE]

---

### Post by mr_y82 on 2011-06-01
also props on solving your own problem... I got a kick out of that...  you just had to put your thoughts down and work through it... 

I was a DOS kid and caved to windows... tinkered in linux and started taking it seriously a couple years ago... Ubuntu-based stuff is so simple and has so much support and software that I haven't learned as much as I should have... back in the day when I got redhat installed on a AMD 233 I felt like I had really accomplished something... they didn't make it easy back then.

---

### Post by chili555 on 2011-06-01
How about letting us see:```
rfkill list all
```Thanks.

---

