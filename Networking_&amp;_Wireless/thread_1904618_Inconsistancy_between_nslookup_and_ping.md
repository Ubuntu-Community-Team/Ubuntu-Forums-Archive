---
title: "Inconsistancy between nslookup and ping"
date: 2012-01-05
forum: Networking &amp; Wireless
---

### Post by Neill_R on 2012-01-05
Hi

A simple question can you help me explain why this happens
please note that this machine was at one time 10.2.10.35 but I changed the subnet mask to 
10.10.1.x/255.255.255.0

i can ping 10.10.1.35 but what is making it look for 10.2.10.35 the old address?

There is a windows 2000 Adv Server at 10.10.1.10 the ubuntu pc 11.04 has joined the domain using likewise. On the server ping freds works.

```


ME\administrator@freds:~$ nslookup freds.me.dyndns-ip.com
Server:        10.10.1.10
Address:    10.10.1.10#53

Name:    freds.me.dyndns-ip.com
Address: 10.10.1.35

ME\administrator@freds:~$ ping freds.me.dyndns-ip.com
PING freds.me.dyndns-ip.com (10.2.10.35) 56(84) bytes of data.
^C
--- freds.n-rutherford.dyndns-ip.com ping statistics ---
10 packets transmitted, 0 received, 100% packet loss, time 9072ms

ME\administrator@freds:~$ 



```

---

### Post by Doug S on 2012-01-05
One possibility is that the DNS reverse files were not updated to reflect the change.
Another possibility is local "hosts" file(s), if there were entries made for this name, were not updated to reflect the change.
There might be other reasons, I don't know.
 
Hope this helps.
 
Edit: (I tihnk) Sometimes windows computers need to be told to forget old DNS stuff. I think (don't quote me) the command is "ipconfig /flushdns"

---

### Post by Neill_R on 2012-01-05
Spot on it was my hosts file /etc/hosts removed the offending 10.2.10.35 reference and it now works. Thank you for reminding me of this file did the windows PC but forgot this one.

Thank you

---

