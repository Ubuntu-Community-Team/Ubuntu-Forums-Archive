---
title: "How to clear TCP metrics cache?"
date: 2011-07-20
forum: Networking &amp; Wireless
---

### Post by bingasedu on 2011-07-20
I'm trying to do some network testing, and I've set net.ipv4.tcp_no_metrics_save=1, but I'm concerned that some connection information was cached before I made this change.  Is there a way to clear whatever cache stores the tcp metrics info?  Thanks.

---

### Post by jmoorse on 2011-07-21
Why are you setting this?

You can check that this value is still valid:

```

cat /proc/sys/net/ipv4/tcp_no_metrics_save

```

I am not sure of a way to query the kernel for the cwnd per session, but now I am curious....

---

### Post by bingasedu on 2011-07-21
Thanks -  I'm setting this because I'm running some network tests between two local machines, and my understanding is that by default some connection characteristics are cached and used for subsequent connections to the same host.  I don't want past connection behavior to impact a current connection in any way while I'm doing testing.  Is there any documentation on what information is cached and where it is stored?  Btw  - I'm running Ubuntu 9.10.

---

### Post by jmoorse on 2011-07-21
Kernel documentation talks about this, I could not find where it is stored.  It my just be kept in /proc/net/tcp  I think the particular string stores things like sender cwnd.

Are you running tests over TCP?

More info here: [http://www.kernel.org/doc/Documentation/networking/ip-sysctl.txt](http://www.kernel.org/doc/Documentation/networking/ip-sysctl.txt) and here [http://www.kernel.org/doc/Documentation/networking/tcp.txt](http://www.kernel.org/doc/Documentation/networking/tcp.txt) (TCP specific)

---

### Post by bingasedu on 2011-07-22
Thanks for suggesting looking in /proc/net - I think that's where it's stored.  According to the documentation the metrics are saved in the route cache, and /proc/net/rt_cache looks to be storing things like src, dst, window, and RTT.  I think that I'm all set as long as the entries for my local network interface are all zeroed out.

I'm running tests over TCP and SCTP, and SCTP doesn't cache info from past connections.

- Jon

---

