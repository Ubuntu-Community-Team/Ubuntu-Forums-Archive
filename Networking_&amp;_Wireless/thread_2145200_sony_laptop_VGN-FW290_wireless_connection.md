---
title: "sony laptop VGN-FW290 wireless connection"
date: 2013-05-14
forum: Networking &amp; Wireless
---

### Post by mattew2010 on 2013-05-14
This laptop has no wireless connection problem under windows vista. 

If under ubuntu, the wireless network can work for a while, but constantly drop the wireless connection after a while :(

I have used the command like:  *modprobe -r iwlagn  and **modprobe iwlagn* when the connection drops. The connection can be restored for a while, then drops happen again. 

any solution to this ?

Thanks,

---

### Post by praseodym on 2013-05-14
Hi,

deactivate the N-mode of the driver iwlagn permanently (bug):
```

echo "options iwlwifi 11n_disable=1" | sudo tee /etc/modprobe.d/iwlwifi.conf
sudo modprobe -rfv iwlwifi
sudo modprobe -v iwlwifi
```

---

