---
title: "How to manually install your rtl8188ce driver step-by-step"
date: 2012-03-21
forum: Networking &amp; Wireless
---

### Post by dan0804smith on 2012-03-21
there is a video link of me preforming this action at the bottom of the page

hey i want to start off by saying that the only reason i am doing this guide is because the ubuntu community has been so helpful to me in the past.

time to give back

How to manually install your rtl8188ce driver :

this tutorial is meant for users using 10.10 and up (im using 10.10)

download the top linux driver from this site (Linux driver for kernel 2.6.24 (and later, up to 3.2.x))
[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#RTL8188CE](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#RTL8188CE)

extract this to your desktop

open terminal

type: sudo su 
then: cd /path/to/file
then: make install

should look something like this:

daniel@daniel-HP-Pavilion-dv6-Notebook-PC:~$ sudo su
[sudo] password for daniel: 
root@daniel-HP-Pavilion-dv6-Notebook-PC:/home/daniel# cd /home/daniel/Desktop/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011
root@daniel-HP-Pavilion-dv6-Notebook-PC:/home/daniel/Desktop/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011# make install

this was my out put:

make -C /lib/modules/2.6.35-32-generic/build M=/home/daniel/Desktop/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.35-32-generic'
  Building modules, stage 2.
  MODPOST 1 modules
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-32-generic'
make[1]: Entering directory `/home/daniel/Desktop/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011/rtl8192ce'
make -C /lib/modules/2.6.35-32-generic/build M=/home/daniel/Desktop/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011/rtl8192ce modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.35-32-generic'
  Building modules, stage 2.
  MODPOST 1 modules
make[2]: Leaving directory `/usr/src/linux-headers-2.6.35-32-generic'
make[1]: Leaving directory `/home/daniel/Desktop/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011/rtl8192ce'
make[1]: Entering directory `/home/daniel/Desktop/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011/rtl8192se'
make -C /lib/modules/2.6.35-32-generic/build M=/home/daniel/Desktop/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011/rtl8192se modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.35-32-generic'
  Building modules, stage 2.
  MODPOST 1 modules
make[2]: Leaving directory `/usr/src/linux-headers-2.6.35-32-generic'
make[1]: Leaving directory `/home/daniel/Desktop/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011/rtl8192se'
make[1]: Entering directory `/home/daniel/Desktop/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011/rtl8192de'
make -C /lib/modules/2.6.35-32-generic/build M=/home/daniel/Desktop/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011/rtl8192de modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.35-32-generic'
  Building modules, stage 2.
  MODPOST 1 modules
make[2]: Leaving directory `/usr/src/linux-headers-2.6.35-32-generic'
make[1]: Leaving directory `/home/daniel/Desktop/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011/rtl8192de'

video of me doing this:  (watch in 720p to read text) 

[http://www.youtube.com/watch?v=QFh2EZhUKgs](http://www.youtube.com/watch?v=QFh2EZhUKgs) 

i hope this helps, let me know if it does.

stay strong my linux                            brethren

---

### Post by MrSchroeder13 on 2012-06-20
This worked great.  Did not need to blacklist the default 8192ce driver for success.  

Why exactly an outdated, non-listed driver works for a different chipset, who knows?  But it works.:KS

---

### Post by Dyronne on 2013-01-24
i tried it but every time i did it with either one of the driver downloads it comes to an message that said there was two errors, one being that "make : *** lib/modules/3.5.0-22-generic/build: No such file directory. Stop" and "make: *** [all] Error 2"

---

### Post by ikrs on 2013-03-22
> **Dyronne said:**
> i tried it but every time i did it with either one of the driver downloads it comes to an message that said there was two errors, one being that "make : *** lib/modules/3.5.0-22-generic/build: No such file directory. Stop" and "make: *** [all] Error 2"

I was having the same trouble make sure that you have kernel headers installed (linux-headers-3.5.0-xx) with the 'xx' being whatever its asking for (in your case 22) hope i helped you out in some way

Oh and thanks so much dan, you really helped me through the lovely experiece of installing drivers ;P

---

### Post by schworak on 2013-06-15
YOU ROCK!

Thank you so very much for this post. The YouTube video is kind of worthless but the link in the description got me here and that got me back online with WiFi! Thank you so very very very much!

---

### Post by Mister_Pyrrhuloxia on 2013-10-20
So I follow all of the directions and this is what I get after typing "make":

```
make
make -C /lib/modules/3.2.6/build M=/root/Desktop/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013 modules
make[1]: Entering directory `/usr/src/linux-source-3.2.6'

  WARNING: Symbol version dump /usr/src/linux-source-3.2.6/Module.symvers
           is missing; modules will have no dependencies and modversions.

  CC [M]  /root/Desktop/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/base.o
  CC [M]  /root/Desktop/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rc.o
  CC [M]  /root/Desktop/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/debug.o
  CC [M]  /root/Desktop/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/regd.o
  CC [M]  /root/Desktop/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/efuse.o
  CC [M]  /root/Desktop/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/cam.o
  CC [M]  /root/Desktop/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/ps.o
  CC [M]  /root/Desktop/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/core.o
  CC [M]  /root/Desktop/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/stats.o
  CC [M]  /root/Desktop/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/pci.o
  LD [M]  /root/Desktop/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtlwifi.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /root/Desktop/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtlwifi.mod.o
  LD [M]  /root/Desktop/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtlwifi.ko
make[1]: Leaving directory `/usr/src/linux-source-3.2.6'
make[1]: Entering directory `/root/Desktop/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8192ce'
make -C /lib/modules/3.2.6/build M=/root/Desktop/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8192ce modules
make[2]: Entering directory `/usr/src/linux-source-3.2.6'

  WARNING: Symbol version dump /usr/src/linux-source-3.2.6/Module.symvers
           is missing; modules will have no dependencies and modversions.

  CC [M]  /root/Desktop/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8192ce/hw.o
  CC [M]  /root/Desktop/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8192ce/table.o
  CC [M]  /root/Desktop/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8192ce/sw.o
  CC [M]  /root/Desktop/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8192ce/trx.o
  CC [M]  /root/Desktop/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8192ce/led.o
  CC [M]  /root/Desktop/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8192ce/fw.o
  CC [M]  /root/Desktop/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8192ce/phy.o
  CC [M]  /root/Desktop/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8192ce/rf.o
  CC [M]  /root/Desktop/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8192ce/dm.o
  LD [M]  /root/Desktop/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8192ce/rtl8192ce.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /root/Desktop/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8192ce/rtl8192ce.mod.o
  LD [M]  /root/Desktop/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8192ce/rtl8192ce.ko
make[2]: Leaving directory `/usr/src/linux-source-3.2.6'
make[1]: Leaving directory `/root/Desktop/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8192ce'
make[1]: Entering directory `/root/Desktop/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8192se'
make -C /lib/modules/3.2.6/build M=/root/Desktop/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8192se modules
make[2]: Entering directory `/usr/src/linux-source-3.2.6'

  WARNING: Symbol version dump /usr/src/linux-source-3.2.6/Module.symvers
           is missing; modules will have no dependencies and modversions.

  CC [M]  /root/Desktop/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8192se/hw.o
  CC [M]  /root/Desktop/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8192se/table.o
  CC [M]  /root/Desktop/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8192se/sw.o
  CC [M]  /root/Desktop/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8192se/trx.o
  CC [M]  /root/Desktop/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8192se/led.o
  CC [M]  /root/Desktop/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8192se/fw.o
  CC [M]  /root/Desktop/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8192se/phy.o
  CC [M]  /root/Desktop/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8192se/rf.o
  CC [M]  /root/Desktop/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8192se/dm.o
  LD [M]  /root/Desktop/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8192se/rtl8192se.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /root/Desktop/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8192se/rtl8192se.mod.o
  LD [M]  /root/Desktop/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8192se/rtl8192se.ko
make[2]: Leaving directory `/usr/src/linux-source-3.2.6'
make[1]: Leaving directory `/root/Desktop/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8192se'
make[1]: Entering directory `/root/Desktop/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8192de'
make -C /lib/modules/3.2.6/build M=/root/Desktop/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8192de modules
make[2]: Entering directory `/usr/src/linux-source-3.2.6'

  WARNING: Symbol version dump /usr/src/linux-source-3.2.6/Module.symvers
           is missing; modules will have no dependencies and modversions.

  CC [M]  /root/Desktop/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8192de/hw.o
  CC [M]  /root/Desktop/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8192de/table.o
  CC [M]  /root/Desktop/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8192de/sw.o
  CC [M]  /root/Desktop/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8192de/trx.o
  CC [M]  /root/Desktop/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8192de/led.o
  CC [M]  /root/Desktop/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8192de/fw.o
  CC [M]  /root/Desktop/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8192de/phy.o
  CC [M]  /root/Desktop/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8192de/rf.o
  CC [M]  /root/Desktop/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8192de/dm.o
  LD [M]  /root/Desktop/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8192de/rtl8192de.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /root/Desktop/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8192de/rtl8192de.mod.o
  LD [M]  /root/Desktop/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8192de/rtl8192de.ko
make[2]: Leaving directory `/usr/src/linux-source-3.2.6'
make[1]: Leaving directory `/root/Desktop/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8192de'
make[1]: Entering directory `/root/Desktop/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8723e'
make -C /lib/modules/3.2.6/build M=/root/Desktop/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8723e modules
make[2]: Entering directory `/usr/src/linux-source-3.2.6'

  WARNING: Symbol version dump /usr/src/linux-source-3.2.6/Module.symvers
           is missing; modules will have no dependencies and modversions.

  CC [M]  /root/Desktop/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8723e/hw.o
  CC [M]  /root/Desktop/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8723e/table.o
  CC [M]  /root/Desktop/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8723e/sw.o
  CC [M]  /root/Desktop/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8723e/trx.o
  CC [M]  /root/Desktop/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8723e/led.o
  CC [M]  /root/Desktop/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8723e/fw.o
  CC [M]  /root/Desktop/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8723e/phy.o
  CC [M]  /root/Desktop/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8723e/rf.o
  CC [M]  /root/Desktop/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8723e/dm.o
  CC [M]  /root/Desktop/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8723e/pwrseq.o
  CC [M]  /root/Desktop/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8723e/pwrseqcmd.o
  CC [M]  /root/Desktop/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8723e/hal_btc.o
  CC [M]  /root/Desktop/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8723e/hal_bt_coexist.o
  LD [M]  /root/Desktop/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8723e/rtl8723e.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /root/Desktop/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8723e/rtl8723e.mod.o
  LD [M]  /root/Desktop/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8723e/rtl8723e.ko
make[2]: Leaving directory `/usr/src/linux-source-3.2.6'
make[1]: Leaving directory `/root/Desktop/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8723e'
make[1]: Entering directory `/root/Desktop/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8188ee'
make -C /lib/modules/3.2.6/build M=/root/Desktop/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8188ee modules
make[2]: Entering directory `/usr/src/linux-source-3.2.6'

  WARNING: Symbol version dump /usr/src/linux-source-3.2.6/Module.symvers
           is missing; modules will have no dependencies and modversions.

  CC [M]  /root/Desktop/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8188ee/hw.o
  CC [M]  /root/Desktop/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8188ee/table.o
  CC [M]  /root/Desktop/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8188ee/sw.o
  CC [M]  /root/Desktop/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8188ee/trx.o
  CC [M]  /root/Desktop/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8188ee/led.o
  CC [M]  /root/Desktop/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8188ee/fw.o
  CC [M]  /root/Desktop/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8188ee/phy.o
  CC [M]  /root/Desktop/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8188ee/rf.o
  CC [M]  /root/Desktop/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8188ee/dm.o
  CC [M]  /root/Desktop/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8188ee/pwrseq.o
  CC [M]  /root/Desktop/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8188ee/pwrseqcmd.o
  LD [M]  /root/Desktop/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8188ee/rtl8188ee.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /root/Desktop/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8188ee/rtl8188ee.mod.o
  LD [M]  /root/Desktop/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8188ee/rtl8188ee.ko
make[2]: Leaving directory `/usr/src/linux-source-3.2.6'
make[1]: Leaving directory `/root/Desktop/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8188ee'
```


What should I do?

---

### Post by alexiscatapum on 2014-01-26
Hi!
 im a new linux user and also new in this forum.

i have troubles to install driver, please help me. i have already read this post and others posts to install [Realtek RTL8188CE Wireless]("http://foro.seguridadwireless.net/zona-linux/drivers-de-red-realtek-rtl8188ce-wireless-lan-802-11n/msg194582/?PHPSESSID=cf200585fee63bf7fef2ea8756773256#msg194582") [http://ubuntuforums.org/showthread.php?t=1604101](http://ubuntuforums.org/showthread.php?t=1604101) and [http://askubuntu.com/questions/342076/step-by-step-ubuntu-12-04-install-of-realtek-rtl8188ce-driver](http://askubuntu.com/questions/342076/step-by-step-ubuntu-12-04-install-of-realtek-rtl8188ce-driver) but i dont find the solution.

i have downloaded the driver from 
[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#RTL8188CE](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#RTL8188CE)
i have extracted the file
open a terminal, and acces the directory wich i extracted
sudo su
apt-get install gcc build-essential linux-headers-generic linux-headers-$(uname -r) 
and 
make install
but ERROR

```
alexis-HP-Pavilion-g6-Notebook-PC rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013 # make install
make -C /lib/modules/3.11.0-12-generic/build M=/home/alexis/Descargas/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013 modules
make[1]: se ingresa al directorio «/usr/src/linux-headers-3.11.0-12-generic»
  CC [M]  /home/alexis/Descargas/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/base.o
In file included from /home/alexis/Descargas/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/base.c:39:0:
/home/alexis/Descargas/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/pci.h:247:15: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘rtl_pci_probe’
 int __devinit rtl_pci_probe(struct pci_dev *pdev,
               ^
/home/alexis/Descargas/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/base.c: In function ‘rtl_action_proc’:
/home/alexis/Descargas/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/base.c:885:32: error: ‘struct ieee80211_conf’ has no member named ‘channel’
       rx_status.freq = hw->conf.channel->center_freq;
                                ^
/home/alexis/Descargas/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/base.c:886:32: error: ‘struct ieee80211_conf’ has no member named ‘channel’
       rx_status.band = hw->conf.channel->band;
                                ^
/home/alexis/Descargas/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/base.c: In function ‘rtl_send_smps_action’:
/home/alexis/Descargas/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/base.c:1451:24: error: ‘struct ieee80211_conf’ has no member named ‘channel’
   info->band = hw->conf.channel->band;
                        ^
make[2]: *** [/home/alexis/Descargas/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/base.o] Error 1
make[1]: *** [_module_/home/alexis/Descargas/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013] Error 2
make[1]: se sale del directorio «/usr/src/linux-headers-3.11.0-12-generic»
make: *** [all] Error 2
```

any idea???

thank you

---

### Post by praseodym on 2014-01-26
Hi,

you need a patched driver for kernel 3.11:
```

sudo apt-get install git
git clone https://github.com/FreedomBen/rtl8188ce-linux-driver
cd rtl8188ce-linux-driver
make
sudo make install
```
This device/driver is known to cause problems. You may want to try these module parameters:```

echo "options rtl8192ce swlps=0 ips=0" | sudo tee /etc/modprobe.d/rtl8192ce.conf
```
Reboot and check:
```

dmesg | grep rtl8
lsmod
iwconfig
```

---

### Post by alexiscatapum on 2014-01-27
> **praseodym said:**
> Hi,

you need a patched driver for kernel 3.11:
```

sudo apt-get install git
git clone https://github.com/FreedomBen/rtl8188ce-linux-driver
cd rtl8188ce-linux-driver
make
sudo make install
```
This device/driver is known to cause problems. You may want to try these module parameters:```

echo "options rtl8192ce swlps=0 ips=0" | sudo tee /etc/modprobe.d/rtl8192ce.conf
```
Reboot and check:
```

dmesg | grep rtl8
lsmod
iwconfig
```

thank you for the answer!

i have done everything with no error but it doesnt works

check:

```

alexis@alexis-HP-Pavilion-g6-Notebook-PC ~ $ echo "options rtl8192ce swlps=0 ips=0" | sudo tee /etc/modprobe.d/rtl8192ce.conf
[sudo] password for alexis: 
options rtl8192ce swlps=0 ips=0

```

reboot

```

alexis@alexis-HP-Pavilion-g6-Notebook-PC ~ $ dmesg | grep rtl8
[   66.315723] Modules linked in: parport_pc(F) ppdev(F) bnep rfcomm bluetooth rt2800usb hp_wmi sparse_keymap rt2x00usb rt2800lib rt2x00lib crc_ccitt(F) uvcvideo videobuf2_vmalloc videobuf2_memops videobuf2_core videodev joydev(F) arc4(F) **rtl8192ce(OF) **kvm_amd(F) kvm(F) rtlwifi(OF) dm_multipath(F) scsi_dh(F) microcode(F) mac80211 rtsx_pci_ms memstick psmouse(F) serio_raw(F) k10temp i2c_piix4 cfg80211 snd_hda_codec_idt snd_hda_codec_hdmi snd_hda_intel snd_hda_codec snd_hwdep(F) snd_pcm(F) snd_page_alloc(F) snd_seq_midi(F) snd_seq_midi_event(F) snd_rawmidi(F) snd_seq(F) snd_seq_device(F) snd_timer(F) snd(F) mac_hid soundcore(F) lp(F) parport(F) dm_mirror(F) dm_region_hash(F) dm_log(F) hid_generic usbhid hid rtsx_pci_sdmmc r8169 mii(F) radeon ohci_pci ahci(F) libahci(F) sdhci_pci rtsx_pci sdhci i2c_algo_bit ttm drm_kms_helper drm wmi video(F)

alexis@alexis-HP-Pavilion-g6-Notebook-PC ~ $ lsmod
Module                  Size  Used by
parport_pc             32701  0 
ppdev                  17671  0 
bnep                   19564  2 
rfcomm                 69070  0 
bluetooth             371874  10 bnep,rfcomm
rt2800usb              27005  0 
hp_wmi                 14062  0 
sparse_keymap          13948  1 hp_wmi
rt2x00usb              20713  1 rt2800usb
rt2800lib              79963  1 rt2800usb
rt2x00lib              55238  3 rt2x00usb,rt2800lib,rt2800usb
crc_ccitt              12707  1 rt2800lib
uvcvideo               80885  0 
videobuf2_vmalloc      13216  1 uvcvideo
videobuf2_memops       13362  1 videobuf2_vmalloc
videobuf2_core         40469  1 uvcvideo
videodev              133390  2 uvcvideo,videobuf2_core
joydev                 17377  0 
arc4                   12608  4 
**rtl8192ce**             137725  0 



```

i have linux mint 16 64 bits. can it be the problem?

---

### Post by praseodym on 2014-01-28
Are you using an USB-wireless stick? Module rt2800usb is loaded:
```

sudo modprobe -rfv rt2800usb rtl8192ce
sudo modprobe -v rtl8192ce
dmesg | egrep 'r8|rtl8'
iwconfig
iwlist chan
sudo iwlist scan
cat /etc/resolv.conf
```

---

### Post by alexiscatapum on 2014-01-28
Yes I'm using a wireless USB stick to access to the internet. but if i disconnect the laptop wireless it does not work anyway 

should repeat the process with the wirless stick offline?

---

### Post by praseodym on 2014-01-28
So, check the outputs without stick

---

### Post by praseodym on 2014-01-28
Did you copy the firmware?
```

cd rtl8188ce-linux-driver
sudo cp -r firmware/* /lib/firmware  
```

---

### Post by alexiscatapum on 2014-01-28
i do everything and seems that it works, but the conection is slow and the power varies every 5 or 10 seconds, 30% 70% 40% ...

do know any way to put maximum performance card?

like this in windows [http://www.taringa.net/posts/hazlo-tu-mismo/13652186/Aumentar-la-senal-de-Wifi-Windows-xp-y-7.html](http://www.taringa.net/posts/hazlo-tu-mismo/13652186/Aumentar-la-senal-de-Wifi-Windows-xp-y-7.html)

---

### Post by praseodym on 2014-01-28
Lets check
```

iwconfig
ifconfig -a
iwlist chan
sudo iwlist scan
cat /etc/resolv.conf
```

---

### Post by alexiscatapum on 2014-01-28
the signal is 100% but now i cant connect through laptop wirless. i have to connect through usb wireless to post this post :(

:(:(:(:(:(:(:(

---

### Post by praseodym on 2014-01-28
Please show the outputs

---

### Post by alexiscatapum on 2014-01-28
alexis@alexis-HP-Pavilion-g6-Notebook-PC ~ $ iwconfig
eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=33 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          
alexis@alexis-HP-Pavilion-g6-Notebook-PC ~ $ ifconfig -a
eth0      Link encap:Ethernet  direcciónHW 74:46:a0:77:b1:ed  
          ACTIVO DIFUSIÓN MULTICAST  MTU:1500  Métrica:1
          Paquetes RX:0 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:0 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:1000 
          Bytes RX:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Bucle local  
          Direc. inet:127.0.0.1  Másc:255.0.0.0
          Dirección inet6: ::1/128 Alcance:Anfitrión
          ACTIVO BUCLE FUNCIONANDO  MTU:65536  Métrica:1
          Paquetes RX:491 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:491 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:0 
          Bytes RX:79991 (79.9 KB)  TX bytes:79991 (79.9 KB)

wlan0     Link encap:Ethernet  direcciónHW 20:10:7a:25:39:c4  
          ACTIVO DIFUSIÓN MULTICAST  MTU:1500  Métrica:1
          Paquetes RX:0 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:0 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:1000 
          Bytes RX:0 (0.0 B)  TX bytes:0 (0.0 B)

alexis@alexis-HP-Pavilion-g6-Notebook-PC ~ $ iwlist chan
eth0      no frequency information.

lo        no frequency information.

wlan0     13 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz
alexis@alexis-HP-Pavilion-g6-Notebook-PC ~ $ cat /etc/resolv.conf
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN

---

### Post by praseodym on 2014-01-29
There are no nameservers listed:
```

echo -e "nameserver 8.8.8.8\nnameserver 8.8.4.4" | sudo tee -a /etc/resolv.conf
sudo /etc/init.d/networking restart
sudo service network-manager restart
```

---

### Post by Filipe_Baptista on 2014-06-23
Hello!
Sorry for interrupting, but I was following your instructions to install the driver, but I had this error when I was doing "make" in console:

"ze@ze-laptop:~/Transferências/2$ make
make -C /lib/modules/2.6.32-62-generic/build M=/home/ze/Transferências/2 modules
make[1]: Entrando no diretório `/usr/src/linux-headers-2.6.32-62-generic'
  CC [M]  /home/ze/Transferências/2/base.o
In file included from /home/ze/Transferências/2/base.c:32:
/home/ze/Transferências/2/wifi.h: In function ‘rtl_find_sta’:
/home/ze/Transferências/2/wifi.h:2257: warning: passing argument 1 of ‘ieee80211_find_sta’ from incompatible pointer type
include/net/mac80211.h:2086: note: expected ‘struct ieee80211_hw *’ but argument is of type ‘struct ieee80211_vif *’
In file included from /home/ze/Transferências/2/base.c:34:
/home/ze/Transferências/2/base.h: At top level:
/home/ze/Transferências/2/base.h:144: warning: ‘enum ieee80211_smps_mode’ declared inside parameter list
/home/ze/Transferências/2/base.h:144: warning: its scope is only this definition or declaration, which is probably not what you want
/home/ze/Transferências/2/base.c: In function ‘_rtl_init_mac80211’:
/home/ze/Transferências/2/base.c:325: error: ‘IEEE80211_HW_CONNECTION_MONITOR’ undeclared (first use in this function)
/home/ze/Transferências/2/base.c:325: error: (Each undeclared identifier is reported only once
/home/ze/Transferências/2/base.c:325: error: for each function it appears in.)
/home/ze/Transferências/2/base.c: In function ‘rtl_tx_agg_start’:
/home/ze/Transferências/2/base.c:1019: warning: passing argument 1 of ‘ieee80211_start_tx_ba_cb_irqsafe’ from incompatible pointer type
include/net/mac80211.h:2033: note: expected ‘struct ieee80211_hw *’ but argument is of type ‘struct ieee80211_vif *’
/home/ze/Transferências/2/base.c: In function ‘rtl_tx_agg_stop’:
/home/ze/Transferências/2/base.c:1048: warning: passing argument 1 of ‘ieee80211_stop_tx_ba_cb_irqsafe’ from incompatible pointer type
include/net/mac80211.h:2074: note: expected ‘struct ieee80211_hw *’ but argument is of type ‘struct ieee80211_vif *’
/home/ze/Transferências/2/base.c: In function ‘rtl_watchdog_wq_callback’:
/home/ze/Transferências/2/base.c:1302: error: implicit declaration of function ‘ieee80211_connection_loss’
/home/ze/Transferências/2/base.c: At top level:
/home/ze/Transferências/2/base.c:1369: warning: ‘enum ieee80211_smps_mode’ declared inside parameter list
/home/ze/Transferências/2/base.c:1369: error: parameter 2 (‘smps’) has incomplete type
/home/ze/Transferências/2/base.c: In function ‘rtl_make_smps_action’:
/home/ze/Transferências/2/base.c:1389: error: ‘WLAN_HT_ACTION_SMPS’ undeclared (first use in this function)
/home/ze/Transferências/2/base.c:1391: error: ‘IEEE80211_SMPS_AUTOMATIC’ undeclared (first use in this function)
/home/ze/Transferências/2/base.c:1392: error: ‘IEEE80211_SMPS_NUM_MODES’ undeclared (first use in this function)
/home/ze/Transferências/2/base.c:1394: error: ‘IEEE80211_SMPS_OFF’ undeclared (first use in this function)
/home/ze/Transferências/2/base.c:1396: error: ‘WLAN_HT_SMPS_CONTROL_DISABLED’ undeclared (first use in this function)
/home/ze/Transferências/2/base.c:1398: error: ‘IEEE80211_SMPS_STATIC’ undeclared (first use in this function)
/home/ze/Transferências/2/base.c:1400: error: ‘WLAN_HT_SMPS_CONTROL_STATIC’ undeclared (first use in this function)
/home/ze/Transferências/2/base.c:1402: error: ‘IEEE80211_SMPS_DYNAMIC’ undeclared (first use in this function)
/home/ze/Transferências/2/base.c:1404: error: ‘WLAN_HT_SMPS_CONTROL_DYNAMIC’ undeclared (first use in this function)
/home/ze/Transferências/2/base.c: At top level:
/home/ze/Transferências/2/base.c:1413: warning: ‘enum ieee80211_smps_mode’ declared inside parameter list
/home/ze/Transferências/2/base.c:1413: error: parameter 3 (‘smps’) has incomplete type
/home/ze/Transferências/2/base.c: In function ‘rtl_send_smps_action’:
/home/ze/Transferências/2/base.c:1441: error: type of formal parameter 2 is incomplete
/home/ze/Transferências/2/base.c: At top level:
/home/ze/Transferências/2/base.c:1832: fatal error: opening dependency file /home/ze/Transferências/2/.base.o.d: Permissão negada
compilation terminated.
make[2]: ** [/home/ze/Transferências/2/base.o] Erro 1
make[1]: ** [_module_/home/ze/Transferências/2] Erro 2
make[1]: Saindo do diretório `/usr/src/linux-headers-2.6.32-62-generic'
make: ** [all] Erro 2

"


Thanks!

---

### Post by wildmanne39 on 2014-06-23
That is an old driver for kernel 2.6 so if you are using a newer version of ubuntu it will not compile on it.

---

### Post by daniel243 on 2015-01-30
How to solve this issue in 14.04?

---

