---
title: "APT over SSH (tunnel) - socks proxy"
date: 2010-04-30
forum: Networking &amp; Wireless
---

### Post by Vorian on 2010-04-30
Hello

I am somewhat new to Linux, and I have a problem I just cant get sorted.

I have a machine at school that I am able to run Linux on, however it's tucked behind a firewall - thus no apt.

I do have a server, and I have my browser and email client set up just fine. I just cant find the right answer for my situation.

---

### Post by jpeddicord on 2010-04-30
> **Vorian said:**
> Hello

I am somewhat new to Linux, and I have a problem I just cant get sorted.

I have a machine at school that I am able to run Linux on, however it's tucked behind a firewall - thus no apt.

I do have a server, and I have my browser and email client set up just fine. I just cant find the right answer for my situation.

You could use `ssh -D 9090 [email]user@ssh.host[/email]` to create the SOCKS proxy, and then point apt to use that proxy on localhost. Googling around it looks like apt doesn't support SOCKS proxies, though, but you can supposedly install tsocks to work around it: [http://paulsundvall.blogspot.com/2009/01/running-apt-get-through-ssh-socks-proxy.html](http://paulsundvall.blogspot.com/2009/01/running-apt-get-through-ssh-socks-proxy.html)

---

### Post by Vorian on 2010-04-30
Yay, thanks Jacob!

---

