---
title: "Alienware M17 Wireless doesn't work"
date: 2009-02-06
forum: Networking &amp; Wireless
---

### Post by MG101 on 2009-02-06
Hello everyone.

I'm new to Linux, but my last obstacle in having a monster machine is getting the wireless to work on Ubuntu 8.04.

I tried the following command to get some info: 
```

lspci -v | less

```

This is what I got:
```

09:00.0 Network controller: Realtek Semiconductor Co., Ltd. Unknown device 9199 (rev 22)
Subsystem: Realtek Semiconductor Co., Ltd. Unknown device 8199
Flags: bus master, fast devsel, latency 0. IRQ 10
I/O ports at 5000 [size=256]
Memory at f8400000 (32-bit, non-prefetchable) [size=16k]
Capabilities: <access denied>

```

Any help guys? Thanks

---

### Post by MG101 on 2009-02-07
OK, from Windows device manager I found my card to be a Realtek RTL8187SE.

Apparently there are drivers for it, no problem, except that those drivers are for Ubuntu 8.04 BUT 32-bit. I am running a 64-bit architecture...

I downloaded the driver that I apparently needed. It gave me an error "wrong architecture i386." I opened that .deb file and saw its components. In a file called control it says the architecture. Would it be harmless for me to just change this to AMD64 so Ubuntu thinks it is for 64bit instead of 32?

ThanOK, from Windows device manager I found my card to be a Realtek RTL8187SE.

Apparently there are drivers for it, no problem, except that those drivers are for Ubuntu 8.04 BUT 32-bit. I am running a 64-bit architecture...

I downloaded the driver that I apparently needed. It gave me an error "wrong architecture i386." I opened that .deb file and saw its components. In a file called control it says the architecture. Would it be harmless for me to just change this to AMD64 so Ubuntu thinks it is for 64bit instead of 32bit architecture?

Thank you

---

