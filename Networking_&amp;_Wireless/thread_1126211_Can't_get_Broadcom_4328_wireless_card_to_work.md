---
title: "Can't get Broadcom 4328 wireless card to work"
date: 2009-04-15
forum: Networking &amp; Wireless
---

### Post by Waelwulf on 2009-04-15
My computer is an Inspiron 1525 with a Broadcom Corporation BCM4328 802.11a/b/g/n (rev 03) wireless card running 64 Studio based on Ubuntu 8.04.

According to the Ubuntu Wiki, my wireless card should be offered restricted drivers to use but under Hardware Drivers I'm given no options. I have tried to compile the Broadcom STA driver. I have build-essentials installed. Trying to compile gives me the following output: 

```
make: Entering directory `/usr/src/linux-headers-2.6.29-1-multimedia-amd64'
  CC [M]  /home/chris/hybrid_wl/src/wl/sys/wl_linux.o
/home/chris/hybrid_wl/src/wl/sys/wl_linux.c: In function &#8216;wl_attach&#8217;:
/home/chris/hybrid_wl/src/wl/sys/wl_linux.c:439: error: implicit declaration of function &#8216;ieee80211_get_crypto_ops&#8217;
/home/chris/hybrid_wl/src/wl/sys/wl_linux.c:439: warning: assignment makes pointer from integer without a cast
/home/chris/hybrid_wl/src/wl/sys/wl_linux.c:442: warning: assignment makes pointer from integer without a cast
/home/chris/hybrid_wl/src/wl/sys/wl_linux.c: In function &#8216;wl_free&#8217;:
/home/chris/hybrid_wl/src/wl/sys/wl_linux.c:712: error: &#8216;struct net_device&#8217; has no member named &#8216;priv&#8217;
/home/chris/hybrid_wl/src/wl/sys/wl_linux.c:747: error: &#8216;struct net_device&#8217; has no member named &#8216;priv&#8217;
/home/chris/hybrid_wl/src/wl/sys/wl_linux.c:763: error: dereferencing pointer to incomplete type
/home/chris/hybrid_wl/src/wl/sys/wl_linux.c:767: error: dereferencing pointer to incomplete type
/home/chris/hybrid_wl/src/wl/sys/wl_linux.c: In function &#8216;wl_open&#8217;:
/home/chris/hybrid_wl/src/wl/sys/wl_linux.c:792: error: &#8216;struct net_device&#8217; has no member named &#8216;priv&#8217;
/home/chris/hybrid_wl/src/wl/sys/wl_linux.c: In function &#8216;wl_close&#8217;:
/home/chris/hybrid_wl/src/wl/sys/wl_linux.c:820: error: &#8216;struct net_device&#8217; has no member named &#8216;priv&#8217;
/home/chris/hybrid_wl/src/wl/sys/wl_linux.c: In function &#8216;wl_start&#8217;:
/home/chris/hybrid_wl/src/wl/sys/wl_linux.c:843: error: &#8216;struct net_device&#8217; has no member named &#8216;priv&#8217;
/home/chris/hybrid_wl/src/wl/sys/wl_linux.c: In function &#8216;wl_alloc_if&#8217;:
/home/chris/hybrid_wl/src/wl/sys/wl_linux.c:929: error: &#8216;struct net_device&#8217; has no member named &#8216;priv&#8217;
/home/chris/hybrid_wl/src/wl/sys/wl_linux.c: In function &#8216;wl_get_driver_info&#8217;:
/home/chris/hybrid_wl/src/wl/sys/wl_linux.c:1108: error: &#8216;struct net_device&#8217; has no member named &#8216;priv&#8217;
/home/chris/hybrid_wl/src/wl/sys/wl_linux.c: In function &#8216;wl_ioctl&#8217;:
/home/chris/hybrid_wl/src/wl/sys/wl_linux.c:1195: error: &#8216;struct net_device&#8217; has no member named &#8216;priv&#8217;
/home/chris/hybrid_wl/src/wl/sys/wl_linux.c:1196: error: &#8216;struct net_device&#8217; has no member named &#8216;priv&#8217;
/home/chris/hybrid_wl/src/wl/sys/wl_linux.c: In function &#8216;wl_get_stats&#8217;:
/home/chris/hybrid_wl/src/wl/sys/wl_linux.c:1280: error: &#8216;struct net_device&#8217; has no member named &#8216;priv&#8217;
/home/chris/hybrid_wl/src/wl/sys/wl_linux.c: In function &#8216;wl_get_wireless_stats&#8217;:
/home/chris/hybrid_wl/src/wl/sys/wl_linux.c:1309: error: &#8216;struct net_device&#8217; has no member named &#8216;priv&#8217;
/home/chris/hybrid_wl/src/wl/sys/wl_linux.c:1310: error: &#8216;struct net_device&#8217; has no member named &#8216;priv&#8217;
/home/chris/hybrid_wl/src/wl/sys/wl_linux.c: In function &#8216;wl_set_mac_address&#8217;:
/home/chris/hybrid_wl/src/wl/sys/wl_linux.c:1373: error: &#8216;struct net_device&#8217; has no member named &#8216;priv&#8217;
/home/chris/hybrid_wl/src/wl/sys/wl_linux.c:1381: error: &#8216;struct net_device&#8217; has no member named &#8216;priv&#8217;
/home/chris/hybrid_wl/src/wl/sys/wl_linux.c: In function &#8216;_wl_set_multicast_list&#8217;:
/home/chris/hybrid_wl/src/wl/sys/wl_linux.c:1406: error: &#8216;struct net_device&#8217; has no member named &#8216;priv&#8217;
/home/chris/hybrid_wl/src/wl/sys/wl_linux.c: In function &#8216;wl_tkip_miccheck&#8217;:
/home/chris/hybrid_wl/src/wl/sys/wl_linux.c:1798: error: dereferencing pointer to incomplete type
/home/chris/hybrid_wl/src/wl/sys/wl_linux.c:1801: error: dereferencing pointer to incomplete type
/home/chris/hybrid_wl/src/wl/sys/wl_linux.c: In function &#8216;wl_tkip_micadd&#8217;:
/home/chris/hybrid_wl/src/wl/sys/wl_linux.c:1820: error: dereferencing pointer to incomplete type
/home/chris/hybrid_wl/src/wl/sys/wl_linux.c: In function &#8216;wl_tkip_encrypt&#8217;:
/home/chris/hybrid_wl/src/wl/sys/wl_linux.c:1840: error: dereferencing pointer to incomplete type
/home/chris/hybrid_wl/src/wl/sys/wl_linux.c: In function &#8216;wl_tkip_decrypt&#8217;:
/home/chris/hybrid_wl/src/wl/sys/wl_linux.c:1862: error: dereferencing pointer to incomplete type
/home/chris/hybrid_wl/src/wl/sys/wl_linux.c:1864: error: dereferencing pointer to incomplete type
/home/chris/hybrid_wl/src/wl/sys/wl_linux.c: In function &#8216;wl_tkip_keyset&#8217;:
/home/chris/hybrid_wl/src/wl/sys/wl_linux.c:1906: error: dereferencing pointer to incomplete type
/home/chris/hybrid_wl/src/wl/sys/wl_linux.c:1916: error: dereferencing pointer to incomplete type
/home/chris/hybrid_wl/src/wl/sys/wl_linux.c:1923: error: dereferencing pointer to incomplete type
/home/chris/hybrid_wl/src/wl/sys/wl_linux.c:1933: error: dereferencing pointer to incomplete type
/home/chris/hybrid_wl/src/wl/sys/wl_linux.c:1943: error: dereferencing pointer to incomplete type
/home/chris/hybrid_wl/src/wl/sys/wl_linux.c:1950: error: dereferencing pointer to incomplete type
/home/chris/hybrid_wl/src/wl/sys/wl_linux.c: In function &#8216;wl_tkip_printstats&#8217;:
/home/chris/hybrid_wl/src/wl/sys/wl_linux.c:1969: error: dereferencing pointer to incomplete type
/home/chris/hybrid_wl/src/wl/sys/wl_linux.c:1971: error: dereferencing pointer to incomplete type
make[1]: *** [/home/chris/hybrid_wl/src/wl/sys/wl_linux.o] Error 1
make: *** [_module_/home/chris/hybrid_wl] Error 2
make: Leaving directory `/usr/src/linux-headers-2.6.29-1-multimedia-amd64'

```

I have tried getting the card to work in Ubuntu Studio using both the provided drivers and ndiswrapper, which yielded only intermittent connectivity; the Fedora 11 beta, Fedora 10 and now 64 Studio. It has been many weeks of frustration and I still don't have a working wireless card.

How do I get my card to work?

---

### Post by Ayuthia on 2009-04-15
> **Waelwulf said:**
> My computer is an Inspiron 1525 with a Broadcom Corporation BCM4328 802.11a/b/g/n (rev 03) wireless card running 64 Studio based on Ubuntu 8.04.

According to the Ubuntu Wiki, my wireless card should be offered restricted drivers to use but under Hardware Drivers I'm given no options. I have tried to compile the Broadcom STA driver. I have build-essentials installed. Trying to compile gives me the following output: 

```
make: Entering directory `/usr/src/linux-headers-2.6.29-1-multimedia-amd64'
  CC [M]  /home/chris/hybrid_wl/src/wl/sys/wl_linux.o
/home/chris/hybrid_wl/src/wl/sys/wl_linux.c: In function ‘wl_attach’:
/home/chris/hybrid_wl/src/wl/sys/wl_linux.c:439: error: implicit declaration of function ‘ieee80211_get_crypto_ops’
/home/chris/hybrid_wl/src/wl/sys/wl_linux.c:439: warning: assignment makes pointer from integer without a cast
/home/chris/hybrid_wl/src/wl/sys/wl_linux.c:442: warning: assignment makes pointer from integer without a cast
/home/chris/hybrid_wl/src/wl/sys/wl_linux.c: In function ‘wl_free’:
/home/chris/hybrid_wl/src/wl/sys/wl_linux.c:712: error: ‘struct net_device’ has no member named ‘priv’
/home/chris/hybrid_wl/src/wl/sys/wl_linux.c:747: error: ‘struct net_device’ has no member named ‘priv’
/home/chris/hybrid_wl/src/wl/sys/wl_linux.c:763: error: dereferencing pointer to incomplete type
/home/chris/hybrid_wl/src/wl/sys/wl_linux.c:767: error: dereferencing pointer to incomplete type
/home/chris/hybrid_wl/src/wl/sys/wl_linux.c: In function ‘wl_open’:
/home/chris/hybrid_wl/src/wl/sys/wl_linux.c:792: error: ‘struct net_device’ has no member named ‘priv’
/home/chris/hybrid_wl/src/wl/sys/wl_linux.c: In function ‘wl_close’:
/home/chris/hybrid_wl/src/wl/sys/wl_linux.c:820: error: ‘struct net_device’ has no member named ‘priv’
/home/chris/hybrid_wl/src/wl/sys/wl_linux.c: In function ‘wl_start’:
/home/chris/hybrid_wl/src/wl/sys/wl_linux.c:843: error: ‘struct net_device’ has no member named ‘priv’
/home/chris/hybrid_wl/src/wl/sys/wl_linux.c: In function ‘wl_alloc_if’:
/home/chris/hybrid_wl/src/wl/sys/wl_linux.c:929: error: ‘struct net_device’ has no member named ‘priv’
/home/chris/hybrid_wl/src/wl/sys/wl_linux.c: In function ‘wl_get_driver_info’:
/home/chris/hybrid_wl/src/wl/sys/wl_linux.c:1108: error: ‘struct net_device’ has no member named ‘priv’
/home/chris/hybrid_wl/src/wl/sys/wl_linux.c: In function ‘wl_ioctl’:
/home/chris/hybrid_wl/src/wl/sys/wl_linux.c:1195: error: ‘struct net_device’ has no member named ‘priv’
/home/chris/hybrid_wl/src/wl/sys/wl_linux.c:1196: error: ‘struct net_device’ has no member named ‘priv’
/home/chris/hybrid_wl/src/wl/sys/wl_linux.c: In function ‘wl_get_stats’:
/home/chris/hybrid_wl/src/wl/sys/wl_linux.c:1280: error: ‘struct net_device’ has no member named ‘priv’
/home/chris/hybrid_wl/src/wl/sys/wl_linux.c: In function ‘wl_get_wireless_stats’:
/home/chris/hybrid_wl/src/wl/sys/wl_linux.c:1309: error: ‘struct net_device’ has no member named ‘priv’
/home/chris/hybrid_wl/src/wl/sys/wl_linux.c:1310: error: ‘struct net_device’ has no member named ‘priv’
/home/chris/hybrid_wl/src/wl/sys/wl_linux.c: In function ‘wl_set_mac_address’:
/home/chris/hybrid_wl/src/wl/sys/wl_linux.c:1373: error: ‘struct net_device’ has no member named ‘priv’
/home/chris/hybrid_wl/src/wl/sys/wl_linux.c:1381: error: ‘struct net_device’ has no member named ‘priv’
/home/chris/hybrid_wl/src/wl/sys/wl_linux.c: In function ‘_wl_set_multicast_list’:
/home/chris/hybrid_wl/src/wl/sys/wl_linux.c:1406: error: ‘struct net_device’ has no member named ‘priv’
/home/chris/hybrid_wl/src/wl/sys/wl_linux.c: In function ‘wl_tkip_miccheck’:
/home/chris/hybrid_wl/src/wl/sys/wl_linux.c:1798: error: dereferencing pointer to incomplete type
/home/chris/hybrid_wl/src/wl/sys/wl_linux.c:1801: error: dereferencing pointer to incomplete type
/home/chris/hybrid_wl/src/wl/sys/wl_linux.c: In function ‘wl_tkip_micadd’:
/home/chris/hybrid_wl/src/wl/sys/wl_linux.c:1820: error: dereferencing pointer to incomplete type
/home/chris/hybrid_wl/src/wl/sys/wl_linux.c: In function ‘wl_tkip_encrypt’:
/home/chris/hybrid_wl/src/wl/sys/wl_linux.c:1840: error: dereferencing pointer to incomplete type
/home/chris/hybrid_wl/src/wl/sys/wl_linux.c: In function ‘wl_tkip_decrypt’:
/home/chris/hybrid_wl/src/wl/sys/wl_linux.c:1862: error: dereferencing pointer to incomplete type
/home/chris/hybrid_wl/src/wl/sys/wl_linux.c:1864: error: dereferencing pointer to incomplete type
/home/chris/hybrid_wl/src/wl/sys/wl_linux.c: In function ‘wl_tkip_keyset’:
/home/chris/hybrid_wl/src/wl/sys/wl_linux.c:1906: error: dereferencing pointer to incomplete type
/home/chris/hybrid_wl/src/wl/sys/wl_linux.c:1916: error: dereferencing pointer to incomplete type
/home/chris/hybrid_wl/src/wl/sys/wl_linux.c:1923: error: dereferencing pointer to incomplete type
/home/chris/hybrid_wl/src/wl/sys/wl_linux.c:1933: error: dereferencing pointer to incomplete type
/home/chris/hybrid_wl/src/wl/sys/wl_linux.c:1943: error: dereferencing pointer to incomplete type
/home/chris/hybrid_wl/src/wl/sys/wl_linux.c:1950: error: dereferencing pointer to incomplete type
/home/chris/hybrid_wl/src/wl/sys/wl_linux.c: In function ‘wl_tkip_printstats’:
/home/chris/hybrid_wl/src/wl/sys/wl_linux.c:1969: error: dereferencing pointer to incomplete type
/home/chris/hybrid_wl/src/wl/sys/wl_linux.c:1971: error: dereferencing pointer to incomplete type
make[1]: *** [/home/chris/hybrid_wl/src/wl/sys/wl_linux.o] Error 1
make: *** [_module_/home/chris/hybrid_wl] Error 2
make: Leaving directory `/usr/src/linux-headers-2.6.29-1-multimedia-amd64'

```

I have tried getting the card to work in Ubuntu Studio using both the provided drivers and ndiswrapper, which yielded only intermittent connectivity; the Fedora 11 beta, Fedora 10 and now 64 Studio. It has been many weeks of frustration and I still don't have a working wireless card.

How do I get my card to work?

You might try adding this patch:
[http://gentoo-overlays.zugaina.org/sabayon/portage/net-wireless/broadcom-sta/files/broadcom-sta-5.10.79.10-linux-2.6.29.patch](http://gentoo-overlays.zugaina.org/sabayon/portage/net-wireless/broadcom-sta/files/broadcom-sta-5.10.79.10-linux-2.6.29.patch)

```
patch -p1 < broadcom-sta-5.10.79.10-linux-2.6.29.patch
```

The source needs a patch to make it compile in 2.6.29.

---

### Post by Waelwulf on 2009-04-15
I'm not so technical as to know how to apply the patch. Can you walk me through it?

---

### Post by Ayuthia on 2009-04-15
> **Waelwulf said:**
> I'm not so technical as to know how to apply the patch. Can you walk me through it?

Just copy the patch into the directory where you compiled the wl driver (using the make command).  From there, add the command from the previous post:
```
patch -p1 < broadcom-sta-5.10.79.10-linux-2.6.29.patch
```
Once the patch has been applied, try doing the make clean and make commands again.

If that is too confusing still, you can go to this [link]("http://linuxfans.betaserver.org/index.php?option=com_content&view=article&id=48:guide-to-compiling-and-using-the-broadcom-sta-module&catid=34:guides&Itemid=61").  It has a set of instructions that might help.

---

### Post by stevie1989 on 2009-06-25
> **Ayuthia said:**
> Just copy the patch into the directory where you compiled the wl driver (using the make command).  From there, add the command from the previous post:
```
patch -p1 < broadcom-sta-5.10.79.10-linux-2.6.29.patch
```Once the patch has been applied, try doing the make clean and make commands again.

If that is too confusing still, you can go to this [link]("http://linuxfans.betaserver.org/index.php?option=com_content&view=article&id=48:guide-to-compiling-and-using-the-broadcom-sta-module&catid=34:guides&Itemid=61").  It has a set of instructions that might help.

Went through the steps, lm running Kubuntu 9.10, worked, but no wireless signals were found so gave it a restart and now l'm back too the Network Manager not being able too have Wireless! Fustration, love and hate relationship so far with the linux OS. 


Also, running ethernet, all my drivers work asides the nVida and Broadcom but nVida has two options too use for 3d and some other one (don't really use them anyways). It's a HP DV2620ca. Want too add the Hardware Drivers says my wireless card is activated and currently in use. My bluetooth works fine and too avoid WPA problems l've been reading about, using WEP with MAC verfication.

Specs from HP Canada
[http://h10025.www1.hp.com/ewfrf/wc/document?lc=en&dlc=en&cc=ca&docname=c01161078](http://h10025.www1.hp.com/ewfrf/wc/document?lc=en&dlc=en&cc=ca&docname=c01161078)

---

### Post by Ayuthia on 2009-06-25
> **stevie1989 said:**
> Went through the steps, lm running Kubuntu 9.10, worked, but no wireless signals were found so gave it a restart and now l'm back too the Network Manager not being able too have Wireless! Fustration, love and hate relationship so far with the linux OS. 


Also, running ethernet, all my drivers work asides the nVida and Broadcom but nVida has two options too use for 3d and some other one (don't really use them anyways). It's a HP DV2620ca. Want too add the Hardware Drivers says my wireless card is activated and currently in use. My bluetooth works fine and too avoid WPA problems l've been reading about, using WEP with MAC verfication.

Specs from HP Canada
[http://h10025.www1.hp.com/ewfrf/wc/document?lc=en&dlc=en&cc=ca&docname=c01161078](http://h10025.www1.hp.com/ewfrf/wc/document?lc=en&dlc=en&cc=ca&docname=c01161078)

Can you post the results of:
```
lshw -C network
lsmod|grep -e b43 -e ssb -e wl -e ndis
```
The first will show which wireless driver your card is trying to use and the second command will see what wireless modules are currently loaded.

---

### Post by stevie1989 on 2009-06-25
First Cmd
```

  *-network
       description: Ethernet interface
       product: MCP67 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a2
       serial: 00:16:d3:f6:75:c7
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=forcedeth driverversion=0.61 ip=192.168.0.96 latency=0 maxlatency=20 mingnt=1 module=forcedeth multicast=yes
  *-network
       description: Network controller
       product: BCM4328 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: de:ff:ab:0f:a9:b5
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes


```2nd Cmd
```

wl                   1281236  0
ieee80211_crypt        13444  1 wl
ssb                    41220  0


```
l read and attempted to remove ssb and use wl, don't know how (worked until rebooted then the blacklist wouldn't go again, lost link too the source though)

---

### Post by Ayuthia on 2009-06-25
> **stevie1989 said:**
> First Cmd
```

  *-network
       description: Ethernet interface
       product: MCP67 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a2
       serial: 00:16:d3:f6:75:c7
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=forcedeth driverversion=0.61 ip=192.168.0.96 latency=0 maxlatency=20 mingnt=1 module=forcedeth multicast=yes
  *-network
       description: Network controller
       product: BCM4328 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: de:ff:ab:0f:a9:b5
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes


```2nd Cmd
```

wl                   1281236  0
ieee80211_crypt        13444  1 wl
ssb                    41220  0


```
l read and attempted to remove ssb and use wl, don't know how (worked until rebooted then the blacklist wouldn't go again, lost link too the source though)

Try the following:
```
sudo modprobe -r ssb wl
sudo modprobe wl
sudo update-initramfs -u
```The last command will update the initramfs file.  This file is used when the system boots up.  Most likely the ssb blacklisting is not updated in there.  This command should fix it.

When you say it worked, did that mean you were able to get connected until you rebooted?

---

### Post by stevie1989 on 2009-06-25
> **Ayuthia said:**
> Try the following:
```
sudo modprobe -r ssb wl
sudo modprobe wl
sudo update-initramfs -u
```The last command will update the initramfs file.  This file is used when the system boots up.  Most likely the ssb blacklisting is not updated in there.  This command should fix it.

When you say it worked, did that mean you were able to get connected until you rebooted?

l'm currently using my Wireless right now, going to give it a boot
WORKS! Thank you so much Ayuthia

---

### Post by jader2toesbumpy on 2009-07-16
> **Ayuthia said:**
> Try the following:
```
sudo modprobe -r ssb wl
sudo modprobe wl
sudo update-initramfs -u
```The last command will update the initramfs file.  This file is used when the system boots up.  Most likely the ssb blacklisting is not updated in there.  This command should fix it.
 

When I first installed Janty back in April my wireless ( BCM 4328 ) worked out of the box. But a couple days a go my hard drive crashed and I installed Janty on my new HDD and the wireless didn't work but this fixed it. Thank you very much.

---

### Post by jmorsman on 2009-08-03
I just installed 9.04 on a Dell m1530 with a broadcom 4328 wireless card. This is the first post that I have found that makes the card run. However the card will not run after reboot. what am I missing what is causing it not to reload after boot.

---

### Post by jmorsman on 2009-08-03
I got it to work. the last command entered tells you what kernel it is updating/changing. If your computer does not reconnect after reboot check what kernel it is using. Mine was updating 2.6.28-13-generic

 update-initramfs: Generating /boot/initrd.img-2.6.28-13-server 

However it was booting 2.6.28-14-generic. The wireless card would not work once the machine was up. I changed it so it would boot from 13 and it works fine now. 

Thanks for the help

---

