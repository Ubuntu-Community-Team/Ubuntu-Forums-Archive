---
title: "Portforwarding to a Virtual Machine?"
date: 2011-11-19
forum: Networking &amp; Wireless
---

### Post by ragul40 on 2011-11-19
Hi.
I need to forward ports for an application. I used to be able to forward ports, when I ran Windows 7.
I basically want to forward ports to my computer, then to a virtual box machine. Is this possible?

---

### Post by Dangertux on 2011-11-19
> **ragul40 said:**
> Hi.
I need to forward ports for an application. I used to be able to forward ports, when I ran Windows 7.
I basically want to forward ports to my computer, then to a virtual box machine. Is this possible?


Set up Virtual Box so that the machine is on a bridged network connection with the original (meaning it has an ip on the same network as the host).

Set up router to forward ports to the IP of the VM.

Hope this helps.

---

