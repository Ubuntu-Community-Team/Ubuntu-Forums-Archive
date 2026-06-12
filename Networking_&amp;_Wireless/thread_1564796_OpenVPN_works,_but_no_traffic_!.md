---
title: "OpenVPN works, but no traffic !"
date: 2010-08-31
forum: Networking &amp; Wireless
---

### Post by maxsteel10 on 2010-08-31
Hi folks 

This is my first post here and I'm happy to join this awesome forum

I just started using Ubuntu 10.04 and I do really like it !! 

I'm facing a problem when I establish VPN connections using OpenVPN to Your Freedom Server. " you can see their documentation [here ]("http://www.your-freedom.net/index.php?id=173")", I've installed OpenVPN from synaptic and I used the client to connect through VPN and it works !! but there is no traffic in FF or any application !! 

I tired to insert some HTTP proxy also belongs to the same server and it works. What really wonders me is that OpenVPN seems to work only when I'm connecting to streams sites "e.g. ustream, justin.tv" 

Is there anyway to force the whole traffic to use OpenVPN " 

I'm using Mobile modem and it works fine with OpenVPN in win7 

hope you could help me ... :)

---

### Post by maxsteel10 on 2010-08-31
any help ... :(

---

### Post by maxsteel10 on 2010-08-31
up

---

### Post by lisati on 2010-08-31
Please don't start multiple threads on the same question. And if you bump your thread sooner than 24 hours after the last post, those of us who go looking specifically for threads with no answer might easily miss it.

---

### Post by BkkBonanza on 2010-08-31
I don't use OpenVPN but you seem to be needing help so I took a look at the openvpn site docs and found this,

[http://openvpn.net/index.php/open-source/documentation/howto.html#redirect](http://openvpn.net/index.php/open-source/documentation/howto.html#redirect)

which sounds like what you need to look into for browsing.

BTW if you are truly needing security I would tend to favour the ssh SOCKS proxy method rather than VPN. On Ubuntu it's easier to use and doesn't depend on SSL Certificates. While SSL is fine for typical cases it is very likely broken as far as  surveillance goes and with hundreds of Certificate Authorities (CA) accepted by most software one never can really know who is able to do monitoring unless you use your own CA.

---

### Post by maxsteel10 on 2010-08-31
> **lisati said:**
> Please don't start multiple threads on the same question. And if you bump your thread sooner than 24 hours after the last post, those of us who go looking specifically for threads with no answer might easily miss it.

I appreciate your reply and sorry for bumping the thread.

---

### Post by maxsteel10 on 2010-08-31
> **BkkBonaza said:**
> I don't use OpenVPN but you seem to be needing help so I took a look at the openvpn site docs and found this,

[http://openvpn.net/index.php/open-source/documentation/howto.html#redirect](http://openvpn.net/index.php/open-source/documentation/howto.html#redirect)

which sounds like what you need to look into for browsing.

BTW if you are truly needing security I would tend to favour the ssh SOCKS proxy method rather than VPN. On Ubuntu it's easier to use and doesn't depend on SSL Certificates. While SSL is fine for typical cases it is very likely broken as far as  surveillance goes and with hundreds of Certificate Authorities (CA) accepted by most software one never can really know who is able to do monitoring unless you use your own CA.

Thanks for your response

I read the link you post before but I couldn't find config file for the client :(

For ssh Socks it don't see any options for it in the client 

I wish if I can just forward my connection to OpenVPN because the connection is working fine with the server but with no traffic

---

### Post by maxsteel10 on 2010-09-01
please help 

I don't want this issue to force me going back to windows 7 :(

---

