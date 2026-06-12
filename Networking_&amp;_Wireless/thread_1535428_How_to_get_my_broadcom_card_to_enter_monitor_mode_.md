---
title: "How to get my broadcom card to enter monitor mode with aircrack-ng suite"
date: 2010-07-20
forum: Networking &amp; Wireless
---

### Post by sqvelasquez on 2010-07-20
I am running Lucid Lynx, kernel 2.6.32.23 generic, I have a card with the Broadcom BCM4311, with the STA Linux Wireless driver. I have no idea how to get monitor mode to work with the Aircrack-ng suite's Airmon-ng command. I use the command:
sudo airmon-ng start eth1

And I get this output:
Found 5 processes that could cause trouble.
If airodump-ng, aireplay-ng or airtun-ng stops working after
a short period of time, you may want to kill (some of) them!

PID    Name
883    NetworkManager
893    avahi-daemon
896    avahi-daemon
931    wpa_supplicant
1533    dhclient
Process with PID 1533 (dhclient) is running on interface eth1


Interface    Chipset        Driver

eth1        Unknown         wl (monitor mode enabled)

and the i run:
sudo airodump-ng eth1

and I get this:
ioctl(SIOCSIWMODE) failed: Invalid argument

ARP linktype is set to 1 (Ethernet) - expected ARPHRD_IEEE80211,
ARPHRD_IEEE80211_FULL or ARPHRD_IEEE80211_PRISM instead.  Make
sure RFMON is enabled: run 'airmon-ng start eth1 <#>'
Sysfs injection support was not found either.


Can anyone help me? I'm sorry I'm a Linux noob

---

### Post by pytheas22 on 2010-07-20
The airmon-ng script usually creates a new virtual interface in monitor mode, leaving the original interface as it is.  In other words, your monitor-mode interface is probably named mon0, not eth1, so after running "sudo airmon-ng start eth1", try:
```

sudo airodump-ng mon0
```

If it says interface mon0 doesn't exist, run "iwconfig" to see what does exist.  Let me know if you have trouble.

I'm also not entirely positively that your driver supports monitor mode, but I guess the airmon-ng script thinks it does, so it's worth a try.

---

### Post by sqvelasquez on 2010-07-20
Yeah the STA driver doesnt support it but i used b43-fwcutter and and now airmon-ng can use it but i still cant get it. Im so confused

---

### Post by pytheas22 on 2010-07-21
What exactly can you still not get?  Are you sure the b43 driver is the one that's actually activated, and not the STA driver (which is called 'wl')?  You can have both drivers installed at the same time but only one can be driving the card.  To switch to b43, type:
```

sudo rmmod wl
sudo rmmod b43
sudo rmmod ssb
sudo modprobe b43
```

---

### Post by sqvelasquez on 2010-07-21
> **pytheas22 said:**
> What exactly can you still not get?  Are you sure the b43 driver is the one that's actually activated, and not the STA driver (which is called 'wl')?  You can have both drivers installed at the same time but only one can be driving the card.  To switch to b43, type:
```

sudo rmmod wl
sudo rmmod b43
sudo rmmod ssb
sudo modprobe b43
```



OMG it works!!!!!! thanks pytheas!!!

---

