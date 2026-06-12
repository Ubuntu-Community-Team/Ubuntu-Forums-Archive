---
title: "Atheros wireless card not working"
date: 2009-02-23
forum: Networking &amp; Wireless
---

### Post by jimmygreen99 on 2009-02-23
Hi, I need some help, 
For some reason, ever since I got a new laptop with a Atheros wifi card in it, I cannot use the wireless function!

I have dug around for hours trying to find some answers, and came up with this, when i type into the terminal:

lspci -v | less

this is the output:

03:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)
        Subsystem: Device 1a32:0303
        Flags: bus master, fast devsel, latency 0, IRQ 11
        Memory at f4600000 (64-bit, non-prefetchable) [size=64K]
        Capabilities: <access denied>

Does the access denied mean anything?

Thanks!!!

---

### Post by jimmygreen99 on 2009-02-25
Is there information that is missing that is turning people away? Sorry, I am somewhat new to Ubuntu so please help me out here, 

Thanks!

---

### Post by computer_freak_8 on 2009-02-25
> **jimmygreen99 said:**
> Does the access denied mean anything?
Try using sudo:
```
sudo lspci -v
```
The rest of the command you had is optional. It is mainly useful whey you have no GUI - that is, just the terminal. If you have a terminal window, you shouldn't need it, but you can still include it if you want to.
```
sudo lspci -v | less
```

---

