---
title: "How to configure host/domain without network-manager"
date: 2006-02-15
forum: Networking &amp; Wireless
---

### Post by zi99y on 2006-02-15
Hi,

I've been scrabbling around trying to find how to do this - network-manager doesn't seem to work anymore - I think I abused it too much! (hangs forever when I click ok)

I have setup a dns server on the lan(debian), so I want to configure the domain for my ubuntu client, so I can talk to my network clients using hostnames instead of ip addresses. This works on a windows so I know the server is setup ok. 

Found the file /etc/hostname but am unsure how to edit it for domain name & domain searches

tia!

zi95ta

---

### Post by spd106 on 2006-02-15
Check out the /etc/resolv.conf file. You need to add a nameserver and the workgroup/domain. Here's mine as an example
```
:~$ cat /etc/resolv.conf
search workgroup
nameserver 192.168.0.1

```
Have a look in the man pages for details.

---

### Post by zi99y on 2006-02-15
you beauty! that fixed it straight away. Sorry it was so simple, I would have found it eventually but I really appreciate the assistance

:mrgreen:

---

### Post by USA1 on 2006-02-15
I am having kind of the same problem, but I am not as advance as the two of you so could you enlighten me a bit on this...

Last night I set up my broadcom card and was able to use network manager GUI to connect to the WIFI and surf the internet.

Today, all that is history, network manager just goes on an infinitive loop for ever after I click okay.

I am looking for a way I could have more control of what goes on with this networking thing that I don't quite understand.

I know the card/driver is install correctly, it has worked within the last 24hrs, but for some reason it only works when it wants to...

What is a DNS, How would it help me, and how do I set it up?

Compaq v2000, Broadcom WIFI card and Belkin WIFI router or Linsys WIFI router also.

Thanks, in advance.

---

