---
title: "Remote network fails to connect to server"
date: 2012-10-24
forum: Networking &amp; Wireless
---

### Post by linuxservernoob on 2012-10-24
Installed Ubuntu server 12.10

Everything works in local network, but remote network doesn't work.
ssh gives connection refused, open by browser fails.

I've set up a port forwarding from my router port 2222 to my server 22, and another from router port 2223 to my server 80.
I've set acces-list to permit from those ports also.

Both of these don't work. While local network works.

Added files for settings

Apache2 ports gives:

Namevirtualhost *:80
listen 80

....

---

