---
title: "Centrino Advanced-N 6200 VS Kismet"
date: 2011-01-19
forum: Networking &amp; Wireless
---

### Post by striker on 2011-01-19
Hi all,

A got a new laptop with Centrino Advanced-N 6200 Wireless card and i want to use Kismet.

From my search i didn't found anyone using this with Kismet neither in their documentation.

Does anyone know which driver shall i use?

Regards

---

### Post by chili555 on 2011-01-19
Did you try *iwl4965* in the kismet.conf file?

From the README:> iwl4965         Intel/Centrino      Linux       iwl4965
                    Intel's new IPW drivers using the mac80211 kernel
                    layer.I don't have the device, so I can't say for sure that it works.

---

### Post by mappuso on 2013-02-03
Hello everyone,
I've got a similar problem of striker. Kismet doesn't run. These are the details of my wireless card;

[FONT="Courier New"] sudo lshw -c network
  *-network               
       description: Wireless interface
       product: Centrino Advanced-N 6230
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan1
       version: 34
       serial: 88:09:12:4f:6e:a4
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=3.2.0-36-generic firmware=18.168.6.1 latency=0 link=no multicast=yes wireless=IEEE 802.11abgn
       resources: irq:54 memory:f1b00000-f1b01fff[/FONT]

And these are the message when I try to lounch kismet.

[FONT="Courier New"]Launching kismet_server: //usr/bin/kismet_server
Suid priv-dropping disabled.  This may not be secure.
No specific sources given to be enabled, all will be enabled.
Non-RFMon VAPs will be destroyed on multi-vap interfaces (ie, madwifi-ng)
Enabling channel hopping.
Enabling channel splitting.
FATAL: Unknown capture source type 'wlan1' in source 'wlan1,iwl4965,iwl4965'
Done.[/FONT]

Is there anyone who can help me to configure kismet?
thanks

---

### Post by chili555 on 2013-02-04
> **mappuso said:**
> Hello everyone,
I've got a similar problem of striker. Kismet doesn't run. 

Enabling channel splitting.
FATAL: Unknown capture source type 'wlan1' in source 'wlan1,iwl4965,iwl4965'
Done.[/FONT]

Is there anyone who can help me to configure kismet?
thanksPlease try:```
iwl4965,wlan1,Intel
```Post back the result and we'll try to troubleshoot fom there.

---

### Post by mappuso on 2013-02-05
Thanks chili555 for your help, but I've resolved upgrading kismet. I've not changed configuration file any more.

---

