---
title: "problem with define multiple ip address on NIC"
date: 2011-04-12
forum: Networking &amp; Wireless
---

### Post by samirafk222 on 2011-04-12
hi friends
i was installed two ubuntu(1,2) via wmware on my laptop(win=7)
on one of them run dhcpserver (ubuntu-1) and i am going to run the other one dhcp client(ubuntu-2)
but on the one NIC that belong to my laptop how to config dhcp client (ununtu-2) get ip adres fom dhcserver(ubuntu 1)

---

### Post by koszta on 2011-04-12
That should be done from within the virtual machine config tool (e.g. vmware or virtualbox). Mostly you have to have the machines comunicate correctly (most common is bridged network connection between the machines).

---

### Post by samirafk222 on 2011-04-12
they are connected together via ping 192.168.131.145/146 but the dhcp server couldn't work correctly

---

### Post by samirafk222 on 2011-04-14
> **koszta said:**
> That should be done from within the virtual machine config tool (e.g. vmware or virtualbox). Mostly you have to have the machines comunicate correctly (most common is bridged network connection between the machines).


thx alot that's right ..your answer is correct ..thx again

---

