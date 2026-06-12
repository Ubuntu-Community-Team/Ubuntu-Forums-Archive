---
title: "Port forwarding through a specific port"
date: 2011-07-14
forum: Networking &amp; Wireless
---

### Post by harish19 on 2011-07-14
I want to set my ip as static and port forward it through a specific port can anyone help me with this im using ubuntu 10 with 64 bit OS

---

### Post by haqking on 2011-07-14
> **harish19 said:**
> I want to set my ip as static and port forward it through a specific port can anyone help me with this im using ubuntu 10 with 64 bit OS


you can assign a static ip using network manager by entering a valid IP in the ethernet or wireless connection of your choice or from console/terminal by editing your net interface file.
However it appears you are new to this so using the GUI network manager is easier.

as for port forwarding then that depends on your router.

There should be a port forward section, enter your IP and the port for TCP or UDP or both and the app that is using it such as bitorrent etc if applicable then thats it.


choose a valid IP and valid port, if you are using a non known port then make sure it is above 1024

---

