---
title: "wifi driver not seems to be working"
date: 2010-11-23
forum: Networking &amp; Wireless
---

### Post by sea_coffee_programmer on 2010-11-23
I have been working on this for a long time now and not much progress, but i have a large amount of information i will give to you all to help with diagnosis.

1)  Broadcom STA wireless driver
----  Installed the driver for my driver
----  System-> Administration-> hardware
----  "This driver is activated by not currently in use."

2)  I updated my system to most recent with sudo apt-get update or what-not

3)  I was following the STA information on the following website:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)
----  Seems to be a temporary resolve as when i reboot, the driver seems to be uninstalled.

4)  lsmod has shown me that the modules are not loaded when the laptop restarts.
----  I am not really sure on how to make it a perma- loaded module.

5)  when i use iwconfig
----  there is no wifi elements at all, only lo and eth1 as my computer is hooked up via cable to type this.
-------- lo = local loopback
-------- eth1 = ethernet cable.


This is all of the information in which i have at the moment, it seems that i have issue piping, or erm.. making the wireless card do its jjob and appear under the something like wfi1 or whatever it is for iwconfig so that i can connect to internet regularly.

Let me know if there is more information, but i was thinking this would be enough.

Also, when doing the update, im pretty sure that it updated to the most current version of UBUNTU.

Cheers~

Sea_coffee_programmer.

---

### Post by chili555 on 2010-11-23
Please do:```
sudo modprobe b43
iwconfig
```Do you now have a wireless interface? Can you connect? If so, let's make it load automagically; please do:```
sudo su
echo b43 >> /etc/modules
exit
```If b43 is not the module or this doesn't fix the problem, please post back with:```
dmesg | grep -e b43 -e wl
```Thanks.

---

### Post by sea_coffee_programmer on 2010-11-23
I am not 100% sure if it worked as every time i reboot, i enter sudo modprobe as i have written prior.


The output from what you told me was as follows:

[   16.429583] wl: module license 'MIXED/Proprietary' taints kernel.
[   16.446724] wl 0000:03:00.0: PCI INT A -> Link[LK4E] -> GSI 19 (level, high) -> IRQ 19
[   16.446731] wl 0000:03:00.0: setting latency timer to 64
[   18.980237] wl 0000:03:00.0: PCI INT A disabled
[  118.161846] wl 0000:03:00.0: PCI INT A -> Link[LK4E] -> GSI 19 (level, high) -> IRQ 19
[  118.161862] wl 0000:03:00.0: setting latency timer to 64

---

### Post by sea_coffee_programmer on 2010-11-23
It seems to work, i rebooted and it seemed to run that module and allow for wireless connection.  Now i need to adjust it to work with the campus wifi as it uses some stupid stuff but ill figure that out later. :)

Thanks alot!

*cheers*

---

### Post by chili555 on 2010-11-23
> every time i reboot, i enter sudo modprobe as i have written prior.

Then please do:```
sudo su
echo wl >> /etc/modules
exit
```

---

