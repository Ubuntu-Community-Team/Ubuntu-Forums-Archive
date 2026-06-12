---
title: "networking issues after installing xubuntu 9.10"
date: 2010-06-21
forum: Networking &amp; Wireless
---

### Post by cjff1963 on 2010-06-21
I was running xubuntu 8.04 for over a year with no issues on a Gateway Solo 2500, using a Compaq WL100 PCMCIA wireless lan card. I decided to install Xubuntu 9.10 from scratch, and, even though the lan card works perfectly during the installation process (I am using the Alternate version CD), the card does not connect once the installation is complete and the machine is rebooted.\
I ran the lshw -C network, and both the Compaq card and the network interface seem ok.

Any ideas? I know it is a very old system, but it was working fine so far.

Thanks.

---

### Post by cjff1963 on 2010-06-25
After finding and loading an agere_sta_fw.bin file, the behaviour of the card looks better, but the error log now shows a line saying "Lucent/Agere firmware doesn't support manual roaming".

Any suggestions?

---

