---
title: "avahi trouble and a question"
date: 2008-12-20
forum: Networking &amp; Wireless
---

### Post by jimmy the saint on 2008-12-20
I have a server running Gutsy.  Firefly (mt-dappd) is running and serving music to various computers in my house.  The problem is that the dapp server's presence is not being advertised.  Each time I wish to connect to it, I have to manually enter the ip and port. 

I downloaded "avahi discovery," which is supposed to identify avahi advertised services.  The server box shows up, but there is no mention of the dappd share.  Avahi is installed and avahi-daemon is running.

Am I missing something?  I spent several hours looking at tutorials, faqs and everything else I could find about getting mt-dappd and avahi running but I didn't see anything that I missed in setting everything up.  Either avahi is not working, or I have seriously misunderstood what it does and how it works.

Is there something that I need to configure in order to get the daap share advertised?  I haven't modified iptables or done anything that should interfere.  

Thanks for any troubleshooting help!

JTS

---

### Post by jimmy the saint on 2008-12-20
I think I figured out that moblock is the problem.  I stopped it and now avahi is publishing the daap service.  If anyone knows enough about moblock to help me fix that, I would be grateful.

---

### Post by jre on 2008-12-20
It should simply be a matter of allowing all traffic from and to your LAN. So just add the IP range of your LAN to /etc/moblock/allow.p2p.

EDIT: I added a new FAQ to the wiki:
[https://help.ubuntu.com/community/MoBlock#Some%20services%20(avahi,%20webmin,%20ftpd,%20sshd,%20...)%20on%20my%20MoBlock%20machine%20aren%27t%20available%20to%20other%20machines%20any%20more](https://help.ubuntu.com/community/MoBlock#Some%20services%20(avahi,%20webmin,%20ftpd,%20sshd,%20...)%20on%20my%20MoBlock%20machine%20aren%27t%20available%20to%20other%20machines%20any%20more)!

---

### Post by jimmy the saint on 2008-12-20
Thanks for that!  All of the other services mentioned worked fine.  I could SSH, ftp and gain access to many other services including samba. I will try to reinstall moblock (the last upgrade seemed to frag the installation when it tried to get the list) and report back.

---

### Post by jre on 2008-12-21
> **jimmy the saint said:**
> I will try to reinstall moblock (the last upgrade seemed to frag the installation when it tried to get the list) and report back.
To make a clean reinstall do:
```
sudo aptitude purge moblock moblock-control mobloquer
sudo aptitude install moblock moblock-control mobloquer

```
When you install you will have to wait some time until the lists are downloaded, be patient!

---

