---
title: "samba across multiple lans?"
date: 2006-06-29
forum: Networking &amp; Wireless
---

### Post by mrweirdo on 2006-06-29
Hello I have a bit of a problem i need to figure out. I have a ubuntu server setup as my router/internet access server using nat with iptables. Basicly I have a network card that gets a public ip hooked to my cable modem. Then I have an internal wired lan on the ip network 192.168.1.0. Also I have a internal wireless card setup on 192.168.2.0 which my laptop connects too over wifi. 

Now what I'm looking to do is to be able to access the fileshares and printer(those are on the 192.168.1.0 network) from my laptop on the wireless network(192.168.2.0). I assume I need to add some rules to my iptables firewall but I'm not sure what for filesharing aka samba.

---

### Post by mrweirdo on 2006-06-30
Got it working partiatly by adding a few Masquerading  rules to iptables by using this [http://www.linux.com/howtos/IP-Masquerade-HOWTO/multiple-masqed-lans.shtml]("http://www.linux.com/howtos/IP-Masquerade-HOWTO/multiple-masqed-lans.shtml") However by partialy I mean that I can only access the shares and printers by using ips addresses. Hostnames dont work for some reason.

---

