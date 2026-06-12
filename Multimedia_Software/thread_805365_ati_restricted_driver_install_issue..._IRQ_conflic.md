---
title: "ati restricted driver install issue... IRQ conflict?"
date: 2008-05-23
forum: Multimedia Software
---

### Post by ouch67 on 2008-05-23
So whenever a new ubuntu comes out it manages to screw up my video driver I can usually fix it, except now I'm getting an error I havn't seen before. anyone have any ideas on how to fix this?




May 23 00:25:23 2-8ghz kernel: [43137.909895] [fglrx] AGP detected, AgpState   = 0x1f004a1b (hardware caps of chipset)
May 23 00:25:23 2-8ghz kernel: [43137.910786] agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
May 23 00:25:23 2-8ghz kernel: [43137.910827] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
May 23 00:25:23 2-8ghz kernel: [43137.910985] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
May 23 00:25:23 2-8ghz kernel: [43137.911361] [fglrx] AGP enabled,  AgpCommand = 0x1f004312 (selected caps)
May 23 00:25:23 2-8ghz kernel: [43138.121746] [fglrx:fireglAsyncioIntEnableMsgHandler] *ERROR* IRQMGR returned error 1 when trying to enable interrupt source 20008000
May 23 00:25:23 2-8ghz kernel: [43138.121756] [fglrx] Receive enable interrupt message with irqEnableMask: 20008000
May 23 00:25:23 2-8ghz kernel: [43138.121773] [fglrx:fireglAsyncioIntEnableMsgHandler] *ERROR* IRQMGR returned error 1 when trying to enable interrupt source 10000000
May 23 00:25:23 2-8ghz kernel: [43138.121779] [fglrx] Receive enable interrupt message with irqEnableMask: 10000000



oh, I have an radeon 9700 pro trying to install it on the new hardy herring.

fglrxinfo says I'm using mesa for everything and direct rendering is disabled despite my efforts... :(

---

### Post by MurDoK on 2008-09-27
Today I have seen a similar issue:

[360663.776727] [fglrx:fireglAsyncioIntEnableMsgHandler] *ERROR* IRQMGR returned error 1 when trying to enable interrupt source 10000000
[360663.776736] [fglrx] Receive enable interrupt message with irqEnableMask: 10000000
[360672.983371] [fglrx] interrupt source 10000000 successfully disabled!
[360672.983377] [fglrx] enable ID = 0x00000001
[360672.983379] [fglrx] Receive disable interrupt message with irqEnableMask: 10000000; dwIRQEnableId: 00000001
[360673.754298] [fglrx:firegl_lock_free] *ERROR* lock was not held by 1! (*lock=0x00000000)
[360673.754307] [fglrx:firegl_unlock] *ERROR* firegl_lock_free failed!

Using Hardy 8.04 fully updated.
I don't know what exactly has caused it because my computer has been 10 days powered

---

