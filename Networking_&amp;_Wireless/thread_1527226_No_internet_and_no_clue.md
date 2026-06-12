---
title: "No internet and no clue"
date: 2010-07-09
forum: Networking &amp; Wireless
---

### Post by wlraider70 on 2010-07-09
I have been working on getting my bind9 service up. 
I have been successful. Now I have no internet and i don't know why.

My error log shows nothing.
I can ping Google. so is it my DNS resolve?

```

/etc/resolv.conf

domain ZION.COM
search ZION.COM
nameserver 127.0.0.1
nameserver 208.67.222.222
nameserver 208.67.220.220


```

it looks normal?

I tried commenting out local host, no change.


Where do i start?

---

### Post by Iowan on 2010-07-09
> **wlraider70 said:**
> I have been working on getting my bind9 service up. 
I have been successful. Now I have no internet and i don't know why.I'm not poking fun at you, but somehow, that doesn't seem like success. ;)

The 127.0.0.1 doesn't seem right - I have my DNS server (DNSMasq) pointed at the next upstream machine.

Can you ping Google by name, or just IP address? 
Did you restart after editing?

---

### Post by wlraider70 on 2010-07-10
lol thanks. i guess i should have said it looks successful.

I am getting this error. 

```

luke@media:~$ sudo service bind9 restart
 * Stopping domain name service... bind9                                                         rndc: connect failed: 127.0.0.1#953: connection refused
                                                                                          [ OK ]
 * Starting domain name service... bind9                                                  [fail] 
luke@media:~$ 

```

of course i looked it up most people aren't having the port issue, and most of them fix it by changing the controls of the key. I have done those things.

If there is something more to do with them im missing it.

---

