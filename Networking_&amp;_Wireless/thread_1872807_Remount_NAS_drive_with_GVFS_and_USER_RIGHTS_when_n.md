---
title: "Remount NAS drive with GVFS and USER RIGHTS when network re-connects?"
date: 2011-10-31
forum: Networking &amp; Wireless
---

### Post by deckoff on 2011-10-31
I use gvfs script to mount my SAMBA share when my system starts. I run it at autostart. Here is the script:

```
#!/bin/bash

sleep 4

   wifi="'$(/sbin/iwconfig eth1 | egrep ESSID | cut -d '"' -f 2)'"

      if [ $wifi = "'deckoff'" ]; then 

 gvfs-mount smb://192.168.1.106/public

      fi
end script
```
It works great, but when network is down I have to manually re-connect. I added the same script to ```
/etc/network/ifup.d
```, and as I expected, I am getting a warning

```
Could not change permissions for
/home/deckoff/MyBookLive/GVFS-mount
```
I suspect the reason is that the script that re-mounts at reconnect is run as sudo. So, ideally, I want a solution that runs the script every time network is connected as user. I will be happy if I get rid if the warning at the very least.

---

