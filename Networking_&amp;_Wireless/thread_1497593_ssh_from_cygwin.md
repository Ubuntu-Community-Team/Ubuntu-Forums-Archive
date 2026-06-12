---
title: "ssh from cygwin"
date: 2010-05-30
forum: Networking &amp; Wireless
---

### Post by swincher4391 on 2010-05-30
Scenario:

Machine A is Windows.
Machine B is Ubuntu.

A and B are connected into a router which is connected into a cable switch.  Thus they have the same external IP.

Using either cygwin or putty I can't seem to ssh into my Ubuntu machine.

Some tests that I have done is look at which ports Machine B is listening to... port 22 is one of them.   I have ssh, openssh-client and openssh-server installed.

From my ubuntu machine I can ssh to myself by using localhost, 127.0.0.1 or my 192.168.x.x address.

However, if I try that very same 192.168.x.x. on the Windows machine, there is a long pause and then finally it times out.

So B can ssh to B, A cannot ssh to B, and A cannot ssh to A.

Can anyone help me fix this problem?

I have also gone into the router and opened up port 22.

---

