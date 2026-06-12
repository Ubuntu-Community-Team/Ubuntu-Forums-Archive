---
title: "Option icon 505 USB modem under Ubuntu 9.10"
date: 2009-12-06
forum: Networking &amp; Wireless
---

### Post by Firidan on 2009-12-06
How do I get icon 505 USB modem to work under ubuntu?
I have searched the internet and found many tutorials for ubuntu 9.04 but not for 9.10.

Please, I'm desperate!

---

### Post by pdc on 2009-12-07
tell us what you have tried;

is it anything like this

[http://www.pharscape.org/networkmanager-0.7.0-and-3g-wwan-modems.html](http://www.pharscape.org/networkmanager-0.7.0-and-3g-wwan-modems.html)

go to "Create a mobile broadband connection"; half-way down page

---

### Post by Firidan on 2009-12-07
Yes. That's the guide I tried. I installed ozerocdoff 0.4 from [https://forge.betavine.net/frs/?group_id=12&release_id=14](https://forge.betavine.net/frs/?group_id=12&release_id=14).
Then added these rules:
ATTRS{idVendor}=="0af0", ATTRS{idProduct}=="d055", RUN+="/usr/sbin/ozerocdoff -wi 0x%s{idProduct}"

SUBSYSTEM=="usb_device", SYSFS{idVendor}=="0af0", SYSFS{idProduct}=="d055", SYSFS{bDeviceClass}=="00", RUN+="/usr/sbin/ozerocdoff -wi 0x%s{idProduct}"

to /etc/udev/rules.d/51-hso-udev.rules

I didn't install HSO connect since ubuntu 9.10 is supposed to have it.

I tried another guide at: [http://translate.google.com/translate?js=y&prev=_t&hl=en&ie=UTF-8&layout=1&eotf=1&u=http%3A%2F2Fjorgenmodin.net%2Findex_html%2Farchive%2F2009%2F08%2F09%2Ff-3g-modemet-option-505-att-fungera-med-ubuntu-linux&sl=sv&tl=en](http://translate.google.com/translate?js=y&prev=_t&hl=en&ie=UTF-8&layout=1&eotf=1&u=http%3A%2F2Fjorgenmodin.net%2Findex_html%2Farchive%2F2009%2F08%2F09%2Ff-3g-modemet-option-505-att-fungera-med-ubuntu-linux&sl=sv&tl=en)

But it didn't work either.

---

### Post by Firidan on 2009-12-08
Come on! Anyone!

---

### Post by alexfish on 2009-12-08
> **Firidan said:**
> Come on! Anyone!


Hi

can I have some basic Info

People sometimes get confused about what modem they have. Often the company that supplied it will rename the device. The solution is to locate the serial number. The** first 2 letters** of the serial number are unique and can be used to identify the device . This may help me To find the Device Without  Doing the below
.............................................................................................................................................................................................................................................................................................................
 to find the device there

 are three basic commands

from a fresh boot

open up terminals first

''''''''   do this in two seperate terminals '''''''

plug the device in

first terminal 

lsusb

 ls -al /dev/ttyU* 


second terminal

tail -f /var/log/syslog


 and post the two outputs


also you can try these

                                 dmesg | grep "modem"
 

 dmesg | grep -e "modem" -e "tty" 


see if you can find the  device id  from device manager

 also can I ask is it 505 or 505M

---

### Post by alexfish on 2009-12-08
Hi 
my advice at present is

 Not to download from betavine, the mobile connect may not work in Version 9.10
     
    you have what you need in the repos  . I think.

---

### Post by Firidan on 2009-12-10
Here are the outputs

**Command**:

lsusb

Output:

Bus 008 Device 002: ID 09da:000a A4 Tech Co., Ltd Port Mouse
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 007: ID 0af0:d055 Option 
Bus 002 Device 005: ID 1784:000a TopSeed Technology Corp. 
Bus 002 Device 004: ID 0bda:0151 Realtek Semiconductor Corp. Mass Stroage Device
Bus 002 Device 002: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 03f0:0f0c Hewlett-Packard Wireless Keyboard and Optical Mouse
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

**Command**:

ls -al /dev/ttyU*

Output:

ls: cannot access /dev/ttyU*: No such file or directory


**Command**:

tail -f /var/log/syslog

Output:

Dec 10 13:38:38 UnixPC NetworkManager: <info>  (hso0): device state change: 1 -> 2 (reason 2)

Dec 10 13:38:38 UnixPC NetworkManager: <info>  (hso0): deactivating device (reason: 2).

Dec 10 13:38:38 UnixPC NetworkManager: <info>  (hso0): device state change: 2 -> 3 (reason 0)

Dec 10 13:38:52 UnixPC ntfs-3g[1965]: Version 2009.4.4 external FUSE 27

Dec 10 13:38:52 UnixPC ntfs-3g[1965]: Mounted /dev/sda1 (Read-Write, label "HP", NTFS 3.1)

Dec 10 13:38:52 UnixPC ntfs-3g[1965]: Cmdline options: rw,nosuid,nodev,uhelper=devkit,uid=1000,gid=1000,dmask=0077

Dec 10 13:38:52 UnixPC ntfs-3g[1965]: Mount options: rw,nosuid,nodev,uhelper=devkit,silent,allow_other,nonempty,default_permissions,relatime,fsname=/dev/sda1,blkdev,blksize=4096

Dec 10 13:39:18 UnixPC wpa_supplicant[1289]: CTRL-EVENT-SCAN-RESULTS 

Dec 10 13:40:08 UnixPC wpa_supplicant[1289]: CTRL-EVENT-SCAN-RESULTS 

Dec 10 13:41:08 UnixPC wpa_supplicant[1289]: CTRL-EVENT-SCAN-RESULTS 

Dec 10 13:42:08 UnixPC wpa_supplicant[1289]: CTRL-EVENT-SCAN-RESULTS 

Dec 10 13:42:49 UnixPC anacron[1583]: Job `cron.daily' started
Dec 10 13:42:49 UnixPC anacron[2023]: Updated timestamp for job `cron.daily' to 2009-12-10

Dec 10 13:43:08 UnixPC wpa_supplicant[1289]: CTRL-EVENT-SCAN-RESULTS 

Dec 10 13:44:01 UnixPC kernel: [  392.654111] usb 2-5.1: reset high speed USB device using ehci_hcd and address 4

Dec 10 13:44:08 UnixPC wpa_supplicant[1289]: CTRL-EVENT-SCAN-RESULTS 

Dec 10 13:45:08 UnixPC wpa_supplicant[1289]: CTRL-EVENT-SCAN-RESULTS 

Dec 10 13:46:08 UnixPC wpa_supplicant[1289]: CTRL-EVENT-SCAN-RESULTS 

Dec 10 13:46:16 UnixPC NetworkManager: <info>  Activation (hso0) starting connection 'Telia Default 1'
Dec 10 13:46:16 UnixPC NetworkManager: <info>  (hso0): device state change: 3 -> 4 (reason 0)

Dec 10 13:46:16 UnixPC NetworkManager: <info>  Activation (hso0) Stage 1 of 5 (Device Prepare) scheduled...

Dec 10 13:46:16 UnixPC NetworkManager: <info>  Activation (hso0) Stage 1 of 5 (Device Prepare) started...

Dec 10 13:46:16 UnixPC NetworkManager: <info>  Activation (hso0) Stage 1 of 5 (Device Prepare) complete.

Dec 10 13:46:16 UnixPC modem-manager: (ttyHS1) opening serial device...

Dec 10 13:46:16 UnixPC NetworkManager: <info>  (hso0): device state change: 4 -> 6 (reason 0)
Dec 10 13:46:17 UnixPC modem-manager: Invalid error code
Dec 10 13:46:17 UnixPC modem-manager: Got failure code 100: Unknown error
Dec 10 13:46:17 UnixPC modem-manager: (ttyHS1) closing serial device...

Dec 10 13:46:23 UnixPC NetworkManager: <info>  Activation (hso0) Stage 1 of 5 (Device Prepare) scheduled...

Dec 10 13:46:23 UnixPC NetworkManager: <info>  Activation (hso0) Stage 1 of 5 (Device Prepare) started...

Dec 10 13:46:23 UnixPC NetworkManager: <info>  (hso0): device state change: 6 -> 4 (reason 0)

Dec 10 13:46:23 UnixPC NetworkManager: <info>  Activation (hso0) Stage 1 of 5 (Device Prepare) complete.

Dec 10 13:46:23 UnixPC modem-manager: (ttyHS1) opening serial device...

Dec 10 13:46:25 UnixPC modem-manager: Registration state changed: 2
Dec 10 13:46:28 UnixPC modem-manager: Registration state changed: 1

Dec 10 13:46:29 UnixPC modem-manager: Got failure code 100: Unknown error

Dec 10 13:46:29 UnixPC NetworkManager: <WARN>  stage1_prepare_done(): GSM modem connection failed: Unknown error

Dec 10 13:46:29 UnixPC NetworkManager: <info>  (hso0): device state change: 4 -> 9 (reason 1)

Dec 10 13:46:29 UnixPC NetworkManager: <info>  Marking connection 'Telia Default 1' invalid.
Dec 10 13:46:29 UnixPC NetworkManager: <info>  Activation (hso0) failed.
Dec 10 13:46:29 UnixPC NetworkManager: <info>  (hso0): device state change: 9 -> 3 (reason 0)
Dec 10 13:46:29 UnixPC NetworkManager: <info>  (hso0): deactivating device (reason: 0).
Dec 10 13:46:29 UnixPC modem-manager: (ttyHS1) closing serial device...


**Command**:

dmesg | grep "modem"

Output:

Doesn't do anything(just like pressing enter)


**Command**:

dmesg | grep -e "modem" -e "tty" 

Output:

[    0.001134] console [tty0] enabled

---

### Post by alexfish on 2009-12-10
Hi


You Entered The Wrong Code

if you have "other " devices pluged in can you remove them while testing

 The Code is

 ls -al /dev/ttyU*

 Also can you post the First Two Letters of the serial Number of the Device


  *Is Your Provider Orange / or check your payment plan/ *check to see if "" hsolinkcontrol""  is installed  if not / it is available from Debian

---

### Post by Firidan on 2009-12-10
how do find out the serial number of the modem?

---

### Post by alexfish on 2009-12-10
Hi
the device  Should have two labels on it 

  the one you want should start with SN. "" _AA_"" nnnnnnnnn
     they are usually letters  where ""AA " =   ch, gh  and so on

     you may need a magnifying glass to find them

  Is it Orange mobile

---

### Post by Firidan on 2009-12-11
my intdrnet provider is telia. i am sure that it is icon 505.

---

### Post by Firidan on 2009-12-11
The only letters I could find are PTION [IMG]http://www.telia.se/images2/mbb_justnu_344x69-3.png[/IMG]

---

### Post by Firidan on 2009-12-13
Come on! Please help!

---

### Post by alexfish on 2009-12-14
> **Firidan said:**
> Come on! Please help!

Hi 

look here And follow the instructions very carefully 

 [I]Re:  Option iCON 515m wireless USB modem (Orange)
[/I]
[http://ubuntuforums.org/showthread.php?t=1351612](http://ubuntuforums.org/showthread.php?t=1351612)

  update to the drivers

---

### Post by Firidan on 2009-12-16
It didn't work.
I got an error massage: "NO INTERNET CONTROLL!!!"

---

### Post by alexfish on 2009-12-16
> **Firidan said:**
> It didn't work.
I got an error massage: "NO INTERNET CONTROLL!!!"

Hi

Where is Your Location//

RE :   Memo When Posting : Let us Know

 1: Your Location 

 2: Your Provider

 3: Your Pay Plan

 4: Type of Device

...........................................................................

I got an error massage: "NO INTERNET CONTROLL!!!"

The Meaning of this Message Look Here


[http://en.wikipedia.org/wiki/Transmission_Control_Protocol](http://en.wikipedia.org/wiki/Transmission_Control_Protocol)




[URL="http://ubuntuforums.org/showthread.php?t=1331317"]
[/URL]

---

### Post by alexfish on 2009-12-16
[SIZE=4]For :[COLOR=Navy]Sweden Telia[/COLOR]
[/SIZE] 
see screen shots do not take notice of my my provider

also there is an update for the driver  // if you are a novice try to seek help / 

The update is here

[http://ubuntuforums.org/showthread.php?t=1351612](http://ubuntuforums.org/showthread.php?t=1351612)

also try to uninstall the ozerocdoff

also do you have a _[SIZE=2][COLOR=Navy]pin code activated[/COLOR][/SIZE]_ on the device  and do you Know your[COLOR=Blue] _PUK_[/COLOR] Code

Thanks in advance

alexfish

---

### Post by Firidan on 2009-12-18
It works now!!!!!!!!!!!!!!!!!!!!!!!!!!!!!:P

I just had to add
ATTRS{idVendor}=="0af0", ATTRS{idProduct}=="d055", RUN+="/usr/sbin/ozerocdoff -wi 0x%s{idProduct}"

and

SUBSYSTEM=="usb_device", SYSFS{idVendor}=="0af0", SYSFS{idProduct}=="d055", SYSFS{bDeviceClass}=="00", RUN+="/usr/sbin/ozerocdoff -wi 0x%s{idProduct}"


to

/etc/udev/rules.d/51-hso-udev.rules


Thanks for your help!!!!!!!!!!!!!!!!

---

