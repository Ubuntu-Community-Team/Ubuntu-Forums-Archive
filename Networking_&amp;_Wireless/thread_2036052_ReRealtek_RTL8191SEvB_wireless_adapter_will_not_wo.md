---
title: "Re:Realtek RTL8191SEvB wireless adapter will not work"
date: 2012-07-31
forum: Networking &amp; Wireless
---

### Post by hantms on 2012-07-31
> **mesilikas said:**
> I have exactly the same problem with the same wireless card (RTL 8191 SEvB) in Thinkpad Edge 13 and installed Ubuntu 10.10 64b will be great pleasure if it can work with wireless internet :(

Still having the same problem.  Had it with my last Thinkpad too; frankly I'm giving up; Ubuntu just doesn't seem fully compatible with my hardware. (Lenovo T410i)

I went to the Realtek website but the driver needs compiling and doing so gives me errors.. this is just way over my head; moving back to Windows 7 makes a lot more sense.

---

### Post by wildmanne39 on 2012-08-01
*Thread moved to **Networking & Wireless**.*

Please post the output of:
```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
lsusb
iwconfig
rfkill list all
lsmod
```
by clicking on new reply and click # then paste the information between the brackets.
Thank you

---

