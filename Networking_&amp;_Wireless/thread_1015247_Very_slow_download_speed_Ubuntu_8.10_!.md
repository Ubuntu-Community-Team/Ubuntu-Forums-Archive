---
title: "Very slow download speed Ubuntu 8.10 !"
date: 2008-12-18
forum: Networking &amp; Wireless
---

### Post by WILL_CHAN on 2008-12-18
- I usually get 1.2mb/s to 1.8mb/s under Windows Vista when downloading from Megaupload and Rapidshare.com. I got both these two accounts and use very fast package for Internet( Time-Warner cable ). However when I download under Ubuntu, the speed is just 200Kb/s->800Kb/s for Mega and only 200-300Kb/s for Rapidshare ! I don't know why there's such a big difference like that ? 
- I already tried wget and download browser of Firefox. Could anyone help me out ?

---

### Post by ProNux on 2008-12-20
I am not sure if this is applicable on normal downloads.  In using torrents, you should open a port.  Open the console/terminal and type the following.

sudo iptables -A INPUT -P tcp --dport 6881 -j ACCEPT

Not sure if it can solve.

---

