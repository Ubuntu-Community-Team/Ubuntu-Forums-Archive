---
title: "Automount samba share using external IP"
date: 2012-11-09
forum: Networking &amp; Wireless
---

### Post by acrocephalus on 2012-11-09
Hello,
I would like to be able to automount a samba share outside my LAN, using my external IP. Is there a way to do it? Currently I am able to automount it adding this line to my /etc/fstab file:
```
//internal_ip/SambaShare /mnt/MountedFolder cifs uid=1000,user=username,password=password 0   0
```
Thank you so much!

Dani

---

