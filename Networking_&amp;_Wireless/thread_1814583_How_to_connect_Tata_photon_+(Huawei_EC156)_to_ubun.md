---
title: "How to connect Tata photon +(Huawei EC156) to ubuntu natty"
date: 2011-07-29
forum: Networking &amp; Wireless
---

### Post by jayadeep on 2011-07-29
Please ensure that you have installed the following packages
 *  usb-modeswitch-data
 *  usb-modeswitch

Connect the device and see whether it is detected automatically in the network manager
if not do the following things.
.Open the terminal
.Type
```
sudo nautilus
```
A new window will be opened for root
.Go to filesystems ----/etc/usb_modeswitch.d
.Create a new config file named **12d1:1505**
 .Cut and Paste the following  
 ```
DefaultVendor= 0x12d1 
DefaultProduct=0x1505 

MessageContent="55534243123456780000000000000011062000000100000000000000000000" 
  
```
 .Save the file
 .Go to terminal  
 .Go to the path by the code  
 ```
cd /etc/usb_modeswitch.d
```
 .Type the command
 ```
sudo usb_modeswitch -I -W -c 12d1\:1505
```
 .It may connect automatically..
 .Just wait for one minute
 .The default network manager may detect your device and follow the instructions by it
 mark it to **connect automatically** in the **mobile broadband** **edit** options
 .If not open your **network mannager** go to **manage connection**
 open the **mobile broadband** and **add** a new connection
 if it detects installed **CDMA device** or **Huawei EC156** follow the instruction given by the network manager
 mark it to **connect automatically** in the **mobile broadband edit** options
 .Rebbot your system and  see it is connected automatically  
 .If not you have to type the two codes mentioned above all the times when you connect your device
 It will be very diffficult to type the codes all the time....so go for the following steps to run that commands automattically


STEPS
Script to run the modeswitch command in boot
steps
1.Open the gedit
2.Type the two commands which you want to run in two separate lines.
3.save the file with the extension **.sh** on the disk where ever you want and make this file **as executable** in the **properties**
4.Then **right click** on the desktop
5 Create **launcher**
6.Set **type** as **Run in terminal**
7.Give your desired name
8.Give the path of file with the extension **.sh** in the **command** box
9.Hit **ok**

Open the launcher.....
enter the password if required

You can change your icon in the properties of the new launcher file

Connect your device when ever required and  click the new icon on the desktop
 Hit the password.....
 enjoy...

---

### Post by drpjkurian on 2011-07-30
Let me make it clear that the command to be typed in gedit to run the modeswitch in boot will be as follows
```
cd /etc/usb_modeswitch.d
sudo usb_modeswitch -I -W -c 12d1\:1505
```

---

### Post by gunashekar on 2011-08-05
Thank you very much. 
I have been trying for a month and Tata indicom service people were sending me from pillar to post. Your post helped me finally.
I was only able to connect by using those terminal commands every time I boot. It connected without a launcher first time. When i created a launcher and used it, I got a permission error. then I realized I did not make the .sh file as an executable file by setting the properties. now it works fine.
Thank you again.

---

### Post by drpjkurian on 2011-08-11
Happy to hear that you have solved it.

---

### Post by prashv on 2011-11-07
Hi people,

Although I tried the same steps to connect Tata Photon EC156 with Ubuntu 11.04 but getting following errors: 
eprasvi@5SF3WQ1:/etc/usb_modeswitch.d$ sudo usb_modeswitch -I -W -c 12d1\:1505
[sudo] password for eprasvi: 

Reading config file: 12d1:1505

 * usb_modeswitch: handle USB devices with multiple modes
 * Version 1.1.6 (C) Josua Dietze 2010
 * Based on libusb0 (0.1.12 and above)

 ! PLEASE REPORT NEW CONFIGURATIONS !

DefaultVendor=  0x12d1
DefaultProduct= 0x1505
TargetVendor=   not set
TargetProduct=  not set
TargetClass=    not set
TargetProductList=""

DetachStorageOnly=0
HuaweiMode=0
SierraMode=0
SonyMode=0
GCTMode=0
KobilMode=0
MessageEndpoint=  not set
MessageContent="55534243123456780000000000000011062000000100000000000000000000"
NeedResponse=0
ResponseEndpoint= not set
Interface=0x00

InquireDevice disabled
Success check disabled
System integration mode disabled

usb_set_debug: Setting debugging level to 15 (on)
usb_os_find_busses: Found 002
usb_os_find_busses: Found 001
usb_os_find_devices: Found 008 on 002
usb_os_find_devices: Found 003 on 002
skipped 1 class/vendor specific interface descriptors
skipped 1 class/vendor specific interface descriptors
usb_os_find_devices: Found 002 on 002
usb_os_find_devices: Found 001 on 002
error obtaining child information: Inappropriate ioctl for device
error obtaining child information: Inappropriate ioctl for device
usb_os_find_devices: Found 004 on 001
skipping descriptor 0xB
skipped 1 class/vendor specific endpoint descriptors
skipped 6 class/vendor specific interface descriptors
skipping descriptor 0x25
skipped 1 class/vendor specific endpoint descriptors
skipped 19 class/vendor specific interface descriptors
skipping descriptor 0xFF
skipped 1 class/vendor specific endpoint descriptors
usb_os_find_devices: Found 003 on 001
skipped 2 class/vendor specific interface descriptors
usb_os_find_devices: Found 002 on 001
usb_os_find_devices: Found 001 on 001
error obtaining child information: Inappropriate ioctl for device
error obtaining child information: Inappropriate ioctl for device

Looking for default devices ...
  searching devices, found USB ID 12d1:1505
   found matching vendor ID
   found matching product ID
   adding device
  searching devices, found USB ID 0a5c:5800
  searching devices, found USB ID 8087:0024
  searching devices, found USB ID 1d6b:0002
  searching devices, found USB ID 05ca:181e
  searching devices, found USB ID 413c:8187
  searching devices, found USB ID 8087:0024
  searching devices, found USB ID 1d6b:0002
 Found devices in default mode, class or configuration (1)
Accessing device 008 on bus 002 ...
Getting the current device configuration ...
 OK, got current device configuration (1)
Using endpoints 0x08 (out) and 0x87 (in)
Using endpoints 0x08 (out) and 0x87 (in)

USB description data (for identification)
-------------------------
Manufacturer: HUA&#65533;WEI TECHNOLOGIES
     Product: HUAWEI Mobile
  Serial No.: &#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;
-------------------------
Looking for active driver ...
 OK, driver found ("usb-storage")
 OK, driver "usb-storage" detached
Setting up communication with interface 0 ...
Using endpoint 0x08 for message sending ...
Trying to send message 1 to endpoint 0x08 ...
 OK, message successfully sent
Resetting response endpoint 0x87
Resetting message endpoint 0x08
USB error: could not clear/halt ep 8: Broken pipe
 Error resetting endpoint: -32
USB error: could not release intf 0: No such device
 Device is gone, skipping any further commands
-> Run lsusb to note any changes. Bye.

eprasvi@5SF3WQ1:/etc/usb_modeswitch.d$ 
eprasvi@5SF3WQ1:/etc/usb_modeswitch.d$ lsusb
Bus 002 Device 009: ID 12d1:140b Huawei Technologies Co., Ltd. EC1260 Wireless Data Modem HSD USB Card
Bus 002 Device 003: ID 0a5c:5800 Broadcom Corp. BCM5880 Secure Applications Processor
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 05ca:181e Ricoh Co., Ltd 
Bus 001 Device 003: ID 413c:8187 Dell Computer Corp. DW375 Bluetooth Module
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
eprasvi@5SF3WQ1:/etc/usb_modeswitch.d$ 

-------------------------------

After this at least I am able to see on Computer "Huawei USB Storage" icon but can't do anything with it.
It also shows "Tata Indicom .... " in networks but not able to connect from it.

Not sure what to do next? 

Please help.

---

### Post by Praveen P on 2011-11-16
Even I am facing the same issue... 


I am getting the following message... I am using ubuntu 10.10 itself.


USB error: could not clear/halt ep 8: Broken pipe
 Error resetting endpoint: -32
-> Run lsusb to note any changes. Bye



bash$:/etc/usb_modeswitch.d$ lsusb 
Bus 002 Device 011: ID 12d1:140b Huawei Technologies Co., Ltd. EC1260 Wireless Data Modem HSD USB Card
Bus 002 Device 008: ID 04f3:0232 Elan Microelectronics Corp. 
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 0c45:6407 Microdia 
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub



I doubt if I am doing the correct configuration.. in the lsusb, the Huawei device is marked as 1260, even though this post was for EC156..... I doubt if I am missing anything....

Please help...


______
Regards
Praveen P

---

### Post by mehulphy on 2011-12-09
Well, the answer suggested by Jayadeep is absolutely right, but the problems occurring (as reported by prashv and Praveen P) can be solved by adding two additional line to the code written in the 12d1:1505 file situated at /etc/usbmodeswitch.d directory. Let me put the complete code again with addition of two lines.

```
DefaultVendor= 0x12d1  
DefaultProduct=0x1505   

MessageContent="55534243123456780000000000000011062000000100000000000000000000"

NeedResponse=1 

CheckSuccess=10
```After this run following command:

```
sudo usb_modeswitch -c /etc/usb_modeswitch.d/12d1\:1505
```[COLOR=#000000][FONT=Verdana]

Actually, if you don't want to run the command 

[/FONT][/COLOR]sudo usb_modeswitch -c /etc/usb_modeswitch.d/12d1\:1505[COLOR=#000000][FONT=Verdana]

every time after you plug in, then do the following.

1) Open terminal
2) Write "gedit" and press "enter key"
3) Text editor will open, now paste the command

sudo usb_modeswitch -c /etc/usb_modeswitch.d/12d1\:1505

4) Click "Save", and name the file "tata.sh" (You can give your own name)
5) Now, every time you don't have to run that long command, 

instead run 

[/FONT][/COLOR]```
./tata.sh
```[COLOR=#000000][FONT=Verdana]

Enjoy......:smile:[/FONT][/COLOR]

---

### Post by itskaur on 2011-12-24
Hi, Thanks for the post. It helped me connect my photon to ubuntu.

Isn't there anyway that photon is detected everytime and we don't have to run this ./tata.sh ??

---

### Post by Senthil.sub on 2012-01-22
i followed the instruction and did the below...
Installed usb-modeswitch-data and usb-modeswitch
Created /etc/usb_modeswitch.d/12d1:1505
Ran 'sudo usb_modeswitch -I -W -c 12d1\:1505' and got the below output int the terminal

[I]         Note: target parameter missing; success check limited
        Looking for default devices ...
         Found default devices (1)
        Accessing device 002 on bus 002 ...
        Using endpoints 0x08 (out) and 0x87 (in)
        Inquiring device details; driver will be detached ...
        Looking for active driver ...
         OK, driver found ("usb-storage")
         OK, driver "usb-storage" detached

        SCSI inquiry data (for identification)[/I] [I]
        -------------------------
          Vendor String: HUAWEI  
           Model String: Mass Storage    
        Revision String: 2.31
        -------------------------

        USB description data (for identification)[/I] [I]
        -------------------------
        Manufacturer: HUA&#65533;WEI TECHNOLOGIES
             Product: HUAWEI Mobile
          Serial No.: ???????????????
        -------------------------
        Setting up communication with interface 0 ...
        Trying to send the message to endpoint 0x08 ...
         OK, message successfully sent
        Reading the response to the message ...
         OK, response successfully read (0 bytes).
         Device is gone, skipping any further commands

        Checking for mode switch (max. 10 times, once per second) ...[/I] [I]
         Original device is gone already, not checking
         (For a better success check provide target IDs or class)
         Original device vanished after switching

        Mode switch most likely succeeded. Bye.[/I]  
the device was not detected automatically, then i tried "Edit Connections..." and the "Mobile broadband" and clicked "Add", no items was enabled in the drop down box.
When i tried reconnecting the Tata Photon+ device its automounted as usb device and it asked for ".. application to launch.." pop up.

Thanks for your help in advance

---

### Post by nicolas.bernaerts on 2012-01-22
A simple guide is available at [http://bernaerts.dyndns.org/linux/209-ubuntu-tata-photonplus](http://bernaerts.dyndns.org/linux/209-ubuntu-tata-photonplus)

It has been tested with a Photon + USB key bought 1 week ago.

Hope it helps.

Nick

---

### Post by sriparandhama on 2012-03-02
Hi Friends ,

Iam able to connect through this procedure.

Thanks a lot !!!!!  :P:D

---

### Post by vgad on 2012-03-27
These Tata Photon chaps keep changing their datacard models, currently they are issuing EC156. Had to mix and match from various posts on this thread to get a foolproof method, that worked on laptops and desktops, for Ubuntu 10.10 and 11.04. And thanks to all those from whose posts I mixed and matched.

--

STEPS 
1) Plug in your Tata Photon. 
2) In a terminal, on command line.... 
Type "cd /etc/usb_modeswitch.d". Press "Enter". 
3) Type "sudo gedit". Press "Enter". 
4) Text editor will open. Paste the following text. 

#### 

DefaultVendor= 0x12d1  
DefaultProduct=0x1505   

MessageContent="55534243123456780000000000000011062000000100000000000000000000" 

NeedResponse=1 

CheckSuccess=10 

---- 

5) Click 'Save' and save the file as 12d1:1505 
6) In terminal, type sudo usb_modeswitch -c /etc/usb_modeswitch.d/12d1\:1505 
7) Supply your sudo password. 
After you do this, you should get a message with something like this. The important thing is the last line, “Mode switch most likely succeeded. Bye.”

Note: target parameter missing; success check limited 
Looking for default devices ... 
 Found devices in default mode, class or configuration (1) 
Accessing device 027 on bus 001 ... 
......
......
.......
Mode switch most likely succeeded. Bye. 

8) Go to System -> Preferences -> Network Connections and click on the Mobile Broadband tab. Select 'Add'. It will show you the Huawei connection. Click 'Forward'. Choose 'India'. Choose 'Tata Indicom (Photon+)' Click on 'Save'. Also check the 'Connect automatically' and 'Show Password' boxes. 
9) Wait for some time, and click on the Indicator Applet on the Right-Hand Side of the Top Panel, and then on the menu that appears, click on the 'Tata Indicom (Photon+) Connection'. And, eureka, you will get connected. 
10) Whenever you want to log on again, insert the datacard, and type “sudo usb_modeswitch -c /etc/usb_modeswitch.d/12d1\:1505”. Supply sudo password. It should connect automatically after a few seconds, but if it does not, follow instructions in point 9. 
11) if you don't want to run the command “sudo usb_modeswitch -c /etc/usb_modeswitch.d/12d1\:1505 every time after you plug in, then do the following:
a) Open terminal
b) Write "gedit" and press "enter key". Text editor will open, now paste the command “sudo usb_modeswitch -c /etc/usb_modeswitch.d/12d1\:1505”.
c) Click "Save", and name the file "photon.sh". In future, you will not have to type the full command, instead run “./photon.sh”.

---

### Post by urveshmendhe on 2012-04-16
Guys have a look around for easy installation

copy and paste these lines in to file

[B]cd /etc/usb_modeswitch.d/
touch 12d1:1505
cat <<EOF >12d1:1505
DefaultVendor= 0x12d1  
DefaultProduct=0x1505   
MessageContent="55534243123456780000000000000011062000000100000000000000000000"
NeedResponse=1 
CheckSuccess=10
EOF

cd /etc/usb_modeswitch.d/
sudo usb_modeswitch -I -W -c 12d1\:1505 [/B]

and Save the file and rename eg. "tataphoton.sh"
sudo chmod +x tataphoton.sh
sudo sh tataphoton.sh


done !!!
You can now check with "lsusb"

---

### Post by timeer on 2012-04-25
> **jayadeep said:**
> Please ensure that you have installed the following packages
 *  usb-modeswitch-data
 *  usb-modeswitch

Connect the device and see whether it is detected automatically in the network manager
if not do the following things.
.Open the terminal
.Type
```
sudo nautilus
```
A new window will be opened for root
.Go to filesystems ----/etc/usb_modeswitch.d
.Create a new config file named **12d1:1505**
 .Cut and Paste the following  
 ```
DefaultVendor= 0x12d1 
DefaultProduct=0x1505 

MessageContent="55534243123456780000000000000011062000000100000000000000000000" 
  
```
 .Save the file
 .Go to terminal  
 .Go to the path by the code  
 ```
cd /etc/usb_modeswitch.d
```
 .Type the command
 ```
sudo usb_modeswitch -I -W -c 12d1\:1505
```
 .It may connect automatically..
 .Just wait for one minute
 .The default network manager may detect your device and follow the instructions by it
 mark it to **connect automatically** in the **mobile broadband** **edit** options
 .If not open your **network mannager** go to **manage connection**
 open the **mobile broadband** and **add** a new connection
 if it detects installed **CDMA device** or **Huawei EC156** follow the instruction given by the network manager
 mark it to **connect automatically** in the **mobile broadband edit** options
 .Rebbot your system and  see it is connected automatically  
 .If not you have to type the two codes mentioned above all the times when you connect your device
 It will be very diffficult to type the codes all the time....so go for the following steps to run that commands automattically


STEPS
Script to run the modeswitch command in boot
steps
1.Open the gedit
2.Type the two commands which you want to run in two separate lines.
3.save the file with the extension **.sh** on the disk where ever you want and make this file **as executable** in the **properties**
4.Then **right click** on the desktop
5 Create **launcher**
6.Set **type** as **Run in terminal**
7.Give your desired name
8.Give the path of file with the extension **.sh** in the **command** box
9.Hit **ok**

Open the launcher.....
enter the password if required

You can change your icon in the properties of the new launcher file

Connect your device when ever required and  click the new icon on the desktop
 Hit the password.....
 enjoy...


sorry nothing can be edited in usb-modeswitch can anyone help me out how i can create directory thr.

---

### Post by treehermit on 2012-07-08
Hi,

I tried connecting a tata photon EC156 on my ubuntu 12.04. nm detects my datacard but fails to connect to the internet. i've tried the above procedures and am able to get the following msg:

"[I]Mode switch most likely succeeded. Bye."

everything looks good & i get no error msg. i click on the 'tata photon+' icon in network manager & all i get is a notification that i'm disconnected.

please help!

am using a DELL XPS 15 (L502x) system with a dual booot of win 7 & ubuntu 12.04.

[/I]

---

### Post by Yasho on 2012-07-18
> **itskaur said:**
> Hi, Thanks for the post. It helped me connect my photon to ubuntu.

Isn't there anyway that photon is detected everytime and we don't have to run this ./tata.sh ??

Hi,
Just saw your post today. In reply , if you can stand the Unity desktop, 12.04 automatically connects you. Just plug in the device, wait a half minute or so, then, click on the network icon top right. In the drop-down menu, you will see the option to connect to Tata Indicom. If you click to enable, you will automatically be logged in. Pretty neat, I think. I'll probably get myself used to the Unity interface, just for this!!!
:popcorn::)

---

### Post by surmabhopali on 2012-07-22
> **ypm said:**
> Hi,
Just saw your post today. In reply , if you can stand the Unity desktop, 12.04 automatically connects you. Just plug in the device, wait a half minute or so, then, click on the network icon top right. In the drop-down menu, you will see the option to connect to Tata Indicom. If you click to enable, you will automatically be logged in. Pretty neat, I think. I'll probably get myself used to the Unity interface, just for this!!!
:popcorn::)

this has helped me to finally migrate to ubuntu....thanks a lot..:)

---

### Post by treehermit on 2012-07-25
this solution worked for me.. thanks !

---

### Post by anantha64 on 2012-10-24
This is whats comming if i run the last part of connecting

> Note: target parameter missing; success check limited
Looking for default devices ...
 No devices in default mode found. Nothing to do. Bye.

what do i do i followed the steps on running lsusb

it shows the device as ec1260

any help
[i'm new to this place okay]:guitar::confused:

---

### Post by gasper43 on 2012-12-12
I am sure many would be doubtful about these procedures and hope to see active participation in the days to come too. I wish you would come up with relevant topics in networking and communication in future too maintaining the same quality. [santa barbara hotels on the beach](http://www.findertravel.com/best-way-to-make-a-fabulous-vacation-to-las-vegas/)
_______________________
Gasper Milton

---

### Post by rooba on 2013-01-11
copy  paste this into a file [say photon.sh] and run sudo ./photon.sh

cd /etc/usb_modeswitch.d/
touch 12d1:140b
cat <<EOF >12d1:140b
DefaultVendor= 0x12d1
DefaultProduct=0x140b
MessageContent="55534243123456780000000000000011062000000100000000000000000000"
NeedResponse=1
CheckSuccess=10
EOF

cd /etc/usb_modeswitch.d/
sudo usb_modeswitch -I -W -c 12d1\:140b 


P.S:
 vendor id=12d1
product id=140b

change as per device,by doing lsusb u can find this :)

---

### Post by Sandeep_Tripathy on 2013-10-26
It worked, I can't express my gratitude to you Jaydeep. Thanks a lot !!

---

### Post by ravindra-luv on 2014-08-09
hi,

i was trying to connect my photon device using your commands but i was unsuccessful in doing so.

tying in this command "sudo usb_modeswitch -I -W -c 12d1\:1505" results me in following output and it doesn't connects.

Reading config file: 12d1:1505

 * usb_modeswitch: handle USB devices with multiple modes
 * Version 1.2.3 (C) Josua Dietze 2012
 * Based on libusb0 (0.1.12 and above)

 ! PLEASE REPORT NEW CONFIGURATIONS !

DefaultVendor=  0x12d1
DefaultProduct= 0x1505
TargetVendor=   not set
TargetProduct=  not set
TargetClass=    not set
TargetProductList=""

DetachStorageOnly=0
HuaweiMode=0
SierraMode=0
SonyMode=0
QisdaMode=0
GCTMode=0
KobilMode=0
SequansMode=0
MobileActionMode=0
CiscoMode=0
MessageEndpoint=  not set
MessageContent="55534243123456780000000000000011062000000100000000000000000000"
NeedResponse=0
ResponseEndpoint= not set

InquireDevice disabled
Success check disabled
System integration mode disabled


usb_set_debug: Setting debugging level to 15 (on)
usb_os_find_busses: Found 007
usb_os_find_busses: Found 006
usb_os_find_busses: Found 005
usb_os_find_busses: Found 004
usb_os_find_busses: Found 003
usb_os_find_busses: Found 002
usb_os_find_busses: Found 001
usb_os_find_devices: Found 001 on 007
usb_os_find_devices: Found 003 on 006
usb_os_find_devices: Found 001 on 006
error obtaining child information: Inappropriate ioctl for device
usb_os_find_devices: Found 001 on 005
usb_os_find_devices: Found 001 on 004
usb_os_find_devices: Found 001 on 003
usb_os_find_devices: Found 002 on 002
skipping descriptor 0xB
skipped 1 class/vendor specific endpoint descriptors
skipped 5 class/vendor specific interface descriptors
skipping descriptor 0x25
skipped 1 class/vendor specific endpoint descriptors
skipped 9 class/vendor specific interface descriptors
usb_os_find_devices: Found 001 on 002
error obtaining child information: Inappropriate ioctl for device
usb_os_find_devices: Found 001 on 001
Looking for default devices ...
  searching devices, found USB ID 1d6b:0001
  searching devices, found USB ID 12d1:140b
   found matching vendor ID
  searching devices, found USB ID 1d6b:0001
  searching devices, found USB ID 1d6b:0001
  searching devices, found USB ID 1d6b:0001
  searching devices, found USB ID 1d6b:0001
  searching devices, found USB ID 04f2:b016
  searching devices, found USB ID 1d6b:0002
  searching devices, found USB ID 1d6b:0002
 No devices in default mode found. Nothing to do. Bye.

Although  my network manager does detect the new CDMA device but still does not connects it.
Can you please help me..

---

