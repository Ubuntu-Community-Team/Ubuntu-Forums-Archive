---
title: "Network Manager dies"
date: 2009-01-21
forum: Networking &amp; Wireless
---

### Post by micoams on 2009-01-21
I am having a problem after the Intrepid dist upgrade. The network manager works fine for a while but then just dies. The icon on the gnome panel changes to disconnected. When I left click on it, all the options are grayed out. When I right click on it, "Enable Networking" is checked on, but clicking on it does not do anything. 

I was going through the  '/var/log/daemon.log', and saw a few weird entries:

```
NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see [http://bugs.launchpad.net/bugs/191889](http://bugs.launchpad.net/bugs/191889))
NetworkManager: <WARN>  nm_error_monitoring_device_link_state(): error monitoring wired ethernet link state: error occurred while waiting for data on socket
nm-system-settings: Error parsing file '/etc/NetworkManager/nm-system-settings.conf': No such file or directory
```

I went to the link for the bug #191889 and it does not seem to be related to the problem I am experiencing.

I checked the file '/etc/NetworkManager/nm-system-settings.conf', and it does exist.


When this happens the network connections still work. I am able to surf (on Firefox), but it is noticeably slower. Once I restart the computer, the Network Manager works fine. But, after some time it dies again. 

It keeps happening. I am not sure what is triggering it. I need help with this. I can post the entire daemon.log if someone thinks it would help.

---

### Post by micoams on 2009-01-27
Update: I could not figure out what the problem was but found an alternative solution. Ditched NetworkManager, and installed Wicd. It is nothing fancy, but it works as it is supposed to.

---

