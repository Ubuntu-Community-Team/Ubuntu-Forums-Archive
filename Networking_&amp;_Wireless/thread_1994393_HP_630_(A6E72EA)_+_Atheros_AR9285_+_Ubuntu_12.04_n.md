---
title: "HP 630 (A6E72EA) + Atheros AR9285 + Ubuntu 12.04 no wireless"
date: 2012-06-02
forum: Networking &amp; Wireless
---

### Post by ilpiero on 2012-06-02
Hi all
I can't manage to make my wireless adapter work on my HP 630 A6E72EA notebook.
I check "enable wireless" on the network manager applet but wireless keeps being disabled.
The hardware switch is on, I'm currently running xubuntu 12.04 , but i can try other versions if needed.

```

rfkill list all 

``` 
gives:
```

0: hp-wifi: Wireless LAN
	Soft blocked: yes
	Hard blocked: no
1: hp-bluetooth: Bluetooth
	Soft blocked: yes
	Hard blocked: no
2: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes
4: hci0: Bluetooth
	Soft blocked: yes
	Hard blocked: no

```


```

 dmesg | grep ath9k

```

gives

```
[    9.024973] ath9k 0000:02:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    9.024990] ath9k 0000:02:00.0: setting latency timer to 64
[    9.274019] ieee80211 phy0: Selected rate control algorithm 'ath9k_rate_control'
[    9.274566] Registered led device: ath9k-phy0
[  528.123767] ath9k 0000:02:00.0: restoring config space at offset 0xf (was 0x1ff, writing 0x10b)
[  528.123803] ath9k 0000:02:00.0: restoring config space at offset 0x4 (was 0x4, writing 0x94400004)
[  528.123812] ath9k 0000:02:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
[  528.123823] ath9k 0000:02:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100007)

```


any help is appreciated ;)

---

### Post by praseodym on 2012-06-03
Hi,

please show
```

lsmod
iwconfig
```
Does

```
sudo rfkill unblock all
```

help?

---

### Post by ilpiero on 2012-06-03
Thanks praseodym, i think i solved.
removed the notebook battery and reset the bios settings (that were already to default), wireless is working now. No idea of what was happening.

Sorry for the post, I'll mark the thread as solved.

---

