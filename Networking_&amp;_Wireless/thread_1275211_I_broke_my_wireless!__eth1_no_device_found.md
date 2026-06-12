---
title: "I broke my wireless!  eth1 no device found"
date: 2009-09-25
forum: Networking &amp; Wireless
---

### Post by Sureshot324 on 2009-09-25
I have a broadcom bcm4312 wireless card in my laptop.  I'm running Ubuntu 9.10 and originally it had the Broadcom STA driver which worked fine.  I wanted to get the b43 driver working so I could enable monitor mode and use kismet.  I tried 'rmmod wl' and then 'modprobe b43', and the module loaded fine, but if I ran ifconfig, the only device showing was eth0 (my ethernet card).  If I then did 'rmmod b43' and 'modprobe wl', the device eth1 would come back and my wireless would start working again.

I read that this may be because I need the latest b43 driver to support my wireless card.  I went to [http://linuxwireless.org/en/users/Drivers/b43](http://linuxwireless.org/en/users/Drivers/b43) to get the latest b43 driver.  I tried the latest daily build but got errors when running the make command.  I then tried the latest stable build, and ran 'make', 'make install', 'make unload', and 'make load'.

Now I can't get the wireless device to show up at all, with either driver.  I still have both the b32 and wl modules and can successfully load/unload them, but no matter what, ifconfig only shows eth0.  There is no eth1 or wlan0.  

I'd be happy just to get the wl driver working again.  Can anyone help?

---

### Post by Ayuthia on 2009-09-25
> **Sureshot324 said:**
> I have a broadcom bcm4312 wireless card in my laptop.  I'm running Ubuntu 9.10 and originally it had the Broadcom STA driver which worked fine.  I wanted to get the b43 driver working so I could enable monitor mode and use kismet.  I tried 'rmmod wl' and then 'modprobe b43', and the module loaded fine, but if I ran ifconfig, the only device showing was eth0 (my ethernet card).  If I then did 'rmmod b43' and 'modprobe wl', the device eth1 would come back and my wireless would start working again.

I read that this may be because I need the latest b43 driver to support my wireless card.  I went to [http://linuxwireless.org/en/users/Drivers/b43](http://linuxwireless.org/en/users/Drivers/b43) to get the latest b43 driver.  I tried the latest daily build but got errors when running the make command.  I then tried the latest stable build, and ran 'make', 'make install', 'make unload', and 'make load'.

Now I can't get the wireless device to show up at all, with either driver.  I still have both the b32 and wl modules and can successfully load/unload them, but no matter what, ifconfig only shows eth0.  There is no eth1 or wlan0.  

I'd be happy just to get the wl driver working again.  Can anyone help?

Are you saying that the following does not work:
```
sudo modprobe -r b43 ssb wl
sudo modprobe wl
sudo iwlist scan
```The last command just scans for wireless sites.

---

### Post by Sureshot324 on 2009-09-25
Thank you that worked.  I think the problem was I didn't remove ssb before.

---

### Post by cespinal on 2009-11-18
I just happened to broke mine dammit!!!!! here is my ifcong output

```
eth0      Link encap:Ethernet  HWaddr 00:1e:68:2c:50:e6  
          inet addr:192.168.1.33  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:68ff:fe2c:50e6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:94 errors:0 dropped:0 overruns:0 frame:0
          TX packets:133 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:17694 (17.6 KB)  TX bytes:14946 (14.9 KB)
          Interrupt:27 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

I tried whats said on this post and this is the reponse I get: 
```
FATAL: Error inserting wl (/lib/modules/2.6.31-15-generic/updates/dkms/wl.ko): Unknown symbol in module, or unknown parameter (see dmesg)
```

sigh....this was one of those times when you are desperate to solve a problem (wifi wont retrieve my home router's IP) and you end up trying stuff on the termina and obviously.. something goes horribly wrong.

Im using an HP DV9000 with the broadcom driver. At this moment, the wifi led is orange...

---

### Post by Sureshot324 on 2009-11-19
Not sure, but you're probably better off making a new thread, since it seems to be a different problem and this thread is already marked solved.

---

### Post by cespinal on 2009-11-20
I solved it.. 

the problem came up when i installed backports. When I figuered it out just removed them and the wifi card came alive again. 

As for the connection itself, tried EVERYTHING and the only thing it worked was to reconfigure the router from WEP to WPA encryption. 

Thanks for the reply!

---

### Post by namethatmeetsstandards on 2009-11-29
thanks for sharing that. I also had lost my wireless since a regular ubuntu update. When I browsed to this thread:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/343556](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/343556), their suggested "modprobe wl" gave the error as described in this current thread and then I realized that it could be the backports. It was. Uninstalling the backports and rebooting has brought back the wireless.
macbook pro 4,1 (broadcom wireless card)

---

