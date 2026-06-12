---
title: "Hard Network problem"
date: 2009-02-26
forum: Networking &amp; Wireless
---

### Post by dox_drum on 2009-02-26
Hi there!

In the office we have several computers running linux (most of them Ubuntu Intrepid). Last Saturday the network black out, and since that moment wired network is not working on Linux machines.

Most of them use the automatic configuration for the web, but even those with fixed IP address are not working. However, wireless network works fine.

Have any of you some idea what is going on? People encharged of the network at the University seems to have not a clue on this.

Thank  you for even trying.

[CENTER]Enjoy![/CENTER]

---

### Post by jflaker on 2009-02-26
give us some idea about what your network infrastructure looks like.

Have you tried restarting the office router?

---

### Post by dox_drum on 2009-02-26
> **jflaker said:**
> give us some idea about what your network infrastructure looks like.

Have you tried restarting the office router?

I'm not at the office, but I'll give you more detail tomorrow a.s.a. I'll get there.

Thanks.

---

### Post by dox_drum on 2009-02-27
Hi again...

I do not know exactly how the network works at the University, but finally we've been able to browse in a SUSE machine. The thing we did was to open the wirewall point (in the NFS configuration).

How could we do the same under Ubuntu?

Thank you very very much.

---

### Post by superprash2003 on 2009-02-27
there could be some ipconflict causing problems!!

---

### Post by dox_drum on 2009-02-27
> **superprash2003 said:**
> there could be some ipconflict causing problems!!

Well, it is supposed to configure the IP automatically.

If I connect the Laptop via WiFi, the isn't problem... but there is if I try to connect via wire, doesn't work.

---

### Post by sgosnell on 2009-02-27
Have you tried resetting the router?  If all the machines are having problems, it points to a router issue.  Try removing the power for a couple of minutes and then reconnecting it.  The reset should cure your problems, if the power spike didn't damage it.  Sometimes power spikes during blackouts can damage electronic equipment.  If the reset doesn't work, try replacing the router with another known good one.

---

### Post by dox_drum on 2009-02-27
> **sgosnell said:**
> Have you tried resetting the router?  If all the machines are having problems, it points to a router issue.  Try removing the power for a couple of minutes and then reconnecting it.  The reset should cure your problems, if the power spike didn't damage it.  Sometimes power spikes during blackouts can damage electronic equipment.  If the reset doesn't work, try replacing the router with another known good one.

We have try already that, and does not work. Moreover, the windows machines are working with the wire connection... and the one I mension with SUSE.

The thing with SUSE was to open a point in the Firewall... But I do not how to do it under Ubuntu.

Thank you.

---

### Post by jflaker on 2009-02-27
> **dox_drum said:**
> We have try already that, and does not work. Moreover, the windows machines are working with the wire connection... and the one I mension with SUSE.

The thing with SUSE was to open a point in the Firewall... But I do not how to do it under Ubuntu.

Thank you.

So, you say the wired machines connect but wireless doesn't?

Did you reset the router yet?

---

### Post by dox_drum on 2009-03-02
> **jflaker said:**
> So, you say the wired machines connect but wireless doesn't?

Did you reset the router yet?

It's the inverse... wireless connect, but wired don't.

---

