---
title: "SSH to server from Internet"
date: 2012-02-20
forum: Networking &amp; Wireless
---

### Post by Red Kelly on 2012-02-20
Could some one point me in the right direction for this?

I just wont to ssh into my server at home from my laptop when out and about in the world.

I have a static IP
Internet is connected through TPlink ADSL2 modem into the server's eth0
Then bridged to eth1 and out to house LAN and WIFI

I would have to allow it through the TPlink firewall and servers iptables, just don't know what exactly to allow.

And is there a different log in command?

Thanks for any help given :)

---

### Post by Cheesehead on 2012-02-20
On your router, you need to enable port-forwarding of ssh to your server. Normally, that's port 22, but you can change it to any port you wish.

WARNING: An internet-facing port 22 with mere password-enabled access (instead of keys) is a *really* bad idea, and you will get attackers trying to penetrate within minutes! Thousands of attempts each day.

There are many security measures you can take. At a minimum, you MUST disable ssh password access and use keys only. When some bots find an open port 22, they automatically begin a dictionary attack.
```
In the server's /etc/ssh/sshd_config:

Port <your preferred port number>
PasswordAuthentication no
PermitRootLogin no
```

I use various supplementary means beyond those.

---

### Post by roelforg on 2012-02-20
assuming you ran
```

sudo apt-get install openssh-server

```for the install and didn't change the ports,

go to your router's firewall and your pc's.
Allow port 22 TCP Both ways (do this on both the router, pc and all other firewalls between pc and modem)

My firewall is off, i think the 3 firewalls between my modem and the switch in my room supplying my 6 pc's are enough.

---

### Post by Perkins on 2012-02-21
Personally when I need an open SSH port facing the internet and I can't just put it on a non-standard port, I use Gibson Research's one time password system to prevent attackers from having more than a snowball's chance in hell of cracking in.  ([http://www.grc.com/ppp/design.htm](http://www.grc.com/ppp/design.htm))  That said, their attempts consume bandwidth.  There are a few programs in the repository (denyhosts is one) that will detect attempts to guess passwords and block further access.

If you are having trouble getting your router to forward port 22 (or whichever other port you've chosen to use), I have had good luck in the past walking people through it via screenshots of the router's webconsole.  Please black out any identifying numbers before posting any such screenshots.

---

### Post by Red Kelly on 2012-02-21
Thanks guys will hopefully have time to try tomorrow.

---

### Post by Lars Noodén on 2012-02-21
You can also limit the allowed rate of attempted connections using iptables.  It is a good layer to add.

```

   ip6tables -I INPUT -p TCP --dport 22 -m state --state NEW -m limit --limit 5/minute --limit-burst 5 -j ACCEPT
   iptables  -I INPUT -p TCP --dport 22 -m state --state NEW -m limit --limit 5/minute --limit-burst 5 -j ACCEPT

```

---

