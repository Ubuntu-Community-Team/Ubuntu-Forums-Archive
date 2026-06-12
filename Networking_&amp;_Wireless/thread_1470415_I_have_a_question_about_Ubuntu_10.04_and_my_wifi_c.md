---
title: "I have a question about Ubuntu 10.04 and my wifi card."
date: 2010-05-02
forum: Networking &amp; Wireless
---

### Post by Cheater87 on 2010-05-02
I have a product: AR9285 Wireless Network Adapter (PCI-Express)
vendor: Atheros Communications Inc. Will this work ok with this release. With 9.10 I had to install the back ports to get wifi to work. If I have to install them again what will I type in? For 9.10 I typed in sudo apt-get install linux-backports-modules-karmic
sudo apt-get install linux-backports-modules-karmic-generic
sudo apt-get install linux-backports-modules-wireless-karmic-generic

What will I type in 10.04 to get it to work if my card is not getting a good signal? Oh and does 32 bit work better with wifi then 64 bit? I am going to be installing the 32 bit version of 10.04.

---

### Post by Cheater87 on 2010-05-03
bump

---

### Post by gordintoronto on 2010-05-03
I don't think 64-bit or 32-bit makes any difference, but I could be wrong.

Try running from a 10.04 LiveCD or, even better, a persistent USB stick, to see how your wifi works. Installing the backports would be the same, substituting "lucid" for "karmic". With a persistent USB stick, you could install the backports to confirm they work.

---

### Post by mdshaver on 2010-05-03
I had the same thoughts with the same wireless card. However, after installing the mentioned backports in 10.04, i saw no changes in wireless signal strength.

---

### Post by Cheater87 on 2010-05-04
No problems with wifi so far. :D I didn't even have to install the back ports.

---

