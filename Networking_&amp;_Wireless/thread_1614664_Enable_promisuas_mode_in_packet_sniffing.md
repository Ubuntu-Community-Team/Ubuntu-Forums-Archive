---
title: "Enable promisuas mode in packet sniffing"
date: 2010-11-05
forum: Networking &amp; Wireless
---

### Post by gizmo720 on 2010-11-05
I am running wireshark on my laptop. It is only showing me the packets addressed to and from it, and broadcast packets. I am running it in promiscuas mode, and in iwconfig set the interface to mode monitor. However it can still not see packets from my other laptop. They are in the same room, both wirelessly connected to the same network. Any ideas?

---

### Post by Der Ritter on 2010-11-05
> **gizmo720 said:**
> I am running wireshark on my laptop. It is only showing me the packets addressed to and from it, and broadcast packets. I am running it in promiscuas mode, and in iwconfig set the interface to mode monitor. However it can still not see packets from my other laptop. They are in the same room, both wirelessly connected to the same network. Any ideas?

It's entirely possible that the driver that is in charge of your network interface cannot support promiscuous mode, a point mentioned in the [Wireshark FAQ](http://www.wireshark.org/faq.html#promiscsniff).

---

### Post by gizmo720 on 2010-11-06
Thanks for the idea, is their any way to get new drivers?

---

