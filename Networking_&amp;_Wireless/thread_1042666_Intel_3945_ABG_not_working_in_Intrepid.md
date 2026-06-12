---
title: "Intel 3945 ABG not working in Intrepid"
date: 2009-01-17
forum: Networking &amp; Wireless
---

### Post by hobojoe789 on 2009-01-17
I started out with 8.04 and wireless was working fine until I compiled a newer kernel and wireless stopped working.  After that I went back to the original kernel that was installed from the ubuntu CD and wireless worked again.  After not updating my laptop for about 4-5 months I ran the ubuntu updates which made wireless stop working again.  So after all that I decided I might as well just upgrade to 8.10 because I assumed that would fix the issue.  

Well I did a clean install of 8.10 and ran the updates and my wireless is still not working my only guess is that it is an issue with the kernel and the drivers but I have no idea because I am a linux noob.  The system is dual booted with windows XP and the wireless is working in XP.  Any help will be appreciated,  It is a Intel 3945 ABG on a Toshiba Portege M400 if that helps with anything

---

### Post by hobojoe789 on 2009-01-18
Any suggestions?

---

### Post by hobojoe789 on 2009-01-19
OK I installed ndiswrapper and now my laptop detects my wireless network but I can not connect to it.  Here is the output of ndiswrapper -l

```

WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 82573L Gigabit Ethernet Controller
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 00
       serial: 00:0e:7b:dc:d8:da
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e1000e driverversion=0.3.3.3-k6 firmware=0.5-1 ip=192.168.233.105 latency=0 module=e1000e multicast=yes
  *-network
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 02
       serial: 00:13:02:17:1f:5e
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+netw39x5 driverversion=1.53+Intel,07/26/2006,10.5.1.59 latency=0 module=ndiswrapper multicast=yes wireless=IEEE 802.11g
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: be:6c:36:b9:01:f4
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes


```

---

### Post by blackened on 2009-01-19
Which driver were you originally using? I have the same adapter and am successfully using the iwl3945 module with wpa2.

Try removing the driver you installed with ndiswrapper, then

```
sudo modprobe iwl3945 disable_hw_scan=1
```

---

### Post by dmflad on 2009-01-20
Same problem as orig poster. Have Intel PRO/Wireless 3945ABG rev2. Fine under 8.04LTS, no ndiswrapper needed. Been fine since 8.04LTS first out. Last update appears to have killed wireless and LT w/o wireless is useless for job it was bought for. Makes me wonder about LTS too.

Reinstalled 8.04, no wireless joy.
Upgraded to 8.10 assuming problem would be corrected, no wireless joy. 
No reason I can think of to support 3945 out of box in earlier 8.04LTS and then to kill it off and (maybe) require use of NDISWrapper.

At least my OLPC XO has working wireless so I can write this.

---

### Post by ussndmac on 2009-01-20
Yep, similar issues here on a Dell XPS 1530 with the 3945.

It worked fine with the original Ubuntu 8.04. OS that was installed from Dell.

After doing all of the following:

1. install -rt kernel
2. wipe drive install 8.10
3. wipe drive install Ubuntu Studio 8.10 amd64
4. wipe drive install Ubuntu Studio 8.0.4 amd64

The wireless shows on the ubuntu box, the ubuntu shows up as connecting in the wap logs, but the ubuntu box can't see anything on the network connected to the wap.

After step #1 above I tried all the iwl, iwp, ndis, back porting, yada... same results.

My wap is an older linsys 802.11b, wep active, and I use static IP's.

Unfortunately, I have to report that my other PC running WinXP connects just fine.

:(

---

