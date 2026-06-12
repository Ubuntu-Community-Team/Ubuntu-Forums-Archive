---
title: "Hardware switch doesn't work for Atheros WiFi"
date: 2011-03-10
forum: Networking &amp; Wireless
---

### Post by TheMaritimeMan on 2011-03-10
Hello all, i'm running Ubuntu 10.10 32-bit on an Acer Aspire 3050 laptop with an Atheros AR5BMB5 WiFi card.

The problem i'm having is that the hardware switch to turn the WiFi on and off isn't working right. When I hit the switch to turn it off, the light doesn't turn off, and Ubuntu just disconnects from the network and searches for more WiFi networks - it doesn't say that the WiFi has been deactivated, and I don't think it is. When I hit the switch again, it finds my network and connects to it.

The lspci -v | less command gives me the following information for the WiFi:

```

08:04.0 Ethernet controller: Atheros Communications Inc. AR2413 802.11bg NIC (rev 01)
        Subsystem: AMBIT Microsystem Corp. Device 0418
        Flags: bus master, medium devsel, latency 168, IRQ 21
        Memory at d0200000 (32-bit, non-prefetchable) [size=64K]
        Capabilities: <access denied>
        Kernel driver in use: ath5k
        Kernel modules: ath5k

```It lists a different model of card, but it's using what I assume is the correct driver, so I don't know if that has anything to do with it. I've checked the card itself and it is a AR5BMB5.

I would like to fix it so the switch actually turns the WiFi off instead of just making it search for more networks (I assume it's not actually turning off), and perhaps make the light turn off as it should as well.

Thanks,
-Trent

---

### Post by TheMaritimeMan on 2011-03-10
Bump?

---

### Post by TheMaritimeMan on 2011-03-11
Bump.

---

### Post by kennedn on 2011-04-16
Im having the exact same problem, I've got the same wireless card as you and the light never switches off, but also when i turn my computer on I've got to keep playing with the switch until my computer recognizes that there are wireless networks. ¬_¬

Ive been searching around tons of forums all are saying different things but none have fixed this silly little problem yet *sigh*

---

### Post by Vi3GameHkr on 2011-06-02
I have had this problem forever, except my card is "Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 1)" but it uses the same drivers.  I've been fine with it as long as I don't disable the wireless via the hardware.  Well recently, I disabled it by accident now the wireless works in Windows 7, but not in either Ubuntu 11.04 or openSUSE.

---

### Post by josephmills on 2011-06-02
hit thee switch and then open your terminal and type in ```
rfkill list all 
``` this will show you what is or is not being blocked

---

### Post by Vi3GameHkr on 2011-06-02
josephmills, for me rfkill list all returns the following:
> 0: hp-wifi: Wireless LAN
        Soft blocked: yes
        Hard blocked: no
1: phy0: Wireless LAN
        Soft blocked: yes
        Hard blocked: no

So now I'm guessing the graphical interface is receiving the wrong info somehow, because when I click the WLAN button (next to the clock and volume and stuff), Enable Wireless is grayed out and it says "wireless is disabled by hardware switch."

A little "man"-power and I was able to figure out how to unblock the stuff on the software side and things work!  I really hate graphic glitches, but it's something we live with.

Thank you, josephmills, although I suppose I should have looked into the rfkill command earlier in my struggles.

---

