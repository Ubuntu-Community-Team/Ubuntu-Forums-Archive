---
title: "Wireless card stopped working after 10.04 Update."
date: 2011-05-11
forum: Networking &amp; Wireless
---

### Post by JoeNixx on 2011-05-11
Good day to you all ! Glad to be a new member of the forum.

Well, I have an issue with my wireless card in Ubuntu 10.04, my wireless card model is:
the D-Link WIRELESS N 150 DESKTOP ADAPTER DWA-525. I was already successful getting it to work by using the RaLink driver suggested [here]("https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsDlink") and following the instructions in their readme.

But after a system update I performed through Update Manager (in which I guess the kernel was updated), the device stopped working completely. The wireless icon remains(in the top panel), but it displays a red exclamation mark next to it. :confused:

Could somebody please help me? I'm a very concerned by this issue, I need to get back online to resume my work :(

Thanks in advance for all your kind help.

J

---

### Post by mikewhatever on 2011-05-11
Check the README or the release notes again, does the driver support the currently used kernel version? If that's not the case, you may need to go back and happily use 10.04 for another two years, of search for the updated driver that does support more recent kernels.

---

### Post by JoeNixx on 2011-05-11
Hello there !, Thanks for the reply... 
I didn't update to 10.10.
I'm still using 10.04.

As far kernel version goes...

```
jose@jarvis:~$ uname -r
2.6.32-31-generic-pae
```

Here's what the documentation says about the Kernel support:

[B]Supporting Kernel:
===================
linux kernel 2.4 and 2.6 series. 
Tested in Redhat 7.3 or later.[/B]

So, Am I still ok? I really not quite clear on what can I do...

Thank you very much in advance.

J

---

### Post by mikewhatever on 2011-05-11
Have you reinstall the wireless driver after the kernel update? You have to do it for each new kernel.

---

### Post by JoeNixx on 2011-05-11
Hello,

Do you mean If I have compiled the driver all over again, after the update? 
if that is waht you're asking, then Yes I have. Actually I've done many things at this point to get it back to work, but so far without any success whatsoever. I don't know what's the status at this point. :(

Thanks for the reply.

---

### Post by mikewhatever on 2011-05-11
Strange. Did it compile without errors?

---

### Post by JoeNixx on 2011-05-11
I'd say it ran without problems, here are the 2 main steps for your consideration:


SUDO MAKE
-------------------------------------------------------------------------------------------------------
```
jose@jarvis:~/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217$ sudo make
make -C tools
make[1]: Entering directory `/home/jose/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/jose/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/tools'
/home/jose/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/tools/bin2h
cp -f os/linux/Makefile.6 /home/jose/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/Makefile
make -C /lib/modules/2.6.32-31-generic-pae/build SUBDIRS=/home/jose/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-31-generic-pae'
  CC [M]  /home/jose/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/rtmp_mcu.o
  LD [M]  /home/jose/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/rt3562sta.o
  Building modules, stage 2.
  MODPOST 1 modules
WARNING: modpost: missing MODULE_LICENSE() in /home/jose/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/rt3562sta.o
see include/linux/module.h for more information
  LD [M]  /home/jose/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/rt3562sta.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-31-generic-pae'
cp -f /home/jose/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/rt3562sta.ko /tftpboot
```

SUDO MAKE INSTALL
------------------------------------------------------------------------------------------------------
```
jose@jarvis:~/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217$ sudo make install
make -C /home/jose/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux -f Makefile.6 install
mkdir: cannot create directory `/etc/Wireless': File exists
make[1]: Entering directory `/home/jose/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux'
rm -rf /etc/Wireless/RT2860STA
mkdir /etc/Wireless/RT2860STA
cp /home/jose/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/RT2860STA.dat /etc/Wireless/RT2860STA/.
install -d /lib/modules/2.6.32-31-generic-pae/kernel/drivers/net/wireless/
install -m 644 -c rt3562sta.ko /lib/modules/2.6.32-31-generic-pae/kernel/drivers/net/wireless/
/sbin/depmod -a 2.6.32-31-generic-pae
make[1]: Leaving directory `/home/jose/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux'
```

I'm by no means senseless by making you read the whole text, but I'm no linux expert, and the only way to know If everything went ok, is If someone else who knows more tells me. 

Please let me know what you think, or if you need any further information.

Thank you !

---

### Post by mikewhatever on 2011-05-11
That looks ok as far as I can see. Can you check if the module (presumably rt3562sta) is loaded with 'lsmod | grep 3562'.

---

### Post by JoeNixx on 2011-05-11
Sure, Here you go, sir...

```
jose@jarvis:/$ lsmod | grep 3562
rt3562sta             908306  1 
```

Thanks, once more.


Note. After Reboot the same command outputs nothing at all.

---

### Post by mikewhatever on 2011-05-11
Really wish I knew what the problem was, but I don't. :confused: Luckily, there are better experts here then myself, so let's wait and see.

---

### Post by JoeNixx on 2011-05-11
:shock:

Uh-Oh.

I have a question for you. Can you tell me if the driver is the correct one for my wireless card ?

Thanks, and Is there a way in these forums to request help from additional experts ?

I'm really worried about this.

Thank you for your time, sir.

---

### Post by as2000 on 2011-05-11
Try terminal command lsusb for usb device or lspci for pci device. It will reveal what type of card you have and can help determine the driver...

---

### Post by JoeNixx on 2011-05-11
Hi! 

ALthough I can't make much out of it, here's the output for lspci:


```
jose@jarvis:~$ lspci
00:00.0 Host bridge: Intel Corporation 4 Series Chipset DRAM Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation 4 Series Chipset PCI Express Root Port (rev 03)
00:02.0 VGA compatible controller: Intel Corporation 4 Series Chipset Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 01)
00:1d.0 USB Controller: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation N10/ICH7 Family SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 01)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
04:04.0 Network controller: RaLink Device 3060
```

I hope you can help me figure out what this means.

Thank you very much !

---

### Post by as2000 on 2011-05-11
Look near the bottom of the readout. Line 3:00 I think. That is your device. Line 4:00 could be your wireless device

---

### Post by JoeNixx on 2011-05-11
Ok, I'm truly lost because according to this [list]("https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsDlink"). I'm using the correct Driver package, But... as you can see:
[IMG]http://farm4.static.flickr.com/3345/5710500439_90047253fd.jpg[/IMG]

In the driver column the driver name it's the rt2860. **Not the rt3562**, which is the one I have now currently active. 

So, I don't really know If I'm trying to get my device to work with *the correct driver at this point*. I wish someone could clarify this for me, I'm really worried. :sad

PS. rt3562 is the driver 'I'm getting' after compilation (with new kernel) - however, this is my humble guess only.

---

### Post by chili555 on 2011-05-11
Let's see:```
lspci -nn
```The pci.id will tell us a lot. Also run and post:```
sudo modprobe rt3562sta
dmesg | grep -e rt2 -e rt3
```

---

### Post by JoeNixx on 2011-05-11
HELLO SIR ! Glad to see you HERE ! THANK YOU !

Let's begin with the outputs..

```
jose@jarvis:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation 4 Series Chipset DRAM Controller [8086:2e30] (rev 03)
00:01.0 PCI bridge [0604]: Intel Corporation 4 Series Chipset PCI Express Root Port [8086:2e31] (rev 03)
00:02.0 VGA compatible controller [0300]: Intel Corporation 4 Series Chipset Integrated Graphics Controller [8086:2e32] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation N10/ICH 7 Family High Definition Audio Controller [8086:27d8] (rev 01)
00:1c.0 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 1 [8086:27d0] (rev 01)
00:1c.1 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 2 [8086:27d2] (rev 01)
00:1d.0 USB Controller [0c03]: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 [8086:27c8] (rev 01)
00:1d.1 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 [8086:27c9] (rev 01)
00:1d.2 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 [8086:27ca] (rev 01)
00:1d.3 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 [8086:27cb] (rev 01)
00:1d.7 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller [8086:27cc] (rev 01)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev e1)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge [8086:27b8] (rev 01)
00:1f.2 IDE interface [0101]: Intel Corporation N10/ICH7 Family SATA IDE Controller [8086:27c0] (rev 01)
00:1f.3 SMBus [0c05]: Intel Corporation N10/ICH 7 Family SMBus Controller [8086:27da] (rev 01)
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 02)
04:04.0 Network controller [0280]: RaLink Device [1814:3060]
```

```
jose@jarvis:~$ sudo modprobe rt3562sta
FATAL: Error inserting rt3562sta (/lib/modules/2.6.32-31-generic-pae/kernel/drivers/net/wireless/rt3562sta.ko): Device or resource busy
```

```
jose@jarvis:~$ dmesg | grep -e rt2 -e rt3
[    7.028097] rt2860sta: module is from the staging directory, the quality is unknown, you have been warned.
[    7.120505] rt3562sta: module license 'unspecified' taints kernel.
[    7.125917] Error: Driver 'rt2860' is already registered, aborting...
[ 5829.005937] Error: Driver 'rt2860' is already registered, aborting...
[ 5845.642592] Error: Driver 'rt2860' is already registered, aborting...
[ 5866.641039] Error: Driver 'rt2860' is already registered, aborting...
```

Let me know what you think, 

Thank you ! I'm so happy for you having showed up :D

Sincerely,

---

### Post by chili555 on 2011-05-11
I think you have too many drivers loading. Let's see:```
modinfo rt3562sta | grep 3060
modinfo rt2860sta | grep 3060
lsmod | grep -e rt2 -e rt3
```We're gainin' on it!

---

### Post by JoeNixx on 2011-05-11
Hi! 

Here are the outputs you requested:

```
jose@jarvis:~$ modinfo rt3562sta | grep 3060
alias:          pci:v00001814d00003060sv*sd*bc*sc*i*
```

The next one gave no output...

```
jose@jarvis:~$ modinfo rt2860sta | grep 3060
jose@jarvis:~$ 
```

and the last one:

```
jose@jarvis:~$ lsmod | grep -e rt2 -e rt3
rt2860sta             481915  0 
```

I can't thank you enough... I hope this is useful.

J

---

### Post by chili555 on 2011-05-11
> 04:04.0 Network controller [0280]: RaLink Device [[COLOR="Red"]1814:3060[/COLOR]]This is wonderful. The driver that doesn't claim and drive your device is loading:```
jose@jarvis:~$ modinfo rt2860sta | grep [COLOR="Red"]3060[/COLOR]
jose@jarvis:~$
```The driver your card wants won't load!> jose@jarvis:~$ sudo modprobe rt3562sta
FATAL: Error inserting rt3562sta (/lib/modules/2.6.32-31-generic-pae/kernel/drivers/net/wireless/rt3562sta.ko): Device or resource busyLet's see why rt2860sta is loading. Please do:```
sudo rmmod -f rt2860sta
sudo gedit /etc/modules
```Is rt2860sta in there, causing the wrong driver to load automagically? If so, remove it, proofread, save and close gedit. If it's not there to be removed, tell me so we can widen the search. Now do:```
sudo modprobe rt3562sta
iwconfig
```Does the monster (your wireless) live??

---

### Post by JoeNixx on 2011-05-11
Alright, Here are the results of the last commands you kindly given me...

The first one(below) produced no output....

```
jose@jarvis:~$ sudo rmmod -f rt2860sta
[sudo] password for jose: 
jose@jarvis:~$ 
```

Next...
```
jose@jarvis:~$ sudo gedit /etc/modules
```
Then inside gedit it displayed this...
```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
rt2860sta
```

After removing the entry (rt2860sta) in gedit and saving... the following command produced no output:
```
jose@jarvis:~$ sudo modprobe rt3562sta
jose@jarvis:~$ 
```

Next,

```
jose@jarvis:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ra0       Ralink STA  
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0
```

And that's it. I hope I have followed your instructions correctly. :)
I hope we're getting close. Thank you very much sir !

---

### Post by chili555 on 2011-05-11
> ra0       Ralink STA  
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0Now you have a wireless interface with no complaints or errors. Can you click the Network Manager icon and see your network? Can you connect?

If not, post:```
rfkill list all
```

---

### Post by JoeNixx on 2011-05-11
> **chili555 said:**
> Can you click the Network Manager icon and see your network? Can you connect? 

:( Nope, I can not connect.

If not, post:```
rfkill list all
```
that command presented no output in my case..
```
jose@jarvis:~$ rfkill list all
jose@jarvis:~$ 
```

The network manager applet still doesn't show any wireless network. the applet icon in the panel remains the same i.e. turned-off with a red exclamation mark.

If I go to System-Preferences-Network Connections, The wireless connection I used to connect to, is still there though.

Please let me know what you think.

---

### Post by chili555 on 2011-05-11
Let's have a peek at:```
dmesg | grep -i rt3
sudo iwlist ra0 scan
```Thanks.

---

### Post by JoeNixx on 2011-05-11
Ok sir, Here they are:

```
jose@jarvis:~$ dmesg | grep -i rt3
[    7.120505] rt3562sta: module license 'unspecified' taints kernel.
```

The next one:

```
jose@jarvis:~$ sudo iwlist ra0 scan
[sudo] password for jose: 
ra0       Interface doesn't support scanning.
```

Thanks, once more !

---

### Post by chili555 on 2011-05-11
Hmmm, no errors and one trivial warning but it doesn't want to work. Please do:```
sudo su
echo rt3562sta >> /etc/modules
exit
```Reboot and try again:```
dmesg | grep -i rt3
dmesg | grep -i rt2
sudo iwlist ra0 scan
```I'd be happier if I could see something obvious to fix!

---

### Post by JoeNixx on 2011-05-11
Hi, here are the results,

for the first 3 commands, I'll post them together...

```
jose@jarvis:~$ sudo su
[sudo] password for jose: 
root@jarvis:/home/jose# echo rt3562sta >> /etc/modules
root@jarvis:/home/jose# 
root@jarvis:/home/jose# exit
```

After I rebooted....

```
jose@jarvis:~$ dmesg | grep -i rt3
[    8.025221] rt3562sta: module license 'unspecified' taints kernel.
```

Next;

```
jose@jarvis:~$ dmesg | grep -i rt2
[    8.031726] ===> rt2860_probe
[    8.031751] rt2860 0000:04:04.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[    8.033231] @rt2860_probe MAC address: 5c:d9:98:08:a5:87
[    8.033233] <=== rt2860_probe
```

Next one :)

```
jose@jarvis:~$ sudo iwlist ra0 scan
[sudo] password for jose: 
ra0       Interface doesn't support scanning.
```

There you go, can't thank you enough.

- J

---

### Post by chili555 on 2011-05-11
> [    8.031751] [COLOR="Red"]rt2860[/COLOR] 0000:04:04.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21Grrr! Is rt2860sta back? Please post:```
lsmod | grep rt2
```

---

### Post by JoeNixx on 2011-05-11
Hi, I'm sorry, no output for that one sir

```
jose@jarvis:~$ lsmod | grep rt2
jose@jarvis:~$
```

:(

If this is frustrating to me, I can't imagine what it is to you.
You're already a saint for helping me for this long, THANK YOU !

---

### Post by chili555 on 2011-05-11
Please do:```
sudo gedit DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/config.mk
```Be certain that HAS_WPA_SUPPLICANT=y and HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y. If not, please change them. Proofread, save and close gedit. Now do:```
sudo su
rmmod -f rt3562sta
cd ~/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217
make clean
make
make install
modprobe rt3562sta
exit
```Post any errors. Now does your network appear in Network Manager?

---

### Post by JoeNixx on 2011-05-11
Sir, unfortunately.. I could execute the first command...

```
jose@jarvis:~$ sudo su
root@jarvis:/home/jose# rmmod -f rt3562sta
root@jarvis:/home/jose#
```

The next one gave an error,

```
root@jarvis:/home/jose# cd ~/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217
bash: cd: /root/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217: No such file or directory
```

I think I kinda understand what you want me to do, which is to cd to that directory, and even when ls shows the name is correct(for the dir), I can't cd into it, as you can see... 
or maybe I'm doing something wrong. 
Please tell me what to do next, 

Always a pleasure.

PS.
This one I did, and changed the file as ordered... :)
```
sudo gedit DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/config.mk
```

---

### Post by chili555 on 2011-05-11
Please try:```
sudo su
cd /home/jose/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217
make clean
make
make install
modprobe rt3562sta
exit
```

---

### Post by JoeNixx on 2011-05-11
HELLO THERE !

Actually I tried itthis way:

```
jose@jarvis:~/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217$ make clean
cp -f os/linux/Makefile.6 os/linux/Makefile
make -C os/linux clean
make[1]: Entering directory `/home/jose/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux'
rm -f ../../common/*.o
rm -f ../../common/.*.{o,cmd,flags,d}
rm -f ../../os/linux/*.{o,ko,mod.{o,c}}
rm -f ../../os/linux/.*.{cmd,flags,d}
rm -fr ../../os/linux/.tmp_versions
rm -f ../../os/linux/Module.symvers
rm -f ../../os/linux/Module.markers
rm -f ../../os/linux/modules.order
rm -f ../../chips/*.o
rm -f ../../chips/.*.{cmd,flags,d}
rm -f ../../sta/*.o
rm -f ../../sta/.*.{cmd,flags,d}
make[1]: Leaving directory `/home/jose/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux'
rm -rf os/linux/Makefile
jose@jarvis:~/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217$
```

Next,

```
jose@jarvis:~/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217$ sudo make
make -C tools
make[1]: Entering directory `/home/jose/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/jose/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/tools'
/home/jose/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/tools/bin2h
cp -f os/linux/Makefile.6 /home/jose/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/Makefile
make -C /lib/modules/2.6.32-31-generic-pae/build SUBDIRS=/home/jose/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-31-generic-pae'
  CC [M]  /home/jose/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/crypt_md5.o
  CC [M]  /home/jose/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/crypt_sha2.o
  CC [M]  /home/jose/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/crypt_hmac.o
  CC [M]  /home/jose/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/crypt_aes.o
/home/jose/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/crypt_aes.c: In function ‘AES_GTK_KEY_WRAP’:
/home/jose/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/crypt_aes.c:2265: warning: the frame size of 1100 bytes is larger than 1024 bytes
/home/jose/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/crypt_aes.c: In function ‘WscDecryptData’:
/home/jose/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/crypt_aes.c:1592: warning: the frame size of 1364 bytes is larger than 1024 bytes
/home/jose/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/crypt_aes.c: In function ‘WscEncryptData’:
/home/jose/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/crypt_aes.c:1522: warning: the frame size of 1364 bytes is larger than 1024 bytes
  CC [M]  /home/jose/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/crypt_arc4.o
  CC [M]  /home/jose/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/mlme.o
  CC [M]  /home/jose/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/cmm_wep.o
  CC [M]  /home/jose/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/action.o
  CC [M]  /home/jose/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/cmm_data.o
  CC [M]  /home/jose/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/rtmp_init.o
/home/jose/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/rtmp_init.c: In function ‘NICInitAsicFromEEPROM’:
/home/jose/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/rtmp_init.c:1391: warning: format ‘%x’ expects type ‘unsigned int’, but argument 3 has type ‘ULONG’
  CC [M]  /home/jose/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/cmm_tkip.o
  CC [M]  /home/jose/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/cmm_aes.o
  CC [M]  /home/jose/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/cmm_sync.o
  CC [M]  /home/jose/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/eeprom.o
  CC [M]  /home/jose/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/cmm_sanity.o
  CC [M]  /home/jose/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/cmm_info.o
  CC [M]  /home/jose/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/cmm_cfg.o
  CC [M]  /home/jose/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/cmm_wpa.o
  CC [M]  /home/jose/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/dfs.o
  CC [M]  /home/jose/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/spectrum.o
  CC [M]  /home/jose/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/rtmp_timer.o
  CC [M]  /home/jose/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/rt_channel.o
  CC [M]  /home/jose/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/cmm_profile.o
  CC [M]  /home/jose/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/cmm_asic.o
  CC [M]  /home/jose/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/cmm_cmd.o
  CC [M]  /home/jose/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../sta/assoc.o
  CC [M]  /home/jose/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../sta/auth.o
  CC [M]  /home/jose/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../sta/auth_rsp.o
  CC [M]  /home/jose/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../sta/sync.o
  CC [M]  /home/jose/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../sta/sanity.o
  CC [M]  /home/jose/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../sta/rtmp_data.o
  CC [M]  /home/jose/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../sta/connect.o
  CC [M]  /home/jose/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../sta/wpa.o
  CC [M]  /home/jose/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../sta/ags.o
  CC [M]  /home/jose/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../sta/sta_cfg.o
  CC [M]  /home/jose/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/rtmp_init_inf.o
  CC [M]  /home/jose/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/ba_action.o
  CC [M]  /home/jose/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/cmm_mac_pci.o
/home/jose/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/cmm_mac_pci.c: In function ‘RTMPResetTxRxRingMemory’:
/home/jose/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/cmm_mac_pci.c:36: warning: unused variable ‘num’
/home/jose/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/cmm_mac_pci.c: In function ‘RTMPFreeTxRxRingMemory’:
/home/jose/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/cmm_mac_pci.c:119: warning: unused variable ‘IrqFlags’
/home/jose/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/cmm_mac_pci.c:118: warning: unused variable ‘pPacket’
/home/jose/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/cmm_mac_pci.c:117: warning: unused variable ‘pTxD’
/home/jose/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/cmm_mac_pci.c:116: warning: unused variable ‘pTxRing’
/home/jose/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/cmm_mac_pci.c:115: warning: unused variable ‘j’
/home/jose/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/cmm_mac_pci.c:115: warning: unused variable ‘index’
/home/jose/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/cmm_mac_pci.c: In function ‘RTMPAllocTxRxRingMemory’:
/home/jose/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/cmm_mac_pci.c:447: warning: unused variable ‘BufBaseVa’
/home/jose/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/cmm_mac_pci.c:446: warning: unused variable ‘BufBasePaLow’
/home/jose/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/cmm_mac_pci.c:445: warning: unused variable ‘BufBasePaHigh’
/home/jose/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/cmm_mac_pci.c:432: warning: unused variable ‘pPacket’
/home/jose/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/cmm_mac_pci.c:431: warning: unused variable ‘pDmaBuf’
/home/jose/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/cmm_mac_pci.c:430: warning: unused variable ‘pTxRing’
/home/jose/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/cmm_mac_pci.c:428: warning: unused variable ‘pRxD’
/home/jose/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/cmm_mac_pci.c:427: warning: unused variable ‘pTxD’
/home/jose/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/cmm_mac_pci.c:425: warning: unused variable ‘RingBaseVa’
/home/jose/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/cmm_mac_pci.c:424: warning: unused variable ‘RingBasePaLow’
/home/jose/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/cmm_mac_pci.c:423: warning: unused variable ‘RingBasePaHigh’
/home/jose/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/cmm_mac_pci.c:489: warning: ‘index’ may be used uninitialized in this function
  CC [M]  /home/jose/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/cmm_data_pci.o
  CC [M]  /home/jose/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/rtmp_mcu.o
  CC [M]  /home/jose/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/ee_prom.o
  CC [M]  /home/jose/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/ee_efuse.o
  CC [M]  /home/jose/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/rt_rf.o
  CC [M]  /home/jose/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../chips/rt30xx.o
  CC [M]  /home/jose/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../chips/rt35xx.o
  CC [M]  /home/jose/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/misc.o
/home/jose/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/misc.c: In function ‘RTMPHwCoexSwitch’:
/home/jose/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/misc.c:963: warning: format ‘%x’ expects type ‘unsigned int’, but argument 6 has type ‘ULONG’
  CC [M]  /home/jose/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../chips/rt3592cb.o
  LD [M]  /home/jose/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/rt3562sta.o
  Building modules, stage 2.
  MODPOST 1 modules
WARNING: modpost: missing MODULE_LICENSE() in /home/jose/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/rt3562sta.o
see include/linux/module.h for more information
  LD [M]  /home/jose/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/rt3562sta.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-31-generic-pae'
cp -f /home/jose/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/rt3562sta.ko /tftpboot
```

Then....

```
jose@jarvis:~/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217$ sudo make install
make -C /home/jose/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux -f Makefile.6 install
mkdir: cannot create directory `/etc/Wireless': File exists
make[1]: Entering directory `/home/jose/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux'
rm -rf /etc/Wireless/RT2860STA
mkdir /etc/Wireless/RT2860STA
cp /home/jose/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/RT2860STA.dat /etc/Wireless/RT2860STA/.
install -d /lib/modules/2.6.32-31-generic-pae/kernel/drivers/net/wireless/
install -m 644 -c rt3562sta.ko /lib/modules/2.6.32-31-generic-pae/kernel/drivers/net/wireless/
/sbin/depmod -a 2.6.32-31-generic-pae
make[1]: Leaving directory `/home/jose/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux'
jose@jarvis:~/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217$
```

And Lastly (No output)

```
jose@jarvis:~/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217$ sudo modprobe rt3562sta
jose@jarvis:~/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217$
```

GUESS WHAT !!!! 

As soon as I finished that last command My Network Manager started to work ! and displayed to me all the nearby wireless Networks ! I connected to mine, It connected right, and I'm BACK ONLINE AGAIN !!!!!! 

SUCCESS !!!!
YES !!!

THANK YOU
THANK YOU
THANK YOU
THANK YOU
THANK YOU
THANK YOU

I can't say thank you enough ! I just can't
:popcorn::D:D:D:D

Now, Just a Quick Question, and I'm only asking because no one out there has been able to answer to me accurately...and it's WAAYYYY OBVIOUS your the eminence at this..

**If I migrate to Ubuntu 11.04, Do you think my wireless as it is will work (someway somehow)?**

Once again, 

You're THE MAN ! :D

---

### Post by chili555 on 2011-05-11
Whew! I was sure we'd crack the case pretty soon. Glad it's working.> If I migrate to Ubuntu 11.04, Do you think my wireless as it is will work (someway somehow)?No native driver supports your device in 11.04. You'll have to compile as above. I just tried it and it compiles with a few warnings but no errors. Be sure your first step is always 'make clean' when you get a new kernel.

I don't have the device, so I can test no farther.

Have fun!

---

### Post by JoeNixx on 2011-05-11
:)

I've already bothered you too many times, so this already feels kind of abusive, I'm sorry :redface:

But as I said before, I feel you're probably one of the few who can certainly answer this types of questions honestly.

> I just tried it and it compiles with a few warnings but no errors

**- Does your last statement mean I could give it a shot by using the Live CD for 11.04 ? and then compiling the driver and seeing if it works?**

**- Is the new Desktop i.e. Unity a factor? (I thought this driver would only work for Gnome desktops)**

Well, thanks again sir. Infinite Thanks... 

I'm sorry to trouble you this much, This is just an invaluable lesson to me. From a great Master of course !

Sincerely, 

Jose

---

### Post by chili555 on 2011-05-12
> Does your last statement mean I could give it a shot by using the Live CD for 11.04 ? and then compiling the driver and seeing if it works?
Absolutely.> Is the new Desktop i.e. Unity a factor? (I thought this driver would only work for Gnome desktops)The windowing manager, Unity, Gnome, XFCE, etc. makes no difference. I can find no reason why it makes the slightest difference.

---

### Post by madgeek on 2011-06-14
> **chili555 said:**
> Please try:```
sudo su
  cd /home/jose/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217
make clean
make
make install
  modprobe rt3562sta
exit
```

Just wanted to pop in to say, this worked for me as well. The changing of the flag (from "n" to "y") did the trick.

---

### Post by JoeNixx on 2011-06-14
Cool, chili555 is amazing.
(@madgeek Could you remind me in which file is this flag?)

@madgeek Are you currently on Ubuntu 11.04? I still have not migrated due to job obligations, but I will soon do, I would like to know with which wireless card device you had success(and to reiterate if you're on Ubuntu 11.04)

Thanks for your post.

J.

---

### Post by madgeek on 2011-07-09
> **JoeNixx said:**
> Cool, chili555 is amazing.
(@madgeek Could you remind me in which file is this flag?)

    @madgeek Are you currently on Ubuntu 11.04? I still have not migrated due to job obligations, but I will soon do, I would like to know with which wireless card device you had success(and to reiterate if you're on Ubuntu 11.04)

Thanks for your post.

J.

   Yes, it was for 11.04



In terminal:[INDENT]sudo gedit os/linux/config.mk


[/INDENT]The following parameters:
HAS_WPA_SUPPLICANT = y
HAS_NATIVE_WPA_SUPPLICANT_SUPPORT = y

Also remember to do this: 
 sudo su 

echo rt3562sta >> /etc/modules
  
Card was DWA 525

---

### Post by JoeNixx on 2011-07-10
Thank you very much for this information,

I needed to confirm it in order to migrate to 11.04.

Fantastic! 

Thanks again,

J

---

