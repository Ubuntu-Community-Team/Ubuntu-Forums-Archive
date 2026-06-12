---
title: "Dude, where's my ethernet?"
date: 2010-02-03
forum: Networking &amp; Wireless
---

### Post by detroit/zero on 2010-02-03
Toshiba Satellite a135-s4527.

Wireless is already installed and works great. However, when I disable wireless networking, network-manager doesn't default back to a wired connection.

Further investigation shows no eth0 device on my system, only loopback and wireless when it's enabled.

No amount of doing will allow me to create, set up, or otherwise configure any sort of wired device.

What gives?

---

### Post by ubudog on 2010-02-03
Try this: ```
ifconfig eth0 up
```

---

### Post by detroit/zero on 2010-02-03
> **ubudog said:**
> Try this: ```
ifconfig eth0 up
```
```
ERROR while getting interface flags: No such device
```

---

### Post by ubudog on 2010-02-03
Try replacing eth0 with eth1.

---

### Post by detroit/zero on 2010-02-03
Same error.

---

### Post by warfacegod on 2010-02-03
Dumb question, ...do you *have* an ethernet card?


Post:

```
lspci
```

---

### Post by detroit/zero on 2010-02-03
I can't post lspci because I can't get the computer online.

Yes, there's an ethernet card. It works in Windows, and in various other Linux distros. I've just never had to hand-configure it before.

---

### Post by ubudog on 2010-02-03
You don't need to be online to do lspci.

---

### Post by chili555 on 2010-02-03
Actually, all we really need is:```
lspci -nn | grep Ethernet
```Write it out on the back of the phone bill and post it here.

---

### Post by detroit/zero on 2010-02-03
The ethernet controller doesn't even show up in my lspci any more - just the wireless card.

Here's the ethernet details from an[ lspci I posted somewhere back in October of 2008]("http://ubuntuforums.org/archive/index.php/t-654058.html"):
```
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 01)
    Subsystem: Toshiba America Info Systems Unknown device ff00
    Flags: bus master, fast devsel, latency 0, IRQ 220
    I/O ports at 4000 [size=256]
    Memory at da000000 (64-bit, non-prefetchable) [size=4K]
    [virtual] Expansion ROM at d4000000 [disabled] [size=64K]
    Capabilities: <access denied>
```

Right now, only the wireless card is being recognized. That doesn't make much sense, because you can't have a wireless card without ethernet for it to interface with.

---

### Post by warfacegod on 2010-02-03
> **detroit/zero said:**
> The ethernet controller doesn't even show up in my lspci any more - just the wireless card.

Here's the ethernet details from an[ lspci I posted somewhere back in October of 2008]("http://ubuntuforums.org/archive/index.php/t-654058.html"):
```
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 01)
    Subsystem: Toshiba America Info Systems Unknown device ff00
    Flags: bus master, fast devsel, latency 0, IRQ 220
    I/O ports at 4000 [size=256]
    Memory at da000000 (64-bit, non-prefetchable) [size=4K]
    [virtual] Expansion ROM at d4000000 [disabled] [size=64K]
    Capabilities: <access denied>
```

Right now, only the wireless card is being recognized. That doesn't make much sense, because you can't have a wireless card without ethernet for it to interface with.

The wireless card ought to be completely separate from the wired one. The one does not depend on the other for accessing the net. If you removed the wired card, your wireless will should work.

---

### Post by detroit/zero on 2010-02-04
> **warfacegod said:**
> The wireless card ought to be completely separate from the wired one. The one does not depend on the other for accessing the net. If you removed the wired card, your wireless will should work.
Well, OK, that's all well and good.

I'd still like to know why the ethernet card isn't listed in my lspci output, isn't detected, and doesn't work in my Ubuntu install when it's always worked before (going all the way back to Feisty Fawn) and still does work in a Vista and Windows 7 install, or any distros livecd session on the same computer.

---

### Post by warfacegod on 2010-02-04
That, I have no explanation for.

---

