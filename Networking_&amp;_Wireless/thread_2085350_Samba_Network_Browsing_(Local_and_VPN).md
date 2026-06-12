---
title: "Samba Network Browsing (Local and VPN)"
date: 2012-11-17
forum: Networking &amp; Wireless
---

### Post by Boondoklife on 2012-11-17
Below is a schematic of my network setup:

```

[Local Samba PDC]    [Remote Samba]
(10.0.55.0/24)        (10.0.66.0/24)
      |                   |
      |             VPN   |
      |            (PPTP) |
      |--------|----------|
               |
               |
        [Local Computer]
        (10.0.55.0/24)

```

More Info:
I am trying to achieve the ability to not only see my local shares as well as the remote shares while connected via VPN. 

I am able to browse my local Domain shares but unable to see the remote machine shares in network neighborhood. I can access the remote machine via UNC so it would seem the connection is fine.

I am running Samba 3.5.x on both of the servers and pptpd on the remote server. I am really at a loss as to what could be the culprit and am open to suggested troubleshooting and what not.

Thanks!

---

