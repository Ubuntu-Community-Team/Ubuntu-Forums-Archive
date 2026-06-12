---
title: "PPTP Server and PPTP Client"
date: 2011-07-01
forum: Networking &amp; Wireless
---

### Post by Undici77 on 2011-07-01
Hello friends, I'm new here and I'm a new Ubuntu user.

My situation in this:

- Ubuntu server with poptop service
- Windoz 7 machine witt pptp client
- Ubuntu 11.04 with network manager

My pptp server working perfect with all windows machine:
- mschap2 with mppe-128

But using the same connections from my fresh installation of Ubuntu I get the message "Connection Failed".

I attach here some logs from my server

```


Jul  1 21:37:17 Giove pptpd[25362]: CTRL: Client 192.168.0.175 control connection started
Jul  1 21:37:18 Giove pptpd[25362]: CTRL: Starting call (launching pppd, opening GRE)
Jul  1 21:37:18 Giove pppd[25363]: Plugin /usr/lib/pptpd/pptpd-logwtmp.so loaded.
Jul  1 21:37:18 Giove pptpd[25362]: GRE: Bad checksum from pppd.
Jul  1 21:37:18 Giove pptpd[25362]: GRE: read(fd=6,buffer=8058660,len=8196) from PTY failed: status = -1 error = Input/output error, usually caused by unexpected termination of pppd, check option syntax and pppd logs
Jul  1 21:37:18 Giove pptpd[25362]: CTRL: PTY read or GRE write failed (pty,gre)=(6,7)
Jul  1 21:37:18 Giove pptpd[25362]: CTRL: Reaping child PPP[25363]
Jul  1 21:37:18 Giove pptpd[25362]: CTRL: Client 192.168.0.175 control connection finished


```Any ideas??

I trust my server side configuration because it's working from many years (and is working with all windows machine)

But It can't work with Ubuntu...

Thanks!!

---

### Post by poolet on 2011-07-02
I am not sure about that but lets try to see what happen.....
Try the following::::

open up a new terminal and type::
```
nano /etc/ppp/pptpd-options
```

putting # sign in start
 [B]#require-mppe-128

[/B]Please let me know if that works......

---

