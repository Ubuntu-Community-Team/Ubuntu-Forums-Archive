---
title: "Trying to install RALINK driver: stuck on defconfig step"
date: 2008-12-24
forum: Networking &amp; Wireless
---

### Post by Pstevens on 2008-12-24
We're trying to get our EDIMAX / RALINK wireless adapter connected under Xubuntu 8.04.  We've downloaded the source files for the relevant driver and are trying to follow the instructions in the README.

We are stuck on the stage that tells us to edit defconfig.

Newbie question:

where is defconfig ?

Subsidiary question:

I'm aware of the command 'whereis' for finding executables; how would I search for a non-executable file such as 'defconfig'?

Thanks in advance for any help.

Richard and Jack Stevens

---

### Post by ibutho on 2008-12-24
The drivers for most ralink based cards are usually built into the kernel so there is no need to compile your own. Check the chipset of your card by running
```
sudo lspci | grep -i net
```
and 
```
sudo lshw -C network
```

---

### Post by ibutho on 2008-12-24
The drivers for most ralink based cards are usually built into the kernel so there is no need to compile your own. Check the chipset of your card by running
```
sudo lspci | grep -i net
```
and 
```
sudo lshw -C network
```

---

### Post by Pstevens on 2008-12-24
Thanks.  We used lsusb originally because this is a USB wireless card, and got
148f:2573

and identified it as an RALINK rt73 chipset, based on
[http://linux-wless.passys.nl/query_part.php?brandname=Edimax](http://linux-wless.passys.nl/query_part.php?brandname=Edimax)

How can I find out whether I need an additional driver or whether it is built into the kernel?

---

### Post by Pstevens on 2008-12-24
PS 
uname -r
tells me that we are running the kernel
2.6.24-22-generic

---

### Post by ibutho on 2008-12-24
You do not need an additional driver if you are using Ubuntu 8.04 and 8.10. The drivers are built into the kernel, so what you need to do is use the network config tools to setup the wireless connection.

---

### Post by Pstevens on 2008-12-24
We've done that, but keep getting prompted to re-enter the WEP key.  We've tried "Open system" mode and "Shared" mode, so we thought we'd go back to basics and verify we had the right driver ... for which, thanks for your help.

---

### Post by ugm6hr on 2008-12-24
> **Pstevens said:**
> We've done that, but keep getting prompted to re-enter the WEP key.  We've tried "Open system" mode and "Shared" mode, so we thought we'd go back to basics and verify we had the right driver ... for which, thanks for your help.

This will identify the driver:
```
lshw -class network
```

I had problems with a similar device.  I think it's actually Network Manager that is the problem.  Consider trying Wicd (v1.5.3) instead.

If that doesn't work, use the serialmonkey driver (which I used).

---

