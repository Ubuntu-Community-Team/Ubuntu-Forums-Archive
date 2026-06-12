---
title: "Multiple servers behind one ip with dns"
date: 2013-04-01
forum: Networking &amp; Wireless
---

### Post by aronwalker on 2013-04-01
At my house, I am running 4 servers ( web, mail, game and 1 that going to be dns). I alsi intend to build a cloud in the future. How can I configure my dns so that I can have all of my servers behind 1 ip. I don't want to port forward all of my ports to the one external ip, as my mail has a web front end running on port 80. I want it to be configured so its www - web. Mail. - mail server play. - game and dns1. - dns. Is this even possible, or will I need more ip's. (Will I have to create a proxy server - I do have another spare server lying arround)

Thanks in advance

Aron

---

### Post by SeijiSensei on 2013-04-01
Use an A record for one of the names; CNAMEs for the remainder.

```

@        IN    NS      ns

ns       IN    A       10.10.10.10
www      IN    CNAME   mail
game     IN    CNAME   mail
mail     IN    CNAME   mail

```

The nameserver needs an A record, so I'd make that the base record.

---

### Post by aronwalker on 2013-04-01
But should I use internal ip's? And if I do, will I be able to access it from outside my local network?

---

### Post by SeijiSensei on 2013-04-01
You have to forward ports across the router.  Look into the instructions for your router for details.

---

### Post by aronwalker on 2013-04-02
But I have my mail server on 80 and my web server on 80 - this will cause a conflict unless I change the ports (which I don't want do to). Maybe I made this sound to complicated. Here is my simplified version of the question again...

I have 2 web servers both running on port 80. (192.168.1.101 + 102)
How can I have a dns (100) that puts it as www1.example.com and www2.example.com. I have a domain and I want it to be accesable from outside my house. (The only reason I mentioned the mail and game server is because I thought some one may have mentioned heders of web pages (which I don't think the game server has)

I want 1 sub domain/server

---

### Post by aronwalker on 2013-04-02
Ok - I tinkered with my dns and I now have it I think

Thanks a lot for the help

Aaron

---

### Post by Doug S on 2013-04-02
Could you tell what you did? I would be interested to know, because currently I do not understand how it is possible. The details might also help someone else in the future.

---

### Post by annoyingrob on 2013-04-02
The only way that it would be possible is to forward both to an HTTP proxy like nginx or haproxy inside your network which would inspect the HTTP header, and forward the request to the appropriate machine based on the URL. This won't work for HTTPS though unless your proxy wants to strip the ssl out first.

---

