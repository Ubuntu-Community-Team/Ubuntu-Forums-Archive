---
title: "opened ports 21, 23, 80 security consideration"
date: 2009-07-08
forum: Networking &amp; Wireless
---

### Post by gueshew on 2009-07-08
I have run an online port scanning, confirmed with a local scan using nmap which showed that ports 21, 23 and 80 are opened.

From what I understand those are FTP, telnet and http ports. Is this necessary to keep those opened considering that I don't use ftp nor remote administration.

More importantly, is my system safe with those ports opened?

I thought ubuntu came with all ports closed and I don't remember opening any, does anyone have a clue why it is so?

---

### Post by prshah on 2009-07-08
> **gueshew said:**
> 
From what I understand those are FTP, telnet and http ports. 

More importantly, is my system safe with those ports opened?

I thought ubuntu came with all ports closed and I don't remember opening any, does anyone have a clue why it is so?

It is most likely that the open ports shown belong to your router, not your computer. You will have to open your routers config page and disable access to these ports on the WAN interface; you can leave them enabled on the LAN interface. Since the exact configuration varies wildly from model to model, it's not really possible to be more explicit.

Unless you have installed the server edition, ubuntu will not have programs listening to the ftp and http ports.

If the ports exposed belong to the router, then security-wise you need not worry _too_ much; but always better to close them, and the sooner the better. If anyone can access your router's config page over the 'net they can compromise system security.

---

### Post by binbash on 2009-07-08
They are ftp ssh and http ports.Unless you installed a ftpd , that should comes closed.

---

### Post by prshah on 2009-07-08
> **binbash said:**
> They are ftp ssh and http ports.Unless you installed a ftpd , that should comes closed.

Just a small point; Port 23 is telnet, not ssh; port 22 is ssh.

---

### Post by sasho_zl on 2009-07-08
Have you configured any Netfilter rules? An Ubuntu out of the box installation really comes with no open ports but the firewall is always a good thing to have. Also check if you can connect to your open ports. Type **telnet localhost**. If you can then the problem is not in a router and you should configure a firewall.

---

### Post by gueshew on 2009-07-08
thanks for your responses.

My router had telnet and fpt opened indeed, which I just closed on the configuration page (which is by the way password protected).

Port 80 is still opened though, but wouldn't closing it prevent me from browsing the web?
On the router configuration page it says: "Web traffic is blocked from the WAN to the LAN" next to the option to block web traffic.

Telnet couldn't connect to locahost when trying the command "telnet localhost". And I haven't modified any netfilter rules.

Even though I have just closed these ports on my router, a web scan sees them closed but running nmap -r on my ip shows :

Not shown: 998 filtered ports
PORT   STATE SERVICE
21/tcp open  ftp
23/tcp open  telnet

Not sure what to make of it...

---

### Post by sasho_zl on 2009-07-08
There is no way that the closing of port 80 could affect your browsing.

---

