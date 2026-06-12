---
title: "network question for 9.10"
date: 2010-01-01
forum: Networking &amp; Wireless
---

### Post by Firch on 2010-01-01
I'm attempting to use my laptop as bridge and I've found that Firestarter has brought me the closest to success than anything else. My problem is that when I run the firewall it says that the connection eth0 is not ready. I've checked and rechecked my network tools and everything is enabled. I was wondering if anybody knew where I'm going wrong?

---

### Post by sir_cheats_a_lot on 2010-01-02
yeah i had that same problem until i installed the dhcp server package.  i still have no net on the second computer, however. i do get a progress bar at the bottom of my browser now, though.. it just never goes anywhere.

out of curiousity.. what does your network setup look like?  might help us figure out where the current or any other issue might be/occur.

---

### Post by Iowan on 2010-01-02
I haven't worked with **ufw**, Firestarter, or **iptables**. Depending on where the "eth0 not ready" message is occurring, it *might* be Network Manager complaining because the interface is configured in */etc/network/interfaces* (although that message is usually  "not managed")

I looked for some articles on bridging, but [this]("https://help.ubuntu.com/community/NetworkConnectionBridge") one is for 6.06.

---

### Post by Firch on 2010-01-03
I've done a bunch of reading up on the subject and all I'm trying to do is allow my laptop which is wireless, to act as a bridge between the wireless router and some unit that I can't get wireless on using an ethernet hook up. The next thing I'm going to try is a static IP, I've read that that has helped other people with similar problems. what's the dhcp server package?

---

### Post by Iowan on 2010-01-03
> **Firch said:**
>  what's the dhcp server package? **dhcp3-server** is the standard - I prefer **dnsmasq** as it ties DHCP and DNS together so you can refer to DHCP clients by hostname.

---

