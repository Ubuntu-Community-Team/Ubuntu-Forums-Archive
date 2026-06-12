---
title: "Qualcomm Gobi 2000 hs-usb, UMTS on a T510"
date: 2010-09-17
forum: Networking &amp; Wireless
---

### Post by hendo2515 on 2010-09-17
Hi,

Does anyone know how to get the internal UMTS device working on a T510 on 10.04. I believe there is a Qualcomm Gobi 2000 hs-usb device on board. I have seen a bug at [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/554099](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/554099) and not sure if this applies. I am not an overly experienced ubuntu user.

---

### Post by hendo2515 on 2010-09-20
Further to this I installed the backport as mentioned towards the end of the bug report in the above message and restarted the computer. I got an NVIDIA error decided to use the reduced graphics and was able to connect fine. Restarted the laptop reconfigured the drivers on the drivers error screen resetting to default and now cant see the driver in NM.

When I look in the log i see:

Sep 20 09:50:18 mel-prg01 kernel: [ 13.979322] USB Serial support registered for Qualcomm USB modem
Sep 20 09:50:18 mel-prg01 kernel: [ 13.979348] qcserial 2-1.4:1.1: Qualcomm USB modem converter detected
Sep 20 09:50:18 mel-prg01 kernel: [ 13.979421] usb 2-1.4: Qualcomm USB modem converter now attached to ttyUSB0

rhenderson@mel-prg01:~$ lsusb
Bus 002 Device 003: ID 05c6:9204 Qualcomm, Inc.
Bus 002 Device 002: ID 8087:0020
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 005: ID 17ef:480f Lenovo
Bus 001 Device 004: ID 0a5c:217f Broadcom Corp.
Bus 001 Device 003: ID 147e:2016 Upek Biometric Touchchip/Touchstrip Fingerprint Sensor
Bus 001 Device 002: ID 8087:0020
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

Laptop is a Lenovo T510 running 64bit lucid. Any ideas?

---

### Post by hendo2515 on 2010-09-20
Ok got it. So going to answer this one in case other people have the same issue. 

So I installed the backport package according to this [comment]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/554099/comments/119"). If you need to find out how to get to the backports package then look [here]("https://wiki.ubuntu.com/Testing/EnableProposed")

Installed the latest qualcomm drivers on my windows partition ([http://www-307.ibm.com/pc/support/site.wss/document.do?lndocid=MIGR-72938]("http://www-307.ibm.com/pc/support/site.wss/document.do?lndocid=MIGR-72938")). Use [wine]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/554099/comments/76") if you don't have a windows partition

C:\Program Files (x86)\Qualcomm\Images\Lenovo\UMTS\AMSS.mbn
C:\Program Files (x86)\Qualcomm\Images\Lenovo\UMTS\Apps.mbn
C:\Program Files (x86)\Qualcomm\Images\Lenovo\0\UQCN.mbn

Copy these 3 files into

/lib/firmware/gobi

(need to create directory and copy with sudo).

Then reboot the laptop. I could then see the Qualcomm device when i add a mobile broadband connection. Hope this helps you all

---

### Post by fsoldera on 2011-07-10
Thank you so much, you saved my day!!! It worked at the first attempt :-)

I had the drivers already installed in the Windows 7 partition. I just copied them with "sudo".

Hardware: ThinkPad Edge 13" (Intel)
OS: Ubuntu 11.04 (Natty)


> **hendo2515 said:**
> Ok got it. So going to answer this one in case other people have the same issue. 

So I installed the backport package according to this [comment]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/554099/comments/119"). If you need to find out how to get to the backports package then look [here]("https://wiki.ubuntu.com/Testing/EnableProposed")

Installed the latest qualcomm drivers on my windows partition ([http://www-307.ibm.com/pc/support/site.wss/document.do?lndocid=MIGR-72938]("http://www-307.ibm.com/pc/support/site.wss/document.do?lndocid=MIGR-72938")). Use [wine]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/554099/comments/76") if you don't have a windows partition

C:\Program Files (x86)\Qualcomm\Images\Lenovo\UMTS\AMSS.mbn
C:\Program Files (x86)\Qualcomm\Images\Lenovo\UMTS\Apps.mbn
C:\Program Files (x86)\Qualcomm\Images\Lenovo\0\UQCN.mbn

Copy these 3 files into

/lib/firmware/gobi

(need to create directory and copy with sudo).

Then reboot the laptop. I could then see the Qualcomm device when i add a mobile broadband connection. Hope this helps you all

---

