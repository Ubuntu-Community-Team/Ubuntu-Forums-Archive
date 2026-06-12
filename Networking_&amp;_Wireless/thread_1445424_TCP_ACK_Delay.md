---
title: "TCP ACK Delay"
date: 2010-04-02
forum: Networking &amp; Wireless
---

### Post by ff8jake on 2010-04-02
Hello,

Currently I have a VPS running Ubuntu 9.10 that I use nearly exclusively for tunneling connections for an online game I play (MMORPG, Aion). It works great for lowering ping times for me and a few friends, but I would like to push the performance a little further so I have been reading around for 'optimal' network settings.

It seems the biggest performance booster on most Windows machines is disabling the TCP Ack delay in the registry. I have searched around google for this setting in Ubuntu but I am not sure exactly which one I should adjust. I see several users doing this for Mac OS by adding entries to /etc/sysctl.conf - but after doing sysctl -a on the server the values appear to be quite different.

So I have three questions:

1. What is the default setting for TCP ACK delay in Ubuntu?
2. Can it be adjusted and if so, where?
3. Using Putty to SOCKS proxy to the server via SSH, will I also need to apply the TCP ACK adjustments to the local client machine for improvement?

Thank you! :popcorn:

---

