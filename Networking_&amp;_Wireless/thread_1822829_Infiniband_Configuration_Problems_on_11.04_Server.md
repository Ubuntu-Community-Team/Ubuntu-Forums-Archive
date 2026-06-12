---
title: "Infiniband Configuration Problems on 11.04 Server"
date: 2011-08-11
forum: Networking &amp; Wireless
---

### Post by eviscares on 2011-08-11
Dear Community,
I work at an IT firm and was tasked with setting up an Infiniband network. As of now this consists of 2 Servers, each with a Mellanox Technologies MT25204 card, connected by a cable.
I installed the userspace drivers and the ofed drivers, added the following to my /etc/modules:

rdma_ucm
ib_sa
ib_cm
ib_umad
ib_addr
ib_uverbs
ib_ipoib
ib_ipath
ib_qib
ib_sdp
ib_mthca

but when I try to start opensm it gives me this error message:Error from osm_opensm_bind (0x2A)
Perhaps another instance of OpenSM is already running"

As well ibstat gives this output:
CA 'mthca0'
	CA type: MT25204
	Number of ports: 1
	Firmware version: 1.2.0
	Hardware version: a0
	Node GUID: 0x0008f10403992be0
	System image GUID: 0x0008f10403992be3
	Port 1:
		State: Initializing
		Physical state: LinkUp
		Rate: 10
		Base lid: 0
		LMC: 0
		SM lid: 0
		Capability mask: 0x02510a68
		Port GUID: 0x0008f10403992be1

I would guess that something is inherently wrong as the adapter should most probably not be remaining in an Initializing stat.
Any Ideas?
Thanks in advance.

---

### Post by eviscares on 2011-08-11
Ok,
I got another error message that I don't understand. After symlinking /dev/infiniband/umad0 to /dev/umad0 (yeah, I guess this can't really work), it now tells me 


```
Aug 11 09:39:18 213168 [F9F7720] 0x01 -> osm_vendor_open_port: ERR 542C: umad_open_port() failed
Aug 11 09:55:40 793377 [824FC720] 0x02 -> osm_vendor_init: 1000 pending umads specified
```

---

