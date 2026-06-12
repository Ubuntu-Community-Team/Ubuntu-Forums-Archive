---
title: "hp laserjet pro M1530 MFP"
date: 2011-04-01
forum: Networking &amp; Wireless
---

### Post by scarab on 2011-04-01
Hi

using Kubuntu 10.10, just connected an hp laserjet pro M1530 MFP directly to networking. 

installed it via system settings-printer conf and all goes OK for printing. 

Now trying to scan and no way.
other data: 
I can ping the printer with no problems

when using hp-setup, no way for the device to be found, not even using its IP: 
Error: "/var/tmp/kdecache-scarab" is owned by uid 1000 instead of uid 0.
(4250) KSharedDataCache::Private::mapSharedMemory: Opening cache "/var/tmp/kdecache-scarab/icon-cache.kcache" page size is 4096
(4250) KSharedDataCache::Private::mapSharedMemory: Attached to cache, determining if it must be initialized
(4250) KSharedDataCache::Private::mapSharedMemory: Cache fully initialized -- attached to memory mapping
(4250) KSharedDataCache::Private::mapSharedMemory: 4366336 bytes available out of 10485760
QInotifyFileSystemWatcherEngine::addPaths: inotify_add_watch failed: No such file or directory
QFileSystemWatcher: failed to add paths: /home/scarab/.config/ibus/bus
Bus::open: Can not get ibus-daemon's address. 
IBusInputContext::createInputContext: no connection to ibus-daemon 
Searching... (bus=net, timeout=5, ttl=4, search=(None) desc=0, method=mdns)
error: No devices found on bus: net

when trying to make uri:

scarab@scarab-laptop1:~$ hp-makeuri 192.168.0.143

HP Linux Imaging and Printing System (ver. 3.10.6)
Device URI Creation Utility ver. 5.0

Copyright (c) 2001-9 Hewlett-Packard Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

error: Device not found

hpcheck-r with one only error:
Printer Ready to print. HP_LaserJet_M1536dnf_MFP is idle.  enabled since Fri 01 Apr 2011 10:05:10 AM AMT
warning: Printer is not HPLIP installed. Printers must use the hp: or hpfax: CUPS backend to function in HPLIP.

how to install it in hplip if it keeps being undetected with hp-setup? tried to remove it from printer configuration and the same occurs.

thanks in advance for possible solutions

F

---

