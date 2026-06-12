---
title: "Hardware Not Detected - Solos Multiport PCI ADSL2+ Modem (4-port)"
date: 2010-10-22
forum: Networking &amp; Wireless
---

### Post by andypike on 2010-10-22
Hi,

I've just installed Zentyal (formally eBox) which is a firewall built on  Ubuntu server 10.04.  Unfortunately my PCI modem is not automatically  detected upon installation and the Zentyal community forum is not very  active.  Maybe someone here can help?

Is it possible to get the 4-port Solos Multiport PCI ADSL2+ Modem card ([http://www.traverse.com.au/productvi...product_id=116]("http://www.traverse.com.au/productview.php?product_id=116")) from Traverse Technologies working under Zentyal?

Apparently  the driver is included in kernel versions 2.6.29 and later  so I was  surprised that it was not automatically detected and working  upon  installation.  It is also available from [http://sourceforge.net/projects/openadsl/](http://sourceforge.net/projects/openadsl/).

Zentyal was able to detect their single port card, the Vicking PCI ADSL2+ ([http://www.traverse.com.au/productvi...product_id=115]("http://www.traverse.com.au/productview.php?product_id=115")).    This card worked out-the-box - all I had to do was enter my static IP   details!  Is there any way to achieve the same functionality with the   Solos 4 port?

Thanks in advance,
Andy

---

### Post by andypike on 2010-10-22
After checking /var/log/kern.log, it appears the card *is* automatically detected and the driver loaded:...

```

Oct 19 23:40:55 wellington kernel: [    6.860110] Solos PCI Driver Version 0.07
Oct 19 23:40:55 wellington kernel: [    6.860149]   alloc irq_desc for 21 on node -1
Oct 19 23:40:55 wellington kernel: [    6.860152]   alloc kstat_irqs on node -1
Oct 19 23:40:55 wellington kernel: [    6.860160] solos 0000:11:00.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
Oct 19 23:40:55 wellington kernel: [    6.860197] solos 0000:11:00.0: Solos FPGA Version 0.03 svn-38
Oct 19 23:40:55 wellington kernel: [    6.860334] solos 0000:11:00.0: Registered ATM device 0
Oct 19 23:40:55 wellington kernel: [    6.880175] solos 0000:11:00.0: Registered ATM device 1
Oct 19 23:40:55 wellington kernel: [    6.880294] solos 0000:11:00.0: Registered ATM device 2
Oct 19 23:40:55 wellington kernel: [    6.880408] solos 0000:11:00.0: Registered ATM device 3

```

... However, the card still does not work.  I don't get it!  The  card should be working but there is no network interface created when I  use ifconfig.

---

