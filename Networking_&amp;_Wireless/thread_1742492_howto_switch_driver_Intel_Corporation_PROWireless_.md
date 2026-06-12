---
title: "howto switch driver: Intel Corporation PRO/Wireless 3945ABG"
date: 2011-04-28
forum: Networking &amp; Wireless
---

### Post by nas123 on 2011-04-28
No wireless on HP nw9440 since 11.04 install.
ubuntu amd64



rfkill list

0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes
1: hp-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no
2: hp-bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
5: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no





lspci -v | less

10:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
        Subsystem: Hewlett-Packard Company Compaq 6710b or nx9420 Notebook
        Flags: bus master, fast devsel, latency 0, IRQ 46
        Memory at f4000000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>
        Kernel driver in use: iwl3945
        Kernel modules: iwl3945



[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsIntel](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsIntel)

wiki page reports possible working with driver:   ipw3945

How do I change the driver ?
Thanks

---

### Post by nas123 on 2011-04-28
Or maybe get this iwl3945 working instead of course.
Thanks

---

### Post by nas123 on 2011-04-29
OK SOLVED.

I have a LAN/WAN switcher in the BIOS turned on !

In other words unplug the cable and wireless turns on, plug cable back in and it turns off.

Thanks Ubuntu for working properly.

---

### Post by Nubnut on 2011-04-30
I have this very same proble. Except I dont have a lan/wan swithcher in the bios turned on. Im on a dell d430

lspci gives

0c:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
        Subsystem: Intel Corporation Device 1021
        Flags: bus master, fast devsel, latency 0, IRQ 44
        Memory at efdff000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>
        Kernel driver in use: iwl3945
        Kernel modules: iwl3945


Ronan

---

