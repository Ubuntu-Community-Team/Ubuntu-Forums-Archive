---
title: "wireless chip deleted from lspci output"
date: 2011-12-17
forum: Networking &amp; Wireless
---

### Post by jamesbon on 2011-12-17
3-4 days back on my Ubuntu 11.04 machine wirless suddenly stopped working.Googling forum etc showed STA driver was the cause of problem so as per this  link 
[http://ubuntuforums.org/archive/index.php/t-1732258.html](http://ubuntuforums.org/archive/index.php/t-1732258.html)
installed the b43 driver (blacklisting etc done)

 by issuing 
```
sudo apt-get purge firmware-b43*
sudo apt-get install firmware-b43-lpphy-installer
``` 
Things worked smooth after a reboot I was able to get wireless back.Today morning I see the wireless again not detected and 
lsmod does not shows any wireless driver module loaded,
lspci -vnn does not even shows the wireless chip which used to be present as
```
14e4:4315
```
What went wrong here? What could be done?
I had installed Oracle Virtualbox yesterday and it was using wlan0 for its networking as interface which used to be my wireless card.

---

