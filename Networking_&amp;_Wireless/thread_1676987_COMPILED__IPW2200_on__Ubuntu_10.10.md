---
title: "COMPILED  IPW2200 on  Ubuntu 10.10"
date: 2011-01-28
forum: Networking &amp; Wireless
---

### Post by xeon111 on 2011-01-28
Basically i was able to compile IPW2200 on ubuntu 10.10.
IEEE80211 was compiled by me by the help of this thread and a few patches [http://ubuntuforums.org/showthread.php?t=1467265](http://ubuntuforums.org/showthread.php?t=1467265)

use all the patches and fixed as used in 
[http://ubuntuforums.org/showpost.php?p=6934824&postcount=34](http://ubuntuforums.org/showpost.php?p=6934824&postcount=34)
then do that following

in IPW2200, some of the code was old.
What i did was track down all the errors and fix them one by one.
what i did in general was well i'll list them in the order of their appearance and the fix for them.
error :  ‘struct device’ has no member named ‘driver_data’

sol: This was due to the fact the in linux build 2.6.32, driver_data was shifted to  drivers/base/dd.c .
Now to fix them what i did was use 
dev_get_drvdata(struct *device) to access the data.
Inside IPW2200
in simple terms comment every occurrence of driver_data and instead use 
dev_get_drvdata(d); in place of driver_data.(d is used everywhere as a name for struct *device)
don't worry a quick replace all wouldn't hurt just save the code before hand.

error:TASK_INTERRUPTIBLE undeclared
sol: add #include <linux/sched.h> in your ipw2200.h 

as this TASK_INTERRUPTABLE was moved to sched.h .

error :implicit declaration of function ‘signal_pending’ and 'schedule_timeout'
sol: same as above signal pending defined in sched.h

error : ‘struct net_device’ has no member named ‘open’
sol : check the link i posted above, in general what you do is
look at the line no in the error and then instantiate a net_dev_ops *  
and  send a reference of the net_dev->netdev_ops to your instantiated net_dev_ops
and call all the members from that using a prefix ndo_ 

example :
dev_ops->ndo_membername= method / member name
or 
dev_ops->ndo_open = ipw_prom_open;

and after changing everything you assign 
 net_dev->net_dev_ops = dev_ops
I am not really good at explaining this i would recommend you read the link i posted above.

what i did (i do not recommend this) was change the  ipw_priv struct 
and added     
struct net_device_ops *prom_dev_ops;


then in the line 11892
what i did was 

//edit begin
/*    priv->prom_net_dev->open = ipw_prom_open;
    priv->prom_net_dev->stop = ipw_prom_stop;
    priv->prom_net_dev->get_stats = ipw_prom_get_stats;
    priv->prom_net_dev->hard_start_xmit = ipw_prom_hard_start_xmit;
*/
    priv->prom_dev_ops = &(priv->prom_net_dev->netdev_ops);
    
    priv->prom_dev_ops->ndo_open = ipw_prom_open;
    priv->prom_dev_ops->ndo_stop = ipw_prom_stop;
    priv->prom_dev_ops->ndo_get_stats = ipw_prom_get_stats;
    priv->prom_dev_ops->ndo_start_xmit = ipw_prom_hard_start_xmit;
    priv->prom_net_dev->netdev_ops = priv->prom_dev_ops;


and well that's it 
Not for the complete newbies.

Any questions , Errors , Death Threats welcome,...wait cross the Death Threats.

---

### Post by yuneng_95 on 2011-07-31
Hey xeon111. :)
Im requesting help, but first i would like to inform that im a newbie in linux, so pls be gentle and i would reli appreciate yr reply. Pls do keep in mind im stil a newbie.

Im now using ubuntu 11.04 and i having this error-[ error : ‘struct device’ has no member named ‘driver_data’ ] and bunch alot of other errors. 

My ipwraw-ng file has no autoconf.h, so i copied it from linux-generic into the ipwraw-ng file. Then terminal recognized that modification, and it load my autoconf.h file. But these errors pop out. 
```
make -C /lib/modules/2.6.38-10-generic/build M=/home/yuneng/ipwraw-ng modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.38-10-generic'
  CC [M]  /home/yuneng/ipwraw-ng/ipwraw.o
In file included from /home/yuneng/ipwraw-ng/ipwraw.h:32:0,
                 from /home/yuneng/ipwraw-ng/ipwraw.c:48:
/home/yuneng/ipwraw-ng/linux/autoconf.h:4589:0: warning: "CONFIG_VERSION_SIGNATURE" redefined
./include/generated/autoconf.h:4591:0: note: this is the location of the previous definition
/home/yuneng/ipwraw-ng/ipwraw.c: In function ‘ipw_send_cmd’:
/home/yuneng/ipwraw-ng/ipwraw.c:1015:8: error: ‘TASK_INTERRUPTIBLE’ undeclared (first use in this function)
/home/yuneng/ipwraw-ng/ipwraw.c:1015:8: note: each undeclared identifier is reported only once for each function it appears in
/home/yuneng/ipwraw-ng/ipwraw.c:1015:3: error: implicit declaration of function ‘signal_pending’
/home/yuneng/ipwraw-ng/ipwraw.c:1015:3: error: implicit declaration of function ‘schedule_timeout’
/home/yuneng/ipwraw-ng/ipwraw.c: In function ‘show_temperature’:
/home/yuneng/ipwraw-ng/ipwraw.c:1360:46: error: ‘struct device’ has no member named ‘driver_data’
/home/yuneng/ipwraw-ng/ipwraw.c: In function ‘show_status’:
/home/yuneng/ipwraw-ng/ipwraw.c:2432:46: error: ‘struct device’ has no member named ‘driver_data’
/home/yuneng/ipwraw-ng/ipwraw.c: In function ‘show_cfg’:
/home/yuneng/ipwraw-ng/ipwraw.c:2443:46: error: ‘struct device’ has no member named ‘driver_data’
/home/yuneng/ipwraw-ng/ipwraw.c: In function ‘dump_error_log’:
/home/yuneng/ipwraw-ng/ipwraw.c:2460:46: error: ‘struct device’ has no member named ‘driver_data’
/home/yuneng/ipwraw-ng/ipwraw.c: In function ‘dump_event_log’:
/home/yuneng/ipwraw-ng/ipwraw.c:2474:46: error: ‘struct device’ has no member named ‘driver_data’
/home/yuneng/ipwraw-ng/ipwraw.c: In function ‘show_rf_kill’:
/home/yuneng/ipwraw-ng/ipwraw.c:2488:46: error: ‘struct device’ has no member named ‘driver_data’
/home/yuneng/ipwraw-ng/ipwraw.c: In function ‘store_rf_kill’:
/home/yuneng/ipwraw-ng/ipwraw.c:2545:46: error: ‘struct device’ has no member named ‘driver_data’
/home/yuneng/ipwraw-ng/ipwraw.c: In function ‘ipw_irq_handle_error’:
/home/yuneng/ipwraw-ng/ipwraw.c:2596:2: error: ‘TASK_INTERRUPTIBLE’ undeclared (first use in this function)
/home/yuneng/ipwraw-ng/ipwraw.c: In function ‘ipw_nic_reset’:
/home/yuneng/ipwraw-ng/ipwraw.c:4991:2: error: ‘TASK_INTERRUPTIBLE’ undeclared (first use in this function)
/home/yuneng/ipwraw-ng/ipwraw.c: In function ‘ipw_handle_promiscuous_tx’:
/home/yuneng/ipwraw-ng/ipwraw.c:6526:24: error: ‘IEEE80211_RADIOTAP_HDRLEN’ undeclared (first use in this function)
/home/yuneng/ipwraw-ng/ipwraw.c: In function ‘ipw_tx_complete’:
/home/yuneng/ipwraw-ng/ipwraw.c:6841:3: error: ‘TASK_INTERRUPTIBLE’ undeclared (first use in this function)
/home/yuneng/ipwraw-ng/ipwraw.c: In function ‘ipw_rx_handle’:
/home/yuneng/ipwraw-ng/ipwraw.c:7187:6: error: ‘TASK_INTERRUPTIBLE’ undeclared (first use in this function)
/home/yuneng/ipwraw-ng/ipwraw.c: In function ‘ipw_bg_rf_kill’:
/home/yuneng/ipwraw-ng/ipwraw.c:7751:2: error: ‘TASK_INTERRUPTIBLE’ undeclared (first use in this function)
/home/yuneng/ipwraw-ng/ipwraw.c: In function ‘ipw_down’:
/home/yuneng/ipwraw-ng/ipwraw.c:8160:2: error: ‘TASK_INTERRUPTIBLE’ undeclared (first use in this function)
/home/yuneng/ipwraw-ng/ipwraw.c: In function ‘ipw_prom_alloc’:
/home/yuneng/ipwraw-ng/ipwraw.c:8375:20: error: ‘struct net_device’ has no member named ‘open’
/home/yuneng/ipwraw-ng/ipwraw.c:8376:20: error: ‘struct net_device’ has no member named ‘stop’
/home/yuneng/ipwraw-ng/ipwraw.c:8377:20: error: ‘struct net_device’ has no member named ‘get_stats’
/home/yuneng/ipwraw-ng/ipwraw.c:8378:20: error: ‘struct net_device’ has no member named ‘hard_start_xmit’
/home/yuneng/ipwraw-ng/ipwraw.c: In function ‘ipw_pci_probe’:
/home/yuneng/ipwraw-ng/ipwraw.c:8897:9: error: ‘struct net_device’ has no member named ‘hard_start_xmit’
/home/yuneng/ipwraw-ng/ipwraw.c:8898:9: error: ‘struct net_device’ has no member named ‘open’
/home/yuneng/ipwraw-ng/ipwraw.c:8899:9: error: ‘struct net_device’ has no member named ‘stop’
/home/yuneng/ipwraw-ng/ipwraw.c:8900:9: error: ‘struct net_device’ has no member named ‘get_stats’
/home/yuneng/ipwraw-ng/ipwraw.c:8901:9: error: ‘struct net_device’ has no member named ‘set_mac_address’
make[2]: *** [/home/yuneng/ipwraw-ng/ipwraw.o] Error 1
make[1]: *** [_module_/home/yuneng/ipwraw-ng] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.38-10-generic'
make: *** [modules] Error 2

```
So, i was wondering whether the driver_data file has been moved to another folder as i cant find the file as instructed by u (dev_get_drvdata)(yours is using 10.04 while mine 11.04, so there might be a difference i guess).
Lets say the driver_data file in 10.04 and 11.04 is the same, then another problem is how do i use dev_get_drvdata(struct *device) to access the data?

Thankyou for yr information anyway,
Yuneng.

---

