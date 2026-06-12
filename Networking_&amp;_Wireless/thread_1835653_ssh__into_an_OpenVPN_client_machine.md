---
title: "ssh  into an OpenVPN client machine?"
date: 2011-08-29
forum: Networking &amp; Wireless
---

### Post by nowhere99 on 2011-08-29
Hi, 

I have a machine, inside my local network which connects to the internet through a router. I have port forwarding on, forwarding an external port to port 22 on the local IP of the machine for ssh. I can connect fine from outside on the public IP and external port and I can connect on port 22 from the local  network using the local IP. 

Now, I connect my machine to an outside OpenVPN server for privacy and security while surfing the net from this machine. I can ssh into this machine just fine from any machine on the local network to the machine's local IP and port 22 but I cannot ssh into this machine from outside, using the external, forwarded port and public IP (which forwards to the same IP and port 22).

Any ideas why not? Ultimately, I would like to have NX and ssh access to this machine while leaving it connected to the OpenVPN server all the time.

Thanks!

---

### Post by supergustaf on 2012-09-13
> **nowhere99 said:**
> Hi, 

I have a machine, inside my local network which connects to the internet through a router. I have port forwarding on, forwarding an external port to port 22 on the local IP of the machine for ssh. I can connect fine from outside on the public IP and external port and I can connect on port 22 from the local  network using the local IP. 

Now, I connect my machine to an outside OpenVPN server for privacy and security while surfing the net from this machine. I can ssh into this machine just fine from any machine on the local network to the machine's local IP and port 22 but I cannot ssh into this machine from outside, using the external, forwarded port and public IP (which forwards to the same IP and port 22).

Any ideas why not? Ultimately, I would like to have NX and ssh access to this machine while leaving it connected to the OpenVPN server all the time.

Thanks!

Did you get this solved? I'm sitting on the exact same issue and trying to understand how things work.

---

