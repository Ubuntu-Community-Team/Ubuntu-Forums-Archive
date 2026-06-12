---
title: "Won't reconnect wireless after standby"
date: 2008-12-20
forum: Networking &amp; Wireless
---

### Post by weaver4 on 2008-12-20
I am using Ubuntu 8.10 with an Atheros WiFi chipset.  I am running Ubuntu on a Toshiba M305 laptop.

When I boot the computer wireless works.  Once the computer goes into standby and then recovers from standby the wireless link will not get restored.  I have tried "sudo ifconfig wlan0 down" and then "up" but that does not work either.  I tried disabling networking from the networking applet and reenabling it but that did not work either.  After it tries to connect it comes back with a dialog box asking me the security info, entering it makes no differance.  It does thy to connect for almost a minute before it quits.

What should I check?  How do you fix this problem?

---

### Post by weaver4 on 2008-12-21
The chipset is Atheros AR928X

---

### Post by weaver4 on 2008-12-23
I did not fix this problem but I did write a bash script that would restart it.  Now if I could find some way to run this script when I come out of standby I would be set.  Any suggestions?  Right now I made a launcher an the top-panel to run it.

Here is the script.  I found it on this forum somewhere.

#!/bin/bash
/sbin/rmmod ath9k
sleep 2
/sbin/modprobe ath9k

---

### Post by Aearenda on 2008-12-23
There is a mechanism already in place to do this - all you need to do is add the driver to the list of modules to be removed before standby, and reloaded on wake. Press ALT and F2 and type this:```
gksudo gedit /etc/pm/config.d/00sleep_module
```and (assuming there is no existing SUSPEND_MODULES line) add this at the end of the file:```
SUSPEND_MODULES="ath9k"
```Then save it and see if it works!

---

### Post by weaver4 on 2008-12-26
Learn something everyday.

Tried it and it worked!  Thanks!

---

### Post by Aearenda on 2008-12-27
Glad it works. One of the hard bits about switching to Linux is that it changes quickly, and the documentation can never keep up, if it exists! That's why forums like this are so important.

---

### Post by weaver4 on 2009-01-12
Well I spoke to soon.  The first time I go into standby the wireless reconnects right away.  But...the second time I go into standby the wireless tries to restart but can't connect.  Restart the computer and the process starts over again.

Any ideas????

---

### Post by Aearenda on 2009-01-13
Does your manual way of unloading and reloading the driver still work after multiple wakes?

---

### Post by weaver4 on 2009-01-14
No it doesn't

---

### Post by Aearenda on 2009-01-14
What happens if you restart Network-manager?
```
sudo /etc/init.d/NetworkManager restart
```

---

### Post by weaver4 on 2009-01-15
I tried this and it did not work.  It seemed to always get stuck trying to get an IP address from my LinkSys Wireless router.  When I restart Ubuntu I do not have a problem getting an IP address from the Router and of course I do not have this problem in Windows.

---

### Post by Aearenda on 2009-01-15
Are you using the ath9k from linux-backports-modules-generic? If not, it might be worth trying that. Otherwise I suggest you file a bug against ath9k on Launchpad - there are several similar issues [there already]("https://bugs.launchpad.net/bugs/+bugs?field.searchtext=ath9k&search=Search+Bug+Reports&field.scope=all&field.scope.target=").

---

### Post by weaver4 on 2009-01-18
I am using ath9k, but how can I tell where it came from?

---

### Post by Aearenda on 2009-01-18
It didn't come from backports unless you deliberately installed it - but one way to find out is to look at the status of the linux-backports-modules-generic package in Synaptic.

---

### Post by psrivats on 2010-03-18
> **Aearenda said:**
> There is a mechanism already in place to do this - all you need to do is add the driver to the list of modules to be removed before standby, and reloaded on wake. Press ALT and F2 and type this:```
gksudo gedit /etc/pm/config.d/00sleep_module
```and (assuming there is no existing SUSPEND_MODULES line) add this at the end of the file:```
SUSPEND_MODULES="ath9k"
```Then save it and see if it works!

Worked for me - using ath5k on a Thinkpad T60. It survives reboots and multiple suspend/hibernates.

Thank you.

---

### Post by ouff on 2010-06-19
My computer has the same problem of not reconnecting on resume from sleep, but I'm not using ath9k.  How do I find the name of my wireless driver?

---

### Post by Aearenda on 2010-06-19
You can run this command in a terminal:```
lshw -c network
```
The look at the output, it will list the driver in the configuration section. Here's mine for comparison:```
 *-network:0             
       description: Wireless interface
       product: Atheros AR5001X+ Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 5
       bus info: pci@0000:02:05.0
       logical name: wifi0
       version: 01
       serial: 00:0b:cd:59:d6:1c
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci ip=192.168.13.171 latency=168 maxlatency=28 mingnt=10 multicast=yes wireless=IEEE 802.11g
       resources: irq:15 memory:e0000000-e000ffff

```

---

