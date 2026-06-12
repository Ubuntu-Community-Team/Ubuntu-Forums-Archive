---
title: "Redirecting from port 443 to port 80"
date: 2012-12-08
forum: Networking &amp; Wireless
---

### Post by fredbird67 on 2012-12-08
I've been trying various ways to get DansGuardian filtering to block https websites.  I can block http sites just fine, but anything I try totally ignores https websites.  I then popped in a live USB of Ubuntu Christian Edition, thinking it might do what I'm trying to do and if it did, I'd study how it did it.  I won't do UCE itself because I tried its Unity desktop, and I _hate_ it with a passion -- it's an absolute train wreck in my book.

Anyways, I found that UCE doesn't block https connections, either -- a bummer, to be sure, but at least I don't feel so stupid anymore, because the UCE creator couldn't do it, either.

Therefore, as an alternative, I got to thinking, is there a way to set up iptables so that it redirects a specific website via https to that same website just using http?  An example of what I'd like to do is, if a user tries to connect to YouTube via https, the request will automatically get redirected to YouTube with just an http connection so that it can be run through DansGuardian.

Mind you, I don't want to prohibit https access entirely, since it's used for online shopping and the like, but I'd like to prohibit https access only for certain websites and instead redirect such requests to a standard http connection if at all possible so that they can be run through DG.

Thanx in advance,
Fred in St. Louis

---

### Post by EmmEight on 2012-12-09
Fred,

Open a terminal

```
 
sudo gedit /etc/hosts

```

Add the following code 

```

127.0.0.1    localhost
127.0.1.1    yournamehere
127.0.0.1    www.overprotective.dad.com
127.0.0.1    www.Ican'tTrustMyKids.org
127.0.0.1    www.NorthKoreaBlocksWebsitesToo.edu/EgyptTriedToAlso
127.0.0.1    www2.HitlerUsedFearTactic.gov/IfYouHideIt/ItDoesntExist/
127.0.0.1    https://www.CardinalsSuck.com/BudwiserSendsMyBeerMoneyToEurope.html


# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters

```

Obviously replacing the fake website addresses with whichever websites you choose to block. 

Just remember that any website can be accessed using its public IP address

For example [http://74.125.224.72/](http://74.125.224.72/) will bring you to [www.google.com](www.google.com) (In America)

But I think this is what you want! :P

---

### Post by SeijiSensei on 2012-12-09
1)  No, you cannot successfully redirect HTTPS requests to port 80. 

2)  If you really want to push HTTPS requests through Squid, you need to jump through some hoops.  Read [this]("wiki.squid-cache.org/Features/SslBump") for details.

---

### Post by fredbird67 on 2012-12-10
Bummer. :-/  But I have found that I can at least block such connections.  And the man-in-the-middle attack sounds a bit too involved for me to even attempt.  Therefore, adding a list of such sites to block via https in iptables will have to do until something better comes along.

---

