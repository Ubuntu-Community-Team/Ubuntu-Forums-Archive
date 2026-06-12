---
title: "IP Masquerade"
date: 2013-03-21
forum: Networking &amp; Wireless
---

### Post by tsofats3 on 2013-03-21
Hello
 
I need help with the steps to setup and configure IP Masquerade on a linux PC.

I think the Kernel version is 3.5.0-17 generic #28-ubuntu SMP, i will like to know if I can setup IP masquerade on this system

Thank you,

---

### Post by Doug S on 2013-03-22
Hi and welcome to Ubuntu forums.
Have a look [here]("https://help.ubuntu.com/12.10/serverguide/firewall.html#ip-masquerading"), which also has links to further references at the end.
Yes, I think you should be able to do it on your system.

---

### Post by Elcoco on 2013-04-30
Hi Im trying to do this to. I followed the guide but i still cant connect to the vpn if ufw is turned on. One issue may be that i dont have an eth0 just p4p1 and lo. Ive tried putting p4p1 in place of eth0 but no luck.

---

### Post by Doug S on 2013-04-30
> **Elcoco said:**
> Hi Im trying to do this to. I followed the guide but i still cant connect to the vpn if ufw is turned on. One issue may be that i dont have an eth0 just p4p1 and lo. Ive tried putting p4p1 in place of eth0 but no luck.It does not make sense, at least to me, that you need masquerading. Could you describe your issue in more detail?

---

