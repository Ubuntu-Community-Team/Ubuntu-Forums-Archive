---
title: "automount webdav when detecting network"
date: 2012-06-08
forum: Networking &amp; Wireless
---

### Post by wolfris on 2012-06-08
Hi,
I want to mount my cloud drive on my Ubuntu (12.04) machine, whenever it connects to the internet. And I want it to mount as user, not as root. I followed all the steps of doing so (updating /etc/fstab, putting my password in the "secret" file, and putting a mounting script in /etc/network/if-up.d).

If I mount it manually, I actually can mount it as user (without sudo), but if it is mounted through the script in /etc/network/if-up.d the drive is mounted as root. 

Is this because the scripts in /etc/network/if-up.d are launched as root? Is there a way around this?

Thanks

---

