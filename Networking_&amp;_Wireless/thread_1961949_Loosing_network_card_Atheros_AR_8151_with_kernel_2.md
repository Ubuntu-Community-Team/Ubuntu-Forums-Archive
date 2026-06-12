---
title: "Loosing network card Atheros AR 8151 with kernel 2.6.32-38 and higher"
date: 2012-04-20
forum: Networking &amp; Wireless
---

### Post by KV Salzgitter on 2012-04-20
Hallo,
i have a small sever running on ubuntu-server lucid doing e-mailing and internet-connection stuff. During the last update to kernel 2.6.32-38-server i lost my external network card. Same with kernel 2.6.32-40-server. All still works fine, if the server is started with the kernel 2.6.32-34-server.
The network card connected to the lost interface eth1 (under 2.6.32-34) is (output from 'lspci'):
05:00.0 Ethernet controller: Atheros Communications AR8151 v1.0 Gigabit Ethernet (rev c0)

during startup i'll find (under 2.6.32-34) in /var/lib/messages:

Apr 19 09:05:46 mail-BS kernel: [   11.322857] ADDRCONF(NETDEV_UP): eth1: link is not ready
Apr 19 09:05:47 mail-BS kernel: [   12.973940] atheros_eth 0000:05:00.0: ATL1C: eth1 NIC Link is Up<100 Mbps Full Duplex>
Apr 19 09:05:47 mail-BS kernel: [   12.974215] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready

and the module 'atl1e' is loaded.

Under 2.6.32-38 and higher, 'lspci' gives the same result, but the entry in messages is missing. At the moment i can't say which modules are loaded then, cause i only can start the server with the -40 kernel at decent times, as it still has to do its work.

But anyway, perhaps someone may have a hint?

Thanks in advance.

---

