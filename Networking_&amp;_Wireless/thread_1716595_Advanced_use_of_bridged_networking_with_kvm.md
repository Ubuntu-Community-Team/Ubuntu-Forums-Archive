---
title: "Advanced use of bridged networking with kvm"
date: 2011-03-28
forum: Networking &amp; Wireless
---

### Post by jason0 on 2011-03-28
Hi,

I can see this post applying to two different major categories: Virtual machines and networking.  I want to build an arbitrary set of networks so that I can do some failover testing.  However, it's not clear to me how to do so.  I have been looking at bridge-utils.

The idea is to create a topology then see if it works as I expect.  I do not expect high performance: just that the packets move as if they are passing through discrete components.  Enclosed is an example network diagram.

Assuming my ideas work, I would eventually like to connect a vlan trunk to a physical ethernet and be able to have different vm's connect to different vlans.

Are my expectations of bridge-utils reasonable?  Is there an advanced resource for these types of uses?

Thank you for your time...

--jason

---

