---
title: "PPPoE: How to get updated dynamic external IP in iptables script?"
date: 2009-01-24
forum: Networking &amp; Wireless
---

### Post by Master One on 2009-01-24
If you use your machine to establish a PPPoE connection to your ISP, with an iptables script to protect you and LAN from the internet + internet connection sharing, and you want to use the dynamic external IP address of your ppp0 device in your iptables script, what's the way to get your $EXT_IP variable updated once the external IP changes?

I could not find any info, how this can be handled the easy way. It was somewhere mentioned, that the iptables script should be rerun once the external IP changes, but how is this supposed to be done?

I want to setup an Ubuntu Server as a gatway-machine. Till now, I thought, I just configure the PPPoE connection with pppoeconf and then write an iptables script, but there is clearly something missing, if you only get a dynamic IP from your ISP.

---

