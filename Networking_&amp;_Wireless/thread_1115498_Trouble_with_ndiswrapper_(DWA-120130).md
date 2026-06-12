---
title: "Trouble with ndiswrapper (DWA-120/130)"
date: 2009-04-03
forum: Networking &amp; Wireless
---

### Post by thinhhoang on 2009-04-03
Good day everyone! I've recently switched to Kubuntu 9.04B.
I've installed ndiswrapper and the DWA-120 driver (D-Link) (DWA-130 is the same) successfully. These are the steps I've followed.

1. Install ndiswrapper.
2. Install ndiswrapper-utils.
3. ndiswrapper -i AGUx86.inf.
4. ndiswrapper -m.
5. ndiswrapper -l.

Everything seems fine, but when I ran iwlist -scanning, I couldn't find wlan0. Please help me! Thank you!

---

### Post by oobe-feisty on 2009-04-03
check if it was created
dmesg | grep wlan

if it was activate it 

ifconfig wlan0 up

if it wasnt check /var/log/syslog and dmesg for errors

---

### Post by thinhhoang on 2009-04-04
Thanks for your reply. I've tried but I didn't work. When I checked the syslog, I found out the Ndiswrapper couldn't prepare the AGUx86, which is the driver of DWA-120. What should I do now?

---

### Post by oobe-feisty on 2009-04-05
you will have to look for different driver versions for you tuner im not sure but it may even be supported under linux would mean there is no need to use ndiswrapper try googling the results of this "lspci | grep Network" or "lsusb -v | grep Network"


> **thinhhoang said:**
> Thanks for your reply. I've tried but I didn't work. When I checked the syslog, I found out the Ndiswrapper couldn't prepare the AGUx86, which is the driver of DWA-120. What should I do now?

---

