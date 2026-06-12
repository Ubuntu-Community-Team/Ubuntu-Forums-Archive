---
title: "HP Pavilion DV6 with Broadcom BCM4312"
date: 2010-09-04
forum: Networking &amp; Wireless
---

### Post by doctorzeus on 2010-09-04
Hi,

I'm relatively new to Ubuntu and Linux OS in general, hope this hasn't already been solved but after trying for 24hrs+ I think it may be time for me to start my own thread (sorry if there is already one).

I have been desperately trying to get my Broadcom BCM4312 wireless card to work and after searching about 100 sites and threads I still can't get it going:(

Here are some of the problems Ive been having(I am running Ubuntu 8.04 by the way):

1. Tried installing "Broadcom STA Wireless Driver" under System->Administration->hardware drivers but after install it didn't show any signs of working.

2. I tried getting the Linux driver off the website 
([http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)) and followed the instructions in the readme to the letter, yet when i am asked to type in one of the final commands:

# sudo insmod wl.ko

I get the output:

# error inserting 'wl.ko': -1 File exists

I have also looked at this website where a guy posts the same problem but no one posted anything back:

[http://jomcode.com/fadhil/jomcode/broadcom-official-linux-driver-bcm4312/](http://jomcode.com/fadhil/jomcode/broadcom-official-linux-driver-bcm4312/)

I also followed the instructions on this site to see if there was solution, still the same problem:

# error inserting 'wl.ko': -1 File exists

3. Went to this website:
[http://penkin.wordpress.com/2008/03/28/ubuntu-804-broadcom-wireless/](http://penkin.wordpress.com/2008/03/28/ubuntu-804-broadcom-wireless/)

 where the guy seems to be having the same problem when installing the driver from System->Administration->hardware drivers but when I get up to  

# export FIRMWARE_INSTALL_DIR="/lib/firmware"

For one I'm a bit confused about what to put here and also I get this output:

# sudo: export: command not found

Please help! I really need this going with the next few days!

Doctorzeus

---

### Post by JLGreen on 2010-09-04
Doctorzues,

I have been having a similiar problem getting this driver to work on my system.  It appears your stuck a few steps behind me though.  When you attempted to run the "insmod" command and got the error "-1 File exists", did you first make sure the original wl.ko file was backed up?  You should have had to copy the wl.ko file from wherever you built it to the /lib/modules/[your kernel version]/kernel/net/wireless.
Perhaps you should make sure the file in that directory has the timestamp of the file you built.

---

### Post by chili555 on 2010-09-04
> error inserting 'wl.ko': -1 File existsThat suggests that the module wl is already loaded. Let's check with:```
lsmod | grep wl
```If the terminal reports it's loaded, something like this:> $ lsmod | grep wl
wl                   1959598  0 
lib80211                5046  1 wlThen you are most of the way done. Please post:```
iwconfig
dmesg | grep wl
```Thanks.

---

### Post by JLGreen on 2010-09-04
I was just directed to this you'll probably want to take a look, it might solve your problem...

[http://ubuntuforums.org/archive/index.php/t-1052779.html](http://ubuntuforums.org/archive/index.php/t-1052779.html)

It looks like you'll want to try
sudo rmmod wl
sudo insmod wl.ko

---

### Post by JLGreen on 2010-09-04
Chili555, 

If you have some time please see if you can help with my issue, I am currently quite stuck.

[http://ubuntuforums.org/showthread.php?p=9798312#post9798312](http://ubuntuforums.org/showthread.php?p=9798312#post9798312)

thanks

---

### Post by doctorzeus on 2010-09-05
> **JLGreen said:**
> Doctorzues,

I have been having a similiar problem getting this driver to work on my system.  It appears your stuck a few steps behind me though.  When you attempted to run the "insmod" command and got the error "-1 File exists", did you first make sure the original wl.ko file was backed up?  You should have had to copy the wl.ko file from wherever you built it to the /lib/modules/[your kernel version]/kernel/net/wireless.
Perhaps you should make sure the file in that directory has the timestamp of the file you built.

Thankyou for the help

Ok I re-installed Ubuntu and went through the read me again, it seems there was a "wl.ko" pre-bundled with Ubuntu already and I removed it and installed the new one:D, however still not working:(. Yes there is the new "wl.ko" file in my "/lib/modules/[your kernel version]/kernel/net/wireless" wireless still not going...Yep both have the same timestamp.

---

### Post by doctorzeus on 2010-09-05
> **chili555 said:**
> That suggests that the module wl is already loaded. Let's check with:```
lsmod | grep wl
```If the terminal reports it's loaded, something like this:Then you are most of the way done. Please post:```
iwconfig
dmesg | grep wl
```Thanks.

Thanks for the help here is my output:

For # lsmod | grep wl:
"
wl                   1968644  0 
ieee80211_crypt         7040  2 ieee80211_crypt_tkip,wl
"

For # iwconfig: 

"
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11bg  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:off   
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Managementmode:All packets received
          Link Quality=5/5  Signal level=0 dBm  Noise level=0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
"

and # dmesg | grep wl: 
"

[   64.935757] wl: module license 'unspecified' taints kernel.

"

Hope this helps

---

### Post by chili555 on 2010-09-05
> [COLOR="Red"]eth1[/COLOR] IEEE 802.11bg ESSID:"" Nickname:""
Mode:Managed Frequency:2.412 GHz Access Point: Not-Associated
Bit Rate:54 Mb/s [COLOR="Red"]Tx-Power:off[/COLOR] Usually, Broadcoms create an interface of wlan0; yours seems to be eth1. May I assume you have no other wireless devices?

Please try:```
sudo iwconfig eth1 txpower 20
```If 20 won't take, try 18 and 16, etc.,  until you find a number that doesn't cause an error. Next try:```
sudo iwlist eth1 scan
```If you get scan results, click the Network Manager icon and see if you can connect.

If not, please post:```
dmesg | grep eth1
```Thanks.

---

### Post by doctorzeus on 2010-09-05
> **chili555 said:**
> Usually, Broadcoms create an interface of wlan0; yours seems to be eth1. May I assume you have no other wireless devices?

Please try:```
sudo iwconfig eth1 txpower 20
```If 20 won't take, try 18 and 16, etc.,  until you find a number that doesn't cause an error. Next try:```
sudo iwlist eth1 scan
```If you get scan results, click the Network Manager icon and see if you can connect.

If not, please post:```
dmesg | grep eth1
```Thanks.



Ok thanks,

"sudo iwconfig eth1 txpower 20" seemed to work (at least I got no errors).

Tried "sudo iwlist eth1 scan" and got this error:

"eth1      Failed to read scan data : Invalid argument"

My Output of "dmesg | grep eth1" is:

"
[   63.816265] eth1: Broadcom BCM4315 802.11 Hybrid Wireless Controller 5.60.48.36 
[  108.409181] eth1: no IPv6 routers present
"

Thanks

Doctorzeus

---

### Post by chili555 on 2010-09-05
Please open System > Administration > Synaptic. Search for linux-restricted-modules. If it is installed, please remove it and reboot. Also, please post:```
rfkill list
```Thanks.

---

### Post by doctorzeus on 2010-09-06
> **chili555 said:**
> Please open System > Administration > Synaptic. Search for linux-restricted-modules. If it is installed, please remove it and reboot. Also, please post:```
rfkill list
```Thanks.

Found 3 restricted Modules, removed them...



Rebooted, no change..when I enter "rfkill list" it says:

"bash: rfkill: command not found", how do I install this so I can proceed?

Thanks

Doctorzeus

---

### Post by chili555 on 2010-09-06
> "bash: rfkill: command not found", how do I install this so I can proceed?Please connect the ethernet cable and do:```
sudo apt-get install rfkill
```

---

### Post by doctorzeus on 2010-09-12
> **chili555 said:**
> Please connect the ethernet cable and do:```
sudo apt-get install rfkill
```

Sorry for the long reply,


I get this error:

~$ sudo apt-get install rfkill
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package rfkill

---

### Post by chili555 on 2010-09-12
Which version of Ubuntu are you running?```
uname -r
```Were you connected to the internet by ethernet at the time?

---

### Post by doctorzeus on 2010-09-14
> **chili555 said:**
> Which version of Ubuntu are you running?```
uname -r
```Were you connected to the internet by ethernet at the time?

I'm Running Hardy, output:

2.6.24-26-generic

Thanks

Doctorzeus

---

### Post by chili555 on 2010-09-14
Hardy is quite old; you might have much better luck with Lucid.

Please post:```
sudo cat /var/log/syslog | grep -i -e kill -e eth1
dmesg | grep -i firm
```Thanks.

---

### Post by doctorzeus on 2010-09-14
> **chili555 said:**
> Hardy is quite old; you might have much better luck with Lucid.

Please post:```
sudo cat /var/log/syslog | grep -i -e kill -e eth1
dmesg | grep -i firm
```Thanks.

My Wireless seemed to work on Lucid before however I don't like the new Ubuntu versions because of the limited custumisation options for the login screen and etc...

Thanks

Doctorzeus

---

### Post by chili555 on 2010-09-14
How about the other tests?

---

### Post by doctorzeus on 2010-09-16
> **chili555 said:**
> How about the other tests?

Sorry, my Laptop's going in for a service (unrelated hardware problem), will post output when I get it back...

Thanks for the help though!

Doctorzeus

---

### Post by doctorzeus on 2010-09-29
> **chili555 said:**
> How about the other tests?

Ok got my Laptop back and HP managed to stuff up the OS :mad:,

Re-initialized Ubuntu Hardy 8.04, decided to check "# lsmod | grep wl" as soon as I installed and got this output: "

wl                   1279060  0 
ieee80211_crypt         7040  2 ieee80211_crypt_tkip,wl
"

turns out wl is already installed to start with, but wireless doesn't work,

"sudo rmmod wl" removes it but it comes back after install, blacklisting it stops any wireless options completely(I re-re-installed Ubuntu after that to get a clean slate)..I haven't installed the driver from the website yet but heres the output you asked for:

Output For "":
"
sudo cat /var/log/syslog | grep -i -e kill -e eth1
Sep 29 18:56:36 Terminal-1077 kernel: [   63.486190] eth1: Broadcom BCM4315 802.11 Wireless Controller 5.10.91.9
Sep 29 18:56:38 Terminal-1077 NetworkManager: <info>  eth1: Device is fully-supported using driver 'wl'. 
Sep 29 18:56:38 Terminal-1077 NetworkManager: <info>  eth1: driver does not support SSID scans (scan_capa 0x00). 
Sep 29 18:56:38 Terminal-1077 NetworkManager: <info>  Now managing wireless (802.11) device 'eth1'. 
Sep 29 18:56:38 Terminal-1077 NetworkManager: <info>  Deactivating device eth1. 
Sep 29 18:56:38 Terminal-1077 NetworkManager: <WARN>  nm_device_802_11_wireless_set_wep_enc_key(): error setting key for device eth1: Invalid argument 
Sep 29 18:56:53 Terminal-1077 avahi-daemon[4785]: Registering new address record for fe80::221:ff:fed1:db93 on eth1.*.
Sep 29 18:57:02 Terminal-1077 kernel: [   95.161171] eth1: no IPv6 routers present
"

No Ouput for "dmesg | grep -i firm"

Thanks for the help!

Doctorzeus

---

### Post by doctorzeus on 2010-09-29
Results that may also be of interest:

Input: "lspci -n | grep 14e4"

Output: "02:00.0 0280: 14e4:4315 (rev 01)"

May not mean it's compatible??

This did shed some light:

[http://forum.aircrack-ng.org/index.php?topic=6434.0](http://forum.aircrack-ng.org/index.php?topic=6434.0)

trying it now...except replacing "karmic" with "hardy"..

Thanks

Doctorzeus

---

### Post by chili555 on 2010-09-29
*wl* is the appropriate module:```
$ modinfo wl | grep 4315
alias:          pci:v0000[COLOR="Red"]14E4[/COLOR]d0000[COLOR="Red"]4315[/COLOR]sv*sd*bc*sc*i*
```I'm not sure why you'd want to rmmod and blacklist it, since "...blacklisting it stops any wireless options completely..."

What wireless options are available? After you re-installed, does scanning produce any result?```
sudo iwlist eth1 scan
```

---

### Post by doctorzeus on 2010-10-04
> **chili555 said:**
> *wl* is the appropriate module:```
$ modinfo wl | grep 4315
alias:          pci:v0000[COLOR="Red"]14E4[/COLOR]d0000[COLOR="Red"]4315[/COLOR]sv*sd*bc*sc*i*
```I'm not sure why you'd want to rmmod and blacklist it, since "...blacklisting it stops any wireless options completely..."

What wireless options are available? After you re-installed, does scanning produce any result?```
sudo iwlist eth1 scan
```

Nope, "eth1 failed to read scan data : invalid argument"..

I "rmmod wl" and installed the Broadcom Driver from the Broadcom website by the way..

Thanks Doctorzeus


Doctorzeus

---

### Post by chili555 on 2010-10-04
> I "rmmod wl" and installed the Broadcom Driver from the Broadcom website by the way..So, what module is driving it now? Please post:```
sudo lshw -C network
```By the way, *rmmod* only works until reboot.

---

### Post by doctorzeus on 2010-10-05
> **chili555 said:**
> So, what module is driving it now? Please post:```
sudo lshw -C network
```By the way, *rmmod* only works until reboot.


I rmmod the pre-bundled wl driver and then installed the driver from the broadcom website:

[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

It contains a wl.ko file which I insmod...will this be overwritten by the pre-bundled ubuntu one?

Heres My output:

```
-network               
       description: Wireless interface
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth1
       version: 01
       serial: 00:21:00:d1:db:93
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.10.91.9 latency=0 module=wl multicast=yes wireless=IEEE 802.11bg
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:26:9e:f0:7e:b8
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.2LK duplex=full ip=192.168.147.105 latency=0 link=yes module=r8169 multicast=yes port=twisted pair speed=100MB/s

```

Thanks

Doctorzeus

---

### Post by bkratz on 2010-10-05
> **doctorzeus said:**
> I rmmod the pre-bundled wl driver and then installed the driver from the broadcom website:

[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

It contains a wl.ko file which I insmod...will this be overwritten by the pre-bundled ubuntu one?


[/CODE]

Thanks

Doctorzeus



did the do the instruction moving the original file as below, to make a "clean" transition, not just the rmmod? From the help me file at that site.


INSTALL INSTRUCTIONS
--------------------

Upgrading from a previous version:
---------------------------------

If you were already running a previous version of wl, you'll want to provide
a clean transition from the older driver. (The path to previous driver is
usually /lib/modules/<kernel-version>/kernel/net/wireless)

# rmmod wl 
# mv <path-to-prev-driver>/wl.ko <path-to-prev-driver>/wl.ko.orig
# cp wl.ko <path-to-prev-driver>/wl.ko
# depmod
# modprobe wl

---

### Post by doctorzeus on 2010-10-05
> **bkratz said:**
> did the do the instruction moving the original file as below, to make a "clean" transition, not just the rmmod? From the help me file at that site.


INSTALL INSTRUCTIONS
--------------------

Upgrading from a previous version:
---------------------------------

If you were already running a previous version of wl, you'll want to provide
a clean transition from the older driver. (The path to previous driver is
usually /lib/modules/<kernel-version>/kernel/net/wireless)

# rmmod wl 
# mv <path-to-prev-driver>/wl.ko <path-to-prev-driver>/wl.ko.orig
# cp wl.ko <path-to-prev-driver>/wl.ko
# depmod
# modprobe wl

Tried that before but to no avail...same problem still...will try again though...

Thanks

Doctorzeus

---

### Post by doctorzeus on 2010-10-19
Nope,

Still not working...

Where is the file that checks what modules are loaded on startup?

(I followed the instructions for nothing happening in the readme and copyed Wl.ko to modules/net/wireless like it said still nothing)...

Wireless is still listing under eth1 suggestions?

Thanks

Doctorzeus

---

