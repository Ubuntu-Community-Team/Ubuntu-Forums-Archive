---
title: "Iptables/ Ipchains and Netfilter"
date: 2012-01-29
forum: Networking &amp; Wireless
---

### Post by UltimateCat on 2012-01-29
I started reading the Linux Network Administators Guide to 
TCP/IP Firewalling- 

My firewall has consistently been hit by this Samba and TCP over and over again. So I thought I should educate myself on How to build a IP Firewall.  So far Firestarter is doing it's job but I have some spoofing going on-

I'm trying to understand a few things. 
The chapter says:
The syntax of the iptables utility is similar to that of the ipchains syntax-
How so?
And if the command ipfwadm is only used for eariler kernels than what type of ipchain  netfilter) would I use?

How do I verify the authenticity of datagrams and commands?

Any ideas and or thoughts are greatly appreciated:D

---

### Post by Dangertux on 2012-01-29
Couple of things here. ipchains is irrelevant at this stage of the game. It was the precursor to iptables which is the front end for the netfilter kernel modules which provide your firewall. Firestarter is just another front end for iptables that provides an allegedly intuitive interface for generating iptables rules, much like GUFW and UFW do. 

That being said if you want to stop spoofing if you think it's happening you can simply do the following which will give you some protection against spoofing and source redirection attacks. 

```

echo "1" > /proc/sys/net/ipv4/tcp_syn_cookies

```

For info on iptables syntax do

```

man iptables

```

Also I'm guessing your book is an older Red Hat book as ipfwadm utility is not present in debian based distributions like Ubuntu. 

Hope this helps.

---

### Post by UltimateCat on 2012-01-31
Dangertux::)
  Thank you for the small education and the codes.

The chapter I actually found online- Didn't have the book physically.

If these attacks continue I won't hesitate to initiate the commands.

Based on the understanding you gave me I need to learn more.

Thanks again;)

---

