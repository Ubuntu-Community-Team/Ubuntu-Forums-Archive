---
title: "Need drivers for Qlogic 2650"
date: 2013-07-11
forum: Networking &amp; Wireless
---

### Post by iron29 on 2013-07-11
Hi

I need help in getting drivers for Qlogic 2650 for one of our deployment. I have installed this card on one system with Ubuntu 12.4 on it. card does get detected and shows in dmesg as well but seems like need to provide drivers for the same.

---

### Post by chili555 on 2013-07-11
What does it say in dmesg about it? How about lspci?

---

### Post by iron29 on 2013-07-11
I have attached screenshots for your reference. I am assuming that If the card  is installed properly , it should list when we run ifconfig command?[ATTACH=CONFIG]244623[/ATTACH][ATTACH=CONFIG]244624[/ATTACH][ATTACH=CONFIG]244625[/ATTACH]

---

### Post by chili555 on 2013-07-11
I have good news and bad news. The good is that you have a driver *qla2xxx* that's included in recent versions of Ubuntu by default. It is loaded according to dmesg. It does require firmware, although it seems to be loading:> ...loading via request-firmware...And there seems to be no complaint about missing firmware. You might check to see that you actually have the firmware:```
ls /lib/firmware| grep ql2
```My 12.10 install includes it, so if it's missing, I can get it to you.```
$ modinfo qla2xxx
filename:       /lib/modules/3.5.0-36-generic/kernel/drivers/scsi/qla2xxx/qla2xxx.ko
[COLOR="#FF0000"]firmware:       ql2500_fw.bin
firmware:       ql2400_fw.bin
firmware:       ql2322_fw.bin
firmware:       ql2300_fw.bin
firmware:       ql2200_fw.bin
firmware:       ql2100_fw.bin[/COLOR]
version:        8.04.00.03-k
license:        GPL
description:    QLogic Fibre Channel HBA Driver
author:         QLogic Corporation
<snip>
```Now, the bad news is that I am not familiar with these devices at all, so, aside from finding and installing the drivers, I am not sure what's supposed to happen next. What is the expected behavior from here? Do I gather that a new networking interface is created? Or...?

If you run:```
modinfo qla2xxx
```You will see there are many parameters available. Ordinarily, ethernet, wireless, et al, parameters are invoked temporarily in Ubuntu by:```
sudo modprobe -r iwlwifi [COLOR="#FF0000"]<--as an example[/COLOR]
sudo modprobe iwlwifi 11n_disable=1
```And to invoke it automatically on boot, by writing a one-line conf file. I would assume the technique is the same here.

Your ethernet interfaces are, I assume, declared in /etc/network/interfaces, correct?

---

### Post by iron29 on 2013-07-11
Thanks for your reply.. It does have firmware file. but it gives firmware failed message at every log in. is there any way around or way to disable it?

---

### Post by chili555 on 2013-07-11
> **iron29 said:**
> Thanks for your reply.. It does have firmware file. but it gives firmware failed message at every log in. is there any way around or way to disable it?
It may be helpful to see the exact failed message. Do you have all six files in /lib/firmware?

---

### Post by iron29 on 2013-07-11
[ATTACH=CONFIG]244632[/ATTACH][ATTACH=CONFIG]244633[/ATTACH]

Hi

I have uploaded screenshots for your reference.

---

### Post by chili555 on 2013-07-11
Wonderful! It seems to be an actual recognized bug:  [https://bugs.launchpad.net/ubuntu/+source/linux-firmware/+bug/1117428](https://bugs.launchpad.net/ubuntu/+source/linux-firmware/+bug/1117428)> [ 7519.592610] qla2xxx [0000:28:00.0]-00fc:16: ISP2532: PCIe (5.0GT/s x4) @ 0000:28:00.0 hdma+ host#=16 fw=4.04.04 (80).
[ 7541.738556] qla2xxx [0000:28:00.0]-8038:16: Cable is unplugged...
[ 7541.738561] qla2xxx [0000:28:00.0]-803b:16: Firmware ready **** FAILED ****.In the bug report, the original poster says that, "...close this bug request as we have got to the bottom of the problem." I can only assume that the problem was solved by installing the later kernel as recommended. I suggest you try it as well.

I notice this parameter in the driver:> parm:           ql2xfwloadbin:Option to specify location from which to load ISP firmware:.
 2 -- load firmware via the request_firmware() (hotplug).
      interface.
 1 -- load firmware from flash.
 0 -- use default semantics.
 (int)
*Is* there a firmware file from your ISP? Do we need to direct the driver to its location; /home/user/firmware or some such? As I say, I am inexperienced with such devices, although I have learned a lot today.

EDIT: Off for the evening; see you tomorrow.

---

