---
title: "broadcom wireless module restart required"
date: 2009-02-11
forum: Networking &amp; Wireless
---

### Post by plewisfdx on 2009-02-11
I have an Acer Extensa 4420 with a Broadcom 4312 wifi chip.  I'm running 8.04 Ubuntu, and the Broadcom STA wireless driver works for the wifi.

The problem is on every bootup the wifi doesn't work.  The hardware drivers dialogue shows this when I boot up:

Broadcom STA wireless driver  Enabled (checked)  Status 'Not in use'

If I uncheck 'Enabled' then re-check it, the wireless works great.

I want to be able to boot up and have the wireless work without having to toggle the 'enabled' manually every time.

I removed ndiswrapper to see if there was a conflict, but the result is the same.

The output of 

```
sudo lshw -C Network
```

 is:


 ```
*-network
       description: Wireless interface
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth1
       version: 01
       serial: 00:1f:e2:a5:79:8e
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl1 driverversion=5.10.27.12 ip=192.168.1.15 latency=0 module=wl multicast=yes wireless=IEEE 802.11bg

```

dmesg doesn't show any lines with Broadcom in them until I toggle the driver to get the wifi to work.

If I need to write a script to toggle the driver on boot, I'll do that, but I don't know the command to do that.

Any help is appreciated.

---

### Post by Ayuthia on 2009-02-11
If you have tried already, you can add the wl module to /etc/modules:
```
echo wl | sudo tee -a /etc/modules
```

That should load the wl module when the system boots.

---

### Post by plewisfdx on 2009-02-11
thanks for the help.  It worked.

---

