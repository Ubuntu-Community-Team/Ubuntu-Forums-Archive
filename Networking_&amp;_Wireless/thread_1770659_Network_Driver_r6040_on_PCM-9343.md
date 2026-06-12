---
title: "Network Driver r6040 on PCM-9343"
date: 2011-05-29
forum: Networking &amp; Wireless
---

### Post by signpainter on 2011-05-29
Hi folks,

I'm trying to get Ubuntu 10.04 running on a [PCM-9343 board from Advantech]("http://www.advantech.com.tw/products/PCM-9343/mod_91657A08-723C-4407-8B54-9B3FC0745C69.aspx"). To do so I followed the instructions in this file from DM&P [ftp://download@ftp.dmp.com.tw/vortex86dx/linux/Debian+Ubuntu_Linux_Installation_Guide.pdf](ftp://download@ftp.dmp.com.tw/vortex86dx/linux/Debian+Ubuntu_Linux_Installation_Guide.pdf)

I installed a text-only Ubuntu using the alternate installer on a CF card that was connected to my PC. After reboot I downloaded the given kernel and updated the installation on the card, as said in the instructions.
Inserting the card into the PCM-9343 gives a working Ubuntu Installation. So far so good.

The only thing not working is networking. The ethernet adapter is not loaded on boot, neither can I up it after logging in using "ifup -a".

I found out, that the driver was not loaded during booting, i.e. the module r6040 didn't show up on "lsmod". The module is included in the modified kernel, that I downloaded from the producer's page. So I added it to /etc/modules and rebooted. Now it's loaded, but still no eth0. 
Ifup -a gives the following messages:
SIOCSIFADDR: No such device
eth0: ERROR while getting interface flags: No such device
eth0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth0.

The content of /etc/network/interfaces
#The loopback network interface
auto lo
iface lo inet loopback

#The primary network interface
auto eth0
iface eth0 inet dhcp

And lspci gives:
00:08.0 Ethernet Controller: RDC Semiconductor, Inc. R6040 MAC Controller

Can anyone help me with that? I'm quite helpless... 

Thanks alot.

signpainter

---

### Post by chili555 on 2011-05-29
I know nothing about your board or the ethernet device, but I know a bit about drivers. Let's do some diagnostics. I assume the module is named r6040. If that's incorrect, please substitute as needed. Please run:```
lspci -nn
```Find out the pci.id for the device. It will be in the form of 1234:abcd or some such. Then run:```
modinfo r6040 | grep ABCD
```where ABCD is the last four characters of the pci.id with any letters capitalized. We will learn if the driver claims your device. Also see if there are any interesting messages in:```
dmesg | grep -i r6040
```How did you install the ethernet driver? Were there any errors or warnings?

---

### Post by signpainter on 2011-05-29
> **chili555 said:**
>  I assume the module is named r6040. If that's incorrect, please substitute as needed. Please run:```
lspci -nn
```Find out the pci.id for the device.
This gives me

00:08.0 Ethernet controller [0200]: RDC Semiconductor, Inc. R6040 MAC Controller [17f3:6040]

So pci.id = 17f3:6040

> **chili555 said:**
> Then run:```
modinfo r6040 | grep ABCD
```where ABCD is the last four characters of the pci.id with any letters capitalized. We will learn if the driver claims your device.

In my case ABCD is 6040. Running the command gives:

filename: /lib/modules/2.6.30-vortex86mx/kernel/drivers/net/r6040.ko
description: RDC R6040 NAPI PCI FastEthernet driver
alias: pci:v000017F3d00006400sv*sd*bc*sc*i*

Seems to me like the driver is the right one for my device...

> **chili555 said:**
> Also see if there are any interesting messages in:```
dmesg | grep -i r6040
```

Output of this command would be:

[17.482165] <6>r6040: RDC R6040 NAPI net driver,version 0.22 (25Mar2009)

[QUOTE=chili555:10877740]How did you install the ethernet driver? Were there any errors or warnings?[/QUOTE]

I actually didn't really install the driver. I followed the instruction in the pdf linked in my first post. The driver was included in the deb-package I updated the installation with BEFORE I put the CF card in the device. So, first I installed Ubuntu onto the CF while being connected to a normal PC. Here ethernet just worked out of the box. Then I "installed" the producer's kernel using dpkg -i xxx.deb and update-initramfs, in which the driver was included.
But the driver wasn't loaded until I added it to the /etc/modules.

Thanks for your help. I hope this gives more light in the dark ;)

Nicest thing would be, if I was able to run the board with an up-to-date kernel, which seems somehow to work, as I can also boot using the 2.6.32-24 kernel but there is noc r6040 driver included...

---

### Post by chili555 on 2011-05-29
> Seems to me like the driver is the right one for my device...Yes, indeed.> [[COLOR="Red"]17.482165[/COLOR]] <6>r6040: RDC R6040 NAPI net driver,version 0.22 (25Mar2009)The timestamp suggests that the driver is loaded during boot. It's hard to tell how soon or late because I haven't a clue how long boot-up takes on these boards. On my laptop, boot-up runs the timestamp up to about 50.00 including loading the driver and connecting my wireless. I have the impression, based on not much, that the driver is loading as a result of its listing in /etc/modules and not because it recognizes and marries the device. Here is my dmesg listing for e1000e, my ethernet device:```
[    1.099350] e1000e: Intel(R) PRO/1000 Network Driver - 1.0.2-k4
[    1.099354] e1000e: Copyright (c) 1999 - 2009 Intel Corporation.
[    1.099387] e1000e 0000:02:00.0: Disabling ASPM  L1
[    1.099413] e1000e 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.099440] e1000e 0000:02:00.0: setting latency timer to 64
[    1.099665] e1000e 0000:02:00.0: irq 45 for MSI/MSI-X
[    1.100161] e1000e 0000:02:00.0: Disabling ASPM L0s 
[    1.230169] e1000e 0000:02:00.0: eth0: (PCI Express:2.5GB/s:Width x1) 00:16:41:e6:cb:ef
[    1.230174] e1000e 0000:02:00.0: eth0: Intel(R) PRO/1000 Network Connection
[    1.230313] e1000e 0000:02:00.0: eth0: MAC: 2, PHY: 2, PBA No: 005301-003
```The timestamp is earlier and the detail is greater. Notice the driver is associated with a bus number, 02:00.0. Your r6040 is not. Your driver ought to associate with [COLOR="Red"]00:08.0[/COLOR]:> 00:08.0 Ethernet Controller: RDC Semiconductor, Inc. R6040 MAC ControllerI suggest you look in syslog and syslog.1 for all these details:```
sudo cat /var/log/syslog | grep -i r6040
sudo cat /var/log/syslog | grep 08.0
sudo cat /var/log/syslog | grep -i ether
```I'm really not too sure where to go from here. Does the board have a BIOS or equivalent? Can ethernet be enabled or disabled in it?

---

### Post by signpainter on 2011-05-30
I finally got it working :)

I looked at the boot messages again and found the following line:

```
[   18.748389] udev: renamed network interface eth0 to eth1
```All I did then, was editing /etc/network/interfaces and replacing eth0 by eth1 and it worked. I could even remove the r6040 entry from /etc/modules. Should read more careful... 

@chili5555: Thanks alot!

---

### Post by chili555 on 2011-05-30
Excellent! Glad it's working.

---

### Post by pallab on 2011-06-18
I have loaded ubuntu 10.04 image on PCM-9343 (advatech board, vortex86dx cpu). The ubutu image is as provided by advantech. Everything is fine, but firefox crashes before it could open. After clicking the firefox icon, in the task bar it shows "starting firefox..." but disappears immediately......nothing opens up...some times an window comes telling " Mozilla has crashed ..." etc..Kindly help me to sove the Firefox issue.....
 
Thanks,
Pallab.

---

### Post by chili555 on 2011-06-18
> **pallab said:**
> I have loaded ubuntu 10.04 image on PCM-9343 (advatech board, vortex86dx cpu). The ubutu image is as provided by advantech. Everything is fine, but firefox crashes before it could open. After clicking the firefox icon, in the task bar it shows "starting firefox..." but disappears immediately......nothing opens up...some times an window comes telling " Mozilla has crashed ..." etc..Kindly help me to sove the Firefox issue.....
 
Thanks,
Pallab.You would probably have better luck in General Help.

[http://ubuntuforums.org/forumdisplay.php?f=331](http://ubuntuforums.org/forumdisplay.php?f=331)

---

