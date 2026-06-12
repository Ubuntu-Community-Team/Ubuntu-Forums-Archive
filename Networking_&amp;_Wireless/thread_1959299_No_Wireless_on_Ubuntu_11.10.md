---
title: "No Wireless on Ubuntu 11.10"
date: 2012-04-15
forum: Networking &amp; Wireless
---

### Post by Utnubu42 on 2012-04-15
I have an ASUS U56E laptop with an Intel Centrino Wireless-n 6150 chip.

Ever since I updated to Ubuntu 11.10, I have been unable to connect to any wireless network. In the network manager tab, I see all of the wireless networks nearby, but whenever I try to connect to one, it appears to keep loading without ever connecting. Password-protected networks ask for the password every 30 seconds without connecting.
Wired connections work fine.

The output of iwconfig is:
```

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"Wireless network to which I am trying to connect"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on

```I was previously able to avoid this problem by booting the 2.6.38 Linux kernel instead of the latest kernel (indicating it is a problem with the kernel?) However, with new updates, the old kernel fails to load Unity and thus is unusable. 

How can this problem be resolved? Thanks.

---

### Post by Stretchkev1 on 2012-04-15
This thread [http://ubuntuforums.org/showthread.php?t=1862484&page=8](http://ubuntuforums.org/showthread.php?t=1862484&page=8) seems to have a solution to the problem. 

In the course of trying the above solution I've managed to kill my wlan0 so I don't if this works or not. So this probably isn't the most helpful.

---

### Post by Utnubu42 on 2012-04-15
Thanks, Stretchkev1! I now have wireless working perfectly.

---

