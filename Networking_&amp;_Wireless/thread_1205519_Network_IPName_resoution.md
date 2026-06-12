---
title: "Network IP/Name resoution"
date: 2009-07-06
forum: Networking &amp; Wireless
---

### Post by sideaway on 2009-07-06
Ok I have strange intermittent problem, I'm using a intel wireless card (unsure what it is) and it has issues with name resolution I think.

What happens is during normal browsing, for about 20 seconds firefox pages will time out, I keep clicking refresh until it works, it continues to work for about 10minutes then it timeouts for 20 seconds again. Now in a terminal, during one of these time outs I cannot ping [www.google.com](www.google.com), however I can ping 74.125.127.100 (google) Which leads me to believe it's a name resolution thing.

Unsure though, hopefully someone can help,
Cheers,
aim

---

### Post by superprash2003 on 2009-07-06
try using opendns servers - 208.67.222.222 and 208.67.220.220

---

### Post by jonobr on 2009-07-06
Hello


It sounds like a problem with your ISP who may be providing your DNS.,

I think superprash2003 is alluding to this by recommending you to switch DNS providers.

That would be a long way to proving the issue is with the ISP.

What you could also do is to do a wireshark trace while your having one of these problems and see what the packets look like.
This would give you ammunition for your ISP to show them their DNS is flaky.


The best way to do it is , during the times your having problems you could run a tcpdump on the DNS port as follows

```
sudo tcpdump -w trace.pcap -s 1600 port 53
```

The try doing a browse to another website to see if packets go out and come back.

The trace above will produce a file called trace.pcap
you will be able to open this in wireshark.

If it shows one packet going out and no response, then you know its an isp issue and you could provide the trace to them.
If you see a packet coming back, then it could be a setup issue.

One last recommendation is to not use the same url each time.

Using a different url each time you troubleshoot this will mean you are not getting involved in any local or router caching issues, and when tracing, you can see where you went each time you did the test

Cheers

---

