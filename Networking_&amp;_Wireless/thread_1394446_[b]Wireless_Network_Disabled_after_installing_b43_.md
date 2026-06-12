---
title: "[b]Wireless Network Disabled after installing b43 drivers"
date: 2010-01-30
forum: Networking &amp; Wireless
---

### Post by aman_josan2001 on 2010-01-30
I installed the b43 drivers to enable the monitor mode for using kismet. but after installing, it shows "Device not Ready"

the dmesg | grep b43 output shows:
[   86.449430] b43 ssb0:0: firmware: requesting b43/ucode15.fw
[  146.449335] b43 ssb0:0: firmware: requesting b43-open/ucode15.fw
[  206.448146] b43-phy0 ERROR: Firmware file "b43/ucode15.fw" not found
[  206.448153] b43-phy0 ERROR: Firmware file "b43-open/ucode15.fw" not found
[  206.448158] b43-phy0 ERROR: You must go to [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware for this driver version. Please carefully read all instructions on this website.

Please help me to re-enable my wireless connection.

---

### Post by chili555 on 2010-01-30
The instructions you were pointed to in *dmesg* gives the following:> Ubuntu/Debian

In recent versions of Ubuntu and Debian, installing the b43-fwcutter package will handle everything for you:

```
sudo apt-get install b43-fwcutter
```

You will be asked to automatically fetch and install the firmware into the right location. Please connect to a wired ethernet connection and proceed.

---

### Post by aman_josan2001 on 2010-01-30
Thanks for the reply..

But i think my card is not supported by these drivers
so i just want to revert back to the STA drivers 
please guide me how to do that as i had blacklisted those drivers earlier

Thanks in advance..

---

