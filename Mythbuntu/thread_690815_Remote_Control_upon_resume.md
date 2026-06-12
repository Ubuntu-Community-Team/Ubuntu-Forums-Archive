---
title: "Remote Control upon resume"
date: 2008-02-07
forum: Mythbuntu
---

### Post by yankcrime on 2008-02-07
I have two problems with my remote/lirc setup for a mythtv built on ubuntu gutsy.  I will try to keep them seperate.
The first problem is that upon I can not wake my box out of suspend (or hibernate for that matter) with the remote (mceusb2).  I believe that is because the S-state of my my /proc/acpi/wakeup file is a bit weird.  It looks as follows:
```

bedfordr@myth-masterbed:~/suspend-0.8$ cat /proc/acpi/wakeup 
Device  S-state   Status   Sysfs node
P0P2      S4     disabled  pci:0000:00:01.0
P0P1      S4     disabled  pci:0000:00:1e.0
UAR1      S4     disabled  pnp:00:06
PS2K      S4     disabled  pnp:00:0d
PS2M      S4     disabled  pnp:00:0e
EUSB      S4     disabled  pci:0000:00:1d.7
USBE      S4     disabled  pci:0000:00:1a.7
P0P5      S4     disabled  
P0P6      S4     disabled  
P0P7      S4     disabled  
P0P8      S4     disabled  pci:0000:00:1c.4
P0P9      S4     disabled  pci:0000:00:1c.5
USB0      S4     enabled   pci:0000:00:1d.0
USB1      S4     disabled  pci:0000:00:1d.1
USB2      S4     disabled  pci:0000:00:1d.2
USB3      S4     disabled  
USB4      S4     disabled  pci:0000:00:1a.0
USB5      S4     disabled  pci:0000:00:1a.1
P0P4      S4     disabled  pci:0000:00:1c.0

```

I believe the S-state should be S3 (suspend to ram), but I don't know how to change that (other than a text file) and even if I change the text file, a restart of the acpid daemon sets it back to S4.  I am enabling the USB0 using the standard
```
echo USB0>/proc/acpi/wakeup
``` in my /etc/rc.local file.  I am using s2ram for sleeping.

---

