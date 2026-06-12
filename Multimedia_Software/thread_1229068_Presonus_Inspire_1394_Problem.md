---
title: "Presonus Inspire 1394 Problem"
date: 2009-08-01
forum: Multimedia Software
---

### Post by jazzman on 2009-08-01
I have been scanning everything I can but I can come up with a solution. I get Qjackctl started, the Inspire unit's light turns blue and then Jack (or Qjackctl) freezes. When I run plugreport I get this:

Host Adapter 0
==============

Node 0 GUID 0x000a9200e6030433
------------------------------
oMPR n_plugs=2, data_rate=2, bcast_channel=63
oPCR[0] online=1, bcast_connection=0, n_p2p_connections=1
	channel=0, data_rate=2, overhead_id=0, payload=130
oPCR[1] online=1, bcast_connection=0, n_p2p_connections=0
	channel=0, data_rate=0, overhead_id=0, payload=130
iMPR n_plugs=2, data_rate=2
iPCR[0] online=1, bcast_connection=0, n_p2p_connections=1
	channel=1
iPCR[1] online=1, bcast_connection=0, n_p2p_connections=0
	channel=0

Node 1 GUID 0x00016c200004fd33
------------------------------
libiec61883 error: error reading oMPR
libiec61883 error: error reading iMPR

Can anyone help? It runs great under Win7 and XP but I am unable to get it to run under Linux.

Thanks!

---

### Post by jjr on 2009-08-30
hi,
i ve got exactly the same problem...
my sound card works with XP, but not on ubuntu...

is there any drivers?
please...

stef

---

