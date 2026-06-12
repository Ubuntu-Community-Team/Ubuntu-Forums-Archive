---
title: "Obtain ip address and timed commands?"
date: 2009-07-07
forum: Networking &amp; Wireless
---

### Post by PartisanEntity on 2009-07-07
I have the following scenario/issue:

I have my Linux box at home, when I connect it to a paid VPN service, the ip number of my machine changes, so I am then unable to connect a remote desktop session to it because I don't know the ip number (the vpn service offers random ip's each time).

How could I have my machine email me it's current ip number? Is this possible at all? Or have it visit a secret link on my site and then obtain the ip number through a php script?

**Basically, question 1 is: can I automate my machine to visit a link when openvpn is active?**

My second question is can I time an app to launch at a specific time? Probably with "at" command?

Thanks!

---

### Post by jpeddicord on 2009-07-07
Would a dynamic DNS service do well here? I use [http://freedns.afraid.org/](http://freedns.afraid.org/) and it's held up pretty well - not sure how well it will integrate with a VPN service, though.

---

### Post by PartisanEntity on 2009-07-07
> **jacobmp92 said:**
> Would a dynamic DNS service do well here? I use [http://freedns.afraid.org/](http://freedns.afraid.org/) and it's held up pretty well - not sure how well it will integrate with a VPN service, though.

Thanks, but how would the service work if I activate the vpn connection remotely on the machine? Would the dns service update automatically and if yes how ?

---

### Post by jpeddicord on 2009-07-07
> **PartisanEntity said:**
> Thanks, but how would the service work if I activate the vpn connection remotely on the machine? Would the dns service update automatically and if yes how ?

Typically you'd install a client that would periodically check your IP, and if it changes send the new IP to the DNS provider to update the record. Only problem is that sometimes these records take anywhere from 5 minutes to an hour to propagate.

What you could do is something similar to what you originally asked. Make a Perl/CGI/PHP script that calls "ifconfig" when visited and displays the IP for all of its interfaces. I think the PHP code is:[PHP]<?php
header("Content-type: text/plain");
echo system("ifconfig");[/PHP]

EDIT: Yep, works. [http://jacob.us.to:8080/ipstuff.php](http://jacob.us.to:8080/ipstuff.php) is it running on my laptop.

---

### Post by PartisanEntity on 2009-07-07
> **jacobmp92 said:**
> Typically you'd install a client that would periodically check your IP, and if it changes send the new IP to the DNS provider to update the record. Only problem is that sometimes these records take anywhere from 5 minutes to an hour to propagate.

What you could do is something similar to what you originally asked. Make a Perl/CGI/PHP script that calls "ifconfig" when visited and displays the IP for all of its interfaces. I think the PHP code is:[PHP]<?php
header("Content-type: text/plain");
echo system("ifconfig");[/PHP]

EDIT: Yep, works. [http://jacob.us.to:8080/ipstuff.php](http://jacob.us.to:8080/ipstuff.php) is it running on my laptop.

Perfect thanks, I think this is the easier method which I can call when needed.

But I am having trouble with the "at" command in the terminal, and the man page is not very clear

What is the correct syntax to use "at"? Can anyone post a few examples? I keep getting syntax errors.

---

### Post by koenn on 2009-07-07
> **PartisanEntity said:**
> Thanks, but how would the service work if I activate the vpn connection remotely on the machine? Would the dns service update automatically and if yes how ?

you run a client on your computer that checks the computer's email addres and updates the DNS record, 

eg; ddclient working with dyndns: 
[http://www.dyndns.com/support/kb/using_ddclient_with_dyndns_services.html](http://www.dyndns.com/support/kb/using_ddclient_with_dyndns_services.html)

```

daemon=600                  # check every 600 seconds
....

### Select one of these options to determine your IP address
...

## via our CheckIP server
use=web, web=checkip.dyndns.com/, web-skip='IP Address'

```

That works just fine for normal internet access with an ISP dynamically assigning addresses.

I'm not sure if it's going to work for you, but that depends on how your vpn works and what you use it for
A- if all your traffic is routed through the vpn tunnel, you may not be able to reach dyndns (or similar service) anymore - unless that vpn also provides internet access

B- it's a bit strange that a vpn conf would change your IP address. Normal operation is to use an existing (but untrusted) network, and use that as the carrier for your secure tunnel. So in stead of having your IP address changed, you'd see a new interface with a different address created alongside it. 
Maybe you have to elaborate on the sort of vpn this provider offers

---

### Post by koenn on 2009-07-07
never used it before, but try something like this
```

k@xinix:~$ at 21:28
warning: commands will be executed using /bin/sh
at> command 1
at> command 2
at> command 3

ctrl+D to end input

```

in scripts ```

at 21:28 <<EOF
command 1
command 2
command 3
EOF

```

it doesn't write to stdout, so you don't get to see output, but it seems to at least register the jobs :

```

k@xinix:~$ atq
3	Tue Jul  7 21:28:00 2009 a k


```

this also works:```
k@xinix:~$ at now + 1 minute 
...
...


```

---

### Post by stwschool on 2009-07-08
The easy way.. set up a cron job to do this..

wget [http://www.mysite.com/getmyip.php](http://www.mysite.com/getmyip.php)

every 5 minutes.

---

