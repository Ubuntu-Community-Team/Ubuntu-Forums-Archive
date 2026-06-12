---
title: "Sound goes jerky then cuts out taking the wireless with it"
date: 2009-10-11
forum: Multimedia Software
---

### Post by Lord_ on 2009-10-11
Hi Everyone,

I have recently come back to Ubuntu from Fed10 (Its good to be back!) I am having some problems with my sound and wireless crashs when I am watching videos. (Both online and AVIs) At a random point the sound will start jerking like a stuck cd and the die. When it dies it also kills the wireless connection. Only a shutdown count to 10 and turn on fixes this, a reboot does not normally work. What I am looking for is two this, assistance with how to fix this, and if someone could tell me how to reset/reload the wireless and sound so I do not have to reboot if it does happen. 

I have some output below, please let me know if there is anything else you would like me to post.

uname -a
Linux donkey-box 2.6.28-15-generic #52-Ubuntu SMP Wed Sep 9 10:49:34 UTC 2009 i686 GNU/Linux

lspci -v    (Sound Card and Wireless card)
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 02)
	Subsystem: Toshiba America Info Systems Device ff10
	Flags: bus master, 66MHz, slow devsel, latency 64, IRQ 17
	Memory at c0003400 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: ATI IXP AC97 controller
	Kernel modules: snd-atiixp

02:04.0 Ethernet controller: Atheros Communications Inc. AR2413 802.11bg NIC (rev 01)
	Subsystem: Askey Computer Corp. Device 7094
	Flags: bus master, medium devsel, latency 168, IRQ 17
	Memory at c0200000 (32-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>
	Kernel driver in use: ath5k_pci
	Kernel modules: ath_pci, ath5k

---

### Post by Lord_ on 2009-10-12
ok I've been reading up and I think I can reset the sound and wireless with modprobe. I can't test this until I get home but anything will be better than having to constantly restart.

Does anyone have any ideas how I can stabilise the sound?

---

