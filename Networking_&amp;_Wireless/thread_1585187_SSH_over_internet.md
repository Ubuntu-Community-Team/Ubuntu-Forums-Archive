---
title: "SSH over internet"
date: 2010-09-30
forum: Networking &amp; Wireless
---

### Post by JaJaBinks on 2010-09-30
I am looking for a way to perform basic administration (via internet) on a friends laptop, from my desktop pc.

I have set up ssh on both machines, and am able ssh the laptop when both are connected to my LAN.

the Laptop uses a Telstra mobile broadband device to access the internet.

attempts to ssh the IP address of the mobile broadband device result in error > *Connect to host xxx.xxx.xx.xx port 22: No route to host*

**Does anyone know if this can be done ?**

All posts, documentation and instructions i have read are for performing ssh the other way around i.e. from laptop to Desktop PC.

I have seen information on reverse ssh, and reverse VNC, but would prefer not to go this route if there is an alternative

Regards to all :)

---

### Post by CharlesA on 2010-09-30
Depending on how the mobile broadband card work, you might have to forward ports, or even have the ISP blocking ports.

You can use shieldsup or something similar to see if port 22 is open.

---

### Post by JaJaBinks on 2010-10-02
Many thanks.
So it appears my ISP *is* blocking port 22. I shall disable isp firewall and try again.
cheers

---

### Post by tturrisi on 2010-10-02
Configure sshd to use port 3022 and use port forwarding on router to forward 3022 requests to the lan ip that's running sshd.
Then do:
ssh -p 3022 username@ip-address

---

