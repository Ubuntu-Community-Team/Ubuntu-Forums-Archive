---
title: "Onboard Wireless [Part 2]"
date: 2011-06-22
forum: Networking &amp; Wireless
---

### Post by Lucradia on 2011-06-22
In continuation of this thread: [http://ubuntuforums.org/showthread.php?t=1765155](http://ubuntuforums.org/showthread.php?t=1765155)

My wireless can now detect the public library network, after disabling the extra ralink drivers, but it cannot obtain the IP Address, ever, it can put the connection (if) up and down, but the network won't give me an IP Address.

Thankfully, I thought about something: What about Fedora? What does it do when I try to use my onboard wireless adapter?

So, I installed fedora using unetbootin, and guess what, my wireless can obtain an IP Address from the public library where Ubuntu couldn't. The drivers that fedora uses are as follows:

from the first reply, here's the output of **lsmod | grep -e rt2 -e rt3**
```
rt2800pci               6905  0 
rt2800lib              28798  1 rt2800pci
crc_ccitt               1253  1 rt2800lib
rt2x00pci               4635  1 rt2800pci
rt2x00lib              35935  3 rt2800pci,rt2800lib,rt2x00pci
mac80211              201962  3 rt2800lib,rt2x00pci,rt2x00lib
cfg80211              116037  2 rt2x00lib,mac80211
eeprom_93cx6            1255  1 rt2800pci
```

Compared to ubuntu:
```
rt2870sta             410104  0 
rt2860sta             494649  0 
rt2800usb              17907  0 
rt2800pci              18159  0 
rt2800lib              43824  2 rt2800usb,rt2800pci
crc_ccitt              12595  3 rt2870sta,rt2860sta,rt2800lib
rt2x00pci              13986  1 rt2800pci
rt2x00usb              19693  1 rt2800usb
rt2x00lib              39075  5 rt2800usb,rt2800pci,rt2800lib,rt2x00pci,rt2x00usb
mac80211              257001  4 rt2800lib,rt2x00pci,rt2x00usb,rt2x00lib
cfg80211              156212  2 rt2x00lib,mac80211
eeprom_93cx6           12653  1 rt2800pci
```

Ignore usb entries in ubuntu, as my d-link adapter was ralink as well. So, can someone figure out what I must do to get ubuntu working, in case I ever want to go back? Fedora works fine, but not ubuntu. As I said, Fedora can **obtain the IP Address of the library, _but not ubuntu_**. Yes, I tried wicd AND gnome network manager, both cannot obtain the IP Address in Ubuntu. (Fedora uses gnome's network manager. I use LXDE Spin.)

---

