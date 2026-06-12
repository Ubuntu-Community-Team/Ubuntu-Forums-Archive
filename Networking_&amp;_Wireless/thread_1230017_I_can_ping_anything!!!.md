---
title: "I can ping anything!!!"
date: 2009-08-02
forum: Networking &amp; Wireless
---

### Post by doublempi on 2009-08-02
I have a netgear router at 192.168.0.1. I have two wired desktops at 192.168.0.2 and 192.168.0.4. My laptop is at 192.168.0.3. I can connect to the Internet from all three machines with no problem. My difficulties started when I decided to set up a home network. I can ping 192.168.0.2 and 192.168.0.4 from any machine, but pinging 192.168.0.3 fails.

So I started running ping and tracepath to try to figure out what the problem was, and found out that I can ping anything. Here's some output.

PING yahoo.com (69.147.114.224) 56(84) bytes of data.
64 bytes from b1.[www.vip.re3.yahoo.com](www.vip.re3.yahoo.com) (69.147.114.224): icmp_seq=1 ttl=50 time=35.7 ms

PING dkfjdkfj (67.63.55.33) 56(84) bytes of data.
64 bytes from mediacomassist.infospace.com (67.63.55.33): icmp_seq=1 ttl=238 time=37.0 ms

PING aklsdjfalksdjflaksdfj (67.63.55.33) 56(84) bytes of data.
64 bytes from mediacomassist.infospace.com (67.63.55.33): icmp_seq=1 ttl=238 time=43.4 ms

Yahoo.com is a good address. The other two entries are the problem.

Can anyone help?

Thanks,
Mike

---

### Post by Iowan on 2009-08-03
Your ISP happen to be Mediacom? Looks like there's a machine (67.63.55.33) trying to "assist" (proxy?).

---

### Post by doublempi on 2009-08-03
> **Iowan said:**
> Your ISP happen to be Mediacom? Looks like there's a machine (67.63.55.33) trying to "assist" (proxy?).

You're right. Mediacom provides a "service" where you're redirected to their custom search page when you try a non-existent URL. I found out how to disable it, so now I get a normal not found/404.

Thanks,
Mike

---

