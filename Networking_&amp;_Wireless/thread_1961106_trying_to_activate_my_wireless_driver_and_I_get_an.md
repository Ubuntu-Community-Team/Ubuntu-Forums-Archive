---
title: "trying to activate my wireless driver and I get anerror message"
date: 2012-04-18
forum: Networking &amp; Wireless
---

### Post by bjgar on 2012-04-18
I have a Broadcom  802.11  Linux sta wireless driver for a Broadcom bcm 4321 card. When I try to activate it it  says it's had failed and tells me to look at the log file details which are as follows, I will also include an attachment with the code


```
2012-04-18 11:31:41,011 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB 
instance at 0x8d0ab6c>
2012-04-18 11:31:41,014 DEBUG: reading modalias file /lib/modules/2.6.32-38-generic/
modules.alias
2012-04-18 11:31:41,243 DEBUG: reading modalias file /usr/share/jockey/modaliases/
bcmwl
2012-04-18 11:31:41,255 DEBUG: reading modalias file /usr/share/jockey/modaliases/
disable-upstream-nvidia
2012-04-18 11:31:41,316 DEBUG: reading modalias file /usr/share/jockey/modaliases/
fglrx-modules.alias.override
2012-04-18 11:31:41,323 DEBUG: reading modalias file /usr/share/jockey/modaliases/
nvidia-173
2012-04-18 11:31:41,332 DEBUG: reading modalias file /usr/share/jockey/modaliases/
nvidia-96
2012-04-18 11:31:41,350 DEBUG: reading modalias file /usr/share/jockey/modaliases/
nvidia-current
2012-04-18 11:31:41,381 WARNING: Could not open DriverDB
 cache /var/cache/jockey/
driverdb-OpenPrintingDriverDB.cache: [Errno 2] No such file or directory:
 '/var/cache/jockey/driverdb-OpenPrintingDriverDB.cache'
2012-04-18 11:31:41,777 DEBUG: loading custom handler
 /usr/share/jockey/handlers/broadcom_wl.py
2012-04-18 11:31:41,961 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler

2012-04-18 11:31:41,962 DEBUG: Broadcom STA wireless 
driver availability undetermined, adding to pool
2012-04-18 11:31:41,962 DEBUG: loading custom handler
 /usr/share/jockey/handlers/madwifi.py
2012-04-18 11:31:41,985 WARNING: modinfo for 
module ath_pci failed: ERROR: could not find module ath_pci
 
```

---

### Post by nothingspecial on 2012-04-19
*Thread moved to **Networking & Wireless**.*

---

### Post by bjgar on 2012-04-20
I don't follow

---

