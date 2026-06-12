---
title: "Network manager and aiccu"
date: 2011-06-24
forum: Networking &amp; Wireless
---

### Post by devil103 on 2011-06-24
I'm running into a small problem using my ipv6 tunneling protocol.
I'm using Sixxs as my tunnel and using the aiccu package to run the tunnel.

So after installing the aiccu package

```
sudo apt-get install aiccu
```

I can run the /etc/init.d/aiccu script after boot from terminal

```
 sudo /etc/init.d/aiccu start
```

but it will not start at boot. It tries to however.
When looking into the syslogd logs I can see tries to start but it can't resolve any DNS queries yet since the networkmanager hasn't started yet.

```
aiccu[1281]: Couldn't resolve host tic.sixxs.net, service 3874
aiccu[1281]: Couldn't connect to the TIC server tic.sixxs.net
aiccu[1281]: Couldn't retrieve first tunnel for the above reason, aborting
```

Is there a way change the boot order of the scripts?

---

### Post by Bachsau on 2012-04-11
You don't have an internet connection when aiccu starts. Read [http://www.meerkoetter.org/wp/2009/10/26/integrating-the-networkmanager-with-aiccu/](http://www.meerkoetter.org/wp/2009/10/26/integrating-the-networkmanager-with-aiccu/)

---

