---
title: "Enable Network"
date: 2009-04-27
forum: Networking &amp; Wireless
---

### Post by DracoJesi on 2009-04-27
ok, I uprgraded to 9.04, 

no wireless, so I download compat-wireless and install it.... 

it seems to work except a few errors, and I get a new wireless driver...

Alternate Atheros "madwifi" driver, I don't really remember but I didn't think my old driver was Atheros... (when I activate the driver, is gets  disabled just as quick...


anyway, still no wireless, but look at lshw...

```
*-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 0a:d3:24:b3:99:10
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes


```

Disabled, oh no!, but that seems to refer to my ethernet...

but maybe this is why I can't see the pc in the other room...

what really worries me is that I didn't see anything from lshw that mentioned my built in wifi....... hopefully I missed it...

from ifconfig

```
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:135 errors:0 dropped:0 overruns:0 frame:0
          TX packets:135 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:16167 (16.1 KB)  TX bytes:16167 (16.1 KB)

```

Edit: found it in lshw

```
*-network UNCLAIMED
                description: Ethernet controller
                product: AR242x 802.11abg Wireless PCI Express Adapter
                vendor: Atheros Communications Inc.
                physical id: 0
                bus info: pci@0000:06:00.0
                version: 01
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix bus_master cap_list
                configuration: latency=0

```

driver issue?

---

### Post by chili555 on 2009-04-27
> it seems to work except a few errors, and I get a new wireless driver...If you got errors in 'make' or 'sudo make install' then you have not built a driver. > *-network UNCLAIMED
                description: Ethernet controller
                product: AR242x 802.11abg Wireless PCI Express Adapter
UNCLAIMED means no driver has attached. Does it still show as UNCLAIMED if you manually insert the driver?```
sudo modprobe ath5k
```Incidentally, I tried to build the compat-wireless package myself, from several version numbers and never got it built correctly.

---

### Post by DracoJesi on 2009-04-27
hmm you to huh? I'll try that command and see what happens 

thanks...

Edit: it worked like a charm, thanks a bunch :)

---

### Post by DracoJesi on 2009-04-28
ok, the celebration was a little premature...

It fixed the problem, but I have to manually set it up every time I reboot, now, this is a major inconvenience, not so much that I have to do it, but I might forget the command....[http://www.microsoft.com/windows/windows-xp/future.aspxrs](http://www.microsoft.com/windows/windows-xp/future.aspxrs)

so I used a new feature in compiz I happened to see, configure key bindings to commands, handy...

so not much of a big deal, if theres no workaround here...

but trying anyways, how can i set it to load when Ubuntu starts?

---

### Post by chili555 on 2009-04-28
The usual way to load a module automatically at boot is:```
sudo gedit /etc/modules
```Add a new line, all by itself:```
ath5k
```Proofread, save and close. Let us know if it works.

---

