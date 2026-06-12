---
title: "How to get the r8712u module for D-link DWA130"
date: 2011-05-15
forum: Networking &amp; Wireless
---

### Post by ShadowWraith on 2011-05-15
I tried out Backtrack 5 linux the other day, and to my  delight I discovered that it natively supports my D-Link DWA-130 card which until now I was forced to use ndiswrapper for.
I ran
```

dmesg | grep 'driver'

```
and found that the driver module in use was r8712u . How can I install this driver in Ubuntu 10.04?

---

### Post by chili555 on 2011-05-15
You can download it from Realtek and compile it. A search for 8712 on this forum will show several examples. Even better, you can upgrade to 11.04 where it's natively supported:> /lib/modules/2.6.38-8-generic/kernel/drivers/staging/rtl8712/r8712u.ko

---

### Post by ShadowWraith on 2011-05-15
I can't actually find anywhere to get the source for r8712u driver. When I search these forums as you suggested, I get only the su drivers, which are for the newer cards.

---

### Post by chili555 on 2011-05-15
I think it is on Realtek's site. It's this package: RTL8192CU_8188CUS_8188CE-VAU_linux_v2.0.1502.20110402. I can't get it to compile in Natty, but you are running 10.04 so you should be OK.

[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true)

---

### Post by ShadowWraith on 2011-05-15
Compiling that gives the driver version 8192cu.ko module, not r8712u.ko ?
Is  there something I'm missing?

---

### Post by chili555 on 2011-05-15
You are exactly right; pardon my error. You want the 8192SU package here:

[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true)

This one compiles like a champ!> LD [M]  /home/chili/Desktop/Forum/shadow/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/[COLOR="Red"]8712u[/COLOR].koSorry for the error.

---

### Post by ShadowWraith on 2011-05-16
Thank you for the info! I did indeed make 8712u.ko , but after running
```

make install

```
nothing has changed (DWA-130 still does nothing & is not detected without ndiswrapper). Is there some install configuration that should be done before I install it?

---

### Post by chili555 on 2011-05-16
> **ShadowWraith said:**
> Thank you for the info! I did indeed make 8712u.ko , but after running
```

make install

```
nothing has changed (DWA-130 still does nothing & is not detected without ndiswrapper). Is there some install configuration that should be done before I install it?You probably need to remove ndiswrapper so that you have no conflicts. Did you modprobe the module?```
sudo modprobe 8712u
iwconfig
```

---

### Post by ShadowWraith on 2011-05-16
Ah, thank you again! I forgot to use modprobe, I'd already removed ndiswrapper.

Works like a charm! It's great to be able to use my DWA-130 !

Thank you very much for your help!

---

