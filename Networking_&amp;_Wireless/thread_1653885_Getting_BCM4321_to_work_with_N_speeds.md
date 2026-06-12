---
title: "Getting BCM4321 to work with N speeds"
date: 2010-12-27
forum: Networking &amp; Wireless
---

### Post by Boondoklife on 2010-12-27
I have a BCM4321 and have not been able to get it to connect at N speeds, but finally got it working with broadcoms drivers from their site. The drivers in jockey would only get me b/g speed not n.

[QUOTE=lshw -c network]  *-network               
       description: Wireless interface
       product: BCM4321 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth2
       version: 03
       serial: 00:21:00:2d:ca:14
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.100.82.38 ip=10.0.1.12 latency=0 multicast=yes wireless=IEEE 802.11abgn
       resources: irq:17 memory:d1200000-d1203fff memory:d1000000-d10fffff
[/QUOTE]

here is a small script that I wrote to assist others in getting it installed and working.

First download the drivers from [http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

then copy this into a script: compile.sh
```
#!/bin/bash
KERNEL=$( uname -r  )

rmmod b43
rmmod wl
rmmod ssb

make -C /lib/modules/"$KERNEL"/build M=`pwd` clean
make -C /lib/modules/"$KERNEL"/build M=`pwd`
cp -f wl.ko /lib/modules/"$KERNEL"/kernel/lib

depmod -a

update-initramfs -u

echo "#Commented out to get wireless card working correctly" | tee -a /etc/modprobe.d/blacklist.conf
echo "blacklist ssb" | tee -a /etc/modprobe.d/blacklist.conf
echo "blacklist b43" | tee -a /etc/modprobe.d/blacklist.conf
echo 'lib80211' | tee -a /etc/modules
echo 'wl' | tee -a /etc/modules
modprobe lib80211
insmod /lib/modules/`uname -r`/kernel/lib/wl.ko

echo '###########################################################'
echo "# Don't forget to add the following line to /etc/rc.local #"
echo '#                                                         #'
echo '# insmod /lib/modules/`uname -r`/kernel/lib/wl.ko         #'
echo '###########################################################'

```Extract the file and place the compile.sh into the folder you extracted the drivers to and run it with sudo.
```
chmod +x compile.sh
sudo ./compile.sh
```Boosted my speeds from 54mbps to 273mbps!!!

Please note, if the kernel changes then you will have to do this again. if you don't want that hassel and don't mind staying on your current kernel then lock it in the package manager.

---

### Post by Boondoklife on 2010-12-31
Just wanted to post that I just get another one of these cards to replace a pos intel 4965 agn (that just can not seem to run in N mode), and the script worked fine.

---

### Post by alfonso78 on 2012-02-11
Hi!

I know this thread has been dead a long time, so I ask: is this still relevant?

I have a BCM4321 802.11a/b/g/n but "iw list" shows no channel in 5 GHz band.

[http://wireless.kernel.org/en/users/Drivers/b43#Not_working_yet](http://wireless.kernel.org/en/users/Drivers/b43#Not_working_yet) says "5GHz for N-PHY cards" is not working yet.

I can see this script blacklists b43 and ssb and uses wl and lib80211 instead. Does this give you access to 5 GHz channels?

thank you,

---

### Post by Boondoklife on 2012-02-12
I believe it did allow me to connect to a 5Ghz band, but can not say for sure. Give it a try and if so, please report back so others will know.

---

### Post by alfonso78 on 2012-02-12
I created a thread with my experience:
[http://ubuntuforums.org/showthread.php?t=1923762](http://ubuntuforums.org/showthread.php?t=1923762)

cheers,

---

