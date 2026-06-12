---
title: "ifup for wireless network in /etc/network/interfaces"
date: 2010-02-02
forum: Networking &amp; Wireless
---

### Post by misha680 on 2010-02-02
Dear All:

I am trying to use ifup for a wireless network to run a script when the network connects.

Here is my /etc/network/interfaces
```

auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet dhcp
wireless-essid attwifi
ifup /home/misha/attwifi-ifup.sh

```

And the script /home/misha/attwifi-ifup.sh
```

#!/usr/bin/env twill-sh
sleep 15
go http://www.bcm.edu
find AT&T
fv 2 username username
fv 2 roamRealm sbcglobal.net
fv 2 password password
fv 2 aupAgree 1
submit

```

Network itself connects fine.

Any idea what I might be doing wrong (script works fine by self too).

Thank you!

Misha

---

