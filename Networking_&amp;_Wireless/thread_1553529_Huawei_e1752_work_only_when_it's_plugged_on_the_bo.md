---
title: "Huawei e1752 work only when it's plugged on the boot"
date: 2010-08-15
forum: Networking &amp; Wireless
---

### Post by seddik_saber on 2010-08-15
I want t understand why my 3G modem work only when it's plugged when my computer boot.
If I forget to plug it , I need to restart my machine to get it working. 
I'm using ubuntu 10.04

when I plug the modem during the boot I get the product id changed from 1446 to 141b and dmesg |grep tty
show me that the modem attached to ttyusb0 and ttyusb1
when I plug it after the startup I get also the product id changed from 1446 to 141b but dmesg |grep tty
show me nothing.

---

### Post by alexfish on 2010-08-15
possible the device is switching on boot , then if usb_modeswitch is installed it will also kick in and try to switch the device
in but will assert wrong info to the system , since it is in storage mode, or a different driver gets assigned to the device

can you post two results of this command from the terminal
one where it configures on boot and the other after boot where it is not recognized

will also need the listing of the logfile viewer / messages , on the parts relevant to the device

are you manually ejecting the device after boot

Code: 

[COLOR=Blue]lsusb -t[/COLOR]

code:

Code:

[COLOR=Blue]ls -al /dev/serial/by-id/usb*[/COLOR]

thanks in advance

alexfish

forgot can you give me the results of

Code:

which usb-devices

---

### Post by seddik_saber on 2010-08-18
thx for your help.
the result of the requested commands are:
when it's connected on boot( notice also if it was connected on boot , it's work , I unplugged it and repluged it, it's work.
cmd : lsusb -t
result```

2-6:1.0: No such file or directory
3-1:1.2: No such file or directory
3-1:1.3: No such file or directory
/:  Bus 08.Port 1: Dev 1, Class=root_hub, Driver=uhci_hcd/2p, 12M
/:  Bus 07.Port 1: Dev 1, Class=root_hub, Driver=uhci_hcd/2p, 12M
/:  Bus 06.Port 1: Dev 1, Class=root_hub, Driver=uhci_hcd/2p, 12M
/:  Bus 05.Port 1: Dev 1, Class=root_hub, Driver=uhci_hcd/2p, 12M
    |__ Port 2: Dev 2, If 0, Class=HID, Driver=usbhid, 12M
    |__ Port 2: Dev 2, If 1, Class=HID, Driver=usbhid, 12M
    |__ Port 2: Dev 2, If 2, Class=HID, Driver=usbhid, 12M
/:  Bus 04.Port 1: Dev 1, Class=root_hub, Driver=uhci_hcd/2p, 12M
/:  Bus 03.Port 1: Dev 1, Class=root_hub, Driver=uhci_hcd/2p, 12M
    |__ Port 1: Dev 2, If 0, Class='bInterfaceClass 0xe0 not yet handled', Driver=btusb, 12M
    |__ Port 1: Dev 2, If 1, Class='bInterfaceClass 0xe0 not yet handled', Driver=btusb, 12M
    |__ Port 1: Dev 2, If 2, Class=vend., Driver=, 12M
    |__ Port 1: Dev 2, If 3, Class=app., Driver=, 12M
/:  Bus 02.Port 1: Dev 1, Class=root_hub, Driver=ehci_hcd/8p, 480M
    |__ Port 1: Dev 2, If 0, Class=vend., Driver=option, 480M
    |__ Port 1: Dev 2, If 1, Class=vend., Driver=option, 480M
    |__ Port 1: Dev 2, If 2, Class=stor., Driver=usb-storage, 480M
    |__ Port 6: Dev 4, If 0, Class=vend., Driver=, 480M
/:  Bus 01.Port 1: Dev 1, Class=root_hub, Driver=ehci_hcd/4p, 480M
    |__ Port 2: Dev 2, If 0, Class='bInterfaceClass 0x0e not yet handled', Driver=uvcvideo, 480M
    |__ Port 2: Dev 2, If 1, Class='bInterfaceClass 0x0e not yet handled', Driver=uvcvideo, 480M

```
cmd :[COLOR=Blue] ls -al /dev/serial/by-id/usb*[/COLOR]
result
```
[COLOR=Blue]
lrwxrwxrwx 1 root root 13 2010-08-18 17:14 /dev/serial/by-id/usb-HUAWEI_Technology_HUAWEI_Mobile_1234567890ABCDEF-if00-port0 -> ../../ttyUSB0
lrwxrwxrwx 1 root root 13 2010-08-18 17:14 /dev/serial/by-id/usb-HUAWEI_Technology_HUAWEI_Mobile_1234567890ABCDEF-if01-port0 -> ../../ttyUSB1

[/COLOR]
```

---

### Post by seddik_saber on 2010-08-18
while disconnected on boot, and connected after 
```

/:  Bus 08.Port 1: Dev 1, Class=root_hub, Driver=uhci_hcd/2p, 12M
/:  Bus 07.Port 1: Dev 1, Class=root_hub, Driver=uhci_hcd/2p, 12M
/:  Bus 06.Port 1: Dev 1, Class=root_hub, Driver=uhci_hcd/2p, 12M
/:  Bus 05.Port 1: Dev 1, Class=root_hub, Driver=uhci_hcd/2p, 12M
    |__ Port 2: Dev 2, If 0, Class=HID, Driver=usbhid, 12M
    |__ Port 2: Dev 2, If 1, Class=HID, Driver=usbhid, 12M
    |__ Port 2: Dev 2, If 2, Class=HID, Driver=usbhid, 12M
/:  Bus 04.Port 1: Dev 1, Class=root_hub, Driver=uhci_hcd/2p, 12M
/:  Bus 03.Port 1: Dev 1, Class=root_hub, Driver=uhci_hcd/2p, 12M
    |__ Port 1: Dev 2, If 0, Class='bInterfaceClass 0xe0 not yet handled', Driver=btusb, 12M
    |__ Port 1: Dev 2, If 1, Class='bInterfaceClass 0xe0 not yet handled', Driver=btusb, 12M
    |__ Port 1: Dev 2, If 2, Class=vend., Driver=, 12M
    |__ Port 1: Dev 2, If 3, Class=app., Driver=, 12M
/:  Bus 02.Port 1: Dev 1, Class=root_hub, Driver=ehci_hcd/8p, 480M
    |__ Port 1: Dev 5, If 0, Class=vend., Driver=, 480M
    |__ Port 1: Dev 5, If 1, Class=vend., Driver=, 480M
    |__ Port 1: Dev 5, If 2, Class=stor., Driver=usb-storage, 480M
    |__ Port 6: Dev 3, If 0, Class=vend., Driver=, 480M
/:  Bus 01.Port 1: Dev 1, Class=root_hub, Driver=ehci_hcd/4p, 480M
    |__ Port 2: Dev 2, If 0, Class='bInterfaceClass 0x0e not yet handled', Driver=uvcvideo, 480M
    |__ Port 2: Dev 2, If 1, Class='bInterfaceClass 0x0e not yet handled', Driver=uvcvideo, 480M

```

and 

```
ls: ne peut accéder /dev/serial/by-id/usb*: Aucun fichier ou dossier de ce type
```

the second result mean they did not found any file or folder.

---

### Post by seddik_saber on 2010-08-18
forget this one, while connected:
```

laptop:~$ which usb-devices
/usr/bin/usb-devices


```

---

### Post by alexfish on 2010-08-18
look as if the drivers are failing to load

can you try 
[B]
Code:[/B]

**sudo modprobe  option**

see what happens

if it fails can post

Code:

lsusb

---

### Post by seddik_saber on 2010-08-18
the modprobe command has no output for the module option.
lsusb while working:
```

Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 045e:0745 Microsoft Corp. 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 0a5c:2151 Broadcom Corp. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 004: ID 1c7a:0801 LighTuning Technology Inc. 
Bus 002 Device 002: ID 12d1:141b Huawei Technologies Co., Ltd. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 064e:a133 Suyin Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


```

---

### Post by alexfish on 2010-08-18
hi

forgot to mention

can you post results of the lsusb command when the device is working after boot:

have you got usb_modeswitch installed:

your device is mentioned here:

[http://www.draisberghof.de/usb_modeswit  ... .php?t=388]("http://www.draisberghof.de/usb_modeswitch/bb/viewtopic.php?t=388")

in a recent usb_modeswitch forum discussion:  read 3 from last post: Josh: moderator:

regards

alexfish

---

### Post by seddik_saber on 2010-08-19
for lsusb it's the last provided listing (while it's work)
for usb_modeswitch i have it installed.

---

### Post by seddik_saber on 2010-08-19
lsusb when the device notworking
> 
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 045e:0745 Microsoft Corp. 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 0a5c:2151 Broadcom Corp. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 005: ID 12d1:141b Huawei Technologies Co., Ltd. 
Bus 002 Device 003: ID 1c7a:0801 LighTuning Technology Inc. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 064e:a133 Suyin Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


---

### Post by alexfish on 2010-08-19
Hi


Possible:
the device is recognised by the kernel and the usb_modeswitch is resetting the device
after boot , if so try to disable usb_modeswitch

see what happens

if you need usb_modeswitch for other devices then you could try installing Sakis3g (latest version of usb_modeswitch is integrated ) , 

even if the connection is CDMA as you can select Sakis3g to only modeswitch the device

Sakis3g details here + links  [How To : Mobile Broadband Connections [ Ubuntu  10.04 : 9.10 : 9.04 ]]("http://ubuntuforums.org/showthread.php?t=1466490")  POST  #[**10**]("http://ubuntuforums.org/showpost.php?p=9283123&postcount=10")

Did you visit the usb_modeswitch forum in the links mentioned in the howto

regards

alexfish

---

### Post by seddik_saber on 2010-08-20
I've deleted usb-modesswitch still the 3G modem work when plugged on boot, but when I unplug it and replug it it doesn't work (it was working before when i unplug it and replug i)
when I plug it during the boot without usb_modeswitch on my machine i see that the product code changed from  1446 to 141b (how is changing the product code ??)  if I unplug it and replug it I see that the product code is 1446 that's confirm that there are no usb_modesswitch installed

---

### Post by Sakis3G on 2010-08-20
Hi seddik,

> **seddik_saber said:**
> when I plug it during the boot without usb_modeswitch on my machine i see that the product code changed from  1446 to 141b (how is changing the product code ??)  if I unplug it and replug it I see that the product code is 1446 that's confirm that there are no usb_modesswitch installed

Some modems automatically switch mode (and some of them product ID along the way), on their own (_without_ the need for Usb-ModeSwitch) when they are simply "ejected". Reason we call it "eject" is that they indeed actually "fool" computer/operating system into presenting themselves as USB CD-ROMs (their commercial name now turns relative: "ZeroCD").

So, what actually happens, and your modem is switched already, when plugged during boot, is that someone "ejects" it, before Linux kernel is even loaded. Guess who is it?

Your BIOS! Some BIOSes (either erratically, or upon your directions), before passing boot sequence on your hard disk's MBR (Master Boot Record), where your boot loader resides (GRUB, Lilo etc.), they first check whether a bootable media is inserted on any attached CD-ROM/DVD-ROM. Given the fact that your modem pretends being one:

[LIST=1]
[*] BIOS has a look at it.
[*] Discovers it is not bootable, and
[*] Reverts procedure (so that operating system to be loaded, finds CD-ROM device on expected state).
[/LIST]
 
During revert/reset procedure, it instructs your "CD-ROM" accordingly (i.e. to consider itself "not-mounted" and allow itself to go in power save mode, and allow having its tray opened etc.). This is where your modem's firmware considers it was instructed to be "ejected" (actually, it was not. BIOS didn't tell it to eject. If it had, your system would be ejecting discs out of its real CD-ROM as well, during boot, but it doesn't. Does it?).

When Linux kernel is given control (BIOS->MODEM->BIOS->MBR->Loader->Kernel), modem has already switched (or is about to appear switched, while kernel still boots). This leads to another one "bad" effect: some (badly implemented) udev rules (of the "hotplug" subsystem) never get triggered. Reason is that device was never "hotplugged", it had been there since the very start. These all lead into some processes (which rely on badly implemented udev rules for being informed accordingly) to ignore the presence of your device and may event prevent you from actually using it.

If you need to disable this behavior, you need to investigate whether it is possible to alter your BIOS's boot sequence (some laptops may keep interfering, even if instructed not to boot from CD-ROMs). Either instruct it to directly boot from your hard disk, or have it consider optical drives not a valid boot source.

Sakis

---

### Post by seddik_saber on 2010-08-20
Sakis3G and Alexfish thank you for your help.
My issue is resolved now , I've only reinstall the rule on usb_modesswitch and it's work fine now.
maybe it's some config was wrong.
anyway many thx for your help.

---

### Post by khatkarrohit on 2010-12-01
I have the same Huawei E1752. I am using Ubuntu 10.10. I did not install anything. 

In starting it worked fine but after few hours my computer restarted automatically and again reboot if I leave the device plugged in PC.

If I remove the device my PC boot normally but if I plug it in any time with my PC PC again crash automatically and reboots. 

Its like PC get reset every time I plug it in.

---

### Post by alexfish on 2010-12-01
> **khatkarrohit said:**
> I have the same Huawei E1752. I am using Ubuntu 10.10. I did not install anything. 

In starting it worked fine but after few hours my computer restarted automatically and again reboot if I leave the device plugged in PC.

If I remove the device my PC boot normally but if I plug it in any time with my PC PC again crash automatically and reboots. 

Its like PC get reset every time I plug it in.

Possible may be a conflict between udev and usb-modeswitch
monitor the logfile viewer see what happening , and or the system monitor
can suggest trying to reinstall usb_modeswitch or disable

This device also has a habit of involuntary switching between modem mode and back to cd / can try disabling the CD part of the device via AT commands : Search the web

if it happens whist connected to the network : could use Sakis3g with -storage

READ in conjunction with above post #13  by Sakis
alexfish

---

