---
title: "Can mount using NFS with the terminal but not with FSTAB"
date: 2011-01-15
forum: Networking &amp; Wireless
---

### Post by calande on 2011-01-15
Hello,

I'm able to mount a NAS using NFS and the terminal, but not using FSTAB. Here's what I'm using to mount is using the terminal:
```
sudo mount 192.168.0.13:/volume1/private /home/charles/diskstation/private
```
It works. Now, here's what I have in my FSTAB:
```
diskstation:/volume1/private	/home/charles/diskstation/private	nfs4 _netdev,auto  0  0
```
It doesn't mount the NAS when I restart my computer. I also tried that:
```
diskstation:/volume1/private	/home/charles/diskstation/private	nfs	rsize=8192,wsize=8192,timeo=14,intr
```
With no success. What do you think should be the correct synthax for my FSTAB? Maybe the computer is trying to mount the NAS before the network board is up? I'm lost...
Thanks,

---

