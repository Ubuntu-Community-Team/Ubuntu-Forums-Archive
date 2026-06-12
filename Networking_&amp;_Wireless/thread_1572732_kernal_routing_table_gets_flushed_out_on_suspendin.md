---
title: "kernal routing table gets flushed out on suspending"
date: 2010-09-11
forum: Networking &amp; Wireless
---

### Post by monk11 on 2010-09-11
kernal routing table becomes empty once I suspend the system and restore it. Then, it can't connect to internet (obviously), even when I start-stop the network service (init.d/network start etc). 
It started to happen for the last 3-4 days(after I took an update). I usually suspend the system at night... it used to run for days without restart; but there is no way now to restore the internet without a restart. 

It is ubuntu 9.10 (can't upgrade to 10.x due to some unrelated issues) 

glimplse of the table: :)

netstat -r
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface

---

### Post by monk11 on 2010-09-13
using wicr these days as a substitute of network manager. but the problem is it is not that user-friendly while connecting to wireless services. lan is ok.

---

### Post by utilitytrack on 2010-09-13
> kernel routing table becomes empty once I suspend the system and restore it.

I don't see any problems here.

---

### Post by monk11 on 2010-09-13
yeah, it is a feature. but the problem was it remained empty after resuming it. So, in essence, to connect to the intenet, i need to restart the system (restarting the network services was not working either).

---

### Post by utilitytrack on 2010-09-13
1) Explain in detail what you doing and how you connect to internet.
2) On that time I can give advice manually turn off all interfaces before suspend; and after resume, manually turn on it again. This will help us to understand what is the problem.
And don't forget post here output of [FONT="Courier New"]$ route -n[/FONT] before and after all of this.

---

