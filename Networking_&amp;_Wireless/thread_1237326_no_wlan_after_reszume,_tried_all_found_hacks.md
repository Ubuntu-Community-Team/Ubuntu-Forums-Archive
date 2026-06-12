---
title: "no wlan after reszume, tried all found hacks"
date: 2009-08-11
forum: Networking &amp; Wireless
---

### Post by garibaldino on 2009-08-11
hello,

After resuming i have to restart manually my network using 
/etc/init.d/networking restart

I tried to add a file in /etc/acpi/resume.d/99-networking.sh so that
```
#!/bin/bash
/etc/init.d/networking restart
```

tried in same stuff in /etc/inid.d/rc.local 

but no working network either

dmesg 
```
[19546.600330] ADDRCONF(NETDEV_UP): wlan0: link is not ready                              
[19548.440518] wlan0: authenticate with AP 00:23:f8:1d:7c:de                              
[19548.442109] wlan0: authenticated                                                       
[19548.442113] wlan0: associate with AP 00:23:f8:1d:7c:de                                 
[19548.445671] wlan0: RX AssocResp from 00:23:f8:1d:7c:de (capab=0xc31 status=0 aid=1)    
[19548.445673] wlan0: associated                                                          
[19548.446071] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready                         
[19549.386282] wlan0: duplicate address detected!                                         
[COLOR="Red"][19568.520037] wlan0: No ProbeResp from current AP 00:23:f8:1d:7c:de - assume out of range[/COLOR]

```

so considering the No ProbeResp I tried to add a sleep before the restart, but problem remains

any idea?

thanks

---

### Post by kerry_s on 2009-08-11
sounds like you need to suspend your wireless driver.

**gksudo gedit /etc/pm/config.d/config**

```
SUSPEND_MODULES="your-drivers"
```

use "lsmod" to see the wireless driver parts you want to suspend.

for example: my wireless uses b43, but there are other parts that work with it, so i suspend them all.

---

