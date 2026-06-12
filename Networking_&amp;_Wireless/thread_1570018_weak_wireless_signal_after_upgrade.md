---
title: "weak wireless signal after upgrade"
date: 2010-09-07
forum: Networking &amp; Wireless
---

### Post by daigoro on 2010-09-07
Hi all!

After I upgraded from 8.10 (or 8.4, I'm not sure), the wireless signal is very weak:
```

~$ sudo iwconfig wlan0
wlan0     IEEE 802.11bg  ESSID:"mina"  
          Mode:Managed  Frequency:2.452 GHz  Access Point: 00:13:F7:93:42:B1   
          Bit Rate=1 Mb/s   Tx-Power=27 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=38/100  Signal level=38/100  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

I'm at lucid right now with the same problem. I think it's a kernel issue because I remember downgrading the kernel and it worked. 

It'a SMC 54Mb wireless pen. zd1211rw driver.

How can I resolve this?

---

### Post by daigoro on 2010-09-09
anyone?

---

