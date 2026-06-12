---
title: "Network Manager Giving Problem with Mobile Broadband"
date: 2009-10-18
forum: Networking &amp; Wireless
---

### Post by kunalgautam on 2009-10-18
I'm having strange problem with my network manager. 
Problem 1 # Disconnection Option Not working
Problem 2 # I discconect using "Enable Networking" Option, After enabling it again I'm unable to Connect, it says ( as per /var/log/syslog )
```


Oct 18 14:47:49 kunal-desktop pppd[10460]: pppd 2.4.5 started by root, uid 0
Oct 18 14:47:49 kunal-desktop NetworkManager: <debug> [1255857469.489006] nm_ppp_manager_start(): ppp started with pid 10460 
Oct 18 14:47:49 kunal-desktop NetworkManager: <info>  Activation (ttyUSB0) Stage 2 of 5 (Device Configure) complete. 
Oct 18 14:47:49 kunal-desktop pppd[10460]: Using interface ppp0
Oct 18 14:47:49 kunal-desktop pppd[10460]: Connect: ppp0 <--> /dev/ttyUSB0
Oct 18 14:47:49 kunal-desktop pppd[10460]: Unable to obtain CHAP password for cdma on  from plugin
Oct 18 14:47:49 kunal-desktop pppd[10460]: No CHAP secret found for authenticating us to 
Oct 18 14:47:49 kunal-desktop pppd[10460]: CHAP authentication failed: Password mismatch^M^J
Oct 18 14:47:49 kunal-desktop pppd[10460]: CHAP authentication failed
Oct 18 14:47:50 kunal-desktop pppd[10460]: Connection terminated.
Oct 18 14:47:51 kunal-desktop pppd[10460]: Exit.
Oct 18 14:47:51 kunal-desktop NetworkManager: <WARN>  ppp_exit_code(): ppp pid 10460 exited with error: Authentication error. We failed to authenticate ourselves to the peer. Maybe bad account or password? 
Oct 18 14:47:51 kunal-desktop NetworkManager: <debug> [1255857471.053493] ppp_watch_cb(): ppp pid 10460 cleaned up 
Oct 18 14:47:51 kunal-desktop NetworkManager: <info>  (ttyUSB0): device state change: 5 -> 9 
Oct 18 14:47:51 kunal-desktop NetworkManager: <debug> [1255857471.053650] nm_serial_device_close(): Closing device 'ttyUSB0' 
Oct 18 14:47:51 kunal-desktop NetworkManager: <info>  Marking connection 'Bharat Sanchar Nigam Ltd.' invalid. 
Oct 18 14:47:51 kunal-desktop NetworkManager: <info>  Activation (ttyUSB0) failed. 
Oct 18 14:47:51 kunal-desktop NetworkManager: <info>  (ttyUSB0): device state change: 9 -> 3 
Oct 18 14:47:51 kunal-desktop NetworkManager: <info>  (ttyUSB0): deactivating device (reason: 0). 
Oct 18 14:47:51 kunal-desktop NetworkManager: nm_system_device_flush_ip4_routes_with_iface: assertion `iface_idx >= 0' failed
Oct 18 14:47:51 kunal-desktop NetworkManager: nm_system_device_flush_ip4_addresses_with_iface: assertion `iface_idx >= 0' failed



```

And still I'm able to connect via WVDIAL

---

