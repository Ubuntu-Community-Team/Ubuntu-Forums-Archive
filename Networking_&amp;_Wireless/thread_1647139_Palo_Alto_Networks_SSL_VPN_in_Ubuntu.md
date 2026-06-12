---
title: "Palo Alto Networks SSL VPN in Ubuntu?"
date: 2010-12-16
forum: Networking &amp; Wireless
---

### Post by matthanielcm on 2010-12-16
I was wondering if it was at all possible to connect to the Palo Alto Networks SSL VPN in Ubuntu? I've been trying to connect to this VPN client in Windows with their crappy VPN client with no luck. So, I've given up on Windows and now am going to try Linux for this. I noticed they don't have an official Linux VPN client, however was wondering if anybody knew a way for me to connect. This is for work and I need to connect to this to finish what I need to do. Thanks.

---

### Post by pkruse on 2010-12-17
[COLOR=black][FONT=Verdana]Though there isn’t currently an SSL/VPN client available for Linux a higher performance solution can be implemented using an IPSEC VPN Tunnel. Ubuntu does support this type of tunnel and so long as it conforms to RFC’s there should be no problem setting it up. There are numerous how-to articles available on the Internet that can walk you through setting up your distro.[/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Thanks,[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Phil[/FONT][/COLOR]

---

### Post by matthanielcm on 2010-12-17
I do prefer the IPSEC tunnel, however I'm trying to connect to a customer's computer. They have an SSL/VPN connection. I unfortunately don't have any control over which VPN they use. I've been connecting on another computer via VNC but, this is not ideal, especially when I'm not at work (I'm using a POS terminal in our lab to run the VPN software from).

---

### Post by revsemi on 2011-05-20
Has anybody solved this problem? I am in the same position where I cannot access a network in ubuntu becasue Palo Alto networks client does not work with Linux.

---

### Post by matthanielcm on 2011-05-24
Unfortunately, I have not yet found a SSL VPN solution directly in Linux. My workaround was to run Windows XP in VirtualBox. However, I have a feeling that if someone were to use the OpenVPN client (and modify it somehow) to access an SSL VPN, it could work. I'm unfortunately not that savvy.

---

### Post by revsemi on 2011-05-24
When you say that you run Windows XP in Virtualbox, you probably meant that you run everything you needed inside windows xp, I suppose.

---

### Post by feralpig on 2011-12-07
> **revsemi said:**
> Has anybody solved this problem? I am in the same position where I cannot access a network in ubuntu becasue Palo Alto networks client does not work with Linux.

Have you tried using IPSEC with xauth to connect to Palo Alto Networks Global Protect Gateway on PAN-OS 4.1?

Hypothetically that should work.

-feralpig

---

### Post by atimonin on 2012-06-26
shrewsoft vpn client works with palo alto global protect.
The only thing you should do by hands:

sysconfig net.ipv4.conf.eth0.rp_filter=0

(or whatever net interface you use)
or permamnetly set it in /etc/sysconfig.d/...

---

### Post by wildmanne39 on 2012-06-26
Deleted

---

