---
title: "More network problems - Realtek"
date: 2006-06-03
forum: Networking &amp; Wireless
---

### Post by astrauss on 2006-06-03
Hi

I'm new to Linux. I cannot get my ethernet card to work at all (Realtek onboard on Gigabyte mobo). 

I've been searching the Ubuntu forums and have tried the load dmfe and blacklist tulip tip mentioned elsewhere, but no luck. I've also tried setting a fixed IP but even though Ubuntu shows the fixed IP there still is no communication with my router (the connected/ctivity light on the router never comes on). It almost seems that the network card is disabled (not sure how to check, but there's no error messages jumping out at me in the Device Manager)

Any help would be gretly appreciated as I would love to learn more about Ubuntu and Linux.

---

### Post by khedron on 2006-06-03
[QUOTE=astrauss]It almost seems that the network card is disabled (not sure how to check)[/QUOTE]

If you are in GNOME, go to System>Administration>Networking. Your network interfaces should show up there. I had an ethernet interface once that I had to manually activate from that menu.

I'm trying to get networking in my Ubuntu at the moment, so I'm afraid I can't help you with your main problem.

---

### Post by astrauss on 2006-06-03
Tried that already, but still no luck

---

### Post by astrauss on 2006-06-03
I just removed my PCI WIFI card from the same PC and now the ethernet card works perfectly.

---

### Post by polo_step on 2006-06-04
[QUOTE=astrauss]I just removed my PCI WIFI card from the same PC and now the ethernet card works perfectly.[/QUOTE]
[FONT="Courier New"]But...but...now your wireless won't work! :mrgreen: 

Just kidding...I can't get my Ralink wireless to really do anything productive, though it scans with iwlist and at least finds the AP.  ](*,) [/FONT]

---

### Post by Robsteranium on 2007-06-07
I'm suffering from the same problem on a xubuntu 7.04 installation.

The same machine running on RHL/ FC2/ XP Pro has no problem identifying/ using the ethernet card.  It's an old 10Mbs Realtek (I think 8139).  None of the following commands (that I've seen suggested elsewhere) have any productive results:
```
lspci | grep -i ethernet
dmesg | grep eth
sudo modprobe 8139cp
sudo modprobe 8139too
```

ifconfig only reports the loopback address.

I'm at a loss and I've not got a WIFI card to remove!

---

### Post by KennyMac on 2008-07-23
> **Robsteranium said:**
> I'm suffering from the same problem on a xubuntu 7.04 installation.

The same machine running on RHL/ FC2/ XP Pro has no problem identifying/ using the ethernet card.  It's an old 10Mbs Realtek (I think 8139).  None of the following commands (that I've seen suggested elsewhere) have any productive results:
```
lspci | grep -i ethernet
dmesg | grep eth
sudo modprobe 8139cp
sudo modprobe 8139too
```

ifconfig only reports the loopback address.

I'm at a loss and I've not got a WIFI card to remove!
Check out the other discussion thread on this.

[http://ubuntuforums.org/showthread.php?t=536373](http://ubuntuforums.org/showthread.php?t=536373)

---

