---
title: "Jaunty and ar5007eg"
date: 2009-07-05
forum: Networking &amp; Wireless
---

### Post by thegodfaza on 2009-07-05
I assume that this problem has to do with my wireless adapter since this is the first version of ubuntu that natively supports it. I'm running an up to date 9.04 on a Toshiba Satellite A215-S5818 with the latest BIOS. When I use ethernet, my connection speeds are fine. Internet browsing is fine. Etc... But when I use the wireless card ( Built in ar5007eg ) my speeds plummet. I did a speedtest.net test. Using ethernet I have 1.5Mb down, .5 up with a ping of 80. Using wifi it took 5 minutes but I got .5 down, .11 up with a ping of 209. Also the download / upload would go about 10% - 20% at a time then stop. Then after a few seconds it would do it again until it was done.

LSPCI: Because I know someone will ask for it.
```
0e:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
```

I've tried the disabled hardware driver, linux-backports-modules-jaunty, and madwifi. All with the same results. I'm also running Windows 7 on the same machine with no issues.

---

### Post by thegodfaza on 2009-07-05
Never mind. I woke up this morning and tried the wireless again and it works perfectly. Not sure why though.

---

