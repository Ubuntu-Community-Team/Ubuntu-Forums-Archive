---
title: "Wireless traffic stops randomly"
date: 2009-04-23
forum: Networking &amp; Wireless
---

### Post by quagz1 on 2009-04-23
Hey Ubuntuers,

I am using Intrepid.

I have set up a MythTV server on an AMD 3800X2 based machine. When streaming from this machine across the wireless network the wireless network traffic seems to randomly freeze.

Facts:
- The System Monitor shows CPU usage as normal with no spikes.
- The System Monitor shows outbound network traffic drops to nearly 0kb/s for about 10 secs
- Wireless throughput resumes as normal
- Repeats every 2-3min

I have *no* idea what is causing this. Any suggestions would be helpful.

Stuff which may help:

lspci entry for wireless card: Ethernet controller: Atheros Communications Inc. Atheros AR5001X+ Wireless Network Adapter (rev 01)


Thanks,

Sean

---

### Post by quagz1 on 2009-04-28
OK,

So after some testing I am now starting to think its not the server causing the issue but rather the client. It looks like the client stops requesting data and then kicks off again after about 8-10 secs.

I will play around with as many settings as possible.

Sean

---

### Post by mzar on 2009-04-28
Do you use iptables as your firewall?

---

