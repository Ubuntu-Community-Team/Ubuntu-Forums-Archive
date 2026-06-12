---
title: "Cannot hibernate because wifi is on"
date: 2009-05-30
forum: Networking &amp; Wireless
---

### Post by afeasfaerw23231233 on 2009-05-30
I have newly installed Ubuntu 9.04 on my notebook. It cannot hibernate/suspend if the wireless is on, but it can if the wireless is shut off manually before clicking the hibernate button. Any idea?

EDIT: the wireless chip is realtek 8187L (internal usb)
```

lsusb
Bus 001 Device 006: ID 0bda:8187 Realtek Semiconductor Corp. RTL8187 Wireless Adapter

```

The screen just goes blank with the flashing prompt cursor ( _ ) and freezes. Can do nothing beside pressing the power button for 2 seconds and shut it off.

Thanks in advance!

---

### Post by afeasfaerw23231233 on 2009-06-01
bumpbo

---

### Post by afeasfaerw23231233 on 2009-06-03
bump

---

### Post by afeasfaerw23231233 on 2009-06-04
Bump

---

### Post by afeasfaerw23231233 on 2009-06-05
No one has this problem?

---

### Post by afeasfaerw23231233 on 2009-06-08
bump

---

### Post by utnubu(k) on 2009-06-08
> **afeasfaerw23231233 said:**
> No one has this problem?
got the same problem with jaunty ubuntun and it bugs me, too.
> lsusb
Bus 001 Device 004: ID 0bda:8187 Realtek Semiconductor Corp. RTL8187 Wireless Adapter

it's an external wifi in my case.
Any help ?

---

### Post by afeasfaerw23231233 on 2009-06-08
Your chip is RealTek 8187 too. Would it be the cause of the problem?

---

### Post by utnubu(k) on 2009-06-12
I guess so, because the problem doesn't occur when doing hibernation with my internal intel wifi.
the driver for the rtl8187 seems incomplete, as the the strength of the wifi signal is almost the same for every network in my environment. even for my wifi router 2 meters next to me it' doesn't show a strong signal.

---

### Post by afeasfaerw23231233 on 2009-06-13
You are right. The auto-negotiation of bit rate seems not working. The bit rate always stays at 54mb/s even though the signal is very weak. 
```

wlan0     IEEE 802.11bg  ESSID:"router"  
          Mode:Managed  Frequency:2.457 GHz  Access Point: 00:23:5B:43:12:11   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=55/100  Signal level:40/65 

```

And in this case I have to fix the rate manually by this command or the connection will drop 
```
sudo ifconfig wlan0 rate fixed []M 
``` ([]M indicated the bit rate, such as 1M, 2M, 11M, etc)

Need to switch off the wifi manually everytime before hibernation. Huh!

---

### Post by kerry_s on 2009-06-13
the fix is to suspend the driver for the wifi.

**gksudo gedit /etc/pm/config.d/config**

```
SUSPEND_MODULES="usbcore your-wireless-driver"
```

save it and you should be good

i take out the usb, cause thats always the cause of problems, but you may not need that.
if you don't know what your wifi driver is you can look at "lsmod" in a terminal.

here's what mine looks like.

---

### Post by afeasfaerw23231233 on 2009-06-13
I have followed your steps but it still cannot hibernate. 
Here's my lsmod
```

 lsmod
Module                  Size  Used by
arc4                    9856  2 
ecb                    10752  2 
rtl8187                53376  0 
mac80211              217208  1 rtl8187
eeprom_93cx6           10240  1 rtl8187
cfg80211               38032  2 rtl8187,mac80211
usbhid                 42336  0 


```

---

### Post by kerry_s on 2009-06-13
> **afeasfaerw23231233 said:**
> I have followed your steps but it still cannot hibernate. 
Here's my lsmod
```

 lsmod
Module                  Size  Used by
arc4                    9856  2 
ecb                    10752  2 
rtl8187                53376  0 
mac80211              217208  1 rtl8187
eeprom_93cx6           10240  1 rtl8187
cfg80211               38032  2 rtl8187,mac80211
usbhid                 42336  0 


```

so you put:
SUSPEND_MODULES="usbcore rtl8187"
in the config file?
have you checked your /var/log/pm-hibernate.log

---

### Post by afeasfaerw23231233 on 2009-06-15
Sorry for my oversight. Now it works! Thank you!

---

### Post by afeasfaerw23231233 on 2009-06-15
Oh, no. It doesn't work again. It just hangs and the screen becomes black.

---

### Post by afeasfaerw23231233 on 2009-06-15
I can't find the /var/log/pm-hibernate.log file. But there are pm-powersave.log and pm-suspend.log 

pm-suspend.log is empty 

pm-powersave.log
```

/usr/lib/pm-utils/power.d/anacron false: success.
/usr/lib/pm-utils/power.d/laptop-mode false: success.
/usr/lib/pm-utils/power.d/sched-powersave false: **sched policy powersave OFF
success.

```
What to do to fix this problem? Thanks!

---

### Post by afeasfaerw23231233 on 2009-06-17
That's strange. After I removed the file and created it again, it worked. 
Thanks for help!

---

