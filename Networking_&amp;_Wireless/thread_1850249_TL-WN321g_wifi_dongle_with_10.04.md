---
title: "TL-WN321g wifi dongle with 10.04"
date: 2011-09-26
forum: Networking &amp; Wireless
---

### Post by chrisbay90 on 2011-09-26
I am trying to get a TP-Link USB wirless dongle model TL-WN321g to work with a Ubuntu 10.04 desktop. By all other accounts it seems this dongle should work out the box (why I chose it). However this is not the case.

I have noticed it works straight out of the box on another Ubuntu laptop. On the machine it works on lsusb presents the device as.
```
$ lsusb
Bus 001 Device 004: ID 148f:2070 Ralink Technology, Corp. RT2070 Wireless Adapter

```

However on the problem machine it is presented as:
```
$ lsusb
Bus 001 Device 002: ID 148f:2070 Ralink Technology, Corp.

```

From other sources on the net I beleive this device has the rt73usb chip is in this device.
There does exist a file  /lib/firmwar/rt73.bin on the problem machine
I installed the package rt73-common
I have run modprobe rt73usb
I have start/stoped network manager and uninstalled reinstalled it.
I have rebooted the machine sever times
There are no packages that can be updated on the system
The device still does not appear in network manager and still displays the same under lsusb

Does anyone have some suggestions as to what the issue may be or a path to a resolution?

---

### Post by praseodym on 2011-09-26
Hi,

its working ootb with Natty, in Lucid you need to add the device ID to the module rt2870sta:

One line (copy/paste):

```
echo 'install rt2870sta modprobe --ignore-install rt2870sta ; /bin/echo "148f 2070" > /sys/bus/usb/drivers/rt2870/new_id' | sudo tee /etc/modprobe.d/rt2870sta.conf
```
and update the firmware:

[http://de.archive.ubuntu.com/ubuntu/pool/main/l/linux-firmware/linux-firmware_1.52_all.deb](http://de.archive.ubuntu.com/ubuntu/pool/main/l/linux-firmware/linux-firmware_1.52_all.deb)

The module rt2800usb has to be blacklisted:

```
echo "blacklist rt2800usb" | sudo tee -a /etc/modprobe.d/blacklist.conf 
```
Additionally you can set up an UDEV-rule:

```
gksudo gedit /etc/udev/rules.d/10-wlan_stick.rules 
```
Insert:
```
# UDEV-Rule for Tp-Link TL-WN321G Rev.1 ID 148f:2070
SUBSYSTEM=="usb", ATTR{idVendor}=="148f", ATTR{idProduct}=="2070", RUN+="/sbin/modprobe rt2870sta"
```
save, exit, and reload udev:
```
sudo service udev reload
```
reboot.

---

### Post by chrisbay90 on 2011-09-26
Thank you very much praseodym. I really appreciate you taking the time to give me such thorough intructions.

I have since past this problem on to a much more experienced user than myself. I passed these instructions allow with it.

Again thank you for your help.

---

### Post by painguin on 2011-10-01
I've got another one for you...

This is a TP-Link:  TL-WN821N (Wireless-N USB Dongle)...

I've read many forum threads on here and on other forums and even found a solution, I thought.  But the driver I needed to install was not in the package that the creator of the how to provided the link for.  

When I plug the adapter into my desktop I do not hear a sound.  There is no notification that a new device has even been plugged into the PC.  I am not experienced with Linux to the point to where I can troubleshoot this.  

Here is a link to the products webpage:  [http://www.tp-link.com/en/products/details/?model=TL-WN821N](http://www.tp-link.com/en/products/details/?model=TL-WN821N)

Any help would be appreciated. 

Thanks in advance!

PAinguIN

---

### Post by painguin on 2011-10-01
> **painguin said:**
> I've got another one for you...

This is a TP-Link:  TL-WN821N (Wireless-N USB Dongle)...

I've read many forum threads on here and on other forums and even found a solution, I thought.  But the driver I needed to install was not in the package that the creator of the how to provided the link for.  

When I plug the adapter into my desktop I do not hear a sound.  There is no notification that a new device has even been plugged into the PC.  I am not experienced with Linux to the point to where I can troubleshoot this.  

Here is a link to the products webpage:  [http://www.tp-link.com/en/products/details/?model=TL-WN821N](http://www.tp-link.com/en/products/details/?model=TL-WN821N)

Any help would be appreciated. 

Thanks in advance!

PAinguIN

Oh yes, 

I am running Ubuntu 11.04 (natty) x64 if this helps.  Thanks!

---

