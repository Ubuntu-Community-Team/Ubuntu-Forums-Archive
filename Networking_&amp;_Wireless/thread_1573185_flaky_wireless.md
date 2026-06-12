---
title: "flaky wireless"
date: 2010-09-12
forum: Networking &amp; Wireless
---

### Post by MarionM on 2010-09-12
Hello,

I upgraded my Lenovo N500 laptop to use Ubuntu 10.4 some time ago. At that point my wireless stopped working. I tried off and on to get it working, with no success. 

Today I downloaded the 10.4 live CD iso and tried booting from the CD. I went into the 

System->Administration->Hardware Drivers

and tried "enable B43" and after downloading the drivers, after a while it was able to connect to my non-encrypted wireless (as it had done before the upgrade). That told me there are no hardware issues. With this new information, I rebooted from  the hard drive and tried to find the same "enable B43" but could only find the "enable Broadcom STA wireless driver" which I did not do. However, some magic happened (which I did not knowingly instigate) and to my great surprise, I was connected to my wireless connection. Naturally I was overjoyed, so I rebooted just to confirm my joy. I am back to no wireless!

What is going on?

Marion

>cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04.1 LTS"


>lshw -C network
WARNING: you should run this program as super-user.
PCI (sysfs)  
  *-network UNCLAIMED     
       description: Network controller
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
       resources: memory:f4700000-f4703fff

---

### Post by bryanfblareunion on 2010-09-12
New linux distributions seem to always have problems with wireless on laptops. I had this same problem. (luckily it turned out i was typing in wrong wpa key) 

Here's what I would do: boot into an earlier kernel. When you boot up it gives you about two or three choices. Boot into an earlier generic kernel and try wireless in there. It does basically zero to your distro that you will notice, but it does improve wireless chances.

---

### Post by MarionM on 2010-09-13
Thanks for your help. But that didn't work. Any other suggestions?

Marion

---

