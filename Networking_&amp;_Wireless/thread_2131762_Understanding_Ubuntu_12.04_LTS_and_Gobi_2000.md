---
title: "Understanding Ubuntu 12.04 LTS and Gobi 2000"
date: 2013-04-02
forum: Networking &amp; Wireless
---

### Post by NomadAU on 2013-04-02
Hi,

While I am far from being a Linux novice, I am still very confused by the workings of my Gobi 2000 wireless card and Ubuntu (12.04 LTS).  I am running this on a Thinkpad W510 with a built-in 3G card.  Before moving across to Ubuntu, I was running RHEL and the wireless setup was working just fine, so I am pretty confident that this configuration can work well together.

If I start up Ubuntu (cold start) then all is good - my 3G is visible, and I can connect using it.

The problem I am trying to diagnose is that often (but not always) after I have Suspended then Resumed, the 3G is no longer visible.  Not only is it no longer visible in the Network Manager, but running **dmesg** (and grep'ing for Qualcomm) seems to indicate that the last activity was to disconnect the device
 
[   28.528884] USB Serial support registered for Qualcomm USB modem
[   28.530017] qcserial 2-1.4:1.1: Qualcomm USB modem converter detected
[   28.530148] usb 2-1.4: Qualcomm USB modem converter now attached to ttyUSB0
[   28.532168] qcserial 2-1.4:1.2: Qualcomm USB modem converter detected
[   28.532335] usb 2-1.4: Qualcomm USB modem converter now attached to ttyUSB1
[   28.533344] qcserial 2-1.4:1.3: Qualcomm USB modem converter detected
[   28.533568] usb 2-1.4: Qualcomm USB modem converter now attached to ttyUSB2
[  190.935461] qcserial ttyUSB0: Qualcomm USB modem converter now disconnected from ttyUSB0
[  190.935664] qcserial ttyUSB1: Qualcomm USB modem converter now disconnected from ttyUSB1
[  190.935868] qcserial ttyUSB2: Qualcomm USB modem converter now disconnected from ttyUSB2

If it's not attached as a tty device, then nothing higher up the stack will be able to access it.
It looks to me as though the first problem I need to fix is how to get it to be recognised (and re-attached) when resuming from a Suspend.

Any ideas on how to further debug this?

---

