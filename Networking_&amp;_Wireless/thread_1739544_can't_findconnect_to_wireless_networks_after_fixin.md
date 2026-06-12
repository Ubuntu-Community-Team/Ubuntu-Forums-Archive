---
title: "can't find/connect to wireless networks after fixing boot failure (initramfs)"
date: 2011-04-26
forum: Networking &amp; Wireless
---

### Post by aravenscroft on 2011-04-26
so a few days ago, i turned on my laptop, running 10.04, and rather than seeing the usual login screen, i was informed that there was some kind of problem with the disk (forgive this vagueness, it was late and i didn't write anything down). when i rebooted, i only could get to a initramfs prompt. after much googling i found that other people had the problem and i needed to use e2fsck (with options cyv, i think) from a livecd. i tried to boot 10.04 from a usb stick (wouldn't work), then burned a 10.10 livecd (i could get in but e2fsck wouldn't work) and finally burned a 9.10 livecd (which seemed to work perfectly and allow me to get into ubuntu). i would provide some of the articles and threads that i followed but i'm struggling to find them and i'm not on the same computer so no search history.

so now, i can get into ubuntu fine and everything seems to be as it was. however, sometimes networks appear and sometimes they don't. and when they do, i can't connect. i've also tried connecting via terminal and still no luck. anyone have any suggestions? cheers.

---

### Post by aravenscroft on 2011-04-27
bump.

any ideas?

---

### Post by aravenscroft on 2011-04-28
another bump. still not working. i have now confirmed that ethernet is fine though.

---

### Post by josephmills on 2011-04-28
```
lspci -nn 
```
please

---

### Post by aravenscroft on 2011-04-28
```
00:00.0 Host bridge [0600]: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub [8086:2a40] (rev 07)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller [8086:2a42] (rev 07)
00:02.1 Display controller [0380]: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller [8086:2a43] (rev 07)
00:1a.0 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 [8086:2937] (rev 03)
00:1a.1 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 [8086:2938] (rev 03)
00:1a.2 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 [8086:2939] (rev 03)
00:1a.7 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 [8086:293c] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801I (ICH9 Family) HD Audio Controller [8086:293e] (rev 03)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 [8086:2940] (rev 03)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 [8086:2942] (rev 03)
00:1c.4 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 [8086:2948] (rev 03)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 [8086:2934] (rev 03)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 [8086:2935] (rev 03)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 [8086:2936] (rev 03)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 [8086:293a] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev 93)
00:1f.0 ISA bridge [0601]: Intel Corporation ICH9M-E LPC Interface Controller [8086:2917] (rev 03)
00:1f.2 SATA controller [0106]: Intel Corporation ICH9M/M-E SATA AHCI Controller [8086:2929] (rev 03)
00:1f.3 SMBus [0c05]: Intel Corporation 82801I (ICH9 Family) SMBus Controller [8086:2930] (rev 03)
02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. Device [10ec:8172] (rev 10)
06:00.0 System peripheral [0880]: JMicron Technology Corp. SD/MMC Host Controller [197b:2382] (rev 80)
06:00.2 SD Host controller [0805]: JMicron Technology Corp. Standard SD Host Controller [197b:2381] (rev 80)
06:00.3 System peripheral [0880]: JMicron Technology Corp. MS Host Controller [197b:2383] (rev 80)
06:00.5 Ethernet controller [0200]: JMicron Technology Corp. JMC250 PCI Express Gigabit Ethernet Controller [197b:0250] (rev 03)

```

---

