---
title: "how replace Broadcom wireless driver?"
date: 2009-02-09
forum: Networking &amp; Wireless
---

### Post by TimDaniels on 2009-02-09
My Dell XPS M1330 laptop runs Ubuntu 8.04, and the Wi-Fi has crapped out.  The symptom is that the Network Manager dropdown menu no longer lists the Enable Wireless checkbox, and I can no longer make a wireless connection.  I'd like to keep the solution as simple and newbie-friendly as possible, and dumping the wireless driver and reinstalling it sounds like the most straight-forward way to recover.  How does one do that?  (BTW, when I boot Vista on the same laptop, wireless works flawlessly, so it's not the hardware or the setting of a physical switch.)

*TimDaniels*

---

### Post by kevdog on 2009-02-09
Lets learn a little bit more about your setup.

Please type and then post the following output from the terminal:

lspci -nnm
lshw -C network

---

### Post by TimDaniels on 2009-02-09
> **kevdog said:**
> Lets learn a little bit more about your setup.

Please type and then post the following output from the terminal:

lspci -nnm
lshw -C network

Thanks for replying, KevDog.
For lspci -nnm, I get:

00:00.0 "Host bridge [0600]" "Intel Corporation [8086]" "Mobile PM965/GM965/GL960 Memory Controller Hub [2a00]" -r0c "Dell [1028]" "Unknown device [0209]"
00:01.0 "PCI bridge [0604]" "Intel Corporation [8086]" "Mobile PM965/GM965/GL960 PCI Express Root Port [2a01]" -r0c "" ""
00:1a.0 "USB Controller [0c03]" "Intel Corporation [8086]" "82801H (ICH8 Family) USB UHCI Controller #4 [2834]" -r02 "Dell [1028]" "Unknown device [0209]"
00:1a.1 "USB Controller [0c03]" "Intel Corporation [8086]" "82801H (ICH8 Family) USB UHCI Controller #5 [2835]" -r02 "Dell [1028]" "Unknown device [0209]"
00:1a.7 "USB Controller [0c03]" "Intel Corporation [8086]" "82801H (ICH8 Family) USB2 EHCI Controller #2 [283a]" -r02 -p20 "Dell [1028]" "Unknown device [0209]"
00:1b.0 "Audio device [0403]" "Intel Corporation [8086]" "82801H (ICH8 Family) HD Audio Controller [284b]" -r02 "Dell [1028]" "Unknown device [0209]"
00:1c.0 "PCI bridge [0604]" "Intel Corporation [8086]" "82801H (ICH8 Family) PCI Express Port 1 [283f]" -r02 "" ""
00:1c.1 "PCI bridge [0604]" "Intel Corporation [8086]" "82801H (ICH8 Family) PCI Express Port 2 [2841]" -r02 "" ""
00:1c.3 "PCI bridge [0604]" "Intel Corporation [8086]" "82801H (ICH8 Family) PCI Express Port 4 [2845]" -r02 "" ""
00:1c.5 "PCI bridge [0604]" "Intel Corporation [8086]" "82801H (ICH8 Family) PCI Express Port 6 [2849]" -r02 "" ""
00:1d.0 "USB Controller [0c03]" "Intel Corporation [8086]" "82801H (ICH8 Family) USB UHCI Controller #1 [2830]" -r02 "Dell [1028]" "Unknown device [0209]"
00:1d.1 "USB Controller [0c03]" "Intel Corporation [8086]" "82801H (ICH8 Family) USB UHCI Controller #2 [2831]" -r02 "Dell [1028]" "Unknown device [0209]"
00:1d.2 "USB Controller [0c03]" "Intel Corporation [8086]" "82801H (ICH8 Family) USB UHCI Controller #3 [2832]" -r02 "Dell [1028]" "Unknown device [0209]"
00:1d.7 "USB Controller [0c03]" "Intel Corporation [8086]" "82801H (ICH8 Family) USB2 EHCI Controller #1 [2836]" -r02 -p20 "Dell [1028]" "Unknown device [0209]"
00:1e.0 "PCI bridge [0604]" "Intel Corporation [8086]" "82801 Mobile PCI Bridge [2448]" -rf2 -p01 "" ""
00:1f.0 "ISA bridge [0601]" "Intel Corporation [8086]" "82801HEM (ICH8M) LPC Interface Controller [2815]" -r02 "Dell [1028]" "Unknown device [0209]"
00:1f.1 "IDE interface [0101]" "Intel Corporation [8086]" "82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller [2850]" -r02 -p8a "Dell [1028]" "Unknown device [0209]"
00:1f.2 "SATA controller [0106]" "Intel Corporation [8086]" "82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller [2829]" -r02 -p01 "Dell [1028]" "Unknown device [0209]"
00:1f.3 "SMBus [0c05]" "Intel Corporation [8086]" "82801H (ICH8 Family) SMBus Controller [283e]" -r02 "Dell [1028]" "Unknown device [0209]"
01:00.0 "VGA compatible controller [0300]" "nVidia Corporation [10de]" "GeForce 8400M GS [0427]" -ra1 "Dell [1028]" "Unknown device [0209]"
03:01.0 "FireWire (IEEE 1394) [0c00]" "Ricoh Co Ltd [1180]" "R5C832 IEEE 1394 Controller [0832]" -r05 -p10 "Dell [1028]" "Unknown device [0209]"
03:01.1 "SD Host controller [0805]" "Ricoh Co Ltd [1180]" "R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [0822]" -r22 -p01 "Dell [1028]" "Unknown device [0209]"
03:01.2 "System peripheral [0880]" "Ricoh Co Ltd [1180]" "R5C843 MMC Host Controller [0843]" -r12 "Dell [1028]" "Unknown device [0209]"
03:01.3 "System peripheral [0880]" "Ricoh Co Ltd [1180]" "R5C592 Memory Stick Bus Host Adapter [0592]" -r12 "Dell [1028]" "Unknown device [0209]"
03:01.4 "System peripheral [0880]" "Ricoh Co Ltd [1180]" "xD-Picture Card Controller [0852]" -rff -pff "" ""
09:00.0 "Ethernet controller [0200]" "Broadcom Corporation [14e4]" "NetLink BCM5906M Fast Ethernet PCI Express [1713]" -r02 "Dell [1028]" "XPS M1330 [0209]"
0c:00.0 "Network controller [0280]" "Broadcom Corporation [14e4]" "BCM4312 802.11a/b/g [4312]" -r01 "Dell [1028]" "Wireless 1490 Dual Band WLAN Mini-Card [0007]"



For lshw -C network, I get:

  *-network               
       description: Network controller
       product: BCM4312 802.11a/b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb
  *-network
       description: Ethernet interface
       product: NetLink BCM5906M Fast Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 02
       serial: 00:1d:09:42:1e:ae
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tg3 driverversion=3.86 latency=0 module=tg3 multicast=yes


What do you think?

*TimDaniels*

---

### Post by superm1 on 2009-02-09
With that card, you should likely be able to enable 'wl' via Jockey and use that.  Once you are fully updated, open up System->Administration->Hardware Drivers.  Should list the Broadcom driver there.

---

### Post by TimDaniels on 2009-02-09
> **superm1 said:**
> With that card, you should likely be able to **enable 'wl' via Jockey** and use that.  Once you are fully updated, open up System->Administration->Hardware Drivers.  Should list the Broadcom driver there.

Hi, SuperM1.  What is Jockey?  What is one doing when one "uses that"?  When the driver is listed in Hardware Drivers, what should one do then?

*TimDaniels*

---

### Post by superm1 on 2009-02-09
> **TimDaniels said:**
> Hi, SuperM1.  What is Jockey?  What is one doing when one "uses that"?  When the driver is listed in Hardware Drivers, what should one do then?

*TimDaniels*
Hi Tim:

Jockey is the name of the package that provides the "Hardware drivers" tool.  When you open up Hardware Drivers, you should see a list of the drivers it can offer you.  Hopefully the Broadcom driver is listed and you can press the activate button and reboot to activate it.

---

### Post by TimDaniels on 2009-02-09
> **superm1 said:**
> Hi Tim:

Jockey is the name of the package that provides the "Hardware drivers" tool.  When you open up Hardware Drivers, you should see a list of the drivers it can offer you.  Hopefully the Broadcom driver is listed and you can press the activate button and reboot to activate it.

I opened Hardware Drivers and checked the box for Broadcom b43 Wireless Driver, and a bunch of commands scrolled past, including one about fwcutter.  Then it reported that the driver was In Use.  But when I click on the Network Manager dual monitor icon, wireless is still not mentioned in the dropdown menu.

What I'd like to do is to install the new Broadcom driver available here: [http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php).  But the README text seems to be written rather tersely by a foreigner, possibly Chinese (he drops the S's from plural nouns) and I can't quite understand how to install the driver.  I did run `make` on 3 modules that I found in /lib/modules, but there was finally an error reported about "l" being an illegal command or option.  Is there another way to download and install this driver through Synaptic Package Manager or other app?

*TimDaniels*

---

### Post by superm1 on 2009-02-09
> **TimDaniels said:**
> I opened Hardware Drivers and checked the box for Broadcom b43 Wireless Driver, and a bunch of commands scrolled past, including one about fwcutter.  Then it reported that the driver was In Use.  But when I click on the Network Manager dual monitor icon, wireless is still not mentioned in the dropdown menu.

What I'd like to do is to install the new Broadcom driver available here: [http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php).  But the README text seems to be written rather tersely by a foreigner, possibly Chinese (he drops the S's from plural nouns) and I can't quite understand how to install the driver.  I did run `make` on 3 modules that I found in /lib/modules, but there was finally an error reported about "l" being an illegal command or option.  Is there another way to download and install this driver through Synaptic Package Manager or other app?

*TimDaniels*
What I was referring to was *not* the b43 driver with fwcutter.  It would have been the STA WL driver.  If it's not being offered, then you either don't have all of your updates done or your card won't support it.

---

### Post by kevdog on 2009-02-09
The STA driver is the same as the wl driver, just an FYI.

[http://linuxfans.betaserver.org/index.php?option=com_content&view=article&id=46:broadcom-guide-for-ubuntu-hardy-and-newer&catid=34:guides&Itemid=61](http://linuxfans.betaserver.org/index.php?option=com_content&view=article&id=46:broadcom-guide-for-ubuntu-hardy-and-newer&catid=34:guides&Itemid=61)

---

### Post by Ayuthia on 2009-02-10
Your card should work with the wl (Broadcom STA) module.  Like superm1 said, the 8.04 version does need to be updated for it to work for your card.  If I recall correctly, you need to be at 2.6.24-21 in order for that module to be available through System->Administration->Hardware Drivers.

If for some reason you do need to compile it, the link that kevodg provided should help (A guide is available on the second to last link on the page that he provided).  I don't recall if I tested out the newest release with 2.6.24 though, but it should help you get started in compiling the module.  

It would be best to try it out with Hardware Drivers first and if it does not work then try to compile.  

If you should run into problems, just come back and let us know what happened.

---

### Post by TimDaniels on 2009-02-10
> **Ayuthia said:**
> Your card should work with the wl (Broadcom STA) module.
Like superm1 said, the 8.04 version does need to be updated for
it to work for your card.  If I recall correctly, you need to be
at 2.6.24-21 in order for that module to be available through
System->Administration->Hardware Drivers.

Sorry to be so dense, but what does it mean to "be at 2.6.24-21"?

In my 8.04 Ubuntu system, /lib/modules contains 3 directories:
2.6.24-19-generic,  2.6.24-21-generic, and  2.6.24-23-generic.

What are these things?
Are all 3 needed, or can I delete 2 of them?

How does one update the 8.04 version of the wl module,
especially if (as it seems to appear) that it's not in the system?

In Hardware Drivers right now there are listed just 2 entries:
Broadcom B43 wireless driver
NVIDIA Accelerated Graphics driver

How does one get rid of the "B43 wireless driver" entry and
replace it with the wl driver?  Or will the installation of the
wl driver just overwrite the B43 driver?


> If for some reason you do need to compile it, the link
that kevodg provided should help (A guide is available on the
second to last link on the page that he provided).  I don't
recall if I tested out the newest release with 2.6.24 though,
but it should help you get started in compiling the module.  

It would be best to try it out with Hardware Drivers first and
if it does not work then try to compile.

How does one get the wl driver as an entry in Hardware Drivers?


*TimDaniels*

---

### Post by Ayuthia on 2009-02-10
> **TimDaniels said:**
> Sorry to be so dense, but what does it mean to "be at 2.6.24-21"?

In my 8.04 Ubuntu system, /lib/modules contains 3 directories:
2.6.24-19-generic,  2.6.24-21-generic, and  2.6.24-23-generic.

What are these things?
Are all 3 needed, or can I delete 2 of them?

How does one update the 8.04 version of the wl module,
especially if (as it seems to appear) that it's not in the system?

In Hardware Drivers right now there are listed just 2 entries:
Broadcom B43 wireless driver
NVIDIA Accelerated Graphics driver

How does one get rid of the "B43 wireless driver" entry and
replace it with the wl driver?  Or will the installation of the
wl driver just overwrite the B43 driver?




How does one get the wl driver as an entry in Hardware Drivers?


*TimDaniels*

If you have 2.6.24-21-generic or 2.6.24-23-generic, the wl driver should be available.  The three different kernel versions are there because there have been at least three different updates to the system.  It will allow you to go back to a previous kernel if the newest one does not work.

You might try using the commands in the Terminal that I mentioned in my previous post.  If it cannot find the wl module, then Ubuntu does not think that your card is supported so you should try to compile (if you still want to try).

---

### Post by TimDaniels on 2009-02-11
> **Ayuthia said:**
> If you have 2.6.24-21-generic or 2.6.24-23-generic, But the wl driver should be available.  The three different kernel versions are there because there have been at least three different updates to the system.  It will allow you to go back to a previous kernel if the newest one does not work.

You might try using the commands in the Terminal that I mentioned in my previous post.  If it cannot find the wl module, then Ubuntu does not think that your card is supported so you should try to compile (if you still want to try).

As I wrote, in /lib/modules there are the 3 directories:
2.6.24-19-generic, 2.6.24-21-generic, and 2.6.24-23-generic.

But I have no idea whether they are all backups or whether the active kernel is running in one of those directories.  The command `uname -r` outputs the name `2.6.24-19-generic` and I suppose that is the name of the running kernel, but I don't know if it is contained in the directory "2.6.24-19-generic" or if the running kernel is a copy of what's in that directory.  If *-19-generic is a kernel prior to *-21-generic and *-23-generic why would *-19-generic be running?  If Hardware Drivers would list the Broadcom wl driver if the *-21-generic or the *-23-generic kernel were running, **how does one switch kernels so that one of these later versions would run?**

*TimDaniels*

---

### Post by Ayuthia on 2009-02-11
> **TimDaniels said:**
> As I wrote, in /lib/modules there are the 3 directories:
2.6.24-19-generic, 2.6.24-21-generic, and 2.6.24-23-generic.

But I have no idea whether they are all backups or whether the active kernel is running in one of those directories.  The command `uname -r` outputs the name `2.6.24-19-generic` and I suppose that is the name of the running kernel, but I don't know if it is contained in the directory "2.6.24-19-generic" or if the running kernel is a copy of what's in that directory.  If *-19-generic is a kernel prior to *-21-generic and *-23-generic why would *-19-generic be running?  If Hardware Drivers would list the Broadcom wl driver if the *-21-generic or the *-23-generic kernel were running, **how does one switch kernels so that one of these later versions would run?**

*TimDaniels*
Since uname -r shows 2.6.24-19-generic, that is the running kernel and that is why you are not seeing the information in Hardware Drivers.

I am not for sure why your menu.lst file is not being updated when there is a kernel update.  It usually updates it for you.  You might try going into the Terminal and try to run a safe-upgrade just to make sure that the kernels are updated:
```
sudo aptitude safe-upgrade
```If there were errors with the kernel, aptitude should show that it will try to configure them.

You can edit /boot/grub/menu.lst and change 2.6.24-19.generic to 2.6.24-23.generic.  To edit the file:
```
gksu gedit /boot/grub/menu.lst
```

Before you update menu.lst, you can try it out when you restart your computer.  If you don't get a list of options to boot into, you can press escape and a menu should come up.  From there you should be given an option to edit an option.  Select the 2.6.24-19-generic lines and change them to 2.6.24-23-generic.  You can then boot into it.  This would be the safer option to go so that if something should go wrong, all you need to do is reboot.

---

### Post by dvlchd3 on 2009-02-11
Try running the following command.  This will install b43 firmware.  Sometimes the restricted driver craps out, and you have to reinstall the firmware for bcm43xx cards.

```
sudo /usr/share/b43-fwcutter/install_bcm43xx_firmware.sh
```

---

### Post by TimDaniels on 2009-02-11
> **Ayuthia said:**
> Since uname -r shows 2.6.24-19-generic, that is the running kernel and that is why you are not seeing the information in Hardware Drivers.

I am not for sure why your menu.lst file is not being updated when there is a kernel update.  It usually updates it for you.  You might try going into the Terminal and try to run a safe-upgrade just to make sure that the kernels are updated:
```
sudo aptitude safe-upgrade
```If there were errors with the kernel, aptitude should show that it will try to configure them.

You can edit /boot/grub/menu.lst and change 2.6.24-19.generic to 2.6.24-23.generic.  To edit the file:
```
gksu gedit /boot/grub/menu.lst
```

OK, I ran `aptitude safe-upgrade`, and before I restart,
here's the output:

belt@laptop:~$ sudo aptitude safe-upgrade
[sudo] password for belt: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             
The following packages are unused and will be REMOVED:
  linux-headers-2.6.24-19 linux-headers-2.6.24-19-generic 
0 packages upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 68.3MB will be freed.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
(Reading database ... 135248 files and directories currently installed.)
Removing linux-headers-2.6.24-19-generic ...
Removing linux-headers-2.6.24-19 ...
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done 


Now I'll restart.

*TimDaniels*

---

### Post by TimDaniels on 2009-02-11
> **Ayuthia said:**
> Since uname -r shows 2.6.24-19-generic, that is the running kernel and that is why you are not seeing the information in Hardware Drivers.

I am not for sure why your menu.lst file is not being updated when there is a kernel update.  It usually updates it for you.  You might try going into the Terminal and try to run a safe-upgrade just to make sure that the kernels are updated:
```
sudo aptitude safe-upgrade
```If there were errors with the kernel, aptitude should show that it will try to configure them.

You can edit /boot/grub/menu.lst and change 2.6.24-19.generic to 2.6.24-23.generic.  To edit the file:
```
gksu gedit /boot/grub/menu.lst
```

Before you update menu.lst, you can try it out when you restart your computer.  If you don't get a list of options to boot into, you can press escape and a menu should come up.  From there you should be given an option to edit an option.  Select the 2.6.24-19-generic lines and change them to 2.6.24-23-generic.  You can then boot into it.  This would be the safer option to go so that if something should go wrong, all you need to do is reboot.

Ok, I've restarted after doing the `aptitude safe-upgrade`, and
uname -r gives:
2.6.24-19-generic

In /boot/grub/menu.lst, there are the (uncommented) lines:

title		Ubuntu 8.04.1
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=e222dd89-fdd8-4846-bf44-031770eb3cb1 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

I won't edit that directly since I don't know what value to
assign to UUID.  Instead, I'll restart and try to catch grub
in the boot process by pressing Esc.

*TimDaniels*

---

### Post by TimDaniels on 2009-02-11
> **Ayuthia said:**
> 
Before you update menu.lst, you can try it out when you restart your computer.  If you don't get a list of options to boot into, you can press escape and a menu should come up.  From there you should be given an option to edit an option.  Select the 2.6.24-19-generic lines and change them to 2.6.24-23-generic.  You can then boot into it.  This would be the safer option to go so that if something should go wrong, all you need to do is reboot.

I restarted, and intercepted grub with Esc.  I selected "e" to edit.  I selected the 2 lines in the menu which contained a reference to 2.6.24-19-generic, and I changed them to 2.6.24-23-generic, but I couldn't make the editor save the changes.  The directions say to press Esc, but that just caused the entries to revert to the original contents.  And one of the lines contained a value assignment for "UUID", and I don't know what value to assign it.  How does one save the changes and assign a value to "UUID"?

*imDaniels*

*TimDaniels*

---

### Post by TimDaniels on 2009-02-11
> **dvlchd3 said:**
> Try running the following command.  This will install b43 firmware.  Sometimes the restricted driver craps out, and you have to reinstall the firmware for bcm43xx cards.

```
sudo /usr/share/b43-fwcutter/install_bcm43xx_firmware.sh
```

OK, I ran it and got:

...$sudo /usr/share/b43-fwcutter/install_bcm43xx_firmware.sh
--12:16:30--  [http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o](http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o)
           => `wl_apsta-3.130.20.0.o'
Resolving downloads.openwrt.org... 195.56.146.238
Connecting to downloads.openwrt.org|195.56.146.238|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 652,866 (638K) [application/x-object]

100%[====================================>] 652,866      193.64K/s    ETA 00:00

12:16:47 (193.20 KB/s) - `wl_apsta-3.130.20.0.o' saved [652866/652866]

--12:16:47--  [http://downloads.openwrt.org/sources/broadcom-wl-4.80.53.0.tar.bz2](http://downloads.openwrt.org/sources/broadcom-wl-4.80.53.0.tar.bz2)
           => `broadcom-wl-4.80.53.0.tar.bz2'
Resolving downloads.openwrt.org... 195.56.146.238
Connecting to downloads.openwrt.org|195.56.146.238|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 904,072 (883K) [application/x-tar]

100%[====================================>] 904,072      264.54K/s    ETA 00:00

12:17:02 (263.76 KB/s) - `broadcom-wl-4.80.53.0.tar.bz2' saved [904072/904072]

This file is recognised as:
  ID         :  FW10
  filename   :  wl_apsta.o
  version    :  295.14
  MD5        :  e08665c5c5b66beb9c3b2dd54aa80cb3
Extracting b43legacy/ucode2.fw
Extracting b43legacy/ucode4.fw
Extracting b43legacy/ucode5.fw
Extracting b43legacy/ucode11.fw
Extracting b43legacy/pcm4.fw
Extracting b43legacy/pcm5.fw
Extracting b43legacy/a0g0bsinitvals2.fw
Extracting b43legacy/b0g0bsinitvals5.fw
Extracting b43legacy/a0g0initvals5.fw
Extracting b43legacy/a0g1bsinitvals5.fw
Extracting b43legacy/a0g0initvals2.fw
Extracting b43legacy/a0g1initvals5.fw
Extracting b43legacy/b0g0bsinitvals2.fw
Extracting b43legacy/b0g0initvals5.fw
Extracting b43legacy/b0g0initvals2.fw
Extracting b43legacy/a0g0bsinitvals5.fw
broadcom-wl-4.80.53.0/
broadcom-wl-4.80.53.0/kmod/
broadcom-wl-4.80.53.0/kmod/wl_apsta_mimo.o
broadcom-wl-4.80.53.0/kmod/wl_apsta.o
broadcom-wl-4.80.53.0/nas
broadcom-wl-4.80.53.0/wl
broadcom-wl-4.80.53.0/WHERE_FROM
broadcom-wl-4.80.53.0/libbcmcrypto.so
This file is recognised as:
  ID         :  FW11
  filename   :  wl_apsta_mimo.o
  version    :  351.126
  MD5        :  722e2e0d8cc04b8f118bb5afe6829ff9
Extracting b43/ucode4.fw
Extracting b43/ucode5.fw
Extracting b43/ucode11.fw
Extracting b43/ucode13.fw
Extracting b43/pcm4.fw
Extracting b43/pcm5.fw
Extracting b43/b0g0initvals4.fw
Extracting b43/b0g0bsinitvals4.fw
Extracting b43/a0g0initvals4.fw
Extracting b43/a0g0bsinitvals4.fw
Extracting b43/b0g0initvals5.fw
Extracting b43/b0g0bsinitvals5.fw
Extracting b43/a0g0initvals5.fw
Extracting b43/a0g1initvals5.fw
Extracting b43/a0g0bsinitvals5.fw
Extracting b43/a0g1bsinitvals5.fw
Extracting b43/lp0initvals13.fw
Extracting b43/lp0bsinitvals13.fw
Extracting b43/b0g0initvals13.fw
Extracting b43/b0g0bsinitvals13.fw
Extracting b43/a0g1initvals13.fw
Extracting b43/a0g1bsinitvals13.fw



Now I'll restart and see what happened.

*TimDaniels*

---

### Post by TimDaniels on 2009-02-11
> **dvlchd3 said:**
> Try running the following command.  This will install b43 firmware.  Sometimes the restricted driver craps out, and you have to reinstall the firmware for bcm43xx cards.

```
sudo /usr/share/b43-fwcutter/install_bcm43xx_firmware.sh
```

OK, I've run the command and restarted, and Hardware Drivers still contains just the "Broadcom B43 driver" entry for wireless, and the Network Manager still doesn't have a checkbox for wireless networking, `uname -r` still lists 2.6.24-19-generic.  Any ideas on what's not right?

*TimDaniels*

---

