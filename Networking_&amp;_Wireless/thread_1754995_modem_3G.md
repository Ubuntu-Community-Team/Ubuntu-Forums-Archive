---
title: "modem 3G"
date: 2011-05-10
forum: Networking &amp; Wireless
---

### Post by vahdani_d on 2011-05-10
**I use the Ubuntu 10**
 I bought a modem with a SIM card connected to the Internet to become mobile
 The modem I installed Linux s file but when I install the file tells the kernel does not match and I'm the Download Now how do I download what I download and I eat Bdrdm please guide
 Bought the hardware model revolves
 **D-link hspad atacard proprictary**

---

### Post by alexfish on 2011-05-10
Need some info
can open up a terminal and post results of the following commands
```
uname -a
```
```
lsusb
```
```
ls -al /dev/serial/by-id
```

---

### Post by vahdani_d on 2011-05-11
sky@ubuntu:~$ uname -a
Linux ubuntu 2.6.35-22-generic #33-Ubuntu SMP Sun Sep 19 20:34:50 UTC 2010 i686 GNU/Linux

sky@ubuntu:~$ lsusb
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 07d1:7e11 D-Link System 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

sky@ubuntu:~$ ls -al /dev/serial/by-id
ls: cannot access /dev/serial/by-id: No such file or directory

---

### Post by alexfish on 2011-05-11
hi

not sure about this device, or even if it will work
initially looking at the vendor ID  this device seems fall into two classes , wilan and ethernet ,
so therefore indicating ,not a 3g device

are you connecting the device through a d-link router or connecting the device directly to the computer
can post the results of usb-devices from the terminal
```
usb-devices
```will then look at the details, but not sure where heading on this one

alexfish

---

### Post by vahdani_d on 2011-05-11
sky@ubuntu:~$ usb-devices



T:  Bus=01 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 6

D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1

P:  Vendor=1d6b ProdID=0002 Rev=02.06

S:  Manufacturer=Linux 2.6.35-22-generic ehci_hcd

S:  Product=EHCI Host Controller

S:  SerialNumber=0000:00:1d.7

C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA

I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub



T:  Bus=01 Lev=01 Prnt=01 Port=02 Cnt=01 Dev#=  2 Spd=480 MxCh= 0

D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1

P:  Vendor=07d1 ProdID=7e11 Rev=00.00

S:  Manufacturer=D-Link,Incorporated

S:  Product=D-Link WCDMA Technologies MSM

S:  SerialNumber=MF112DDLKD010000

C:  #Ifs= 4 Cfg#= 1 Atr=e0 MxPwr=500mA

I:  If#= 0 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)

I:  If#= 1 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)

I:  If#= 2 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage

I:  If#= 3 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)



T:  Bus=02 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2

D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1

P:  Vendor=1d6b ProdID=0001 Rev=02.06

S:  Manufacturer=Linux 2.6.35-22-generic uhci_hcd

S:  Product=UHCI Host Controller

S:  SerialNumber=0000:00:1d.0

C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA

I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub



T:  Bus=03 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2

D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1

P:  Vendor=1d6b ProdID=0001 Rev=02.06

S:  Manufacturer=Linux 2.6.35-22-generic uhci_hcd

S:  Product=UHCI Host Controller

S:  SerialNumber=0000:00:1d.1

C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA

I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub



T:  Bus=04 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2

D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1

P:  Vendor=1d6b ProdID=0001 Rev=02.06

S:  Manufacturer=Linux 2.6.35-22-generic uhci_hcd

S:  Product=UHCI Host Controller

S:  SerialNumber=0000:00:1d.2

C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA

I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

---

### Post by alexfish on 2011-05-11
Ok

can try see if option driver will work with this device

```
sudo modeprobe -r option
```
```
sudo modeprobe option
```then send the device id's to the new_id
```
echo "0x07d1 0x7e11" > /sys/bus/usb-serial/drivers/option1/new_id 
```or
```
echo "0x07d1 0x7e11" > /sys/module/option/drivers/usb-serial:option1/new_id
```then see if registered
```
ls -al /dev/serial/by-id
```
if nothing happens will have to look further

---

### Post by yktan on 2012-07-24
Hi alexfish, I am having the same modem as vahdani_d and typing your commands (modprobe instead of modeprobe) manage to get my modem registered and I am able to dial with wvdial.

May I know what does that mean? Why doesn't it register automatically? How do I automate this part?

Thanks for your help!

---

### Post by alexfish on 2012-07-25
Hi

this is old thread needs to be closed

@ yktan , search through , threads by and posts by alexfish ,  recent 

regards

alexfish

---

### Post by lisati on 2012-07-25
A lot can change in the space of a year. If you are having a similar problem, please start a new thread.

From the forum [code of conduct]("http://ubuntuforums.org/index.php?page=policy"):
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

Thread closed.

---

### Post by Elfy on 2012-07-25
closed

---

