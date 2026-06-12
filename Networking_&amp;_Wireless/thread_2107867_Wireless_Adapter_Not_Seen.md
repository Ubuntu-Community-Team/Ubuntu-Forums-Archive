---
title: "Wireless Adapter Not Seen"
date: 2013-01-22
forum: Networking &amp; Wireless
---

### Post by mattdt on 2013-01-22
My 10.04 system won't recognize my LM Technologies LM006 Wireless Adapter.

Terminal gives me:

$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

And:

$ rfkill list all
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

Not sure what to do to get my system to see this adapter. BTW: It does work and on booted in Win XP on the same box.

Thanks.](*,)

---

### Post by ahallubuntu on 2013-01-23
It uses the Realtek RTL8188SU/8192CU chipset.  Try getting and building the driver from Realtek's website for RTL8192CU .  Follow these instructions (but you can skip the blacklisting, as 10.04 loads no other driver for it):

[http://ubuntuforums.org/showthread.php?t=2076315](http://ubuntuforums.org/showthread.php?t=2076315)

---

