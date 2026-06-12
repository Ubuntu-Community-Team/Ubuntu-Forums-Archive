---
title: "Mobile broadband problem"
date: 2010-03-10
forum: Networking &amp; Wireless
---

### Post by mooz123 on 2010-03-10
Hi,

My mobile broadband connection is installed, but it will not start up properly in Ubuntu: I cannot get a connection via NetworkManager. When I start the connection in Windows, and reboot to Ubuntu, everything worked fine, although I lost the connection later. I would be grateful receiving your ideas how to solve this!

//Mark

Ubuntu 9.10 Huawei E1750 modem

---

### Post by mooz123 on 2010-03-11
Suggestions anybody? I've used Ubuntu for a couple of years, and this is the first time it is a complete disaster

---

### Post by chrisp1000 on 2010-03-11
[COLOR=Blue]**[SOLVED for Me by Alexfish and Pauligrinder thanks guys] But I didnt create thread so can't change heading**[/COLOR]

I am having the same problem. 

DELL Latitude E6500
3 broadband modem (Huwai E1750)
Windows 7 Pro
LinuxMint 8 Helena (Ubuntu Karmic + extras)

lsusb shows that the modem is connected. I have installed usb-modeswitch, when I run modeswitch it says there is no driver loaded.

But if I load Windows then reboot to Linux without disconnecting from the internet or removing the dongle everything seems to just work.

Any help is much appreciated.

---

### Post by chrisp1000 on 2010-03-11
ok some further info:

I installed usb-modeswitch from karmic web repo (as no internet in Linux atm!)

I used the instructions from the forums so typed:
echo 'SUBSYSTEM=="usb", SYSFS(idProduct)=="1446", SYSFS(idVendor)=="12d1", RUN+="/lib/udev/modem-modeswitch --vendor 0x12d1 --product 0x1446 --type option-zerocd"' | sudo tee /etc/udev/rules.d/45-huawei1750.rules

so my udev rules file for the modem reads:
SUBSYSTEM=="usb", SYSFS(idProduct)=="1446", SYSFS(idVendor)=="12d1", RUN+="/lib/udev/modem-modeswitch --vendor 0x12d1 --product 0x1446 --type option-zerocd"

I then plugged the modem in and entered the following commands with results shown:

~ $ dmesg | grep ttyU
[    8.784195] usb 2-4: GSM modem (1-port) converter now attached to ttyUSB0
[    8.784234] usb 2-4: GSM modem (1-port) converter now attached to ttyUSB1
[    8.784265] usb 2-4: GSM modem (1-port) converter now attached to ttyUSB2
[  382.269860] option1 ttyUSB0: GSM modem (1-port) converter now disconnected from ttyUSB0
[  382.270174] option1 ttyUSB1: GSM modem (1-port) converter now disconnected from ttyUSB1
[  382.270485] option1 ttyUSB2: GSM modem (1-port) converter now disconnected from ttyUSB2
~ $ ls /dev/ttyU*
ls: cannot access /dev/ttyU*: No such file or directory
~ $ sudo modprobe usbserial vendor=0x12d1 product=0x1446
~ $

So please any help here guys.

---

### Post by Pauligrinder on 2010-03-11
This seems to be a common bug in Karmic (which is one of the reasons I'm still using Jaunty). You could try using wvdial, but I can't help with your settings in /etc/wvdial.conf. Also, it may be a bit difficult to install without internet, you will have to check what other packages it requires and download them all from windows. (I used it when I tested WICD, which doesn't have 3G support yet)
If you get it, here's my configuration for reference:
```

[Dialer Defaults]
Modem = /dev/ttyUSB0
Init =
AT+CGDCONT = 1,"IP","internet","0.0.0.0",0.0
Phone=*99#
Username = "rlnet"
Password = "internet"
Stupid Mode = 1

```
I think all other settings can be left as is, but you have to replace Phone, Username and Password with those provided by your operator.

Actually, looking at your last post, I don't think this'll work :( Might still be worth a try.

---

### Post by jd87 on 2010-03-11
> **Pauligrinder said:**
> This seems to be a common bug in Karmic (which is one of the reasons I'm still using Jaunty). 

I'm having similar issues with a Huawei stick. I have read that they tend to have problems with Karmic but that Jaunty works fine. If you've read my thread you'll see I've tried all kinds of things. If I install Jaunty instead is that likely to fix the problem?

---

### Post by chrisp1000 on 2010-03-11
Hi Pauli, many thanks for the reply. I will def try that but I think the problem is in the USB connection of the device as the dmesg says the GSM device has been disconnected.

I have tried stick on my PC as that still has LinuxMint 7 which I think was Jaunty. But I can't even get that to do anything lol, will trawl the forums some more :(

---

### Post by chrisp1000 on 2010-03-11
Well no luck with the previous version. Anyone got any ideas how I can sort the latest build to work?

---

### Post by fx2248 on 2010-03-11
I have battled with Ubuntu 9.04 and 9.10 to connect to a Next G wireless internet and trawled thru many forums, and have come to the conclusion that Ubuntu may look good compared to windows but it falls well short of ease of use.

With windows vista  (yuk) all one does is plug in the modem and everything gets done. Learning Ubuntu is like learning another language, so unfortunately for me ubuntu get chucked into the bin and out comes windows.

Pity Ubuntu is so unfriendly to newbies.

---

### Post by Pauligrinder on 2010-03-12
sounds like that 3G modem isn't supported by networkmanager yet. My Huawei-E169 works flawlessly on Jaunty. When I plug it in, I get a connection wizard in which I choose my operator, then it works. (same with interpid, in hardy I used wvdial and in karmic nothing seemed to work)

> I have tried stick on my PC as that still has LinuxMint 7 which I think was Jaunty. But I can't even get that to do anything lol, will trawl the forums some more :(

Are you completely sure your stick isn't broken?

---

### Post by chrisp1000 on 2010-03-12
My dongle is working fine Pauli I get a brilliant connection in Win7 and also in Linux if I connect in windows then reboot.

I seem to have made some progress. I noticed that the command in /etc/udev/rules.d/45-huawei1750.rules was 

modem-modeswitch 

yet that is not available at the command line. At the command line the instruction is 

usb_modeswitch

So I am playing with that at the moment, I did get:
 ~ $ dmesg | grep ttyU
[  248.462620] usb 2-4: generic converter now attached to ttyUSB0

but I now just get:
~ $ dmesg | grep ttyU
[  248.462620] usb 2-4: generic converter now attached to ttyUSB0
[  594.826895] generic ttyUSB0: generic converter now disconnected from ttyUSB0

Any thoughts ?

---

### Post by chrisp1000 on 2010-03-12
ok modem-modeswitch is the right choice. so right back where I started. Come on guys someone must have an idea!  Where is yoda when you need him?

I have tried wvdial and this is what I get:
~ $ wvdial
--> WvDial: Internet dialer version 1.60
--> Cannot open /dev/ttyUSB0: No such file or directory
--> Cannot open /dev/ttyUSB0: No such file or directory
--> Cannot open /dev/ttyUSB0: No such file or directory

If there are extra commands I should run to give more info just say and it shall be done ;)

---

### Post by chrisp1000 on 2010-03-14
No yoda's out there?

---

### Post by alexfish on 2010-03-14
> **chrisp1000 said:**
> ok some further info:

I installed usb-modeswitch from karmic web repo (as no internet in Linux atm!)

I used the instructions from the forums so typed:
echo 'SUBSYSTEM=="usb", SYSFS(idProduct)=="1446", SYSFS(idVendor)=="12d1", RUN+="/lib/udev/modem-modeswitch --vendor 0x12d1 --product 0x1446 --type option-zerocd"' | sudo tee /etc/udev/rules.d/45-huawei1750.rules

so my udev rules file for the modem reads:
SUBSYSTEM=="usb", SYSFS(idProduct)=="1446", SYSFS(idVendor)=="12d1", RUN+="/lib/udev/modem-modeswitch --vendor 0x12d1 --product 0x1446 --type option-zerocd"

I then plugged the modem in and entered the following commands with results shown:

~ $ dmesg | grep ttyU
[    8.784195] usb 2-4: GSM modem (1-port) converter now attached to ttyUSB0
[    8.784234] usb 2-4: GSM modem (1-port) converter now attached to ttyUSB1
[    8.784265] usb 2-4: GSM modem (1-port) converter now attached to ttyUSB2
[  382.269860] option1 ttyUSB0: GSM modem (1-port) converter now disconnected from ttyUSB0
[  382.270174] option1 ttyUSB1: GSM modem (1-port) converter now disconnected from ttyUSB1
[  382.270485] option1 ttyUSB2: GSM modem (1-port) converter now disconnected from ttyUSB2
~ $ ls /dev/ttyU*
ls: cannot access /dev/ttyU*: No such file or directory
~ $ sudo modprobe usbserial vendor=0x12d1 product=0x1446
~ $

So please any help here guys.

Hi

according to info these are the rules

sudo gedit /etc/udev/rules.d/61-huawei_e1750.rule

SUBSYSTEM=="usb", SYSFS{idVendor}=="12d1", SYSFS{idProduct}=="1446",  RUN+="/usr/sbin/usb_modeswitch --default-vendor 0x12d1 --default-product  0x1446 --target-vendor 0x12d1 --target-product 0x1001 --message-content  55534243000000000000000000000011060000000000000000 000000000000"



If, for some reason, the device doesn't get recognized automatically,  when you plug it in, you can use this from the command line

sudo  /usr/sbin/usb_modeswitch --default-vendor 0x12d1 --default-product  0x1446 --target-vendor 0x12d1 --target-product 0x1001 --message-content  55534243000000000000000000000011060000000000000000 000000000000

make sure the message-content doesn't contain a SPACE, UbuntuForums puts  one in it when displays this article for some unknown reason

---

### Post by chrisp1000 on 2010-03-15
Removed

---

### Post by chrisp1000 on 2010-03-15
Hi Alex, many thanks for that, once I used my brain and did a reboot my modem now works beautifully. Top stuff thanks you.

---

