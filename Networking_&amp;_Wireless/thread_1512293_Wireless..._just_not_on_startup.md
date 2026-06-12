---
title: "Wireless... just not on startup"
date: 2010-06-17
forum: Networking &amp; Wireless
---

### Post by ToyotaGuy23 on 2010-06-17
System: Dell 1721 notebook.  9.04 installed.  Broadcomm bcm4328.  On startup, there is no wireless.

'lshw -C network' shows network: DISABLED.  

Go to System > Admin > Hardware Drivers and the Broadcomm Driver is installed but not in use.  'Deactivate' and then 'Activate' and wireless is working.  

I need this to happen on startup.  

Please help. 
Thanks!

---

### Post by leorolla on 2010-06-18
Could you run
```
sudo lshw -C network
```
after it is enabled and paste the results here?

---

### Post by ToyotaGuy23 on 2010-06-18
On startup:  


matt@matt-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Network controller
       product: BCM4328 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:1d:09:af:31:a4
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=b44 driverversion=2.0 latency=64 module=ssb multicast=yes
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: da:3e:a0:ae:84:4a
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
matt@matt-laptop:~$ 


-------------------------------------------------------------

After DeActivating and Reactivating the Driver:



matt@matt-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: BCM4328 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       logical name: eth1
       version: 03
       serial: 00:1e:4c:77:f8:a0
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl1 driverversion=5.10.27.12 ip=192.168.1.105 latency=0 module=wl multicast=yes wireless=IEEE 802.11
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:1d:09:af:31:a4
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=b44 driverversion=2.0 latency=64 module=ssb multicast=yes
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: da:3e:a0:ae:84:4a
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
matt@matt-laptop:~$

---

### Post by purelinuxuser on 2010-06-18
I've had a similar problem before.  Press Alt+F2, type
```
gksudo gedit /etc/rc.local
```
And add in the following lines before the last one that says "exit 0":
```
modprobe -r b43 ssb wl
modprobe wl
```
On reboot wireless should work. :)

---

### Post by leorolla on 2010-06-19
Alternatively, open a terminal and run
```
echo blacklist ssb | sudo tee -a /etc/modprobe.d/blacklist-ssb.conf
echo blacklist b43 | sudo tee -a /etc/modprobe.d/blacklist-b43.conf
echo wl | sudo tee -a /etc/modules
```
This will prevent modules ssb and b43 from being loaded, and will load module wl.

---

### Post by ToyotaGuy23 on 2010-06-19
Thanks for the replies.  

Unfortunately, neither solution worked for me.
What should I try next?

Thanks!

---

### Post by purelinuxuser on 2010-06-20
> **ToyotaGuy23 said:**
> Thanks for the replies.  

Unfortunately, neither solution worked for me.
What should I try next?

Thanks!

Looks like we'll need to dig in deeper.  Post the output of the following commands:
```
sudo rmmod b43
sudo modprobe wl
```

Let me know if that second command makes the wireless work.

---

### Post by purelinuxuser on 2010-06-20
> **ToyotaGuy23 said:**
> Thanks for the replies.  

Unfortunately, neither solution worked for me.
What should I try next?

Thanks!

Looks like we'll need to dig in deeper.  Post the output of the following commands:
```
sudo modprobe -r b43
sudo modprobe wl
```

Let me know if that second command makes the wireless work.

---

### Post by leorolla on 2010-06-20
It's strange from post #3 that the associated driver was wl1 and not wl. Is it normal?

---

### Post by ToyotaGuy23 on 2010-06-20
Here's what I got. 


matt@matt-laptop:~$ sudo rmmod b43
[sudo] password for matt: 
ERROR: Module b43 does not exist in /proc/modules
matt@matt-laptop:~$ sudo modprobe wl
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
matt@matt-laptop:~$ sudo modprobe -r b43
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
matt@matt-laptop:~$ sudo modprobe wl
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
matt@matt-laptop:~$

---

### Post by ToyotaGuy23 on 2010-06-20
Same results so far.

---

### Post by leorolla on 2010-06-20
After this, do you have internet?
Could you post the result of sudo lshw -C network after running these commands?
Also, could you after this open the same window where you Deactivate/activate the driver, and run sudo lshw -C network one again?

---

### Post by purelinuxuser on 2010-06-20
> **leorolla said:**
> It's strange from post #3 that the associated driver was wl1 and not wl. Is it normal?

Yes, that is normal.  Modules and drives sometimes have different names.

What I don't understand is why wl won't claim the wireless card even when it is loaded manually. :confused:

---

### Post by leorolla on 2010-06-21
Oh, could you run a different test?
```

lsmod
sudo rmmod b43 ssb wl
sleep 5
lsmod
sudo modprobe wl
lsmod

```

I guess purelinuxuser forgot some modules to remove during copy/paste.

Anyway, it is surprising but there are some things I never understood with wireless drivers... at some point I was using ndiswrapper but it would work if and only if wl was not blacklisted... crazy.

---

### Post by bkratz on 2010-06-21
> **leorolla said:**
> Oh, could you run a different test?
```

lsmod
sudo rmmod b43 ssb wl
sleep 5
lsmod
sudo modprobe wl
lsmod

```

I guess purelinuxuser forgot some modules to remove during copy/paste.

Anyway, it is surprising but there are some things I never understood with wireless drivers... at some point I was using ndiswrapper but it would work if and only if wl was not blacklisted... crazy.


Sorry to jump in at such a late date, but I believe that since the poster has the following

```
description: Ethernet interface
product: BCM4401-B0 100Base-TX
vendor: Broadcom Corporation
```

which uses b44  that removal of the ssb module which may prevent the wired connection from working ( just something to remember and watch in the future).

---

### Post by bkratz on 2010-06-21
Did find this posting which explains what is probably going on, that since you have the b44 driver ssb is probably capturing the card before wl.. is. See the posting for better info, I remember seeing the correct order somewhere and if this helps, will find it.

[http://ubuntuforums.org/showpost.php?p=9164616&postcount=6](http://ubuntuforums.org/showpost.php?p=9164616&postcount=6)

---

### Post by purelinuxuser on 2010-06-21
> **bkratz said:**
> Sorry to jump in at such a late date, but I believe that since the poster has the following

```
description: Ethernet interface
product: BCM4401-B0 100Base-TX
vendor: Broadcom Corporation
```which uses b44  that removal of the ssb module which may prevent the wired connection from working ( just something to remember and watch in the future).

Yeah, I had to same setup on my old laptop.  I just didn't think he did. ;)

---

### Post by leorolla on 2010-06-22
Makes sense.

Toyota,
Could you run the following and post the output here?
```
lsmod && sudo rmmod b43 ssb wl && sleep 5 && lsmod && sudo modprobe wl && sleep 5 && lsmod && sudo modprobe ssb && sleep 5 && lsmod && sudo lshw -C network
```
You can select it here with the mouse and click with the middle button in the terminal.

Please, after you copy-paste the output here, select it with the mouse and click on the "#" above your text (it is one of the formatting buttons). It will make it easier for us to read it:

```
good format
```bad format

---

### Post by leorolla on 2010-06-22
I found this patch:
[https://patchwork.kernel.org/patch/70481/](https://patchwork.kernel.org/patch/70481/)

It is already on Maverick's kernels but not on Lucid's.

Maybe you can try Maverick Live Session just to see if it works with b43 natively. You will need wired connection to fetch the firmware, though.

---

