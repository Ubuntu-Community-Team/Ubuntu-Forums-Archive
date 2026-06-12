---
title: "Fixing Broadcom wireless 4311 module"
date: 2009-05-14
forum: Networking &amp; Wireless
---

### Post by Volt9000 on 2009-05-14
I've got a laptop with a Broadcom 4311 wireless card, as described by the output of lspci. I've been looking at tutorials and guides on ndiswrapper, and found a guide in this thread:

[http://ubuntuforums.org/showthread.php?t=1072243](http://ubuntuforums.org/showthread.php?t=1072243)

I followed the instructions in Ayuthia's post, and typed in the following commands:

```

sudo modprobe -r b43 b44 ssb wl
sudo modprobe wl
sudo modprobe b44
sudo /etc/init.d/networking restart
sudo iwlist scan

```

After I do this, my wireless starts working. But the problem is this is only temporary, and after I restart I have to type these all over again.
What can I do to make these changes permanent?

---

### Post by Ayuthia on 2009-05-14
You might try the following:
```
echo -e '#ssb workaround, added' `date` '\ninstall wl modprobe -r b43 b44 b43legacy ssb wl; modprobe --ignore-install wl' | sudo tee -a /etc/modprobe.d/wl.conf
```

I have not had a chance to test it, but I think that it should work in Jaunty (9.04).  If you are using an older version, you will need to change wl.conf back to wl.

Hope that helps.

---

### Post by Volt9000 on 2009-05-14
Thanks for the reply but this didn't work. This did was create a file called "wl" in my /etc/modprobe.d directory with the following contents:

```

#ssb workaround, added Thu May 14 22:12:11 EDT 2009 
install wl modprobe -r b43 b44 b43legacy ssb wl; modprobe --ignore-install wl

```

However when I restart Ubuntu nothing seems to change.

I'm using Intrepid, BTW.

---

### Post by mjoolnir on 2009-05-14
Try blacklisting b43 and ssb [http://www.the-little-things.net/blog/?p=32](http://www.the-little-things.net/blog/?p=32)

---

### Post by Volt9000 on 2009-05-14
I tried blacklisting both, no dice.
Any other suggestions?

---

### Post by mjoolnir on 2009-05-14
> **Volt9000 said:**
> I tried blacklisting both, no dice.
Any other suggestions?

Ah I read the first post wrong, I'm not sure what is wrong but the blacklist suggestion won't work. For the time being you could make a bash alias to do all that, at least you won't have to type it out.

---

### Post by Ayuthia on 2009-05-16
> **Volt9000 said:**
> Thanks for the reply but this didn't work. This did was create a file called "wl" in my /etc/modprobe.d directory with the following contents:

```

#ssb workaround, added Thu May 14 22:12:11 EDT 2009 
install wl modprobe -r b43 b44 b43legacy ssb wl; modprobe --ignore-install wl

```

However when I restart Ubuntu nothing seems to change.

I'm using Intrepid, BTW.

Ok.  We should remove this file:
```
sudo rm /etc/modprobe.d/wl
```

We can then try adding the commands to rc.local.  Open up rc.local:
```
gksu /etc/rc.local
```Above the exit 0 line, add the following:
```
modprobe -r b43 b44 ssb wl
modprobe wl
modprobe b44

```
Save the file and hopefully that will fix it.  Having these commands in rc.local will run those commands automatically for you.

---

### Post by Volt9000 on 2009-05-19
Thanks Ayuthia, worked like a charm!

---

### Post by Volt9000 on 2009-05-24
Ah crud... did an update, and now it no longer works. :(
When I hover my mouse cursor over the Network Manager icon it says something like "Network manager not enabled". What gives?

---

### Post by Ayuthia on 2009-05-24
You might check in the Terminal:
```
lshw -C network
```
and see if your wireless card shows up and that the wl module is showing as the driver.

---

### Post by Volt9000 on 2009-05-24
Here's the output:

```

WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: eth1
       version: 01
       serial: 00:19:7e:b3:85:06
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.10.27.12 latency=0 module=wl multicast=yes wireless=IEEE 802.11
  *-network DISABLED
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:19:b9:80:af:cf
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=b44 driverversion=2.0 latency=64 module=ssb multicast=yes
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: a6:02:d3:73:b2:03
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

```

The wireless network adapter is enabled, using driver wl0 and module wl, but strangely the wired Ethernet adapter is disabled.

Here's my /etc/rc.local file:

```

#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

# Fix for the Broadcom 4311 wireless module
modprobe -r b43 b44 ssb wl
modprobe wl
modprobe b44
exit 0

```

I've verified the file's permissions are 755.

---

### Post by Volt9000 on 2009-05-24
I looked through the output of dmesg and found some interesting lines:

```

...
[   27.273223] input: b43-phy0 as /devices/virtual/input/input10
[   27.473145] firmware: requesting b43/ucode5.fw
[   27.500603] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[   27.500611] b43-phy0 ERROR: You must go to http://linuxwireless.org/en/users/Drivers/b43#devicefirmware and download the latest firmware (version 4).
[   29.135096] b44: eth0: powering down PHY
[   29.177170] b44 0000:03:00.0: PCI INT A disabled
[   29.194486] b43-pci-bridge 0000:0c:00.0: PCI INT A disabled
[   29.254811] ieee80211_crypt: registered algorithm 'NULL'
[   29.260726] wl 0000:0c:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   29.260751] wl 0000:0c:00.0: setting latency timer to 64
[   29.279606] ieee80211_crypt: registered algorithm 'TKIP'
[   29.279762] eth0: Broadcom BCM4311 802.11 Wireless Controller 5.10.27.12
[   29.287836] udev: renamed network interface eth0 to eth1
[   29.520051] b44 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   29.580100] ssb: Sonics Silicon Backplane found on PCI device 0000:03:00.0
[   29.580135] b44.c:v2.0
[   29.608507] eth0: Broadcom 44xx/47xx 10/100BaseT Ethernet 00:19:b9:80:af:cf
[   31.117884] NET: Registered protocol family 17
[   31.700556] NetworkManager[5299]: segfault at 0 ip b7ad0323 sp bfba321c error 4 in libc-2.8.90.so[b7a59000+158000]
...

```

Looks like the reason NetworkManager isn't running is because of a segmentation fault-- why, I don't know. Possibly due to the missing firmware file it complains about at the beginning?

---

### Post by Volt9000 on 2009-05-24
Ok well I tried installing that driver as suggested, and everything seemed to work because I get no errors in the dmesg output, but NetworkManager is still segfaulting...

```

...
[   30.611214] NetworkManager[5304]: segfault at 0 ip b7ba3323 sp bfb7616c error 4 in libc-2.8.90.so[b7b2c000+158000]
...

```

---

### Post by Volt9000 on 2009-05-24
Ok, well I got it working.
After installing the drivers it suggested, I removed the modprobe lines from the /etc/rc.local file, and now all is well-- wired and wireless.

Wonder why those modprobe lines caused NetworkManager to fail like that.

---

### Post by Ayuthia on 2009-05-24
You might check lshw -C network again.  My guess is that you are now switched back to the b43 module instead of the wl module.  The messages that you saw in dmesg were telling you how to install the firmware to make the b43 module work.

You might check in the logs in /var/log to see what was installed in that last update.  My guess is that there was an update to NetworkManager that might have caused NetworkManager to crash with the wl module.

---

