---
title: "Netgear FA310TX woos"
date: 2005-03-19
forum: Networking &amp; Wireless
---

### Post by Terryg on 2005-03-19
Greeting,

I'm new here and I have been searching through the posts to find a resolution to my problem and no go. I just installed a Linksys WRT56G wireless router and am composing this message via my main box (wired) running mdk 10.1. 

I installed ubuntu 4.10 on a box I eventually intend to place a wireless card in and give to my mom to use. However, I am just trying to get it on the internet to update the system. Below is  a segment of my syslog file:

Mar 19 06:26:55 localhost syslogd 1.4.1#14ubuntu4: restart.
Mar 19 06:26:55 localhost udev[17209]: removing device node '/dev/vcs12'
Mar 19 06:26:55 localhost udev[17221]: removing device node '/dev/vcsa12'
Mar 19 06:26:55 localhost udev[17225]: creating device node '/dev/vcsa12'
Mar 19 06:26:55 localhost udev[17222]: creating device node '/dev/vcs12'

<snip>

Mar 19 16:30:21 localhost dhclient: Internet Systems Consortium DHCP Client V3.0.1rc14
Mar 19 16:30:21 localhost dhclient: Copyright 2004 Internet Systems Consortium.
Mar 19 16:30:21 localhost dhclient: All rights reserved.
Mar 19 16:30:21 localhost dhclient: For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)
Mar 19 16:30:21 localhost dhclient: 
Mar 19 16:30:21 localhost dhclient: sit0: unknown hardware address type 776

and ifconfig shows sit0, but what is it?

Mar 19 16:30:22 localhost kernel: irq 10: nobody cared!
Mar 19 16:30:22 localhost kernel:  [__report_bad_irq+49/115] __report_bad_irq+0x31/0x73
Mar 19 16:30:22 localhost kernel:  [note_interrupt+76/111] note_interrupt+0x4c/0x6f
Mar 19 16:30:22 localhost kernel:  [do_IRQ+146/249] do_IRQ+0x92/0xf9
Mar 19 16:30:22 localhost kernel:  [common_interrupt+24/32] common_interrupt+0x18/0x20
Mar 19 16:30:22 localhost kernel:  [__do_softirq+44/115] __do_softirq+0x2c/0x73
Mar 19 16:30:22 localhost kernel:  [do_softirq+34/38] do_softirq+0x22/0x26
Mar 19 16:30:22 localhost kernel:  [do_IRQ+229/249] do_IRQ+0xe5/0xf9
Mar 19 16:30:22 localhost kernel:  [common_interrupt+24/32] common_interrupt+0x18/0x20
Mar 19 16:30:22 localhost kernel:  [setup_irq+168/205] setup_irq+0xa8/0xcd
Mar 19 16:30:22 localhost kernel:  [__crc_tcp_transmit_skb+3033061/3143968] tulip_interrupt+0x0/0x69a [tulip]
Mar 19 16:30:22 localhost kernel:  [request_irq+140/162] request_irq+0x8c/0xa2
Mar 19 16:30:22 localhost kernel:  [__crc_tcp_transmit_skb+3041004/3143968] tulip_open+0x1a/0x3a [tulip]
Mar 19 16:30:22 localhost kernel:  [__crc_tcp_transmit_skb+3033061/3143968] tulip_interrupt+0x0/0x69a [tulip]
Mar 19 16:30:22 localhost kernel:  [dev_open+96/197] dev_open+0x60/0xc5
Mar 19 16:30:22 localhost kernel:  [dev_change_flags+74/238] dev_change_flags+0x4a/0xee
Mar 19 16:30:22 localhost kernel:  [devinet_ioctl+591/1268] devinet_ioctl+0x24f/0x4f4
Mar 19 16:30:22 localhost kernel:  [inet_ioctl+69/111] inet_ioctl+0x45/0x6f
Mar 19 16:30:22 localhost kernel:  [sock_ioctl+575/611] sock_ioctl+0x23f/0x263
Mar 19 16:30:22 localhost kernel:  [sys_ioctl+459/528] sys_ioctl+0x1cb/0x210
Mar 19 16:30:22 localhost kernel:  [syscall_call+7/11] syscall_call+0x7/0xb
Mar 19 16:30:22 localhost kernel: handlers:
Mar 19 16:30:22 localhost kernel: [__crc_tcp_transmit_skb+3033061/3143968] (tulip_interrupt+0x0/0x69a [tulip])

Doing an lsmod shows the dulip module loaded

Mar 19 16:30:22 localhost kernel: Disabling IRQ #10

Why would it do that?

Mar 19 16:30:23 localhost dhclient: sit0: unknown hardware address type 776
Mar 19 16:30:23 localhost dhclient: Listening on LPF/eth0/00:a0:cc:d1:5f:83
Mar 19 16:30:23 localhost dhclient: Sending on   LPF/eth0/00:a0:cc:d1:5f:83
Mar 19 16:30:23 localhost dhclient: Sending on   Socket/fallback
Mar 19 16:30:24 localhost dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
Mar 19 16:30:25 localhost kernel: eth0: Setting full-duplex based on MII#1 link partner capability of 45e1.
Mar 19 16:30:27 localhost dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
Mar 19 16:30:31 localhost dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
Mar 19 16:30:32 localhost kernel: eth0: no IPv6 routers present

If IPv6 is a problem, how would I disable it?

Mar 19 16:30:41 localhost dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
Mar 19 16:30:52 localhost dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
Mar 19 16:30:59 localhost dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
Mar 19 16:31:06 localhost dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10

killed here before a DHCNOOFFER or like message would appear and repeat intermittantly.

Thanks,

Terry

---

### Post by alastair on 2005-03-19
sit0 is an IPv4 in IPv6 tunnel device - it is probably not the problem.

The "irq 10: nobody cared!" is probably a problem though.

Try booting with an additional  kernel arg (ESC at boot, "e" to edit kernel line, "b" to boot) :

pci=routeirq

or perhaps :

acpi=off

---

### Post by Terryg on 2005-03-19
[QUOTE=alastair]sit0 is an IPv4 in IPv6 tunnel device - it is probably not the problem.

The "irq 10: nobody cared!" is probably a problem though.

Try booting with an additional  kernel arg (ESC at boot, "e" to edit kernel line, "b" to boot) :

pci=routeirq

or perhaps :

acpi=off[/QUOTE]

I'll give it a try right now.

Terry

---

### Post by Terryg on 2005-03-19
[QUOTE=alastair]sit0 is an IPv4 in IPv6 tunnel device - it is probably not the problem.

The "irq 10: nobody cared!" is probably a problem though.

Try booting with an additional  kernel arg (ESC at boot, "e" to edit kernel line, "b" to boot) :

pci=routeirq

boot message PCI routeirq not recognized.

Still nobody cared    :( 

or perhaps :

acpi=off[/QUOTE]

reconized the above, but still nobody cared.  :( 

What to do next?

Thanks,

Terry

---

