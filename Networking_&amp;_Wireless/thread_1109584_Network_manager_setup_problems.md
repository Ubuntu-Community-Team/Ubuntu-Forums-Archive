---
title: "Network manager setup problems"
date: 2009-03-28
forum: Networking &amp; Wireless
---

### Post by psyboy55 on 2009-03-28
i finally have network manager running. when i click on it and see all the avalible networks i click mine. It does the two cicle loading thing, but none of them turn green. i click connect to other wireless network and type evreything in but nothing happens! did i get the WPa key wrong or did i do something else wrong?

---

### Post by pytheas22 on 2009-03-28
Obviously you should double-check to make sure the WPA passphrase that you're entering is correct.  Also make sure that it's set as the correct kind of password and authentication scheme--usually NetworkManager detects this automatically, but it may be wrong (for example, make sure it's not trying to use WEP instead of WPA).

If that doesn't help, you may have better luck using wicd, an alternative connection manager.  You can install wicd by typing:
```

echo 'deb http://apt.wicd.net hardy extras' | sudo tee -a /etc/apt/sources.list
wget -q http://apt.wicd.net/wicd.gpg -O- | sudo apt-key add -
sudo apt-get update
sudo apt-get install wicd
```

Then launch it from the Applications>Internet menu.

If you still can't connect using wicd, please open a terminal (Applications>Accessories>Terminal), run the following commands and post the output:
```

lshw -C Network
sudo iwlist scan
uname -rm
```

Please also tell me the name of the wireless network you're trying to connect to.

---

### Post by psyboy55 on 2009-03-28
it didn't work it said no such file or directory.

---

### Post by pytheas22 on 2009-03-28
> it didn't work it said no such file or directory.

Please be more specific.  What said 'no such file or directory'?

---

### Post by psyboy55 on 2009-03-29
Once i typed in the first line of the command terminal said "tee: ect/apt/sources.list: No such file or directory deb [http://apt.wicd.net](http://apt.wicd.net) hardy extras" Do i need internet connection for this?
p.s. thanks for your help!

---

### Post by pytheas22 on 2009-03-29
It looks like you made a typo: it should be:
```

echo 'deb http://apt.wicd.net hardy extras' | sudo tee -a **/etc**/apt/sources.list
```

I think you wrote .../**ect**/apt/... instead.  Also pay attention to the -a part of the command--if you leave it off, you will do something you don't want to do.  If possible, you should just copy and paste the commands to avoid errors.

Also, you will need an Internet connection for those commands to work, so if possible, plug your computer in via the wire.  If that's totally impossible, let me know and I'll provide instructions for installing wicd offline.

---

### Post by psyboy55 on 2009-03-29
ah ha! it now says "deb [http://apt.wicd.net](http://apt.wicd.net) hardy extras" im guessing that means i should be online. i can connect tommorow! i will post again in like 16 hours or so

---

### Post by pytheas22 on 2009-03-29
Actually the first command doesn't require an Internet connection; only the last three do.  But post back tomorrow and we'll take it from there.

FYI: to install wicd without being online, you need to download [this file]("http://downloads.sourceforge.net/wicd/wicd_1.5.9_all.deb?use_mirror=superb-west"), transfer it to your Ubuntu machine, and double-click to install.  This is what I suspect you will have to do, because I don't think your Ubuntu computer is really connected to the Internet right now.

---

### Post by psyboy55 on 2009-03-29
it says that it ca't install because of network manager. Im going to uninstall network manager to see what it will do

---

### Post by psyboy55 on 2009-03-29
ok i installed it. i found my network, went into advanced settngs and typed the WPA in, then i clicked connect . nothing happened......it just said connecting for abit, then stopped. What do i do!

---

### Post by pytheas22 on 2009-03-29
Please post the output of these commands:
```

lshw -C Network
sudo iwlist scan
uname -rm
```

---

### Post by psyboy55 on 2009-03-29
here it is

WARNING: you should run this program as super-user. 
  *-network:0              
       description: Ethernet interface 
       product: RTL-8139/8139C/8139C+ 
       vendor: Realtek Semiconductor Co., Ltd. 
       physical id: 9 
       bus info: pci@0000:01:09.0 
       logical name: eth0 
       version: 10 
       serial: 00:20:18:dc:15:1e 
       width: 32 bits 
       clock: 33MHz 
       capabilities: bus_master cap_list ethernet physical 
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 latency=64 maxlatency=64 mingnt=32 module=8139too multicast=yes 
  *-network:1 DISABLED 
       description: Wireless interface 
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller 
       vendor: Broadcom Corporation 
       physical id: a 
       bus info: pci@0000:01:0a.0 
       logical name: eth1 
       version: 02 
       serial: 00:1d:60:06:9c:22 
       width: 32 bits 
       clock: 33MHz 
       capabilities: bus_master ethernet physical wireless 
       configuration: broadcast=yes driver=bcm43xx driverversion=2.6.22-16-generic latency=64 module=bcm43xx multicast=yes wireless=IEEE 802.11b/g 


lo        Interface doesn't support scanning. 
 
eth0      Interface doesn't support scanning. 
 
eth1      Interface doesn't support scanning : No such device 

2.6.22-16-generic i686

---

### Post by pytheas22 on 2009-03-29
It looks like you're using an old version of Ubuntu (7.10 I think).  Is there a reason you're not using a more up-to-date release?  You would probably have better luck connecting then.

If you really need to stay with this old version, we might still be able to make your wireless connect, but it would be easier if you upgraded or reinstalled Ubuntu using a later version.

Also, please let me know whether or not it's possible for you to plug your computer into the Internet temporarily to connect.  It's going to be much easier to get the wireless working if you can get online using an ethernet cable for a few minutes first, in order to download some things.

---

### Post by psyboy55 on 2009-03-29
i am actually running 7.04. When i had internet connection and i clicked the update button it said ." I can get internet connection maybe today.

---

### Post by pytheas22 on 2009-03-29
Ubuntu 7.04 is no longer even supported--it reached end of life in October 2008.  It would really be much better for several reasons if you could upgrade to a more recent version of Ubuntu.

---

### Post by psyboy55 on 2009-03-29
do i have to order a new CD?

---

### Post by psyboy55 on 2009-03-29
ok i got ethernet connection and im trying to upgrade the Os

---

### Post by pytheas22 on 2009-03-29
> ok i got ethernet connection and im trying to upgrade the Os 

Good; you should upgrade to at least Ubuntu 8.04.  If the online update fails (which it may given that you're jumping up several versions of Ubuntu at once), you could just burn a CD of 8.04 or 8.10 from [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download).

---

### Post by psyboy55 on 2009-03-29
ok im doing that now, it's at 31%

---

### Post by psyboy55 on 2009-03-30
internet explorer restarted  the download multiple times! i switched To firefox...

---

