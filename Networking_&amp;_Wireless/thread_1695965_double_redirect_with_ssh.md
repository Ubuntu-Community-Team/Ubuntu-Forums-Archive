---
title: "double redirect with ssh?"
date: 2011-02-26
forum: Networking &amp; Wireless
---

### Post by miak on 2011-02-26
Hi,  I know you redirect your traffic from your computer's specific port to a second computer with ssh, and it works fine for me. But I was wondering if you can then redirect the same traffic from the second computer to the third? I think it is possible, but I don't seem to be able to do it. Say I redirect my computer's 4444 port to the second computer. I tried redirecting seconds computer's 4444 port, but it didn't help. Also 1080 port just in case since I was using SOCKS protocol, but it didn't help again. Any suggestion?  Thanks in advance, miak

---

### Post by miak on 2011-02-26
I think I got it, just unfortunately don't have root privileges on the second computer to test it. SSH binds to the port 22 on the second computer, and you can specify which port to bind to by the option -p(for me this doesn't work as the second computer refuses connections to all the other ports.) then if you had root privileges you can just redirect port 22, but I don't. This was the way I thought when writing the previous post, but is there any other way?   -miak

---

