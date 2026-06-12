---
title: "ZTE 852 on ubuntu 9.10"
date: 2009-10-28
forum: Networking &amp; Wireless
---

### Post by fahim_1182 on 2009-10-28
hi,
i installed Ubuntu 9.10 beta version, i just want to configure my ZTE 852 modem, ubudsl is not available for ubuntu 9.10. can anybody help me to configure the modem. thnx

---

### Post by pdc on 2009-10-31
so none of this is any use?

[http://ubuntuforums.org/showthread.php?t=851795](http://ubuntuforums.org/showthread.php?t=851795)

---

### Post by joannesfdo on 2009-11-03
**Hay ubudsl software is not  compatible with ubuntu 9.10 do any one know how to get the driver for ZTE ZXDSL 852 USB ADSL MODEM ???** :(

---

### Post by pdc on 2009-11-03
folks are reporting problems using Ubuntu 9.10 with mobile broadband; you might be best downloading an earlier version eg 9.04 and trying that

---

### Post by joannesfdo on 2009-11-03
> **pdc said:**
> folks are reporting problems using Ubuntu 9.10 with mobile broadband; you might be best downloading an earlier version eg 9.04 and trying that

This is not a mobile broadband its a ADSL (SLT) connection

---

### Post by akila87 on 2009-11-05
I also have the same problem. Can any one fix that bug in ubdsal because it worked perfectly in 9.04 or post a new method

---

### Post by akila87 on 2009-11-05
I make ubudsl work in Ubuntu 9.10 but the modem not synchronizing 

try this
 
1. press Alt + F2 & type

```
gksu gedit /usr/share/ubudsl/configs/system.ini
```

2. add these lines to the file, save & close 

```
[Ubuntu_9.10]
package_manager=apt
basic_from_cd=
devel_from_cd=build-essential
```

Now you can run ubudsl but my modem is not synchronizing if any one go through that please post here.

---

### Post by dakshika on 2009-11-08
i have same problem now i can run ubudsl on 9.10 but still my modem power button is not working ?? 

any help plzzzz............

---

### Post by ham4ever on 2009-11-10
i have same problem ,, i can not run abudsl in  ubuntu 9.10 
looks like i gonna back to XP :(

---

### Post by ham4ever on 2009-11-11
i solved the problem with  ur help :D

go to this to see how i did it 
[http://ubuntuforums.org/showthread.php?t=1323042](http://ubuntuforums.org/showthread.php?t=1323042)

goodluck ;)

---

### Post by ruphert on 2009-12-02
Patch for ZTE ZXDSL v2 driver on kernel 2.6.31

[http://mariuszs.googlepages.com/zxdslv2-2.6.31.diff](http://mariuszs.googlepages.com/zxdslv2-2.6.31.diff)

Using:

```
mkdir unicorn
cd unicorn
wget http://linnet.cba.pl/attachment.php?aid=5 -O steryzxdsl.tar.gz
tar zxvf steryzxdsl.tar.gz
wget http://mariuszs.googlepages.com/zxdslv2-2.6.31.diff
patch src/unicorn_ethdrv.c <>
make
sudo make install
```

cat zxdslv2-2.6.31.diff
```
--- ../oryg/src/unicorn_ethdrv.c	2008-10-02 14:10:27.000000000 +0200
+++ src/unicorn_ethdrv.c	2009-11-30 19:20:37.733581549 +0100
@@ -3,6 +3,9 @@
   The chipset consists of the ADSL DMT transceiver ST70138 and the
   ST20174 Analog Front End (AFE).
   This file contains the ethernet interface and SAR routines.
+
+  Updated to work with Linux kernel >= 2.6.31 by 
+  Mariusz Smyku&#322;a 2009-11-30 <mariuszs@gmail.com>
 */
 #include <linux/autoconf.h>
 #include <linux/version.h>
@@ -961,7 +964,7 @@
 
 static int unicorn_eth_send(struct sk_buff *skb, struct net_device *eth_dev) 
 {
-	struct unicorn_ethdrv *drv = (struct unicorn_ethdrv *) eth_dev->priv;
+	struct unicorn_ethdrv *drv = (struct unicorn_ethdrv *) netdev_priv(eth_dev);
 	struct atm_ext_skb_data *skb_data;
  	int status;
 	
@@ -1082,7 +1085,7 @@
 
 static int unicorn_eth_open(struct net_device *eth_dev) 
 {
-	struct unicorn_ethdrv *drv = (struct unicorn_ethdrv *)eth_dev->priv;
+	struct unicorn_ethdrv *drv = (struct unicorn_ethdrv *)netdev_priv(eth_dev);
 
 	DBG(ATM_D,"vpi=%d,vci=%d\n",drv->vpi,drv->vci);
 
@@ -1100,12 +1103,12 @@
 	// Install the proc_read function in /proc/net/atm/
 #ifndef CONFIG_ATM
 	atm_proc_root = proc_mkdir("net/atm",NULL);
-	if (atm_proc_root) atm_proc_root->owner=THIS_MODULE;
+	//if (atm_proc_root) atm_proc_root->owner=THIS_MODULE;
 #endif	
 	if (atm_proc_root) {
 		drv->proc_dir_entry = create_proc_read_entry("UNICORN:0",0,atm_proc_root,unicorn_eth_proc_read,drv);
 		if (drv->proc_dir_entry) {
-			drv->proc_dir_entry->owner = THIS_MODULE;
+			//drv->proc_dir_entry->owner = THIS_MODULE;
 		} else {
 			DBG(ATM_D,"no proc entry installed\n");
 		}
@@ -1126,7 +1129,7 @@
 static int 
 unicorn_eth_close(struct net_device *eth_dev) 
 {
-	struct unicorn_ethdrv *drv = (struct unicorn_ethdrv *)eth_dev->priv;
+	struct unicorn_ethdrv *drv = (struct unicorn_ethdrv *)netdev_priv(eth_dev);
   
 	DBG(ATM_D,"\n");
 
@@ -1153,7 +1156,7 @@
 
 static struct net_device_stats *unicorn_eth_stats(struct net_device *eth_dev)
 {
-	struct unicorn_ethdrv *drv = (struct unicorn_ethdrv *)eth_dev->priv;
+	struct unicorn_ethdrv *drv = (struct unicorn_ethdrv *)netdev_priv(eth_dev);
 	return &drv->eth_stats;
 }
 
@@ -1305,7 +1308,7 @@
 
 static int unicorn_eth_ioctl(struct net_device *eth_dev, struct ifreq *rq, int cmd) 
 {
-	struct unicorn_ethdrv *drv = (struct unicorn_ethdrv *)eth_dev->priv;
+	struct unicorn_ethdrv *drv = (struct unicorn_ethdrv *)netdev_priv(eth_dev);
 	T_MswCtrl ctrl;
 	void *user_buffer;
 	int err = -ENOTTY;
@@ -1376,6 +1379,18 @@
 #endif
 #endif
 
+
+static const struct net_device_ops unicorn_netdev_ops = {
+       	.ndo_open               = unicorn_eth_open,
+       	.ndo_stop               = unicorn_eth_close,
+	.ndo_do_ioctl		= unicorn_eth_ioctl,	
+       	.ndo_change_mtu         = unicorn_eth_change_mtu,      
+       	.ndo_start_xmit         = unicorn_eth_send,
+      	.ndo_get_stats 		= unicorn_eth_stats,
+	.ndo_set_multicast_list = unicorn_eth_set_multicast,
+	.ndo_tx_timeout        	= unicorn_eth_tx_timeout
+};
+
 int unicorn_eth_init(void)
 {
 	struct net_device *eth_dev;
@@ -1391,11 +1406,11 @@
 	}
 
 	eth_dev = alloc_etherdev(sizeof(struct unicorn_ethdrv));
-	if (!eth_dev || !eth_dev->priv) {
+	if (!eth_dev || !netdev_priv(eth_dev)) {
 		DBG(ATM_D,"no memory for drv data\n");
 		return -ENOMEM;
 	}
-	unicorn_ethdrv = drv = eth_dev->priv;
+	unicorn_ethdrv = drv = netdev_priv(eth_dev);
 	memset(drv, 0, sizeof(struct unicorn_ethdrv));  
 #if 	(LINUX_VERSION_CODE < KERNEL_VERSION(2,6,23))
 	SET_MODULE_OWNER(eth_dev);
@@ -1447,14 +1462,8 @@
 	// set MAC address,
 	unicorn_set_mac(eth_dev,mac_address);
 
-	eth_dev->open               = unicorn_eth_open;
-	eth_dev->stop               = unicorn_eth_close;
-	eth_dev->do_ioctl           = unicorn_eth_ioctl;
-	eth_dev->change_mtu         = unicorn_eth_change_mtu;
-	eth_dev->hard_start_xmit    = unicorn_eth_send;
-	eth_dev->get_stats          = unicorn_eth_stats;
-	eth_dev->set_multicast_list = unicorn_eth_set_multicast;
-	eth_dev->tx_timeout         = unicorn_eth_tx_timeout;
+	eth_dev->netdev_ops = &unicorn_netdev_ops;
+	
 	eth_dev->watchdog_timeo     = HZ*5;
 	
 	return 0;
```

This is not tested.

Cheers

---

### Post by joannesfdo on 2010-02-17
Hi bro i try to patch the way that you given but some of the steps are not working do i need internet connection while im doing patch?

---

### Post by logari81 on 2010-02-22
please try the lucid package from here:
[https://launchpad.net/~logari81/+archive/ppa](https://launchpad.net/~logari81/+archive/ppa)

I have experimentally included the patch of #11. Even if the package is uploaded in the lucid repo, it is thought for karmic. Please test it I am looking for testers.

---

### Post by joannesfdo on 2010-02-25
its not working on ubuntu 9.10

---

### Post by logari81 on 2010-03-01
> **joannesfdo said:**
> its not working on ubuntu 9.10

what does this mean? Do you have problems with the installation or do you receive any message after starting ubudsl?

---

### Post by joannesfdo on 2010-03-02
Bro i installed it but modem is not synchronizeing, but i did it manually now its working fine (But u need g++)

---

