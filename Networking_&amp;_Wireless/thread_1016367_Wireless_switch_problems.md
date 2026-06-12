---
title: "Wireless switch problems"
date: 2008-12-19
forum: Networking &amp; Wireless
---

### Post by Noah Schoem on 2008-12-19
I am using an old Gateway 7330GZ laptop running Intrepid Ibex.  It has a Broadcom wireless card and a Broadcom ethernet port.  I am unable to connect to any wireless networks.  Prior to uninstalling Windows, I may have turned off the wireless switch and I cannot turn it back on (it's a keyboard sequence (Fn+F2).  Without reinstalling Windows, how do I turn on the wireless switch?

---

### Post by miniyak on 2008-12-19
i dont think that this is that type of problem, it shouldnt matter what you did in xp, so fortunately it doesn't need to be reinstalled. however i believe broadcom is one of those companies that do not release open source drivers for their junk. A lot of people do not have wireless after installing ubuntu because of political reasons.. as far as im concerned. The good news is that this can be fixed. This is a common problem as far as i know, so some good info should all ready be on these forums or all over the web. in a nut shell, its called ndiswrapper, you install it then you find the proprietary drivers and its makes your card work. sorry im sending you somewhere else, ive only heard of the problem.

---

### Post by pytheas22 on 2008-12-19
Broadcom actually does have open-source drivers that should work well for most cards (although if yours is old, it's possible that it's not supported...but it would need to be really old).  They were reverse-engineered by volunteers, not provided by Broadcom, but they exist (Broadcom also [released a closed-source Linux driver]("http://ubuntuforums.org/showthread.php?t=880218") for a handful of cards last summer, but there are some issues with it, and it's very proprietary so it doesn't mix well with the licensing of most Linux distributions).

You should probably not need to use ndiswrapper for your card (although it's an option if all else fails).  The reason it's not working now is probably that it requires firmware before it can work (the switch being off is not likely the problem; the Linux driver should be able to turn the card on as well as Windows).

Anyway, the above was just FYI.  To figure out why your card won't work, please open a terminal (Applications>Accessories menu), run these commands and post the output:
```

lspci -nn | grep -i broadcom
lshw -C Network
sudo iwlist scan
dmesg | grep -e b43 -e ssb -e wlan
```

That will give a more exact idea of what's wrong; then we can fix it.

---

### Post by Noah Schoem on 2008-12-19
Pytheas22:  I took your advice and ran each command:

> nschoem@nschoem-laptop:~$ lspci -nn | grep -i broadcom
01:06.0 Ethernet controller [0200]: Broadcom Corporation BCM4401 100Base-T [14e4:4401] (rev 01)
01:09.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)
nschoem@nschoem-laptop:~$ lshw -C Network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Ethernet interface
       product: BCM4401 100Base-T
       vendor: Broadcom Corporation
       physical id: 6
       bus info: pci@0000:01:06.0
       logical name: eth0
       version: 01
       serial: 00:03:25:12:ed:64
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=b44 driverversion=2.0 latency=64 module=ssb multicast=yes
  *-network:1
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 9
       bus info: pci@0000:01:09.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network:0 DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:14:a5:3b:3a:33
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: d2:25:16:20:07:06
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
nschoem@nschoem-laptop:~$ sudo iwlist scan
[sudo] password for nschoem: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Network is down

pan0      Interface doesn't support scanning.

nschoem@nschoem-laptop:~$ dmesg | grep -e b43 -e ssb -e wlan
[    3.464337] b43-pci-bridge 0000:01:09.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    3.525074] ssb: Sonics Silicon Backplane found on PCI device 0000:01:09.0
[    3.640083] ssb: Sonics Silicon Backplane found on PCI device 0000:01:06.0
[   16.027288] b43-phy0: Broadcom 4318 WLAN found
[   28.334606] input: b43-phy0 as /devices/virtual/input/input9
[   28.432064] firmware: requesting b43/ucode5.fw
[   28.484049] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[   28.484070] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the latest firmware (version 4).
[   28.541543] input: b43-phy0 as /devices/virtual/input/input10
[   28.614422] firmware: requesting b43/ucode5.fw
[   28.629465] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[   28.629493] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the latest firmware (version 4).
[ 2337.333937] input: b43-phy0 as /devices/virtual/input/input11
[ 2337.413068] firmware: requesting b43/ucode5.fw
[ 2337.438465] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[ 2337.438497] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the latest firmware (version 4).
[ 3809.984612] b43-pci-bridge 0000:01:09.0: PCI INT A disabled
[ 3810.528021] b43-pci-bridge 0000:01:09.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[ 3810.528043] b43-pci-bridge 0000:01:09.0: restoring config space at offset 0x1 (was 0x102, writing 0x106)
nschoem@nschoem-laptop:~$ 



Ok, so it looks like some firmware is missing.  Question is, how do I install it?

---

### Post by pytheas22 on 2008-12-19
Yes, it looks like missing firmware.  These commands should install it:
```

sudo apt-get update
sudo apt-get install b43-fwcutter
```

Please post the output of those commands so that we can make sure that they do what they're supposed to.  After they run, you should reboot and then be able to use the wireless.

---

### Post by Noah Schoem on 2008-12-19
Here's a problem:  my Ubuntu laptop is not connected to the internet at all!

I have some tar.bz2 packages sitting on my desktop.  One is "b43-fwcutter-011.tar.bz2", the other is "broadcom-wl-4.150.t0.5.tar.bz2"

I understand that this is enough to install fwcutter and the proper firmware, but how?

If you wish to see the result of the two commands:

> nschoem@nschoem-laptop:~$ sudo apt-get update
Err [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release.gpg
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Translation-en_US
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Translation-en_US
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Translation-en_US
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Translation-en_US
  Could not resolve 'security.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid Release.gpg
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/main Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/restricted Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/universe Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/multiverse Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates Release.gpg
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/restricted Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/universe Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/multiverse Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Reading package lists... Done
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/intrepid/Release.gpg)  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid/main/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/intrepid/main/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid/restricted/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/intrepid/restricted/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid/universe/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/intrepid/universe/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid/multiverse/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/intrepid/multiverse/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/Release.gpg)  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/main/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/main/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/restricted/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/restricted/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/universe/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/universe/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/multiverse/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/multiverse/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/intrepid-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/intrepid-security/Release.gpg)  Could not resolve 'security.ubuntu.com'

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/intrepid-security/main/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/intrepid-security/main/i18n/Translation-en_US.bz2)  Could not resolve 'security.ubuntu.com'

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/intrepid-security/restricted/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/intrepid-security/restricted/i18n/Translation-en_US.bz2)  Could not resolve 'security.ubuntu.com'

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/intrepid-security/universe/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/intrepid-security/universe/i18n/Translation-en_US.bz2)  Could not resolve 'security.ubuntu.com'

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/intrepid-security/multiverse/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/intrepid-security/multiverse/i18n/Translation-en_US.bz2)  Could not resolve 'security.ubuntu.com'

W: Some index files failed to download, they have been ignored, or old ones used instead.
W: You may want to run apt-get update to correct these problems
nschoem@nschoem-laptop:~$ sudo apt-get install b43-fwcutter
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package b43-fwcutter
nschoem@nschoem-laptop:~$ 



---

### Post by pytheas22 on 2008-12-19
Yes, those commands won't work without an Internet connection!  Sorry for not asking whether you had one--I assumed you were plugged into the wire.

But you can still get the firmware.  Please download [this file]("http://burnthesorbonne.com/files/b43_firmware.tar.gz") and transfer it to your Ubuntu machine.  Save it on the desktop there.  Then run these commands:
```

cd ~/Desktop
tar -xzvf b43_firmware.tar.gz
cd b43_firmware/
sudo cp -R * /lib/firmware/
```

That should do it.  Reboot, and if things still don't work, please post the output of:
```

lshw -C Network
dmesg | grep -e b43 -e ssb -e wlan
```

---

### Post by Noah Schoem on 2008-12-19
Thanks!

Now it's working so well that I can't turn off my wireless switch, but at least I have a workaround for that.

---

### Post by pytheas22 on 2008-12-19
Glad to hear it's working :)

Sorry it was not as intuitive as it should be--normally a box would pop up that would prompt you to download the firmware after you boot into Ubuntu for the first time, but I guess in your case that never happened for some obscure reason.  Ubuntu won't include the firmware by default because the legality of its redistribution by parties other than Broadcom is a topic of dispute.

Also, I'm not sure why the switch won't work--if you want to try to troubleshoot it, press Fn-F2 a few times, then post the output of the command 'dmesg | tail' and we might be able to figure it out--but you can always manually put the card down by typing 'sudo rmmod b43'.  Type 'sudo modprobe b43' (or reboot) to make it come on again.

Either way, I hope you have fun with Ubuntu!

---

