---
title: "bcm4401 wired ethernet card 'disabled' in windows after ubuntu install"
date: 2013-03-30
forum: Networking &amp; Wireless
---

### Post by Jerrytu on 2013-03-30
Hi all,

I just installed latest ubuntu 12.04.02on my pc, configured as grub dual boot with my previous windows os. Now everything including wired ethernet works perfectly in ubuntu, but there is a strange thing  when I choose boot to windows.

Symptoms:

1. Wired cable plugged firmly into both my pc and router, but the ethernet LED indicator will not be lighted up until about 2 seconds before ubuntu login appears. It does not have any impact to ubuntu, wired ethernet works ok after login.

2. But that's really a big problem when I switched to boot windows, the bcm4401 would never work even after I re-installed the correct drivers and reboot. It seems there is no cable plugged in, the ethernet LED will never be lighted up!

From my experience, it's unreasonable. I think if my pc have power cable plugged in,  the wired ethernet LED on both ports  of my router and pc should be lighted up, even if the pc is not booted, right? So I can't figure out what's the cause of the problem. To me, it seems after install ubuntu, there is a 'lock' added to my NIC, only after boot  ubuntu to certain steps will 'unlock' it. 

That means without touching or moving any cable, any card, and any other hardware, my bcm4401 only works in unbuntu but not in windows.

My environment:

ubuntu:
     12.04.02 installed with latest 3.5 kernel iso image, updated all packages.

uname -a:
     Linux 3.5.0-26-generic #42~precise1-Ubuntu SMP

lspci | grep Eth:
    02:05.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01)

lsmod | grep b44   
    b44                    31365  0
    ssb                    50757  1 b44


Pls help me to analyse the root or possible cause of this strange problem.  Any advice will be appeciated. Thanks.

---

### Post by Hadaka on 2013-03-30
Hi, what is your windows version...7..8?
and have you tried a power reset on the router and
the computer??
thanks.

---

### Post by Jerrytu on 2013-03-31
> **Hadaka said:**
> Hi, what is your windows version...7..8?
and have you tried a power reset on the router and
the computer??
thanks.

Thank you for reply. I did several power reset test, no effect. It seems it's not a problem caused by windows. because the key symptom is the same on both os:  this bcm4401 Ethernet NIC will not be lighted up on a pc with power supply cable(with power of cause) plugged in, it abnormal. When I switched the same ethernet cable from this pc to another laptop, ports on both router and laptop NIC were on immediately. What I can conclude is it's not a router issue, it's not a windows issue, it's not a cable issue. And what I doubt is if it's a kernel issue, but it still need to find out how can ubuntu activate a 'hardware disabled' NIC. I really don't understand if any data can be 'stored' on a NIC card by a driver... 

If anybody can give me a possible explanation that why the NIC start to 'work' only after boot ubuntu to certain steps, I think that that will help me to find the root cause.

---

### Post by Jerrytu on 2013-03-31
Ok.  The strange problem is solved after analysis using 'broadcom  control suite' software. After install the latest bcm4401 NIC driver for  win, version 4.60., the NIC card can be activated in windows now. But  after several more tests, I can say there is a bug in my ubuntu  environment (should be the bug of kernel or driver). When ubuntu is  powered off or restarted, it will drop the NIC to 'no cable' mode, but  not the correct mode ' cable plugged but link down'. With my old NIC  driver  in windows, it will never reset the status again. But the new  broadcom driver for windows solved this issus, it will force the NIC up  during windows boot. So my problem is partially solved, now both ubuntu  and win can use the bcm4401. 

But as I mentioned, an OS should  never automatically change NIC status from 'link up' to 'no cable',  the  correct status after power off the pc should be ' cable plugged but  link down'. 

Anybody has the same problem may download the latest driver of bcm4401 from [here]("http://www.broadcom.com/support/ethernet_nic/4401.php"). It will not solved the bug on ubuntu, but will give a chance to aviod the painful impact to the windows.

---

