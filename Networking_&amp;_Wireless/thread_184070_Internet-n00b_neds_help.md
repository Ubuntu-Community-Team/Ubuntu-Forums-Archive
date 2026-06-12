---
title: "Internet-n00b neds help"
date: 2006-05-29
forum: Networking &amp; Wireless
---

### Post by Pomo on 2006-05-29
Hope I get an answer. I'been trying for days now to connect to Internet on my Ubuntu machine, without any luck. At first I was trying to install wpa_supplicant, and got nowhere. Today I just set up my wired network, got to routers interface no prob, connected, and nothing. Type in [www.google.com](www.google.com) and it said "destination host unreachable".
I need a quick and dirty way of connecting to Internet over lan wire and dsl wireless router/modem, and details on how to setup wpa_supplicant. I read howto on wiki, and howto on ubuntu forum, and it still does not work.
Thanks, Pomo

---

### Post by christhemonkey on 2006-05-29
What make/model of router, ethernet card, wireless card, modem?

---

### Post by Pomo on 2006-05-29
Siemens se515 router, ethernet card realtek 8100b (integrated on Abit sa7 mobo), wifi micronet sp906gl with Atheros 5212 chip, modem is built into router.
I secured my network with wpa-psk, so I need wpa_supplicant. All cards work, and are recognized by Ubuntu. Gave them static ip addreses. N00b in Ubuntu, NOT in networking (Cisco CCNA preparing).

---

### Post by mips on 2006-06-01
1. Please disable IPv6 and reboot:
[B]sudo mv /lib/modules/$(uname -r)/kernel/net/ipv6/ipv6.ko /lib/modules/$(uname -r)/kernel/net/ipv6/ipv6.ko.bak
sudo depmod -a[/B]
2. Please post output of **ifconfig eth0**  (Depends on your interface number)
3. Please post output of **lspci | grep Eth**
4. Please post output of **route -n**
5. Please post output of **cat /etc/resolv.conf**
6. Please post output of **cat /etc/network/interfaces**
7. Please copy **entire** output of windows **ipconfig /all** command here
8. Who is your ISP and provide a web link.

---

