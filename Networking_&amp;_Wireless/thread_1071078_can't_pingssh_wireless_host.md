---
title: "can't ping/ssh wireless host?"
date: 2009-02-15
forum: Networking &amp; Wireless
---

### Post by lourp on 2009-02-15
I have a peculiar network issue I think. It may turn out to be perfectly normal?

I have a desktop server connected to router via cat5 cable. I have a remote HTPC (mythbuntu) wirelessly connected to the router via a TP-LINK TL-WN321G USB adapter.

The HTPC has no issue connecting to internet.

From the HTPC, I can ping/ssh to the desktop server. From the server I cannot ping/ssh the HTPC at all?

Is this a firewall issue? If I plug the HTPC in with a network cable, there is no problem whatsoever. Why would a firewall deprive a wlan0 interface of pings etc, but not the eth0?

---

### Post by lourp on 2009-02-15
Well I can rule out firewall. Installed firestarter and disabled firewall completely. I still cannot ping the mythbuntu wireless machine from the desktop server.

Perhaps my router is preventing this? Billion 7401VGP.

---

### Post by zander1013 on 2009-02-16
hi,

can you ping the other machine if they are connected by hardwire?

i am having ssh issues to i cannot even connect with a cat5 cable beteween them.

---

### Post by dmizer on 2009-02-16
Are you sure you are connected to your own wireless network, and not a neighbors?

Edit:
Nope ... bad dmizer, no points for reading comprehension today :)

You indicated that you can ssh from the wireless to the desktop but not from the desktop to the wireless. This sounds like one of a few possible issues:
1) Is Openssh-server installed and correctly configured on the wireless computer?
2) Is the openssh-server daemon actually running on the wireless computer?
3) Firewall on the wireless computer?

Installing firestarter probably made your problem worse.

---

### Post by lourp on 2009-02-16
ssh is my goal, but ping is not working which concerns me more. Does a firewall block ping? I have forced my router to always issue the wireless with the same IP address.

ssh is installed correctly, as with cat5 connection, I can ping/ssh no problem (different IP).

Why would I have made things worse with firestarter? Isn't just a gui wrapper for iptables?

---

### Post by dmizer on 2009-02-16
Yes it's just a gui wrapper for IPtables, but its default configuration is overly restrictive (blocks almost all LAN resources including ICMP and SSH) and takes knowledge and patience to configure it correctly. It's actually easier to manually configure UFW from the command line.

Plus, any time you're having trouble with a system resource, step number 1 in troubleshooting is to completely disable any firewalls. It appears that all you did was to ditch one firewall configuration for another.

Further, with firestarter ... even if you disable it, it's not actually disabled.

---

