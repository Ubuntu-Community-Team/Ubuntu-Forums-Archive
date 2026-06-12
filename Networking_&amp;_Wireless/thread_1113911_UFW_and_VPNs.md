---
title: "UFW and VPNs"
date: 2009-04-02
forum: Networking &amp; Wireless
---

### Post by Steve1961 on 2009-04-02
I've just switched from firestarter to ufw with the gufw gui, and on the whole I'm impressed.  However, so far I haven't found a way to allow pptp vpn traffic on the gre protocol p -47, just standard tcp and udp stuff.  Anybody have any ideas?

---

### Post by Steve1961 on 2009-04-04
OK, after a little reasearch I've found that I need to add iptables commands into the before ufw scripts, although there's suprisingly little documentation about this.  The iptables commands I need to add are:

iptables -I INPUT -p 47 -m state --state ESTABLISHED -j ACCEPT
iptables -I OUTPUT -p 47 -m state --state NEW,ESTABLISHED -j ACCEPT
iptables -I INPUT -p tcp --sport 1723 -m state --state ESTABLISHED -j ACCEPT
iptables -I OUTPUT -p tcp --dport 1723 -m state --state NEW,ESTABLISHED -j ACCEPT

or even this one:

# iptables -A INPUT -p 47 -j ACCEPT
# iptables -A OUTPUT -p 47 -j ACCEPT
# iptables -A INPUT -p TCP -s 0.0.0.0/0 --source-port 1723 -j ACCEPT
# iptables -A OUTPUT -p TCP -d 0.0.0.0/0 --destination-port 1723 -j ACCEPT

I would appreciate it if some ufw guru out there could convert these commands into ufw syntax so that I can use them.  Many thanks in advance.

---

### Post by Dennis-K on 2009-12-25
Thank you for idea, your rules works successfully in such form:

-A ufw-before-input -p 47 -j ACCEPT
-A ufw-before-output -p 47 -j ACCEPT
-A ufw-before-input -p tcp -s 0.0.0.0/0 --sport 1723 -j ACCEPT
-A ufw-before-output -p tcp -d 0.0.0.0/0 --dport 1723 -j ACCEPT

(tested on Ubuntu 9.10 with ufw + corbina pptp + network-manager)

---

### Post by Steve1961 on 2009-12-26
Thanks for the feedback. Actually when onnecting to my work VPN i found that a pptp connection works without any rules - presumably because its stateful

---

### Post by diebels on 2011-04-03
Actually putting this ```
-A ufw-before-input -p 47 -j ACCEPT
-A ufw-before-output -p 47 -j ACCEPT
``` into /etc/ufw/before.rules is enough.  TCP port 1723 can be added in the GUI.  I'm also seeing some blocking of TCP and UDP port 36224, not sure what that's about.

---

### Post by saeed144 on 2011-08-02
I have set up PPTP VPN server on ubuntu.
But accounts are open for concurrent simultaneous connections. means there can be many users using one account at the time.
i need to limit that to one user at the time.
anybody knows how it can be done?

---

### Post by Welly Wu on 2012-06-12
I have an ASUS N61JV-X2 notebook PC with Crucial 8 GB dual-channel 1,066 MHz SODIMM SDRAM and an Intel 2nd Generation 2.5" MLC NAND FLASH X25-M 160 GB Solid State Drive running Ubuntu 12.04 64 bit Long Term Support. I subscribe to WiTopia personal VPN basic for now. I followed the WiTopia guide to setting up PPTP, but it does not work with GUFW. I made an exception rule for outgoing traffic over port 1723 over TCP protocol and I added the rule for IP 47 (GRE) to both iptables and /etc/ufw/before.rules, but I still can not connect via PPTP protocol when GUFW is denying outgoing traffic. I also made an exception rule for ports 80, 443, 8080, and 53 over TCP and UDP protocols respectively.

How do I get this to work with GUFW?

I will open up a support ticket with WiTopia soon.

---

### Post by Welly Wu on 2012-06-12
I got it to work successfully.

I am connected to WiTopia VPN through the PPTP protocol.

I configured my WiTopia PPTP VPN settings correctly according to the WiTopia setup guide. I also permitted port 1723 over both TCP and UDP protocols in GUFW. I followed the rules for IP 47 (GRE) and I added them to my /etc/ufw/before.rules. It works.

Next Wednesday, I will purchase WiTopia personal VPN PRO for $70.00 USD for one year of service. This will give me access to OpenVPN protocol using Blowfish cipher in Cipher Block Chaining mode of operation at 256 bits cipher strength and SHA-256 bits hash algorithm. I already followed the WiTopia OpenVPN setup guide so I hope that it will work properly after I pay my annual subscription fee next Wednesday.

So far, so good.

---

### Post by wildmanne39 on 2013-05-04
Thread closed. Please do not post in old threads.

---

