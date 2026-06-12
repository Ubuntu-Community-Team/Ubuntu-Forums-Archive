---
title: "How to load balance interrupts?"
date: 2012-12-19
forum: Networking &amp; Wireless
---

### Post by leblakedan on 2012-12-19
Hi,

I run a server that is frequently under denial of service attacks. We filter these attacks with iptables/ipset and its manageable for the most part.

One issue we have is that the interrupts a second spikes during a attack (100-500k PPS) and it causes only one CPU core to spike. What would be the cause for this? How can we load balance the interrupts across all cores? We believe if we could load balance the interrupts we should be able to handle 1 million PPS. Right now the limitation is the interrupts are all on one core...

MSI-X already seems to be enabled:

root@serverf683:~/ipset-6.16.1# grep -i msi /var/log/dmesg
[    1.512002] e1000e 0000:01:00.0: irq 40 for MSI/MSI-X
[    1.512009] e1000e 0000:01:00.0: irq 41 for MSI/MSI-X
[    1.512016] e1000e 0000:01:00.0: irq 42 for MSI/MSI-X
[    1.520536] ahci 0000:00:1f.2: irq 43 for MSI/MSI-X
[    1.624536] e1000e 0000:02:00.0: irq 44 for MSI/MSI-X
[    1.624541] e1000e 0000:02:00.0: irq 45 for MSI/MSI-X
[    1.624545] e1000e 0000:02:00.0: irq 46 for MSI/MSI-X
[    7.074374] ioatdma 0000:00:16.0: irq 47 for MSI/MSI-X
[    7.074629] ioatdma 0000:00:16.1: irq 48 for MSI/MSI-X
[    7.074827] ioatdma 0000:00:16.2: irq 49 for MSI/MSI-X
[    7.075012] ioatdma 0000:00:16.3: irq 50 for MSI/MSI-X
[    7.075194] ioatdma 0000:00:16.4: irq 51 for MSI/MSI-X
[    7.075373] ioatdma 0000:00:16.5: irq 52 for MSI/MSI-X
[    7.075551] ioatdma 0000:00:16.6: irq 53 for MSI/MSI-X
[    7.075728] ioatdma 0000:00:16.7: irq 54 for MSI/MSI-X
root@serverf683:~/ipset-6.16.1#

---

