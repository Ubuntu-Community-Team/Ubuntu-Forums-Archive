---
title: "Not able to access the internet after connecting to office VPN!!"
date: 2010-09-15
forum: Networking &amp; Wireless
---

### Post by amlife on 2010-09-15
[FONT="Trebuchet MS"]Hello 

As soon as I connect to my office Network, I lose the ability to connect to the internet or other local resources in my home network.

I tried pining by IP or DNS names with no luck, so I don't think it is DNS issue.

can someone put me in the right direction? 

Thank you

[/FONT]

---

### Post by DirtDart on 2010-09-17
> **amlife said:**
> As soon as I connect to my office Network,

If you are connecting via VPN, that's probably your issue.  Once you connect via VPN, your network connection will be the same as if you were at the office.

---

### Post by amlife on 2010-09-17
Thanks for your reply,  I was able to fix this problem, simply make sure that when you edit your VPN connection settings, click on IPv4 Settings -> Routes -> 

1. check   "Use this connection only for resources on its network" 
2. uncheck "Ignore automatically obtained routes".

open up terminal and do "ip route show" last route of the output should present the network that you are locally connected to.
I hope this helps other people in the future ;)

---

### Post by DirtDart on 2010-09-18
Glad you got it fixed!

Please mark your post as Solved, in case others have the same issue.

---

