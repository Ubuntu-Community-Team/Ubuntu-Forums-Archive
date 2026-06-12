---
title: "Newbie Networking/Wireless Question"
date: 2010-10-22
forum: Networking &amp; Wireless
---

### Post by hell_rider on 2010-10-22
Hello all,

Am a newbie in terms of Linux troubleshooting / internals.

Running Ubuntu 8.04 LTS on a Toshiba Satellite A100 laptop.  My wireless is running properly (touchwood).

But I have some doubts regarding the wireless drivers in use.

My wireless hardware is as follows:

```
$ lspci | grep Wireless 
05:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
```

Modprobe reveals the following information:
```
$ modprobe -l | grep ipw
/lib/modules/2.6.24-28-generic/kernel/drivers/usb/serial/ipw.ko
/lib/modules/2.6.24-28-generic/kernel/drivers/net/wireless/ipw2200.ko
/lib/modules/2.6.24-28-generic/kernel/drivers/net/wireless/ipw2100.ko

$modprobe -l | grep 3945
/lib/modules/2.6.24-28-generic/ubuntu/wireless/iwlwifi/iwlwifi/compatible/iwl3945.ko
```

Now, according to some googling I did, specifically as per this page,
[http://www.dotkam.com/2008/09/29/sure-way-to-restart-a-wireless-network/](http://www.dotkam.com/2008/09/29/sure-way-to-restart-a-wireless-network/)

the driver for my wireless should be ipw3945.ko

My queries are as follows:

[LIST=1]
[*]Why is it showing something different for my wireless ?  
[*]How is one to determine which is the driver actually being used ??
[*]Where/which are the files (e.g. in the /etc folder) which store the settings for wireless ?
[/LIST]
Many thanks in advance.  I would really like to start understanding some of the "internals" of my installation.

Thanks and Regards.

---

### Post by utilitytrack on 2010-10-22
In newer kernels (for example, 2.6.32) appropriate kernel module for Intel 3945ABG is [FONT="Courier New"]iwl3945[/FONT].

---

### Post by hell_rider on 2010-10-22
Thanks utilitytrack.

Your clarification much appreciated.

But this raises a couple of doubts for me.

[LIST=1]
[*]modprobe is now listing 4 drivers for wireless all of which seem to be loaded.  Isn't something wrong here ?  How do I know for sure which is the one actually being used ?
[*]Can't the other three drivers be unloaded ??  How do I prevent them from being loaded at startup if they are not needed ?
[*]Is there a specific path for the drivers to be loaded, or is it all just arbitrary ?
[/LIST]

Would really appreciate it if you can clear my doubts.

Thanks and Regards.

---

### Post by hell_rider on 2010-10-22
I went through the info pages.

As I understand modprobe -l only lists the available modules. 
lsmod is the one that actually shows the loaded modules.

Is my understanding correct ??

If yes, the following output shows 2 modules loaded:
```
$ lsmod | grep 3945
iwl3945                89840  0 
iwlwifi_mac80211      219236  1 iwl3945
```

Does this output mean there are 2 wireless modules loaded ??

Thanks and Regards.

---

### Post by utilitytrack on 2010-10-22
The module iwl3945 is a driver for Intel 3945ABG wireless card. This module depends (in your case) of a mac80211 module, which is the IEEE 802.11 subsystem.

For newer kernels (2.6.35 in my case) a list of drivers for several Intel Wireless WiFi Link adapters looks like:
```
$ ls -l /lib/modules/2.6.35.4-custom/kernel/drivers/net/wireless/iwlwifi/*
-rw-r--r-- 1 root root  79K Sep  6 06:46 /lib/modules/2.6.35.4-custom/kernel/drivers/net/wireless/iwlwifi/iwl3945.ko
-rw-r--r-- 1 root root 144K Sep  6 06:46 /lib/modules/2.6.35.4-custom/kernel/drivers/net/wireless/iwlwifi/iwlagn.ko
-rw-r--r-- 1 root root 108K Sep  6 06:46 /lib/modules/2.6.35.4-custom/kernel/drivers/net/wireless/iwlwifi/iwlcore.ko
```

Full list of hardware which supported by this three modules you can see on
[http://wiki.debian.org/iwlwifi#supported]("http://wiki.debian.org/iwlwifi#supported") and [http://wiki.debian.org/iwlagn#SupportedDevices]("http://wiki.debian.org/iwlagn#SupportedDevices")

---

### Post by hell_rider on 2010-10-22
Thanks utilitytrack.

Things are clearer.

---

