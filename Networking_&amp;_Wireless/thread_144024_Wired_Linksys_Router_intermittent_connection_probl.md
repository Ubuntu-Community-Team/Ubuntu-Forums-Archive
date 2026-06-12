---
title: "Wired Linksys Router intermittent connection problem"
date: 2006-03-13
forum: Networking &amp; Wireless
---

### Post by Mitush on 2006-03-13
I have basic DSL Internet via the SpeadStream modem (SBC) which works fine with my AMD64 Breezy host. I have DHCP and my IP address is not static. Recently I've purchased basic wired Linksys 4-port router (BEFSR41 ver4) to share the internet connection with my second Ubuntu computer. I've set up the router in WinXPpro (I have dual boot) and I got the internet working in this box-router-modem configuration both in Win and linux. Or al least I though I did. In Linux, it works intermittently. Namely, it works fine after the OS comes up and, minutes later, connection may go away. I can ping the router (192.168.1.1), another host on the network (192.168.1.100) (if it is present), but I cannot ping the modem (192.168.0.1, I think) and, since I understand  the modem acts as a DNS server, it cannot resolve any names. Occasionally, it starts working again, although for a brief period of time. I've called Linksys support, they walked me through logging into web interface of the router and making sure it is configured properly. The problem still persists. I don't know if WinXP would have the same problem.

What can I do to figure out what's wrong?

---

### Post by mips on 2006-03-14
Manually configure your ISP DNS server IPs in ubuntu.

---

### Post by Mitush on 2006-03-14
[QUOTE=mips]Manually configure your ISP DNS server IPs in ubuntu.[/QUOTE]

Thanks for replying. My configuration is that I have a single DNS server (192.168.0.1) which is the DSL modem. What should I add/change? On a separate note, I decided not to run firestarter (firewall) this morning and Internet seems to work fine now, or so it seems. Well, maybe that's just a big coincidence.

---

### Post by mips on 2006-03-14
Your ISP will have it's own DNS servers, this info is passed on to your router/modem. You can also get the info from your ISP via web or phone, remove the 192.... router address from the resolv.conf file and add the two addresses for your ISPs DNS servers.

But if it is working now then dont fix it ;)

---

### Post by Mitush on 2006-03-15
Thanks for the advice, I'll keep that in mind. The internet is still working fine, without the firestarter that is. I hope that fixed it. Now, if I could only fix the [nvidia driver - related hang ups...]("http://bugzilla.ubuntu.com/show_bug.cgi?id=7183")

---

