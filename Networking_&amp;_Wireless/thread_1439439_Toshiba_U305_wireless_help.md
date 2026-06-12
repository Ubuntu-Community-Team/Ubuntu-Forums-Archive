---
title: "Toshiba U305 wireless help"
date: 2010-03-26
forum: Networking &amp; Wireless
---

### Post by tripower on 2010-03-26
I have a Toshiba Satellite U305-2812S and everything seems to work fine except wireless. (Ubuntu 9.01 64 bit). How can I check my existing driver if any and how can I update this wireless driver?

---

### Post by chili555 on 2010-03-26
Please open Applications > Accessories > Terminal and do:```
sudo lshw -C network
```You will find data about your ethernet and wireless devices. You can search for the wireless details for previous posts about how to get your device working or, if you are unsure, post the details here.

Here is an example:> *-network
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: [COLOR="Red"]wlan0[/COLOR]
       version: 02
       serial: 99:19:x2:c2:1b:88
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes [COLOR="Red"]driver=iwl3945[/COLOR] ip=192.168.1.103 latency=0 multicast=yes wireless=IEEE 802.11abg
       resources: irq:31 memory:edf00000-edf00fffIf you see an interface and a driver, you are all set; click the Network Manager icon at the top right of your desktop and connect.

---

### Post by tripower on 2010-03-26
> **chili555 said:**
> Please open Applications > Accessories > Terminal and do:```
sudo lshw -C network
```You will find data about your ethernet and wireless devices. You can search for the wireless details for previous posts about how to get your device working or, if you are unsure, post the details here.

Here is an example:If you see an interface and a driver, you are all set; click the Network Manager icon at the top right of your desktop and connect.

gotcha.

---

### Post by chili555 on 2010-03-26
You have a wireless interface and a driver. You needn't have ****** the logical name, or interface. It's wlan0. Let's try to find out why it's not working. Please run:```
rfkill list
dmesg | grep iwl
```

---

### Post by tripower on 2010-03-26
That worked thanks a bunch!

---

