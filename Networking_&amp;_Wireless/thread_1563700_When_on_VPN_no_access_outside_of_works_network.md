---
title: "When on VPN no access outside of works network?"
date: 2010-08-29
forum: Networking &amp; Wireless
---

### Post by steffi on 2010-08-29
So I've used VPN clients on Snow Leopard and Linux Ubuntu with my companies VPN. Each time I'm using CISCO clients. I've seen both vpnclient and vpnc both show under Ubuntu that any network traffic that is outside of my companies network just blocks. Where as on the Mac under Snow Leopard this was never a problem. I could always reach outside the companies network when on the Snow Leopard VPN CISCO client.

---

### Post by scorp123 on 2010-08-29
I had the same issue when I was still working for HP ... What you describe is a feature called ***"split horizon"*** and as far as I remember the Linux version of the Cisco VPN client cannot do that. Apparently they don't devote as much time to develop the Linux version and its features as they devote to the Windows and Mac versions. And because it's closed source you can't do much about it.

If you use Linux as your main OS you could run Windows inside e.g. VirtualBox and then run the Cisco VPN from inside the Windows virtual machine? I did it like that, it was far less trouble then to mess with the Linux version of the VPN client.

---

