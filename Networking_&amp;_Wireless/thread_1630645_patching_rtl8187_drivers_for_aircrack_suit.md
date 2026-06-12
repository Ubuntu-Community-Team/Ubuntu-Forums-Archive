---
title: "patching rtl8187 drivers for aircrack suit"
date: 2010-11-25
forum: Networking &amp; Wireless
---

### Post by mrpervie on 2010-11-25
ubuntu 10.10
im trying to follow this tutorial 

[http://aircrack-ng.org/doku.php?id=r8187](http://aircrack-ng.org/doku.php?id=r8187)

###############################################################
R8187

rmmod the r8187 and rtl8187 modules before proceeding:

ifconfig wlan0 down	 
rmmod r8187 rtl8187 2>/dev/null
wget [http://dl.aircrack-ng.org/drivers/rtl8187_linux_26.1010.zip](http://dl.aircrack-ng.org/drivers/rtl8187_linux_26.1010.zip)
unzip rtl8187_linux_26.1010.zip
cd rtl8187_linux_26.1010.0622.2006/
wget [http://patches.aircrack-ng.org/rtl8187_2.6.27.patch](http://patches.aircrack-ng.org/rtl8187_2.6.27.patch)
wget [http://patches.aircrack-ng.org/rtl8187_2.6.32.patch](http://patches.aircrack-ng.org/rtl8187_2.6.32.patch)
tar xzf drv.tar.gz
tar xzf stack.tar.gz
patch -Np1 -i rtl8187_2.6.27.patch
patch -Np1 -i rtl8187_2.6.32.patch
make<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<i get stuck here
make install



##########################################################

when i get to "make" 
im not 100 percent sure what im supposed to do...
when i type MAKE i get this error....
##########################################################

haxor@user-System-Product-Name:~/rtl8187_linux_26.1010.0622.2006$ make
rm -f ieee80211/Module.symvers 2>/dev/null
rm -f ieee80211/Modules.symvers 2>/dev/null
make -C ieee80211 all
make[1]: Entering directory `/home/user/rtl8187_linux_26.1010.0622.2006/ieee80211'
make -C /lib/modules/2.6.35-23-generic/build M=/home/user/rtl8187_linux_26.1010.0622.2006/ieee80211 modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.35-23-generic'
  CC [M]  /home/user/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_rx.o
/home/user/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_rx.c:48: fatal error: linux/autoconf.h: No such file or directory
compilation terminated.
make[3]: *** [/home/user/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_rx.o] Error 1
make[2]: *** [_module_/home/user/rtl8187_linux_26.1010.0622.2006/ieee80211] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.35-23-generic'
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/home/user/rtl8187_linux_26.1010.0622.2006/ieee80211'
make: *** [all] Error 2
haxor@user-System-Product-Name:~/rtl8187_linux_26.1010.0622.2006$
############################################################ 
i can see a config file does not exist but im not sure what im missing ? should something else be installed?

---

### Post by Scytheon3 on 2011-01-03
I get this exact same error and so far how found no solution.

---

### Post by yo-mu on 2011-02-13
same error here. plz someone help

---

### Post by emtdan on 2011-02-15
You are getting an error because you need to input, "sudo su" then your password, before you can have access to "make" anything

---

### Post by hrki87 on 2011-02-20
Solution:

[B]touch /usr/src/linux-headers-[COLOR=Red]2.6.35-24[/COLOR]-generic/include/linux/autoconf.h

[/B]insert yours kernel version

---

### Post by Deadboy420 on 2011-03-02
I ran into a similar problem when patching drivers on Maverick 10.10 and realized that I needed kernel headers and a few other packages. Try this to download the necessary packages:

```
sudo apt-get install linux-headers-$(uname -r) build-essential make 
```

then go back to the folder you were working in and do your "make" and "make install" as the tutorial shows.

---

### Post by MDCCLXXVI on 2012-07-08
I did what the tutorial said [COLOR=Green]plus[/COLOR] what hrki87 said to do.

```
[B]
touch /usr/src/linux-headers-[COLOR=Red]2.6.35-32[/COLOR]-generic/include/linux/autoconf.h[/B]

```After that, the 'make' command executed ok.
But when I typed 'make install' this is what happened.

```

[COLOR=Blue]root@christo-pc:/home/christo/rtl8187_linux_26.1010.0622.2006# make[/COLOR]
rm -f ieee80211/Module.symvers 2>/dev/null
rm -f ieee80211/Modules.symvers 2>/dev/null
make -C ieee80211 all
make[1]: Entering directory `/home/christo/rtl8187_linux_26.1010.0622.2006/ieee80211'
make -C /lib/modules/2.6.35-32-generic/build M=/home/christo/rtl8187_linux_26.1010.0622.2006/ieee80211 modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.35-32-generic'
  Building modules, stage 2.
  MODPOST 5 modules
make[2]: Leaving directory `/usr/src/linux-headers-2.6.35-32-generic'
make[1]: Leaving directory `/home/christo/rtl8187_linux_26.1010.0622.2006/ieee80211'
chmod +x symvers
./symvers
make -C beta-8187 all
make[1]: Entering directory `/home/christo/rtl8187_linux_26.1010.0622.2006/beta-8187'
make -C /lib/modules/2.6.35-32-generic/build M=/home/christo/rtl8187_linux_26.1010.0622.2006/beta-8187 modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.35-32-generic'
  Building modules, stage 2.
  MODPOST 1 modules
make[2]: Leaving directory `/usr/src/linux-headers-2.6.35-32-generic'
make[1]: Leaving directory `/home/christo/rtl8187_linux_26.1010.0622.2006/beta-8187'
[COLOR=Blue]root@christo-pc:/home/christo/rtl8187_linux_26.1010.0622.2006# make install[/COLOR]
install -d /lib/modules/2.6.35-32-generic/kernel/drivers/net/wireless/rtl_ieee80211
install -d /lib/modules/2.6.35-32-generic/kernel/drivers/net/wireless/rtl8187
install -m 644 ./ieee80211/*.ko /lib/modules/2.6.35-32-generic/kernel/drivers/net/wireless/rtl_ieee80211
install -m 644 ./beta-8187/*.ko /lib/modules/2.6.35-32-generic/kernel/drivers/net/wireless/rtl8187
depmod -ae
[COLOR=Red]WARNING: -e needs -E or -F[/COLOR]

```Then I tried this after the error:

```

[COLOR=Blue]root@christo-pc:/home/christo/rtl8187_linux_26.1010.0622.2006# ls[/COLOR]
[COLOR=Indigo]beta-8187  drv.tar.gz  ieee80211  ifcfg-wlan0  makedrv  makedrvbk  Makefile  ReadMe.txt  rtl8187_2.6.27.patch  rtl8187_2.6.32.patch  stack.tar.gz  symvers  wlan0dhcp  wlan0down  wlan0rmv  wlan0up  wpa_supplicant-0.4.9[/COLOR]
[COLOR=Blue]root@christo-pc:/home/christo/rtl8187_linux_26.1010.0622.2006# make install -f Makefile[/COLOR]
install -d /lib/modules/2.6.35-32-generic/kernel/drivers/net/wireless/rtl_ieee80211
install -d /lib/modules/2.6.35-32-generic/kernel/drivers/net/wireless/rtl8187
install -m 644 ./ieee80211/*.ko /lib/modules/2.6.35-32-generic/kernel/drivers/net/wireless/rtl_ieee80211
install -m 644 ./beta-8187/*.ko /lib/modules/2.6.35-32-generic/kernel/drivers/net/wireless/rtl8187
depmod -ae
[COLOR=Red]WARNING: -e needs -E or -F[/COLOR]

```HELP!!! :confused::confused::confused:
I'm running ubuntu 10.10, kernel version **[COLOR=Red]2.6.35-32[/COLOR]**

---

### Post by chili555 on 2012-07-08
We don't support aircrack here, so I can't tell you how or if it works. However, I have patched a few drivers in my life and this is a warning, not an error. I suspect it can be safely ignored. Can you load the module rtl8187 without error? Does it connect to your network? If so, that's all we can do to help.

---

