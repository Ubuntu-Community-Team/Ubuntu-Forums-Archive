---
title: "nfs hang on shutdown"
date: 2009-07-15
forum: Networking &amp; Wireless
---

### Post by renkinjutsu on 2009-07-15
i have some NFS exports on my desktop and the nfs-kernel-server always causes my computer to hang during shutdown (even after i unmount everything and stop the service) .. it either hangs on "unexporting directories" or "flushing server cache"

so i followed the documentation here
[https://help.ubuntu.com/community/SettingUpNFSHowTo]("https://help.ubuntu.com/community/SettingUpNFSHowTo")
and did this ```
sudo update-rc.d -f setkey remove
sudo update-rc.d setkey start 37 0 6 S .
```

i pasted that into the terminal and unfortunately, the output is ```
update-rc.d: /etc/init.d/setkey: file does not exist
```

i then did a `sudo touch /etc/init.d/setkey` and ran the 2nd command again... is there anything wrong with doing so?

---

### Post by renkinjutsu on 2009-07-17
bump,


Now i get this error message at boot.

/etc/init.d/rc:390: /etc/rcS.d/S37setkey: Permission denied


i checked and te rcS.d directory doesn't even exist!

---

