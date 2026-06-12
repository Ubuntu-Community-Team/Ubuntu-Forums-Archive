---
title: "Wireless driver name"
date: 2012-01-05
forum: Networking &amp; Wireless
---

### Post by roseparade on 2012-01-05
I recently found these steps that I believe may help my wireless situation. The wireless works before the computer sleeps, but after the computer wakes the adapter is disabled and the only way that I know to fix it is to unplug and then reinsert the adapter.

**gksudo gedit /etc/pm/config.d/config**

put:

[B]SUSPEND_MODULES="your-drivers"

[/B]However, I cannot figure out how to find my wireless driver name. I am using ndiswrapper for a d-link dwl ag132 usb adapter. 
Also, if anyone has any different steps involving getting this adapter to work besides the ones I listed above, I'd appreciate it.

---

### Post by Goatrancer on 2012-02-27
Same situation here. The threads I have found have not helped.
I wanted to try the follwing:
[http://askubuntu.com/questions/96333/what-wireless-driver-am-i-using](http://askubuntu.com/questions/96333/what-wireless-driver-am-i-using)

but I have not been able to install aircrack-ng, due to the following error:

E: Package 'aircrack-ng' has no installation candidate


Any help would be appreciated.

PS, I can't use network manager to get this info because I use WICD, and Network Manager refused to work at all last time I tried it.

---

### Post by Goatrancer on 2012-02-28
OK well I tried this:

```
 dmesg | grep 'driver'
[72357.394928] usbcore: registered new interface driver cdc_acm
[72357.395357] cdc_acm: v0.26:USB Abstract Control Model driver for USB modems and ISDN adapters
```

Is cdc_acm the driver I want to use in the above fix as:

```
SUSPEND_MODULES="cdc_atm"
```?

I'm a bit unclear as to whether the "virtual modem" driver stands in for wifi and all other communication related drivers, or if it's its own thing, and I still need to find a specific wifi driver.

---

### Post by chili555 on 2012-02-28
> Is cdc_acm the driver I want to use in the above fixI doubt it. Is your device USB? Let's see, from a terminal:```
lsusb
sudo lshw -C network
```Thanks.

---

### Post by Goatrancer on 2012-02-28
Output of lsusb:

```
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 064e:a102 Suyin Corp. Acer/Lenovo Webcam [CN0316]
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

Doesn't look like it.

output of lshw -C network

```

  *-network               
       description: Ethernet interface
       product: AR8131 Gigabit Ethernet
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: c0
       serial: 00:26:9e:a8:9e:19
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.0.2-NAPI firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: irq:29 memory:93500000-9353ffff ioport:2000(size=128)
  *-network
       description: Wireless interface
       product: Centrino Wireless-N 1000
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 00
       serial: 00:1e:64:2a:ef:4c
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn ip=10.125.180.99 latency=0 multicast=yes wireless=IEEE 802.11bgn
       resources: irq:28 memory:92500000-92501fff
```

So I guess what I want is:
SUSPEND_MODULES="iwlagn"

---

### Post by chili555 on 2012-02-28
> So I guess what I want is:
SUSPEND_MODULES="iwlagn"Quite correct.

---

### Post by Goatrancer on 2012-02-29
Oh well, I tried it and it didn't end up solving my problem :(

---

### Post by kevdog on 2012-02-29
I had this problem way way back in edgy.  I really never found the solution however I just remember creating a script that would automatically take down the interface and bring it back up via script.  I'm uncertain if you could make this happen in your case, but you could at least see if you brought the interface down manually and then up manually (without Network Manager) if this at least avoids the need to unplug the adapter.  If you can confirm the script works, the next step would be to automate it -- somehow into the power management routine.

---

### Post by Goatrancer on 2012-02-29
Yeah I guess I'll just do that. My situation actually isn't exactly the same as the OP's.. I dont have to unplug anything, just have to go to my WICD panel and re-connect manually. Kindof a pain, but would be solved by a script.
Thanks for the suggestion.

---

