---
title: "btlaunchmanycurses and tor"
date: 2010-04-06
forum: Networking &amp; Wireless
---

### Post by c01e on 2010-04-06
When I do:

btlaunchmanycurses . --tracker-proxy 127.0.0.1:8118

I get Try X: died, retrying in Y

If I do not use the tracker proxy it downloads ok.

Also if I set the environment variable http_proxy to 127.0.0.1:8118 btdownloadcurses says "Problem connecting to tracker - timeout exceeded". If i unset this environment variable it downloads ok.

Tried with 9.10 and 9.04.

Any ideas?

---

### Post by Gunman1982 on 2010-04-06
Do you have a firewall installed which is blocking local port 8118?
Execute 'netstat -an | grep LISTEN' and check if there is a something listening on port 8118.

---

### Post by c01e on 2010-04-07
Nar, no firewall and nothing listening on 8118.

Are you able to use btlaunchmanycurses . --tracker-proxy 127.0.0.1:8118

---

### Post by TheSqueak on 2010-04-07
> **c01e said:**
> Nar, no firewall and **nothing listening on 8118**.

That will be your problem - you don't have a proxy server configured for btlaunchmanycurses to connect to.

Have you installed privoxy?

What output do you get if you run ```
netstat -l
```

---

### Post by c01e on 2010-04-07
Silly me, should of realised what not listen on 8118 means (must of been busy with other stuff).

Anyway, on my 8.04 machine 8118 is listen, but I still get the died errors. 

And on my 9.10, 8118 is not listening, but privoxy is installed (9050 is listening tho). Any thoughts on the first issue, as I'm sure the second issue is just a installation issue.

---

### Post by TheSqueak on 2010-04-07
> **c01e said:**
> Silly me, should of realised what not listen on 8118 means (must of been busy with other stuff).

Anyway, on my 8.04 machine 8118 is listen, but I still get the died errors. 

And on my 9.10, 8118 is not listening, but privoxy is installed (9050 is listening tho), and I can use TOR in firefox. Any thoughts for both issues.

On the 9.10 machine, try using ```
btlaunchmanycurses . --tracker-proxy 127.0.0.1:9050
```

On the 8.04 machine, what is the output from ```
sudo netstat -pln | grep 8118
```

---

### Post by c01e on 2010-04-07
Tried that on the 9.10 box too, it still gets the died errors. But I'm rather sure the proxy needs to use port 8118, I'm sure its just an installation issue on my 9.10 box. So I'd rather solve it for the 8.04Tried that on the 9.10 box too, it still gets the died errors. But I'm rather sure the proxy needs to use port 8118, I'm sure its just an installation issue on my 9.10 box. So I'd rather solve it for the 8.04 first first

```

fileserver:~/torrent_proxy_test> sudo netstat -pln | grep 8118
tcp        0      0 127.0.0.1:8118          0.0.0.0:*               LISTEN      8764/privoxy

```

---

### Post by TheSqueak on 2010-04-07
Can I see the output from:

```
sudo tail /var/log/privoxy/errorfile

sudo tail /var/log/privoxy/logfile

grep -v "#" /etc/privoxy/config
```

---

### Post by c01e on 2010-04-07
```

fileserver:~/torrent_proxy_test> sudo tail /var/log/privoxy/errorfile
Apr 04 11:40:01.061 Privoxy(7f0616d6f6e0) Info: Privoxy version 3.0.8
Apr 04 11:40:01.061 Privoxy(7f0616d6f6e0) Info: Program name: /usr/sbin/privoxy

fileserver:~/torrent_proxy_test> sudo tail /var/log/privoxy/logfile

fileserver:~/torrent_proxy_test> grep -v "#" /etc/privoxy/config
user-manual /usr/share/doc/privoxy/user-manual
confdir /etc/privoxy
logdir /var/log/privoxy
filterfile default.filter
logfile logfile
listen-address  127.0.0.1:8118
toggle  1
enable-remote-toggle  0
enable-remote-http-toggle  0
enable-edit-actions 0
enforce-blocks 0
buffer-limit 4096
forwarded-connect-retries  0
accept-intercepted-requests 0
allow-cgi-request-crunching 0
split-large-forms 0
forward-socks4a / localhost:9050 .

```

FYI, got tor/prioxy working (8118 is now listening and working in firefox) in 9.10 and still get the died issue.

---

