---
title: "Can't reach NAS"
date: 2010-10-16
forum: Networking &amp; Wireless
---

### Post by TopGear on 2010-10-16
Hello people,

I just installed Kubuntu 10.10. And I've got a NAS in my network.
I just want to access that NAS, but I can't. When I go to Network, I see the NAS. I dubbleclick on it, and there's a SMB version of my NAS, and a folder wich redirects to de URL of my NAS. Such as 192.168.111.111.
But I can't get into the NAS itself, what's quite annoying.

Thank you for the help :D

After installing SMBFS and running
```
sudo mount -t smbfs //IPNAS/Qmultimedia /mnt/Qmultimedia -o username=xxx,password=xxx
```
I can just reach my NAS @ /mnt/Qmultimedia :D

---

