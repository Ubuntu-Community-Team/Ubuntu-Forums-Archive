---
title: "Dynamic IP address with PTR record versus Fixed IP address without"
date: 2010-05-07
forum: Networking &amp; Wireless
---

### Post by ruyterb on 2010-05-07
Hi,

I am running my own Postfix mail server. Some time ago I noticed that most email was rejected because of the server's dynamic IP address. So I got a fixed IP address. However then I noticed that some mails got rejected due to failing the reverse DNS check. So my ISP told me to get a range of IP addresses and they could then create a PTR record for one of those addresses. That is now running but it turns out that the IP address used for the PTR record is a ... dynamic IP address. So Spamhaus PBL rejects my emails again.

How do I resolve this?

---

