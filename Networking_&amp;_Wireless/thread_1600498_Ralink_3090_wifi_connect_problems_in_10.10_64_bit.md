---
title: "Ralink 3090 wifi connect problems in 10.10 64 bit"
date: 2010-10-19
forum: Networking &amp; Wireless
---

### Post by archithcr on 2010-10-19
Hi everyone

I have an HP DV6 3143se which has a Ralink 3090 wifi card in it.the only thing that doesn't work at the moment is the Wifi. I tried installing the Linux backports module, but the trouble is that sometimes, my home wifi network is shown on the list of available networks and most often, it's not.

when the network does show up, and i click on it and enter my WPA2 password, it takes ages to handshake and then it tells me that my password is wrong. the same password works in windows 7 so something's not working.

when i try to disable and re enable wireless network on the network manager applet, i get a Wireless device not ready or Network manager not running message.

Any suggestions would be most welcome as i hate having to depend on my wired ethernet to stay connected.


EDIT
Thanks all :)  Please follow the method outlined below. Much thanks to Rtomakov for guiding me.  

 Download new driver from ralink support page (version 2.4.1) and unpack it somewhere (I did it in my Download folder). 
Read README_STA_PCI file - find file config.mk in os/linux folder, open it with gedit and edit lines: - 
HAS_ATE=y (originally was n) - 
HAS_WPA_SUPPLICANT=y (originally was n) - 
HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y (originally was n) and - 
HAS_ANTENNA_DIVERSITY_SUPPORT=y originally was n)  

 Now, before compile, install via synaptic these packages: build-essential, devscripts and cdbs. * Note : I didn't have to do this, but perhaps you can try it out if you have your wired internet working. Edit is mine, not Rtomakov's. *  

 Enter DPO_... folder from terminal and do sudo make, and after make finishes (without errors, ignore warnings) do sudo make install. That is it, but it is not over yet. Now open /etc/modprobe.d/blacklist.conf (as root) and add at the end: blacklist rt2800pci. Also open (as root) file /etc/modules and add: rt3390sta.   

* to do the above, i used the command - gksudo gedit /etc/modprobe.d/blacklist.conf and - gksudo gedit /etc/modules. Make your edits in gedit, Save them and CLOSE the file to return to the terminal.*   

Now, reboot. That should work.

---

### Post by archithcr on 2010-10-19
Anyone with any suggestions?

Atleast the wifi networks are getting shown. But the problem with WPA passwords still remains. If anyone has any tips, it would be great :)

---

### Post by rtomakov on 2010-10-20
Easiest way:  download linux drivers for rt3090 from ralink download page ([http://www.ralinktech.com/support.php?s=2](http://www.ralinktech.com/support.php?s=2)), install it (read how to do that in readme file in driver package) and add "rt3090sta" in /etc/modules file. This card works on ubuntu 10.10 without any problems.
If installing drivers shows some errors (it shouldnt, but ...), install (via synaptic) these packages:build-essentials, devscripts and cdbs and then try to build driver

---

### Post by archithcr on 2010-10-21
Problem solved. Sorta.

I Had to remove the 64 bit installation and install 32 bit version of ubuntu 10.10. Wireless works perfect now. must be a 64 bit incompatibility with drivers.

---

### Post by rtomakov on 2010-10-21
Wrong!
ralink driver works on x86_64 version - I have it installed as I described above.

---

### Post by llafar on 2010-10-25
@rtomakov: Can you please describe how you installed ralink driver or can you share the files?

I'm fighting with rl3090 on HP 4320s for many days now. 



[LIST]
[*]rt3090-dkms package and its manual recompilation does not work.
[/LIST]

[LIST]
[*]ralink driver as you described compiles itself with bunch of warnings, but I get driver for 3090 (and 3390). Nevertheless it still does not work.
[/LIST]

On 32-bit platforms everything runs seamlessly. On every 10.10-amd64 the wifi fails.

---

### Post by rtomakov on 2010-10-26
Download new driver from ralink support page (version 2.4.1) and unpack it somewhere (I did it in my Download folder). Read README_STA_PCI file -  find file config.mk in os/linux folder, open it with gedit and edit lines:
- HAS_ATE=**y** (originally was **n**)
- HAS_WPA_SUPPLICANT=**y **(originally was **n**)
- HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=**y **(originally was **n**) and
- HAS_ANTENNA_DIVERSITY_SUPPORT=**y** originally was **n**)

Now, before compile, install via synaptic these packages: build-essential, devscripts and cdbs.

Enter DPO_... folder from terminal and do **sudo make**, and after make finishes (without errors, ignore warnings) do **sudo make install. **That is it, but it is not over yet. Now open /etc/modprobe.d/blacklist.conf (as root) and add at the end: blacklist rt2800pci. Also open (as root) file /etc/modules and add: rt3390sta. 
Now, reboot. That should work. Write some feedback.

---

### Post by llafar on 2010-10-26
You are genius! 

It's not only working, but the driver (2.4.0.1, I didn't find 2.4.1 on ralink page) is supporting card even better then default driver in 32bit systems. I.e. 1) wifi switch on & off do not kills the card until next reboot and 2) wifi led is just operating like under original suse and not blinking as crazy.

Without your explanation it was not clear even after reading README_STA_pci for the fourth time. Once again many thanks for your help!

---

### Post by rtomakov on 2010-10-27
I am glad I could help someone.

---

### Post by llafar on 2010-10-28
I found something interesting.

There is no rt3090sta nor rt3390sta module loaded to kernel. The card works on rt2680sta module. I see additionally some warnings, I suppose they are because of modprobe'ing rt3390sta driver.

I will do tomorrow some additional checks. I suspect, that if wifi works on rt2860sta module then perhaps it is enough to put "blacklist rt2800pci" in modprobe.d. I need plain installation of ubuntu x64, so i will try to modify usb image for that.

---

### Post by rtomakov on 2010-10-28
Just look in modules.alias. 
As I can remember there is entry  "alias rt3390sta rt2860sta" or something like that, what identify rt3390sta module as rt2860. If I understood this correctly, module rt3390sta exists and it is in use  (and it is installed in /lib/modules/... dir) but it is not identified as 3390 but 2860.
 Also, if you run "additonal hardware drivers" - jockey-gtk from settings - control panel, it should show rt3390 driver as active and in use.

---

### Post by archithcr on 2010-10-29
here's a bit of an update from me.

The instructions that came along with the driver from Ralink site were good, but for a n00b like me, were a bit too much as some modifications required root access, but i didn't want to create a root account on Ubuntu as my machine is connected to public networks.

there's a deb version of the drivers found here at [https://launchpad.net/~markus-tisoft/+archive/rt3090/+build/1098170](https://launchpad.net/~markus-tisoft/+archive/rt3090/+build/1098170)

that takes care of everything. only problem is that it wasn't installing on the 10.10 kernels as it needed dpkms but the problem is that i couldn't connect to the internet in the first place, lol. yes, even my ethernet connection wasn't working.

but i found a distro which let me install the above driver to connect to the net without needing additional dependencies. that distro was Linux mint 9. I was able to get my wifi drivers installed on 64bit without problems. the weird bit is that the deb drivers don't install on  linux mint 10 which is the latest version. 

i tried open suse, kubuntu, fedora and debian but none of them could recognise the 3090 or install the driver.

it's strange because linux mint is an ubuntu derivative. for comparison, i tried installing the driver on lucid, but ran into the same dpkms error as 10.10.

that's my experience and i really hope there's a better integration of wifi drivers in 11.04.

Thanks for the patience and replies guys :)

---

### Post by llafar on 2010-10-31
Regarding root account: root account is on any linux. You don't have to create it. It's just there. So @archithcr, I really recommend the below method "sudo vi /etc/modprobe.d/blacklist.conf" or "sudo nano /etc/modprobe.d/blacklist.conf" or use whatever editor you like (I like midnight commander, but I'm old, it just remind me '80 and early '90).

For me the simplest solution that works is as follows:
"Open /etc/modprobe.d/blacklist.conf (as root) and add at the end: blacklist rt2800pci"

I also tried it on ubuntu-desktop-10.10-amd64 runned from pendrive. But since I do not know how to modify initrd, I just did it differently.

[LIST=1]
[*]Remove all modules with name like rt2*: lsmod | fgrep rt2, and then remove it all, like modprobe -r rt2860sta, modprobe -r rt2x00pci, modprobe -r rt2x00usb, .... according to their dependencies.
[*]Add the module mentioned below: modprobe -a rt2860sta
[/LIST]

I reviewed the rt2860sta module and it is not an alias. This module is just in staging area:
```

$ modinfo rt2860sta
filename:       /lib/modules/2.6.35-22-generic/kernel/drivers/staging/rt2860/rt2860sta.ko
version:        2.1.0.0
alias:          rt3090sta
license:        GPL
description:    RT2860/RT3090 Wireless Lan Linux Driver
author:         Jett Chen <jett_chen@ralinktech.com>
firmware:       rt3090.bin
firmware:       rt2860.bin
srcversion:     1CC5B0F527E33CC4AF73D2B
alias:          pci:v00001814d00003092sv*sd*bc*sc*i*
alias:          pci:v00001814d00003091sv*sd*bc*sc*i*
alias:          pci:v00001814d00003090sv*sd*bc*sc*i*
alias:          pci:v00001432d00007768sv*sd*bc*sc*i*
alias:          pci:v00001432d00007748sv*sd*bc*sc*i*
alias:          pci:v00001432d00007738sv*sd*bc*sc*i*
alias:          pci:v00001432d00007727sv*sd*bc*sc*i*
alias:          pci:v00001432d00007758sv*sd*bc*sc*i*
alias:          pci:v00001432d00007728sv*sd*bc*sc*i*
alias:          pci:v00001432d00007708sv*sd*bc*sc*i*
alias:          pci:v00001A3Bd00001059sv*sd*bc*sc*i*
alias:          pci:v00001814d00000781sv*sd*bc*sc*i*
alias:          pci:v00001814d00000701sv*sd*bc*sc*i*
alias:          pci:v00001814d00000681sv*sd*bc*sc*i*
alias:          pci:v00001814d00000601sv*sd*bc*sc*i*
depends:        crc-ccitt
staging:        Y
vermagic:       2.6.35-22-generic SMP mod_unload modversions 
parm:           mac:rt28xx: wireless mac addr (charp)

```My kernel does not load rt3390sta driver due to some errors. I assume it has something to do with:
```

[   10.259180] rt2860sta: module is from the staging directory, the quality is unknown, you have been warned.
[   10.267283] rt2860 0000:43:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[   10.267339] rt2860 0000:43:00.0: setting latency timer to 64
[   10.267421] === pAd = ffffc90010fd1000, size = 528640 ===
[   10.267423] <-- RTMPAllocAdapterBlock, Status=0
[   10.267424] pAd->CSRBaseAddress =0xffffc90010a40000, csr_addr=0xffffc90010a40000!
[   10.333127] lis3lv02d: hardware type HPB432x found.
[   10.333990] lis3lv02d: 8 bits sensor found
[   10.360095] lp: driver loaded but no devices found
[   10.374611] input: HP WMI hotkeys as /devices/virtual/input/input9
[   10.406682] Error: Driver 'rt2860' is already registered, aborting...
[   10.441911] type=1400 audit(1288535798.031:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient3" pid=853 comm="apparmor_parser"
[   10.442460] type=1400 audit(1288535798.031:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=853 comm="apparmor_parser"
[   10.442707] type=1400 audit(1288535798.031:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=853 comm="apparmor_parser"
[   10.465464] input: ST LIS3LV02DL Accelerometer as /devices/platform/lis3lv02d/input/input10
[   10.466507] Bluetooth: Core ver 2.15
[   10.466525] NET: Registered protocol family 31
[   10.466526] Bluetooth: HCI device and connection manager initialized
[   10.466528] Bluetooth: HCI socket layer initialized
[   10.469886] Bluetooth: Generic Bluetooth USB driver ver 0.6
[   10.469974] Linux video capture interface: v2.00
[   10.472997] uvcvideo: Found UVC 1.00 device HP Webcam [2 MP Fixed] (05c8:0403)
[   10.476545] Error: Driver 'rt2860' is already registered, aborting...
[   10.480618] Registered led device: hp::hddprotect
[   10.480638] lis3lv02d driver loaded.
[   10.482040] usbcore: registered new interface driver btusb

```
But I will not dig into further as I'm happy enough with standard ubuntu driver.

---

### Post by rvr on 2010-11-01
i tried open suse, kubuntu, fedora and debian but none of them could recognise the 3090 or install the driver. [post#12]

Dear Archithcr, it`s a pity you did not try pclinuxos or mandriva. They have a support in synaptic, you can use after installing. You need only once a wired internet. I work with it now for half a year, but with ubuntu i could not fix it.

---

### Post by archithcr on 2010-11-03
@llafar and @rvr Hey thanks for the input guys. From my understanding, by default, Ubuntu doesn't create a root account right? It gives root privileges to the user account created during the initial setup. Since i read somewhere that most hackers try to crack a root account first, not having a root account is a decent security measure and that's why i didn't like the idea of venturing into creating one.  But i decided to try @rtomakov's method and it worked great! i was able to get my wifi up and running in Maverick following his method. the only thing i did slightly different was to use the "gksudo gedit" command to edit the blacklist.conf and module files. Thanks a lot Rtomakov :)  So i can say that with a bit of tweaking, the 3090 wifi chipset does indeed work in ubuntu 10.10 64 bit.  Thanks guys and hopefully this will work for anyone who is facing the same problem as i was facing.

---

### Post by Johonunu on 2010-11-05
Thank you! Your solution worked for me on MSI CR720 :)

---

### Post by ohadary on 2010-12-04
Hi guys,

Have you tried to build the version currently available on the Ralink website i.e. PCIe3090 2.4.0.2 driver.

I followed your instructions, however, with the slightly newer version I get the errors below. For cross reference I wanted to try your instructions with the 2.4.0.1 version, however, I can't find those drivers on the web (perhaps you have a link).

Thank you,
Ori


/20101125_RT3090_LinuxSTA_V2.4.0.2_WiFiBTCombo_RFKill_DPO/os/linux/../../common/rt_ate.c: In function ‘ATETxPwrHandler’:
/20101125_RT3090_LinuxSTA_V2.4.0.2_WiFiBTCombo_RFKill_DPO/os/linux/../../common/rt_ate.c:1813: error: ‘struct _RTMP_ADAPTER’ has no member named ‘TxPowerCtrl’
/20101125_RT3090_LinuxSTA_V2.4.0.2_WiFiBTCombo_RFKill_DPO/os/linux/../../common/rt_ate.c:1819: error: ‘pTxPowerTuningEntry’ undeclared (first use in this function)
/20101125_RT3090_LinuxSTA_V2.4.0.2_WiFiBTCombo_RFKill_DPO/os/linux/../../common/rt_ate.c:1819: error: (Each undeclared identifier is reported only once
/20101125_RT3090_LinuxSTA_V2.4.0.2_WiFiBTCombo_RFKill_DPO/os/linux/../../common/rt_ate.c:1819: error: for each function it appears in.)
/20101125_RT3090_LinuxSTA_V2.4.0.2_WiFiBTCombo_RFKill_DPO/os/linux/../../common/rt_ate.c:1819: error: ‘TxPowerTuningTable’ undeclared (first use in this function)
/20101125_RT3090_LinuxSTA_V2.4.0.2_WiFiBTCombo_RFKill_DPO/os/linux/../../common/rt_ate.c:1819: error: ‘struct _RTMP_ADAPTER’ has no member named ‘TxPowerCtrl’
/20101125_RT3090_LinuxSTA_V2.4.0.2_WiFiBTCombo_RFKill_DPO/os/linux/../../common/rt_ate.c:1819: error: ‘TX_POWER_TUNING_ENTRY_OFFSET’ undeclared (first use in this function)
/20101125_RT3090_LinuxSTA_V2.4.0.2_WiFiBTCombo_RFKill_DPO/os/linux/../../common/rt_ate.c:1820: error: ‘struct _RTMP_ADAPTER’ has no member named ‘TxPowerCtrl’
/20101125_RT3090_LinuxSTA_V2.4.0.2_WiFiBTCombo_RFKill_DPO/os/linux/../../common/rt_ate.c:1821: error: ‘struct _RTMP_ADAPTER’ has no member named ‘TxPowerCtrl’
/20101125_RT3090_LinuxSTA_V2.4.0.2_WiFiBTCombo_RFKill_DPO/os/linux/../../common/rt_ate.c:1827: error: ‘struct _RTMP_ADAPTER’ has no member named ‘TxPowerCtrl’
/20101125_RT3090_LinuxSTA_V2.4.0.2_WiFiBTCombo_RFKill_DPO/os/linux/../../common/rt_ate.c:1833: error: ‘TotalDeltaPower’ undeclared (first use in this function)
/20101125_RT3090_LinuxSTA_V2.4.0.2_WiFiBTCombo_RFKill_DPO/os/linux/../../common/rt_ate.c:1833: error: ‘struct _RTMP_ADAPTER’ has no member named ‘TxPowerCtrl’
/20101125_RT3090_LinuxSTA_V2.4.0.2_WiFiBTCombo_RFKill_DPO/os/linux/../../common/rt_ate.c:1839: error: ‘TxPwr’ undeclared (first use in this function)
/20101125_RT3090_LinuxSTA_V2.4.0.2_WiFiBTCombo_RFKill_DPO/os/linux/../../common/rt_ate.c:1882: error: ‘i’ undeclared (first use in this function)
/20101125_RT3090_LinuxSTA_V2.4.0.2_WiFiBTCombo_RFKill_DPO/os/linux/../../common/rt_ate.c:1886: error: ‘j’ undeclared (first use in this function)
/20101125_RT3090_LinuxSTA_V2.4.0.2_WiFiBTCombo_RFKill_DPO/os/linux/../../common/rt_ate.c:1888: error: ‘Value’ undeclared (first use in this function)
/20101125_RT3090_LinuxSTA_V2.4.0.2_WiFiBTCombo_RFKill_DPO/os/linux/../../common/rt_ate.c: In function ‘ATEAsicSwitchChannel’:
/20101125_RT3090_LinuxSTA_V2.4.0.2_WiFiBTCombo_RFKill_DPO/os/linux/../../common/rt_ate.c:4727: warning: unused variable ‘RFValue2’
/20101125_RT3090_LinuxSTA_V2.4.0.2_WiFiBTCombo_RFKill_DPO/os/linux/../../common/rt_ate.c:4722: warning: unused variable ‘RFRegTable’
/20101125_RT3090_LinuxSTA_V2.4.0.2_WiFiBTCombo_RFKill_DPO/os/linux/../../common/rt_ate.c:4721: warning: unused variable ‘R4’
/20101125_RT3090_LinuxSTA_V2.4.0.2_WiFiBTCombo_RFKill_DPO/os/linux/../../common/rt_ate.c:4721: warning: unused variable ‘R3’
/20101125_RT3090_LinuxSTA_V2.4.0.2_WiFiBTCombo_RFKill_DPO/os/linux/../../common/rt_ate.c:4721: warning: unused variable ‘R2’
make[2]: *** [/20101125_RT3090_LinuxSTA_V2.4.0.2_WiFiBTCombo_RFKill_DPO/os/linux/../../common/rt_ate.o] Error 1
make[1]: *** [_module_/20101125_RT3090_LinuxSTA_V2.4.0.2_WiFiBTCombo_RFKill_DPO/os/linux] Error 2
make: *** [LINUX] Error 2

---

### Post by Mindr on 2010-12-05
Yeah, same problem with 2.4.0.2, can't compile.

I'm sure someone in this topic has archive of 2.4.0.1 version on his HDD, so upload this please :)

rt2860 driver works ugly in my case (HP ProBook 4520s, Ubuntu 10.10 amd64).

---

### Post by archithcr on 2010-12-06
here's the link to the old 2.4.01 drivers.

[http://rapidshare.com/files/435249513/DPO_RT3390_LinuxSTA_V2.4.0.1_20100831.tgz](http://rapidshare.com/files/435249513/DPO_RT3390_LinuxSTA_V2.4.0.1_20100831.tgz)

hope this helps :)

---

### Post by Mindr on 2010-12-06
The filename says it's RT3390, not RT3090.

---

### Post by archithcr on 2010-12-06
hey,i installed the driver from the above file and it worked for me. give it a shot and see. it's normal to see warnings when you run the makefile command, it's only errors you have to worry about.

---

### Post by Mindr on 2010-12-06
Good, I will try this today. Thank you, archithcr.

Also, how's about disconnects? With rt2860 driver my laptop loses connection every few minutes. With rt2800, which was enabled by default and is now blacklisted, it didn't connect to any wireless network at all.

---

### Post by Mindr on 2010-12-06
Ok. This works just as good as Windows driver and also enables the N-standard. And there's no disconnects.

Big thanks!

---

### Post by Mindr on 2010-12-07
I was wrong, it works no better than if i just add rt2800pci in the blacklist.

Did somebody had problems with connection stability?

---

### Post by lanceafa on 2010-12-08
THX a lot!!! this fix worked in a HP dv6 with linux mint 10 
:)

---

### Post by Mindr on 2010-12-10
I've just compiled RT3090 2.4.0.2 (without HAS_ATE option enables), added all of rt**** modules I found in my system to the blacklist and added rt3090sta to /etc/modules (just in case).

It seems this module actually loads (lsmod | grep rt), but it doesn't work, network manager just tries to connect infinitely.

In my tty1 i'm getting the following messages:
Tx Power, BBP R49=e, TssiRef=11, TxAgcStep=1, step = +0

How to get this thing work properly?

---

### Post by Mindr on 2010-12-10
Something from dmesg:
```
[  865.625672] lo: Disabled Privacy Extensions
[  901.277332] ===>rt_ioctl_giwscan. 8(8) BSS returned, data->length = 1525
[  941.258997] ===>rt_ioctl_giwscan. 5(5) BSS returned, data->length = 922
[  945.946740] lo: Disabled Privacy Extensions
[ 1001.231093] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 597
[ 1081.191643] ===>rt_ioctl_giwscan. 6(6) BSS returned, data->length = 1209
[ 1138.273493] ===>rt_ioctl_giwscan. 5(5) BSS returned, data->length = 979
[ 1148.276951] ===>rt_ioctl_giwscan. 5(5) BSS returned, data->length = 979
[ 1148.436302] rt28xx_close call RT28xxPciAsicRadioOff fail!
[ 1148.444510] RX DESC ffff8800a58e5000  size = 2048
[ 1148.444691] <-- RTMPAllocTxRxRingMemory, Status=0
[ 1148.447927] 1. Phy Mode = 0
[ 1148.447930] 2. Phy Mode = 0
[ 1148.447933] NVM is Efuse and its size =2d[2d0-2fc] 
[ 1148.449897] 3. Phy Mode = 0
[ 1148.452405] MCS Set = 00 00 00 00 00
[ 1148.475815] <==== rt28xx_init, Status=0
[ 1148.475921] 0x1300 = 000a4200
[ 1148.475947]  AUX_CTRL = 0x                            1c42
[ 1148.475954]  Read AUX_CTRL = 0x1c42
[ 1148.475958]  Write AUX_CTRL = 0x1c42
[ 1148.475963]  OSC_CTRL = 0x3ff11
[ 1148.476117] ====> rt30xx Read PowerLevelMode =  0x3.
[ 1148.476120] ====> rt30xx F Write 0x83 Command = 0x3.
[ 1158.277101] ===>rt_ioctl_giwscan. 10(10) BSS returned, data->length = 1891
[ 1158.277282] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=1)
[ 1159.007267] wlan0: no IPv6 routers present
[ 1181.133865] ===>rt_ioctl_giwscan. 7(7) BSS returned, data->length = 1303
```

It's with rt2860sta driver.

---

### Post by miguecomputonto on 2010-12-18
This (following the instructions in the first post of this thread) solves the shutdown / suspend / hibernate problem in the sony VAIO  VPCM120AL netbook. 

I appreciate this help, now the laptop does shutdown without the need of sliding and holding the power button which was very annoying.

---

### Post by Mindr on 2011-01-10
I did install a newer kernel from Natty (2.6.27-12), and built-in rt2860sta driver works good, no connection loses in past three days.

---

### Post by luberfly on 2011-01-26
Hello friends, someone can help me with the compiling of the driver?

I have some problems.

Who can help me to translate the readme file into the Ubuntu version?

It is not easy for me to compile the file.... sometime the readme file make a refernce to rt2860sta sometimes to rt3090sta and I do not understand anithing.

Best regards

Luca

---

### Post by dbsjunk on 2011-01-27
Has anyone verified that the card achieves 802.11n speeds with these solutions? I have my Ralink 3090 working fine in 10.10 with both the default drivers and the ones from the Ralink site, but I am unable to get more than 3MB/s (802.11g speeds) despite the fact that my MacBook pro sitting in the same location can get 9MB/s to the same router.

---

### Post by sagaciousL on 2011-01-29
> **rtomakov said:**
> Download new driver from ralink support page (version 2.4.1) and unpack it somewhere (I did it in my Download folder). Read README_STA_PCI file -  find file config.mk in os/linux folder, open it with gedit and edit lines:
- HAS_ATE=**y** (originally was **n**)
- HAS_WPA_SUPPLICANT=**y **(originally was **n**)
- HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=**y **(originally was **n**) and
- HAS_ANTENNA_DIVERSITY_SUPPORT=**y** originally was **n**)

Now, before compile, install via synaptic these packages: build-essential, devscripts and cdbs.

Enter DPO_... folder from terminal and do **sudo make**, and after make finishes (without errors, ignore warnings) do **sudo make install. **That is it, but it is not over yet. Now open /etc/modprobe.d/blacklist.conf (as root) and add at the end: blacklist rt2800pci. Also open (as root) file /etc/modules and add: rt3390sta. 
Now, reboot. That should work. Write some feedback.

 
This worked perfectly for me as well.  You ARE a genius!      Running a newer (as of today) HP dv7-4170 with 64-bit architecture, could not get the wireless to work with Ubuntu 10.10 (documentation says 11.04).  Tried several solutions from other help threads -- this one did the job.  Many thanks -- cheers!

---

### Post by luberfly on 2011-02-10
Hi friends,
I have done all the inscruction avove (see @rtomakov) with ubuntu 10.10 64 bit firt then 10.10 32bit and I have always the some problems.
When I start my ubuntu there is a message "RT2860 is already loaded" an then my wifi card doesn't work.
With ubuntu 10.04 32bit everithing work fine!

Please, comeone can help me?

Best Regards

Luca

... here the result:

lsmod | fgrep rt

> parport_pc             26378  0 
rt2860sta             504703  1 
crc_ccitt               1351  1 rt2860sta
agpgart                32075  2 fglrx,intel_agp
parport                31492  3 parport_pc,ppdev,lp


---

### Post by Joshun on 2011-02-17
> Enter DPO_... folder from terminal and do sudo make, and after make finishes (without errors, ignore warnings) do sudo make install. That is it, but it is not over yet. Now open /etc/modprobe.d/blacklist.conf (as root) and add at the end: blacklist rt2800pci. Also open (as root) file /etc/modules and add: rt3390sta.'rt3390sta' - that is a typo - should be rt3090sta. Its an easy mistake to make but makes a huge difference, as rt2860sta, included in the kernel by default, is loaded instead of ralink's official rt3090sta. Also add rt2860sta to the blacklist as this loads when not needed.:popcorn:

---

### Post by Joshun on 2011-02-17
@_luberfly:_ Try adding **blacklist rt2860sta** and **blacklist rt2800pci**, to /etc/modprobe.d/blacklist.conf. Then add **rt3090sta** to the end of /etc/modules.

---

### Post by VaiPhile on 2011-02-21
Thanks for this.  I installed a 10.10 on a second partition on my ProBook and HP only supports Suse, so I have been trying to wrangle this driver to work.  Following these instructions worked no problem, and it was good to get the dev and make files on there as this is a new install and I haven't really built much on it.  Thanks again!

---

### Post by n3mo.wolf on 2011-03-07
Hello.
I bought HP Probook 4320s last week and I'm pretty happy with it, but on my Ubuntu 10.10 the default wi-fi driver disconnect a lot, so i have installed this one ( 2.4.0.4 from RT site ) and everything looks good.... Until i tried to download a big file - like torrent or something like this - It starts, my speed raise to ~2mb/s and then my internet stops ... speed drop to 0b/s I can load a webpage.... just stops and lose connection. If i restart the card ( on/off button from keyboard ) it connects again and everything works until i try to download something....
Can anyone help me?

p.s.
Sorry about my bad English.

---

### Post by Mindr on 2011-03-08
I solved this problem installing the new kernel 2.6.37 from 11.04.

You need these 3 packages:
linux-headers-2.6.37-12 ([all archs]("http://launchpadlibrarian.net/61680250/linux-headers-2.6.37-12_2.6.37-12.26_all.deb"))
linux-headers-2.6.37-12-generic ([i386]("http://launchpadlibrarian.net/61680254/linux-headers-2.6.37-12-generic_2.6.37-12.26_i386.deb") or [amd64]("http://launchpadlibrarian.net/61707321/linux-headers-2.6.37-12-generic_2.6.37-12.26_amd64.deb"))
linux-image-2.6.37-12-generic ([i386]("http://launchpadlibrarian.net/61680252/linux-image-2.6.37-12-generic_2.6.37-12.26_i386.deb") or [amd64]("http://launchpadlibrarian.net/61707320/linux-image-2.6.37-12-generic_2.6.37-12.26_amd64.deb"))

You also need to blacklist the rt2800pci and add rt2860sta into /etc/modules (but I have some doubts if this ttep is necessarily).

---

### Post by n3mo.wolf on 2011-03-08
Thank you for your fast answer, but where did you find kernel images, because I need pae enabled - I have 8GB of ram.

---

### Post by Mindr on 2011-03-08
Originally I found it at [http://packages.ubuntu.com/](http://packages.ubuntu.com/) , but since they updated natty's kernel to 2.6.38 RC, which is not working properly for me (suspend fails), you'll have to search it on [https://launchpad.net/ubuntu/natty/](https://launchpad.net/ubuntu/natty/) , and this is kinda tricky.

Which specific kernel are you using? In 10.10 I've only found ec2, generic, server and virtual... no packages named "pae".

---

### Post by Mindr on 2011-03-08
8 GB &#8212; why PAE, not amd64?

---

### Post by n3mo.wolf on 2011-03-08
I'm using 2.6.35-27-generic-pae and wasn't able to find pae image for 2.6.37-12 , but I've got headers for 2.6.37-12 ... Can I compile my own kernel image and headers, etc ?


I'm not sure 64bit is a good idea, tried it a year ago on my PC and it wasn't smooth.

---

### Post by Mindr on 2011-03-08
Ok, here's 2.6.37-generic-pae:
[http://launchpadlibrarian.net/61680255/linux-image-2.6.37-12-generic-pae_2.6.37-12.26_i386.deb](http://launchpadlibrarian.net/61680255/linux-image-2.6.37-12-generic-pae_2.6.37-12.26_i386.deb)
[http://launchpadlibrarian.net/61680256/linux-headers-2.6.37-12-generic-pae_2.6.37-12.26_i386.deb](http://launchpadlibrarian.net/61680256/linux-headers-2.6.37-12-generic-pae_2.6.37-12.26_i386.deb)
[http://launchpadlibrarian.net/61680250/linux-headers-2.6.37-12_2.6.37-12.26_all.deb](http://launchpadlibrarian.net/61680250/linux-headers-2.6.37-12_2.6.37-12.26_all.deb)

Of course you can build it from the source if you want to. Kernel sources:
[http://launchpadlibrarian.net/61680245/linux-source-2.6.37_2.6.37-12.26_all.deb](http://launchpadlibrarian.net/61680245/linux-source-2.6.37_2.6.37-12.26_all.deb)

---

### Post by Mindr on 2011-03-08
I'm using 64bit version on my 4520s and it works just fine. There was a few issues with wi-fi and touchpad, but I think with i386 I'll encounter same problems.

---

### Post by n3mo.wolf on 2011-03-08
I installed this kernel, but I has a lot of issues with it. First - my video drivers doesn't work, my touch pad doesn't work as expected and insmod and modprobe said that rt3090sta.ko is wrong module format....
Maybe I'll wait until 11.04 ...

---

### Post by Mindr on 2011-03-08
1. What videocard is installed in your laptop?
2. How did you get touchpad working with Ubuntu? Are using 10.04 or 10.10?
3. You may need to blacklist both rt2800pci and rt3090sta drivers and use rt2860sta instead (which I'm using).

---

### Post by n3mo.wolf on 2011-03-08
> **Mindr said:**
> 1. What videocard is installed in your laptop?
2. How did you get touchpad working with Ubuntu? Are using 10.04 or 10.10?
3. You may need to blacklist both rt2800pci and rt3090sta drivers and use rt2860sta instead (which I'm using).
1. My video card is ATI-AMD Mobility Radeon HD 4350.
2. I'm using ubuntu 10.10 ( installed it with macbuntu theme and packages ) and I use synaptic driver to get basic multi touch + two fingers gestures.
3. The main idea is not to use rt2800pci and rt2860sta drivers, because they used to disconnect from networks randomly and doesn't show information about straight of wi-fi signal. Also with rt2860 the LED on turn on/off button for wireless is blinking like mad.

Short after I installed Ubuntu 10.10 it found ati drivers and installed them. I have been updating my kernel three times and never have such problems as with version 2.6.37-12.

---

### Post by Mindr on 2011-03-08
2. Maybe you should reinstall that driver?
3. The point of installing 2.6.37 is that it contains better rt2860sta driver and doesn't lose wi-fi like every five minutes.

---

### Post by n3mo.wolf on 2011-03-08
> **Mindr said:**
> 2. Maybe you should reinstall that driver?
3. The point of installing 2.6.37 is that it contains better rt2860sta driver and doesn't lose wi-fi like every five minutes.

Ubuntu doesn't find my video cart in Additional Drivers , but i can try other way to reinstall it. 
Back to main topic:
Can you see straight of wi-fi signal ? Can you turn on/off your wireless cart from the keyboard?

---

### Post by Mindr on 2011-03-08
Video… that's kinda strange, I'm using open source drivers which were enabled by default.

Yes, I can see signal straight and can turn off/on wi-fi from the keyboard.

---

### Post by n3mo.wolf on 2011-03-08
Strange but after installing 2.6.37-12 kernel it comes with new rt2680sta module, so i just loaded it when using 2.6.35-27 . Turning on/off wireless with keyboard works just fine, but i wasn't able to see my network... I see some other networks near me, but can't find my own. Now i'm back to rt3090sta driver and still trying to fix my issue with bigger files.
Thanks after all.

---

### Post by xmapact on 2011-03-13
HP Compaq Presario CQ 56 with Ralink 3090 wi-fi controller works, thx to rtomakov.
:o

---

### Post by graysonc on 2011-03-14
I have rt3090 working on Kubuntu 10.10 64. I also had the same problems with "RT2860 is already loaded". I resolved this by blacklisting two previously compiled drivers rt2860sta and RT3090sta. see my [notes ]("http://sussexcomputerworks.co.uk/computer-services-and-web-design/tech-stuff/43-linux/77-ubuntu-1010-64bit-ralink3090.html")for further details. Oddly enough the new driver seems to be called RT3390STA

---

### Post by diafygi on 2011-03-18
> **dbsjunk said:**
> Has anyone verified that the card achieves 802.11n speeds with these solutions? I have my Ralink 3090 working fine in 10.10 with both the default drivers and the ones from the Ralink site, but I am unable to get more than 3MB/s (802.11g speeds) despite the fact that my MacBook pro sitting in the same location can get 9MB/s to the same router.

I am having the same issue. I am able to get 802.11n speeds on my Win7 partition, but not on Ubuntu. Has anyone been able to get 802.11n speeds on Ubuntu with the RT3090 hardware?

---

### Post by werzer on 2011-03-30
I have patched sources of drivers, but have got error: 
 > 
 hpwork tmp # modprobe rt5390sta 
hpwork tmp # dmesg 
[ 1401.657903] rt5390 0000:02:00.0: setting latency timer to 64 
[ 1401.658399] <-- RTMPAllocAdapterBlock, Status=0 
[ 1402.619085] KH: Use High Memory for Beacon 
[ 1402.623111] <-- RTMPAllocTxRxRingMemory, Status=0 
[ 1402.626559] ERROR!!! RTMPReadParametersHook failed, Status[=0x00000001] 
[ 1402.654646] KH: Use High Memory for Beacon 
[ 1402.658664] <-- RTMPAllocTxRxRingMemory, Status=0 
[ 1402.662275] ERROR!!! RTMPReadParametersHook failed, Status[=0x00000001] 
[ 1402.742960] KH: Use High Memory for Beacon 
[ 1402.747051] <-- RTMPAllocTxRxRingMemory, Status=0 
[ 1402.750512] ERROR!!! RTMPReadParametersHook failed, Status[=0x00000001] 
 

> 
hpwork ~ # lspci  | grep -i ralink
02:00.0 Network controller: RaLink Device 539f

> 
hpwork ~ # uname -a
Linux hpwork 2.6.36-gentoo-r8 #1 SMP Mon Mar 28 22:37:09 MSD 2011 x86_64 AMD E-350 Processor AuthenticAMD GNU/Linux


 How to solve this problem?

---

### Post by kalex on 2011-03-30
Thanks! That worked fine for me too.

---

### Post by Sven6210 on 2011-05-09
You can have a look on my how-to at [http://ubuntuforums.org/showthread.p...ghlight=RT3090]("http://ubuntuforums.org/showthread.php?t=1476007&highlight=RT3090")

It also works for the RaLink RT3090, you just need to replace the "[FONT=Verdana, sans-serif]RT2860" with "RT3090".

Disadvantage of this procedure:
[/FONT]
[LIST]
[*]You need to recompile the driver each time you make a  major kernel-update. The backports I have tried so far did not work very  well
[/LIST]
Advantage of this procedure:

[LIST]
[*]On my EeeBox B202 and my friends EeePC 1015 P it works very well and reliable
[/LIST]

The manual should also work for newer releases of Ubuntu, I am still running Ubuntu 10.04 LTS on my systems.

Good luck

Sven

---

### Post by sero on 2011-06-01
> **rtomakov said:**
> Download new driver from ralink support page (version 2.4.1) and unpack it somewhere (I did it in my Download folder). Read README_STA_PCI file -  find file config.mk in os/linux folder, open it with gedit and edit lines:
- HAS_ATE=**y** (originally was **n**)
- HAS_WPA_SUPPLICANT=**y **(originally was **n**)
- HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=**y **(originally was **n**) and
- HAS_ANTENNA_DIVERSITY_SUPPORT=**y** originally was **n**)

Now, before compile, install via synaptic these packages: build-essential, devscripts and cdbs.

Enter DPO_... folder from terminal and do **sudo make**, and after make finishes (without errors, ignore warnings) do **sudo make install. **That is it, but it is not over yet. Now open /etc/modprobe.d/blacklist.conf (as root) and add at the end: blacklist rt2800pci. Also open (as root) file /etc/modules and add: rt3390sta. 
Now, reboot. That should work. Write some feedback.
Worked for me! Although I did not need to compile the driver again in 11.04, just the blacklisting is enough.

---

### Post by ogfx on 2011-06-10
Hi Guys...I tried everything above exactly as described but to no avail....really sad dat my wifi & bluetooth dont work well

:(

Need ur kind assistance!!!

---

### Post by bugslayr on 2011-06-11
Hi ogfx,
you should reply what kind of hardware you use: "lspci -vv | less" does the trick. Go to the section describing your wireless card. It'll tell you what drivers are available for the card and which one is loaded. Post that section.
Also mention which type of computer you use - hardware may vary ...
What version of Linux are you using? Ubuntu 10.10, as mentioned in the subject? 11.04? Or something different?

quote >> Try adding **blacklist rt2860sta** and **blacklist rt2800pci**, to /etc/modprobe.d/blacklist.conf. Then add **rt3090sta** to the end of /etc/modules.

For me blacklisting **rt2800pci **helped. But you may have to blacklist **rt2860sta **too. On one netbook I had to add 4 drivers to the blacklist ... (it's currently not here, so I cannot check now, but I can post the entries if you need them).

Good luck!
    bugslayr

---

### Post by Frank.Heinen on 2011-07-14
Hi all,

Tnx for all this info but for me this does not work still. Note: I am a NOOB!

I have Ubuntu 11.04.
Laptop HP Probook 4720s XX816EA (with 8GB)

Now what I did:
1 - added the PPA [https://launchpad.net/~markus-tisoft/+archive/rt3090](https://launchpad.net/~markus-tisoft/+archive/rt3090)
2 - added the following to /etc/modprobe.d/blacklist.conf
# Blacklist conflicting RaLink driver modules
#blacklist rt2800pci
#blacklist rt2800lib
#blacklist rt2x00usb
#blacklist rt2x00pci
#blacklist rt2x00lib
#blacklist rt2860sta
3 - Tried adding rt3090sta to the /etc/modules

It seems to not load the rt2800 module but it does not load the rt3090 module.

Reading this tread I tried:

 lspci | egrep -i '(ether|network|wire)'
44:00.0 Network controller: Ralink corp. RT3090 Wireless 802.11n 1T/1R PCIe
45:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)

and:

frank@frank-HP-ProBook-4720s:~$ modinfo rt3090sta
filename:       /lib/modules/2.6.38-10-generic-pae/updates/dkms/rt3090sta.ko
license:        GPL
version:        2.4.0.4
srcversion:     9A7B078F56A0351E1A34B06
alias:          pci:v00001814d00003092sv*sd*bc*sc*i*
alias:          pci:v00001814d00003091sv*sd*bc*sc*i*
alias:          pci:v00001814d00003090sv*sd*bc*sc*i*
depends:        cfg80211
vermagic:       2.6.38-8-generic-pae SMP mod_unload modversions 686 
parm:           mac:rt28xx: wireless mac addr (charp)

and:
frank@frank-HP-ProBook-4720s:~$ sudo modprobe rt3090sta
FATAL: Error inserting rt3090sta (/lib/modules/2.6.38-10-generic-pae/updates/dkms/rt3090sta.ko): Invalid module format

Not sure this gives any idea about the cause of the problem
but I hope if someone can help me a little here.

---

### Post by Frank.Heinen on 2011-07-18
Okay, 1 step further, it seems that I updated the kernel just after I installed the RT3090 module. Now it seems to be installed good.
But still not there it seems. The wireless connection information tells me that it uses the RT2860 driver. Again not sure if this is the same as the RT2860STA driver. But I will fiddle something more. 

/me thinks that I will be a Linux guru (someday in 2035) ;)

---

### Post by bugslayr on 2011-07-19
Hello Frank,

you are perfectly right, rt2860sta and rt3090sta are the same module, exactly speaking, rt3090sta is an alias for rt2860sta.
You may verify with: 
modinfo rt2860sta

I am having the same notebook (HP Probook 4720s; )I did not install markus' ppa and went with the kernel that came with Natty Narwhal.
The only driver I blacklisted is rt2800pci

I would try without markus' driver ... it worked with me.

I hope I could help! Please let me know!

Cheers
     Martin

---

### Post by Kraid1 on 2011-07-28
Hello!

I have successfully installed the driver following rtamakov's description. Available networks showed up. But, when I turned on the notebook after several days I saw the wifi was disconnected. I looked in System -> Administration -> Additional drivers - it shows that the driver is active but not currently in use. What can I do?

---

### Post by mbbrady on 2011-08-03
Hi, 

I'm trying to install the driver for Ralink 5390 using the instructions below. I've made the changes to the config.mk file, but when I attempt to use the make command I get a message saying that nothing needs to be done to that file. 

Why would I get this message if I have made changes to the config.mk file?

Any guidance will be greatly appreciated.

---

### Post by Failbot on 2011-08-11
After messing around with the rt3090 ppa drivers and still having the "device not ready" problem after sleep/suspend I grabbed the 3.0.1 kernel from [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/) 
(remove all entries from blacklist.conf if you've added them, the driver is now integrated into rt2800pci)

Initial testing shows shutdown/restart OK. Reconnect after sleep/suspend OK.

System is a MSI Wind L1350D with RaLink RT3090 Ubuntu 10.10 32 bit.

:D

---

### Post by Frank.Heinen on 2011-08-17
@bugslayr

Thanks for your input, I was on holiday.
modinfo gives:

modinfo rt2860sta
filename:       /lib/modules/2.6.38-10-generic-pae/kernel/drivers/staging/rt2860/rt2860sta.ko
version:        2.1.0.0
alias:          rt3090sta
license:        GPL
description:    RT2860/RT3090 Wireless Lan Linux Driver
author:         Jett Chen <jett_chen@ralinktech.com>
firmware:       rt3090.bin
firmware:       rt2860.bin
srcversion:     C22EE7282F9A519D7E9A764
alias:          pci:v00001814d00003092sv*sd*bc*sc*i*
alias:          pci:v00001814d00003091sv*sd*bc*sc*i*
alias:          pci:v00001814d00003090sv*sd*bc*sc*i*
alias:          pci:v00001432d00007768sv*sd*bc*sc*i*
alias:          pci:v00001432d00007748sv*sd*bc*sc*i*
alias:          pci:v00001432d00007738sv*sd*bc*sc*i*
alias:          pci:v00001432d00007727sv*sd*bc*sc*i*
alias:          pci:v00001432d00007758sv*sd*bc*sc*i*
alias:          pci:v00001432d00007728sv*sd*bc*sc*i*
alias:          pci:v00001432d00007708sv*sd*bc*sc*i*
alias:          pci:v00001A3Bd00001059sv*sd*bc*sc*i*
alias:          pci:v00001814d00000781sv*sd*bc*sc*i*
alias:          pci:v00001814d00000701sv*sd*bc*sc*i*
alias:          pci:v00001814d00000681sv*sd*bc*sc*i*
alias:          pci:v00001814d00000601sv*sd*bc*sc*i*
depends:        crc-ccitt
staging:        Y
vermagic:       2.6.38-10-generic-pae SMP mod_unload modversions 686 
parm:           mac:rt28xx: wireless mac addr (charp)

I will now try to disabling/uninstalling it and see if this works. This module (rt2860sta from Markus) seems to work better but it is still far from stable. Loosing WPA connections regular and only getting connection after this by disabling network and enabling it. WEP encrypted networks seem totally not possible to connect to (I have only 1 known to connect to so not much test material).

I will report if disabling works better.

---

### Post by squidink on 2011-08-30
> **rtomakov said:**
> Download new driver from ralink support page (version 2.4.1) and unpack it somewhere (I did it in my Download folder). Read README_STA_PCI file -  find file config.mk in os/linux folder, open it with gedit and edit lines:
- HAS_ATE=**y** (originally was **n**)
- HAS_WPA_SUPPLICANT=**y **(originally was **n**)
- HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=**y **(originally was **n**) and
- HAS_ANTENNA_DIVERSITY_SUPPORT=**y** originally was **n**)

Now, before compile, install via synaptic these packages: build-essential, devscripts and cdbs.

Enter DPO_... folder from terminal and do **sudo make**, and after make finishes (without errors, ignore warnings) do **sudo make install. **That is it, but it is not over yet. Now open /etc/modprobe.d/blacklist.conf (as root) and add at the end: blacklist rt2800pci. Also open (as root) file /etc/modules and add: rt3390sta. 
Now, reboot. That should work. Write some feedback.
Another thank you, rtomakov! I haven't had that much fun since my old machine fitted with Windows 98 and I'm new to this Ubuntu/Linux from yesterday! :)

My wireless is up and running seamlessly so far and no flashing wifi button on my 4520s Probook. I will admit that the quickly flashing violet/orange wifi button did look really cool for a while with the newly installed Ubuntu desktop. That is until I realized that it meant that the wifi was, in fact, NOT working...

---

### Post by SEEDster on 2011-11-02
THANK YOU SO MUCH!!!  You are my savior!!!!  I can't tell you how much time I have spent trying to resolved them problem only to have given up at the end and resorted to cat5 cable instead.  This is absolutely the best guild I have seen.  Thank you so much :-)

---

### Post by tulipán on 2011-11-03
hi, I cannot thank you enough! i absolutely have no clue what i've just done, but kinda followed your instructions, and i am posting this reply without my ethernet cable plugged in (xubuntu 10.10, hp G62). it felt like following Burda instructions in the good ol'days, when sawing stuff at home -- you had no idea what you were doing but sticking to the intructions got you end up with a lined blazer. or a wireless connection. I love you Rtomakov! :)

---

### Post by icblu on 2011-11-27
I'm a bit late to the party but have to thank you for this step by step that had my wireless up an running in short order.

I spent most of yesterday trying all sorts of workarounds and config solutions from the web and  ubuntu forums. This morning I decided on a fresh install in the hopes of getting my wifi and HDMI sound working. In the bright light of day I found this post and after the few short minutes of reading, downloading and editing I was on my way to making the install.

I had wifi running almost immediately and it hasn't disconnected on its own yet (4 hours), but does does disconnect and reconnect as it should. 

Many thanks -- you are a genius!

~~~

PS anyone still struggling with the second problem when installing linux on an Acer Revo -- no HDMI sound --  the fix for mine was simply to unmute S/PIDF1 using alsamixer -- launch it using the terminal and put mm instead of 00 in the  S/PIDF1 column

---

