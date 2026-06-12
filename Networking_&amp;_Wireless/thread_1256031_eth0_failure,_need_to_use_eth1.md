---
title: "eth0 failure, need to use eth1"
date: 2009-09-02
forum: Networking &amp; Wireless
---

### Post by tom66 on 2009-09-02
I have a server running Red Hat 6.0. It's a desktop PC and not really designed to be a server. Long story short, the network device in it has failed (it's built on to the motherboard), and is always showing the connection as 'off'. The device can identify itself properly, it just doesn't work. 

I installed a secondary PCI card which I want to use as the primary device,  but I don't know how to do that. Any help appreciated.

---

### Post by t0mppa on 2009-09-02
Edit */etc/udev/rules.d/70-persistent-net.rules* and rename the interfaces. If you completely remove the non-working device, the system will just think it is recognizing new hardware on next boot and will add it back in.

---

### Post by tom66 on 2009-09-02
That file doesn't exist. Remember, I'm on Red Hat not Ubuntu..., so maybe that is a Debian feature. 

Thanks

---

### Post by t0mppa on 2009-09-02
Bugger, I was wondering about that, but a quick look on Google showed Red Hat forums talking about the file as well, so figured it would exist. Maybe you should just consult their forums or drop by on a Red Hat IRC channel to ask where to find the file on their system.

---

### Post by Iowan on 2009-09-02
> **tom66 said:**
>  Remember, I'm on Red Hat not Ubuntu..., so maybe that is a Debian feature. 
Perhaps the Red Hat forum might be more helpful? I can think of a few workarounds - but I've forgotten most of Red Hat.

---

