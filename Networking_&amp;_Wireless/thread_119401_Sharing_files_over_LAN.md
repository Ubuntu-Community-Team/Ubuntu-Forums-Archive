---
title: "Sharing files over LAN"
date: 2006-01-19
forum: Networking &amp; Wireless
---

### Post by kyldere on 2006-01-19
Hello all ...

This is my first post, and I consider myself a n00b, so please take it easy on me. Here is my problem in a nutshell:

I have installed Ubuntu 5.10 on my desktop and laptop. Both have working wired NICs and I am able to browse the Internet on either of the machines (or both at the same time, if I so choose). I have my router set up to administer addresses via DHCP and I can ping one machine from the other. What do I need to do (install, run, etc) to enable file sharing between the two computers? I am also concerned about security (to an extent ... I am using a hardware firewall that is built into my router). I have browsed the forums here and see that SAMBA is used for Windows sharing, and NFS has been mentioned, albeit with caveats regarding security. I could also probably set up SSH, but will this pose a security risk?

My apologies for not including pertinent information and thanks for any help are offered.

---

### Post by marcantonio on 2006-01-19
The easiest and most secure way to share files between two Linux boxes is SSH.  Just use the scp command.

---

