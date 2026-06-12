---
title: "Start with Firewall Off ??"
date: 2009-12-04
forum: Networking &amp; Wireless
---

### Post by cian1500ww on 2009-12-04
Hi,

I'm just wondering what command I should add to the startup applications that will turn the firewall off at startup ?

---

### Post by dvlchd3 on 2009-12-04
By default there is technically no "firewall". (There are safeguards in place though)  Unless you have installed some other application, or used iptables, there is no "firewall" to turn off.

Also, may I inquire as to the reason you would want to disable a firewall to begin with?  Perhaps we could give you a better answer if we knew what you were attempting to accomplish.

---

### Post by cian1500ww on 2009-12-04
Thanks for the reply, I'm using Firestarter btw. I want to turn off the firewall because it always prevents Samba from working properly, maybe there's a way to configure Firestarter too allow samba to work ?

---

### Post by dvlchd3 on 2009-12-04
Set a policy to allow tcp connections through port 139.  Since I don't use Firestarter, I'm not exactly sure how to do this, but I believe there is a way to add firewall rules under the policy tab???

---

