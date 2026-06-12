---
title: "Help needed with Tata photon+ internet stick"
date: 2011-01-21
forum: Networking &amp; Wireless
---

### Post by viltsu_zzz on 2011-01-21
I'm a finn traveling long time in India. I have with me Nokia Booklet 3G minilaptop with Ubuntu 10.10. I bought Tata Docomo Photon+ internet stick, which according to manual should support Linux.
Manual says this device is Olive VME101 and sticker inside says: Qualcom 3G.

My laptop doesn't recognise the stick. According to manual an icon should appear on the desktop when connecting the stick. This does not happen.
lsusb shows correct info when stick is on, 'ID 201e:2009' like it should.

After that I give modprobe with these details, as in manual:
'sudo modprobe usbserial vendor=0x201e product=0x2009
For this I dont't get error or confirmation.

After that dmesg should find the stick and show the name of the modem, something like 'ttyUSB0'. This does not happen.
I have edited /etc/wvdial.conf file with correct number, id and pw.

When trying wvdialconf or wvdial, the modem is not found.

Installing new mobile wideband connection shows modem as Option N.V. globetrotter HSUPA modem. It also finds Tata Docomo, but also this way I cannot connect.

Testing is little complicated as I need to connect to the internet with my friends Windows laptop, with this same stick. Installing to Windows was easy PnP.

Please help me out of the misery of beeing forced to use Windows. Any steps or ideas are taken happily.

---

### Post by alexfish on 2011-01-21
Hi

can have a look a these threads

[FONT=Verdana][SIZE=2][http://start.ubuntuforums.org/showthread.php?p=6447749 ]("http://start.ubuntuforums.org/showthread.php?p=6447749")[/SIZE][/FONT][FONT=Verdana][SIZE=2]
[http://ubuntuforums.org/showthread.php?t=1008200](http://ubuntuforums.org/showthread.php?t=1008200)[/SIZE][/FONT] [FONT=Verdana][SIZE=2]

[/SIZE][/FONT]If is GOBI CHIPSET the gobi-loader can be installed from synaptic (ubuntu 10.10)

also have a look here 

[http://packages.debian.org/sid/gobi-loader](http://packages.debian.org/sid/gobi-loader)

can  download this to usb-stick on other computer , then it will self install when in Ubuntu

alexfish

---

### Post by anisur.mullick on 2011-01-28
Hi,

I have configured the HUAWEI modem, hope following the steps could help.


Successful configuration of TATA PHOTON+ on Kubuntu on DELL
-------------------------------------------------------------------------------
Modem: Huawei Modem 270+ (EC1261)

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
Check it out at [http://armtechnologies.com/blog/?p=6](http://armtechnologies.com/blog/?p=6)

Good luck!

---

