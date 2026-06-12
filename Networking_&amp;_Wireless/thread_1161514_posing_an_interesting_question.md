---
title: "posing an interesting question"
date: 2009-05-16
forum: Networking &amp; Wireless
---

### Post by simonalexander2005 on 2009-05-16
Hi,

Me and some friends have been debating how transferring between network devices or PC's works.

To illustrate what I mean, here is an example setup:

PC1 ----ethernet----  Router ----ethernet---- PC2
PC3 ----ethernet----         ----ethernet---- PC4

(i.e 4 computers all connected to a router)

now, if a user at PC2 were to access shared files on PC1, and transfer them to a shared folder on PC3, would the router / OS be smart enough not to transfer the data to PC2, or would it have to go there so the initiator of the transfer has control over the data being transferred?

Cheers,

Simon

---

### Post by Iowan on 2009-05-18
Not that it would affect results - but where is PC3?
My suspicion (without tangible proof) is that the router would consider PC1 to be the client, and send the files there.
As I (barely) recall, the old Netware (3.12?) had an **ncopy** command that copied files from one server directory to another without sending files to requesting computer.

---

### Post by bab1 on 2009-05-18
> **simonalexander2005 said:**
> Hi,

Me and some friends have been debating how transferring between network devices or PC's works.

To illustrate what I mean, here is an example setup:

PC1 ----ethernet----  Router ----ethernet---- PC2
PC3 ----ethernet----         ----ethernet---- PC4

(i.e 4 computers all connected to a router)

now, if a user at PC2 were to access shared files on PC1, and transfer them to a shared folder on PC3, would the router / OS be smart enough not to transfer the data to PC2, or would it have to go there so the initiator of the transfer has control over the data being transferred?

Cheers,

Simon

The best way to think of this is by asking yourself; At what layer do these things happen?  Layer2 is Ethernet, Layer3 is TCP/UDP  and Layer4 for is IP.

The router you show should have a L2 switch built in (the 4/6 ports)to connect L2 datagrams.  The router is for internetworking TCP/IP networks (DSL).

If so, then there is no need to "route" anything as we are not leaving our local network.  The packet is put "on the wire" and the receiving host would accept it.  This would sorta look like this:
```

(PC2)L3->L2->L1>->L1->L2->switch->L2->L1->>L1->L2->L3(PC3 )
Note: L1=wire(PHY), L2=Ethernet, L3=TCP/UDP, L4=IP

```

The data follows the session stream.  So connecting to a shared folder is one session and connecting to another folder is another session.

---

### Post by simonalexander2005 on 2009-05-18
Cheers! That's a great answer. :)

---

