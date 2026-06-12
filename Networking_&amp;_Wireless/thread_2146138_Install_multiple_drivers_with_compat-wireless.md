---
title: "Install multiple drivers with compat-wireless"
date: 2013-05-17
forum: Networking &amp; Wireless
---

### Post by psycovic23 on 2013-05-17
I'm running into a strange problem trying to install two drivers using the ./script/driver-select in compat-wireless. Installing one seems to undo everything. Here's my process:

./driver-select restore
./driver-select iwlwifi
make
sudo make install
<reboot>

[at this point wireless works]

./driver-select alx
make
sudo make install
<reboot>

[now nothing works and the modules are missing]

Any ideas? This is on 11.10

---

### Post by praseodym on 2013-05-17
You know that 11.10 is outdated? I recommend updating to 12.04. For iwlwifi there should be no need for updating, just disable the N-mode (Bug):
```

echo "options iwlwifi 11n_disable=1" | sudo tee /etc/modprobe.d/iwlwifi.conf
sudo modprobe -rfv iwlwifi
sudo modprobe -v iwlwifi
```
For 12.xx the alx driver can be installed with dkms according to this:
[http://forum.ubuntuusers.de/topic/lan-wlan-probleme-mit-lenovo-g580/2/#post-4987097](http://forum.ubuntuusers.de/topic/lan-wlan-probleme-mit-lenovo-g580/2/#post-4987097)

---

### Post by psycovic23 on 2013-05-18
Unfortunately I have to use 11.10 for legacy issues. Does that work for 11.10?

---

### Post by praseodym on 2013-05-19
Just try it. Alternatively, you can try an older version of linux-wireless or a mainline kernel

---

