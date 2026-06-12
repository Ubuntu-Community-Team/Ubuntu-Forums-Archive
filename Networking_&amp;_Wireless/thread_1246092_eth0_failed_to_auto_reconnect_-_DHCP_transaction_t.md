---
title: "eth0 failed to auto reconnect - DHCP transaction too long?"
date: 2009-08-21
forum: Networking &amp; Wireless
---

### Post by 6tangos on 2009-08-21
Hi,

Yesterday evening at work our building lost network connectivity for approximately 20 minutes (the building is part of a wider intranet, IP assigned by DHCP). 

This morning my machines failed to automatically reconnect eth0.

I was off-site at the time and required remote access, after unsuccessful ssh login attempts to both my machines (running Ubuntu 9.04) and no ping response I returned expecting to have to restart eth0.

However, all I had to do to solve the problem was check the "Connect automatically" tick box in eth0 settings. After looking in the logs it seems that eth0 was deactivated due to the DHCP transaction taking too long.
(see daemon.log extract below).

Is there a way to extend the timeout value? 
Due to engineering works in our building over the summer it is likely network outages will reoccur, I would rather not have to return to work whilst working off-site simply to re-check the tick box.

Aug 20 17:41:49 mybox dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
Aug 20 17:41:57 mybox dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
Aug 20 17:42:07 mybox dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
Aug 20 17:42:18 mybox dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
Aug 20 17:42:30 mybox NetworkManager: <info>  Device 'eth0' DHCP transaction took too long (>45s), stopping it. 
Aug 20 17:42:30 mybox NetworkManager: <info>  eth0: canceled DHCP transaction, dhcp client pid 13460 
Aug 20 17:42:30 mybox NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Timeout) scheduled... 
Aug 20 17:42:30 mybox NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Timeout) started... 
Aug 20 17:42:30 mybox NetworkManager: <info>  (eth0): device state change: 7 -> 9 
Aug 20 17:42:30 mybox NetworkManager: <info>  Marking connection 'Auto eth0' invalid. 
Aug 20 17:42:30 mybox NetworkManager: <info>  Activation (eth0) failed. 
Aug 20 17:42:30 mybox NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Timeout) complete. 
Aug 20 17:42:30 mybox NetworkManager: <info>  (eth0): device state change: 9 -> 3 
Aug 20 17:42:30 mybox NetworkManager: <info>  (eth0): deactivating device (reason: 0).

---

### Post by rcmadawala on 2009-08-21
hey, these people aren't help to this kind of problems.i have a problem about automatic connect problem. but these people didn't help me.if they give a answer to your problem, you are lucky mate. Finally i went back to windows (because i haven't any option rather than that). 

So if you can, take a look about my problem from here :)

[http://ubuntuforums.org/showthread.php?t=1241614]("http://ubuntuforums.org/showthread.php?t=1241614")

---

### Post by jamest09 on 2009-08-21
> **6tangos said:**
> Hi,

Yesterday evening at work our building lost network connectivity for approximately 20 minutes (the building is part of a wider intranet, IP assigned by DHCP). 

This morning my machines failed to automatically reconnect eth0.

I was off-site at the time and required remote access, after unsuccessful ssh login attempts to both my machines (running Ubuntu 9.04) and no ping response I returned expecting to have to restart eth0.

However, all I had to do to solve the problem was check the "Connect automatically" tick box in eth0 settings. After looking in the logs it seems that eth0 was deactivated due to the DHCP transaction taking too long.
(see daemon.log extract below).

Is there a way to extend the timeout value? 
Due to engineering works in our building over the summer it is likely network outages will reoccur, I would rather not have to return to work whilst working off-site simply to re-check the tick box.

Aug 20 17:41:49 mybox dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
Aug 20 17:41:57 mybox dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
Aug 20 17:42:07 mybox dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
Aug 20 17:42:18 mybox dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
Aug 20 17:42:30 mybox NetworkManager: <info>  Device 'eth0' DHCP transaction took too long (>45s), stopping it. 
Aug 20 17:42:30 mybox NetworkManager: <info>  eth0: canceled DHCP transaction, dhcp client pid 13460 
Aug 20 17:42:30 mybox NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Timeout) scheduled... 
Aug 20 17:42:30 mybox NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Timeout) started... 
Aug 20 17:42:30 mybox NetworkManager: <info>  (eth0): device state change: 7 -> 9 
Aug 20 17:42:30 mybox NetworkManager: <info>  Marking connection 'Auto eth0' invalid. 
Aug 20 17:42:30 mybox NetworkManager: <info>  Activation (eth0) failed. 
Aug 20 17:42:30 mybox NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Timeout) complete. 
Aug 20 17:42:30 mybox NetworkManager: <info>  (eth0): device state change: 9 -> 3 
Aug 20 17:42:30 mybox NetworkManager: <info>  (eth0): deactivating device (reason: 0).

Try configuring you network in /etc/network/interfaces and see if the problem goes away.

---

