---
title: "What did &quot;lspci -v | less&quot; tell me?"
date: 2009-03-29
forum: Networking &amp; Wireless
---

### Post by audit on 2009-03-29
I am so new I feel guilty writing a  question; but, how do I know what type of wireless hardware is inside my laptop? I typed "lspci -v | less" at the terminal and received the following information. What is it telling me?

00:1f.6 Signal processing controller: Intel Corporation 82801I (ICH9 Family) Thermal Subsystem (rev 03)
        Subsystem: Hewlett-Packard Company Device 360b
        Flags: fast devsel, IRQ 11
        Memory at 94704000 (64-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
        Subsystem: Hewlett-Packard Company Device 360b
        Flags: bus master, fast devsel, latency 0, IRQ 220
        I/O ports at 3000 [size=256]
        Memory at 90410000 (64-bit, prefetchable) [size=4K]
        Memory at 90400000 (64-bit, prefetchable) [size=64K]
        Expansion ROM at 90420000 [disabled] [size=128K]
        Capabilities: <access denied>
        Kernel driver in use: r8169
        Kernel modules: r8169

02:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
        Subsystem: Hewlett-Packard Company Device 137a
        Flags: fast devsel, IRQ 17
        Memory at 92600000 (64-bit, non-prefetchable) [disabled] [size=64K]
        Capabilities: <access denied>
        Kernel modules: ath_pci

---

### Post by pbasil on 2009-03-29
That does not seem to be the complete output. I can not see your network controller. 
Can you please copy the complete output for 

lspci

(no "-v", do not use "less")

---

### Post by pbasil on 2009-03-30
Execute following to know what lspci tells you :)
That is the way you consult the reference manual

man lspci

---

