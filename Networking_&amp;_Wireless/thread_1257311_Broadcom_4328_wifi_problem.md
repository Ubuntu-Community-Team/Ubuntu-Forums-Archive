---
title: "Broadcom 4328 wifi problem"
date: 2009-09-03
forum: Networking &amp; Wireless
---

### Post by smoczyna on 2009-09-03
I'm trying to set up wireless connection on my new kubuntu 9.4 for amd64. When reviewing tool System-> Hardware Drivers  I can see that 
Broadcom STA wireless driver is activated but not currently in use. 

When running  following
lspci | grep Broadcom< Corporation 
I have the response
03:00.0 Network controller: Broadcom Corporation BCM4328 802.11a/b/g/n (rev 03)

So it seems the driver is working. But I can't use it anyway, in network tool called: Manage Connections wireless tab is grayed and connection cannot be configured.

I added the following line to /etc/network/interfaces
iface wlan0 inet dhcp
Still nothing

My question is how to feal with that? What determine that the interface is ifup ? Or how turn it on ?

---

### Post by Darkz_Soul on 2009-09-08
I have the same problem with my amd64 bit machine i have looked around but with no avail have i been able to find any solution... I hear this is an anomaly with 9.04 so we might have to wait till 9.10 comes out

---

### Post by t0mppa on 2009-09-08
> **smoczyna said:**
> I'm trying to set up wireless connection on my new kubuntu 9.4 for amd64. When reviewing tool System-> Hardware Drivers  I can see that 
**Broadcom STA wireless driver is activated but not currently in use.**

That pretty much means what it says: your wireless interface is not using this driver. 

> **smoczyna said:**
> When running  following
lspci | grep Broadcom< Corporation 
I have the response
03:00.0 Network controller: Broadcom Corporation BCM4328 802.11a/b/g/n (rev 03)

So it seems the driver is working.

Wrong. All that lspci output tells is that the system detects your card physically. You'll need to run **lshw -C network** to get an idea what state your wireless interace is in and what driver (if any) it's using.

> **smoczyna said:**
> But I can't use it anyway, in network tool called: Manage Connections wireless tab is grayed and connection cannot be configured.

I added the following line to /etc/network/interfaces
iface wlan0 inet dhcp
Still nothing

My question is how to feal with that? What determine that the interface is ifup ? Or how turn it on ?

You shouldn't change the /etc/network/interfaces file, if you use any GUI method to set up your connection, only change it if you want to set everything manually.

[QUOTE=Darkz_Soul]I have the same problem with my amd64 bit machine i have looked around but with no avail have i been able to find any solution... I hear this is an anomaly with 9.04 so we might have to wait till 9.10 comes out[/QUOTE]

Well, I don't know about 64 bit (sometimes has odd bugs), but on 32 bit at least it is fixable.

---

### Post by Darkz_Soul on 2009-09-10
well i appreciate the help but i have switched to vista for the time being but.... I plan to try again is there anyway to tell the computer to use the driver??? I would like some idea on how to edit the file so that it becomes in use

---

### Post by Ayuthia on 2009-09-10
Ubuntu sometimes still has the b43 and/or ssb module (the open source Broadcom module) loaded and it causes conflicts with the Broadcom STA module.  It might be your problem.  You should be able to confirm that with the lshw -C network command and it shows that the b43 module is loaded.  It is usually best to blacklist them:
```
echo blacklist b43 | sudo tee -a /etc/modprobe.d/blacklist.conf
echo blacklist ssb | sudo tee -a /etc/modprobe.d/blacklist.conf
```and you should add the wl (the Broadcom STA module) into /etc/modules so that it will load automatically:
```
echo wl | sudo tee -a /etc/modules
```

---

### Post by smoczyna on 2009-09-21
OK gentlemen, maybe I did not express myself correctly so let's start from the beginning.

We know that my wireless card is visible by the system so I trying this:
**modprobe -l | grep b43**
output is like that:
kernel/drivers/net/wireless/b43/b43.ko
kernel/drivers/net/wireless/b43legacy/b43legacy.ko

so it seems I have 2 modules of broadcom driver. Now I'm doing this:
**modprobe -v b43**
output:
insmod /lib/modules/2.6.28-11-generic/kernel/drivers/leds/led-class.ko
insmod /lib/modules/2.6.28-11-generic/kernel/net/wireless/cfg80211.ko
insmod /lib/modules/2.6.28-11-generic/kernel/net/mac80211/mac80211.ko
insmod /lib/modules/2.6.28-11-generic/kernel/drivers/net/wireless/b43/b43.ko

Now when I try this:
** lsmod  | grep b43 **
I have this:
b43                   145192  0
mac80211              251144  1 b43
led_class              13064  1 b43
input_polldev          12688  1 b43
ssb                    46724  1 b43

Is it supposed to be successfully loaded driver or not?

if I run this:
**ifconfig -a**

I have that:

eth0      Link encap:Ethernet  HWaddr 00:1b:24:60:c0:22
          inet addr:192.168.1.5  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:24ff:fe60:c022/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1018213 errors:0 dropped:0 overruns:0 frame:0
          TX packets:594174 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1445973321 (1.4 GB)  TX bytes:43416680 (43.4 MB)
          Interrupt:20 Base address:0xc000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:64 errors:0 dropped:0 overruns:0 frame:0
          TX packets:64 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:4080 (4.0 KB)  TX bytes:4080 (4.0 KB)

pan0      Link encap:Ethernet  HWaddr 02:26:92:c1:df:73
          inet6 addr: fe80::26:92ff:fec1:df73/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:543 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 B)  TX bytes:167367 (167.3 KB)

pan0:avahi Link encap:Ethernet  HWaddr 02:26:92:c1:df:73
          inet addr:169.254.9.73  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

it look like my wlan card is named pan0 and it is working, is that correct ?

so how can I force my system to use it instead of eth0 ??? After restart of the system b43 driver becomes inactive again and I still can't see it in GUI network configuration tools but that might be because it is not refreshed or something.

Ooh, and making everything complete by typing t0mppa  suggestion:
**lshw -C network**

I have the output like that:
*-network
       description: Network controller
       product: BCM4328 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb
  *-network
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 02:26:92:c1:df:73
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes


Thanks guys for your time, I appreciate that.

---

### Post by Ayuthia on 2009-09-21
The 4328 card does not work with the b43 module.  It is a wireless N card and these cards have not been programmed into the b43 module at this time.  The only options that you have are the Broadcom STA module and NDISwrapper.

pan0 is used for bluetooth so if your 4328 card is not a bluetooth, it will not be used with pan0.  It should either have a wlanX or ethX name where X is a number.

Going to your lshw -C network information, it is showing that your wireless card is trying to use the b43 module.  This is preventing your wireless card from working.  In order to get your wireless card to work, you need to go into System->Administration->Hardware Drivers and disable the b43 option and activate the Broadcom STA option.  You should also do the following to help make sure that the Broadcom STA option is loaded automatically and that the b43 module is not loaded:
```
echo blacklist b43 | sudo tee -a /etc/modprobe.d/blacklist.conf
echo blacklist ssb | sudo tee -a /etc/modprobe.d/blacklist.conf
echo wl | sudo tee -a /etc/modules
```

I hope this helps.

---

### Post by smoczyna on 2009-09-21
OK I did what you've said and have one change. Now Hardware Drivers utility show that Broadcom STA is loaded and currently in use. Previously it was loaded but not in use.
But I still can't use network GUI tools, wireless tab is still inactive. 

Is that mean this driver don't work correctly and i have to use NdisWrapper or there is native solution ?

**lshw -C network** - that stuff haven''t changed much

*-network
       description: Network controller
       product: BCM4328 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb
  *-network
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: ba:ba:3d:80:a2:a6
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

that's strange but it still looks like b43 ??? Can I somehow uninstall it to be sure it is not disturbing ?

---

### Post by Ayuthia on 2009-09-21
> **smoczyna said:**
> OK I did what you've said and have one change. Now Hardware Drivers utility show that Broadcom STA is loaded and currently in use. Previously it was loaded but not in use.
But I still can't use network GUI tools, wireless tab is still inactive. 

Is that mean this driver don't work correctly and i have to use NdisWrapper or there is native solution ?

**lshw -C network** - that stuff haven''t changed much

*-network
       description: Network controller
       product: BCM4328 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb
  *-network
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: ba:ba:3d:80:a2:a6
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

that's strange but it still looks like b43 ??? Can I somehow uninstall it to be sure it is not disturbing ?

To test it out, please try the following:
```
sudo modprobe -r b43 ssb wl
sudo modprobe wl
sudo iwlist scan
```

By any chance, have you restarted your computer?  If not, then most likely the b43 modules are still active.  The commands in this post will remove them and then load the correct module.  Then it will scan for wireless sites.

---

### Post by smoczyna on 2009-09-22
Thanks man, finally I've got this working :guitar:

---

### Post by cohomologie on 2009-09-22
Hey guys, great that I immediately found this topic, because
I have just installed ubuntu 9.04 and I have (almost) exactly the same problem with this wifi card.
Although when I reboot things go back to being screwed...

When I do:
```
lshw -C network
```I get:

WARNING: you should run this program as super-user.
  *-network               
       description: Network controller
       product: BCM4328 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 4e:12:09:4c:d9:85
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes



and after:
```
sudo modprobe -r b43 ssb wl
sudo modprobe wl
sudo iwlist scan
```he even finds my router in the scan 
and 
```
lshw -C network
``` shows that b43 is off:

WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: BCM4328 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth1
       version: 03
       serial: 00:1a:73:7d:7b:4b
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.10.91.9 latency=0 module=wl multicast=yes wireless=IEEE 802.11
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 4e:12:09:4c:d9:85
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes



But after rebooting everything is back to being screwed.

I also blacklisted b43 and ssb with:
```
echo blacklist b43 | sudo tee -a /etc/modprobe.d/blacklist.conf
echo blacklist ssb | sudo tee -a /etc/modprobe.d/blacklist.conf
echo wl | sudo tee -a /etc/modules
```Does anyone know how to solve this?
I am a linux noob by the way,

thanks a lot :)

---

### Post by Ayuthia on 2009-09-23
There is a possibility that the system is loading the b43 module earlier and does not have its blacklist updated.  This might fix it:
```
sudo update-initramfs -a
```

A workaround for this is to add a couple of lines to /etc/rc.local.  To edit the file, go into the Terminal and do the following:
```
gksudo gedit /etc/rc.local
```
and before the exit 0 line, add the following:
```
modprobe -r b43 ssb wl
modprobe wl
```and save the file.  This should also fix the problem so that you don't have to type it every time you restart.

Hope that helps.

---

### Post by cohomologie on 2009-09-23
Thanks so much, I think it work now!

Think I like Ubuntu already so much better than windows, especially with a community like this :D

---

