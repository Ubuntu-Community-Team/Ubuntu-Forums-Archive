---
title: "Network changed after upgrade"
date: 2009-11-17
forum: Networking &amp; Wireless
---

### Post by Hackit on 2009-11-17
Hi Everyone,

I must say I decided to upgrade to 9.10 last night and things went very well.

I have been left with one issue.

My rig has 2 Ethernet adapters, one built into the board and i put in a giga bit card.

Let me also explain I have 2 separate isp's in the house. one for everyone to use and the other is for me only. so I also have 2 routers, i will call the r1me and r2all.

So back to my linux rig, eth0 is for the r1me and I use eth1 is r2all. so i could download on r1me and also share files on r2all with out taking away form r1me resources.

Now linux decide after the upgrade to make a eth1 the default active connection, how can i change to this to make eth0 the default connection.

Thanks,

I've tried to make this as simple as possible but if this is to confusing I'll try and explain.

---

### Post by Hackit on 2009-11-17
> **Hackit said:**
> Hi Everyone,

I must say I decided to upgrade to 9.10 last night and things went very well.

I have been left with one issue.

My rig has 2 Ethernet adapters, one built into the board and i put in a giga bit card.

Let me also explain I have 2 separate isp's in the house. one for everyone to use and the other is for me only. so I also have 2 routers, i will call the r1me and r2all.

So back to my linux rig, eth0 is for the r1me and I use eth1 is r2all. so i could download on r1me and also share files on r2all with out taking away form r1me resources.

Now linux decide after the upgrade to make a eth1 the default active connection, how can i change to this to make eth0 the default connection.

Thanks,

I've tried to make this as simple as possible but if this is to confusing I'll try and explain.


Fixed the issue, edited eth0 connection, and changed the default connection.

---

