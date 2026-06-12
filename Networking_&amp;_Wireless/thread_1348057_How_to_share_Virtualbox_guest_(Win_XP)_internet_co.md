---
title: "How to share Virtualbox guest (Win XP) internet connection to host (ubuntu 9.10)"
date: 2009-12-06
forum: Networking &amp; Wireless
---

### Post by Otto321 on 2009-12-06
I can't find any proper posts that covers the hole procedure to do this. I am a Newbie - so I need all steps. Please HELP I been spending 5-6 hours already.

Host OS: Ubuntu 9.10
Virtualbox:    3.1
Guest OS: Windows XP Professional SP3

Goal: to share the internet of my dialup connection in Guest OS to Host Ubuntu.

I tried many things.... right now in virtualbox network settings I have Host-adaptor and in guest I have enabled ICS on the dial up. I have the feeling I need to do something on the Ubuntu (host) OS to make this work. I can not get to any pages on internet with Firefox in Ubuntu, XP ok.

Do you know how to do this or do you know of an instruction how to do this (link)?
What to do on Ubuntu?
What to do in XP? (if not only enabeling ICS on the connction intended to share internet from)

THANK YOU,
Otto

---

### Post by sedawk on 2009-12-07
From a high level you have to do this:

Solution A with IP forwarding:
* ethernet network card "lan0" in XP (a virtual one defined in virtualbox)
* forward traffic from "lan0" to your dialup IP (I have no clue
  how to do this with XP).
* Check your Host OS can ping the IP of lan0 (in windows).
  If it can do set the IP of lan0 as your default gateway
  in the host OS. Now requests to unknown IPs should
  be send to "lan0".
* Name resolution still doesn't work. You have to define
  a DNS server. You have to check the IP of the DNS that
  XP gets from the dialup-connection and set that one
  one the Host OS. 

Solution B with proxy (like squid):
When using a proxy you can skip IP forwarding and DNS
but can only use basic web browsing via HTTP/HTTPS.
The proxy will forward all requests incoming on "lan0"
to the real internet located on the dialup connection
and the name resolution will happen automatically.

---

### Post by Otto321 on 2009-12-08
sedawk, thanx:) I investigated Solution A and finally found a solution at [http://forums.virtualbox.org/viewtopic.php?f=7&t=23823](http://forums.virtualbox.org/viewtopic.php?f=7&t=23823). It does not work 'as is' but I will make comments in that thread. The disadvantage of that solution is that a script must be run after each time Virtualbox has been restarted. Also if the preferred DNS server is changing often (my case dep. on internet provider) the DNS IP must be extracted from the guest to be used in the script of the host.

If anyone has a permanent solution it would be much welcomed in this thread.

---

