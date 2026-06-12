---
title: "Networked - no internet"
date: 2010-07-10
forum: Networking &amp; Wireless
---

### Post by vicbee on 2010-07-10
Instead a creating a new post I'll follow up on the same thread since I have the same problem.

I have a wireless network with 3 pc, a printer and soon an external hd.  Both pc have an MS OS.  I've just installed Ubuntu 10.4 on a laptop along side Vista to see if I could jump in the linux world without too much difficulties...

Well, OS installed fine but Firefox cannot find internet connection.  I manually pointed to the network which is recognized and working but I still have no internet connection.  I unchecked "Working Offline" and the WEP key is correct so at this point I'm not sure what else to do.

Any suggestions?  Not a good start...

---

### Post by Iowan on 2010-07-10
Moved to new thread so we can concentrate on *your* issues.
Original thread is [here]("http://ubuntuforums.org/showthread.php?t=1528236").
So... local network is working?
Can you ping internet by name (google.com) or IP address (74.125.95.103)?

---

### Post by capscrew on 2010-07-10
> **Iowan said:**
> Moved to new thread so we can concentrate on *your* issues.
Original thread is [here]("http://ubuntuforums.org/showthread.php?t=1528236").
So... local network is working?
Can you ping internet by name (google.com) or IP address (74.125.95.103)?

I'll chime in here.  What we are really talking about is network connectivity.  Here is what I do when I have a problem.  

From the command line:
```
1. ping 127.0.0.1 (this checks if the IP stack is functioning)
2. Ping <The IP address of the host you are at> (this checks that that the NIC is working)
3. ping the gateway (this checks the LAN connectivity and gateway)
4. Ping an outside IP address (72.247.90.135 (whitehouse.gov) -- this checks the 
  functionality of the gateway device)
5. Ping FQDN of a known up location -- whitehouse.gov (this checks that DNS is working
   (along with everything else))
5a. If you want to check if local DNS is functioning ping a
   host on the LAN by name.  

```

With this set of logical steps you should be able to pinpoint where the problem is.

---

