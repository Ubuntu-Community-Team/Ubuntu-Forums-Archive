---
title: "Intermittent issue with Intel 82575EB gigabit NIC - waiting for headers issue"
date: 2009-06-21
forum: Networking &amp; Wireless
---

### Post by televisi on 2009-06-21
Hi All,
I just got new hardware, it comes with 2 NIC built in cards, they are Intel 82575EB Gigabit Ethernet.

I've tried to install:
- Ubuntu Server 8.04 (32 bit)
- Ubuntu Server 8.04 (64 bit)
- Ubuntu Server 9.04 (32 bit)
- Ubuntu Server 9.04 (64 bit)

but all of them having an intermittent issue, meaning: 
- I can ping my ADSL modem very fast (I get the ping response very fast)
- if I can ping [www.yahoo.com]("http://www.yahoo.com"), it shows [B]slow ping response
[/B]Slow ping response ==> amount of TTL and time is exactly the same, but the 'ping reply text' is *stuttering*)

Strange thing, I try on different PC (which has Ubuntu server 8.04 32 bit), pinging yahoo is faster than that new computer.

Also, everytime I do "sudo apt-get update", it always **stuck / wait for very long time in [Waiting for headers]**, but then when I use the other PC, it runs very very quick...

Question:
- Does it mean my Ubuntu Server (8.04 / 9.04) unable to use this new gigabit NIC? if that's the case should I 'reinstall' the driver?
- How do I 'reinstall' RPM driver in Ubuntu (as that's what Intel site support)

Thanks in advance!!!</div></div>

---

### Post by televisi on 2009-06-21
I found similar old thread but using e1000 driver ([http://ubuntuforums.org/showthread.php?t=551720);](http://ubuntuforums.org/showthread.php?t=551720);) will it be the same? as my Intel 82575EB is not listed there??

Thanks

---

### Post by jhannah on 2009-06-21
Are you sure your NIC isn't using the e1000 driver? You can double check with:

```
ethtool -i **eth0**
```Replacing eth0 with the interfaces you wish to check. The "driver:" line should identify the kernel module that is presenting the device.

The issue you are reporting sounds most likely to be related to the MTU value you have set on the interfaces. The PPPoE (which the transport used to reach your ADSL modem) packet overhead could be causing frames to be fragmented in ways that don't really make sense. The default value of 1500 is enough to encompass the most Ethernet encapsulated packets but with the addition of the extra, larger, header I would recommend you try upping the MTU to 1518 and see if that helps. 

To do so, run the following on both interfaces:

```
ifconfig **eth0** mtu 1518
```If that does the trick, you can make it perminant by adding an mtu line to your /etc/network/interfaces configuration. Check out the man page for interfaces for more information on that.

Let me know if that helps.

---

### Post by televisi on 2009-06-21
Err... I cannot do ethtool as it is not installed 

Is there anyway I can download it from my Windows machine and install it to my offline PC?

Also, I tried that
```
ifconfig eth0 mtu 1518
```and the ```
sudo apt-get update
``` still very slow and at the end just stuck there... :cry:

---

### Post by televisi on 2009-06-21
Ah... finally able to get ethtool info:

```

Driver: igb
Version: 1.2.45-k2
Firmware-version: 2.1-0
Bus-info: 0000:01:00.0

```So, in this case I can't use e1000 driver, right?

Err... I've been thinking, if Ubuntu server 9.04 able to detect my NIC cards (as per above), then it must have been something else that causing "sudo apt-get update"**stuck / wait for very long time in [Waiting for headers]**, right?

Apparently, according to _[Intel site]("http://downloadcenter.intel.com/Detail_Desc.aspx?ProductID=2874&DwnldID=13663&lang=eng")_, the latest driver they have is 1.3.19.3. Do you think it is wise to upgrade to the latest driver?

Let say, this issue caused by driver, please tell me whether the below process is okay to update my driver:
- download the latest intel driver (igb-1.3.19.3.tar.gz) and put in home folder
- extract it using command ==> **tar -zxvf igb-1.3.19.3.tar.gz**
- go to ~/[B]igb-1.3.19.3/src/
- sudo make install
[/B]- go to /lib/modules/2.6.28-11-server/kernel/drivers/net/igb/ (where supposedly I will see *igb.ko*)
- sudo modprobe igb
- sudo insmod igb

But then, when doing **sudo make install **in the above, I receive the following error:
```
Makefile:69: *** Linux kernel soource not found in any of these locations:
Makefile:70: 
Makefile:71: *** Install the appropriate kernel development package,eg.
Makefile:72: *** kernel-devel, for building kernel modules and try again. Stop. 
```

---

### Post by jhannah on 2009-06-24
You are correct the driver you have is out of date. Keep in mind that the new module you build will be blown away once you update linux-kernel. In order to build the module, you will need a copy of linux-headers so go ahead and run the below command:

```
sudo aptitude install linux-kernel-headers
```

Unfortunately, that will require you do download a pretty large file.

I was pretty sure that the e1000 driver would work with this card. It might be worth trying to remove the igb driver and modprobing the e1000 driver to see if it detects it and if it makes your network connection more reliable:

```

sudo rmmod igb
sudo modprobe e1000
dmesg | tail -n50

```

After that, it will dump out dmesg which should tell you if it detected the interface. You can then double check the driver with ethtool provided the above commands complete successfully.

---

### Post by televisi on 2009-06-24
Hi Jon,
Thanks for such a comprehensive steps, I suspect the file "linux-kernel-headers" can be downloaded from [http://packages.ubuntu.com/jaunty/linux-libc-dev](http://packages.ubuntu.com/jaunty/linux-libc-dev) ?

Also, is it worth trying e1000 driver, although the fact Intel already supply their own igb driver (which is from this [Intel site]("http://downloadcenter.intel.com/Detail_Desc.aspx?ProductID=2874&DwnldID=13663&lang=eng"))

Also, I suspect, by installing that "linux-kernel-headers" package will remove the issue when I do **sudo make install**, right?

Thanks heaps!!!

---

### Post by jhannah on 2009-06-25
You are correct, that package should do the trick and will provide the files necessary to build the module against your kernel. Just make sure the version matches your installed kernel version (you can check this with 'uname -r').

I think if the e1000 driver ends up working it is probably worth just sticking with that driver. It has been around for quite awhile and is well tested and used prolifically. I'm not 100% positive that the e1000 driver even supports the NIC though.

---

### Post by televisi on 2009-07-01
Hi Jon,
After looking back to this thread as well as [_**e1000 thread**_]("http://ubuntuforums.org/showthread.php?t=551720")
I've decided to download all necessary packages from [http://packages.ubuntu.com](http://packages.ubuntu.com) and copy them over to my Ubuntu 9.04 server through usb; and install it using 'dpkg -i' method.

My kernel ('uname -r'): 2.6.28-11-server

These are the list:
- make_3.81-5_amd64.deb
- dpkg-dev_1.14.24ubuntu1_all.deb
- linux-libc-dev_2.6.28-11.42_amd64.deb
- linux-source-2.6.28_2.6.28-11.42_all.deb
- build-essential_11.4_amd64.deb
- libc6-dev_2.9-4ubuntu6_amd64.deb

But after all of them installed, I still receive the same error message when trying to install [Intel igb driver]("http://downloadcenter.intel.com/Detail_Desc.aspx?ProductID=2874&DwnldID=13663&lang=eng")
```
Makefile:69: *** Linux kernel soource not found in any of these locations:
Makefile:70: 
Makefile:71: *** Install the appropriate kernel development package,eg.
Makefile:72: *** kernel-devel, for building kernel modules and try again. Stop.
```I was thinking to create/build e1000 driver; unfortunately the intel site no longer supply that driver...

Furthermore, one of the suggestion from **_[e1000 post]("http://ubuntuforums.org/showpost.php?p=3436802&postcount=17")_** is to change "autoneg off"; 
```
sudo ethtool -s eth0 speed 1000 duplex full autoneg off
```right after I change the autoneg to off, my ethernet can't access anything...and I have to restart my PC
```
Speed:Unknown! (65535)
Duplex: Unknown! (255)

```
I really really need everyone's help in this issue :(

Thanks so much again!

---

### Post by knurft on 2009-07-02
Like it says on the linux-libc-dev page: 
"They are NOT meant to be used to build third-party modules for your kernel. Use linux-headers-* packages for that."

In your case that would be  [http://packages.ubuntu.com/jaunty/linux-headers-2.6.28-11-server](http://packages.ubuntu.com/jaunty/linux-headers-2.6.28-11-server) I guess.

Hope this helps,

Thijs

---

### Post by televisi on 2009-07-14
Finally, after getting help from my friend, I'm able to upgrade my Intel igb driver. 

Please find below the steps to upgrade your igb driver:
   
  Assumption:
- igb NIC card is eth0

Steps:
- attach another NIC card, so at least you can connect to internet while upgrading the problematic igb NIC card
  - download [latest intel driver]("http://downloadcenter.intel.com/Detail_Desc.aspx?ProductID=2874&DwnldID=13663&lang=eng") from intel site to your home folder
```
$ cd
$ wget http://downloadmirror.intel.com/13663/eng/igb-1.3.19.3.tar.gz
```- Extract it to your home directory
```
$ tar -zxvf igb-1.3.19.3.tar.gz
```-Make install
```
$[FONT=&quot] cd igb-1.3.19.3/src/[/FONT]
$[FONT=&quot] sudo make install[/FONT]

```Your result might be like this:
> make -C /lib/modules/2.6.28-11-server/build SUBDIRS=/home/televisi/igb-1.3.19.3/src modules
  make[1]: Entering directory `/usr/src/linux-headers-2.6.28-11-server'
    CC [M]  /home/televisi/igb-1.3.19.3/src/igb_main.o
    CC [M]  /home/televisi/igb-1.3.19.3/src/e1000_82575.o
    CC [M]  /home/televisi/igb-1.3.19.3/src/e1000_mac.o
    CC [M]  /home/televisi/igb-1.3.19.3/src/e1000_nvm.o
    CC [M]  /home/televisi/igb-1.3.19.3/src/e1000_phy.o
    CC [M]  /home/televisi/igb-1.3.19.3/src/e1000_manage.o
    CC [M]  /home/televisi/igb-1.3.19.3/src/igb_param.o
    CC [M]  /home/televisi/igb-1.3.19.3/src/igb_ethtool.o
    CC [M]  /home/televisi/igb-1.3.19.3/src/kcompat.o
    CC [M]  /home/televisi/igb-1.3.19.3/src/e1000_api.o
    LD [M]  /home/televisi/igb-1.3.19.3/src/igb.o
    Building modules, stage 2.
    MODPOST 1 modules
    CC      /home/televisi/igb-1.3.19.3/src/igb.mod.o
    LD [M]  /home/televisi/igb-1.3.19.3/src/igb.ko
  make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-11-server'
  gzip -c ../igb.7 > igb.7.gz
  # remove all old versions of the driver
  find /lib/modules/2.6.28-11-server -name igb.ko -exec rm -f {} \; || true
  find /lib/modules/2.6.28-11-server -name igb.ko.gz -exec rm -f {} \; || true
  install -D -m 644 igb.ko /lib/modules/2.6.28-11-server/kernel/drivers/net/igb/igb.ko
  /sbin/depmod -a || true
  install -D -m 644 igb.7.gz /usr/share/man/man7/igb.7.gz
  man -c -P'cat > /dev/null' igb || true
  igb.
  - Check whether the existing/old driver still showing the old one
```
$ [FONT=&quot]ethtool &#8211;i eth0[/FONT]
```> driver: igb
version: 1.2.45-k2
firmware-version: 2.1-0
bus-info: 0000:01:00.0
- If yes, you need to bring eth0 down and reload the driver
```
$ ifconfig eth0 down
$ lsmod | grep igb; **make sure it's there**
$ modprobe -r igb; lsmod | grep igb; **make sure it's not there**
$ modprobe igb
$ ifconfig eth0 up

```- now use **ethtool &#8211;i eth0**, and you will find the latest driver
> driver: igb
version: **1.3.19.3**
firmware-version: 2.1-0
bus-info: 0000:01:00.0</div></div>

---

