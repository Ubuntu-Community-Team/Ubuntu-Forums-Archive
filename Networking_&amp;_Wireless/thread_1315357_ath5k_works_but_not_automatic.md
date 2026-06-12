---
title: "ath5k works but not automatic"
date: 2009-11-05
forum: Networking &amp; Wireless
---

### Post by ottosykora on 2009-11-05
I managed after lot of trying to make my atheros 5001 on my toshiba satelite M40 to operate.
Ubuntu 9.10, no windows drivers installed, hostapd deinstalled, the ath5k taken out of the blacklist by adding comment to its line.

Still ath5k does load correctly on boot.
When I go to terminal and enter sudo modprobe ath5k, then it starts and makes connection automatically.

Any hints as how to make it start on boot?

---

### Post by t0mppa on 2009-11-05
It should be automatic, after removing the blacklisting. You can add it to */etc/modules* though, just to be sure. Any modules listed there will get automatically loaded during boot.

---

### Post by ottosykora on 2009-11-05
> **t0mppa said:**
> It should be automatic, after removing the blacklisting. You can add it to */etc/modules* though, just to be sure. Any modules listed there will get automatically loaded during boot.

hmmm, the /etc/modules/ folder does not exist on my 9.10 in fact.

Tried to uncomment it all but no cure. 
So far did a sh script placed on my desktop containing the modprobe ath5k.

Even this works and will start the rest automatically , no errors, wifi-radar does not crash this way etc. 

Funny, although I mean I have enabled it everywhere, there is no trace of ath5k in dmesg log.

Have you any idea where else there can be something preventing it of probing ath5k?

---

### Post by ottosykora on 2009-11-05
OK solved at least for me:

there was an other blacklisting in a list madwifi.conf. I thought I have deinstalled madwifi in fact and that ath5k takes now over, so why there is this madwifi.conf still there? And it is still read somehow, since I tried to rename it (changed the conf to something else) and got some complains in the bash when modprobing by hand the ath5k.

Now I have removed the blacklist in this ??obsolete?? madwifi.conf as well and the ath5k is loaded at the end of the boot:

```
[    8.758312] ath5k 0000:06:02.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    8.758391] ath5k 0000:06:02.0: registered as 'phy0'



[    9.513545] ath5k phy0: Atheros AR2414 chip found (MAC: 0x79, PHY: 0x45)
```

---

### Post by t0mppa on 2009-11-05
> **ottosykora said:**
> hmmm, the /etc/modules/ folder does not exist on my 9.10 in fact.

It's a file, not a folder. And I'm pretty sure it does exist. However, you really don't need to use it anymore.

> **ottosykora said:**
> OK solved at least for me:

there was an other blacklisting in a list madwifi.conf. I thought I have deinstalled madwifi in fact and that ath5k takes now over, so why there is this madwifi.conf still there? And it is still read somehow, since I tried to rename it (changed the conf to something else) and got some complains in the bash when modprobing by hand the ath5k.

Now I have removed the blacklist in this ??obsolete?? madwifi.conf as well and the ath5k is loaded at the end of the boot

Ah yes, that explains it, was going to suggest it, but figured you had gone through all of them already. And you can delete the files or create new ones in that directory, if you want. It's just a way to organize the information better, instead of dumping it all in one long .conf file.

---

