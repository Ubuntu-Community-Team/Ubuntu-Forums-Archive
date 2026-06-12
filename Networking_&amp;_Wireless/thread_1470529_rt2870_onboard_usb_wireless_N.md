---
title: "rt2870 onboard usb wireless N"
date: 2010-05-02
forum: Networking &amp; Wireless
---

### Post by Cue2 on 2010-05-02
Can somebody please help me troubleshoot my network problems in ubuntu 10.04, I'm so close I can almost taste it.

what I have done so far. I had conflicting modules so I blacklisted the following

```

blacklist rt2x00usb
blacklist rt2x00lib
blacklist rt2800usb
```

now only one of them loads
```

$ lsmod | grep rt
rt2870sta
```

i tried to connect to my router but it keeps asking for the wpa key over and over
I tried to see if my driver is there

```
$ lshw -C network
discription: wireless interface
physical id: 1
capabilities: ethernet physical wireless
configuration: broadcast=yes multicast=yes wireless=RTxx70

```
 
what does wireless=RTxx70 mean, does this mean the driver is working? because it doesn't seem to say driver=rt2870

the output of nm-tool only shows "usb" as the driver.
```

$ nm-tool
- Device: wlan0 -----------
type: 802.11 wifi
driver: usb
state: disconnected
default: no

Capabilities:

wireless properties
 wep: yes
 wpa: yes
 wpa2: yes
```


some more info which may be useful
```

lsusb -v
Bus 001 Device 002: ID 0b05:1742 ASUSTek Computer, Inc. 802.11n Network Adaptor
```

I tried to use the commands below hoping it will solve my driver problems
```

echo 'install rt2870sta modprobe --ignore-install rt2870sta ; /bin/echo "0b05 1742 " > /sys/bus/usb/drivers/rt2870/new_id' | sudo tee /etc/modprobe.d/rt2870sta.conf
sudo modprobe -rf rt2870sta
sudo modprobe rt2870sta
dmesg | egrep 'rt28|usb|Phy'
iwconfig
```

but sudo modprobe -rf rt2870sta does not work because it's in use

any suggestions because I have no idea? has my driver installed properly? if so why does it keep asking for a wpa key?

---

### Post by Cue2 on 2010-05-03
I solved it. I have an ASUS P5E3 premium with onboard (usb) wireless n but it should work for anybody else having trouble using the same chipset. If you have a problem where it keeps asking for the WPA key over and over again even after solving the driver conflict you need to build your own rt2870sta module.


_**Resolving the Driver conflict**_

First check if there is a driver conflict by doing this

```

lsmod | grep rt

```

if you see all of these:
```

rt2x00usb
rt2x00lib
rt2800usb

rt2870sta
```

in the output, you have a conflict and you need to blacklist some modules

do
```
gksudo gedit /etc/modprobe.d/blacklist.conf
```

and add this:
```
# Wifi Drivers conflict with rt2870sta
blacklist rt2x00usb
blacklist rt2x00lib
blacklist rt2800usb

```
to the bottom of the file that opens, then save and close gedit.


_**Build your own (newer) rt2870sta**_

Make sure you have build-essentials

either with an alternative internet connection with:
```

sudo apt-get install build-essential
```

OR from the UBUNTU cd
```
apt-cdrom add-d / cdrom 
apt-get update.
apt-get install build-essential.
```


download the latest rt2870USB(RT2870/RT2770) file from their website
[http://www.ralinktech.com/support.php?s=2](http://www.ralinktech.com/support.php?s=2)

extract the files somewhere

in a terminal go to the directory which you just extracted
e.g.
```

cd /home/user/Downloads/RT2870_LinuxSTA_V2.3.0.0

```

do 
```
gedit Makefile
```

and make sure these are set
```
RT28xx_MODE = STA
TARGET = LINUX
```

if so, close gedit making sure to save if you had to change them.

check config.mk
```

gedit ./os/linux/config.mk
```
make sure these are set correctly 

```
HAS_WPA_SUPPLICANT = y
HAS_NATIVE_WPA_SUPPLICANT_SUPPORT = y
```

if so, back at the terminal do:

```
sudo ifconfig wlan0 down
```
where you replace "wlan0" with the name of your wireless interface

unload the module
```
sudo modprobe -rf rt2870sta

```

do:
```

make
sudo make install

```

now overwrite the rt2870sta module

```
sudo cp ./os/linux/rt2870sta.ko /lib/modules/ <your kernel> (e.g. 2.6.32-21-generic)/kernel/drivers/staging/rt2870/rt2870sta.ko
```

restart the computer and your wireless n should now work.

Hope this helps

PS:Can somebody advise me on a better way of loading the alternative module at startup instead of replacing the default kernel one? since a kernel update will overwrite it with the default again.

---

### Post by ErkSmeijer on 2010-05-04
Thanks Cue2, for this excellent post. :cool:

It took my Ralink2870usb  from a 54g connection to a full 270Mb/s n connection.

You might want to change two details for the benefit of future readers:

```
sudo apt-get install build-essential(s) remove (s) 
```and

```
(added sudo) sudo cp ./os/linux/rt2870sta.ko /lib/modules/ <your kernel> (e.g. 2.6.32-21-generic)/kernel/drivers/staging/rt2870/rt2870sta.ko 
```Just minor details that should be obvious, but maybe not to all.

Erik.

---

### Post by loray on 2010-05-04
I tried this solution, but when complied with make returns

WARNING: modpost: missing MODULE_LICENSE() in /home/fer/temp/DPO_RT3070_LinuxSTA_V2.3.0.2_20100412/os/linux/rt3070sta.o
see include/linux/module.h for more information
  LD [M]  /home/fer/temp/DPO_RT3070_LinuxSTA_V2.3.0.2_20100412/os/linux/rt3070sta.ko
make[1]: Saindo do diretório `/usr/src/linux-headers-2.6.32-22-generic'
cp -f /home/fer/temp/DPO_RT3070_LinuxSTA_V2.3.0.2_20100412/os/linux/rt3070sta.ko /tftpboot
cp: não foi possível remover `/tftpboot': Permissão negada
make: ** [LINUX] Erro 1

What I did wrong?

---

### Post by loray on 2010-05-04
> **loray said:**
> I tried this solution, but when complied with make returns

WARNING: modpost: missing MODULE_LICENSE() in /home/fer/temp/DPO_RT3070_LinuxSTA_V2.3.0.2_20100412/os/linux/rt3070sta.o
see include/linux/module.h for more information
  LD [M]  /home/fer/temp/DPO_RT3070_LinuxSTA_V2.3.0.2_20100412/os/linux/rt3070sta.ko
make[1]: Saindo do diretório `/usr/src/linux-headers-2.6.32-22-generic'
cp -f /home/fer/temp/DPO_RT3070_LinuxSTA_V2.3.0.2_20100412/os/linux/rt3070sta.ko /tftpboot
cp: não foi possível remover `/tftpboot': Permissão negada
make: ** [LINUX] Erro 1

What I did wrong?

I was using the wrong driver, now It works. I restarted the computer, but now the connection keeping asking for my secret key, althoug it&#347; right

---

### Post by Cue2 on 2010-05-04
Thanks Erik, I've edited it now.


Loray

from within the extracted directory try

```
sudo cp RT2870STA.dat /etc/Wireless/RT2870STA/RT2870STA.dat
```

restart your computer. If it still doesn't work can you tell me what the output of the following commands are.

```
lshw -C network
```

```
iwconfig
```

```
modinfo rt2870sta
```

```
lsusb
```

---

### Post by loray on 2010-05-04
> **Cue2 said:**
> Thanks Erik, I've edited it now.


Loray

from within the extracted directory try

```
sudo cp RT2870STA.dat /etc/Wireless/RT2870STA/RT2870STA.dat
```

restart your computer. If it still doesn't work can you tell me what the output of the following commands are.

```
lshw -C network
```

```
iwconfig
```

```
modinfo rt2870sta
```

```
lsusb
```

It work&#347;, great, now I have a N connection.:D  Thanks Cue2.

---

### Post by Jedster on 2010-05-31
Help,
I'm having similar problems.
At first I was getting a  network connection some of the time in that the joggler would never  connect on power up and would eventually prompt me for my network keys  which it then took a while to reject or accept.Or I could select my  network from the network manager and again it would sometimes accept  this or sometimes eventually reject this.
Interestingly enough, if I  selected my neibours network it rejected that immediately.

I  tried the suggestion above, but now I can't get a network connection at  all. :(
(Not the end of the world, I have a backup of the USB stick).




My  output from the mentioned commands is as follows 

Any help in  getting a consistently working network (which ideally automatically  connects on boot) much appreciated.

Many thanks,
Jedster



joggler@joggletop:~$  lshw -C network
WARNING: you should run this program as super-user.
   *-network DISABLED      
       description: Ethernet interface
        product: RTL8111/8168B PCI Express Gigabit Ethernet controller
        vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
        bus info: pci@0000:01:00.0
       logical name: eth4
        version: 02
       serial: 35:35:35:73:15:35
       width: 64 bits
        clock: 33MHz
       capabilities: bus_master cap_list rom ethernet  physical
       configuration: broadcast=yes driver=r8169  driverversion=2.3LK-NAPI latency=0 multicast=yes
       resources:  irq:24 ioport:e000(size=256) memory:fef10000-fef10fff(prefetchable)  memory:fef00000-fef0ffff(prefetchable)  memory:d0000000-d000ffff(prefetchable)
  *-network
        description: Wireless interface
       physical id: 2
        logical name: ra0
       serial: 00:0e:8e:24:c1:74
        capabilities: ethernet physical wireless
       configuration:  broadcast=yes driver=RALINK WLAN driverversion=2.3.0.0 multicast=yes  wireless=Ralink STA





joggler@joggletop:~$ iwconfig
lo         no wireless extensions.

eth4      no wireless extensions.

ra0        Ralink STA  ESSID:"11n-AP"  Nickname:"RT2870STA"
           Mode:Auto  Frequency=2.412 GHz  Access Point: Not-Associated   
           Bit Rate:1 Mb/s   
          RTS thr:off   Fragment thr:off
           Link Quality=10/100  Signal level:0 dBm  Noise level:-87 dBm
           Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
           Tx excessive retries:0  Invalid misc:0   Missed beacon:0





joggler@joggletop:~$  modinfo rt2870sta
filename:        /lib/modules/2.6.31-20-generic/kernel/drivers/staging/rt2870/rt2870sta.ko
version:         2.3.0.0
license:        GPL
description:    RT2870 Wireless Lan  Linux Driver
author:         Paul Lin <paul_lin@ralinktech.com>
srcversion:      BFE72125F5BC16053AC2BDE
alias:           usb:v0DB0p6899d*dc*dsc*dp*ic*isc*ip*
alias:           usb:v100Dp9031d*dc*dsc*dp*ic*isc*ip*
alias:           usb:v050Dp815Cd*dc*dsc*dp*ic*isc*ip*
alias:           usb:v0411p00E8d*dc*dsc*dp*ic*isc*ip*
alias:           usb:v1737p0071d*dc*dsc*dp*ic*isc*ip*
alias:           usb:v1737p0070d*dc*dsc*dp*ic*isc*ip*
alias:           usb:v7392p7717d*dc*dsc*dp*ic*isc*ip*
alias:           usb:v7392p7718d*dc*dsc*dp*ic*isc*ip*
alias:           usb:v5A57p0282d*dc*dsc*dp*ic*isc*ip*
alias:           usb:v5A57p0280d*dc*dsc*dp*ic*isc*ip*
alias:           usb:v1690p0740d*dc*dsc*dp*ic*isc*ip*
alias:           usb:v04E8p2018d*dc*dsc*dp*ic*isc*ip*
alias:           usb:v14B2p3C09d*dc*dsc*dp*ic*isc*ip*
alias:           usb:v1482p3C09d*dc*dsc*dp*ic*isc*ip*
alias:           usb:v050Dp815Cd*dc*dsc*dp*ic*isc*ip*
alias:           usb:v050Dp805Cd*dc*dsc*dp*ic*isc*ip*
alias:           usb:v157Ep300Ed*dc*dsc*dp*ic*isc*ip*
alias:           usb:v129Bp1828d*dc*dsc*dp*ic*isc*ip*
alias:           usb:v0E66p0003d*dc*dsc*dp*ic*isc*ip*
alias:           usb:v0E66p0001d*dc*dsc*dp*ic*isc*ip*
alias:           usb:v15C5p0008d*dc*dsc*dp*ic*isc*ip*
alias:           usb:v083Ap6618d*dc*dsc*dp*ic*isc*ip*
alias:           usb:v13D3p3247d*dc*dsc*dp*ic*isc*ip*
alias:           usb:v14B2p3C25d*dc*dsc*dp*ic*isc*ip*
alias:           usb:v0471p200Fd*dc*dsc*dp*ic*isc*ip*
alias:           usb:v1740p9702d*dc*dsc*dp*ic*isc*ip*
alias:           usb:v1740p9701d*dc*dsc*dp*ic*isc*ip*
alias:           usb:v0CDEp0025d*dc*dsc*dp*ic*isc*ip*
alias:           usb:v0586p3416d*dc*dsc*dp*ic*isc*ip*
alias:           usb:v0CDEp0022d*dc*dsc*dp*ic*isc*ip*
alias:           usb:v083Ap7522d*dc*dsc*dp*ic*isc*ip*
alias:           usb:v083Ap8522d*dc*dsc*dp*ic*isc*ip*
alias:           usb:v083ApA618d*dc*dsc*dp*ic*isc*ip*
alias:           usb:v083ApB522d*dc*dsc*dp*ic*isc*ip*
alias:           usb:v15A9p0006d*dc*dsc*dp*ic*isc*ip*
alias:           usb:v1044p800Bd*dc*dsc*dp*ic*isc*ip*
alias:           usb:v07AAp003Fd*dc*dsc*dp*ic*isc*ip*
alias:           usb:v07AAp003Cd*dc*dsc*dp*ic*isc*ip*
alias:           usb:v07AAp002Fd*dc*dsc*dp*ic*isc*ip*
alias:           usb:v14B2p3C27d*dc*dsc*dp*ic*isc*ip*
alias:           usb:v14B2p3C23d*dc*dsc*dp*ic*isc*ip*
alias:           usb:v050Dp8053d*dc*dsc*dp*ic*isc*ip*
alias:           usb:v14B2p3C07d*dc*dsc*dp*ic*isc*ip*
alias:           usb:v07D1p3C11d*dc*dsc*dp*ic*isc*ip*
alias:           usb:v07D1p3C09d*dc*dsc*dp*ic*isc*ip*
alias:           usb:v2019pED06d*dc*dsc*dp*ic*isc*ip*
alias:           usb:v14B2p3C28d*dc*dsc*dp*ic*isc*ip*
alias:           usb:v14B2p3C06d*dc*dsc*dp*ic*isc*ip*
alias:           usb:v0DF6p002Dd*dc*dsc*dp*ic*isc*ip*
alias:           usb:v0DF6p002Cd*dc*dsc*dp*ic*isc*ip*
alias:           usb:v0DF6p002Bd*dc*dsc*dp*ic*isc*ip*
alias:           usb:v0DF6p0017d*dc*dsc*dp*ic*isc*ip*
alias:           usb:v0B05p1742d*dc*dsc*dp*ic*isc*ip*
alias:           usb:v0B05p1732d*dc*dsc*dp*ic*isc*ip*
alias:           usb:v0B05p1731d*dc*dsc*dp*ic*isc*ip*
alias:           usb:v177Fp0302d*dc*dsc*dp*ic*isc*ip*
alias:           usb:v0789p0164d*dc*dsc*dp*ic*isc*ip*
alias:           usb:v0789p0163d*dc*dsc*dp*ic*isc*ip*
alias:           usb:v0789p0162d*dc*dsc*dp*ic*isc*ip*
alias:           usb:v083Ap7512d*dc*dsc*dp*ic*isc*ip*
alias:           usb:v0DF6p003Fd*dc*dsc*dp*ic*isc*ip*
alias:           usb:v0DF6p0039d*dc*dsc*dp*ic*isc*ip*
alias:           usb:v07B8p2770d*dc*dsc*dp*ic*isc*ip*
alias:           usb:v07B8p2870d*dc*dsc*dp*ic*isc*ip*
alias:           usb:v148Fp2870d*dc*dsc*dp*ic*isc*ip*
alias:           usb:v148Fp2770d*dc*dsc*dp*ic*isc*ip*
depends:        
vermagic:        2.6.31-20-generic SMP mod_unload modversions 586 
parm:            mac:rt28xx: wireless mac addr (charp)






joggler@joggletop:~$  lsusb
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus  004 Device 002: ID 04b4:1974 Cypress Semiconductor Corp. 
Bus 004  Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device  007: ID 1307:0165 Transcend Information, Inc. 2GB/4GB Flash Drive
Bus  001 Device 006: ID 0e6a:6001 Megawin Technology Co., Ltd 
Bus 001  Device 005: ID 0f62:1001 Acrox Technologies Co., Ltd Targus Mini  Trackball Optical Mouse
Bus 001 Device 002: ID 05e3:0606 Genesys  Logic, Inc. USB 2.0 Hub / D-Link DUB-H4 USB 2.0 Hub
Bus 001 Device  003: ID 148f:2770 Ralink Technology, Corp. 
Bus 001 Device 001: ID  1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID  1d6b:0001 Linux Foundation 1.1 root hub
joggler@joggletop:~$

---

### Post by Talon2 on 2010-05-31
Feel free to jump on this bug:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/549801](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/549801)

Maybe the more attention this bug gets, the sooner we'll get someone to sort this out.

---

### Post by Jedster on 2010-05-31
I'm not convinced that's my problem (although I may be wrong).
Firstly I'm at 9.10 and secondly I've already got those devices blacklisted.

Thanks,
Jedster.

---

### Post by Jedster on 2010-06-03
I think I've found a workable solution to this. 
Forget Network  Manager  and use WICD!!
I haven't got it auto connecting yet  (probably because my SSID is currently hidden), but once I tell it to go  find my hidden SSID it usually finds it and then I'm able to connect to  it.

That'll do for now.

:)

Jedster

---

### Post by nevixa on 2011-06-28
Hello,

Sorry for bumping up an one year old thread, but I have an problem with my onboard usb wireless n from Asus.

Thank you for the guide Cue2, but I can't build the downloaded drivers.
When I make the driver I get this:

```
make -C tools
make[1]: Entering directory `/home/diip/Downloads/newwifi/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/diip/Downloads/newwifi/tools'
/home/diip/Downloads/newwifi/tools/bin2h
cp -f os/linux/Makefile.6 /home/diip/Downloads/newwifi/os/linux/Makefile
make -C /lib/modules/2.6.35-28-generic/build SUBDIRS=/home/diip/Downloads/newwifi/os/linux modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.35-28-generic'
  CC [M]  /home/diip/Downloads/newwifi/os/linux/../../common/cmm_mac_usb.o
/home/diip/Downloads/newwifi/os/linux/../../common/cmm_mac_usb.c: In function &#8216;RTMPAllocUsbBulkBufStruct&#8217;:
/home/diip/Downloads/newwifi/os/linux/../../common/cmm_mac_usb.c:52: error: implicit declaration of function &#8216;usb_buffer_alloc&#8217;
/home/diip/Downloads/newwifi/os/linux/../../common/cmm_mac_usb.c:52: warning: assignment makes pointer from integer without a cast
/home/diip/Downloads/newwifi/os/linux/../../common/cmm_mac_usb.c: In function &#8216;RTMPFreeUsbBulkBufStruct&#8217;:
/home/diip/Downloads/newwifi/os/linux/../../common/cmm_mac_usb.c:78: error: implicit declaration of function &#8216;usb_buffer_free&#8217;
/home/diip/Downloads/newwifi/os/linux/../../common/cmm_mac_usb.c: In function &#8216;RTMPFreeTxRxRingMemory&#8217;:
/home/diip/Downloads/newwifi/os/linux/../../common/cmm_mac_usb.c:234: warning: passing argument 3 of &#8216;RTMPFreeUsbBulkBufStruct&#8217; from incompatible pointer type
/home/diip/Downloads/newwifi/os/linux/../../common/cmm_mac_usb.c:62: note: expected &#8216;UCHAR **&#8217; but argument is of type &#8216;struct __TX_BUFFER **&#8217;
/home/diip/Downloads/newwifi/os/linux/../../common/cmm_mac_usb.c:241: warning: passing argument 3 of &#8216;RTMPFreeUsbBulkBufStruct&#8217; from incompatible pointer type
/home/diip/Downloads/newwifi/os/linux/../../common/cmm_mac_usb.c:62: note: expected &#8216;UCHAR **&#8217; but argument is of type &#8216;struct __TX_BUFFER **&#8217;
/home/diip/Downloads/newwifi/os/linux/../../common/cmm_mac_usb.c:278: warning: passing argument 3 of &#8216;RTMPFreeUsbBulkBufStruct&#8217; from incompatible pointer type
/home/diip/Downloads/newwifi/os/linux/../../common/cmm_mac_usb.c:62: note: expected &#8216;UCHAR **&#8217; but argument is of type &#8216;struct __HTTX_BUFFER **&#8217;
/home/diip/Downloads/newwifi/os/linux/../../common/cmm_mac_usb.c: In function &#8216;NICInitTransmit&#8217;:
/home/diip/Downloads/newwifi/os/linux/../../common/cmm_mac_usb.c:507: warning: passing argument 3 of &#8216;RTMPFreeUsbBulkBufStruct&#8217; from incompatible pointer type
/home/diip/Downloads/newwifi/os/linux/../../common/cmm_mac_usb.c:62: note: expected &#8216;UCHAR **&#8217; but argument is of type &#8216;struct __TX_BUFFER **&#8217;
/home/diip/Downloads/newwifi/os/linux/../../common/cmm_mac_usb.c: In function &#8216;RTMPAllocTxRxRingMemory&#8217;:
/home/diip/Downloads/newwifi/os/linux/../../common/cmm_mac_usb.c:566: warning: passing argument 3 of &#8216;RTMPAllocUsbBulkBufStruct&#8217; from incompatible pointer type
/home/diip/Downloads/newwifi/os/linux/../../common/cmm_mac_usb.c:34: note: expected &#8216;VOID **&#8217; but argument is of type &#8216;struct __HTTX_BUFFER **&#8217;
/home/diip/Downloads/newwifi/os/linux/../../common/cmm_mac_usb.c:596: warning: passing argument 3 of &#8216;RTMPAllocUsbBulkBufStruct&#8217; from incompatible pointer type
/home/diip/Downloads/newwifi/os/linux/../../common/cmm_mac_usb.c:34: note: expected &#8216;VOID **&#8217; but argument is of type &#8216;struct __TX_BUFFER **&#8217;
/home/diip/Downloads/newwifi/os/linux/../../common/cmm_mac_usb.c:610: warning: passing argument 3 of &#8216;RTMPAllocUsbBulkBufStruct&#8217; from incompatible pointer type
/home/diip/Downloads/newwifi/os/linux/../../common/cmm_mac_usb.c:34: note: expected &#8216;VOID **&#8217; but argument is of type &#8216;struct __TX_BUFFER **&#8217;
/home/diip/Downloads/newwifi/os/linux/../../common/cmm_mac_usb.c:628: warning: passing argument 3 of &#8216;RTMPAllocUsbBulkBufStruct&#8217; from incompatible pointer type
/home/diip/Downloads/newwifi/os/linux/../../common/cmm_mac_usb.c:34: note: expected &#8216;VOID **&#8217; but argument is of type &#8216;UCHAR **&#8217;
make[2]: *** [/home/diip/Downloads/newwifi/os/linux/../../common/cmm_mac_usb.o] Error 1
make[1]: *** [_module_/home/diip/Downloads/newwifi/os/linux] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-28-generic'
make: *** [LINUX] Error 2

```Any ideas how to get this driver to build?

Thank you!

---

### Post by nevixa on 2011-06-28
The build issue is solved by here:
[http://ubuntuforums.org/archive/index.php/t-1671799.html](http://ubuntuforums.org/archive/index.php/t-1671799.html)

But it is still not working. 
Here is some additional information:
```

lshw -C network:
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 03
       serial: bc:ae:c5:2a:79:93
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list rom ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI ip=10.56.162.97 latency=0 multicast=yes
       resources: irq:43 ioport:e800(size=256) memory:fafff000-faffffff memory:faff8000-faffbfff memory:feaf0000-feafffff

iwconfig:
lo        no wireless extensions.

eth0      no wireless extensions.

modinfo rt2870sta:
filename:       /lib/modules/2.6.35-28-generic/kernel/net/wireless/rt2870sta.ko
version:        2.4.0.0
license:        GPL
description:    RT2870 Wireless Lan Linux Driver
author:         Paul Lin <paul_lin@ralinktech.com>
srcversion:     5598BFE60F8B720D8D64062
alias:          usb:v0DB0p6899d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v100Dp9031d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp815Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0411p00E8d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1737p0071d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1737p0070d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v7392p7717d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v7392p7718d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v5A57p0282d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v5A57p0280d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1690p0740d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v04E8p2018d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C09d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1482p3C09d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp815Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp805Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v157Ep300Ed*dc*dsc*dp*ic*isc*ip*
alias:          usb:v129Bp1828d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0E66p0003d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0E66p0001d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v15C5p0008d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083Ap6618d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3247d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C25d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0471p200Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p9702d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p9701d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0CDEp0025d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0586p3416d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0CDEp0022d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083Ap7522d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083Ap8522d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083ApA618d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083ApB522d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v15A9p0006d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1044p800Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07AAp003Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07AAp003Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07AAp002Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C27d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C23d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp8053d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C07d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C11d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C09d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2019pED06d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C28d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C06d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p002Dd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p002Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p002Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0017d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0B05p1742d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0B05p1732d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0B05p1731d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v177Fp0302d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0789p0164d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0789p0163d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0789p0162d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083Ap7512d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p003Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0039d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8p2770d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8p2870d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp2870d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp2770d*dc*dsc*dp*ic*isc*ip*
depends:        
vermagic:       2.6.32-31-generic SMP mod_unload modversions 586 
parm:           mac:rt28xx: wireless mac addr (charp)

lsusb:
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 0cf3:3002 Atheros Communications, Inc. 
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 004: ID 04d8:fe88 Microchip Technology, Inc. 
Bus 004 Device 003: ID 05d5:6782 Super Gate Technology Co., Ltd 
Bus 004 Device 002: ID 046d:c043 Logitech, Inc. MX320/MX400 Laser Mouse
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 0b05:1742 ASUSTek Computer, Inc. 802.11n Network Adapter
Bus 002 Device 002: ID 045e:075d Microsoft Corp. LifeCam Cinema
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 045e:075d Microsoft Corp. LifeCam Cinema
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

Anyone any idea how to get wifi working?

---

### Post by chili555 on 2011-06-28
> Anyone any idea how to get wifi working?Are there any errors or warnings when you load the module?```
sudo modprobe rt2870sta
```Any interesting messages here?```
dmesg | grep -i rt2
```Thanks.

---

### Post by nevixa on 2011-06-28
Thank you for your quick reply.

I got this:
```

 sudo modprobe rt2870sta

WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
FATAL: Error inserting rt2870sta (/lib/modules/2.6.35-28-generic/kernel/net/wireless/rt2870sta.ko): Invalid module format

dmesg | grep -i rt2
[   12.922839] rt2870sta: disagrees about version of symbol module_layout
[ 1840.406819] rt2870sta: disagrees about version of symbol module_layout

```

---

### Post by chili555 on 2011-06-28
> **nevixa said:**
> Thank you for your quick reply.

I got this:
```

 sudo modprobe rt2870sta

WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
FATAL: Error inserting rt2870sta (/lib/modules/2.6.35-28-generic/kernel/net/wireless/rt2870sta.ko): Invalid module format

dmesg | grep -i rt2
[   12.922839] rt2870sta: disagrees about version of symbol module_layout
[ 1840.406819] rt2870sta: disagrees about version of symbol module_layout

```Evidently, there were too many warnings in your compile. I noticed you built version 2.4.0.0. In the link you provided, the poster says:> I've uploaded a pre-modified version of the driver that WILL compile on kernels >= 2.6.35 here:
2010_0709_RT2870_Linux_STA_v[COLOR="Red"]2.4.0.1[/COLOR].tar.bz2 ([http://bit.ly/eZHx0J](http://bit.ly/eZHx0J))I suggest you try that.

---

### Post by nevixa on 2011-06-28
I think I already did that. That was what helped me past the 'make/build' issue from my first post. Or maybe I just completely misunderstood your previous post.

My make of 2.4.0.1 below:
```

make -C tools
make[1]: Entering directory `/home/diip/Downloads/newwifi2/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/diip/Downloads/newwifi2/tools'
/home/diip/Downloads/newwifi2/tools/bin2h
cp -f os/linux/Makefile.6 /home/diip/Downloads/newwifi2/os/linux/Makefile
make -C /lib/modules/2.6.35-28-generic/build SUBDIRS=/home/diip/Downloads/newwifi2/os/linux modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.35-28-generic'
  CC [M]  /home/diip/Downloads/newwifi2/os/linux/../../common/crypt_md5.o
  CC [M]  /home/diip/Downloads/newwifi2/os/linux/../../common/crypt_sha2.o
  CC [M]  /home/diip/Downloads/newwifi2/os/linux/../../common/crypt_hmac.o
  CC [M]  /home/diip/Downloads/newwifi2/os/linux/../../common/crypt_aes.o
/home/diip/Downloads/newwifi2/os/linux/../../common/crypt_aes.c: In function ‘AES_GTK_KEY_WRAP’:
/home/diip/Downloads/newwifi2/os/linux/../../common/crypt_aes.c:2265: warning: the frame size of 1100 bytes is larger than 1024 bytes
/home/diip/Downloads/newwifi2/os/linux/../../common/crypt_aes.c: In function ‘WscDecryptData’:
/home/diip/Downloads/newwifi2/os/linux/../../common/crypt_aes.c:1592: warning: the frame size of 1356 bytes is larger than 1024 bytes
/home/diip/Downloads/newwifi2/os/linux/../../common/crypt_aes.c: In function ‘WscEncryptData’:
/home/diip/Downloads/newwifi2/os/linux/../../common/crypt_aes.c:1522: warning: the frame size of 1356 bytes is larger than 1024 bytes
  CC [M]  /home/diip/Downloads/newwifi2/os/linux/../../common/crypt_arc4.o
  CC [M]  /home/diip/Downloads/newwifi2/os/linux/../../common/mlme.o
/home/diip/Downloads/newwifi2/os/linux/../../common/mlme.c: In function ‘BssTableSortByRssi’:
/home/diip/Downloads/newwifi2/os/linux/../../common/mlme.c:6100: warning: the frame size of 1720 bytes is larger than 1024 bytes
  CC [M]  /home/diip/Downloads/newwifi2/os/linux/../../common/cmm_wep.o
  CC [M]  /home/diip/Downloads/newwifi2/os/linux/../../common/action.o
  CC [M]  /home/diip/Downloads/newwifi2/os/linux/../../common/cmm_data.o
  CC [M]  /home/diip/Downloads/newwifi2/os/linux/../../common/rtmp_init.o
  CC [M]  /home/diip/Downloads/newwifi2/os/linux/../../common/cmm_tkip.o
  CC [M]  /home/diip/Downloads/newwifi2/os/linux/../../common/cmm_aes.o
  CC [M]  /home/diip/Downloads/newwifi2/os/linux/../../common/cmm_sync.o
  CC [M]  /home/diip/Downloads/newwifi2/os/linux/../../common/eeprom.o
  CC [M]  /home/diip/Downloads/newwifi2/os/linux/../../common/cmm_sanity.o
  CC [M]  /home/diip/Downloads/newwifi2/os/linux/../../common/cmm_info.o
  CC [M]  /home/diip/Downloads/newwifi2/os/linux/../../common/cmm_cfg.o
  CC [M]  /home/diip/Downloads/newwifi2/os/linux/../../common/cmm_wpa.o
  CC [M]  /home/diip/Downloads/newwifi2/os/linux/../../common/dfs.o
  CC [M]  /home/diip/Downloads/newwifi2/os/linux/../../common/spectrum.o
  CC [M]  /home/diip/Downloads/newwifi2/os/linux/../../common/rtmp_timer.o
  CC [M]  /home/diip/Downloads/newwifi2/os/linux/../../common/rt_channel.o
  CC [M]  /home/diip/Downloads/newwifi2/os/linux/../../common/cmm_profile.o
  CC [M]  /home/diip/Downloads/newwifi2/os/linux/../../common/cmm_asic.o
  CC [M]  /home/diip/Downloads/newwifi2/os/linux/../../common/cmm_cmd.o
  CC [M]  /home/diip/Downloads/newwifi2/os/linux/../../sta/assoc.o
  CC [M]  /home/diip/Downloads/newwifi2/os/linux/../../sta/auth.o
  CC [M]  /home/diip/Downloads/newwifi2/os/linux/../../sta/auth_rsp.o
  CC [M]  /home/diip/Downloads/newwifi2/os/linux/../../sta/sync.o
/home/diip/Downloads/newwifi2/os/linux/../../sta/sync.c: In function ‘PeerBeacon’:
/home/diip/Downloads/newwifi2/os/linux/../../sta/sync.c:1764: warning: the frame size of 1308 bytes is larger than 1024 bytes
/home/diip/Downloads/newwifi2/os/linux/../../sta/sync.c: In function ‘PeerBeaconAtJoinAction’:
/home/diip/Downloads/newwifi2/os/linux/../../sta/sync.c:1094: warning: the frame size of 1296 bytes is larger than 1024 bytes
/home/diip/Downloads/newwifi2/os/linux/../../sta/sync.c: In function ‘PeerBeaconAtScanAction’:
/home/diip/Downloads/newwifi2/os/linux/../../sta/sync.c:764: warning: the frame size of 1264 bytes is larger than 1024 bytes
/home/diip/Downloads/newwifi2/os/linux/../../sta/sync.c: In function ‘MlmeStartReqAction’:
/home/diip/Downloads/newwifi2/os/linux/../../sta/sync.c:581: warning: the frame size of 1064 bytes is larger than 1024 bytes
  CC [M]  /home/diip/Downloads/newwifi2/os/linux/../../sta/sanity.o
  CC [M]  /home/diip/Downloads/newwifi2/os/linux/../../sta/rtmp_data.o
  CC [M]  /home/diip/Downloads/newwifi2/os/linux/../../sta/connect.o
/home/diip/Downloads/newwifi2/os/linux/../../sta/connect.c: In function ‘CntlOidScanProc’:
/home/diip/Downloads/newwifi2/os/linux/../../sta/connect.c:355: warning: the frame size of 1748 bytes is larger than 1024 bytes
  CC [M]  /home/diip/Downloads/newwifi2/os/linux/../../sta/wpa.o
  CC [M]  /home/diip/Downloads/newwifi2/os/linux/../../sta/ags.o
  CC [M]  /home/diip/Downloads/newwifi2/os/linux/../../sta/sta_cfg.o
  CC [M]  /home/diip/Downloads/newwifi2/os/linux/../../common/rtmp_init_inf.o
  CC [M]  /home/diip/Downloads/newwifi2/os/linux/../../common/ba_action.o
  CC [M]  /home/diip/Downloads/newwifi2/os/linux/../../common/cmm_mac_usb.o
/home/diip/Downloads/newwifi2/os/linux/../../common/cmm_mac_usb.c: In function ‘RTMPFreeTxRxRingMemory’:
/home/diip/Downloads/newwifi2/os/linux/../../common/cmm_mac_usb.c:234: warning: passing argument 3 of ‘RTMPFreeUsbBulkBufStruct’ from incompatible pointer type
/home/diip/Downloads/newwifi2/os/linux/../../common/cmm_mac_usb.c:62: note: expected ‘UCHAR **’ but argument is of type ‘struct __TX_BUFFER **’
/home/diip/Downloads/newwifi2/os/linux/../../common/cmm_mac_usb.c:241: warning: passing argument 3 of ‘RTMPFreeUsbBulkBufStruct’ from incompatible pointer type
/home/diip/Downloads/newwifi2/os/linux/../../common/cmm_mac_usb.c:62: note: expected ‘UCHAR **’ but argument is of type ‘struct __TX_BUFFER **’
/home/diip/Downloads/newwifi2/os/linux/../../common/cmm_mac_usb.c:278: warning: passing argument 3 of ‘RTMPFreeUsbBulkBufStruct’ from incompatible pointer type
/home/diip/Downloads/newwifi2/os/linux/../../common/cmm_mac_usb.c:62: note: expected ‘UCHAR **’ but argument is of type ‘struct __HTTX_BUFFER **’
/home/diip/Downloads/newwifi2/os/linux/../../common/cmm_mac_usb.c: In function ‘NICInitTransmit’:
/home/diip/Downloads/newwifi2/os/linux/../../common/cmm_mac_usb.c:507: warning: passing argument 3 of ‘RTMPFreeUsbBulkBufStruct’ from incompatible pointer type
/home/diip/Downloads/newwifi2/os/linux/../../common/cmm_mac_usb.c:62: note: expected ‘UCHAR **’ but argument is of type ‘struct __TX_BUFFER **’
/home/diip/Downloads/newwifi2/os/linux/../../common/cmm_mac_usb.c: In function ‘RTMPAllocTxRxRingMemory’:
/home/diip/Downloads/newwifi2/os/linux/../../common/cmm_mac_usb.c:566: warning: passing argument 3 of ‘RTMPAllocUsbBulkBufStruct’ from incompatible pointer type
/home/diip/Downloads/newwifi2/os/linux/../../common/cmm_mac_usb.c:34: note: expected ‘VOID **’ but argument is of type ‘struct __HTTX_BUFFER **’
/home/diip/Downloads/newwifi2/os/linux/../../common/cmm_mac_usb.c:596: warning: passing argument 3 of ‘RTMPAllocUsbBulkBufStruct’ from incompatible pointer type
/home/diip/Downloads/newwifi2/os/linux/../../common/cmm_mac_usb.c:34: note: expected ‘VOID **’ but argument is of type ‘struct __TX_BUFFER **’
/home/diip/Downloads/newwifi2/os/linux/../../common/cmm_mac_usb.c:610: warning: passing argument 3 of ‘RTMPAllocUsbBulkBufStruct’ from incompatible pointer type
/home/diip/Downloads/newwifi2/os/linux/../../common/cmm_mac_usb.c:34: note: expected ‘VOID **’ but argument is of type ‘struct __TX_BUFFER **’
/home/diip/Downloads/newwifi2/os/linux/../../common/cmm_mac_usb.c:628: warning: passing argument 3 of ‘RTMPAllocUsbBulkBufStruct’ from incompatible pointer type
/home/diip/Downloads/newwifi2/os/linux/../../common/cmm_mac_usb.c:34: note: expected ‘VOID **’ but argument is of type ‘UCHAR **’
  CC [M]  /home/diip/Downloads/newwifi2/os/linux/../../common/rtusb_io.o
  CC [M]  /home/diip/Downloads/newwifi2/os/linux/../../common/rtusb_bulk.o
  CC [M]  /home/diip/Downloads/newwifi2/os/linux/../../common/rtusb_data.o
  CC [M]  /home/diip/Downloads/newwifi2/os/linux/../../common/cmm_data_usb.o
  CC [M]  /home/diip/Downloads/newwifi2/os/linux/../../common/ee_prom.o
  CC [M]  /home/diip/Downloads/newwifi2/os/linux/../../common/rtmp_mcu.o
  CC [M]  /home/diip/Downloads/newwifi2/os/linux/../../common/rtusb_dev_id.o
  LD [M]  /home/diip/Downloads/newwifi2/os/linux/rt2870sta.o
  Building modules, stage 2.
  MODPOST 1 modules
  LD [M]  /home/diip/Downloads/newwifi2/os/linux/rt2870sta.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-28-generic'

```

---

### Post by chili555 on 2011-06-28
And your sudo make install and sudo modprobe rt2870sta? There are quite a few warnings there, but let's go forward.

---

### Post by nevixa on 2011-06-28
```

sudo make install:

make -C /home/diip/Downloads/newwifi2/os/linux -f Makefile.6 install
mkdir: cannot create directory `/etc/Wireless': File exists
make[1]: Entering directory `/home/diip/Downloads/newwifi2/os/linux'
rm -rf /etc/Wireless/RT2870STA
mkdir /etc/Wireless/RT2870STA
cp /home/diip/Downloads/newwifi2/RT2870STA.dat /etc/Wireless/RT2870STA/.
install -d /lib/modules/2.6.35-28-generic/kernel/drivers/net/wireless/
install -m 644 -c rt2870sta.ko /lib/modules/2.6.35-28-generic/kernel/drivers/net/wireless/
/sbin/depmod -a 2.6.35-28-generic
make[1]: Leaving directory `/home/diip/Downloads/newwifi2/os/linux'

sudo modprobe rt2870sta:
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
FATAL: Error inserting rt2870sta (/lib/modules/2.6.35-28-generic/kernel/net/wireless/rt2870sta.ko): Invalid module format

```

thanx!

---

### Post by chili555 on 2011-06-28
Let's remove both of the not-working compiled modules. Please do:```
cd Downloads/newwifi
sudo make uninstall
cd 
cd Downloads/newwifi2
sudo make uninstall
modinfo rt2870sta
```If the uninstall of both faulty modules has gone well, then the original underlying in-kernel driver should now be available:```
modinfo rt2870sta
```The compiled versions were installed in /lib/modules/2.6.35-28-generic/kernel/drivers[COLOR="RoyalBlue"]/net/wireless/[/COLOR].

The original is in /lib/modules/2.6.35-28-generic/kernel/drivers[COLOR="Red"]/staging/rt2870/[/COLOR]

If all has gone well, staging is now in place and we'll do some slight of hand to try to get the original to drive your device. Before we proceed, let's also make sure it loads without error or warning:```
sudo modprobe rt2870sta
```

---

### Post by nevixa on 2011-06-29
I uninstalled both driver, but apparently the first one that I installed isn't gone because modinfo gives me:
```

filename:       /lib/modules/2.6.35-28-generic/kernel/net/wireless/rt2870sta.ko
version:        2.4.0.0

```

Also after another sudo make uninstall it didn't change.
Thank you for taking time!

---

### Post by chili555 on 2011-06-29
Please run:```
sudo updatedb
locate rt2870sta.ko
```We may be able to simply delete the compiled versions, but let's make sure we know what we have before we burn down the barn.

---

### Post by nevixa on 2011-06-29
Thanx, here is the output:

```

/home/diip/Downloads/newwifi2/os/linux/.rt2870sta.ko.cmd
/home/diip/Downloads/newwifi2/os/linux/rt2870sta.ko
/home/diip/Downloads/wifi_thomas/os/linux/.rt2870sta.ko.cmd
/home/diip/Downloads/wifi_thomas/os/linux/rt2870sta.ko
/lib/modules/2.6.32-31-generic/kernel/drivers/net/wireless/rt2870sta.ko
/lib/modules/2.6.32-31-generic/kernel/drivers/staging/rt2870/rt2870sta.ko
/lib/modules/2.6.35-28-generic/kernel/drivers/staging/rt2870/rt2870sta.ko
/lib/modules/2.6.35-28-generic/kernel/net/wireless/rt2870sta.ko

```

---

### Post by nevixa on 2011-06-29
btw, I also did a sudo make uninstall in the wifi_thomas directory. but didn't help.

---

### Post by chili555 on 2011-06-29
> /lib/modules/2.6.35-28-generic/kernel/drivers/[COLOR="Red"]staging/rt2870[/COLOR]/rt2870sta.ko^^^ That is the original, in kernel version.> /lib/modules/2.6.35-28-generic/kernel/[COLOR="Red"]net/wireless[/COLOR]/rt2870sta.koAnd this one ^^^ is the compiled version. Let's simply remove the compiled version; you have the downloaded file, so you could recompile and reinstall a not-working version if you had to! Please do:```
sudo rm /lib/modules/2.6.35-28-generic/kernel/net/wireless/rt2870sta.ko
```Now run:```
modinfo rt2870sta
```Does it return the staging version? Good!

We need to double-check the usb.id for your device. Please run and post:```
lsusb
```Thanks.

---

### Post by nevixa on 2011-06-30
Ok, now it returns the staging version! Thanks!
Now I also see in the top system bar (don't know the official term, sorry) the words: Wireless Network, which I haven't seen for a long time.Below that I see: device not managed. I don't see any networks yet, but that is the next step I guess. 

lsusb returns:
```

Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 0cf3:3002 Atheros Communications, Inc. 
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 003: ID 05d5:6782 Super Gate Technology Co., Ltd 
Bus 004 Device 002: ID 046d:c043 Logitech, Inc. MX320/MX400 Laser Mouse
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 0b05:1742 ASUSTek Computer, Inc. 802.11n Network Adapter
Bus 002 Device 002: ID 045e:075d Microsoft Corp. LifeCam Cinema
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 045e:075d Microsoft Corp. LifeCam Cinema
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

---

### Post by nevixa on 2011-06-30
Is it possible that one of the actions I did killed one of my usb webcams? I used to be able to run 2 usb webcams at the same time. Now I am not able to use any webcam on one of the usb ports on the same usb controller. The other usb controller is working fine, with both webcams, but not simultaneously. I think something else killed it, like me upgrading the kernel and when I saw the webcam problem I downgrade the kernel again. If you have any idea…

---

### Post by chili555 on 2011-06-30
> Is it possible that one of the actions I did killed one of my usb webcams? I used to be able to run 2 usb webcams at the same time. Now I am not able to use any webcam on one of the usb ports on the same usb controller. The other usb controller is working fine, with both webcams, but not simultaneously. I think something else killed it, like me upgrading the kernel and when I saw the webcam problem I downgrade the kernel again. If you have any idea…I am not too sure. What I think is a possibility is that your USB controller doesn't put out enough power to enable two webcams and a wireless device and a mouse and a bluetooth device and...and...

I am intrigued:> Now I also see in the top system bar (don't know the official term, sorry) the words: Wireless Network, which I haven't seen for a long time.Below that I see: device not managed. I don't see any networks yet, but that is the next step I guess. Do you have an internal wireless card that has been resurrected? The built-in rt2870sta driver definitely doesn't drive your USB device, at least in 2.6.35. By the time we get to Natty, 2.6.38, the usb.id has been added. That's exactly what we're going to do.

Remove the device and in a terminal, do:```

sudo gedit /etc/udev/rules.d/network_drivers.rules
```Add one long line:```

ACTION=="add", SUBSYSTEM=="usb", ATTR{idVendor}=="0b05", ATTR{idProduct}=="1784", RUN+="/sbin/modprobe -qba rt2870sta"
```Caps, brackets, punctuation, etc. are crucial. Proofread twice, save and close gedit.```
sudo gedit /etc/modprobe.d/network_drivers.conf
```Add one long single line:```

install rt2870sta /sbin/modprobe --ignore-install rt2870sta $CMDLINE_OPTS; /bin/echo "0b05 1784" > /sys/bus/usb/drivers/rt2870/new_id
```
Proofread twice, save and close gedit. Insert the device. If it doesn't start immediately, you might have to do:```
sudo modprobe rt2870sta
```

---

### Post by nevixa on 2011-06-30
Wow , it seems like it is actually working. This post is send via wifi. I have to say that I am not really sure about if any of the last steps helped, because at some point I suddenly was able to see and connect to an access point, even before doing the last steps.

Is it normal that both files (network_drivers.rules and .conf) were empty files?

If my two usb controllers can't deliver the bandwidth or power for also the wifi card, there is a easy way to test this. By just disabling the wifi card. I remember something like wlan0 down? Is this correct?

Really thanx for all the help!

---

### Post by chili555 on 2011-06-30
> Is it normal that both files (network_drivers.rules and .conf) were empty files?Yes; you created new files.> By just disabling the wifi card. I remember something like wlan0 down? Is this correct?You mean an internal one? Or disable the USB so you can use two webcams or ???

I suspect that we are not quite done.

---

### Post by nevixa on 2011-06-30
> **chili555 said:**
> Yes; you created new files.You mean an internal one? Or disable the USB so you can use two webcams or ???

I suspect that we are not quite done.

I want to disable the internal wifi. My motherboard has an internal USB wifi card. To be honost, the two webcams are more important to me than the wifi. If the two webcams do work with wifi disabled, I can live with that. Is there any way to test if the two camera's do work when I disable the wifi card?

---

### Post by chili555 on 2011-06-30
```
sudo ifconfig wlan0 down
sudo rmmod -f rt2870sta
```> Is there any way to test if the two camera's do work when I disable the wifi card? I don't know. I have a very narrow area of (supposed) expertise. All I know about USB webcams is that I bought one that was supposed to work with Linux and Skype and it does. You might ask on General Help. [http://ubuntuforums.org/forumdisplay.php?f=331](http://ubuntuforums.org/forumdisplay.php?f=331)

---

### Post by nevixa on 2011-06-30
Thanks again. I got this and tried something:
```

diip@diipsel-2:~$ sudo ifconfig wlan0 down
[sudo] password for diip: 
wlan0: ERROR while getting interface flags: No such device
diip@diipsel-2:~$ sudo ifconfig ra0 down
diip@diipsel-2:~$ sudo rmmod -f rt2870sta
ERROR: Removing 'rt2870sta': Resource temporarily unavailable

```Any ideas how to get it down, because it is stil working ;)

---

### Post by chili555 on 2011-06-30
Let's see:```
ifconfig
iwconfig
```Thanks.

---

### Post by nevixa on 2011-06-30
What I did is: rightclick on the network icon in the top system bar and than click 'enable Wireless'. That worked. Now it seems like the cameras are also working again...which is nice, but also means that Wifi will be difficult to get working simultaneously with the 2 cameras.

---

### Post by nevixa on 2011-06-30
But I do have one question. When I reboot the system, Wireless is automatically enabled. Is there a way that this does not happen? I will shortly post my ifconfig and iwconfig if the linux box reboted.

---

### Post by nevixa on 2011-06-30
ifconfig:
```

eth0      Link encap:Ethernet  HWaddr bc:ae:c5:2a:79:93  
          inet addr:10.56.162.97  Bcast:10.56.162.255  Mask:255.255.255.0
          inet6 addr: fe80::beae:c5ff:fe2a:7993/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:656 errors:0 dropped:0 overruns:0 frame:0
          TX packets:771 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:589105 (589.1 KB)  TX bytes:103727 (103.7 KB)
          Interrupt:43 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

ra0       Link encap:Ethernet  HWaddr 48:5d:60:8a:a3:2a  
          inet addr:10.56.186.84  Bcast:10.56.187.255  Mask:255.255.254.0
          inet6 addr: fe80::4a5d:60ff:fe8a:a32a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4422 errors:0 dropped:0 overruns:0 frame:0
          TX packets:128 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1006948 (1.0 MB)  TX bytes:17844 (17.8 KB)

```

iwconfig:
```

lo        no wireless extensions.

eth0      no wireless extensions.

ra0       Ralink STA  ESSID:"WLAN-PUB"  Nickname:"RT2870STA"
          Mode:Managed  Frequency=2.437 GHz  Access Point: 58:BC:27:0E:22:D4   
          Bit Rate=65 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=100/100  Signal level:-46 dBm  Noise level:-59 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


```

Thank you for your time, effort and help so far!

---

### Post by chili555 on 2011-06-30
Yikes! Two interfaces with two IP addresses! Does your computer work any smoother with the ethernet cable detached? If you want to disable the wireless temporarily, do:```
sudo ifconfig ra0 down
sudo rmmod -f rt2870sta
```If it won't rmmod, it may be because Network Manager is starting ra0 right back up. The solution then is to blacklist rt2870sta and reboot. Are you sure that's what is driving it?```
lsmod | grep -e rt2 -e rt3
```

---

### Post by nevixa on 2011-06-30
I don't think that is the solution. Because it even effects booting ubuntu. Now I have to following workaround:
- Unplug 1 usb camera
- Start up ubuntu
- Disable Wireless
- Plug usb camera back in
- Everything works (except wifi ofcourse)

When I startup ubuntu with the camera pluged in, I get all kinds of errors during the boot. When ubuntu is started, I am unable to do something with the second camera.

---

### Post by chili555 on 2011-06-30
> When I startup ubuntu with the camera pluged in, I get all kinds of errors during the bootLike what?```
dmesg
```Did you Google and try to resolve the errors? Do you want to kill the internal wireless altogether? We have ways...(reversible, of course!)

---

