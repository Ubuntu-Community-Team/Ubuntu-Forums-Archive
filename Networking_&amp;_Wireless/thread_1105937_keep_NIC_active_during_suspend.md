---
title: "keep NIC active during suspend"
date: 2009-03-25
forum: Networking &amp; Wireless
---

### Post by cmaz on 2009-03-25
Hi,

i am completely new to linux. i've got an old Dell optiplex 170l with dual boot windows xp and ubuntu 8.10. It has an onboard intel 10/100 ve network interface. It is wired to my linksys wrt54g router which also serves two other wireless computers on the network.

My problem is that i would like the other computers to be able to access the ubuntu machine while it is in suspend mode.

i have set the bios so that the network is capable of remote wake up, and it works under xp. But with ubuntu, when the machine suspends, both the green and orange diodes go out, so i'm assuming it is shutting down the network interface and that is why the other computers can't wake it up (even with magic packets--and that's another question, should i really *need* magic packets in this instance? The computer is not shut down, just asleep.)

i've tried editing my acpi-support file to add "e100" to the modules_whitelist, and added "eth0" to skip_interfaces

Any help at all in getting my network computers to access or otherwise wake this computer up from suspend would be greatly appreciated.

Thanks!

---

