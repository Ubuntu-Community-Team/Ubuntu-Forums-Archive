---
title: "madwifi problems"
date: 2011-05-18
forum: Networking &amp; Wireless
---

### Post by w24kw on 2011-05-18
hi, i try to install my d-link dwl-g520 h/w:A1 in master mode with madwifi drivers but:
[B]$ lshw
*-network:1
             description: Wireless interface
             product: Atheros AR5001X+ Wireless Network Adapter
             vendor: Atheros Communications Inc.
             physical id: 5
             bus info: pci@0000:00:05.0
             logical name: wlan0
             version: 01
             serial: 00:80:c8:15:35:8f
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list ethernet physical wireless
             configuration: broadcast=yes driver=ath5k latency=168 maxlatency=28 mingnt=10 multicast=yes wireless=IEEE 802.11bg
             resources: irq:17 memory:2a100000-2a10ffff

---------------------------------------------------------------------------------------------------
$ lspci | grep Atheros
00:05.0 Ethernet controller: Atheros Communications Inc. Atheros AR5001X+ Wireless Network Adapter (rev 01)
---------------------------------------------------------------------------------------------------
$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any
          Mode:Managed  Access Point: Not-Associated   Tx-Power=27 dBm
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

--------------------------------------------------------------------------------------------------
$ sudo make
Checking requirements... ok.
Checking kernel configuration... ok.
make -C /lib/modules/2.6.32-24-generic/build SUBDIRS=/home/irondesk/madwifi-0.9.4 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-24-generic'
  CC [M]  /home/irondesk/madwifi-0.9.4/ath/if_ath.o
In file included from /home/irondesk/madwifi-0.9.4/ath/../net80211/ieee80211_monitor.h:45,
                 from /home/irondesk/madwifi-0.9.4/ath/if_ath.c:71:
/home/irondesk/madwifi-0.9.4/ath/../ath/if_athvar.h:98: error: conflicting types for 'irqreturn_t'
include/linux/irqreturn.h:16: note: previous declaration of 'irqreturn_t' was here
/home/irondesk/madwifi-0.9.4/ath/if_ath.c: In function 'ath_attach':
/home/irondesk/madwifi-0.9.4/ath/if_ath.c:402: error: 'struct net_device' has no member named 'priv'
/home/irondesk/madwifi-0.9.4/ath/if_ath.c:678: error: 'struct net_device' has no member named 'open'
/home/irondesk/madwifi-0.9.4/ath/if_ath.c:679: error: 'struct net_device' has no member named 'stop'
/home/irondesk/madwifi-0.9.4/ath/if_ath.c:680: error: 'struct net_device' has no member named 'hard_start_xmit'
/home/irondesk/madwifi-0.9.4/ath/if_ath.c:681: error: 'struct net_device' has no member named 'tx_timeout'
/home/irondesk/madwifi-0.9.4/ath/if_ath.c:683: error: 'struct net_device' has no member named 'set_multicast_list'
/home/irondesk/madwifi-0.9.4/ath/if_ath.c:684: error: 'struct net_device' has no member named 'do_ioctl'
/home/irondesk/madwifi-0.9.4/ath/if_ath.c:685: error: 'struct net_device' has no member named 'get_stats'
/home/irondesk/madwifi-0.9.4/ath/if_ath.c:686: error: 'struct net_device' has no member named 'set_mac_address'
/home/irondesk/madwifi-0.9.4/ath/if_ath.c:687: error: 'struct net_device' has no member named 'change_mtu'
/home/irondesk/madwifi-0.9.4/ath/if_ath.c: In function 'ath_detach':
/home/irondesk/madwifi-0.9.4/ath/if_ath.c:958: error: 'struct net_device' has no member named 'priv'
/home/irondesk/madwifi-0.9.4/ath/if_ath.c:1005: error: 'struct net_device' has no member named 'stop'
/home/irondesk/madwifi-0.9.4/ath/if_ath.c: In function 'ath_vap_create':
/home/irondesk/madwifi-0.9.4/ath/if_ath.c:1014: error: 'struct net_device' has no member named 'priv'
/home/irondesk/madwifi-0.9.4/ath/if_ath.c:1084: error: 'struct net_device' has no member named 'priv'
/home/irondesk/madwifi-0.9.4/ath/if_ath.c: In function 'ath_vap_delete':
/home/irondesk/madwifi-0.9.4/ath/if_ath.c:1248: error: 'struct net_device' has no member named 'priv'
/home/irondesk/madwifi-0.9.4/ath/if_ath.c: In function 'ath_suspend':
/home/irondesk/madwifi-0.9.4/ath/if_ath.c:1350: error: 'struct net_device' has no member named 'priv'
/home/irondesk/madwifi-0.9.4/ath/if_ath.c: In function 'ath_resume':
/home/irondesk/madwifi-0.9.4/ath/if_ath.c:1359: error: 'struct net_device' has no member named 'priv'
/home/irondesk/madwifi-0.9.4/ath/if_ath.c: In function 'ath_intr':
/home/irondesk/madwifi-0.9.4/ath/if_ath.c:1652: error: 'struct net_device' has no member named 'priv'
/home/irondesk/madwifi-0.9.4/ath/if_ath.c: In function 'ath_bmiss_tasklet':
/home/irondesk/madwifi-0.9.4/ath/if_ath.c:1843: error: 'struct net_device' has no member named 'priv'
/home/irondesk/madwifi-0.9.4/ath/if_ath.c: In function 'ath_init':
/home/irondesk/madwifi-0.9.4/ath/if_ath.c:1886: error: 'struct net_device' has no member named 'priv'
/home/irondesk/madwifi-0.9.4/ath/if_ath.c: In function 'ath_stop_locked':
/home/irondesk/madwifi-0.9.4/ath/if_ath.c:2014: error: 'struct net_device' has no member named 'priv'
/home/irondesk/madwifi-0.9.4/ath/if_ath.c: In function 'ath_stop':
/home/irondesk/madwifi-0.9.4/ath/if_ath.c:2078: error: 'struct net_device' has no member named 'priv'
/home/irondesk/madwifi-0.9.4/ath/if_ath.c: In function 'ath_reset':
/home/irondesk/madwifi-0.9.4/ath/if_ath.c:2182: error: 'struct net_device' has no member named 'priv'
/home/irondesk/madwifi-0.9.4/ath/if_ath.c: In function 'ath_tx_startraw':
/home/irondesk/madwifi-0.9.4/ath/if_ath.c:2343: error: 'struct net_device' has no member named 'priv'
/home/irondesk/madwifi-0.9.4/ath/if_ath.c: In function 'ath_hardstart':
/home/irondesk/madwifi-0.9.4/ath/if_ath.c:2558: error: 'struct net_device' has no member named 'priv'
/home/irondesk/madwifi-0.9.4/ath/if_ath.c: In function 'ath_mgtstart':
/home/irondesk/madwifi-0.9.4/ath/if_ath.c:2875: error: 'struct net_device' has no member named 'priv'
/home/irondesk/madwifi-0.9.4/ath/if_ath.c: In function 'ath_key_alloc':
/home/irondesk/madwifi-0.9.4/ath/if_ath.c:3237: error: 'struct net_device' has no member named 'priv'
/home/irondesk/madwifi-0.9.4/ath/if_ath.c: In function 'ath_key_delete':
/home/irondesk/madwifi-0.9.4/ath/if_ath.c:3304: error: 'struct net_device' has no member named 'priv'
/home/irondesk/madwifi-0.9.4/ath/if_ath.c: In function 'ath_key_set':
/home/irondesk/madwifi-0.9.4/ath/if_ath.c:3380: error: 'struct net_device' has no member named 'priv'
/home/irondesk/madwifi-0.9.4/ath/if_ath.c: In function 'ath_key_update_begin':
/home/irondesk/madwifi-0.9.4/ath/if_ath.c:3395: error: 'struct net_device' has no member named 'priv'
/home/irondesk/madwifi-0.9.4/ath/if_ath.c: In function 'ath_key_update_end':
/home/irondesk/madwifi-0.9.4/ath/if_ath.c:3416: error: 'struct net_device' has no member named 'priv'
/home/irondesk/madwifi-0.9.4/ath/if_ath.c: In function 'ath_mode_init':
/home/irondesk/madwifi-0.9.4/ath/if_ath.c:3504: error: 'struct net_device' has no member named 'priv'
/home/irondesk/madwifi-0.9.4/ath/if_ath.c: In function 'ath_updateslot':
/home/irondesk/madwifi-0.9.4/ath/if_ath.c:3555: error: 'struct net_device' has no member named 'priv'
/home/irondesk/madwifi-0.9.4/ath/if_ath.c: In function 'ath_beacon_dturbo_config':
/home/irondesk/madwifi-0.9.4/ath/if_ath.c:3585: error: 'struct net_device' has no member named 'priv'
/home/irondesk/madwifi-0.9.4/ath/if_ath.c: In function 'ath_beacon_dturbo_update':
/home/irondesk/madwifi-0.9.4/ath/if_ath.c:3633: error: 'struct net_device' has no member named 'priv'
/home/irondesk/madwifi-0.9.4/ath/if_ath.c: In function 'ath_turbo_switch_mode':
/home/irondesk/madwifi-0.9.4/ath/if_ath.c:3776: error: 'struct net_device' has no member named 'priv'
/home/irondesk/madwifi-0.9.4/ath/if_ath.c: In function 'ath_bstuck_tasklet':
/home/irondesk/madwifi-0.9.4/ath/if_ath.c:4368: error: 'struct net_device' has no member named 'priv'
/home/irondesk/madwifi-0.9.4/ath/if_ath.c: In function 'ath_node_alloc':
/home/irondesk/madwifi-0.9.4/ath/if_ath.c:4820: error: 'struct net_device' has no member named 'priv'
/home/irondesk/madwifi-0.9.4/ath/if_ath.c: In function 'ath_node_cleanup':
/home/irondesk/madwifi-0.9.4/ath/if_ath.c:4855: error: 'struct net_device' has no member named 'priv'
/home/irondesk/madwifi-0.9.4/ath/if_ath.c: In function 'ath_node_free':
/home/irondesk/madwifi-0.9.4/ath/if_ath.c:4909: error: 'struct net_device' has no member named 'priv'
/home/irondesk/madwifi-0.9.4/ath/if_ath.c: In function 'ath_rx_capture':
/home/irondesk/madwifi-0.9.4/ath/if_ath.c:5404: error: 'struct net_device' has no member named 'priv'
/home/irondesk/madwifi-0.9.4/ath/if_ath.c: In function 'ath_tx_capture':
/home/irondesk/madwifi-0.9.4/ath/if_ath.c:5437: error: 'struct net_device' has no member named 'priv'
/home/irondesk/madwifi-0.9.4/ath/if_ath.c: In function 'ath_recv_mgmt':
/home/irondesk/madwifi-0.9.4/ath/if_ath.c:5502: error: 'struct net_device' has no member named 'priv'
/home/irondesk/madwifi-0.9.4/ath/if_ath.c: In function 'ath_rx_tasklet':
/home/irondesk/madwifi-0.9.4/ath/if_ath.c:5574: error: 'struct net_device' has no member named 'priv'
/home/irondesk/madwifi-0.9.4/ath/if_ath.c: In function 'ath_grppoll_start':
/home/irondesk/madwifi-0.9.4/ath/if_ath.c:6013: error: 'struct net_device' has no member named 'priv'
/home/irondesk/madwifi-0.9.4/ath/if_ath.c: In function 'ath_grppoll_stop':
/home/irondesk/madwifi-0.9.4/ath/if_ath.c:6226: error: 'struct net_device' has no member named 'priv'
/home/irondesk/madwifi-0.9.4/ath/if_ath.c: In function 'ath_wme_update':
/home/irondesk/madwifi-0.9.4/ath/if_ath.c:6441: error: 'struct net_device' has no member named 'priv'
/home/irondesk/madwifi-0.9.4/ath/if_ath.c: In function 'ath_uapsd_flush':
/home/irondesk/madwifi-0.9.4/ath/if_ath.c:6460: error: 'struct net_device' has no member named 'priv'
/home/irondesk/madwifi-0.9.4/ath/if_ath.c: In function 'ath_tx_start':
/home/irondesk/madwifi-0.9.4/ath/if_ath.c:6655: error: 'struct net_device' has no member named 'priv'
/home/irondesk/madwifi-0.9.4/ath/if_ath.c: In function 'ath_tx_tasklet_q0':
/home/irondesk/madwifi-0.9.4/ath/if_ath.c:7495: error: 'struct net_device' has no member named 'priv'
/home/irondesk/madwifi-0.9.4/ath/if_ath.c: In function 'ath_tx_tasklet_q0123':
/home/irondesk/madwifi-0.9.4/ath/if_ath.c:7516: error: 'struct net_device' has no member named 'priv'
/home/irondesk/madwifi-0.9.4/ath/if_ath.c: In function 'ath_tx_tasklet':
/home/irondesk/madwifi-0.9.4/ath/if_ath.c:7551: error: 'struct net_device' has no member named 'priv'
/home/irondesk/madwifi-0.9.4/ath/if_ath.c: In function 'ath_tx_timeout':
/home/irondesk/madwifi-0.9.4/ath/if_ath.c:7574: error: 'struct net_device' has no member named 'priv'
/home/irondesk/madwifi-0.9.4/ath/if_ath.c: In function 'ath_calibrate':
/home/irondesk/madwifi-0.9.4/ath/if_ath.c:7937: error: 'struct net_device' has no member named 'priv'
/home/irondesk/madwifi-0.9.4/ath/if_ath.c: In function 'ath_scan_start':
/home/irondesk/madwifi-0.9.4/ath/if_ath.c:8003: error: 'struct net_device' has no member named 'priv'
/home/irondesk/madwifi-0.9.4/ath/if_ath.c: In function 'ath_scan_end':
/home/irondesk/madwifi-0.9.4/ath/if_ath.c:8023: error: 'struct net_device' has no member named 'priv'
/home/irondesk/madwifi-0.9.4/ath/if_ath.c: In function 'ath_set_channel':
/home/irondesk/madwifi-0.9.4/ath/if_ath.c:8041: error: 'struct net_device' has no member named 'priv'
/home/irondesk/madwifi-0.9.4/ath/if_ath.c: In function 'ath_set_coverageclass':
/home/irondesk/madwifi-0.9.4/ath/if_ath.c:8057: error: 'struct net_device' has no member named 'priv'
/home/irondesk/madwifi-0.9.4/ath/if_ath.c: In function 'ath_mhz2ieee':
/home/irondesk/madwifi-0.9.4/ath/if_ath.c:8067: error: 'struct net_device' has no member named 'priv'
/home/irondesk/madwifi-0.9.4/ath/if_ath.c: In function 'ath_newstate':
/home/irondesk/madwifi-0.9.4/ath/if_ath.c:8082: error: 'struct net_device' has no member named 'priv'
/home/irondesk/madwifi-0.9.4/ath/if_ath.c: In function 'ath_setup_stationkey':
/home/irondesk/madwifi-0.9.4/ath/if_ath.c:8471: error: 'struct net_device' has no member named 'priv'
/home/irondesk/madwifi-0.9.4/ath/if_ath.c: In function 'ath_newassoc':
/home/irondesk/madwifi-0.9.4/ath/if_ath.c:8631: error: 'struct net_device' has no member named 'priv'
/home/irondesk/madwifi-0.9.4/ath/if_ath.c: In function 'ath_getchannels':
/home/irondesk/madwifi-0.9.4/ath/if_ath.c:8662: error: 'struct net_device' has no member named 'priv'
/home/irondesk/madwifi-0.9.4/ath/if_ath.c: In function 'ath_xr_rate_setup':
/home/irondesk/madwifi-0.9.4/ath/if_ath.c:8832: error: 'struct net_device' has no member named 'priv'
/home/irondesk/madwifi-0.9.4/ath/if_ath.c: In function 'ath_setup_subrates':
/home/irondesk/madwifi-0.9.4/ath/if_ath.c:8861: error: 'struct net_device' has no member named 'priv'
/home/irondesk/madwifi-0.9.4/ath/if_ath.c: In function 'ath_rate_setup':
/home/irondesk/madwifi-0.9.4/ath/if_ath.c:8904: error: 'struct net_device' has no member named 'priv'
/home/irondesk/madwifi-0.9.4/ath/if_ath.c: In function 'ath_getstats':
/home/irondesk/madwifi-0.9.4/ath/if_ath.c:9141: error: 'struct net_device' has no member named 'priv'
/home/irondesk/madwifi-0.9.4/ath/if_ath.c: In function 'ath_set_mac_address':
/home/irondesk/madwifi-0.9.4/ath/if_ath.c:9164: error: 'struct net_device' has no member named 'priv'
/home/irondesk/madwifi-0.9.4/ath/if_ath.c: In function 'ath_change_mtu':
/home/irondesk/madwifi-0.9.4/ath/if_ath.c:9196: error: 'struct net_device' has no member named 'priv'
/home/irondesk/madwifi-0.9.4/ath/if_ath.c: In function 'ath_ioctl':
/home/irondesk/madwifi-0.9.4/ath/if_ath.c:9283: error: 'struct net_device' has no member named 'priv'
cc1: warnings being treated as errors
/home/irondesk/madwifi-0.9.4/ath/if_ath.c: In function 'ath_sysctl_halparam':
/home/irondesk/madwifi-0.9.4/ath/if_ath.c:9370: error: passing argument 5 of 'proc_dointvec' from incompatible pointer type
include/linux/sysctl.h:985: note: expected 'loff_t *' but argument is of type 'size_t *'
/home/irondesk/madwifi-0.9.4/ath/if_ath.c:9370: error: too many arguments to function 'proc_dointvec'
/home/irondesk/madwifi-0.9.4/ath/if_ath.c:9562: error: passing argument 5 of 'proc_dointvec' from incompatible pointer type
include/linux/sysctl.h:985: note: expected 'loff_t *' but argument is of type 'size_t *'
/home/irondesk/madwifi-0.9.4/ath/if_ath.c:9562: error: too many arguments to function 'proc_dointvec'
/home/irondesk/madwifi-0.9.4/ath/if_ath.c: At top level:
/home/irondesk/madwifi-0.9.4/ath/if_ath.c:9574: error: initialization from incompatible pointer type
/home/irondesk/madwifi-0.9.4/ath/if_ath.c:9580: error: initialization from incompatible pointer type
/home/irondesk/madwifi-0.9.4/ath/if_ath.c:9586: error: initialization from incompatible pointer type
/home/irondesk/madwifi-0.9.4/ath/if_ath.c:9592: error: initialization from incompatible pointer type
/home/irondesk/madwifi-0.9.4/ath/if_ath.c:9598: error: initialization from incompatible pointer type
/home/irondesk/madwifi-0.9.4/ath/if_ath.c:9604: error: initialization from incompatible pointer type
/home/irondesk/madwifi-0.9.4/ath/if_ath.c:9610: error: initialization from incompatible pointer type
/home/irondesk/madwifi-0.9.4/ath/if_ath.c:9616: error: initialization from incompatible pointer type
/home/irondesk/madwifi-0.9.4/ath/if_ath.c:9623: error: initialization from incompatible pointer type
/home/irondesk/madwifi-0.9.4/ath/if_ath.c:9630: error: initialization from incompatible pointer type
/home/irondesk/madwifi-0.9.4/ath/if_ath.c:9636: error: initialization from incompatible pointer type
/home/irondesk/madwifi-0.9.4/ath/if_ath.c:9642: error: initialization from incompatible pointer type
/home/irondesk/madwifi-0.9.4/ath/if_ath.c:9648: error: initialization from incompatible pointer type
/home/irondesk/madwifi-0.9.4/ath/if_ath.c:9654: error: initialization from incompatible pointer type
/home/irondesk/madwifi-0.9.4/ath/if_ath.c:9660: error: initialization from incompatible pointer type
/home/irondesk/madwifi-0.9.4/ath/if_ath.c:9667: error: initialization from incompatible pointer type
/home/irondesk/madwifi-0.9.4/ath/if_ath.c:9673: error: initialization from incompatible pointer type
/home/irondesk/madwifi-0.9.4/ath/if_ath.c:9680: error: initialization from incompatible pointer type
/home/irondesk/madwifi-0.9.4/ath/if_ath.c:9686: error: initialization from incompatible pointer type
/home/irondesk/madwifi-0.9.4/ath/if_ath.c: In function 'ath_announce':
/home/irondesk/madwifi-0.9.4/ath/if_ath.c:9779: error: 'struct net_device' has no member named 'priv'
/home/irondesk/madwifi-0.9.4/ath/if_ath.c: In function 'ath_rcv_dev_event':
/home/irondesk/madwifi-0.9.4/ath/if_ath.c:9926: error: 'struct net_device' has no member named 'priv'
/home/irondesk/madwifi-0.9.4/ath/if_ath.c:9928: error: 'struct net_device' has no member named 'open'
make[3]: *** [/home/irondesk/madwifi-0.9.4/ath/if_ath.o] Error 1
make[2]: *** [/home/irondesk/madwifi-0.9.4/ath] Error 2
make[1]: *** [_module_/home/irondesk/madwifi-0.9.4] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-24-generic'
make: *** [modules] Error 2[/B]

---

### Post by w24kw on 2011-05-27
finally installed madwifi, but now when i try to change the channel SO freezes

---

