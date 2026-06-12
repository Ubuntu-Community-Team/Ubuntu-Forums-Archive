---
title: "Access denied to soundcards"
date: 2011-10-13
forum: Multimedia Software
---

### Post by debiant on 2011-10-13
The first bit is me SU:

03:05.0 Multimedia audio controller: Creative Labs SB0400 Audigy2 Value
	Subsystem: Creative Labs Device 4002
	Flags: bus master, medium devsel, latency 64, IRQ 20
	I/O ports at cf00 [size=64]
	Capabilities: [dc] Power Management version 2
	Kernel driver in use: EMU10K1_Audigy

root@LMD:/home/mike# exit
exit
mike@LMD:~$ lspci -v
03:05.0 Multimedia audio controller: Creative Labs SB0400 Audigy2 Value
	Subsystem: Creative Labs Device 4002
	Flags: bus master, medium devsel, latency 64, IRQ 20
	I/O ports at cf00 [size=64]
	Capabilities: <access denied>
	Kernel driver in use: EMU10K1_Audigy

If anyone can help with this I'll be extremely grateful! Haven't had a linux box since 9.10 and I miss it!  

:(

---

