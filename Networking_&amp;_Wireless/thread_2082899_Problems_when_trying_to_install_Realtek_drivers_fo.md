---
title: "Problems when trying to install Realtek drivers for RTL8188CE WiFi Adapte"
date: 2012-11-10
forum: Networking &amp; Wireless
---

### Post by apeisa on 2012-11-10
I am new to linux and having problems with Wifi. It does work, but it's very slow and shaky (drops connection). All the other machines (few Windows, Xbox, Samsung smart-tv etc) work just fine.

I have searched these forums and it seems that many people are having problems with default drivers. [Realtek provides linux drivers]("http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PFid=48&Level=5&Conn=4&ProdID=278&DownTypeID=3&GetDown=false&Downloads=true#2722"), but I am not sure how to install them. These are the steps I have taken:

1. Downloaded the drivers from realtek site ([http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PFid=48&Level=5&Conn=4&ProdID=278&DownTypeID=3&GetDown=false&Downloads=true#2722](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PFid=48&Level=5&Conn=4&ProdID=278&DownTypeID=3&GetDown=false&Downloads=true#2722)) 
2. Extracted the tar.gz package to /home/Downloads/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/
3. Opened terminal, cd:d to the directory above
4. Read readme and did steps that was instructed
4.1 sudo su
4.2 make
4.3 make install
4.4 reboot

After reboot nothing seems to be changed and I don't really have clue if the new driver is installed or in use currently?

---

### Post by apeisa on 2012-11-10
I have used this command to see my hardware and drivers:

sudo lshw -html >> system_info.html

And it shows:

> 
id:	
network
description:	Wireless interface
product:	RTL8188CE 802.11b/g/n WiFi Adapter
vendor:	Realtek Semiconductor Co., Ltd.
physical id:	
0
bus info:	
pci@0000:02:00.0
logical name:	
wlan0
version:	01
serial:	7c:4f:b5:45:c2:ab
width:	64 bits
clock:	33MHz
capabilities:	pm msi pciexpress bus_master cap_list ethernet physical wireless
configuration:	
broadcast	=	yes
driver	=	rtl8192ce
driverversion	=	3.2.0-32-generic
firmware	=	N/A
ip	=	192.168.100.34
latency	=	0
link	=	yes
multicast	=	yes
wireless	=	IEEE 802.11bgn
resources:	
irq	:	17
ioport	:	2000(size=256)
memory	:	c0500000-c0503fff


---

### Post by ahallubuntu on 2012-11-10
You may have to blacklist the existing driver so the new one will be used instead.

Go back to a terminal and type

```
sudo modprobe -r rtl8192ce
```

then go back and re-build the driver like you did the first time (should be a bit quicker this time).

If it now works better, you can blacklist the old driver permanently and always load the new one.

First, type "lsmod" and look for the name of the new driver (might be 8192ce or something close).

Then add just the name of the module to the end of the file /etc/modules .

Finally, blacklist the old driver permanently.  Add this line:

```
blacklist rtl8192ce
```

to the end of the file /etc/modprobe.d/blacklist.conf 

You need to be "sudo" to edit these two files.

There's some chance that the new module is also called "rtl8192ce"  When I built the Realtek driver for my 8192CU USB card, the old and new modules had different names.

---

### Post by apeisa on 2012-11-10
Thanks for your help. Did like you suggested. After blacklisting my wifi dropped out. Then run the sudo make and sudo make install. It did run some text, but after that nothing happened (wifi didn't come back up).

So maybe they have same name? Or for some reason it didn't install properly?

I did modprobe rtl8192ce to get back online.

---

### Post by apeisa on 2012-11-10
Thanks for your help. Did like you suggested. After blacklisting my wifi dropped out. Then run the sudo make and sudo make install. It did run some text, but after that nothing happened (wifi didn't come back up).

So maybe they have same name? Or for some reason it didn't install properly?

I did modprobe rtl8192ce to get back online.

---

### Post by ahallubuntu on 2012-11-10
Are you sure there weren't any errors in the build process?  If it worked correctly, I think you'd see the name of the module it has just built listed near the end of the process...

---

### Post by apeisa on 2012-11-10
I am not sure. I did extract the package to another location and run sudo make again and this is the output:

> 
make -C /lib/modules/3.2.0-32-generic/build M=/home/omistaja/Downloads/new/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012 modules
make[1]: Entering directory `/usr/src/linux-headers-3.2.0-32-generic'
  CC [M]  /home/omistaja/Downloads/new/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/base.o
  CC [M]  /home/omistaja/Downloads/new/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rc.o
  CC [M]  /home/omistaja/Downloads/new/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/debug.o
  CC [M]  /home/omistaja/Downloads/new/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/regd.o
  CC [M]  /home/omistaja/Downloads/new/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/efuse.o
  CC [M]  /home/omistaja/Downloads/new/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/cam.o
  CC [M]  /home/omistaja/Downloads/new/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/ps.o
  CC [M]  /home/omistaja/Downloads/new/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/core.o
  CC [M]  /home/omistaja/Downloads/new/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/stats.o
  CC [M]  /home/omistaja/Downloads/new/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/pci.o
  LD [M]  /home/omistaja/Downloads/new/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtlwifi.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/omistaja/Downloads/new/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtlwifi.mod.o
  LD [M]  /home/omistaja/Downloads/new/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtlwifi.ko
make[1]: Leaving directory `/usr/src/linux-headers-3.2.0-32-generic'
make[1]: Entering directory `/home/omistaja/Downloads/new/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8192ce'
make -C /lib/modules/3.2.0-32-generic/build M=/home/omistaja/Downloads/new/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8192ce modules
make[2]: Entering directory `/usr/src/linux-headers-3.2.0-32-generic'
  CC [M]  /home/omistaja/Downloads/new/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8192ce/hw.o
  CC [M]  /home/omistaja/Downloads/new/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8192ce/table.o
  CC [M]  /home/omistaja/Downloads/new/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8192ce/sw.o
  CC [M]  /home/omistaja/Downloads/new/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8192ce/trx.o
  CC [M]  /home/omistaja/Downloads/new/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8192ce/led.o
  CC [M]  /home/omistaja/Downloads/new/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8192ce/fw.o
/home/omistaja/Downloads/new/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8192ce/fw.c: In function &#8216;rtl92c_download_fw&#8217;:
/home/omistaja/Downloads/new/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8192ce/fw.c:239:3: warning: format &#8216;%d&#8217; expects argument of type &#8216;int&#8217;, but argument 4 has type &#8216;long unsigned int&#8217; [-Wformat]
  CC [M]  /home/omistaja/Downloads/new/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8192ce/phy.o
  CC [M]  /home/omistaja/Downloads/new/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8192ce/rf.o
  CC [M]  /home/omistaja/Downloads/new/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8192ce/dm.o
  LD [M]  /home/omistaja/Downloads/new/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8192ce/rtl8192ce.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/omistaja/Downloads/new/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8192ce/rtl8192ce.mod.o
  LD [M]  /home/omistaja/Downloads/new/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8192ce/rtl8192ce.ko
make[2]: Leaving directory `/usr/src/linux-headers-3.2.0-32-generic'
make[1]: Leaving directory `/home/omistaja/Downloads/new/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8192ce'
make[1]: Entering directory `/home/omistaja/Downloads/new/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8192se'
make -C /lib/modules/3.2.0-32-generic/build M=/home/omistaja/Downloads/new/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8192se modules
make[2]: Entering directory `/usr/src/linux-headers-3.2.0-32-generic'
  CC [M]  /home/omistaja/Downloads/new/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8192se/hw.o
  CC [M]  /home/omistaja/Downloads/new/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8192se/table.o
  CC [M]  /home/omistaja/Downloads/new/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8192se/sw.o
  CC [M]  /home/omistaja/Downloads/new/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8192se/trx.o
  CC [M]  /home/omistaja/Downloads/new/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8192se/led.o
  CC [M]  /home/omistaja/Downloads/new/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8192se/fw.o
  CC [M]  /home/omistaja/Downloads/new/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8192se/phy.o
  CC [M]  /home/omistaja/Downloads/new/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8192se/rf.o
  CC [M]  /home/omistaja/Downloads/new/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8192se/dm.o
  LD [M]  /home/omistaja/Downloads/new/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8192se/rtl8192se.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/omistaja/Downloads/new/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8192se/rtl8192se.mod.o
  LD [M]  /home/omistaja/Downloads/new/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8192se/rtl8192se.ko
make[2]: Leaving directory `/usr/src/linux-headers-3.2.0-32-generic'
make[1]: Leaving directory `/home/omistaja/Downloads/new/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8192se'
make[1]: Entering directory `/home/omistaja/Downloads/new/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8192de'
make -C /lib/modules/3.2.0-32-generic/build M=/home/omistaja/Downloads/new/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8192de modules
make[2]: Entering directory `/usr/src/linux-headers-3.2.0-32-generic'
  CC [M]  /home/omistaja/Downloads/new/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8192de/hw.o
  CC [M]  /home/omistaja/Downloads/new/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8192de/table.o
  CC [M]  /home/omistaja/Downloads/new/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8192de/sw.o
  CC [M]  /home/omistaja/Downloads/new/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8192de/trx.o
  CC [M]  /home/omistaja/Downloads/new/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8192de/led.o
  CC [M]  /home/omistaja/Downloads/new/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8192de/fw.o
  CC [M]  /home/omistaja/Downloads/new/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8192de/phy.o
/home/omistaja/Downloads/new/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8192de/phy.c: In function &#8216;rtl92d_phy_reset_iqk_result&#8217;:
/home/omistaja/Downloads/new/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8192de/phy.c:3002:2: warning: format &#8216;%d&#8217; expects argument of type &#8216;int&#8217;, but argument 2 has type &#8216;long unsigned int&#8217; [-Wformat]
  CC [M]  /home/omistaja/Downloads/new/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8192de/rf.o
  CC [M]  /home/omistaja/Downloads/new/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8192de/dm.o
  LD [M]  /home/omistaja/Downloads/new/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8192de/rtl8192de.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/omistaja/Downloads/new/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8192de/rtl8192de.mod.o
  LD [M]  /home/omistaja/Downloads/new/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8192de/rtl8192de.ko
make[2]: Leaving directory `/usr/src/linux-headers-3.2.0-32-generic'
make[1]: Leaving directory `/home/omistaja/Downloads/new/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8192de'
make[1]: Entering directory `/home/omistaja/Downloads/new/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8723e'
make -C /lib/modules/3.2.0-32-generic/build M=/home/omistaja/Downloads/new/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8723e modules
make[2]: Entering directory `/usr/src/linux-headers-3.2.0-32-generic'
  CC [M]  /home/omistaja/Downloads/new/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8723e/hw.o
  CC [M]  /home/omistaja/Downloads/new/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8723e/table.o
  CC [M]  /home/omistaja/Downloads/new/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8723e/sw.o
  CC [M]  /home/omistaja/Downloads/new/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8723e/trx.o
  CC [M]  /home/omistaja/Downloads/new/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8723e/led.o
  CC [M]  /home/omistaja/Downloads/new/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8723e/fw.o
/home/omistaja/Downloads/new/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8723e/fw.c: In function &#8216;rtl8723e_download_fw&#8217;:
/home/omistaja/Downloads/new/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8723e/fw.c:204:3: warning: format &#8216;%d&#8217; expects argument of type &#8216;int&#8217;, but argument 4 has type &#8216;long unsigned int&#8217; [-Wformat]
  CC [M]  /home/omistaja/Downloads/new/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8723e/phy.o
  CC [M]  /home/omistaja/Downloads/new/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8723e/rf.o
  CC [M]  /home/omistaja/Downloads/new/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8723e/dm.o
  CC [M]  /home/omistaja/Downloads/new/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8723e/pwrseq.o
  CC [M]  /home/omistaja/Downloads/new/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8723e/pwrseqcmd.o
  CC [M]  /home/omistaja/Downloads/new/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8723e/hal_btc.o
  CC [M]  /home/omistaja/Downloads/new/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8723e/hal_bt_coexist.o
  LD [M]  /home/omistaja/Downloads/new/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8723e/rtl8723e.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/omistaja/Downloads/new/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8723e/rtl8723e.mod.o
  LD [M]  /home/omistaja/Downloads/new/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8723e/rtl8723e.ko
make[2]: Leaving directory `/usr/src/linux-headers-3.2.0-32-generic'
make[1]: Leaving directory `/home/omistaja/Downloads/new/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8723e'



---

### Post by ahallubuntu on 2012-11-10
After the make, did you do "make install" as well?

---

### Post by apeisa on 2012-11-10
Yep. This is the output:

> make -C /lib/modules/3.2.0-32-generic/build M=/home/omistaja/Downloads/new/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012 modules
make[1]: Entering directory `/usr/src/linux-headers-3.2.0-32-generic'
  Building modules, stage 2.
  MODPOST 1 modules
make[1]: Leaving directory `/usr/src/linux-headers-3.2.0-32-generic'
make[1]: Entering directory `/home/omistaja/Downloads/new/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8192ce'
make -C /lib/modules/3.2.0-32-generic/build M=/home/omistaja/Downloads/new/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8192ce modules
make[2]: Entering directory `/usr/src/linux-headers-3.2.0-32-generic'
  Building modules, stage 2.
  MODPOST 1 modules
make[2]: Leaving directory `/usr/src/linux-headers-3.2.0-32-generic'
make[1]: Leaving directory `/home/omistaja/Downloads/new/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8192ce'
make[1]: Entering directory `/home/omistaja/Downloads/new/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8192se'
make -C /lib/modules/3.2.0-32-generic/build M=/home/omistaja/Downloads/new/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8192se modules
make[2]: Entering directory `/usr/src/linux-headers-3.2.0-32-generic'
  Building modules, stage 2.
  MODPOST 1 modules
make[2]: Leaving directory `/usr/src/linux-headers-3.2.0-32-generic'
make[1]: Leaving directory `/home/omistaja/Downloads/new/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8192se'
make[1]: Entering directory `/home/omistaja/Downloads/new/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8192de'
make -C /lib/modules/3.2.0-32-generic/build M=/home/omistaja/Downloads/new/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8192de modules
make[2]: Entering directory `/usr/src/linux-headers-3.2.0-32-generic'
  Building modules, stage 2.
  MODPOST 1 modules
make[2]: Leaving directory `/usr/src/linux-headers-3.2.0-32-generic'
make[1]: Leaving directory `/home/omistaja/Downloads/new/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8192de'
make[1]: Entering directory `/home/omistaja/Downloads/new/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8723e'
make -C /lib/modules/3.2.0-32-generic/build M=/home/omistaja/Downloads/new/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8723e modules
make[2]: Entering directory `/usr/src/linux-headers-3.2.0-32-generic'
  Building modules, stage 2.
  MODPOST 1 modules
make[2]: Leaving directory `/usr/src/linux-headers-3.2.0-32-generic'
make[1]: Leaving directory `/home/omistaja/Downloads/new/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8723e'
find /lib/modules/3.2.0-32-generic -name "r8192se_*.ko" -exec rm {} \;
find /lib/modules/3.2.0-32-generic -name "r8192ce_*.ko" -exec rm {} \;
find /lib/modules/3.2.0-32-generic -name "r8723e_*.ko" -exec rm {} \;


---

### Post by apeisa on 2012-11-11
Any ideas on what to try next? Has anyone succesfully installed those realtek drivers?

---

### Post by apeisa on 2012-11-11
I found the wireless_script from these forums, I run it and this is the output:

> 

*************** info trace ****************



**** uname -a ****


Linux omistaja-PBL00 3.2.0-32-generic #51-Ubuntu SMP Wed Sep 26 21:33:09 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux


**** lsb-release ****


DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04.1 LTS"


**** lspci ****


01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 06)
	Subsystem: COMPAL Electronics Inc Device [14c0:0056]
	Kernel driver in use: r8169
--
02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter [10ec:8176] (rev 01)
	Subsystem: Realtek Semiconductor Co., Ltd. Device [10ec:9176]
	Kernel driver in use: rtl8192ce


**** lsusb ****


Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 003: ID 0bda:58e8 Realtek Semiconductor Corp. 
Bus 001 Device 004: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)


**** iwconfig ****


wlan0     IEEE 802.11bgn  ESSID:"Koti160"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: <MAC address removed>   
          Bit Rate=7.2 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=12/70  Signal level=-98 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:54   Missed beacon:0



**** rfkill ****


3: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
4: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no


**** lsmod ****


Module                  Size  Used by
ums_realtek            18248  0 
uas                    18180  0 
usb_storage            49198  1 ums_realtek
rtl8192ce             137478  0 
rtlwifi               118749  1 rtl8192ce
mac80211              506816  2 rtl8192ce,rtlwifi
cfg80211              205544  2 rtlwifi,mac80211
joydev                 17693  0 
snd_hda_codec_hdmi     32474  1 
snd_hda_codec_realtek   224173  1 
parport_pc             32866  0 
ppdev                  17113  0 
rfcomm                 47604  12 
bnep                   18281  2 
arc4                   12529  2 
snd_hda_intel          33773  3 
snd_hda_codec         127706  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                97188  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30748  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
uvcvideo               72627  0 
psmouse                97443  0 
videodev               98259  1 uvcvideo
btusb                  18288  2 
snd                    78855  16 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
serio_raw              13211  0 
v4l2_compat_ioctl32    17128  1 videodev
bluetooth             180104  23 rfcomm,bnep,btusb
i915                  473298  4 
soundcore              15091  1 snd
drm_kms_helper         46978  1 i915
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
drm                   241921  5 i915,drm_kms_helper
mei                    41616  0 
i2c_algo_bit           13423  1 i915
video                  19596  1 i915
mac_hid                13253  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
r8169                  62099  0 


**** nm-tool ****



NetworkManager Tool

State: connected (global)

- Device: wlan0  [Koti160] -----------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8192ce
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>

  Capabilities:
    Speed:           7 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    *Koti160:        Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 30 WPA

  IPv4 Settings:
    Address:         192.168.100.34
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.100.1

    DNS:             192.168.100.1


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        <MAC address removed>

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off




**** NetworkManager.state ****



[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true


**** NetworkManager.conf ****


[main]
plugins=ifupdown,keyfile
dns=dnsmasq

[ifupdown]
managed=false


**** NetworkManager.conf-10.04 ****




**** interfaces ****


auto lo
iface lo inet loopback



**** iwlist ****


wlan0     Scan completed :
          Cell 01 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=62/70  Signal level=-48 dBm  
                    Encryption key:on
                    ESSID:"Koti160"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000002140a58180
                    Extra: Last beacon: 728ms ago
                    IE: Unknown: 00074B6F7469313630
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030101
                    IE: Unknown: 0706555320010B1B
                    IE: Unknown: 200100
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1AAC011BFF7F000000000000000000000000000000000000000000
                    IE: Unknown: 331AAC011BFF7F000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601080400000000000000000000000000000000000000
                    IE: Unknown: 341601080400000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101810003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DDB90050F204104A0001101044000102103B000103104700107F93053C0000000000000000000000101021000E4D666772204E616D6520486572651023000F4D6F64656C204E616D652048657265102400114D6F64656C204E756D62657220486572651042001253657269616C204E756D62657220486572651054000800060050F20400021011000F456C697361204B6F7469626F6B7369100800020082103C000103104900140024E26002000101600000020001600100020001



**** resolv ****


# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.0.1
search Elisa


**** blacklist.conf ****


# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp

# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac
# blacklist rtl8192ce


**** dmesg ****


[ 1426.850994] wlan0: Connection to AP <MAC address removed> lost.
[ 1428.135791] wlan0: authenticate with <MAC address removed> (try 1)
[ 1428.139646] wlan0: authenticated
[ 1428.139803] wlan0: associate with <MAC address removed> (try 1)
[ 1428.337333] wlan0: associate with <MAC address removed> (try 2)
[ 1428.537113] wlan0: associate with <MAC address removed> (try 3)
[ 1428.736798] wlan0: association with <MAC address removed> timed out
[ 1434.472999] wlan0: authenticate with <MAC address removed> (try 1)
[ 1434.670243] wlan0: authenticate with <MAC address removed> (try 2)
[ 1434.870128] wlan0: authenticate with <MAC address removed> (try 3)
[ 1435.069826] wlan0: authentication with <MAC address removed> timed out
[ 1440.797881] wlan0: authenticate with <MAC address removed> (try 1)
[ 1440.995297] wlan0: authenticate with <MAC address removed> (try 2)
[ 1441.195086] wlan0: authenticate with <MAC address removed> (try 3)
[ 1441.394914] wlan0: authentication with <MAC address removed> timed out
[ 1442.675340] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1447.194967] wlan0: authenticate with <MAC address removed> (try 1)
[ 1447.396301] wlan0: authenticate with <MAC address removed> (try 2)
[ 1447.596078] wlan0: authenticate with <MAC address removed> (try 3)
[ 1447.795848] wlan0: authentication with <MAC address removed> timed out
[ 1453.559976] wlan0: authenticate with <MAC address removed> (try 1)
[ 1453.757282] wlan0: authenticate with <MAC address removed> (try 2)
[ 1453.957131] wlan0: authenticate with <MAC address removed> (try 3)
[ 1454.156840] wlan0: authentication with <MAC address removed> timed out
[ 1459.884931] wlan0: authenticate with <MAC address removed> (try 1)
[ 1460.082362] wlan0: authenticate with <MAC address removed> (try 2)
[ 1460.282126] wlan0: authenticate with <MAC address removed> (try 3)
[ 1460.481887] wlan0: authentication with <MAC address removed> timed out
[ 1466.257897] wlan0: authenticate with <MAC address removed> (try 1)
[ 1466.455355] wlan0: authenticate with <MAC address removed> (try 2)
[ 1466.655177] wlan0: authenticate with <MAC address removed> (try 3)
[ 1466.855003] wlan0: authentication with <MAC address removed> timed out
[ 1472.587084] wlan0: authenticate with <MAC address removed> (try 1)
[ 1472.784492] wlan0: authenticate with <MAC address removed> (try 2)
[ 1472.984181] wlan0: authenticate with <MAC address removed> (try 3)
[ 1473.183978] wlan0: authentication with <MAC address removed> timed out
[ 1478.912212] wlan0: authenticate with <MAC address removed> (try 1)
[ 1479.109450] wlan0: authenticate with <MAC address removed> (try 2)
[ 1479.309229] wlan0: authenticate with <MAC address removed> (try 3)
[ 1479.508991] wlan0: authentication with <MAC address removed> timed out
[ 1485.241165] wlan0: authenticate with <MAC address removed> (try 1)
[ 1485.438532] wlan0: authenticate with <MAC address removed> (try 2)
[ 1485.638251] wlan0: authenticate with <MAC address removed> (try 3)
[ 1485.644547] wlan0: authenticated
[ 1485.644761] wlan0: associate with <MAC address removed> (try 1)
[ 1485.842092] wlan0: associate with <MAC address removed> (try 2)
[ 1486.041835] wlan0: associate with <MAC address removed> (try 3)
[ 1486.241593] wlan0: association with <MAC address removed> timed out
[ 1492.005751] wlan0: authenticate with <MAC address removed> (try 1)
[ 1492.203114] wlan0: authenticate with <MAC address removed> (try 2)
[ 1492.402844] wlan0: authenticate with <MAC address removed> (try 3)
[ 1492.602624] wlan0: authentication with <MAC address removed> timed out
[ 1498.330867] wlan0: authenticate with <MAC address removed> (try 1)
[ 1498.528112] wlan0: authenticate with <MAC address removed> (try 2)
[ 1498.728002] wlan0: authenticate with <MAC address removed> (try 3)
[ 1498.927768] wlan0: authentication with <MAC address removed> timed out
[ 1517.075082] wlan0: authenticate with <MAC address removed> (try 1)
[ 1517.271516] wlan0: authenticate with <MAC address removed> (try 2)
[ 1517.471298] wlan0: authenticate with <MAC address removed> (try 3)
[ 1517.671051] wlan0: authentication with <MAC address removed> timed out
[ 1523.423106] wlan0: authenticate with <MAC address removed> (try 1)
[ 1523.426552] wlan0: authenticated
[ 1523.426732] wlan0: associate with <MAC address removed> (try 1)
[ 1523.624518] wlan0: associate with <MAC address removed> (try 2)
[ 1523.632221] wlan0: RX ReassocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[ 1523.632225] wlan0: associated
[ 1523.632228] wlan0: No basic rates in AssocResp. Using min supported rate instead.
[ 1523.643365] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 1525.490358] wlan0: deauthenticated from <MAC address removed> (Reason: 6)
[ 1526.667587] wlan0: authenticate with <MAC address removed> (try 1)
[ 1526.670446] wlan0: authenticated
[ 1526.670710] wlan0: associate with <MAC address removed> (try 1)
[ 1526.676844] wlan0: RX ReassocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[ 1526.676848] wlan0: associated
[ 1526.676852] wlan0: No basic rates in AssocResp. Using min supported rate instead.
[ 1535.945582] wlan0: deauthenticated from <MAC address removed> (Reason: 6)
[ 1537.132085] wlan0: authenticate with <MAC address removed> (try 1)
[ 1537.134452] wlan0: authenticated
[ 1537.134608] wlan0: associate with <MAC address removed> (try 1)
[ 1537.138458] wlan0: RX ReassocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[ 1537.138462] wlan0: associated
[ 1537.138465] wlan0: No basic rates in AssocResp. Using min supported rate instead.
[ 1546.406094] wlan0: deauthenticated from <MAC address removed> (Reason: 6)
[ 1547.624675] wlan0: authenticate with <MAC address removed> (try 1)
[ 1547.627521] wlan0: authenticated
[ 1547.627939] wlan0: associate with <MAC address removed> (try 1)
[ 1547.632014] wlan0: RX ReassocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[ 1547.632024] wlan0: associated
[ 1547.632032] wlan0: No basic rates in AssocResp. Using min supported rate instead.
[ 1550.873686] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 1551.656230] wlan0: authenticate with <MAC address removed> (try 1)
[ 1551.659739] wlan0: authenticated
[ 1551.660072] wlan0: associate with <MAC address removed> (try 1)
[ 1551.665925] wlan0: RX ReassocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[ 1551.665938] wlan0: associated
[ 1551.665949] wlan0: No basic rates in AssocResp. Using min supported rate instead.
[ 1560.986046] wlan0: deauthenticated from <MAC address removed> (Reason: 6)
[ 1562.188567] wlan0: authenticate with <MAC address removed> (try 1)
[ 1562.191606] wlan0: authenticated
[ 1562.191753] wlan0: associate with <MAC address removed> (try 1)
[ 1562.196554] wlan0: RX ReassocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[ 1562.196559] wlan0: associated
[ 1562.196564] wlan0: No basic rates in AssocResp. Using min supported rate instead.
[ 1571.466639] wlan0: deauthenticated from <MAC address removed> (Reason: 6)
[ 1572.661953] wlan0: authenticate with <MAC address removed> (try 1)
[ 1572.664044] wlan0: authenticated
[ 1572.664202] wlan0: associate with <MAC address removed> (try 1)
[ 1572.668088] wlan0: RX ReassocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[ 1572.668093] wlan0: associated
[ 1572.668097] wlan0: No basic rates in AssocResp. Using min supported rate instead.
[ 1581.938637] wlan0: deauthenticated from <MAC address removed> (Reason: 6)
[ 1583.157550] wlan0: authenticate with <MAC address removed> (try 1)
[ 1583.159790] wlan0: authenticated
[ 1583.160195] wlan0: associate with <MAC address removed> (try 1)
[ 1583.164176] wlan0: RX ReassocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[ 1583.164186] wlan0: associated
[ 1583.164194] wlan0: No basic rates in AssocResp. Using min supported rate instead.
[ 1592.431647] wlan0: deauthenticated from <MAC address removed> (Reason: 6)
[ 1593.653894] wlan0: authenticate with <MAC address removed> (try 1)
[ 1593.656056] wlan0: authenticated
[ 1593.656321] wlan0: associate with <MAC address removed> (try 1)
[ 1593.660275] wlan0: RX ReassocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[ 1593.660280] wlan0: associated
[ 1593.660283] wlan0: No basic rates in AssocResp. Using min supported rate instead.
[ 1602.931771] wlan0: deauthenticated from <MAC address removed> (Reason: 6)
[ 1604.142430] wlan0: authenticate with <MAC address removed> (try 1)
[ 1604.144897] wlan0: authenticated
[ 1604.145157] wlan0: associate with <MAC address removed> (try 1)
[ 1604.149017] wlan0: RX ReassocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[ 1604.149027] wlan0: associated
[ 1604.149037] wlan0: No basic rates in AssocResp. Using min supported rate instead.
[ 1611.230786] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 1617.459991] wlan0: authenticate with <MAC address removed> (try 1)
[ 1617.462335] wlan0: authenticated
[ 1617.462657] wlan0: associate with <MAC address removed> (try 1)
[ 1617.466881] wlan0: RX ReassocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[ 1617.466891] wlan0: associated
[ 1617.466899] wlan0: No basic rates in AssocResp. Using min supported rate instead.
[ 1626.729937] wlan0: deauthenticated from <MAC address removed> (Reason: 6)
[ 1627.937256] wlan0: authenticate with <MAC address removed> (try 1)
[ 1627.939676] wlan0: authenticated
[ 1627.940011] wlan0: associate with <MAC address removed> (try 1)
[ 1627.947392] wlan0: RX ReassocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[ 1627.947398] wlan0: associated
[ 1627.947402] wlan0: No basic rates in AssocResp. Using min supported rate instead.
[ 1637.210057] wlan0: deauthenticated from <MAC address removed> (Reason: 6)
[ 1638.422237] wlan0: authenticate with <MAC address removed> (try 1)
[ 1638.424379] wlan0: authenticated
[ 1638.424642] wlan0: associate with <MAC address removed> (try 1)
[ 1638.428688] wlan0: RX ReassocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[ 1638.428698] wlan0: associated
[ 1638.428706] wlan0: No basic rates in AssocResp. Using min supported rate instead.
[ 1647.698730] wlan0: deauthenticated from <MAC address removed> (Reason: 6)
[ 1648.905375] wlan0: authenticate with <MAC address removed> (try 1)
[ 1648.907681] wlan0: authenticated
[ 1648.908012] wlan0: associate with <MAC address removed> (try 1)
[ 1648.912067] wlan0: RX ReassocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[ 1648.912077] wlan0: associated
[ 1648.912084] wlan0: No basic rates in AssocResp. Using min supported rate instead.
[ 1658.914510] wlan0: disassociating from <MAC address removed> by local choice (reason=3)
[ 1658.954691] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 1659.685582] wlan0: authenticate with <MAC address removed> (try 1)
[ 1659.688009] wlan0: authenticated
[ 1659.688365] wlan0: associate with <MAC address removed> (try 1)
[ 1659.692350] wlan0: RX ReassocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[ 1659.692361] wlan0: associated
[ 1659.692369] wlan0: No basic rates in AssocResp. Using min supported rate instead.
[ 1668.192263] wlan0: deauthenticated from <MAC address removed> (Reason: 6)
[ 1669.383269] wlan0: authenticate with <MAC address removed> (try 1)
[ 1669.385402] wlan0: authenticated
[ 1669.385738] wlan0: associate with <MAC address removed> (try 1)
[ 1669.390192] wlan0: RX ReassocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[ 1669.390196] wlan0: associated
[ 1669.390199] wlan0: No basic rates in AssocResp. Using min supported rate instead.
[ 1676.158931] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 1682.892059] wlan0: authenticate with <MAC address removed> (try 1)
[ 1682.894233] wlan0: authenticated
[ 1682.894564] wlan0: associate with <MAC address removed> (try 1)
[ 1682.898587] wlan0: RX ReassocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[ 1682.898598] wlan0: associated
[ 1682.898605] wlan0: No basic rates in AssocResp. Using min supported rate instead.
[ 1692.170124] wlan0: deauthenticated from <MAC address removed> (Reason: 6)
[ 1693.032918] wlan0: authenticate with <MAC address removed> (try 1)
[ 1693.036032] wlan0: authenticated
[ 1693.036361] wlan0: associate with <MAC address removed> (try 1)
[ 1693.040361] wlan0: RX ReassocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[ 1693.040371] wlan0: associated
[ 1693.040379] wlan0: No basic rates in AssocResp. Using min supported rate instead.
[ 1702.178611] wlan0: deauthenticated from <MAC address removed> (Reason: 6)
[ 1703.401553] wlan0: authenticate with <MAC address removed> (try 1)
[ 1703.403719] wlan0: authenticated
[ 1703.404170] wlan0: associate with <MAC address removed> (try 1)
[ 1703.408111] wlan0: RX ReassocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[ 1703.408115] wlan0: associated
[ 1703.408118] wlan0: No basic rates in AssocResp. Using min supported rate instead.
[ 1712.679450] wlan0: deauthenticated from <MAC address removed> (Reason: 6)
[ 1713.866059] wlan0: authenticate with <MAC address removed> (try 1)
[ 1713.870161] wlan0: authenticated
[ 1713.870597] wlan0: associate with <MAC address removed> (try 1)
[ 1713.874574] wlan0: RX ReassocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[ 1713.874584] wlan0: associated
[ 1713.874591] wlan0: No basic rates in AssocResp. Using min supported rate instead.
[ 1723.143654] wlan0: deauthenticated from <MAC address removed> (Reason: 6)
[ 1724.358532] wlan0: authenticate with <MAC address removed> (try 1)
[ 1724.360742] wlan0: authenticated
[ 1724.361223] wlan0: associate with <MAC address removed> (try 1)
[ 1724.365166] wlan0: RX ReassocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[ 1724.365176] wlan0: associated
[ 1724.365183] wlan0: No basic rates in AssocResp. Using min supported rate instead.
[ 1733.628154] wlan0: deauthenticated from <MAC address removed> (Reason: 6)
[ 1734.835020] wlan0: authenticate with <MAC address removed> (try 1)
[ 1734.839934] wlan0: authenticated
[ 1734.840140] wlan0: associate with <MAC address removed> (try 1)
[ 1734.844084] wlan0: RX ReassocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[ 1734.844094] wlan0: associated
[ 1734.844102] wlan0: No basic rates in AssocResp. Using min supported rate instead.
[ 1742.086787] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 1802.700486] wlan0: authenticate with <MAC address removed> (try 1)
[ 1802.704681] wlan0: authenticated
[ 1802.705443] wlan0: associate with <MAC address removed> (try 1)
[ 1802.709428] wlan0: RX ReassocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[ 1802.709438] wlan0: associated
[ 1802.709445] wlan0: No basic rates in AssocResp. Using min supported rate instead.
[ 1813.721770] wlan0: no IPv6 routers present
[ 1825.992119] wlan0: Connection to AP <MAC address removed> lost.
[ 1827.173793] wlan0: authenticate with <MAC address removed> (try 1)
[ 1827.176045] wlan0: authenticated
[ 1827.176424] wlan0: associate with <MAC address removed> (try 1)
[ 1827.180402] wlan0: RX ReassocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[ 1827.180412] wlan0: associated
[ 1827.180419] wlan0: No basic rates in AssocResp. Using min supported rate instead.
[ 1838.456610] wlan0: Connection to AP <MAC address removed> lost.
[ 1839.642301] wlan0: authenticate with <MAC address removed> (try 1)
[ 1839.644642] wlan0: authenticated
[ 1839.644974] wlan0: associate with <MAC address removed> (try 1)
[ 1839.648924] wlan0: RX ReassocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[ 1839.648934] wlan0: associated
[ 1839.648942] wlan0: No basic rates in AssocResp. Using min supported rate instead.
[ 1848.922348] wlan0: Connection to AP <MAC address removed> lost.
[ 1850.159326] wlan0: authenticate with <MAC address removed> (try 1)
[ 1850.356573] wlan0: authenticate with <MAC address removed> (try 2)
[ 1850.556402] wlan0: authenticate with <MAC address removed> (try 3)
[ 1850.756139] wlan0: authentication with <MAC address removed> timed out
[ 1856.488161] wlan0: authenticate with <MAC address removed> (try 1)
[ 1856.685618] wlan0: authenticate with <MAC address removed> (try 2)
[ 1856.885455] wlan0: authenticate with <MAC address removed> (try 3)
[ 1857.085179] wlan0: authentication with <MAC address removed> timed out
[ 1862.817248] wlan0: authenticate with <MAC address removed> (try 1)
[ 1863.014640] wlan0: authenticate with <MAC address removed> (try 2)
[ 1863.214491] wlan0: authenticate with <MAC address removed> (try 3)
[ 1863.414197] wlan0: authentication with <MAC address removed> timed out
[ 1864.216774] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1869.150216] wlan0: authenticate with <MAC address removed> (try 1)
[ 1869.347677] wlan0: authenticate with <MAC address removed> (try 2)
[ 1869.547504] wlan0: authenticate with <MAC address removed> (try 3)
[ 1869.747248] wlan0: authentication with <MAC address removed> timed out
[ 1875.547400] wlan0: authenticate with <MAC address removed> (try 1)
[ 1875.744771] wlan0: authenticate with <MAC address removed> (try 2)
[ 1875.944546] wlan0: authenticate with <MAC address removed> (try 3)
[ 1876.144334] wlan0: authentication with <MAC address removed> timed out
[ 1881.880372] wlan0: authenticate with <MAC address removed> (try 1)
[ 1882.077806] wlan0: authenticate with <MAC address removed> (try 2)
[ 1882.277553] wlan0: authenticate with <MAC address removed> (try 3)
[ 1882.477320] wlan0: authentication with <MAC address removed> timed out
[ 1888.205525] wlan0: authenticate with <MAC address removed> (try 1)
[ 1888.402820] wlan0: authenticate with <MAC address removed> (try 2)
[ 1888.602522] wlan0: authenticate with <MAC address removed> (try 3)
[ 1888.802310] wlan0: authentication with <MAC address removed> timed out
[ 1894.538553] wlan0: authenticate with <MAC address removed> (try 1)
[ 1894.735910] wlan0: authenticate with <MAC address removed> (try 2)
[ 1894.935667] wlan0: authenticate with <MAC address removed> (try 3)
[ 1895.135505] wlan0: authentication with <MAC address removed> timed out
[ 1900.867663] wlan0: authenticate with <MAC address removed> (try 1)
[ 1900.873571] wlan0: authenticated
[ 1900.874029] wlan0: associate with <MAC address removed> (try 1)
[ 1900.889336] wlan0: RX ReassocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[ 1900.889347] wlan0: associated
[ 1900.889355] wlan0: No basic rates in AssocResp. Using min supported rate instead.
[ 1900.902631] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 1907.557979] wlan0: Connection to AP <MAC address removed> lost.
[ 1908.755284] wlan0: authenticate with <MAC address removed> (try 1)
[ 1908.757396] wlan0: authenticated
[ 1908.757545] wlan0: associate with <MAC address removed> (try 1)
[ 1908.761443] wlan0: RX ReassocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[ 1908.761457] wlan0: associated
[ 1908.761468] wlan0: No basic rates in AssocResp. Using min supported rate instead.
[ 1919.204889] wlan0: no IPv6 routers present
[ 1930.038941] wlan0: Connection to AP <MAC address removed> lost.
[ 1931.227188] wlan0: authenticate with <MAC address removed> (try 1)
[ 1931.229301] wlan0: authenticated
[ 1931.229467] wlan0: associate with <MAC address removed> (try 1)
[ 1931.233329] wlan0: RX ReassocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[ 1931.233333] wlan0: associated
[ 1931.233336] wlan0: No basic rates in AssocResp. Using min supported rate instead.
[ 1938.497402] wlan0: Connection to AP <MAC address removed> lost.
[ 1939.685869] wlan0: authenticate with <MAC address removed> (try 1)
[ 1939.688092] wlan0: authenticated
[ 1939.688371] wlan0: associate with <MAC address removed> (try 1)
[ 1939.692223] wlan0: RX ReassocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[ 1939.692232] wlan0: associated
[ 1939.692239] wlan0: No basic rates in AssocResp. Using min supported rate instead.
[ 1952.954290] wlan0: Connection to AP <MAC address removed> lost.
[ 1954.142844] wlan0: authenticate with <MAC address removed> (try 1)
[ 1954.145367] wlan0: authenticated
[ 1954.145798] wlan0: associate with <MAC address removed> (try 1)
[ 1954.149801] wlan0: RX ReassocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[ 1954.149811] wlan0: associated
[ 1954.149819] wlan0: No basic rates in AssocResp. Using min supported rate instead.
[ 1963.414208] wlan0: Connection to AP <MAC address removed> lost.
[ 1964.267599] wlan0: authenticate with <MAC address removed> (try 1)
[ 1964.464878] wlan0: authenticate with <MAC address removed> (try 2)
[ 1964.664656] wlan0: authenticate with <MAC address removed> (try 3)
[ 1964.864441] wlan0: authentication with <MAC address removed> timed out
[ 1970.596396] wlan0: authenticate with <MAC address removed> (try 1)
[ 1970.600689] wlan0: authenticated
[ 1970.600828] wlan0: associate with <MAC address removed> (try 1)
[ 1970.604780] wlan0: RX ReassocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[ 1970.604789] wlan0: associated
[ 1970.604797] wlan0: No basic rates in AssocResp. Using min supported rate instead.
[ 1991.439254] wlan0: Connection to AP <MAC address removed> lost.
[ 1992.728053] wlan0: authenticate with <MAC address removed> (try 1)
[ 1992.730171] wlan0: authenticated
[ 1992.730430] wlan0: associate with <MAC address removed> (try 1)
[ 1992.735965] wlan0: RX ReassocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[ 1992.735970] wlan0: associated
[ 1992.735973] wlan0: No basic rates in AssocResp. Using min supported rate instead.
[ 2002.003636] wlan0: Connection to AP <MAC address removed> lost.
[ 2003.196587] wlan0: authenticate with <MAC address removed> (try 1)
[ 2003.394079] wlan0: authenticate with <MAC address removed> (try 2)
[ 2003.396382] wlan0: authenticated
[ 2003.396952] wlan0: associate with <MAC address removed> (try 1)
[ 2003.401023] wlan0: RX ReassocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[ 2003.401033] wlan0: associated
[ 2003.401041] wlan0: No basic rates in AssocResp. Using min supported rate instead.
[ 2058.513628] wlan0: Connection to AP <MAC address removed> lost.
[ 2059.774379] wlan0: authenticate with <MAC address removed> (try 1)
[ 2059.776520] wlan0: authenticated
[ 2059.776719] wlan0: associate with <MAC address removed> (try 1)
[ 2059.780519] wlan0: RX ReassocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[ 2059.780523] wlan0: associated
[ 2059.780525] wlan0: No basic rates in AssocResp. Using min supported rate instead.
[ 2091.065897] wlan0: Connection to AP <MAC address removed> lost.
[ 2092.302883] wlan0: authenticate with <MAC address removed> (try 1)
[ 2092.305175] wlan0: authenticated
[ 2092.305534] wlan0: associate with <MAC address removed> (try 1)
[ 2092.309620] wlan0: RX ReassocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[ 2092.309630] wlan0: associated
[ 2092.309639] wlan0: No basic rates in AssocResp. Using min supported rate instead.
[ 2107.586829] wlan0: Connection to AP <MAC address removed> lost.
[ 2108.768747] wlan0: authenticate with <MAC address removed> (try 1)
[ 2108.770997] wlan0: authenticated
[ 2108.771302] wlan0: associate with <MAC address removed> (try 1)
[ 2108.775363] wlan0: RX ReassocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[ 2108.775374] wlan0: associated
[ 2108.775382] wlan0: No basic rates in AssocResp. Using min supported rate instead.
[ 2155.669953] wlan0: deauthenticated from <MAC address removed> (Reason: 6)
[ 2156.907985] wlan0: authenticate with <MAC address removed> (try 1)
[ 2156.910141] wlan0: authenticated
[ 2156.910418] wlan0: associate with <MAC address removed> (try 1)
[ 2156.914407] wlan0: RX ReassocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[ 2156.914418] wlan0: associated
[ 2156.914426] wlan0: No basic rates in AssocResp. Using min supported rate instead.
[ 2176.192389] wlan0: Connection to AP <MAC address removed> lost.
[ 2177.441263] wlan0: authenticate with <MAC address removed> (try 1)
[ 2177.443802] wlan0: authenticated
[ 2177.444206] wlan0: associate with <MAC address removed> (try 1)
[ 2177.448285] wlan0: RX ReassocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[ 2177.448296] wlan0: associated
[ 2177.448304] wlan0: No basic rates in AssocResp. Using min supported rate instead.
[ 2302.821089] wlan0: Connection to AP <MAC address removed> lost.
[ 2304.074004] wlan0: authenticate with <MAC address removed> (try 1)
[ 2304.271396] wlan0: authenticate with <MAC address removed> (try 2)
[ 2304.274659] wlan0: authenticated
[ 2304.274904] wlan0: associate with <MAC address removed> (try 1)
[ 2304.471290] wlan0: associate with <MAC address removed> (try 2)
[ 2304.670982] wlan0: associate with <MAC address removed> (try 3)
[ 2304.870786] wlan0: association with <MAC address removed> timed out
[ 2310.610899] wlan0: authenticate with <MAC address removed> (try 1)
[ 2310.613144] wlan0: authenticated
[ 2310.613504] wlan0: associate with <MAC address removed> (try 1)
[ 2310.812235] wlan0: associate with <MAC address removed> (try 2)
[ 2310.816114] wlan0: RX ReassocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[ 2310.816124] wlan0: associated
[ 2310.816132] wlan0: No basic rates in AssocResp. Using min supported rate instead.
[ 2315.435404] wlan0: Connection to AP <MAC address removed> lost.
[ 2316.964056] wlan0: authenticate with <MAC address removed> (try 1)
[ 2317.161260] wlan0: authenticate with <MAC address removed> (try 2)
[ 2317.361051] wlan0: authenticate with <MAC address removed> (try 3)
[ 2317.560817] wlan0: authentication with <MAC address removed> timed out
[ 2323.297129] wlan0: authenticate with <MAC address removed> (try 1)
[ 2323.300135] wlan0: authenticated
[ 2323.300486] wlan0: associate with <MAC address removed> (try 1)
[ 2323.304537] wlan0: RX ReassocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[ 2323.304546] wlan0: associated
[ 2323.304554] wlan0: No basic rates in AssocResp. Using min supported rate instead.
[ 2329.451121] wlan0: Connection to AP <MAC address removed> lost.
[ 2330.636990] wlan0: authenticate with <MAC address removed> (try 1)
[ 2330.639283] wlan0: authenticated
[ 2330.639656] wlan0: associate with <MAC address removed> (try 1)
[ 2330.643696] wlan0: RX ReassocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[ 2330.643706] wlan0: associated
[ 2330.643714] wlan0: No basic rates in AssocResp. Using min supported rate instead.
[ 2361.932172] wlan0: Connection to AP <MAC address removed> lost.
[ 2363.225034] wlan0: authenticate with <MAC address removed> (try 1)
[ 2363.227820] wlan0: authenticated
[ 2363.227965] wlan0: associate with <MAC address removed> (try 1)
[ 2363.231787] wlan0: RX ReassocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[ 2363.231791] wlan0: associated
[ 2363.231794] wlan0: No basic rates in AssocResp. Using min supported rate instead.
[ 2372.500582] wlan0: Connection to AP <MAC address removed> lost.
[ 2373.677512] wlan0: authenticate with <MAC address removed> (try 1)
[ 2373.679749] wlan0: authenticated
[ 2373.679891] wlan0: associate with <MAC address removed> (try 1)
[ 2373.683676] wlan0: RX ReassocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[ 2373.683681] wlan0: associated
[ 2373.683685] wlan0: No basic rates in AssocResp. Using min supported rate instead.
[ 2386.956907] wlan0: Connection to AP <MAC address removed> lost.
[ 2388.141777] wlan0: authenticate with <MAC address removed> (try 1)
[ 2388.144228] wlan0: authenticated
[ 2388.144578] wlan0: associate with <MAC address removed> (try 1)
[ 2388.148598] wlan0: RX ReassocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[ 2388.148608] wlan0: associated
[ 2388.148615] wlan0: No basic rates in AssocResp. Using min supported rate instead.
[ 2399.418991] wlan0: Connection to AP <MAC address removed> lost.
[ 2400.627824] wlan0: authenticate with <MAC address removed> (try 1)
[ 2400.630536] wlan0: authenticated
[ 2400.630678] wlan0: associate with <MAC address removed> (try 1)
[ 2400.829406] wlan0: associate with <MAC address removed> (try 2)
[ 2400.841092] wlan0: RX ReassocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[ 2400.841103] wlan0: associated
[ 2400.841112] wlan0: No basic rates in AssocResp. Using min supported rate instead.
[ 2407.988856] wlan0: Connection to AP <MAC address removed> lost.
[ 2409.166510] wlan0: authenticate with <MAC address removed> (try 1)
[ 2409.168685] wlan0: authenticated
[ 2409.168824] wlan0: associate with <MAC address removed> (try 1)
[ 2409.176400] wlan0: RX ReassocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[ 2409.176404] wlan0: associated
[ 2409.176407] wlan0: No basic rates in AssocResp. Using min supported rate instead.
[ 2416.527332] wlan0: Connection to AP <MAC address removed> lost.
[ 2417.745128] wlan0: authenticate with <MAC address removed> (try 1)
[ 2417.750848] wlan0: authenticated
[ 2417.751381] wlan0: associate with <MAC address removed> (try 1)
[ 2417.765236] wlan0: RX ReassocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[ 2417.765245] wlan0: associated
[ 2417.765253] wlan0: No basic rates in AssocResp. Using min supported rate instead.
[ 2493.159916] wlan0: Connection to AP <MAC address removed> lost.
[ 2494.405083] wlan0: authenticate with <MAC address removed> (try 1)
[ 2494.407930] wlan0: authenticated
[ 2494.408376] wlan0: associate with <MAC address removed> (try 1)
[ 2494.416851] wlan0: RX ReassocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[ 2494.416861] wlan0: associated
[ 2494.416869] wlan0: No basic rates in AssocResp. Using min supported rate instead.
[ 2501.762521] wlan0: Connection to AP <MAC address removed> lost.
[ 2502.947589] wlan0: authenticate with <MAC address removed> (try 1)
[ 2502.952323] wlan0: authenticated
[ 2502.952698] wlan0: associate with <MAC address removed> (try 1)
[ 2502.958052] wlan0: RX ReassocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[ 2502.958064] wlan0: associated
[ 2502.958074] wlan0: No basic rates in AssocResp. Using min supported rate instead.
[ 2518.228618] wlan0: Connection to AP <MAC address removed> lost.
[ 2519.413598] wlan0: authenticate with <MAC address removed> (try 1)
[ 2519.415801] wlan0: authenticated
[ 2519.416173] wlan0: associate with <MAC address removed> (try 1)
[ 2519.422397] wlan0: RX ReassocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[ 2519.422407] wlan0: associated
[ 2519.422416] wlan0: No basic rates in AssocResp. Using min supported rate instead.
[ 2582.737645] wlan0: Connection to AP <MAC address removed> lost.
[ 2590.099865] wlan0: authenticate with <MAC address removed> (try 1)
[ 2590.104991] wlan0: authenticated
[ 2590.105595] wlan0: associate with <MAC address removed> (try 1)
[ 2590.110789] wlan0: RX ReassocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[ 2590.110800] wlan0: associated
[ 2590.110809] wlan0: No basic rates in AssocResp. Using min supported rate instead.
[24584.006035] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[24587.521457] rtl8192ce 0000:02:00.0: restoring config space at offset 0xf (was 0x100, writing 0x10a)
[24591.592356] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[24593.855814] wlan0: authenticate with <MAC address removed> (try 1)
[24593.860217] wlan0: authenticated
[24593.860632] wlan0: associate with <MAC address removed> (try 1)
[24593.864708] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[24593.864719] wlan0: associated
[24593.864727] wlan0: No basic rates in AssocResp. Using min supported rate instead.
[24593.876874] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[24604.245907] wlan0: no IPv6 routers present


**************** done ********************





---

