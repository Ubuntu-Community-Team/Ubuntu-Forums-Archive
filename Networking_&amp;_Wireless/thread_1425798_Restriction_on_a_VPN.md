---
title: "Restriction on a VPN"
date: 2010-03-09
forum: Networking &amp; Wireless
---

### Post by P_O on 2010-03-09
I want to connect to a server at my university so l'll be able to read scientific articles available on their network from home.

Here is how I do it
```

ssh -X -p 5822 -L 80:localhost:80 me@server.university.ca

``` 

It connects, I am on the server and I am able to connect firefox to the localhost. However, I can only access the sites that start with "university.ca/". Everything else is blocked. 

I realized that I have the same problem when I am trying to set a cisco VPN to my office network. I can only access site that are on the vpn server it self.

The vpn gatway gateway vpn.work.ca and then I can only ping  vpn.work.ca or go on it with firefox. Other site/servers will not answer.




My colleagues are using other linux distribution and do not have problem to connect on the cisco VPN or the ssh tunnel, so the problem has to come from my machine configuration. 

Anyone with an idea?

---

