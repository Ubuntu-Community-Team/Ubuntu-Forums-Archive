---
title: "DNS problem?"
date: 2009-03-02
forum: Networking &amp; Wireless
---

### Post by icek on 2009-03-02
Hi,
I have installed ubuntu on my girlfriend´s PC, everything works great, but internet. I set IP, dns, gate... Now, problem is, that she can acces sites which have domain of our country, but if she try lets say [www.youtube.com](www.youtube.com), it do not work... I can ping to [www.youtube.com](www.youtube.com), but site does not load... Before there was XP and it was OK. 

So, is there something I should check? or may this be a bug?

---

### Post by dmizer on 2009-03-02
What version of Ubuntu did you install?

Try disabling IPv6 according to this howto: [https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4](https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4)

---

### Post by icek on 2009-03-03
Ubuntu 8.10, IPv6 is disabled already...

---

### Post by dmizer on 2009-03-03
Try using Opendns (as a test): [https://www.opendns.com/start/device/ubuntu](https://www.opendns.com/start/device/ubuntu)
(follow the directions under step [noparse]8)[/noparse].

---

### Post by icek on 2009-03-03
thank you, problem solved :-) but I still have no idea why it did not work with DNS of her internet provider...

---

### Post by dmizer on 2009-03-03
> **icek said:**
> thank you, problem solved :-) but I still have no idea why it did not work with DNS of her internet provider...

Ubuntu pulls DNS from the gateway, so her router was probably not forwarding DNS requests correctly. If you use the same method outlined on the OpenDNS page to include her ISP DNS servers, you'll probably have satisfactory results as well.

---

