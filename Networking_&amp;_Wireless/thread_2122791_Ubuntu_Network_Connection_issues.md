---
title: "Ubuntu Network Connection issues"
date: 2013-03-06
forum: Networking &amp; Wireless
---

### Post by NielTheWorx on 2013-03-06
Good Day guys

I hope you are all well and could assist me.

I have recently installed an ATTO 4 port 10GB Ethernet adapter and 40TB Storage on my Ubuntu Server.
I have 4 workstations connected to the server.
I have setup the IP's statically using the Network manager as follows:
Server side : 10.0.0.1 goes to 10.0.0.10
Server side : 10.0.0.2 goes to 10.0.0.20
Server side : 10.0.0.3 goes to 10.0.0.30
Server side : 10.0.0.4 goes to 10.0.0.40

The Storage is shared for all the machines.
The issue is that I can only have one "Wired Connection" at a time.
When I click 10.0.0.1 for example it establishes a connection to 10.0.0.10 and the storage is accessible from the workstation.
As soon as I establish another connection it disconnects the previous connection.
Is there a way to get all the intefaces connected at the same time so that all 4 workstations can access the storage?

Thanks in advance.

---

### Post by iponeverything on 2013-03-06
- 
Managing the interfaces through /etc/network/interfaces will prevent network manager from managing interfaces, and allow you to by-pass the limitations of network manager.

---

### Post by NielTheWorx on 2013-03-07
Thanks so much iponeverything. I m going to disable network manager and set eveverything via interfaces.

---

