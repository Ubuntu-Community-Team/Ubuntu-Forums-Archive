---
title: "Atheros AR5212 802.11abg NIC Not working"
date: 2009-10-31
forum: Networking &amp; Wireless
---

### Post by dinoman1989 on 2009-10-31
Hello,

I just upgraded from 9.04 to 9.10, and my wireless broke.  I have a lenovo T61.  As the subject suggests, I'm using an AR5212 802.11abg NIC from Atheros.  I already added ath5k to my modules, and commented the madwifi.conf file to un-blacklist ath5k and blacklist all the madwifi stuff.

The error:
```
root@adamtux:/etc# ifconfig wlan0 up
SIOCSIFFLAGS: Unknown error 132

```The info:```

  *-network DISABLED
       description: Wireless interface
       product: AR5212 802.11abg NIC
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 01
       serial: 00:1c:26:10:d9:0d
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath5k latency=0 multicast=yes wireless=IEEE 802.11abg
       resources: irq:17 memory:df3f0000-df3fffff

``````
# iwconfig wlan0
wlan0     IEEE 802.11abg  Mode:Managed  Access Point: Not-Associated   
          Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off

```Any more info I can provide, I'd be happy to do so.  I'm pretty desperate to get this fixed, so please help!

Thanks,
Adam

---

### Post by dinoman1989 on 2009-10-31
Alright, I solved the problem myself.  The solution was to disable ath5k and install madwifi from source (the version in synaptic wasn't working, blacklist ath5k and unblacklist madwifi).

---

### Post by jshayden on 2009-11-01
That is how I got mine working in Jaunty, but it isn't working for me in Karmic.  I have a z60t.  Which version of madwifi did you install?

Thanks,
Josh

---

### Post by gnu4vn on 2009-11-09
I got same problem.

:(

Error when compile madwifi:

andv@skipper:~/madwifi-0.9.4$ make
Checking requirements... ok.
Checking kernel configuration... ok.
make -C /lib/modules/2.6.31-15-generic/build SUBDIRS=/home/andv/madwifi-0.9.4 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-15-generic'
  CC [M]  /home/andv/madwifi-0.9.4/ath/if_ath.o
In file included from /home/andv/madwifi-0.9.4/ath/../net80211/ieee80211_monitor.h:45,
                 from /home/andv/madwifi-0.9.4/ath/if_ath.c:71:
/home/andv/madwifi-0.9.4/ath/../ath/if_athvar.h:98: error: conflicting types for 'irqreturn_t'
include/linux/irqreturn.h:16: note: previous declaration of 'irqreturn_t' was here
/home/andv/madwifi-0.9.4/ath/if_ath.c: In function 'ath_attach':
/home/andv/madwifi-0.9.4/ath/if_ath.c:402: error: 'struct net_device' has no member named 'priv'
/home/andv/madwifi-0.9.4/ath/if_ath.c:678: error: 'struct net_device' has no member named 'open'
/home/andv/madwifi-0.9.4/ath/if_ath.c:679: error: 'struct net_device' has no member named 'stop'
/home/andv/madwifi-0.9.4/ath/if_ath.c:680: error: 'struct net_device' has no member named 'hard_start_xmit'
/home/andv/madwifi-0.9.4/ath/if_ath.c:681: error: 'struct net_device' has no member named 'tx_timeout'
/home/andv/madwifi-0.9.4/ath/if_ath.c:683: error: 'struct net_device' has no member named 'set_multicast_list'
/home/andv/madwifi-0.9.4/ath/if_ath.c:684: error: 'struct net_device' has no member named 'do_ioctl'
/home/andv/madwifi-0.9.4/ath/if_ath.c:685: error: 'struct net_device' has no member named 'get_stats'
/home/andv/madwifi-0.9.4/ath/if_ath.c:686: error: 'struct net_device' has no member named 'set_mac_address'
/home/andv/madwifi-0.9.4/ath/if_ath.c:687: error: 'struct net_device' has no member named 'change_mtu'
/home/andv/madwifi-0.9.4/ath/if_ath.c: In function 'ath_detach':
/home/andv/madwifi-0.9.4/ath/if_ath.c:958: error: 'struct net_device' has no member named 'priv'
/home/andv/madwifi-0.9.4/ath/if_ath.c:1005: error: 'struct net_device' has no member named 'stop'
/home/andv/madwifi-0.9.4/ath/if_ath.c: In function 'ath_vap_create':
/home/andv/madwifi-0.9.4/ath/if_ath.c:1014: error: 'struct net_device' has no member named 'priv'
/home/andv/madwifi-0.9.4/ath/if_ath.c:1084: error: 'struct net_device' has no member named 'priv'
/home/andv/madwifi-0.9.4/ath/if_ath.c: In function 'ath_vap_delete':
/home/andv/madwifi-0.9.4/ath/if_ath.c:1248: error: 'struct net_device' has no member named 'priv'
/home/andv/madwifi-0.9.4/ath/if_ath.c: In function 'ath_suspend':
/home/andv/madwifi-0.9.4/ath/if_ath.c:1350: error: 'struct net_device' has no member named 'priv'
/home/andv/madwifi-0.9.4/ath/if_ath.c: In function 'ath_resume':
/home/andv/madwifi-0.9.4/ath/if_ath.c:1359: error: 'struct net_device' has no member named 'priv'
/home/andv/madwifi-0.9.4/ath/if_ath.c: In function 'ath_intr':
/home/andv/madwifi-0.9.4/ath/if_ath.c:1652: error: 'struct net_device' has no member named 'priv'
/home/andv/madwifi-0.9.4/ath/if_ath.c: In function 'ath_bmiss_tasklet':
/home/andv/madwifi-0.9.4/ath/if_ath.c:1843: error: 'struct net_device' has no member named 'priv'
/home/andv/madwifi-0.9.4/ath/if_ath.c: In function 'ath_init':
/home/andv/madwifi-0.9.4/ath/if_ath.c:1886: error: 'struct net_device' has no member named 'priv'
/home/andv/madwifi-0.9.4/ath/if_ath.c: In function 'ath_stop_locked':
/home/andv/madwifi-0.9.4/ath/if_ath.c:2014: error: 'struct net_device' has no member named 'priv'
/home/andv/madwifi-0.9.4/ath/if_ath.c: In function 'ath_stop':
/home/andv/madwifi-0.9.4/ath/if_ath.c:2078: error: 'struct net_device' has no member named 'priv'
/home/andv/madwifi-0.9.4/ath/if_ath.c: In function 'ath_reset':
/home/andv/madwifi-0.9.4/ath/if_ath.c:2182: error: 'struct net_device' has no member named 'priv'
/home/andv/madwifi-0.9.4/ath/if_ath.c: In function 'ath_tx_startraw':
/home/andv/madwifi-0.9.4/ath/if_ath.c:2343: error: 'struct net_device' has no member named 'priv'
/home/andv/madwifi-0.9.4/ath/if_ath.c: In function 'ath_hardstart':
/home/andv/madwifi-0.9.4/ath/if_ath.c:2558: error: 'struct net_device' has no member named 'priv'
/home/andv/madwifi-0.9.4/ath/if_ath.c: In function 'ath_mgtstart':
/home/andv/madwifi-0.9.4/ath/if_ath.c:2875: error: 'struct net_device' has no member named 'priv'
/home/andv/madwifi-0.9.4/ath/if_ath.c: In function 'ath_key_alloc':
/home/andv/madwifi-0.9.4/ath/if_ath.c:3237: error: 'struct net_device' has no member named 'priv'
/home/andv/madwifi-0.9.4/ath/if_ath.c: In function 'ath_key_delete':
/home/andv/madwifi-0.9.4/ath/if_ath.c:3304: error: 'struct net_device' has no member named 'priv'
/home/andv/madwifi-0.9.4/ath/if_ath.c: In function 'ath_key_set':
/home/andv/madwifi-0.9.4/ath/if_ath.c:3380: error: 'struct net_device' has no member named 'priv'
/home/andv/madwifi-0.9.4/ath/if_ath.c: In function 'ath_key_update_begin':
/home/andv/madwifi-0.9.4/ath/if_ath.c:3395: error: 'struct net_device' has no member named 'priv'
/home/andv/madwifi-0.9.4/ath/if_ath.c: In function 'ath_key_update_end':
/home/andv/madwifi-0.9.4/ath/if_ath.c:3416: error: 'struct net_device' has no member named 'priv'
/home/andv/madwifi-0.9.4/ath/if_ath.c: In function 'ath_mode_init':
/home/andv/madwifi-0.9.4/ath/if_ath.c:3504: error: 'struct net_device' has no member named 'priv'
/home/andv/madwifi-0.9.4/ath/if_ath.c: In function 'ath_updateslot':
/home/andv/madwifi-0.9.4/ath/if_ath.c:3555: error: 'struct net_device' has no member named 'priv'
/home/andv/madwifi-0.9.4/ath/if_ath.c: In function 'ath_beacon_dturbo_config':
/home/andv/madwifi-0.9.4/ath/if_ath.c:3585: error: 'struct net_device' has no member named 'priv'
/home/andv/madwifi-0.9.4/ath/if_ath.c: In function 'ath_beacon_dturbo_update':
/home/andv/madwifi-0.9.4/ath/if_ath.c:3633: error: 'struct net_device' has no member named 'priv'
/home/andv/madwifi-0.9.4/ath/if_ath.c: In function 'ath_turbo_switch_mode':
/home/andv/madwifi-0.9.4/ath/if_ath.c:3776: error: 'struct net_device' has no member named 'priv'
/home/andv/madwifi-0.9.4/ath/if_ath.c: In function 'ath_bstuck_tasklet':
/home/andv/madwifi-0.9.4/ath/if_ath.c:4368: error: 'struct net_device' has no member named 'priv'
/home/andv/madwifi-0.9.4/ath/if_ath.c: In function 'ath_node_alloc':
/home/andv/madwifi-0.9.4/ath/if_ath.c:4820: error: 'struct net_device' has no member named 'priv'
/home/andv/madwifi-0.9.4/ath/if_ath.c: In function 'ath_node_cleanup':
/home/andv/madwifi-0.9.4/ath/if_ath.c:4855: error: 'struct net_device' has no member named 'priv'
/home/andv/madwifi-0.9.4/ath/if_ath.c: In function 'ath_node_free':
/home/andv/madwifi-0.9.4/ath/if_ath.c:4909: error: 'struct net_device' has no member named 'priv'
/home/andv/madwifi-0.9.4/ath/if_ath.c: In function 'ath_rx_capture':
/home/andv/madwifi-0.9.4/ath/if_ath.c:5404: error: 'struct net_device' has no member named 'priv'
/home/andv/madwifi-0.9.4/ath/if_ath.c: In function 'ath_tx_capture':
/home/andv/madwifi-0.9.4/ath/if_ath.c:5437: error: 'struct net_device' has no member named 'priv'
/home/andv/madwifi-0.9.4/ath/if_ath.c: In function 'ath_recv_mgmt':
/home/andv/madwifi-0.9.4/ath/if_ath.c:5502: error: 'struct net_device' has no member named 'priv'
/home/andv/madwifi-0.9.4/ath/if_ath.c: In function 'ath_rx_tasklet':
/home/andv/madwifi-0.9.4/ath/if_ath.c:5574: error: 'struct net_device' has no member named 'priv'
/home/andv/madwifi-0.9.4/ath/if_ath.c: In function 'ath_grppoll_start':
/home/andv/madwifi-0.9.4/ath/if_ath.c:6013: error: 'struct net_device' has no member named 'priv'
/home/andv/madwifi-0.9.4/ath/if_ath.c: In function 'ath_grppoll_stop':
/home/andv/madwifi-0.9.4/ath/if_ath.c:6226: error: 'struct net_device' has no member named 'priv'
/home/andv/madwifi-0.9.4/ath/if_ath.c: In function 'ath_wme_update':
/home/andv/madwifi-0.9.4/ath/if_ath.c:6441: error: 'struct net_device' has no member named 'priv'
/home/andv/madwifi-0.9.4/ath/if_ath.c: In function 'ath_uapsd_flush':
/home/andv/madwifi-0.9.4/ath/if_ath.c:6460: error: 'struct net_device' has no member named 'priv'
/home/andv/madwifi-0.9.4/ath/if_ath.c: In function 'ath_tx_start':
/home/andv/madwifi-0.9.4/ath/if_ath.c:6655: error: 'struct net_device' has no member named 'priv'
/home/andv/madwifi-0.9.4/ath/if_ath.c: In function 'ath_tx_tasklet_q0':
/home/andv/madwifi-0.9.4/ath/if_ath.c:7495: error: 'struct net_device' has no member named 'priv'
/home/andv/madwifi-0.9.4/ath/if_ath.c: In function 'ath_tx_tasklet_q0123':
/home/andv/madwifi-0.9.4/ath/if_ath.c:7516: error: 'struct net_device' has no member named 'priv'
/home/andv/madwifi-0.9.4/ath/if_ath.c: In function 'ath_tx_tasklet':
/home/andv/madwifi-0.9.4/ath/if_ath.c:7551: error: 'struct net_device' has no member named 'priv'
/home/andv/madwifi-0.9.4/ath/if_ath.c: In function 'ath_tx_timeout':
/home/andv/madwifi-0.9.4/ath/if_ath.c:7574: error: 'struct net_device' has no member named 'priv'
/home/andv/madwifi-0.9.4/ath/if_ath.c: In function 'ath_calibrate':
/home/andv/madwifi-0.9.4/ath/if_ath.c:7937: error: 'struct net_device' has no member named 'priv'
/home/andv/madwifi-0.9.4/ath/if_ath.c: In function 'ath_scan_start':
/home/andv/madwifi-0.9.4/ath/if_ath.c:8003: error: 'struct net_device' has no member named 'priv'
/home/andv/madwifi-0.9.4/ath/if_ath.c: In function 'ath_scan_end':
/home/andv/madwifi-0.9.4/ath/if_ath.c:8023: error: 'struct net_device' has no member named 'priv'
/home/andv/madwifi-0.9.4/ath/if_ath.c: In function 'ath_set_channel':
/home/andv/madwifi-0.9.4/ath/if_ath.c:8041: error: 'struct net_device' has no member named 'priv'
/home/andv/madwifi-0.9.4/ath/if_ath.c: In function 'ath_set_coverageclass':
/home/andv/madwifi-0.9.4/ath/if_ath.c:8057: error: 'struct net_device' has no member named 'priv'
/home/andv/madwifi-0.9.4/ath/if_ath.c: In function 'ath_mhz2ieee':
/home/andv/madwifi-0.9.4/ath/if_ath.c:8067: error: 'struct net_device' has no member named 'priv'
/home/andv/madwifi-0.9.4/ath/if_ath.c: In function 'ath_newstate':
/home/andv/madwifi-0.9.4/ath/if_ath.c:8082: error: 'struct net_device' has no member named 'priv'
/home/andv/madwifi-0.9.4/ath/if_ath.c: In function 'ath_setup_stationkey':
/home/andv/madwifi-0.9.4/ath/if_ath.c:8471: error: 'struct net_device' has no member named 'priv'
/home/andv/madwifi-0.9.4/ath/if_ath.c: In function 'ath_newassoc':
/home/andv/madwifi-0.9.4/ath/if_ath.c:8631: error: 'struct net_device' has no member named 'priv'
/home/andv/madwifi-0.9.4/ath/if_ath.c: In function 'ath_getchannels':
/home/andv/madwifi-0.9.4/ath/if_ath.c:8662: error: 'struct net_device' has no member named 'priv'
/home/andv/madwifi-0.9.4/ath/if_ath.c: In function 'ath_xr_rate_setup':
/home/andv/madwifi-0.9.4/ath/if_ath.c:8832: error: 'struct net_device' has no member named 'priv'
/home/andv/madwifi-0.9.4/ath/if_ath.c: In function 'ath_setup_subrates':
/home/andv/madwifi-0.9.4/ath/if_ath.c:8861: error: 'struct net_device' has no member named 'priv'
/home/andv/madwifi-0.9.4/ath/if_ath.c: In function 'ath_rate_setup':
/home/andv/madwifi-0.9.4/ath/if_ath.c:8904: error: 'struct net_device' has no member named 'priv'
/home/andv/madwifi-0.9.4/ath/if_ath.c: In function 'ath_getstats':
/home/andv/madwifi-0.9.4/ath/if_ath.c:9141: error: 'struct net_device' has no member named 'priv'
/home/andv/madwifi-0.9.4/ath/if_ath.c: In function 'ath_set_mac_address':
/home/andv/madwifi-0.9.4/ath/if_ath.c:9164: error: 'struct net_device' has no member named 'priv'
/home/andv/madwifi-0.9.4/ath/if_ath.c: In function 'ath_change_mtu':
/home/andv/madwifi-0.9.4/ath/if_ath.c:9196: error: 'struct net_device' has no member named 'priv'
/home/andv/madwifi-0.9.4/ath/if_ath.c: In function 'ath_ioctl':
/home/andv/madwifi-0.9.4/ath/if_ath.c:9283: error: 'struct net_device' has no member named 'priv'
/home/andv/madwifi-0.9.4/ath/if_ath.c: In function 'ath_announce':
/home/andv/madwifi-0.9.4/ath/if_ath.c:9779: error: 'struct net_device' has no member named 'priv'
/home/andv/madwifi-0.9.4/ath/if_ath.c: In function 'ath_rcv_dev_event':
/home/andv/madwifi-0.9.4/ath/if_ath.c:9926: error: 'struct net_device' has no member named 'priv'
/home/andv/madwifi-0.9.4/ath/if_ath.c:9928: error: 'struct net_device' has no member named 'open'
make[3]: *** [/home/andv/madwifi-0.9.4/ath/if_ath.o] Error 1
make[2]: *** [/home/andv/madwifi-0.9.4/ath] Error 2
make[1]: *** [_module_/home/andv/madwifi-0.9.4] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-15-generic'
make: *** [modules] Error 2
andv@skipper:~/madwifi-0.9.4$ 
andv@skipper:~/madwifi-0.9.4$ make
Checking requirements... ok.
Checking kernel configuration... ok.
make -C /lib/modules/2.6.31-15-generic/build SUBDIRS=/home/andv/madwifi-0.9.4 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-15-generic'
  CC [M]  /home/andv/madwifi-0.9.4/ath/if_ath.o
In file included from /home/andv/madwifi-0.9.4/ath/../net80211/ieee80211_monitor.h:45,
                 from /home/andv/madwifi-0.9.4/ath/if_ath.c:71:
/home/andv/madwifi-0.9.4/ath/../ath/if_athvar.h:98: error: conflicting types for 'irqreturn_t'
include/linux/irqreturn.h:16: note: previous declaration of 'irqreturn_t' was here
/home/andv/madwifi-0.9.4/ath/if_ath.c: In function 'ath_attach':
/home/andv/madwifi-0.9.4/ath/if_ath.c:402: error: 'struct net_device' has no member named 'priv'
/home/andv/madwifi-0.9.4/ath/if_ath.c:678: error: 'struct net_device' has no member named 'open'
/home/andv/madwifi-0.9.4/ath/if_ath.c:679: error: 'struct net_device' has no member named 'stop'
/home/andv/madwifi-0.9.4/ath/if_ath.c:680: error: 'struct net_device' has no member named 'hard_start_xmit'
/home/andv/madwifi-0.9.4/ath/if_ath.c:681: error: 'struct net_device' has no member named 'tx_timeout'
/home/andv/madwifi-0.9.4/ath/if_ath.c:683: error: 'struct net_device' has no member named 'set_multicast_list'
/home/andv/madwifi-0.9.4/ath/if_ath.c:684: error: 'struct net_device' has no member named 'do_ioctl'
/home/andv/madwifi-0.9.4/ath/if_ath.c:685: error: 'struct net_device' has no member named 'get_stats'
/home/andv/madwifi-0.9.4/ath/if_ath.c:686: error: 'struct net_device' has no member named 'set_mac_address'
/home/andv/madwifi-0.9.4/ath/if_ath.c:687: error: 'struct net_device' has no member named 'change_mtu'
/home/andv/madwifi-0.9.4/ath/if_ath.c: In function 'ath_detach':
/home/andv/madwifi-0.9.4/ath/if_ath.c:958: error: 'struct net_device' has no member named 'priv'
/home/andv/madwifi-0.9.4/ath/if_ath.c:1005: error: 'struct net_device' has no member named 'stop'
/home/andv/madwifi-0.9.4/ath/if_ath.c: In function 'ath_vap_create':
/home/andv/madwifi-0.9.4/ath/if_ath.c:1014: error: 'struct net_device' has no member named 'priv'
/home/andv/madwifi-0.9.4/ath/if_ath.c:1084: error: 'struct net_device' has no member named 'priv'
/home/andv/madwifi-0.9.4/ath/if_ath.c: In function 'ath_vap_delete':
/home/andv/madwifi-0.9.4/ath/if_ath.c:1248: error: 'struct net_device' has no member named 'priv'
/home/andv/madwifi-0.9.4/ath/if_ath.c: In function 'ath_suspend':
/home/andv/madwifi-0.9.4/ath/if_ath.c:1350: error: 'struct net_device' has no member named 'priv'
/home/andv/madwifi-0.9.4/ath/if_ath.c: In function 'ath_resume':
/home/andv/madwifi-0.9.4/ath/if_ath.c:1359: error: 'struct net_device' has no member named 'priv'
/home/andv/madwifi-0.9.4/ath/if_ath.c: In function 'ath_intr':
/home/andv/madwifi-0.9.4/ath/if_ath.c:1652: error: 'struct net_device' has no member named 'priv'
/home/andv/madwifi-0.9.4/ath/if_ath.c: In function 'ath_bmiss_tasklet':
/home/andv/madwifi-0.9.4/ath/if_ath.c:1843: error: 'struct net_device' has no member named 'priv'
/home/andv/madwifi-0.9.4/ath/if_ath.c: In function 'ath_init':
/home/andv/madwifi-0.9.4/ath/if_ath.c:1886: error: 'struct net_device' has no member named 'priv'
/home/andv/madwifi-0.9.4/ath/if_ath.c: In function 'ath_stop_locked':
/home/andv/madwifi-0.9.4/ath/if_ath.c:2014: error: 'struct net_device' has no member named 'priv'
/home/andv/madwifi-0.9.4/ath/if_ath.c: In function 'ath_stop':
/home/andv/madwifi-0.9.4/ath/if_ath.c:2078: error: 'struct net_device' has no member named 'priv'
/home/andv/madwifi-0.9.4/ath/if_ath.c: In function 'ath_reset':
/home/andv/madwifi-0.9.4/ath/if_ath.c:2182: error: 'struct net_device' has no member named 'priv'
/home/andv/madwifi-0.9.4/ath/if_ath.c: In function 'ath_tx_startraw':
/home/andv/madwifi-0.9.4/ath/if_ath.c:2343: error: 'struct net_device' has no member named 'priv'
/home/andv/madwifi-0.9.4/ath/if_ath.c: In function 'ath_hardstart':
/home/andv/madwifi-0.9.4/ath/if_ath.c:2558: error: 'struct net_device' has no member named 'priv'
/home/andv/madwifi-0.9.4/ath/if_ath.c: In function 'ath_mgtstart':
/home/andv/madwifi-0.9.4/ath/if_ath.c:2875: error: 'struct net_device' has no member named 'priv'
/home/andv/madwifi-0.9.4/ath/if_ath.c: In function 'ath_key_alloc':
/home/andv/madwifi-0.9.4/ath/if_ath.c:3237: error: 'struct net_device' has no member named 'priv'
/home/andv/madwifi-0.9.4/ath/if_ath.c: In function 'ath_key_delete':
/home/andv/madwifi-0.9.4/ath/if_ath.c:3304: error: 'struct net_device' has no member named 'priv'
/home/andv/madwifi-0.9.4/ath/if_ath.c: In function 'ath_key_set':
/home/andv/madwifi-0.9.4/ath/if_ath.c:3380: error: 'struct net_device' has no member named 'priv'
/home/andv/madwifi-0.9.4/ath/if_ath.c: In function 'ath_key_update_begin':
/home/andv/madwifi-0.9.4/ath/if_ath.c:3395: error: 'struct net_device' has no member named 'priv'
/home/andv/madwifi-0.9.4/ath/if_ath.c: In function 'ath_key_update_end':
/home/andv/madwifi-0.9.4/ath/if_ath.c:3416: error: 'struct net_device' has no member named 'priv'
/home/andv/madwifi-0.9.4/ath/if_ath.c: In function 'ath_mode_init':
/home/andv/madwifi-0.9.4/ath/if_ath.c:3504: error: 'struct net_device' has no member named 'priv'
/home/andv/madwifi-0.9.4/ath/if_ath.c: In function 'ath_updateslot':
/home/andv/madwifi-0.9.4/ath/if_ath.c:3555: error: 'struct net_device' has no member named 'priv'
/home/andv/madwifi-0.9.4/ath/if_ath.c: In function 'ath_beacon_dturbo_config':
/home/andv/madwifi-0.9.4/ath/if_ath.c:3585: error: 'struct net_device' has no member named 'priv'
/home/andv/madwifi-0.9.4/ath/if_ath.c: In function 'ath_beacon_dturbo_update':
/home/andv/madwifi-0.9.4/ath/if_ath.c:3633: error: 'struct net_device' has no member named 'priv'
/home/andv/madwifi-0.9.4/ath/if_ath.c: In function 'ath_turbo_switch_mode':
/home/andv/madwifi-0.9.4/ath/if_ath.c:3776: error: 'struct net_device' has no member named 'priv'
/home/andv/madwifi-0.9.4/ath/if_ath.c: In function 'ath_bstuck_tasklet':
/home/andv/madwifi-0.9.4/ath/if_ath.c:4368: error: 'struct net_device' has no member named 'priv'
/home/andv/madwifi-0.9.4/ath/if_ath.c: In function 'ath_node_alloc':
/home/andv/madwifi-0.9.4/ath/if_ath.c:4820: error: 'struct net_device' has no member named 'priv'
/home/andv/madwifi-0.9.4/ath/if_ath.c: In function 'ath_node_cleanup':
/home/andv/madwifi-0.9.4/ath/if_ath.c:4855: error: 'struct net_device' has no member named 'priv'
/home/andv/madwifi-0.9.4/ath/if_ath.c: In function 'ath_node_free':
/home/andv/madwifi-0.9.4/ath/if_ath.c:4909: error: 'struct net_device' has no member named 'priv'
/home/andv/madwifi-0.9.4/ath/if_ath.c: In function 'ath_rx_capture':
/home/andv/madwifi-0.9.4/ath/if_ath.c:5404: error: 'struct net_device' has no member named 'priv'
/home/andv/madwifi-0.9.4/ath/if_ath.c: In function 'ath_tx_capture':
/home/andv/madwifi-0.9.4/ath/if_ath.c:5437: error: 'struct net_device' has no member named 'priv'
/home/andv/madwifi-0.9.4/ath/if_ath.c: In function 'ath_recv_mgmt':
/home/andv/madwifi-0.9.4/ath/if_ath.c:5502: error: 'struct net_device' has no member named 'priv'
/home/andv/madwifi-0.9.4/ath/if_ath.c: In function 'ath_rx_tasklet':
/home/andv/madwifi-0.9.4/ath/if_ath.c:5574: error: 'struct net_device' has no member named 'priv'
/home/andv/madwifi-0.9.4/ath/if_ath.c: In function 'ath_grppoll_start':
/home/andv/madwifi-0.9.4/ath/if_ath.c:6013: error: 'struct net_device' has no member named 'priv'
/home/andv/madwifi-0.9.4/ath/if_ath.c: In function 'ath_grppoll_stop':
/home/andv/madwifi-0.9.4/ath/if_ath.c:6226: error: 'struct net_device' has no member named 'priv'
/home/andv/madwifi-0.9.4/ath/if_ath.c: In function 'ath_wme_update':
/home/andv/madwifi-0.9.4/ath/if_ath.c:6441: error: 'struct net_device' has no member named 'priv'
/home/andv/madwifi-0.9.4/ath/if_ath.c: In function 'ath_uapsd_flush':
/home/andv/madwifi-0.9.4/ath/if_ath.c:6460: error: 'struct net_device' has no member named 'priv'
/home/andv/madwifi-0.9.4/ath/if_ath.c: In function 'ath_tx_start':
/home/andv/madwifi-0.9.4/ath/if_ath.c:6655: error: 'struct net_device' has no member named 'priv'
/home/andv/madwifi-0.9.4/ath/if_ath.c: In function 'ath_tx_tasklet_q0':
/home/andv/madwifi-0.9.4/ath/if_ath.c:7495: error: 'struct net_device' has no member named 'priv'
/home/andv/madwifi-0.9.4/ath/if_ath.c: In function 'ath_tx_tasklet_q0123':
/home/andv/madwifi-0.9.4/ath/if_ath.c:7516: error: 'struct net_device' has no member named 'priv'
/home/andv/madwifi-0.9.4/ath/if_ath.c: In function 'ath_tx_tasklet':
/home/andv/madwifi-0.9.4/ath/if_ath.c:7551: error: 'struct net_device' has no member named 'priv'
/home/andv/madwifi-0.9.4/ath/if_ath.c: In function 'ath_tx_timeout':
/home/andv/madwifi-0.9.4/ath/if_ath.c:7574: error: 'struct net_device' has no member named 'priv'
/home/andv/madwifi-0.9.4/ath/if_ath.c: In function 'ath_calibrate':
/home/andv/madwifi-0.9.4/ath/if_ath.c:7937: error: 'struct net_device' has no member named 'priv'
/home/andv/madwifi-0.9.4/ath/if_ath.c: In function 'ath_scan_start':
/home/andv/madwifi-0.9.4/ath/if_ath.c:8003: error: 'struct net_device' has no member named 'priv'
/home/andv/madwifi-0.9.4/ath/if_ath.c: In function 'ath_scan_end':
/home/andv/madwifi-0.9.4/ath/if_ath.c:8023: error: 'struct net_device' has no member named 'priv'
/home/andv/madwifi-0.9.4/ath/if_ath.c: In function 'ath_set_channel':
/home/andv/madwifi-0.9.4/ath/if_ath.c:8041: error: 'struct net_device' has no member named 'priv'
/home/andv/madwifi-0.9.4/ath/if_ath.c: In function 'ath_set_coverageclass':
/home/andv/madwifi-0.9.4/ath/if_ath.c:8057: error: 'struct net_device' has no member named 'priv'
/home/andv/madwifi-0.9.4/ath/if_ath.c: In function 'ath_mhz2ieee':
/home/andv/madwifi-0.9.4/ath/if_ath.c:8067: error: 'struct net_device' has no member named 'priv'
/home/andv/madwifi-0.9.4/ath/if_ath.c: In function 'ath_newstate':
/home/andv/madwifi-0.9.4/ath/if_ath.c:8082: error: 'struct net_device' has no member named 'priv'
/home/andv/madwifi-0.9.4/ath/if_ath.c: In function 'ath_setup_stationkey':
/home/andv/madwifi-0.9.4/ath/if_ath.c:8471: error: 'struct net_device' has no member named 'priv'
/home/andv/madwifi-0.9.4/ath/if_ath.c: In function 'ath_newassoc':
/home/andv/madwifi-0.9.4/ath/if_ath.c:8631: error: 'struct net_device' has no member named 'priv'
/home/andv/madwifi-0.9.4/ath/if_ath.c: In function 'ath_getchannels':
/home/andv/madwifi-0.9.4/ath/if_ath.c:8662: error: 'struct net_device' has no member named 'priv'
/home/andv/madwifi-0.9.4/ath/if_ath.c: In function 'ath_xr_rate_setup':
/home/andv/madwifi-0.9.4/ath/if_ath.c:8832: error: 'struct net_device' has no member named 'priv'
/home/andv/madwifi-0.9.4/ath/if_ath.c: In function 'ath_setup_subrates':
/home/andv/madwifi-0.9.4/ath/if_ath.c:8861: error: 'struct net_device' has no member named 'priv'
/home/andv/madwifi-0.9.4/ath/if_ath.c: In function 'ath_rate_setup':
/home/andv/madwifi-0.9.4/ath/if_ath.c:8904: error: 'struct net_device' has no member named 'priv'
/home/andv/madwifi-0.9.4/ath/if_ath.c: In function 'ath_getstats':
/home/andv/madwifi-0.9.4/ath/if_ath.c:9141: error: 'struct net_device' has no member named 'priv'
/home/andv/madwifi-0.9.4/ath/if_ath.c: In function 'ath_set_mac_address':
/home/andv/madwifi-0.9.4/ath/if_ath.c:9164: error: 'struct net_device' has no member named 'priv'
/home/andv/madwifi-0.9.4/ath/if_ath.c: In function 'ath_change_mtu':
/home/andv/madwifi-0.9.4/ath/if_ath.c:9196: error: 'struct net_device' has no member named 'priv'
/home/andv/madwifi-0.9.4/ath/if_ath.c: In function 'ath_ioctl':
/home/andv/madwifi-0.9.4/ath/if_ath.c:9283: error: 'struct net_device' has no member named 'priv'
/home/andv/madwifi-0.9.4/ath/if_ath.c: In function 'ath_announce':
/home/andv/madwifi-0.9.4/ath/if_ath.c:9779: error: 'struct net_device' has no member named 'priv'
/home/andv/madwifi-0.9.4/ath/if_ath.c: In function 'ath_rcv_dev_event':
/home/andv/madwifi-0.9.4/ath/if_ath.c:9926: error: 'struct net_device' has no member named 'priv'
/home/andv/madwifi-0.9.4/ath/if_ath.c:9928: error: 'struct net_device' has no member named 'open'
make[3]: *** [/home/andv/madwifi-0.9.4/ath/if_ath.o] Error 1
make[2]: *** [/home/andv/madwifi-0.9.4/ath] Error 2
make[1]: *** [_module_/home/andv/madwifi-0.9.4] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-15-generic'
make: *** [modules] Error 2

---

### Post by Ant59 on 2009-11-13
I've got the exact same problem. After googling a bit, I think it's a kernel incompatibility.

---

