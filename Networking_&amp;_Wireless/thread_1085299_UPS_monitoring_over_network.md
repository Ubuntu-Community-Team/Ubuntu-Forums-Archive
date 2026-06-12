---
title: "UPS monitoring over network"
date: 2009-03-02
forum: Networking &amp; Wireless
---

### Post by Keith_Beef on 2009-03-02
I'm struggling with monitoring the UPS supply to a ReadyNAS box...

After reading everything I can find about nuts, apcupsd and gkrellm I'm just becoming more confused.

The ReadyNAS has a page in Frontview (its web-based configuration tool) that should share UPS data over the network:

I connected the signal cable from the UPS to the USB connector on the back of the ReadyNAS NV+ and then looked in Frontview.

In Status - Health, I see:
```
UPS 1	APC Back-UPS XS 1300 LCD, Battery charge: 100%, 31 minutes
```
and in System - Power I can set:
```
Select shutdown on battery low threshold: Auto
Enable network monitoring of attached UPS
Hosts allowed access:   	 192.168.0.2/32
```

Now I just need a daemon on my main computer, listening for a signal sent from the ReadyNAS in the even of a power failure.

I tried making a configuration file for nut:
```
#/etc/nut/upsmon.conf
# define the ups to monitor and the permissions
MONITOR myups@192.168.0.4 1	upsmaster   zaphod  slave

# define the shutdown comand
SHUTDOWNCMD "/sbin/shutdown -h +10"
```

but this seems to do nothing... and I don't see any activity in /var/log/daemon.log either.

Anybody able to enlighten me?

K.

---

### Post by tgalati4 on 2009-03-03
Configure and run apcusd on your pc.  Connect ups cable to pc and make it the master.  Set NAS  to listen to pc for shutdown.

Test it by yanking the plug.

---

### Post by Keith_Beef on 2009-03-03
> **tgalati4 said:**
> Configure and run apcusd on your pc.  Connect ups cable to pc and make it the master.  Set NAS  to listen to pc for shutdown.

Test it by yanking the plug.

I can see how that would work for some set-ups, but not for me...

The NAS is in the basement with the UPS, wireless router, modem, telephone.
These are the "always on" elements.

I want it to serve up files to portable computers round the house, as well as to the big computer that is in the basement. The big computer is not always on, so cannot control the NAS.

The NAS is around 35W - 55W whereas the big computer takes at least three times that power (according to the UPS panel).

Additionally, the NAS configuration doesn't include anything for a listener daemon, only a connection for the UPD that supposedly can send out a signal to listeners on the network...

K.

---

