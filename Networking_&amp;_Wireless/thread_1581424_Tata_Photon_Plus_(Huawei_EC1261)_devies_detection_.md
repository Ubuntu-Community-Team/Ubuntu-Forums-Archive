---
title: "Tata Photon Plus (Huawei EC1261) devies detection problem"
date: 2010-09-24
forum: Networking &amp; Wireless
---

### Post by melwin.a3 on 2010-09-24
I am using Huawei EC1261 for internet.by installing usb modeswitch and updated usbmodeswitch data version.It works fine at first time only.after disconnect the modem or reboot.it fails to detect the device.but keep on plug and unplug the device more than 10 or 20 times it will detect by network manager and i can connect....

Showing  wrong ID 12d1:1440 first 10 or more time during plug and unplug the device
lsusb
Bus 002 Device 004: ID 12d1:1440 Huawei Technologies Co., Ltd. 

When Actual ID detect after 10 times plug and unplug
lsusb
Bus 002 Device 004: ID 12d1:140b Huawei Technologies Co., Ltd. 

dmesg -c
[  236.485550] usb 2-1.3: new full speed USB device using ehci_hcd and address 3
[  236.597864] usb 2-1.3: configuration #1 chosen from 1 choice
[  236.598572] scsi5 : SCSI emulation for USB Mass Storage devices
[  236.598742] usb-storage: device found at 3
[  236.598745] usb-storage: waiting for device to settle before scanning
[  237.596939] usb 2-1.3: USB disconnect, address 3
[  241.413208] usb 2-1.3: new full speed USB device using ehci_hcd and address 4
[  241.525160] usb 2-1.3: configuration #1 chosen from 1 choice
[  241.527516] scsi9 : SCSI emulation for USB Mass Storage devices
[  241.527793] usb-storage: device found at 4
[  241.527798] usb-storage: waiting for device to settle before scanning
[  241.714953] usbcore: registered new interface driver usbserial
[  241.715147] USB Serial support registered for generic
[  241.715394] usbcore: registered new interface driver usbserial_generic
[  241.715398] usbserial: USB Serial Driver core
[  241.724752] USB Serial support registered for GSM modem (1-port)
[  241.725249] option 2-1.3:1.0: GSM modem (1-port) converter detected
[  241.726124] usb 2-1.3: GSM modem (1-port) converter now attached to ttyUSB0
[  241.726684] option 2-1.3:1.1: GSM modem (1-port) converter detected
[  241.726881] usb 2-1.3: GSM modem (1-port) converter now attached to ttyUSB1
[  241.726924] option 2-1.3:1.2: GSM modem (1-port) converter detected
[  241.727115] usb 2-1.3: GSM modem (1-port) converter now attached to ttyUSB2
[  241.727151] usbcore: registered new interface driver option
[  241.727154] option: v0.7.2:USB Driver for GSM modems
[  246.522331] usb-storage: device scan complete
[  246.524748] scsi 9:0:0:0: CD-ROM            HUAWEI   Mass Storage     2.31 PQ: 0 ANSI: 0
[  246.526748] scsi 9:0:0:1: Direct-Access     HUAWEI   SD Storage       2.31 PQ: 0 ANSI: 2
[  246.543728] sr1: scsi-1 drive
[  246.544930] sr 9:0:0:0: Attached scsi CD-ROM sr1
[  246.545526] sr 9:0:0:0: Attached scsi generic sg3 type 5
[  246.547627] sd 9:0:0:1: Attached scsi generic sg4 type 0
[  246.555703] sd 9:0:0:1: [sdc] Attached SCSI removable disk
[  250.706918] ISO 9660 Extensions: Microsoft Joliet Level 1
[  250.721965] ISOFS: changing to secondary root
[  412.125308] PPP BSD Compression module registered
[  412.144448] PPP Deflate Compression module registered

---

### Post by melwin.a3 on 2010-09-25
before detecting the device

sudo dmesg -c
[ 7001.805534] usb 2-1.3: new full speed USB device using ehci_hcd and address 3
[ 7001.918254] usb 2-1.3: configuration #1 chosen from 1 choice
[ 7001.918738] scsi5 : SCSI emulation for USB Mass Storage devices
[ 7001.918871] usb-storage: device found at 3
[ 7001.918875] usb-storage: waiting for device to settle before scanning


lsusb

Bus 002 Device 003: ID 12d1:1446 Huawei Technologies Co., Ltd.



after detecting the device more than 10 times plug and unplug the usb modem
sudo dmesg -c
[ 7141.800557] usb 2-1.1: new full speed USB device using ehci_hcd and address 8
[ 7141.915761] usb 2-1.1: configuration #1 chosen from 1 choice
[ 7141.918566] scsi13 : SCSI emulation for USB Mass Storage devices
[ 7141.918837] usb-storage: device found at 8
[ 7141.918842] usb-storage: waiting for device to settle before scanning
[ 7141.967153] usbcore: registered new interface driver usbserial
[ 7141.967168] USB Serial support registered for generic
[ 7141.967240] usbcore: registered new interface driver usbserial_generic
[ 7141.967243] usbserial: USB Serial Driver core
[ 7141.982859] USB Serial support registered for GSM modem (1-port)
[ 7141.983087] option 2-1.1:1.0: GSM modem (1-port) converter detected
[ 7141.983282] usb 2-1.1: GSM modem (1-port) converter now attached to ttyUSB0
[ 7141.983311] option 2-1.1:1.1: GSM modem (1-port) converter detected
[ 7141.983434] usb 2-1.1: GSM modem (1-port) converter now attached to ttyUSB1
[ 7141.983466] option 2-1.1:1.2: GSM modem (1-port) converter detected
[ 7141.983598] usb 2-1.1: GSM modem (1-port) converter now attached to ttyUSB2
[ 7141.983646] usbcore: registered new interface driver option
[ 7141.983652] option: v0.7.2:USB Driver for GSM modems

lsusb
Bus 002 Device 008: ID 12d1:140b Huawei Technologies Co., Ltd.

---

### Post by alexfish on 2010-09-26
Hi

some of these devices take time to settle , some a lot more than others

what happens if you just sit and wait(no constant plugging) , does it eventually appear in the NM connection , or not

---

### Post by melwin.a3 on 2010-09-26
i am waiting for more than 5 min. its not detecing....

if lsusb shows huawei device
Bus 002 Device 003: ID 12d1:**1446** Huawei Technologies Co., Ltd
nm not detecting...
lsusb shows 
Bus 002 Device 008: ID 12d1:**140b** Huawei Technologies Co., Ltd.

i have to plug an unplug the device until it says 140b...

---

### Post by alexfish on 2010-09-26
hi

I have look through the data base for this device but can't find a listing

or have you written your own rules

does the following commands from the terminal show anything


cat /etc/usb_modeswitch.d/12d1:1440

regards

alexfish

---

### Post by melwin.a3 on 2010-09-27
friend,
i just checked cat/etc/usb_modeswitch.d/12d1:1440...its empty only

---

### Post by alexfish on 2010-09-27
hi

thought that would be the case ,

try booting up the the computer without the device , connect the device

does any device or file show on the desktop, if so

from the terminal

Code:

lsusb


try right-click and eject the device or file

and issue the command lsusb again see if anything changes , also try safely remove if nothing happens

Also check to see if this command works from the terminal/ post the results of only the device,( if the command works)

Code:

usb-devices

---

### Post by luvshines on 2010-09-27
This helps ??

[http://www.botskool.com/geeks/how-configure-tata-photon-ec1261-ubuntu-1004-lucid-lynx](http://www.botskool.com/geeks/how-configure-tata-photon-ec1261-ubuntu-1004-lucid-lynx)

---

### Post by luvshines on 2010-09-27
Maybe these can also be referred:

I followed this link to configure my friend's a couple of dayz ago, but don't know the model
[http://ubuntuforums.org/showthread.php?t=1545700&highlight=tata+photon](http://ubuntuforums.org/showthread.php?t=1545700&highlight=tata+photon)

See comment #22 in this. Looks gud:
[http://ubuntuforums.org/showthread.php?t=1491351&highlight=tata+photon&page=3](http://ubuntuforums.org/showthread.php?t=1491351&highlight=tata+photon&page=3)

---

### Post by alexfish on 2010-09-27
hi Lovshines

thanks for the input , just realised a possible typo or a bus error above RE id's Post#1
lsusb
Bus 002 Device 004: ID 12d1:1440 Huawei Technologies Co., Ltd.


the code  should have been

Code:

cat /etc/usb_modeswitch.d/12d1:1446

then shows

$ cat /etc/usb_modeswitch.d/12d1:1446
########################################################
# Huawei, newer modems

DefaultVendor= 0x12d1
DefaultProduct=0x1446

TargetVendor=  0x12d1
TargetProductList="1001,1406,140c,141b,14ac"

CheckSuccess=20

MessageContent="55534243123456780000000000000011060000000000000000000000000000"

so the rest of your post links may be correct

the only thing of note , is to why some times the device is configuring(as shown is some of the posts) without the Target Product been listed in the usb modeswitch data, hence the see what happens if the device is just simply ejected , and also the posting of the command " usb-devices "

thanks again

alexfish

---

### Post by melwin.a3 on 2010-09-27
actually my modem huawei ec1261 is **140b**..but it is showing [COLOR="DarkRed"]**1440**[/COLOR].....keep on plug and unplug than only it will detect 140b..and i can able to connect to the internet...

i am using ubuntu lucid 64 bit..usb modeswitch 1.1.3-1 and usb modeswitch data 20100707

---

### Post by alexfish on 2010-09-28
hi

yes I know , but at some stage the device id changes from 1440 to 1446 then to 140b

have you tried what is suggested in post #7

try the command " usb-devices" . this give the necessary info as to what is happening

or try the "lsusb -t" command , remember to follow the sequences mentioned

Also of note you appear to be using 64bit, have done several post concerning these devices (64 bit system) so I am presuming there may be a bug which may need to be reported

regards

alexfish

---

### Post by htbsupport on 2011-01-23
My Device still does not work its EC152 and Ubuntu 9.x OS

---

### Post by melwin.a3 on 2011-01-24
Hi friend
U have to do a lot in ubuntu 9.X to configure tata photon +.SOo try to use Ubuntu maverick meerkat 10.10..Its easily detect the tata photon device.

---

### Post by anisur.mullick on 2011-01-28
Successful configuration of TATA PHOTON+ on Kubuntu on DELL
-------------------------------------------------------------------------------
Modem: Huawei Modem 270+ (EC1261)

All the above post are good but scattered, so here I put a complete details altogether that will be required for the newer modem that has inbuilt storage.

1. You will need  usb-modeswitch, usb-modeswitch-data, wvdail . To install issue the command 'sudo apt-get install usb-modeswitch usb-modeswitch-data wvdial''.

2. Check your Modem device - After 5 sec of inserting the modem device, issue the command 'lsusb'
Here you will see your device as 'Bus 002 Device 025: ID 12d1:140b Huawei Technologies Co., Ltd.' or
'Bus 002 Device 007: ID 12d1:1446 Huawei Technologies Co., Ltd.'

3. To avoid any mis-configuration, edit the file '/etc/usb_modeswitch.d/12d1\:1446' at line TargetProductList="1001,1406,140c,14ac" to  TargetProductList="1001,1406,140c,14ac,140b"
Create a new file '/etc/usb_modeswitch.d/12d1\:140b:uMa=AnyDATA', you can issue the command
sudo cp  "/etc/usb_modeswitch.d/12d1:1446" "/etc/usb_modeswitch.d/12d1\:140b:uMa=AnyDATA".
In the new file '/etc/usb_modeswitch.d/12d1\:140b:uMa=AnyDATA', edit the line TargetProductList="1001,1406,140c,14ac,140b" to TargetProductList="140b"

4. Create the file '/etc/usb-modeswitch.conf' as follow:

########################################################
# Huawei E270+  (HSPA+ modem)

DisableSwitching=0

DefaultVendor= 0x12d1
DefaultProduct=0x1446

TargetVendor=  0x12d1
TargetProductList="1001,1406,140c,14ac,140b"
CheckSuccess=20

MessageContent="55534243123456780000000000000011060000000000000000000000000000"

HuaweiMode=1

EnableLogging=0

5. Then run the command 'sudo usb_modeswitch -c /etc/usb_modeswitch.d/12d1:140b:uMa=AnyDATA'
If it says that 'Waiting for original device to vanish ...', then after say 5 secs issue it again. Now, it will say

Original device is gone already, not checking
Searching for target devices ...
...............
Mode switch succeeded. Bye.

6. Setting up wvdial. Create/edit the file /etc/wvdial.conf. The file should look like

[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = Analog Modem
Baud = 115200
New PPPD = yes
Modem = /dev/ttyUSB0
ISDN = 0
Phone = #777
Password = internet
Username = internet

7. Checking modem : ls -l /dev/ttyU*, it will show something like

crw-rw---- 1 root dialout 188, 0 2011-01-28 16:07 /dev/ttyUSB0
crw-rw---- 1 root dialout 188, 1 2011-01-28 16:07 /dev/ttyUSB1
crw-rw---- 1 root dialout 188, 2 2011-01-28 16:07 /dev/ttyUSB2

8. Dial out - To connect issue the command sudo wvdial.

And you will be connected to internet using your TATA PHOTON+ on Kubuntu

---

### Post by LeonardoDaInvinci on 2011-02-12
Does this method work for Huwaei EC152 as well? Recently tata photon plus is shipped with this EC152 device. I googled for its specifications never I get it anywhere, not even on Huwaei site. Why TATA/Huwaei keeping EC152 hidden? Which is better EC152 or EC1261?

Well, My request is anything else is needed apart from the info given in this post to bring up EC152 device.

thanks.

---

### Post by tiwari.aditya on 2011-02-17
For Tata Photon Plus Huawei EC152 / EC 152
This device uses a flip/toggle device id and when conned to usb, it is detected as storage device.

Use a tool called **usb_modeswitch** to change the device to "modem mode"

Now Tata Photon Plus Huawei EC152 / EC 152 works fine for me on lucid.
Hacking android driver/conf to use it on android tablet.

---

### Post by Rishi.r on 2011-02-23
hi,
 m totally new to ubuntu.I jst recently installed ubuntu 9.10 and i wa able to connect my tata photon modem EC1261 in 9.10 and dint hve ane problem connecting to the internet.But after i updated to 10.04LTS i dnt get the option of connecting to tata photon+ in da connections.i tried installing usb-modeswitch data and usb-modeswitch,but this dint solve my problem.Please give me a solution for this

---

### Post by raja52 on 2011-03-09
> **tiwari.aditya said:**
> 

Now Tata Photon Plus Huawei EC152 / EC 152 works fine for me on lucid.
Hacking android driver/conf to use it on android tablet.

Hi,
I am interested in a driver for EC1261 for android tablet. Can you help me in getting a good solution?
Thanks in advance.):P

---

