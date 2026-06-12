---
title: "how to see recorded files on iphone in Ubuntu 24.04?"
date: 2024-09-19
forum: Multimedia Software
---

### Post by shantiq on 2024-09-19
This is an update of an earlier post for 24.04




&#10122;
```
sudo apt install ideviceinstaller  libimobiledevice-utils python3-plist usbmuxd libimobiledevice6 libplist3 ifus



```

then plug iphone should be visible


Only if problems:


&#10123;


```
sudo usbmuxd --verbose -f
```    if VLC iphone does not show (if installed from App Store)


&#10124; sometimes on new installs or in my case when I upgraded from earlier to latter version of Distro it does not see the iphone if you unplug and replug during a session


If you are in a similar situation run:




```
 systemctl start usbmuxd

```

also at times may need to do ```
idevicepair unpair &&  idevicepair pair
``` 


NB: your iphone will ask you if communicating with your PC is ok

---

