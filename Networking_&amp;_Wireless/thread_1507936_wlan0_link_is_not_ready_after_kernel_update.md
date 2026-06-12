---
title: "wlan0: link is not ready after kernel update"
date: 2010-06-12
forum: Networking &amp; Wireless
---

### Post by 4logon on 2010-06-12
after my last kernel update to 2.6.32-22-generic, my wlan card(s) doesn't work!.


look at the output of dmesg...

dmesg
[  980.104134] pcmcia_socket pcmcia_socket0: pccard: CardBus card inserted into slot 0
[  980.104199] pci 0000:03:00.0: reg 10 32bit mmio: [0x000000-0x00ffff]
[  980.104514] ath5k 0000:03:00.0: enabling device (0000 -> 0002)
[  980.104539] ath5k 0000:03:00.0: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
[  980.104650] ath5k 0000:03:00.0: registered as 'phy4'
[  980.459501] ath: EEPROM regdomain: 0x60
[  980.459511] ath: EEPROM indicates we should expect a direct regpair map
[  980.459525] ath: Country alpha2 being used: 00
[  980.459532] ath: Regpair used: 0x60
[  980.473724] phy4: Selected rate control algorithm 'minstrel'
[  980.487847] ath5k phy4: Atheros AR5212 chip found (MAC: 0x56, PHY: 0x41)
[  980.487862] ath5k phy4: RF5111 5GHz radio found (0x17)
[  980.487870] ath5k phy4: RF2111 2GHz radio found (0x23)
[  980.782901] ADDRCONF(NETDEV_UP): wlan0: link is not ready


loaded drivers:
lsmod | grep ath
ath5k                 121792  0 
mac80211              204922  1 ath5k
ath                     7611  1 ath5k
cfg80211              126485  4 orinoco,ath5k,mac80211,ath
led_class               2864  2 ath5k,thinkpad_acpi

any idea??
bye 4logon.

---

### Post by jnorthr on 2010-06-12
i'm having a similar prob on upgrade from 9.10 to 10.04, so i'm taking the previous kernel as a starting point cos i know my card worked fine in both 9.04 and after upgrade to 9.10 but NOT after upgrade to 10.04. So i'll be looking at the kernel first.

---

### Post by 4logon on 2010-06-17
in the meantime I found a solution as workaround.
To fix the problem I had removed the network-manger* packages and add the necessary entries manual to /etc/network/interfaces. After that run command /etc/init.d/networking restart

now wlan works fine.

so i think the problem is around the network-manger software.

by. 4logon.

---

