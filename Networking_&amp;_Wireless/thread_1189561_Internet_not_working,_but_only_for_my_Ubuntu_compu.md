---
title: "Internet not working, but only for my Ubuntu computer..."
date: 2009-06-16
forum: Networking &amp; Wireless
---

### Post by Bradj47 on 2009-06-16
My internet just stopped working today. I have had Ubuntu 9.04 installed since April and this has just happened for the first time. I can still ping other computers on my network and my other computers get internet. What could have happened?

---

### Post by pedja_portugalac on 2009-06-16
Did you change your iptables settings?

---

### Post by Bradj47 on 2009-06-16
I didn't. Not intentionally anyway. I hadn't even heard of iptables until now. I'll read through the man page. Perhaps an application modified them?

---

### Post by Iowan on 2009-06-16
**route -n** look kosher? */etc/resolv.conf* showing proper DNS servers?

---

### Post by Bradj47 on 2009-06-17
Ah, thanks. It was the DNS servers, it didn't have the proper DNS names in there. And I am happy to say that I am making this post back on my Ubuntu computer. :D Thanks!

---

