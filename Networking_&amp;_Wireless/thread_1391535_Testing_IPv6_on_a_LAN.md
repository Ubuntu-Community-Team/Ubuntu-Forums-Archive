---
title: "Testing IPv6 on a LAN"
date: 2010-01-26
forum: Networking &amp; Wireless
---

### Post by Rob_H on 2010-01-26
Hi. I have two Ubuntu boxes on a LAN and I'm trying to get them talking to each other over IPv6 as a test. Following this [HOWTO]("http://tldp.org/HOWTO/Linux+IPv6-HOWTO/"), I gave each one a static, site local address. On the first box I ran:

```
sudo ifconfig eth0 inet6 add fec0::1/64
```

And on the second box, I ran:

```
sudo ifconfig eth0 inet6 add fec0::2/64
```

Next, on the second box, I added a new entry in /etc/hosts for the first box, mapping it to fec0::1. And then I tried to SSH from the second box to the first using the new name. 

Unfortunately, SSH just hangs. No error or anything. If I run tcpdump during the test, I don't see any IPv6 traffic at all. What am I doing wrong? Any help appreciated.

---

### Post by Rob_H on 2010-01-27
<bump> Any ideas?

---

### Post by Lars Noodén on 2010-01-27
> **Rob_H said:**
>  If I run tcpdump during the test, I don't see any IPv6 traffic at all. What am I doing wrong? Any help appreciated.

That would be your first place to look.  Can you ping it with [ping6](http://manpages.ubuntu.com/manpages/karmic/en/man8/ping6.8.html) or not?  Try both directions.

---

### Post by Rob_H on 2010-01-27
> **Lars Noodén said:**
> That would be your first place to look.  Can you ping it with [ping6](http://manpages.ubuntu.com/manpages/karmic/en/man8/ping6.8.html) or not?  Try both directions.

I did try ping6 from the client to server, and strangely, I got "operation not permitted" even when I ran it under **sudo**.

---

### Post by Skaperen on 2010-02-02
Try using a "Unique Local Address" like fdXX:XXXX:XXXX:XXXX:ZZZZ:ZZZZ:ZZZZ:ZZZZ/64 where the X's are randomly generated (RFC 4193 section 3.2.2 suggests a way) and the Z's are the EUI-64 translation of your MAC address, which you can get from the lower 64 bits of the link-local address already generated for the interface.

---

### Post by Rob_H on 2010-02-02
Interesting. I will give that a shot. Thanks.

---

### Post by Skaperen on 2010-02-02
Here is some (wide) code you can use in a script to automatically set the address, after you set the environment variable ULA to the first 64 bit part (also shown in the example with a fake ULA value):
```
export ULA="fd01:0203:0405:0607"
ifconfig | awk '{if(substr($0,1,1)!=" ")i=$1;if($1=="inet6"&&$2=="addr:"&&substr($3,1,6)=="fe80::"&&$4=="Scope:Link")printf "ifconfig %s add %s:%s\n",i,ENVIRON["ULA"],substr($3,7);}' | sh
```

---

