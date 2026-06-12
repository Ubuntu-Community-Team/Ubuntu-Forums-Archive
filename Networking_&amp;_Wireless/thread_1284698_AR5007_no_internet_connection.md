---
title: "AR5007 no internet connection"
date: 2009-10-06
forum: Networking &amp; Wireless
---

### Post by Raufio on 2009-10-06
I have a vista and ubuntu partioned laptop. In unbuntu, originally, I could get wireless connection but now i have none. I am typing this from Vista because it can connect. I think this means that there is a driver problem. I was just wondering if there was a way that i could get all of the necesary files on to a USB drive and transfer them from the usb to the ubuntu side. I just need to know where to get all of the necesary files.
thanks
Stephen

---

### Post by Raufio on 2009-10-07
I solved the problem hopefully permanently.
I ran
 ```
sudo apt-get install linux-headers-$(uname -r)
wget http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6-current.tar.gz
sudo mv madwifi-hal-0.10.5.6-current.tar.gz /usr/local/src/
cd /usr/local/src/
sudo tar -zxvf madwifi-hal-0.10.5.6-current.tar.gz
cd madwifi-hal-0.10.5.6-r4016-20090429/scripts/
sudo ./madwifi-unload
sudo ./find-madwifi-modules.sh $(uname -r)

WARNING:
It seems that there are modules left from previous MadWifi installations.
If you are unistalling the MadWifi modules please press "r" to remove them.
If you are installing new MadWifi modules, you should consider removing those
already installed, or else you may experience problems during operation.
Remove old modules?

[l]ist, [r]emove, [i]gnore or e[x]it (l,r,i,[x]) ? 
r

cd ..
sudo make
sudo make install
```
after putting [http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6-current.tar.gz](http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6-current.tar.gz) on a flash drive and onto my desktop.
that didn't solve the problem all the way.
so I ran
```

sudo gedit              /etc/modprobe.d/blacklist

```
and added "blacklist ath_pci"
rebooted and ran
```

sudo modprobe ath_pci

```
and it started working!!!!
:guitar:
I then did 
```

sudo gedit /etc/modules

```
and added "ath_pci"
so that it will, hopefully, work everytime i start it up.

---

