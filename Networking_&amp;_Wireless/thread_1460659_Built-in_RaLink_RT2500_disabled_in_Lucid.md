---
title: "Built-in RaLink RT2500 disabled in Lucid"
date: 2010-04-23
forum: Networking &amp; Wireless
---

### Post by Ader_ on 2010-04-23
Hi!
I am on a Fujitsu Siemens Amilo L1310G which has a built-in RaLink RT2500 wireless network card. This has worked fairly well with every ditribution since I started using Ubuntu in Hardy.

I just installed Lucid RC, and here it is acting up. It claims that the card is disabled. 

lshw gives me the following output for the card:

```

           *-network:0 DISABLED
                description: Wireless interface
                product: RT2500 802.11g Cardbus/mini-PCI
                vendor: RaLink
                physical id: 1
                bus info: pci@0000:02:01.0
                logical name: wlan0
                version: 01
                serial: 00:14:a5:08:30:f9
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=rt2500pci latency=64 multicast=yes wireless=IEEE 802.11bg
                resources: irq:23 memory:d0204000-d0205fff

```

Now, the little led which specifies whether the card is enabled or not is off. But it has been in this state since Hardy without that being any hinderance to the card working. To enable it in Windows, I press a button which is not part of the "normal" keyboard, but this button does not seem to be working in Ubuntu. Is there any way of enabling the card through the command line?

I've also attached some other logs hoping that they might be of any help.

Thanks!

Rasmus

---

### Post by zob on 2010-05-02
There has been a kernel regression in 2.6.32 (10.04 kernel) which affects the rt2500 drivers built into the kernel.
This is kind of bad news. But there's a bug report. You can subscribe to it, to see what is happening.
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/539794](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/539794)
For now I just installed the 2.6.31 RT kernel which was the only old kernel I could find in repos. I fixes the problem, though it might bring others. It is certainly not as smooth as the 2.6.32-21.
You could also install 9.10...

Oh and have a look in your syslog or kern.log. It's getting spammed with errors - probably.

---

