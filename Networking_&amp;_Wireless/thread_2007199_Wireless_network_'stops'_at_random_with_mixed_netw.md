---
title: "Wireless network 'stops' at random with mixed network + WPA"
date: 2012-06-20
forum: Networking &amp; Wireless
---

### Post by Ranko Kohime on 2012-06-20
Just got upgraded to fiber last week, and the phone company installed an N-capable AP/router.

We have 3 computers on the wireless side of the network at present:

[LIST]
[*]Lenovo Thinkpad E420
[*]Acer Aspire 5733Z
[*]Asus EeePC 701SD
[/LIST]

The former two are N-capable, the latter is B/G.  The N-capable pair are running Ubuntu 12.04 x64, the EeePC is running 12.04 x32.  (Per necessity, it's a 32-bit processor)

What the problem is, the EeePC will connect to the network fine, but after a few minutes, it will lose it's connection.  Network Manager claims it's still connected, ifconfig reports an established connection with an IP address, but ALL pings to or from the local network fail.  Disconnecting and reconnecting returns the connectivity for a brief period, but it generally will fail again.

This will also happen, but less frequently, to the N-capable computers, but NEVER unless the EeePC is connected and has not yet lost it's connectivity.

This isn't signal interference.  I'm not experiencing *some* packet loss, (the N-capable pair can transfer files between each other at reasonable speeds of almost 3MBps), I'm experiencing 100% packet loss on the affected computer when this occurs.

Router claims to be a ZyXEL, model "VSG1432-B101".  I've tried limiting the AP to B/G, this does not help.

I get the problem with either WPA1 or WPA2.  Turning all encryption OFF seems to fix the problem, BUT, I don't want to do that.  WEP isn't really worth testing.

Any ideas?  Should I submit a bug report?

---

### Post by Ranko Kohime on 2012-06-23
Bump and update:

I have a much lower occurrence of the stoppage without encryption, but it does still stop occasionally.  However, without encryption, it's typically the N-capable pair that disconnect, the EeePC has been stable now for two days running.  This with N enabled, and the N-capable pair running at 72Mbps, and the EeePC running G at 54Mbps.

---

### Post by amireldor on 2012-07-24
I'm having exactly the same problem with my Asus N55SF.
I also read the other thread you posted on: [http://ubuntuforums.org/showthread.php?t=2005981&page=3](http://ubuntuforums.org/showthread.php?t=2005981&page=3)

```

$ lspci | grep -i network
03:00.0 Network controller: Intel Corporation Centrino Wireless-N 1030 (rev 34)

```The driver/module is `iwlwifi`.

I've tried with the following file I've created as someone on the net wrote somewhere, but the problem persists:
```

$ cat /etc/modprobe.d/wlan.conf 
options iwlwifi swcrypto=1
```

Have you solved your issue? And how?

---

