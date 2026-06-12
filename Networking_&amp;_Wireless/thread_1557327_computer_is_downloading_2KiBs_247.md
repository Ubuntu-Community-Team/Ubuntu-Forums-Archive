---
title: "computer is downloading 2KiB/s 24/7"
date: 2010-08-20
forum: Networking &amp; Wireless
---

### Post by rowbird on 2010-08-20
Can someone help me discover what on earth is downloading and stop it. I tried to upgrade to the new ALSA driver with the user script, and it left in error. Thanks in advance wireshark showed LLC SNAP many of them.  THanks in advance

---

### Post by stlsaint on 2010-08-20
If its a process than just kill it with htop but are you sure your not just reading send/receive signals to router/gateway?

---

### Post by CharlesA on 2010-08-20
**netstat **will show current connections.

---

### Post by rowbird on 2010-08-20
Here are htop, and netstat outputs. I did discover it is a root process since the other user accounts are showing the same symptoms.

---

### Post by rowbird on 2010-08-20
Thanks guys, It stopped on it's own , but I was able to use nethogs in synaptic package manager to identify pids on my network.

---

### Post by rowbird on 2010-08-22
Update, Not solved. Nethogs only works on Ethernet, and I found that my wireless driver to be the culprit, although I don't know how to stop it. I am using rt3090-dkms_2.3.1.3-0ubuntu0~ppa1_all.deb to run my wireless Ralink 3090. It will not download anything when using external wireless. Any help will be appreciated. Thanks.

---

