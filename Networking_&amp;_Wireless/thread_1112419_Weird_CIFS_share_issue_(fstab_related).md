---
title: "Weird CIFS share issue (fstab related)"
date: 2009-03-31
forum: Networking &amp; Wireless
---

### Post by dbsoundman on 2009-03-31
I've got an old machine in my living room running Ubuntu 7.04, which I have connected to my Ubuntu 8.10 "server" machine in my room via samba. However I can't seem to get the entry in fstab to automount the share on startup. I had this system before with my server running openSUSE and it was fine, now I've got Ubuntu on it and I can't get it to work. I can manually mount it using ```
sudo mount -t cifs
``` and all that stuff, but I can't get my fstab entry to work. Here's what it is:
```
//192.168.2.2/dan /remote/blackdiamond/files cifs username=dan,password=xxxxxx,rw,_netdev 0 0
```

All I did after the "switch" was change the share name IIRC, but now it doesn't work. I also added the _netdev option to see if that helped. What could be the problem here?

Thanks,
Dan

---

