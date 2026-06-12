---
title: "Belkin F5D7010"
date: 2010-03-29
forum: Networking &amp; Wireless
---

### Post by pycoed on 2010-03-29
As a Linux newbie, trying to establish a Microshaft free zone & flushed with success after installing  Ubuntu 9.04 on my home PC ( fine in every respect! , I've just installed Xubuntu 9.1 on an old  Dell Inspiron 1150 with 768M RAM & am very happy with it too.

However, I have a weird problem with the wireless network card. Its a Belkin F5D7010 which Xubuntu recognised fine & connected OK. However even within 3 feet of my wireless router (a BT Home hub) it connects only at 1 mb/s & shows only 1 or 2 bars. This I can live with.
But periodically it will lose connection & will not renegatiate that connection. It asks for the WEP key, but will never re-connect. If I reboot, the connection is remade & all is well for an hour or two until the wireless link is  lost, then I have to reboot again (it's like using bl**dy Windows 95!).
Any pointers as to how to remedy this would be highly appreciated!

---

### Post by inobe on 2010-03-29
welcome to the ubuntu forums.

i have the 7050 and i noticed when i'm too close to the router the signal weakens, i get 80% 20+ foot away.

also seems to work better using wpa2 rather than wep.

---

### Post by coffeecat on 2010-03-29
@pycoed, just to clarify - you do mean a F5D7010 which is a PCMCIA card? Not a F5D7050 which is a USB device? If you look here:

[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsBelkin#PCMCIA](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsBelkin#PCMCIA)

... you'll see that there are a number of different chipsets in the F5D7010 depending on the revision number. Don't take that link too literally. It's a bit neglected in the F5D7010 entries - last updated between 2006 to 2008. The Atheros ought to work out of the box now, I would have thought.

Anyway - we need to know the chipset. Post the terminal output of:

```
lspci | grep Wireless
```If that doesn't give you anything, try:

```
lspci | grep 802.11
```

---

### Post by pycoed on 2010-03-30
> **inobe said:**
> welcome to the ubuntu forums.

i have the 7050 and i noticed when i'm too close to the router the signal weakens, i get 80% 20+ foot away.

also seems to work better using wpa2 rather than wep.

Well it doesn't seem to degrade any further when I move to the living room, about 25 feet away! But I never get above 1 bar on the little connection icon. I'll try WPA2 & see if it makes a difference. Cheers!

---

### Post by pycoed on 2010-03-30
> **coffeecat said:**
> @pycoed, just to clarify - you do mean a F5D7010 which is a PCMCIA card? Not a F5D7050 which is a USB device? If you look here:

[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsBelkin#PCMCIA](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsBelkin#PCMCIA)

... you'll see that there are a number of different chipsets in the F5D7010 depending on the revision number. Don't take that link too literally. It's a bit neglected in the F5D7010 entries - last updated between 2006 to 2008. The Atheros ought to work out of the box now, I would have thought.

Anyway - we need to know the chipset. Post the terminal output of:

```
lspci | grep Wireless
```If that doesn't give you anything, try:

```
lspci | grep 802.11
```

Hi,
Yes it is the 7010 PCMCIA card version on Xubuntu 9.10 which did work out of the box - until it droppped connection - then only reboots seem to re-establish it
 Can't get either of those commands to run, but "lspci" by itself returns  two ethernet controllers, one is listed as 
Broadcom Corporation BCM 4401 100Base-T (rev01)
& the other as 
**Belkin Device 701f (rev 20)**

PCI bridge is listed as 
Intel Corporation 82801 Mobile PCI Bridge (rev 81)
Cheers!

---

### Post by coffeecat on 2010-03-30
> **pycoed said:**
> Can't get either of those commands to run

:sigh: - With most manufacturers' devices you get either 'Wireless' or '802.11' in the lspci line for a wireless device (seems logical), but not Belkin it seems. Who call a wireless device an ethernet device. To keep us on our toes no doubt. :rolleyes:

Anyway....

> **pycoed said:**
> **Belkin Device 701f (rev 20)**

It's the 701f ID number that's important. Googling around told me that this was a Realtek chipset. And then I found this thread:

[http://ubuntuforums.org/showthread.php?t=1119015](http://ubuntuforums.org/showthread.php?t=1119015)

Which I'd forgotten all about. :p It's a bit dated because both the OP and I were using Intrepid (8.10). Also, my Belkin PCI card has a different identifier (700f), but both the OP's card and mine were using the same driver - rtl8180 - which is what you are probably using. You might want to see what the output of 'lspci -v' is for you - just the Belkin bit.

Which doesn't really get us much further. All I can say is that when I used that card (I don't now), WPA worked OK, but the signal strength was always misreported as being low.

---

### Post by pycoed on 2010-03-30
Which I'd forgotten all about. :p It's a bit dated because both the OP and I were using Intrepid (8.10). Also, my Belkin PCI card has a different identifier (700f), but both the OP's card and mine were using the same driver - rtl8180 - which is what you are probably using. You might want to see what the output of 'lspci -v' is for you - just the Belkin bit.

Which doesn't really get us much further. All I can say is that when I used that card (I don't now), WPA worked OK, but the signal strength was always misreported as being low.[/QUOTE]

lspci - v returns :-

03:00.0 Ethernet controller: Belkin Device 701f (rev 20)
	Subsystem: Belkin Device 701f
	Flags: bus master, medium devsel, latency 64, IRQ 11
	I/O ports at d000 [size=256]
	Memory at f8000000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: rtl8180
	Kernel modules: rtl8180

So - it looks like it IS rtl8180.

Cheers!

---

