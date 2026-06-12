---
title: "Getting Atheros wireless to work after upgrade"
date: 2010-11-16
forum: Networking &amp; Wireless
---

### Post by pokeyThePenguin on 2010-11-16
I upgraded from 10.04 to 10.10 tonight, which broke my wireless functionality. I had always been using madwifi drivers.

Apparently every time you upgrade your kernel version, you need to reinstall the madwifi driver. I tried doing this:

```

wget http://snapshots.madwifi-project.org/madwifi-0.9.4-current.tar.gz
tar -zxvf madwifi-0.9.4-current.tar.gz
cd madwifi-0.9.4-r4133-20100922/
sudo make
sudo make install

```

But that didn't seem to do anything. I checked out System->Administration->Additional Drivers. Madwifi was an option. I tried to activate it, but Ubuntu complained. I started researching for other solutions.

I read that Atheros wireless support is pretty good in Ubuntu now via ath5k. I didn't need to install or download anything. I just immediately ran:

```

sudo modprobe ath5k

```

And then a wireless connection established. Then I edited /etc/modules so that ath5k will automatically load on startup (just add "ath5k" on a line by itself):

```

sudo gedit /etc/modules

```

Cheers!

---

