---
title: "wired network drivers for dell vostro 1310"
date: 2012-08-17
forum: Networking &amp; Wireless
---

### Post by nawaz1 on 2012-08-17
code shor below ...suggest me alternate way to dowload these driver from windows because i dont have net connectivity on ubunu dnt have wirless conection

so plz help so my wired net starts working 





sudo apt-get install --reinstall linux-headers-$(uname -r) linux-headers-generic build-essential dkms
wget [http://media.cdn.ubuntu-de.org/forum/attachments/24/23/3005217-r8168-dkms-8.031.00.tar.gz](http://media.cdn.ubuntu-de.org/forum/attachments/24/23/3005217-r8168-dkms-8.031.00.tar.gz)
sudo tar xvf 3005217-r8168-dkms-8.031.00.tar.gz -C /usr/src
sudo dkms add -m r8168-dkms -v 8.031.00
sudo dkms build -m r8168-dkms -v 8.031.00
sudo dkms install -m r8168-dkms -v 8.031.00 
echo "blacklist r8169" | sudo tee -a /etc/modprobe.d/blacklist.conf
sudo modprobe -rfv r8169
sudo mv /lib/modules/$(uname -r)/kernel/drivers/net/r8169.ko /lib/modules/$(uname -r)/kernel/drivers/net/r8169.bak
sudo modprobe -v r8168

---

