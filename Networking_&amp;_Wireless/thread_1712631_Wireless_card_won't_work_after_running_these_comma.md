---
title: "Wireless card won't work after running these commands..."
date: 2011-03-23
forum: Networking &amp; Wireless
---

### Post by ingramproductions on 2011-03-23
I'm running Ubuntu 10.10. From this link, [http://www.sumardi.net/2011/01/10/aircrack-fixed-channel-mon0-1/]("http://www.sumardi.net/2011/01/10/aircrack-fixed-channel-mon0-1/"), I ran the following commands:
```
sudo apt-get install linux-headers-$(uname -r)
wget http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-2010-12-20.tar.bz2
tar -jxf compat-wireless-2010-12-20.tar.bz2
cd compat-wireless-2010-12-20
wget http://patches.aircrack-ng.org/channel-negative-one-maxim.patch
sudo apt-get install patch
patch ./net/wireless/chan.c channel-negative-one-maxim.patch
make
sudo make install
sudo make unload
sudo reboot
```

Now when I run ifconfig, my wireless adapter is not listed, so I can't connect to any wireless network.

Does anybody know how to reverse this, or at least help me to get my wireless adapter working again?

---

### Post by wojox on 2011-03-23
Usually go back into the directory and 

```
sudo make uninstall
```

---

### Post by ingramproductions on 2011-03-23
That worked, Thanks

---

