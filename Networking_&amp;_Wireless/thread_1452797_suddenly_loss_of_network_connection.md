---
title: "suddenly loss of network connection"
date: 2010-04-12
forum: Networking &amp; Wireless
---

### Post by residentevil on 2010-04-12
Hi fellas :)
I got a really strange problem. I loose my network connection almost suddenly. Now I said 'almost' because it's not that unexpected. It happens every single time when I start downloading torrents or I am sending a mail with an attachment bigger than 1M.
I have checked records in /var/logs but no error message appears to be there.
The problem is solved when I restart the networking, the following line do the job for me:
```

/etc/init.d/networking stop
start networking

```

The only error message which I can get is when I start ```
ping google.com 
```
and the network freezes during that time.
The error message is:
```

ping: sendmsg: No buffer space available

```

It seems that it is an issues with the network buffer, but to be honest I have no idea how to fix it.

I am using ubuntu 9.10 on a laptop HP compaq 6715s(if you google it you can find its hardware specs).

Any ideas ? Anyone experienced a similar problem ?

Thanks & Regards.

---

### Post by UbuKunubi on 2010-04-12
Is AOL your ISP? they have some 'problems' today.

If so call them on 08444995555 to find out more about the outage in your area.

Hope this of help,
Ubu

---

### Post by residentevil on 2010-04-12
No, it's Manchester University & ja.net

However, it seems that it is NOT ISP dependent. It tend to happen on my home connection as well.

---

