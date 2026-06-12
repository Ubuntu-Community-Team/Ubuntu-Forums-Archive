---
title: "Cant set pci adapter"
date: 2012-12-31
forum: Networking &amp; Wireless
---

### Post by rain987 on 2012-12-31
Hi, a lightning strike and took both my router and internet card, so i replace both, now running on dfe-528tx.

I had no issue with windows, but i am not sure about the workaround on ubuntu(v12.04).

Currently stucked, tried searching (driver,ubuntu,dfe528tx)
Keying commands i got from google have left me dry.

ifconfig gave me 2 result,
eth0 ( my dead internet card) and lo 

lspci shows me my d-link

sudo lshw -c network shows that my eth0 is disable( i have disable this intentionally, this is the broken card)

while network :0 unclaimed for my dlink

This lead me to google for the driver to run on ubuntu, download a few but all failed to run.

Any pointers of keyword would do me greatly. thanks in advance.


Solve (post 7)

---

### Post by rain987 on 2013-01-01
Bump :fingers cross:

---

### Post by steeldriver on 2013-01-01
what does [FONT=Courier New]lspci -nn[/FONT] say is the PCI ID of the device (the number in square brackets [xxxx:xxxx] )

---

### Post by rain987 on 2013-01-01
> **steeldriver said:**
> what does [FONT=Courier New]lspci -nn[/FONT] say is the PCI ID of the device (the number in square brackets [xxxx:xxxx] )
02:00.0 Ethernet controller [0200]: D-Link System Inc RTL8139 Ethernet [1186:1300] (rev 10)
02:04.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)

Thank for answering.

ps:Kinda new to ubuntu, my dlink is not listed in both ifconfig and ifconfig -a.
But running system checking on network it detect both my dlink and realtek. Hope this info helps.

---

### Post by steeldriver on 2013-01-01
well a bit of googling suggests that 1186:1300 should be supported in recent kernels by module 8139too - does

```
lsmod | grep 8139too
```output anything? if not, what happens if you try

```
sudo modprobe -v 8139too
```

Also, HOW did you disable the old card? maybe THAT is what is preventing the dlink device driver from loading?

---

### Post by rain987 on 2013-01-01
lsmod | grep 8139too
8139too                23283  0 

what i did was ifdown i think.  it cause my Realtek to be disable, but my dlink still unclaimed.

edit : i have enable it back, but still no sign of dlink in ifconfig/ifconfig -a

---

### Post by rain987 on 2013-01-03
Hi, my problem  was solve, had to simply remove and reinsert( i insert into a different slot) the pci adapter and the problem was fix immediately.

thanks [steeldriver]("http://ubuntuforums.org/member.php?u=1627500") for replying and trying to help.

---

