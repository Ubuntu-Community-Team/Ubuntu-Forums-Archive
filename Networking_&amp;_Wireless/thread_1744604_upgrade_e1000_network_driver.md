---
title: "upgrade e1000 network driver"
date: 2011-04-30
forum: Networking &amp; Wireless
---

### Post by taopublic on 2011-04-30
I'm a linux newbie and just installed ubuntu 10.04 LTS with upgrades. I have an intel pro 1000MT desktop adapter. With ubuntu 10.04 installation, the driver version is 7.3.21-k5. Because I have a lot of "Tx hang" error messages in the syslog, I've decided to upgrade to the latest network driver. I followed the README file in the new driver installation package (make install, rmmod, then modprobe, etc.) After it is done, I verified that I'm indeed running the new version, 

$ ethtool -i eth0
driver: e1000
version: **8.0.30-NAPI**
firmware-version: N/A
bus-info: 0000:01:07.0

The driver binary also has today's timestamp,

$ ls -l /lib/modules/2.6.32-31-generic/kernel/drivers/net/e1000
total 188
-rw-r--r-- 1 root root 189549 **2011-04-30** 11:10 e1000.ko

However, as soon as I reboot my computer, ethtool reports the old version again,

$ ethtool -i eth0
driver: e1000
version: **7.3.21-k5**-NAPI
firmware-version: N/A
bus-info: 0000:01:07.0

The driver binary still remains the same,

$ ls -l /lib/modules/2.6.32-31-generic/kernel/drivers/net/e1000
total 188
-rw-r--r-- 1 root root 189549 **2011-04-30** 11:10 e1000.ko

How can I make the new driver sticky?

---

### Post by chili555 on 2011-04-30
> ollowed the README file in the new driver installation package (make install, rmmod, then modprobe, etc.) Is that really what the README says? Doesn't it say [COLOR="Red"]make[/COLOR], sudo make install, rmmod and modprobe? Please try again with one additional step:```
make clean
make
sudo make install
sudo rmmod -f e1000
sudo modprobe e1000
modinfo e1000
```Post any errors. Any improvement?

---

### Post by taopublic on 2011-04-30
tried make then make install. not difference. same problem.

---

### Post by RoyB (Aus) on 2011-12-06
Any resolution to this issue?  I am having the exact same problem.  Followed the instructions in the driver readme and the old driver is still loaded.  Followed the slightly different instructions as above and the old driver is still loaded.

I'm almost at the point of having to rebuild the server using Centos or some other dist just to overcome this problem.  I'd really rather stick with Ubuntu.

---

### Post by chili555 on 2011-12-06
How about showing us the result of:```
cd directory/of/e1000 <--or wherever
make clean
make
sudo make install
sudo modprobe -rv e1000
sudo modprobe e1000
modinfo e1000
```Thanks.

---

### Post by BPuma on 2012-02-10
I have the same problem. I tried the above. What's the solution? :confused::confused::confused:

---

