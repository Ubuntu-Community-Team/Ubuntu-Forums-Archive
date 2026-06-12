---
title: "Cannot install Wi-Fi drivers in Ubuntu 12.10"
date: 2013-04-29
forum: Networking &amp; Wireless
---

### Post by Ramche on 2013-04-29
Hi guys, I just installed Ubuntu 12.10, but there is no Wi-Fi driver form my HP ProBook 4510s. I am trying all the time to install the HP official drivers from ([link]("http://h20000.www2.hp.com/bizsupport/TechSupport/SoftwareIndex.jsp?lang=en&cc=us&prodNameId=3934829&prodTypeId=321957&prodSeriesId=3934828&swLang=13&taskId=135&swEnvOID=2020")) but I cannot install. I cannot understand are they compatible with this version of Linux?
Please someone help me, I am a beginner on Ubuntu.
Thank you! ;)

---

### Post by Ramche on 2013-04-29
Hi guys, I just installed Ubuntu 12.10, but there is no Wi-Fi driver form my HP ProBook 4510s. I am trying all the time to install the HP official drivers from (link) but I cannot install. I cannot understand are they compatible with this version of Linux?
Please someone help me, I am a beginner on Ubuntu.
Thank you! ;)

---

### Post by fantab on 2013-04-29
Post the output of:

```
lspci
```

---

### Post by Bucky Ball on 2013-04-29
*Thread moved to **Networking & Wireless***

Better still:

```
sudo lshw -C network

```
This will tell us if there is a driver already loaded, its state and the make/model of your card (with any luck).

---

### Post by Ramche on 2013-04-29
```
Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)
```

I think this was my Wirelass card of my laptop...

---

### Post by Ramche on 2013-04-29
```
*-network UNCLAIMED     
       description: Network controller
       product: BCM4312 802.11b/g LP-PHY
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:d8200000-d8203fff


```
and so on....

---

### Post by howefield on 2013-04-29
Threads merged, please stick to one thread. Makes it easier for people to offer help.

---

### Post by Bucky Ball on 2013-04-29
You'll need to get online with a cable and install, from Synaptics or Software Centre:

b43-fwcutter
firmware-b43-lpphy-installer

You might need to restart but I think that should work.

Is there a driver disabled in 'Additional Drivers'? (It would be b43 or STA.)

---

### Post by Ramche on 2013-04-30
Hey it is working now, I hden't installed the firmware-b43-lpphy-installer.
Befor I installed firmware-b43-lpphy-installer, I tried several times to activate the driver of my Wi-Fi card found by the 'Additional drivers', but it used to fail. After I installed firmware-b43-lpphy-installer it worked.
Thank you!

---

