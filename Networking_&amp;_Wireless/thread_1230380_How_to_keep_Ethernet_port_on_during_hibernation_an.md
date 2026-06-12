---
title: "How to keep Ethernet port on during hibernation and soft off?"
date: 2009-08-03
forum: Networking &amp; Wireless
---

### Post by Gustavo Narea on 2009-08-03
Hello, everyone.

I'm setting up Wake-on-LAN on my home server and so far I've made it work with suspend (ACPI mode S3) only. I want to make it work with either hibernation (ACPI mode S4) or soft off (ACPI mode S5) in order to save more energy, but unfortunately the Ethernet port's LED is off during these modes, which means it's not active.

Below are the contents of /proc/acpi/wakeup, where *PCIE* represents my NIC according to `*lspci*':
```
Device  S-state   Status   Sysfs node
LID       S3    *enabled
PBTN      S4    *enabled
PCI0      S3     enabled   no-bus:pci0000:00
USB0      S0     disabled  pci:0000:00:1d.0
USB1      S0     disabled  pci:0000:00:1d.1
USB2      S0     disabled  pci:0000:00:1d.2
USB3      S0     disabled  pci:0000:00:1d.3
EHCI      S0     disabled  pci:0000:00:1d.7
AZAL      S3     disabled  pci:0000:00:1b.0
PCIE      S4     enabled   pci:0000:00:1e.0
RP01      S4     disabled  pci:0000:00:1c.0
RP02      S3     disabled
RP03      S3     disabled
RP04      S3     disabled  pci:0000:00:1c.3
RP05      S3     disabled
RP06      S3     disabled
```

How come the Ethernet port is supposedly enabled for S4, but is only on during S3?

Below are the commands I use to suspend, hibernate and shutdown, respectively:
[LIST]
[*]sudo pm-suspend
[*]sudo pm-hibernate
[*]sudo halt
[/LIST]

I've even modified */etc/default/acpi-support*, so my NIC driver (b44) is kept in the kernel during suspends and its interface (eth0) isn't stopped during suspends:
```
MODULES_WHITELIST="b44"
SKIP_INTERFACES="dummy qemu eth0"
```

But nothing changes.

What else can I do to keep the Ethernet port active during hibernation and/or soft off?

Thanks in advance.

---

### Post by Gustavo Narea on 2009-08-21
Anyone? :confused:

---

