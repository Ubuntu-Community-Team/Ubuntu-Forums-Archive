---
title: "&quot;Bad password&quot; error message when trying to connect to WPA/WPA2 wireless network"
date: 2011-07-05
forum: Networking &amp; Wireless
---

### Post by elrock on 2011-07-05
I keep getting a "bad password" error message when trying to connect via wpa_supplicant to a wireless network (Apple Time Capsule WPA/WPA2 mixed).

Here's my wpa_supplicant.conf:

```
ctrl_interface=/var/run/wpa_supplicant
ap_scan=1

network={
        ssid="MyNetwork"
        scan_ssid=1
        proto=WPA RSA
        key_mgmt=WPA-PSK
        pairwise=CCMP TKIP
        group=CCMP TKIP
        psk=ac8498e34632792a0c90099d83cae98852d079d6b7f12b6c88db23dbc80af1fc
}
```

And the relevant line in the /etc/network/interfaces file:

```
wpa_supplicant -Dwext -ira0 -c/etc/wpa_supplicant.conf
```

The Time Capsule log contains the following error message--

```
WPA handshake failed with STA XX:XX:XX:XX:XX likely due to bad password from client
```

So perhaps the password is somehow getting lost in translation from Ubuntu to the Time Capsule?

---

### Post by chili555 on 2011-07-05
Many of us have no luck at all with WPA/WPA2 mixed and beautiful results from WPA2 only. I suggest you try it if possible.

---

### Post by elrock on 2011-07-06
Switching to WPA2 didn't help.  I know it's not very informative, but this is the message I get when I run wpa_supplicant from the terminal:

```
Trying to associate with xx:xx:xx:xx:xx:xx (SSID='My_Network' freq=2462 MHz)
ioctl[SIOCSIWGENIE]: Operation not supported
Association request to the driver failed
```

This could possibly be the source of the problem: the Linux wireless driver (RT2870STA, I presume) is listed twice under Hardware Drivers.  I can deactivate the duplicate but I can't figure out how to remove it completely so there is only one driver listed.  I don't even know if it's needed since I am using the generic wext driver with wpa_supplicant.

Thanks for any help with this.  I know it can work since it worked before I reinstalled Ubuntu; I just need to pinpoint the source of the problem this time.

---

### Post by chili555 on 2011-07-06
> the Linux wireless driver (RT2870STA, I presume) is listed twice Ah, ha!!! Now I think I see it. Please post:```
lsmod | grep rt2
```Thanks.

---

### Post by elrock on 2011-07-06
grep rt2 returned nothing, but this turned up a different driver by the same manufacturer:

```
lsmod | grep rt3
rt3070sta             616023  0
```

I removed it from the kernel (modprobe -r) to see if that would solve the problem, but it ended up killing the wireless interface entirely (couldn't be brought up with ifconfig).

---

### Post by chili555 on 2011-07-07
There is no driver conflict as I suspected. Have you tried the simple way in /etc/network/interfaces, even temporarily? First, make a backup:```
sudo cp /etc/network/interfaces /etc/network/interfaces.bak
```Then modify the file:```
auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet dhcp
#or static if you prefer
wpa-essid My_Network
wpa-psk mycleartextkey
```Then do:```
sudo ifdown wlan0 && sudo ifup wlan0
```If it doesn't connect, syslog may give some clues.

May I assume that Network Manager, Wicd and all other automagic networking tools are not running?

---

### Post by elrock on 2011-07-07
I did have Wicd installed, and removed it.  Network Manager had previously been removed.

This is the message I get after "ifup ra0"

```
Listening on LPF/ra0/xx:xx:xx:xx:xx:xx
Sending on   LPF/ra0/xx:xx:xx:xx:xx:xx
Sending on   Socket/fallback
wpa_supplicant: /sbin/wpa_supplicant daemon failed to start
run-parts: /etc/network/if-pre-up.d/wpasupplicant exited with return code 1
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

Listening on LPF/ra0/xx:xx:xx:xx:xx:xx
Sending on   LPF/ra0/xx:xx:xx:xx:xx:xx
Sending on   Socket/fallback
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 19
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 9
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
ssh stop/waiting
ssh start/running, process 24614
```

The router log repeatedly showed the same error message -- "bad password" -- until I killed wpa_supplicant.

Is there anything in particular I should be looking for in syslog?  Some of the messages there might indicate errors in the driver configuration file (rt2870sta.dat -- apparently used for later version drivers like mine).

---

### Post by chili555 on 2011-07-07
> Some of the messages there might indicate errors in the driver configuration file (rt2870sta.dat -- apparently used for later version drivers like mine).That's a definite possibility. You might edit the file to add the relevant details. I was confident that, as soon as the interface started, if there was an /etc/network/interfaces file, it took precedence. Perhaps not. 

I believe you compiled the driver from source; there is a README_STA file that explains the parameters. I suggest you edit the rt2870sta file and unload and reload the driver:```
sudo rmmod -f rt3070sta
sudo modprobe rt3070sta
sudo ifdown ra0 && sudo ifup ra0
```Be sure interfaces is written for ra0, not wlan0. Post back if you need assistance.

---

### Post by elrock on 2011-07-07
We are sooo close, but still no cigar.

I changed WirelessMode from 5 (11ABGN mixed) to 9 (11BGN mixed) in the RT2870STA.dat file, and that got rid of the "bad password" error message.  Yay!

Now this is what appears repeatedly in the router log:

```
Installed unicast CCMP key for supplicant xx:xx:xx:xx:xx:xx
Associated with station xx:xx:xx:xx:xx:xx
Disassociated with station xx:xx:xx:xx:xx:xx
```

I think this has something to do with CCMP and TKIP.  I fixed it before by changing some lines in the wpa_supplicant.conf file, but I don't remember exactly what I did last time.  Sorry for my bad memory.

---

### Post by chili555 on 2011-07-07
> Default
CountryRegion=5
CountryRegionABand=7
CountryCode=
ChannelGeography=1
[COLOR="Red"]SSID[/COLOR]=11n-AP
NetworkType=Infra
WirelessMode=5
Channel=0
BeaconPeriod=100
TxPower=100
BGProtection=0
TxPreamble=0
RTSThreshold=2347
FragThreshold=2346
TxBurst=1
PktAggregate=0
WmmCapable=1
AckPolicy=0;0;0;0
[COLOR="Red"]AuthMode[/COLOR]=OPEN
[COLOR="Red"]EncrypType[/COLOR]=NONE
[COLOR="Red"]WPAPSK[/COLOR]=
How about these fields?

---

### Post by elrock on 2011-07-07
This is weird -- when I kill wpa_supplicant, it stays connected, until an idle timeout (I have a wired connection running concurrently while I figure out how to get wireless up and running).  I thought that wpa_supplicant was required for joining encrypted wireless networks.

Here are the fields from the RT2870STA.dat file:

```
SSID=MyNetwork (not in quotes)
AuthMode=WPA2PSK
EncrypType=TKIP
WPAPSK=mypassword (not in quotes)
```

Does it matter if I use WPAPSK or WPA2PSK in the AuthMode field for a network that is mixed WPA/WPA2 (unfortunately, I need it to be mixed in order for my wireless printer to work)?  I see that there are more options if wpa_supplicant is used, to confuse the issue even more.

---

### Post by chili555 on 2011-07-07
> Does it matter if I use WPAPSK or WPA2PSK in the AuthMode field for a network that is mixed WPA/WPA2 (unfortunately, I need it to be mixed in order for my wireless printer to work)?Ouch! That would be reason enough for an old Linux absolutist like me, to not buy a particular wireless printer!

It probably does, I'd try both.> I thought that wpa_supplicant was required for joining encrypted wireless networks.It is; just not to *stay* connected until the next inactivity; probe and response I believe.

---

### Post by elrock on 2011-07-07
Okay, so what do I do about wpa_supplicant?  Is there a way to kill the process automatically so that wireless stays connected?

---

### Post by chili555 on 2011-07-07
Stays connected?? I wasn't aware we *were* connected. Did you compile for being controlled by wpa_supplicant? From the README:> 3> In os/linux/config.mk 
	define the GCC and LD of the target machine
	define the compiler flags CFLAGS
	modify to meet your need.
	** Build for being controlled by NetworkManager or wpa_supplicant wext functions
	   Please set 'HAS_WPA_SUPPLICANT=y' and 'HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y'.What device and version do you have?```
lsusb
uname -r
```There is a later driver version, rt5370sta. Should we compile it instead?

---

### Post by elrock on 2011-07-07
Yup, definitely connected.  The wireless gets assigned an IP address and I can ssh into it for the brief time that it's up.

I will try recompiling from the newer driver version and see if that helps.  The readme file from ralink isn't the clearest set of instructions I've ever seen, but I'll give it another go.  Thanks for your help and patience.

---

### Post by chili555 on 2011-07-07
> The readme file from ralink isn't the clearest set of instructions I've ever seen, but I'll give it another go.I fully agree. As well, in some places, they are obviously copied from an earlier version and downright wrong. However, I can usually read between the lines and figure it out; probably because I've compiled Ralink drivers 20-25 times a year for several years and rt5370sta today! That's a long-winded way of saying that if you get stuck, please ask.

---

### Post by elrock on 2011-07-07
Following the ralink instructions, here's the error message I get when I try to load the driver after compiling it:

```
/sbin/insmod rt5370sta.ko
insmod: error inserting 'rt5370sta.ko': -1 Unknown symbol in module
```

I got that same message before and couldn't fix it so I just ignored it and hoped it wouldn't matter.  Perhaps it did matter...?

---

### Post by chili555 on 2011-07-07
Let's do a little diagnostic:```
cd wherethedriverwasextracted
sudo su
make clean
make > elrock.txt
make install >> elrock.txt
modprobe rt5370sta >> elrock.txt
dmesg | grep rt5 >> elrock.txt
uname -r >> elrock.txt
exit
zip elrock.zip elrock.txt
```In the location where the driver was extracted, find elrock.zip and attach it to your reply. Thanks.

---

### Post by elrock on 2011-07-07
It didn't end up being a large file so I'll just paste it here.

```
make -C tools
make[1]: Entering directory `/home/leslie/wireless_driver/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/leslie/wireless_driver/tools'
/home/leslie/wireless_driver/tools/bin2h
cp -f os/linux/Makefile.6 /home/leslie/wireless_driver/os/linux/Makefile
make -C /lib/modules/2.6.32-32-generic/build SUBDIRS=/home/leslie/wireless_driver/os/linux modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-32-generic'
  CC [M]  /home/leslie/wireless_driver/os/linux/../../common/rtmp_mcu.o
  LD [M]  /home/leslie/wireless_driver/os/linux/rt5370sta.o
  Building modules, stage 2.
  MODPOST 1 modules
  LD [M]  /home/leslie/wireless_driver/os/linux/rt5370sta.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-32-generic'
cp -f /home/leslie/wireless_driver/os/linux/rt5370sta.ko /tftpboot
make -C /home/leslie/wireless_driver/os/linux -f Makefile.6 install
make[1]: Entering directory `/home/leslie/wireless_driver/os/linux'
rm -rf /etc/Wireless/RT2870STA
mkdir /etc/Wireless/RT2870STA
cp /home/leslie/wireless_driver/RT2870STA.dat /etc/Wireless/RT2870STA/.
install -d /lib/modules/2.6.32-32-generic/kernel/drivers/net/wireless/
install -m 644 -c rt5370sta.ko /lib/modules/2.6.32-32-generic/kernel/drivers/net/wireless/
/sbin/depmod -a 2.6.32-32-generic
make[1]: Leaving directory `/home/leslie/wireless_driver/os/linux'
[19798.403905] rt5370sta: Unknown symbol usb_alloc_urb
[19798.403976] rt5370sta: Unknown symbol usb_free_urb
[19798.404183] rt5370sta: Unknown symbol usb_register_driver
[19798.404334] rt5370sta: Unknown symbol usb_put_dev
[19798.404392] rt5370sta: Unknown symbol usb_get_dev
[19798.404495] rt5370sta: Unknown symbol usb_submit_urb
[19798.404765] rt5370sta: Unknown symbol usb_control_msg
[19798.404937] rt5370sta: Unknown symbol usb_deregister
[19798.405208] rt5370sta: Unknown symbol usb_kill_urb
[19798.405263] rt5370sta: Unknown symbol usb_buffer_free
[19798.405512] rt5370sta: Unknown symbol usb_buffer_alloc
[21876.328848] rt5370sta: Unknown symbol usb_alloc_urb
[21876.329109] rt5370sta: Unknown symbol usb_free_urb
[21876.329880] rt5370sta: Unknown symbol usb_register_driver
[21876.330456] rt5370sta: Unknown symbol usb_put_dev
[21876.330673] rt5370sta: Unknown symbol usb_get_dev
[21876.331166] rt5370sta: Unknown symbol usb_submit_urb
[21876.332180] rt5370sta: Unknown symbol usb_control_msg
[21876.332826] rt5370sta: Unknown symbol usb_deregister
[21876.333842] rt5370sta: Unknown symbol usb_kill_urb
[21876.334048] rt5370sta: Unknown symbol usb_buffer_free
[21876.334981] rt5370sta: Unknown symbol usb_buffer_alloc
2.6.32-32-generic
```

Hmm...lots of unknown symbols.

To further complicate the issue, there is also a ralink firmware file that I downloaded.  It looks like it's for older driver versions so perhaps it's not needed.

---

### Post by chili555 on 2011-07-07
> $ modinfo rt5370sta
filename:       /lib/modules/2.6.38-8-generic/kernel/drivers/net/wireless/rt5370sta.ko
version:        2.5.0.1
description:    RT2870 Wireless Lan Linux Driver
author:         Paul Lin <paul_lin@ralinktech.com>
srcversion:     6B9B3D07B4E8749CE952ACA
alias:          usb:v13D3p3329d*dc*dsc*dp*ic*isc*ip*
<snip>
As you can see, firmware is not mentioned; it's not required.> make -C /lib/modules/2.6.32-32-genericYou have an interesting problem; an older kernel and gcc version with a newer driver. I was so encouraged when 'make' went oh so perfectly. I think you have the reverse of this problem:[http://xlcwu.wordpress.com/2010/07/09/build-rt3070-kernel-module-on-ubuntu-10-04-lucid-lynx/](http://xlcwu.wordpress.com/2010/07/09/build-rt3070-kernel-module-on-ubuntu-10-04-lucid-lynx/)> Specifically, these functions have been renamed. I believe the fix is to replace all instances of usb_buffer_alloc with usb_alloc_coherent and all instances of usb_buffer_free with usb_free_coherent. The instances I replaced were in include/os/rt_linux.h and os/linux/rt_usb_util.c.In other words, in those two files, change usb_free_coherent *back* to usb_buffer_free and usb_alloc_coherent *back* to usb_buffer_alloc.

Please try it and try compiling again preceeded with 'make clean.'

If you need more guidance, please ask. The doctor is in.

Of course, you could always install 11.04!

---

### Post by elrock on 2011-07-13
Hi Chili, I'm baaaack!  (You probably thought I had my wireless problems licked by now.  No such luck...)

The WPA "bad password" error is long gone, the wireless driver module is built, installed, and loaded properly, and I can connect to wireless via Network Manager.  But now I get a new "bad password" message whenever I reboot: "enter password to unlock your login keyring."  Once I enter my LOGIN password (NOT my wireless password), the machine automatically connects to the wireless network with no problems.  I set up the machine to log in automatically, so I don't know why it keeps throwing up this message.

I am doing this all through the GUI although I would rather do it through a remote terminal since this is meant to be a headless machine.  Unfortunately, Network Manager is the only way I can get wireless to work right now.  I tried removing Network Manager and adding the wireless interface to the /etc/network/interfaces file, but that just causes an endless loop of connecting and then disconnecting.  (Perhaps it indicates an ongoing problem with the wpa_supplicant settings?)  

So, is there a way to get rid of the "login password" message on reboot?

Edited to add: Never mind, I solved it!  In Network Manager, I edited the wireless connection to make it available to all users.

---

