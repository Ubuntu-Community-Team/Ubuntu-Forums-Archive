---
title: "Load-Balancing Across Multiple WWAN modems"
date: 2009-03-22
forum: Networking &amp; Wireless
---

### Post by The Altruist on 2009-03-22
Some buddies of mine are looking to room together while I go to college. However, we'll be off-campus and not in dorms. Our internet will have to be our own. One buddy has a Cricket Wireless Broadband modem, and after browsing the forums, I think we should be able to get it working on Ubuntu OK. Now, that's the easy part. I was thinking, what if I got one too? Could we use them together on the same machine, and be able to load-balance it to share among our network?

---

### Post by Saghaulor on 2009-04-03
I'm interested in doing something similar. I'm still researching what may be used to accomplish this end.

I believe iproute may be able to do the trick. Balance(-NG) may also do the trick.


To reiterate the desired goal: There are multiple internet gateways, which we would like to load balance/failover to, from our internal network. More specifically, we are not trying to load balance external traffic to multiple servers in our lan, but rather, to distribute internal traffic loads out to the internet across the multiple gateways, so that no single gateway is bogged down.


If anyone has any ideas, I'm all ears.

---

### Post by Saghaulor on 2009-04-03
More research has revealed that this may be more of what we are looking for.

[http://ubuntuforums.org/showthread.php?t=1029811&highlight=load+balancing](http://ubuntuforums.org/showthread.php?t=1029811&highlight=load+balancing)

I believe that we need to bond our network interfaces that our gateways are connected to. Then we need to forward the traffic to our third network interface which feeds to our lan. And then all should work as we desire.

I'll keep updating as I discover more.

---

### Post by Saghaulor on 2009-04-04
Here is a very helpful article that provides instructions to bond your interfaces.
[http://www.enterprisenetworkingplanet.com/nethub/article.php/3696561](http://www.enterprisenetworkingplanet.com/nethub/article.php/3696561)

Here is another link that provides more detailed information on the types of bonding that can be performed.
[http://www.debianhelp.co.uk/bonding.htm](http://www.debianhelp.co.uk/bonding.htm)

Here is even further and more detailed information regarding bonding.
[http://www.linuxfoundation.org/en/Net:Bonding](http://www.linuxfoundation.org/en/Net:Bonding)

More on bonding in Ubuntu.
[http://www.howtoforge.com/network_bonding_ubuntu_6.10](http://www.howtoforge.com/network_bonding_ubuntu_6.10)

Yet even more.
[https://help.ubuntu.com/community/UbuntuBonding](https://help.ubuntu.com/community/UbuntuBonding)

More still.
[http://onlyubuntu.blogspot.com/2009/02/howto-setup-dual-dual-nic-bonding-on.html](http://onlyubuntu.blogspot.com/2009/02/howto-setup-dual-dual-nic-bonding-on.html)

---

### Post by mushroom_mover on 2009-05-01
Hi folks - this might be a little pricey for home use, but you might want to check some of the new wares at EVDO info:

[http://www.evdoinfo.com/content/view/2464/64/](http://www.evdoinfo.com/content/view/2464/64/)

BTW, this is more than load balancing. In the peered mode, you can upload files at a rate close to the sum of the available capacities on the line, and is capable of transporting live streaming video at remarkably high quality...

May there be mushrooms in your future. Best wishes...

---

