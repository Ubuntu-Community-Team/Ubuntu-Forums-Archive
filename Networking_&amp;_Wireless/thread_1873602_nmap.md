---
title: "nmap ?"
date: 2011-11-01
forum: Networking &amp; Wireless
---

### Post by Z.K. on 2011-11-01
I was wondering if it is possible to use an external file such as ports.txt as input so it is not necessary to list all the specific ports on the command line.  I know it can be done with the hosts IP addresses using iL, but I don't see where or if it can be done with just specific ports using a text file.

---

### Post by haqking on 2011-11-01
> **Z.K. said:**
> I was wondering if it is possible to use an external file such as ports.txt as input so it is not necessary to list all the specific ports on the command line.  I know it can be done with the hosts IP addresses using iL, but I don't see where or if it can be done with just specific ports using a text file.


you could edit the nmap services file if you want then  use -F which does a fast scan using that file

I was gonna say -iL but that is for targets

or use a redirect < possibly or bash script it if its recurring thing you do

---

### Post by Dangertux on 2011-11-01
You can specify an alternate services file by using the following 

```

nmap --servicedb filename 127.222.31.34

```

Note that it must be in the nmap-services format which is 

```

servicename port#/proto       frequency 

```

Example : 

```

http 80/tcp     0.458000

```

Hope this helps.

---

