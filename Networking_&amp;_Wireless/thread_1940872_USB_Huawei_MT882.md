---
title: "USB Huawei MT882"
date: 2012-03-14
forum: Networking &amp; Wireless
---

### Post by lauta13 on 2012-03-14
Hello people, i just installed Ubuntu 11.10 in my computer, and  im having trouble getting it to connect to internet thru my Huawei Smartax MT882 connected via USB (Ethernet is already in use by my other computers, so its out of the question, and i have too much electric tension already where im plugging the computer cause i also plug eveything else of my room there, so its also out of the question to buy a switch).

I seached for the answer but its too messy for me to understand or they just dont work (for example i tried UbuDSL but when i try to run it the OS tells me that 11.10 its not compatible yet)

In Windows 7 it was just a matter of installing the drivers (XP drivers in compatibility mode) and that was it, no configuration at all needed (except for the first time conection, like 6 years ago)

So yeah, im really looking forward to use this OS, so i hope you guys can give me a hand, but i must mention its the first time i use linux so i dont really know the terminal commands and such apart from the DOS-like ones, so i beg you to be patience with me :p

I hope you can give me a hand and get this thing working.

---

### Post by codemaniac on 2012-03-14
Hello mate ,
welcome to Ubuntuforums .Please follow the below guide in order to connect your USB modem to the internet .Best of luck .
[https://help.ubuntu.com/11.10/ubuntu-help/net-mobile.html]("https://help.ubuntu.com/11.10/ubuntu-help/net-mobile.html")

---

### Post by lauta13 on 2012-03-14
> **codemaniac said:**
> Hello mate ,
welcome to Ubuntuforums .Please follow the below guide in order to connect your USB modem to the internet .Best of luck .
[https://help.ubuntu.com/11.10/ubuntu-help/net-mobile.html](https://help.ubuntu.com/11.10/ubuntu-help/net-mobile.html)
Hello, thanks for answering but i already tried that way and it didnt work, that wizard seems to be more of a wireless modem thing, my modem its an actual ADSL modem:
[IMG]http://www.stream-support.ru/modems/images/mt882.jpg[/IMG]

Unless im not writing the data for the boxes properly, or im placing wrong information in em, and some of them i dont know what they require... if thats the case, i would like to know exactly what im supposed to input and where to get that information in case i dont know.

---

### Post by lauta13 on 2012-03-14
Or it may be a VPN issue or something else, which i dont really know how to configure... 
i just dont know

---

### Post by alexfish on 2012-03-14
> **lauta13 said:**
> Or it may be a VPN issue or something else, which i dont really know how to configure... 
i just dont know

done some searches and came up with this

[https://help.ubuntu.com/community/UsbAdslModem](https://help.ubuntu.com/community/UsbAdslModem)

and

[http://www.honeytechblog.com/how-to-connect-broadband-in-ubuntu/](http://www.honeytechblog.com/how-to-connect-broadband-in-ubuntu/)

hope it helps

alexfish

---

### Post by winh8r on 2012-03-14
I have one of these lying around here somwhere, they do not require additional drivers for use with Ubuntu. Always worked right out of the box with all the different versions of Ubuntu right up to the new 12.04 Beta.

Best to use ethernet though as the USB is very unreliable. Also when you edit any settings in the modem itself make sure you click the save button then reload and save again to make sure they are saved properly.

You need to type 192.168.1.1 into the address bar of Firefox to get access to the admin page for the modem. Unless you have set it otherwise use "admin" for both username and password to get to the admin page (set it to something else for security reasons!!!and remember to write it down)

You can do all sorts of diagnostics from the admin page to let you see where your connection is failing.

Hope this is of some help to you.

---

### Post by lauta13 on 2012-03-15
> **winh8r said:**
> I have one of these lying around here somwhere, they do not require additional drivers for use with Ubuntu. Always worked right out of the box with all the different versions of Ubuntu right up to the new 12.04 Beta.

Best to use ethernet though as the USB is very unreliable. Also when you edit any settings in the modem itself make sure you click the save button then reload and save again to make sure they are saved properly.

You need to type 192.168.1.1 into the address bar of Firefox to get access to the admin page for the modem. Unless you have set it otherwise use "admin" for both username and password to get to the admin page (set it to something else for security reasons!!!and remember to write it down)

You can do all sorts of diagnostics from the admin page to let you see where your connection is failing.

Hope this is of some help to you.
Ok, lemme boot up with ubuntu and will try with that ip, but ive tried to use the ip i use in windows to access the modem's admin tools and (10.0.0.100) and nothing came up in the browser.

btw: ive been using the usb conection since 2006 and never had any type of problems at all.

---

### Post by lauta13 on 2012-03-15
Ok, nothing you guys gave me worked but i noticed that by unplugging and replugging the usb, and then doing "lsusb" in the console, linux actually detects the hardware.

what should i do from now?

---

### Post by winh8r on 2012-03-15
As far as I have been able to figure out, these modems are designed to be used EITHER for a USB connection OR an Ethernet connection as opposed to both at the same time. They are of a very basic design and the USB and Ethernet ports on the modem seem to be incapable of being used simultaneously. I may be wrong here but I strongly suspect that it is one or the other and not both at once.

Looks like you are going to need to get an ethernet hub if you want two computers running on the internet at the same time.

---

### Post by alexfish on 2012-03-15
> **lauta13 said:**
> Ok, nothing you guys gave me worked but i noticed that by unplugging and replugging the usb, and then doing "lsusb" in the console, linux actually detects the hardware.

what should i do from now?

can post the results of this command from the terminal
```
usb-devices
```Locate the lines which indicate the device and only those lines

alexfish

---

### Post by lauta13 on 2012-03-15
> **winh8r said:**
> As far as I have been able to figure out, these modems are designed to be used EITHER for a USB connection OR an Ethernet connection as opposed to both at the same time. They are of a very basic design and the USB and Ethernet ports on the modem seem to be incapable of being used simultaneously. I may be wrong here but I strongly suspect that it is one or the other and not both at once.

Looks like you are going to need to get an ethernet hub if you want two computers running on the internet at the same time.
As ive said before, ive been using both the USB (for the computer here, in my room) and the Ethernet (connected to a hub in the other side of my house, that connects two other computers) simultaneously without any problem at all with all 3 computers using internet at the same time.

My problem is with LINUX not working with the USB connection, but in Windows i can use it without any problems, like, right now...

---

### Post by lauta13 on 2012-03-15
> **alexfish said:**
> can post the results of this command from the terminal
```
usb-devices
```Locate the lines which indicate the device and only those lines

alexfish
Im sorry, i dont understand what you want me to do, do you want me to post the results of that command in the terminal here in the forums, right?

---

### Post by alexfish on 2012-03-15
> **lauta13 said:**
> Im sorry, i dont understand what you want me to do, do you want me to post the results of that command in the terminal here in the forums, right?
```
alexfish@alexfish-desktop:~$ can do one of two things
No command 'can' found, but there are 17 similar ones
can: command not found
alexfish@alexfish-desktop:~$ 
```use copy and paste , use mouse right click, in the terminal,a menu will appear

or can redirect the output to a file
alexfish@alexfish-desktop:~$ can do one of two things
```
No command 'can' found, but there are 17 similar ones
can: command not found
alexfish@alexfish-desktop:~$ usb-devices > ./my_usb_devices
alexfish@alexfish-desktop:~$ 
```

the results will be in the /home directory/ my_usb_devices

---

### Post by lauta13 on 2012-03-15
> **alexfish said:**
> ```
alexfish@alexfish-desktop:~$ can do one of two things
No command 'can' found, but there are 17 similar ones
can: command not found
alexfish@alexfish-desktop:~$ 
```use copy and paste , use mouse right click, in the terminal,a menu will appear

or can redirect the output to a file
alexfish@alexfish-desktop:~$ can do one of two things
```
No command 'can' found, but there are 17 similar ones
can: command not found
alexfish@alexfish-desktop:~$ usb-devices > ./my_usb_devices
alexfish@alexfish-desktop:~$ 
```the results will be in the /home directory/ my_usb_devices


T:  Bus=01 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 6
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev=03.00
S:  Manufacturer=Linux 3.0.0-16-generic ehci_hcd
S:  Product=EHCI Host Controller
S:  SerialNumber=0000:00:1d.7
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=02 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev=03.00
S:  Manufacturer=Linux 3.0.0-16-generic uhci_hcd
S:  Product=UHCI Host Controller
S:  SerialNumber=0000:00:1d.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=03 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev=03.00
S:  Manufacturer=Linux 3.0.0-16-generic uhci_hcd
S:  Product=UHCI Host Controller
S:  SerialNumber=0000:00:1d.1
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=03 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=12  MxCh= 0
D:  Ver= 1.10 Cls=02(commc) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1110 ProdID=5c01 Rev=00.14
S:  Manufacturer=MT882
S:  SerialNumber=123456789abcdx
C:  #Ifs= 1 Cfg#= 1 Atr=c0 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=0a(data ) Sub=00 Prot=00 Driver=(none)

T:  Bus=03 Lev=01 Prnt=01 Port=01 Cnt=02 Dev#=  3 Spd=1.5 MxCh= 0
D:  Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=093a ProdID=2510 Rev=01.00
S:  Manufacturer=PIXART
S:  Product=USB OPTICAL MOUSE
C:  #Ifs= 1 Cfg#= 1 Atr=a0 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=01 Prot=02 Driver=usbhid

T:  Bus=04 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev=03.00
S:  Manufacturer=Linux 3.0.0-16-generic uhci_hcd
S:  Product=UHCI Host Controller
S:  SerialNumber=0000:00:1d.2
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

---

### Post by alexfish on 2012-03-16
Hi
the device has no driver
```
T: Bus=03 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#= 2 Spd=12 MxCh= 0
D: Ver= 1.10 Cls=02(commc) Sub=00 Prot=00 MxPS=64 #Cfgs= 1
P: Vendor=1110 ProdID=5c01 Rev=00.14
S: Manufacturer=MT882
S: SerialNumber=123456789abcdx
C: #Ifs= 1 Cfg#= 1 Atr=c0 MxPwr=100mA
I: If#= 0 Alt= 0 #EPs= 3 Cls=0a(data ) Sub=00 Prot=00 Driver=(none) <<<HERE
```
 Did a search and found possible driver : did "modinfo ueagle_atm"

showing 
```
filename:       /lib/modules/2.6.38-13-generic/kernel/drivers/usb/atm/ueagle-atm.ko
license:        Dual BSD/GPL
description:    ADI 930/Eagle USB ADSL Modem driver
author:         Damien Bergamini/Matthieu Castet/Stanislaw W. Gruszka

alias:          usb:v1110p9041d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1110p9042d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1110p9031d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1110p9032d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1110p9023d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1110p9024d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1110p9021d*dc*dsc*dp*ic*isc*ip*
```has Vendor Id alias: usb:v1110 : but no match to the product

searching the net indicators are that cdc_ether is associated with this device . but the modalias is questionable:: 

can possibly try adding to new_id to the nearest match by the description "ADI 930/Eagle USB ADSL Modem driver"

```
sudo modprobe ueagle_atm
```

```
sudo su
 echo "1110 5c01" > /sys/bus/usb/drivers/ueagle-atm/new_id
```then try listing the device with usb-devices to see if the driver has bound
also see if this command will list the device
```
ls -al /dev/serial/by-id
```

if bound to the driver . possible try configuring the device with Network Manager

---

### Post by lauta13 on 2012-03-16
Thanks a lot for your help but im kinda lost, could you please sum up all the commands i have to do? 
is this safe? cause i have no idea how to take back the changes i do and i already messed up two installations of this OS because of the damn AMD drivers...

---

### Post by alexfish on 2012-03-16
> **lauta13 said:**
> Thanks a lot for your help but im kinda lost, could you please sum up all the commands i have to do? 
is this safe? cause i have no idea how to take back the changes i do and i already messed up two installations of this OS because of the damn AMD drivers...

yes they are safe , at worst the driver will not bind to the device, no harm done

if they bind to the device , at worst the device may accept commands and get connected but info sent back may not be readable to the linux system.  then upon reboot your system will be the same

the only damage you can do to the system , is when trying to install or compile 3rd party drivers into the Kernel.

if using windows copy the above to a file , then when in Ubuntu can use the copy and paste, what is in the code blocks or type them in line by line , when prompted for password enter your password

alexfish

---

### Post by lauta13 on 2012-03-17
> **alexfish said:**
> yes they are safe , at worst the driver will not bind to the device, no harm done

if they bind to the device , at worst the device may accept commands and get connected but info sent back may not be readable to the linux system.  then upon reboot your system will be the same

the only damage you can do to the system , is when trying to install or compile 3rd party drivers into the Kernel.

if using windows copy the above to a file , then when in Ubuntu can use the copy and paste, what is in the code blocks or type them in line by line , when prompted for password enter your password

alexfish
Ok bro, ill try it tonight and let you know, thanks a lot!

---

### Post by lauta13 on 2012-03-18
did what you told me and now it shows me:

T:  Bus=03 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=12  MxCh= 0
D:  Ver= 1.10 Cls=02(commc) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1110 ProdID=5c01 Rev=00.14
S:  Manufacturer=MT882
S:  SerialNumber=123456789abcdx
C:  #Ifs= 1 Cfg#= 1 Atr=c0 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=0a(data ) Sub=00 Prot=00 Driver=[B]ueagle-atm
[/B]
it worked, right?

what should i do now?

---

### Post by alexfish on 2012-03-18
> **lauta13 said:**
> did what you told me and now it shows me:

T:  Bus=03 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=12  MxCh= 0
D:  Ver= 1.10 Cls=02(commc) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1110 ProdID=5c01 Rev=00.14
S:  Manufacturer=MT882
S:  SerialNumber=123456789abcdx
C:  #Ifs= 1 Cfg#= 1 Atr=c0 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=0a(data ) Sub=00 Prot=00 Driver=[B]ueagle-atm
[/B]
it worked, right?

what should i do now?[FONT=monospace]
[/FONT]

Have a look at previous posts with the links  on how to configure the device

IE: get the info ready then Set up with Network Manager.

remember each boot you will have to use the codes again to load the driver, ensure the driver has loaded

IE: line looks like
```
I:  If#= 0 Alt= 0 #EPs= 3 Cls=0a(data ) Sub=00 Prot=00 Driver=ueagle-atm
```I assume the device may show in Network Manager as a Wired Connection

see if it will list
```
nm-tool
```

---

