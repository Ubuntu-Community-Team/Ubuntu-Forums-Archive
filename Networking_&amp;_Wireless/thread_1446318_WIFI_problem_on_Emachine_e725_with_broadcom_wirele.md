---
title: "WIFI problem on Emachine e725 with broadcom wireless card running under ubuntu 9.10"
date: 2010-04-03
forum: Networking &amp; Wireless
---

### Post by lemahdois on 2010-04-03
Hi all, 
I'm searching for solution from 2 days, i tried many things foud in forums 
the last thing was as described here [http://playingwithsid.blogspot.com/2009/09/configure-broadcom-wireless-drivers.html](http://playingwithsid.blogspot.com/2009/09/configure-broadcom-wireless-drivers.html) 
but i still haven't mt wireless card working.
Any one can help please?

---

### Post by coffeeaddict22 on 2010-04-04
Hi,
Can you open a terminal, type in ```
lshw -C network
nm-tool
sudo iwlist scan
```
and post back the output?

---

### Post by lemahdois on 2010-04-04
sudo lshw -C network

```

 *-network UNCLAIMED     
       description: Network controller
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:94600000-94603fff
  *-network
       description: Ethernet interface
       product: Atheros AR8132 / L1c Gigabit Ethernet Adapter
       vendor: Attansic Technology Corp.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: c0
       serial: 70:5a:b6:44:96:ad
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.0.2-NAPI duplex=full firmware=N/A ip=192.168.1.3 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:29 memory:93500000-9353ffff ioport:1000(size=128)



```nm-tool

```

NetworkManager Tool

State: connected

- Device: eth0  [Auto eth0] ----------------------------------------------------
  Type:              Wired
  Driver:            atl1c
  State:             connected
  Default:           yes
  HW Address:        70:5A:B6:44:96:AD

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.3
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1



``````

issam@issam-laptop:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.



```

---

### Post by coffeeaddict22 on 2010-04-04
You haven't got a driver installed.  
There's some discussion on the best one; google ndiswrapper for the alternative.  I prefer going into System/Administration/Hardware Drivers (while connected to the internet) and activating the Broadcom STA driver.  That should fix your problem.

---

### Post by alexdelprogramador on 2010-04-04
> 
 product: BCM4312 802.11b/g
 vendor: Broadcom Corporation



ok

I guess that you have a broadcom wireless card with BCM4312  chipset

Its not assigned an iterface "like wlan0 or wlan1" because you havent a firmware installed on your ubuntu distribution.

Why dont try to find from synaptic this words:?

```

bcm43xx


```

it will be appear a fwcutter package.

It could be the firmware you needed

wating your responses ;)

---

### Post by lemahdois on 2010-04-05
i've activated driver from synaptic but i still have the same problem.

---

### Post by alexdelprogramador on 2010-04-05
> **lemahdois said:**
> i've activated driver from synaptic but i still have the same problem.

Ok

[SIZE=5]I had the solution!![/SIZE] :p

its easy

Readding the readme.txt broadcom instalation:

[http://www.broadcom.com/docs/linux_sta/README.txt](http://www.broadcom.com/docs/linux_sta/README.txt)

The best and quickest way is to do what are in the last of the manual:

> 
Ubuntu:
------
Go to System->Administration->Hardware Drivers
Choose the Broadcom STA wireless driver
Activate

**Sometimes the driver does not show up in the Hardware Drivers choices**.  In
this case, try reintalling the driver from the GUI or shell like this:

From the GUI:
Package Manager (System>Administration>Synaptic Package Manager). Click the 
Reload button in the upper left corner of Synaptic to refresh your index then 
search for and reinstall the package named bcmwl-kernel-source.

---

### Post by lemahdois on 2010-04-05
i did all what u said, and i have the driver installed but still can't have WIFI, now i will resume the situation : this is what i have
From synaptic i got bcmwl-kernel-source installed
[[IMG]http://img693.imageshack.us/img693/417/captureqi.png[/IMG]](http://img693.imageshack.us/i/captureqi.png/)

and in the drivers list, i got the driver activated but never used

[[IMG]http://img249.imageshack.us/img249/6148/capture1p.png[/IMG]](http://img249.imageshack.us/i/capture1p.png/)

and i still havent wifi connection

---

### Post by alexdelprogramador on 2010-04-05
ok, the posibility is that the module isnt properly loaded.

the last solution is to install it manualy.


in readme.txt from broadcom web page are the steps to do it.

so look this file, and try to do it:

[http://www.broadcom.com/docs/linux_sta/README.txt](http://www.broadcom.com/docs/linux_sta/README.txt)

---

### Post by alexdelprogramador on 2010-04-05
I have an spanish manual to do it manualy

[http://www.alcancelibre.org/article.php/como-driver-bcm43xx-linux](http://www.alcancelibre.org/article.php/como-driver-bcm43xx-linux)

its the same ussing readme.txt from broadcom.

bye

---

### Post by terrorx on 2010-04-06
hi,
i had the exact same problem on the exact same laptop, what i diid was perform an update to my ubuntu and the install the broadcom drivers from the hardware manager, now what problem i have is the wifi card is detected and also my access point is detected, but i cant access the internet, what ubuntu does is constantly keep asking my WPA2 password and i keep typing it in but no net access... pls anyone have any idea what can be wrong???

thx
terrorx

---

### Post by MarcG on 2011-07-01
> **terrorx said:**
> hi,
i had the exact same problem on the exact same laptop, what i diid was perform an update to my ubuntu and the install the broadcom drivers from the hardware manager, now what problem i have is the wifi card is detected and also my access point is detected, but i cant access the internet, what ubuntu does is constantly keep asking my WPA2 password and i keep typing it in but no net access... pls anyone have any idea what can be wrong???


I'm having the same problem with 10.04. I did a fresh install due to a problem after an update/upgrade. The wireless connected for maybe 20 seconds, then disconnected. Now it just tries to connect, only to fail asking for my password.

---

### Post by MarcG on 2011-07-01
> **terrorx said:**
> hi,
i had the exact same problem on the exact same laptop, what i diid was perform an update to my ubuntu and the install the broadcom drivers from the hardware manager, now what problem i have is the wifi card is detected and also my access point is detected, but i cant access the internet, what ubuntu does is constantly keep asking my WPA2 password and i keep typing it in but no net access... pls anyone have any idea what can be wrong???


I'm having the same problem with 10.04. I did a fresh install due to a problem after an update/upgrade. The wireless connected for maybe 20 seconds, then disconnected. Now it just tries to connect, only to fail asking for my password.

---

