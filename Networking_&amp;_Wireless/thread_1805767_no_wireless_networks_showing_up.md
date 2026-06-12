---
title: "no wireless networks showing up"
date: 2011-07-16
forum: Networking &amp; Wireless
---

### Post by milos.ilic on 2011-07-16
Hello,
I have installed Ubunu 10.04, and after that i have installed the wireless driver from Hardware Drivers.
The problem is that no wireless networks are showing up and i cannot connect to my wireless router. Tried rebooting, but still nothing.
Thanks in advance.
Milos

---

### Post by wildmanne39 on 2011-07-16
Hi, please run these commands in a terminal
one at a time.
```
sudo lshw -C network
``` 
```
lspci -nn
```
```
lsmod
```
```
rfkill list All
```
and post the outcome  here by clicking on new reply and click # and paste the information between the brackets.

---

### Post by garvinrick4 on 2011-07-16
@wildmanne39
Have you used this script? Is kind of nice up to version 2.1 now.

[Wireless Script 1.0 - Browse Files at SourceForge.net]("http://sourceforge.net/projects/wirelessscript/files/")

---

### Post by wildmanne39 on 2011-07-17
> **garvinrick4 said:**
> @wildmanne39
Have you used this script? Is kind of nice up to version 2.1 now.

[Wireless Script 1.0 - Browse Files at SourceForge.net]("http://sourceforge.net/projects/wirelessscript/files/")Hi, no I have not tried that script before it looks like a nice one to have. Thank you for showing me the link I appreciate it very much.

---

