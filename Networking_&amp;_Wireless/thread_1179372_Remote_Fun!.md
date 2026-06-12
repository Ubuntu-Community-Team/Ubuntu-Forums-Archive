---
title: "Remote Fun!"
date: 2009-06-05
forum: Networking &amp; Wireless
---

### Post by whhs41 on 2009-06-05
I am trying to remote into Ubuntu (which is installed on VirtualBox) from my laptop.  It is part of the domain so I am just using the computer name as the server address.  The IP of the VirtualBox is 127.0.0.1, which is the loopback IP, so I couldn't use it.

Firewall is also disabled.

It refuses to connect to Ubuntu : \  Any thoughts?

---

### Post by whhs41 on 2009-06-05
I have tried to VNC route w/o success.  anything?

---

### Post by jonobr on 2009-06-05
Can you ping the IP address directly?

Whats the result of ifconfig on the machine your connecting to?

Can you talk back the way from ubuntu to the macine your testing from via ping or hostname?

---

### Post by DGortze380 on 2009-06-05
> **whhs41 said:**
> I am trying to remote into Ubuntu (which is installed on VirtualBox) from my laptop.  It is part of the domain so I am just using the computer name as the server address.  The IP of the VirtualBox is 127.0.0.1, which is the loopback IP, so I couldn't use it.

Firewall is also disabled.

It refuses to connect to Ubuntu : \  Any thoughts?

Sounds like you're a little confused...

and I don't quite understand your setup.

You have a laptop, on which you've installed Ubuntu in VirtualBox??

Do you have the Ubuntu VM setup with Host-Interface Networking? (Bridged Adapter)

---

