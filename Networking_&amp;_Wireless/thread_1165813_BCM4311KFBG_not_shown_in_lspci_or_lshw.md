---
title: "BCM4311KFBG not shown in lspci or lshw"
date: 2009-05-21
forum: Networking &amp; Wireless
---

### Post by pb10gagan on 2009-05-21
i have compaq v6000. previously i had windows xp on it. one fine day i installed ubuntu ibex intrepid 8.10. everything was fine.
i used my wireless and all.
one day i updated the release and suddenly my wireless stopped working.
i googled a lot, every solution to this problem starts with "see if your card exists in lspci"
my problem is that my broadcom wireless card does not exist in the output of lspci.
recently i upgraded to 9.04 jaunty. the wireless again came up.
the card used to be in the output of lspci.
but after a shutdown, the wireless disappeared again.
now again i can not see wireless card in my lspci output.
i have tried everything including plugging out and plugging in the pci-e card.
please help in determining, what is wrong, why does lspci does not show broadcom wireless card.
after i have upgraded to 9.04 jaunty the output of "lsmod" shows b43 and ssb modules loaded.
but i dont know if these kernel modules are of any use/help, if the hardware is not detected.
can someone suggest some other pci tools through which i can see the state of my pci-e card.

---

### Post by superprash2003 on 2009-05-21
could you post your lshw -C network output

---

