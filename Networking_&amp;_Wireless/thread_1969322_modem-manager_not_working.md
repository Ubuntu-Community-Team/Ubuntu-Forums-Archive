---
title: "modem-manager not working"
date: 2012-04-29
forum: Networking &amp; Wireless
---

### Post by malakar.subhendu on 2012-04-29
Just installed my 12.04 and had restored backup from the 12.04 beta-2 version i was using previously. now my modem is not been detected by ubuntu. Previously it was never a problem(till 11.10). tried to use a third party software "sakis3G". it also didn't worked out(segmentation fault and core dumped). in the beta-2 also, it had problems sometimes but "sakis3G" would have connected to the internet easily. Now it's not working. Please Help!!!

---

### Post by alexfish on 2012-04-29
from a fresh cold boot , allow time for the system to settle , then plug the device

from the terminal

```
usb-devices
```
```
ls -al /dev/serial/by-id
```

---

### Post by malakar.subhendu on 2012-04-29
still not working.
what are the commands for?
the first one produced a lot of information.
second one there was no such folder.
should i post the output of first one.

---

### Post by alexfish on 2012-04-30
how to find the device :

first use lsusb command

```
lsusb
``` it shows a result like
```
Bus 002 Device 002: ID 0603:00f2 Novatek Microelectronics Corp. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 006: ID 12d1:14ac Huawei Technologies Co., Ltd. 
Bus 001 Device 003: ID 059b:047a Iomega Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```
from this info I know the device is
```
[COLOR=Blue]12d1:14ac Huawei Technologies Co., Ltd.[/COLOR]
```the usb-devices command , look for block information with the device id's , highlighted

```
T:  Bus=01 Lev=01 Prnt=01 Port=02 Cnt=02 Dev#=  6 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
[COLOR=Blue]P:  Vendor=12d1 ProdID=14ac Rev=00.00[/COLOR]
[COLOR=Blue]S:  Manufacturer=Huawei Technologies[/COLOR]
S:  Product=HUAWEI Mobile
C:  #Ifs= 6 Cfg#= 1 Atr=c0 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I:  If#= 1 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I:  If#= 2 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I:  If#= 3 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I:  If#= 4 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage
I:  If#= 5 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage
``` then post the info , like so

Remember the above is an example , and will explain what the commands do later

---

### Post by malakar.subhendu on 2012-04-30
this is the segment of the modem. 
> T:  Bus=01 Lev=02 Prnt=02 Port=00 Cnt=01 Dev#=  5 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1c9e ProdID=9605 Rev=00.00
S:  Manufacturer=USB Modem
S:  Product=USB Modem
S:  SerialNumber=1234567890ABCDEF
C:  #Ifs= 5 Cfg#= 1 Atr=e0 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)
I:  If#= 1 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)
I:  If#= 2 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)
I:  If#= 3 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)
I:  If#= 4 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage

---

### Post by alexfish on 2012-04-30
That be the device , buts has no drivers attached , can try load the driver and ensure the device gets entered in the new id , if not recognise by the driver 
these commands may load the driver

open up the terminal and enter root
```
sudo su
``````
modprobe option
```try the usb-devices command

if the driver has not loaded after that command ( let me know if it has or has not) try this ,

this command may load the device into the new id
```
echo 1C9E 9605 > /sys/bus/usb-serial/drivers/option1/new_id
```then check the results with the usb-devices command

if this works will post details on how to ensure the drivers loads each time the device is plugged in

---

### Post by malakar.subhendu on 2012-04-30
applied both the methods.
first time it showed the modem and i was able to connect to the internet. then restarted the machine. it does not show the modem now again.

---

### Post by alexfish on 2012-04-30
redo the commands as listed , does it show ,

Also post results of the Device from the terminal

It Don't show , means nothing From where I sit...

alexfish

---

### Post by malakar.subhendu on 2012-04-30
reinstalled precise
but no help.

doing this 
```
echo 1C9E 9605 > /sys/bus/usb-serial/drivers/option1/new_id
```


the modem got detected
now connected to internet.

result of usb-devices:

```
T:  Bus=01 Lev=02 Prnt=02 Port=00 Cnt=01 Dev#=  5 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1c9e ProdID=9605 Rev=00.00
S:  Manufacturer=USB Modem
S:  Product=USB Modem
S:  SerialNumber=1234567890ABCDEF
C:  #Ifs= 5 Cfg#= 1 Atr=e0 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I:  If#= 1 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I:  If#= 2 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I:  If#= 3 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I:  If#= 4 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage

```

---

### Post by ProNux on 2012-05-02
> **alexfish said:**
> That be the device , buts has no drivers attached , can try load the driver and ensure the device gets entered in the new id , if not recognise by the driver 
these commands may load the driver

open up the terminal and enter root
```
sudo su
``````
modprobe option
```try the usb-devices command

if the driver has not loaded after that command ( let me know if it has or has not) try this ,

this command may load the device into the new id
```
echo 1C9E 9605 > /sys/bus/usb-serial/drivers/option1/new_id
```then check the results with the usb-devices command

if this works will post details on how to ensure the drivers loads each time the device is plugged in
With your permission, I ought to join this thread.

I have a similar case, though I have a different modem.  The drivers were loaded and I can connect to the internet, but it does not retain; I have to enter the same commands whenever I plug the modem.  Can you please post how to load the drivers every time the modem is connected.

Thanks in advance.

---

### Post by alexfish on 2012-05-02
> **ProNux said:**
> With your permission, I ought to join this thread.

I have a similar case, though I have a different modem.  The drivers were loaded and I can connect to the internet, but it does not retain; I have to enter the same commands whenever I plug the modem.  Can you please post how to load the drivers every time the modem is connected.

Thanks in advance.

Here is a sample
 Remember to change the ID's according to the device Highlighted in blue , as listed by the (lsusb) command
```

sudo su
``````
gedit /usr/bin/option_[COLOR=Blue]1C9E[/COLOR]:[COLOR=Blue]9605[/COLOR]
```add code : Remember to change the ID's according to the device Highlighted in blue , as listed by the (lsusb) command
```

#! /bin/bash
echo [COLOR=Blue]1C9E 9605[/COLOR] > /sys/bus/usb-serial/drivers/option1/new_id
```save the file and exit gedit
```
chmod +x /usr/bin/[COLOR=Blue]option_1C9E:9605[/COLOR]
``````
gedit /etc/udev/rules.d/option.rules
```add the code: Remember to edit the device Id's according to your device , note the lowercase letters !!!! IE , [COLOR=Blue]c[/COLOR] , not C :
 ```
ATTRS{idVendor}=="[COLOR=Blue]1c9e[/COLOR]", ATTRS{idProduct}=="[COLOR=Blue]9605[/COLOR]", RUN+="/sbin/modprobe option"
ATTRS{idVendor}=="[COLOR=Blue]1c9e[/COLOR]", ATTRS{idProduct}=="[COLOR=Blue]9605[/COLOR]", RUN+="/usr/bin/[COLOR=Blue]option_1C9E:9605[/COLOR]"
```save and exit

if not loading try re-plugging the device

---

### Post by malakar.subhendu on 2012-05-03
thanks for the help. Alexfish.
marking this as solved. 
thanks again.

---

### Post by ProNux on 2012-05-04
Thanks Alexfish, it worked on my modem too!8)

---

### Post by kridybel on 2012-05-04
I have a vodafone K3806 stick, which works on my sons windows 7 pc. 

I'm still getting the segmentation error. I have downloaded the i386 version of sagis 3G for my eeepc 1011 running xubuntu 12.04.

the usb-devices commend gives following output:
```
T:  Bus=01 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  5 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=12d1 ProdID=14ae Rev=01.02
S:  Manufacturer=Vodafone Group (Huawei)
S:  Product=Vodafone Mobile Broadband (Huawei)
S:  SerialNumber=0
C:  #Ifs= 4 Cfg#= 1 Atr=80 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I:  If#= 1 Alt= 0 #EPs= 1 Cls=02(commc) Sub=06 Prot=ff Driver=(none)
I:  If#= 2 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I:  If#= 3 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage

```

so it looks like I have a driver right?

the other command gives
```
kris@kris-1011PX:~$ ls -al /dev/serial/by-id
totaal 0
drwxr-xr-x 2 root root 80 mei  4 21:20 .
drwxr-xr-x 4 root root 80 mei  4 21:20 ..
lrwxrwxrwx 1 root root 13 mei  4 21:20 usb-Vodafone_Group__Huawei__Vodafone_Mobile_Broadband__Huawei__0-if00-port0 -> ../../ttyUSB0
lrwxrwxrwx 1 root root 13 mei  4 21:20 usb-Vodafone_Group__Huawei__Vodafone_Mobile_Broadband__Huawei__0-if02-port0 -> ../../ttyUSB1

```

lsusb gives
```
Bus 001 Device 005: ID 12d1:14ae Huawei Technologies Co., Ltd. 
```

after making the option file and option.rules with 12D1 and 14AE

the usb-devices command gives
```

T:  Bus=01 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  7 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=12d1 ProdID=14ae Rev=01.02
S:  Manufacturer=Vodafone Group (Huawei)
S:  Product=Vodafone Mobile Broadband (Huawei)
S:  SerialNumber=0
C:  #Ifs= 4 Cfg#= 1 Atr=80 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I:  If#= 1 Alt= 0 #EPs= 1 Cls=02(commc) Sub=06 Prot=ff Driver=option
I:  If#= 2 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I:  If#= 3 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage


```

but the ./sakis3g --interactive command still results in a segmentation fault after connect with 3G is selected

Sorry for riding along, but any help would be very much appreciated.

---

### Post by alexfish on 2012-05-04
@kridybel

not sure if i386 would make any different , may only apply to modeswitch , but not sure

but can check the system  build with this command
```
echo SYSTEM_BIT=$($(which getconf) LONG_BIT)
``` should see 32 or 64 , this will then suggest which sakis3g to download

coincidently , can you connect with Network Manager.

as regards sakis3g the script nearly always works its Bash , so only aspect to look at here is Chat
don't know if chat checks certain parts of the modem , or waits for certain signals , 

have posted methods of using terminal as serial port , look at resent posts regarding these devices

alexfish

---

### Post by malakar.subhendu on 2012-05-04
kridybel
It seems that your modem is been detected. I think u should try to connect to the internet via the network-manager. Sakis3G still gives me segmentation fault and core dumped error messages. But the gnome network manager works fine for me. Hope that yours will be good too.

---

### Post by kridybel on 2012-05-05
echo SYSTEM_BIT=$($(which getconf) LONG_BIT)
gave 32 so the I386 should have been the right one

The strange thing is that in my network manager the usb modem has always been detected as mobile broadband modem.

The wizard opens, the modem is suggested, i make the selections for country and apn. When I try to make a connection the waiting wheel spins for a couple of minutes. 

If I click on the network manager while spinning there is a small icon next to my connection name, which seems to indicate that there is a signal, but I do not get connected.

---

### Post by malakar.subhendu on 2012-05-05
May be your operator's network has some problem. 
Try for a few times again. Is that working on your sons's lappy?
What's the signal quality. 
Mine's also doesn't work sometimes. Replugs it and it works again.

---

### Post by alexfish on 2012-05-05
> **kridybel said:**
> echo SYSTEM_BIT=$($(which getconf) LONG_BIT)
gave 32 so the I386 should have been the right one

The strange thing is that in my network manager the usb modem has always been detected as mobile broadband modem.

The wizard opens, the modem is suggested, i make the selections for country and apn. When I try to make a connection the waiting wheel spins for a couple of minutes. 

If I click on the network manager while spinning there is a small icon next to my connection name, which seems to indicate that there is a signal, but I do not get connected.
Have looked further into this Message :RE: segmentation fault ,

may be emanating from the pppd , and not chat

from old bugs reports , needed to find if certain file exists on the system
the code to find if file exist is
```
file="/var/run/pppd.tdb"
if [ -f "$file" ]
then
    echo "$file found."
else
    echo "$file not found."
fi

```

---

### Post by rienesl on 2012-05-05
Hi,
got exactly the same Problem with the XS Stick P14 (1c9e:9605). After hours of searching for a solution, I did the following:
1) First tell networtk-manager, he should remember the PIN for the SIM-Card. This will be important for step 3!
2) Adding the following line in /etc/rc.local:
```
modprobe usbserial vendor=0x1c9e product=0x9605
```
This switches the stick from datastore-mode into the modem-mode.
3) Added a script with the following in auto-start:
```

#!/bin/sh
sleep 75
nmcli nm wwan on

```
This gets around the bug of the network-manager, which disables the mobile broadband after every restart. Don't be suprised about the 75 seconds wait. The USB-Stick takes up to 55 Seconds to initialisize after typing in the pin for the sim. Additionally the networkmanager is launched after the script started and it will need a few seconds to start itself. So adding at this point 20 seconds is safe, you might try up to 10 seconds, but that might fail. Will definitive fail, if you skipped point 1!
4) (Optional) Configure the mobile connection to connect automatically

Works so far, but fails, when unplugging the stick. I thought, I'll have to live with this, but then I was searching for something different and found this. I tried your advise which is described in post 11 and now replugging works. OK, it woks not 100% I still have to re-enable mobile broadband, by typing in ```
nmcli nm wwan on
``` but hey, I don't have to restart the whole machine anymore ;)

---

### Post by alexfish on 2012-05-05
@rienesl

have you tried adding
"nmcli nm wwan on" to your script Re; the script which udev invokes when device is plugged

udev Rules are easier to remember , users have a tendency to forget about what's in rc.local

---

### Post by kridybel on 2012-05-06
> **alexfish said:**
> Have looked further into this Message :RE: segmentation fault ,

may be emanating from the pppd , and not chat

from old bugs reports , needed to find if certain file exists on the system
the code to find if file exist is
```
file="/var/run/pppd.tdb"
if [ -f "$file" ]
then
    echo "$file found."
else
    echo "$file not found."
fi

```
There is no pppd.tbd file in my var/run  directory

---

### Post by alexfish on 2012-05-06
@kridybel

Just noticed something;Vodafone K3806
last time see this device it was under : ZTE banner
#[**87**]("http://ubuntuforums.org/showpost.php?p=10490373&postcount=87")

So not sure what looking at , Do Know some of these devices need different treatment as regards , Identifying the correct ports and the protocol associated::

suggest, Start A new thread ,  hopefully myself or some one with Knowlege of the devices will spot it.

only thing I can do is run through some of what the device is about and some testing to see if can get a CONNECT message ,

---

### Post by surja on 2012-05-08
Just wanted to confirm that alexfish's solution works perfectly for a Capitel EVDO 3G USB modem (device id - 1c9e:9e00) (Service provider - BSNL India).

---

### Post by malakar.subhendu on 2012-05-09
@surja: what was the result?

---

### Post by surja on 2012-05-12
> **malakar.subhendu said:**
> @surja: what was the result?

Well i can connect to the net if the 3G modem is detected after typing the suggested commands. But it does not work all the time. I hope there is a permanent solution to this soon.

---

### Post by alexfish on 2012-05-15
> **kridybel said:**
> I have a vodafone K3806 stick, which works on my sons windows 7 pc. 

I'm still getting the segmentation error. I have downloaded the i386 version of sagis 3G for my eeepc 1011 running xubuntu 12.04.
EDIT>>>>

```

T:  Bus=01 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  7 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=12d1 ProdID=14ae Rev=01.02
S:  Manufacturer=Vodafone Group (Huawei)
S:  Product=Vodafone Mobile Broadband (Huawei)
S:  SerialNumber=0
C:  #Ifs= 4 Cfg#= 1 Atr=80 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I:  If#= 1 Alt= 0 #EPs= 1 Cls=02(commc) Sub=06 Prot=ff Driver=option
I:  If#= 2 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I:  If#= 3 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage


```but the ./sakis3g --interactive command still results in a segmentation fault after connect with 3G is selected

Sorry for riding along, but any help would be very much appreciated.

@kridybel

have had time to look at the device details . possible it has 2 ports which could be the modem

```
T:  Bus=01 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  7 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=12d1 ProdID=14ae Rev=01.02
S:  Manufacturer=Vodafone Group (Huawei)
S:  Product=Vodafone Mobile Broadband (Huawei)
S:  SerialNumber=0
C:  #Ifs= 4 Cfg#= 1 Atr=80 MxPwr=500mA
[COLOR=Blue]I:  If#= 0 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff Driver=option  <<< THIS ONE ttyUSB0[/COLOR]
I:  If#= 1 Alt= 0 #EPs= 1 Cls=02(commc) Sub=06 Prot=ff Driver=option  [COLOR=Red]<<< NOT SURE what this port is [/COLOR]
[COLOR=Blue]I:  If#= 2 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff Driver=option  <<<<THIS ONE ttyUSB1[/COLOR]
I:  If#= 3 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage
```can look at this post 
              #[**62**]("http://ubuntuforums.org/showpost.php?p=11585976&postcount=62")
There is a script for testing modem-manager , can post the results ,

alexfish

---

### Post by kridybel on 2012-05-17
mm-dbus-test gave following output:

```
----*-----* MM-TEST DEVICE_ENABLE_DISABLE *-----*----

 DEVICE ENABLED : false
 ACTION :enable
 DEVICE ENABLE : true

 ----*-----* MM-TEST DEVICE_INFO *-----*----

 DEVICE :1
 MASTER_DEVICE :/sys/devices/pci0000:00/0000:00:1d.7/usb1/1-1
 ENUMERATED DEVICE TYPE :1
 DEVICE INFO :Vodafone (Huawei) K3806 31.116.27.07.37
 MODEM TYPE :GSM
 DIAL COMMAND :*99#

 ----*-----* MM-TEST MM-INFO *-----*-----

 DRIVER :option1
 DEVICE :/dev/ttyUSB0
 PIN STATUS :""
 ENUMERATED IP METHOD :Use PPP to get the address.
 DEVICE ENABLED : true
 ACTION :disconnect
 DEVICE ENABLE : false

```

---

### Post by alexfish on 2012-05-17
@kridybel

modem-manager is not finding registration data from the device .

can try using ppp for the connection,  call editor from command-line
```

sudo pppconfig
``` can try using /dev/ttyUSB0 first then try a connection using/dev/ttyUSB1
call ppp by the connection name IE : ```
pon <connection-name>
``` , if have permission problems
```
sudo pon <connection-name>
```

---

### Post by kridybel on 2012-05-17
Thanks,


I have made configuration files for USB0 (<name>) and USB1 (<name1>).

Nothing happens after the sudo pon <name> or sudo pon <name1> command.

What should happen after the sudo pon command?

thx for the support.

---

### Post by alexfish on 2012-05-17
wait a few moments then enter this command in the terminal
```
plog
``` it will list the last few lines of the sys log , 
Example
```
alexfish@alexfish-desktop:~$ plog
May 17 21:20:35 alexfish-desktop pppd[2055]: rcvd [IPCP ConfNak id=0x3 <addr 92.40.67.243> <ms-dns1 217.171.132.1> <ms-dns2 217.171.135.1>]
May 17 21:20:35 alexfish-desktop pppd[2055]: sent [IPCP ConfReq id=0x4 <addr 92.40.67.243> <ms-dns1 217.171.132.1> <ms-dns2 217.171.135.1>]
May 17 21:20:35 alexfish-desktop pppd[2055]: rcvd [IPCP ConfAck id=0x4 <addr 92.40.67.243> <ms-dns1 217.171.132.1> <ms-dns2 217.171.135.1>]
May 17 21:20:35 alexfish-desktop pppd[2055]: Could not determine remote IP address: defaulting to 10.64.64.64
May 17 21:20:35 alexfish-desktop pppd[2055]: local  IP address 92.40.67.243
May 17 21:20:35 alexfish-desktop pppd[2055]: remote IP address 10.64.64.64
May 17 21:20:35 alexfish-desktop pppd[2055]: primary   DNS address 217.171.132.1
May 17 21:20:35 alexfish-desktop pppd[2055]: secondary DNS address 217.171.135.1
May 17 21:20:35 alexfish-desktop pppd[2055]: Script /etc/ppp/ip-up started (pid 2102)
May 17 21:20:38 alexfish-desktop pppd[2055]: Script /etc/ppp/ip-up finished (pid 2102), status = 0x0

```
or can monitor the events in 
another terminal with this command
```
tail -f /var/log/syslog
```

just want to mention , been on a thread where for some reason wvdial has been used to some success where MM has failed.

---

### Post by kridybel on 2012-05-20
the plog command following on the pon gives:

```
kris@kris-1011PX:~$ sudo pon belgacom
[sudo] password for kris: 
kris@kris-1011PX:~$ plog
May 20 20:58:35 kris-1011PX chat[2622]: send (ATZ^M)
May 20 20:58:35 kris-1011PX chat[2622]: expect (OK)
May 20 20:58:35 kris-1011PX chat[2622]: ^M
May 20 20:58:35 kris-1011PX chat[2622]: OK
May 20 20:58:35 kris-1011PX chat[2622]:  -- got it
May 20 20:58:35 kris-1011PX chat[2622]: send (ATDT*99#^M)
May 20 20:58:35 kris-1011PX chat[2622]: expect (CONNECT)
May 20 20:58:35 kris-1011PX chat[2622]: ^M
May 20 20:58:35 kris-1011PX chat[2622]: ^M
May 20 20:58:35 kris-1011PX chat[2622]: ERROR^M

```

---

### Post by xlearner on 2012-07-05
Dear AlexFish,

I need your help (again). I have a usb mobile broadband device from HUAWEI TECHNOLOGIES. The service provider is MTS Mblaze in India. I want to connect to Internet using this. But for some reason it does not work!

The output of the command usb-devices is as follows:
T:  Bus=03 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  5 Spd=12  MxCh= 0
D:  Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=12d1 ProdID=1446 Rev=00.00
S:  Manufacturer=HUAÿWEI TECHNOLOGIES
S:  Product=HUAWEI Mobile
S:  SerialNumber=ÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿ
C:  #Ifs= 1 Cfg#= 1 Atr=a0 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=(none)

So it can be seen that the driver is 'none'. The vendor & product ids are 12d1:1446. I followed the commands as you have suggested. But it still does not work :-(! Here is the output of the commands:

$ cat /usr/bin/option_12d1\:1446 
#! /bin/bash
echo 1C9E 9605 > /sys/bus/usb-serial/drivers/option1/new_id

ls -l /usr/bin/option_12d1\:1446 
-rwxr-xr-x 1 root root 74 Jul  5 15:50 /usr/bin/option_12d1:1446

$ ls -l /sys/bus/usb-serial/drivers/option1/new_id 
-rwxr--r-- 1 root root 4096 Jul  5 16:06 /sys/bus/usb-serial/drivers/option1/new_id

$ cat /etc/udev/rules.d/option.rules
ATTRS{idVendor}=="12d1", ATTRS{idProduct}=="1446", RUN+="/sbin/modprobe option"
ATTRS{idVendor}=="12d1", ATTRS{idProduct}=="1446", RUN+="/usr/bin/option_12d1:1446"

Having followed your commands, unfortuntely it still does not connect. The driver option for this device listed in the usb-devices command is still none. So can you please guide me on this? Thanks a lot for your help and cooperation. 

Regds
Xlearner

---

### Post by alexfish on 2012-07-05
@ xlearner

Looks as if the device has not switched

try this command from the terminal

```
sudo usb_modeswitch -v 0x12d1 -p 0x1446 -M "55534243123456780000000000000011060000000000000000000000000000"
```then list the device with
```
usb-devices
```

alexfish

---

### Post by xlearner on 2012-07-05
@Alexfish,

I followed the command as you suggested. Here is the output:

$ sudo usb_modeswitch -v 0x12d1 -p 0x1446 -M "55534243123456780000000000000011060000000000000000000000000000"

Looking for default devices ...
   found matching product ID
   adding device
 Found device in default mode, class or configuration (1)
Accessing device 003 on bus 003 ...
Getting the current device configuration ...
 OK, got current device configuration (1)
Using first interface: 0x00
Using endpoints 0x08 (out) and 0x87 (in)
Inquiring device details; driver will be detached ...
Looking for active driver ...
 No driver found. Either detached before or never attached

SCSI inquiry data (for identification)
-------------------------
  Vendor String: HUAWEI  
   Model String: Mass Storage    
Revision String: 2.31
-------------------------

USB description data (for identification)
-------------------------
Manufacturer: HUA&#65533;WEI TECHNOLOGIES
     Product: HUAWEI Mobile
  Serial No.: &#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;
-------------------------
Setting up communication with interface 0
Using endpoint 0x08 for message sending ...
Trying to send message 1 to endpoint 0x08 ...
 OK, message successfully sent
Resetting response endpoint 0x87
Resetting message endpoint 0x08
-> Run lsusb to note any changes. Bye.
$

After this output, I listed the devices with the command usb-devices as you suggested. I have listed the output only for this device below:
$ usb-devices
.
.
.
T:  Bus=03 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  3 Spd=12  MxCh= 0
D:  Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=12d1 ProdID=1446 Rev=00.00
S:  Manufacturer=HUAÿWEI TECHNOLOGIES
S:  Product=HUAWEI Mobile
S:  SerialNumber=ÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿ
C:  #Ifs= 1 Cfg#= 1 Atr=a0 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=(none)
.
.
.
.
$

So the driver is still none. Am I missing something?

BTW, when I attempted these steps, I was connected to a regular wireless network. Can that affect the working of the usb modem? Thanks again!

---

### Post by alexfish on 2012-07-05
Not sure ,

the amount of info shown does not match a similar device that have tested,

do know this device "12d1 1446" can be problematic   , it has various modes of operation when switched + product ID's vary when switched.

or how your provider has configured it,
 

also behaves differently , depending on the Kernel

need to know if your dual booting with windows or using virtual box or similar ,

also trying plugging the device before and after booting , this sometimes can be important if the device is getting reset,

also check the sim card is inserted the correct way , 

if the device still not switching , check to see if working in windows.

failing that , can only suggest trying to get advice from the Modeswitch forum

**[Draisberghof - Software - USB_ModeSwitch]("http://www.google.com/url?sa=t&rct=j&q=usb%20modeswitch&source=web&cd=1&ved=0CFsQFjAA&url=http%3A%2F%2Fwww.draisberghof.de%2Fusb_modeswitch%2F&ei=tT_2T73TB-nL0QWmyN25DQ&usg=AFQjCNHXRDd_7g_A3ekgGQ2d_tARDOR6iA&cad=rja")**


or try installing Huawei's own drivers + software,

note if using Huawie drivers then it may not be seen by Network Manager

can look here , note best chance for these devices is to use Latest Ubuntu 

                        [COLOR=#980101]**[ubuntu]**[/COLOR] 			 			[Huawei Mobile Broadband Devices (Ubuntu 12.04)]("http://ubuntuforums.org/showthread.php?t=1974458")    : use at own risk

alexfish

---

### Post by xlearner on 2012-07-06
Alexfish,

Thanks for the information. I will look at the pointers that you gave me. I will look into it. 

Strangely enough, this modem was working very well in 11.10. Once I updated to 12.04, it stopped working. It is sad to know that things that used to work on an earlier have stopped working in the latest version. 

Xlearner

---

### Post by alexfish on 2012-07-06
> **xlearner said:**
> Alexfish,

Thanks for the information. I will look at the pointers that you gave me. I will look into it. 

Strangely enough, this modem was working very well in 11.10. Once I updated to 12.04, it stopped working. It is sad to know that things that used to work on an earlier have stopped working in the latest version. 

Xlearner

Strange perhaps try re-installing usb_modeswitch

also some times deleting the existing connection in NM ,then make new , also helps.

have a look in the log file viewer , syslog , see what it shows

regards

alexfish

---

### Post by xlearner on 2012-07-06
Alexfish,

Actually I distinctly remember how I used to connect through Internet on 11.10. I was having classic gnome 2.0 on Ubuntu 11.10. I used to follow these steps: Firstly, I had to right click on the Network Connections manager. Then I used to enable the Mobile Broadband option. 
Only when I enabled to the Mobile Broadband option, I was able to see the option for connecting to Internet using the USB Modem. 

But the problem in 12.04 is that I don't see any option for enabling the Mobile Broadband option. I am able to 'Edit Connections' and create a network connection for the USB Modem. After creating the connection, it is just not appearing in the list of the networks available. 

So do you have any idea, how I can enable the Mobile Broadband option? Currently I am still running classic gnome 2.0 on Ubuntu 12.04. 

Thanks
Xlearner

---

### Post by alexfish on 2012-07-06
> **xlearner said:**
> Alexfish,

Actually I distinctly remember how I used to connect through Internet on 11.10. I was having classic gnome 2.0 on Ubuntu 11.10. I used to follow these steps: Firstly, I had to right click on the Network Connections manager. Then I used to enable the Mobile Broadband option. 
Only when I enabled to the Mobile Broadband option, I was able to see the option for connecting to Internet using the USB Modem. 

But the problem in 12.04 is that I don't see any option for enabling the Mobile Broadband option. I am able to 'Edit Connections' and create a network connection for the USB Modem. After creating the connection, it is just not appearing in the list of the networks available. 

So do you have any idea, how I can enable the Mobile Broadband option? Currently I am still running classic gnome 2.0 on Ubuntu 12.04. 

Thanks
Xlearner
Hi

First, is to get the device recognized as a modem,

so need to see any results from the syslog,

open up the log file viewer , the plug the modem,

post any info which shows the modem details,

from this I may have an idea of what action can be taken,

once the device has switched to modem mode then it is easy to get connect from the Terminal , say he I think.

can also try this command from the terminal 
```
tail -f /var/log/syslog
```then plug the modem

regards

alexfish

---

### Post by xlearner on 2012-07-06
Alexfish,

I did as you have suggested. I am displaying the output of 'tail -f /var/log/syslog'. There is a line in the middle. It signifies the instant after which I plugged the modem. 

Xlearner

Jul  7 02:52:51 sath-VPCSA35GG mtp-probe: checking bus 2, device 13: "/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.3"
Jul  7 02:52:51 sath-VPCSA35GG mtp-probe: bus: 2, device: 13 was not an MTP device
Jul  7 02:53:12 sath-VPCSA35GG kernel: [18025.266834] CPU3: Package power limit notification (total events = 76333)
Jul  7 02:53:12 sath-VPCSA35GG kernel: [18025.266837] CPU2: Package power limit notification (total events = 76333)
Jul  7 02:53:12 sath-VPCSA35GG kernel: [18025.266841] CPU1: Package power limit notification (total events = 75807)
Jul  7 02:53:12 sath-VPCSA35GG kernel: [18025.266843] CPU0: Package power limit notification (total events = 75791)
Jul  7 02:53:12 sath-VPCSA35GG kernel: [18025.266924] CPU1: Package power limit normal
Jul  7 02:53:12 sath-VPCSA35GG kernel: [18025.266927] CPU3: Package power limit normal
Jul  7 02:53:12 sath-VPCSA35GG kernel: [18025.266929] CPU2: Package power limit normal
Jul  7 02:53:12 sath-VPCSA35GG kernel: [18025.266931] CPU0: Package power limit normal
---------------------------------------------------------------------------------------------------------------------------------------------------------------
Jul  7 02:55:43 sath-VPCSA35GG kernel: [18175.795452] usb 3-1: new full-speed USB device number 5 using xhci_hcd
Jul  7 02:55:43 sath-VPCSA35GG mtp-probe: checking bus 3, device 5: "/sys/devices/pci0000:00/0000:00:1c.2/0000:04:00.0/usb3/3-1"
Jul  7 02:55:43 sath-VPCSA35GG mtp-probe: bus: 3, device: 5 was not an MTP device
Jul  7 02:55:43 sath-VPCSA35GG kernel: [18175.837011] scsi9 : usb-storage 3-1:1.0
Jul  7 02:55:43 sath-VPCSA35GG kernel: [18175.920135] usbcore: registered new interface driver usbserial
Jul  7 02:55:43 sath-VPCSA35GG kernel: [18175.920144] USB Serial support registered for generic
Jul  7 02:55:43 sath-VPCSA35GG kernel: [18175.920162] usbcore: registered new interface driver usbserial_generic
Jul  7 02:55:43 sath-VPCSA35GG kernel: [18175.920163] usbserial: USB Serial Driver core
Jul  7 02:55:43 sath-VPCSA35GG kernel: [18175.940683] USB Serial support registered for GSM modem (1-port)
Jul  7 02:55:43 sath-VPCSA35GG kernel: [18175.940757] usbcore: registered new interface driver option
Jul  7 02:55:43 sath-VPCSA35GG kernel: [18175.940758] option: v0.7.2:USB Driver for GSM modems
Jul  7 02:55:44 sath-VPCSA35GG kernel: [18176.838650] scsi 9:0:0:0: CD-ROM            HUAWEI   Mass Storage     2.31 PQ: 0 ANSI: 0
Jul  7 02:55:44 sath-VPCSA35GG kernel: [18176.851555] sr1: scsi-1 drive
Jul  7 02:55:44 sath-VPCSA35GG kernel: [18176.851691] sr 9:0:0:0: Attached scsi CD-ROM sr1
Jul  7 02:55:44 sath-VPCSA35GG kernel: [18176.851822] sr 9:0:0:0: Attached scsi generic sg4 type 5
Jul  7 02:55:45 sath-VPCSA35GG usb_modeswitch: switching device 12d1:1446 on 003/005

---

### Post by alexfish on 2012-07-06
looks like mtpbrobe having a look at the device first, for me this is a new one

Looked at, possible mtp-probe may be part of mtp-tools , for media transfere 

if the probe is holding the device then it could be a problem

suggest look at the System Monitor to see if a daemon is running , RE apart of the mtp-tools

if there is suggest killing the daemon , can do that from the System monitor

or from the terminal

```
sudo killall <name of daemon>
```

also check and see if there are two instances of udev running

can also suggest dissable usb_modeswitch

```
sudo gedit /etc/usb_modeswitch.conf
```
edit the line
```
DisableSwitching=0
```to
```
DisableSwitching=1
```
save and exit

after the probing , wait a while then issue the usb_modeswitch command , have already posted how to do this.

see what happens

regards

alexfish

---

### Post by xlearner on 2012-07-07
Alexfish,

I tried to look for mtp daemon as you suggested. But I could not find any such process in the system monitor. I tried it on the terminal as well:
$ ps -ef|grep mtp
sath    3518  3219  0 17:32 pts/0    00:00:00 grep --color=auto mtp
I could not find any such process. I have attached log from the output of the command, 'ps -ef'. 

Next, I wanted to execute the other steps mentioned in your post. But I was not clear on one thing: Do you still want me to disable usb_modeswitch, probe it and issue usb_modeswitch command? I am asking this as I was not sure if this is related to mtp probe daemon or unrelated to it. 
If they are not unrelated, then I will execute these steps. 

Thanks
Xlearner

---

### Post by xlearner on 2012-07-07
Alexfish,

Continuing with my previous reply, I executed the other steps as well. First I edited, /etc/usb_modeswitch.conf and set DisableSwitching=1. Then I plugged the usb modem, "12d1 1446". The output of usb-devices for this device after plugging the device is as follows: 

> 
T:  Bus=03 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  3 Spd=12  MxCh= 0
D:  Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=12d1 ProdID=1446 Rev=00.00
S:  Manufacturer=HUAÿWEI TECHNOLOGIES
S:  Product=HUAWEI Mobile
S:  SerialNumber=ÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿ
C:  #Ifs= 1 Cfg#= 1 Atr=a0 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage


So I can see that the driver is set to usb-storage. Next, I tried to switch the usb modem using the command you suggested previously on the terminal. But surprisingly, it is giving an error. The output is as follows:

> $ sudo usb_modeswitch -v 0x12d1 -p 0x1446 -M "55534243123456780000000000000011060000000000000000000000000000"

Looking for default devices ...
   found matching product ID
   adding device
 Found device in default mode, class or configuration (1)
Accessing device 002 on bus 003 ...
Getting the current device configuration ...
 OK, got current device configuration (1)
Using first interface: 0x00
Using endpoints 0x08 (out) and 0x87 (in)
Inquiring device details; driver will be detached ...
Looking for active driver ...
 OK, driver found ("usb-storage")
 OK, driver "usb-storage" detached

 Could not get INQUIRY response (error -19)
Error: could not get description string "manufacturer"
Error: could not get description string "product"
Error: could not get description string "serial number"

USB description data (for identification)
-------------------------
Manufacturer: 
     Product: 
  Serial No.: 
-------------------------
Looking for active driver ...
 No driver found. Either detached before or never attached
Setting up communication with interface 0
 Could not claim interface (error -19). Skipping message sending
-> Run lsusb to note any changes. Bye.


So any suggestions? 

Xlearner

---

### Post by alexfish on 2012-07-08
Hi

Not sure what is happening , I have not install 12.04 as of yet.

Yet Last reports I received , indicated that the Device ID 12d1,1446 worked in both modes . See last page
[How To : Mobile Broadband Connections [ Ubuntu 11.04 : 10.10 : 10.04 : 9.10]]("http://ubuntuforums.org/showthread.php?t=1466490")             ([IMG]http://ubuntuforums.org/images/rebrand/misc/multipage.gif[/IMG]  [1]("http://ubuntuforums.org/showthread.php?t=1466490") [2]("http://ubuntuforums.org/showthread.php?t=1466490&page=2") [3]("http://ubuntuforums.org/showthread.php?t=1466490&page=3") ... [Last Page]("http://ubuntuforums.org/showthread.php?t=1466490&page=8"))

Please Note this Tutorial is now closed.

on Ubuntu 12.04 , but now wondering if there is diff between 64 bit and 32 bit systems

can post if system 32 or 64 bit

I do know some devices may work with a different message , this will not implement the ethernet type interface $g mode, present on newer devices , sakis3g ,usually gets them working in the 3g mode, but still operate at the faster speeds (4g) of the standard 3g method of connecting.

So, 
from what I am seeing , best advice , Visit the usb_modeswitch forum.

They may advise installing usb_modeswitch from source , IE , compile it ,for and on your
system , It is easy to do, even for a novice ,also Josh is very helpful , but not in a direction,
where usb_modeswitch scripts have been adapted to suit some systems, the main one
 for some Ubuntu versions , could be the lack of tcl , 

regards

alexfish

---

### Post by xlearner on 2012-07-09
Alexfish,

I am currently running 32 bit version of ubuntu 12.04. 

I will ask the same query at usb_modeswitch forum. Let me hope for the best!

In the meantime, I will also try to get hold of a system that has 11.10 (since I know that it works perfectly well on that system). I will see the output of /var/log and compare it with the output in 12.04 when I plugin the usb modem. 

Xlearner

---

### Post by surja on 2012-07-10
sad that Ubuntu isn't issuing a permanent fix for this irritating problem. I had to switch to Fedora where this problem with 3G dongles does not exist.

---

### Post by alexfish on 2012-07-10
> **surja said:**
> sad that Ubuntu isn't issuing a permanent fix for this irritating problem. I had to switch to Fedora where this problem with 3G dongles does not exist.

Hi surga

I am not sure if this a specific as in "Ubuntu" , if it were , then I would have presumed to have seen a lot more , "Can't  Connect" , Threads ,

Lets see what the out come is between the two version + the out come , if any,  via usb_modeswitch forum 

alexfish

---

### Post by xlearner on 2012-07-10
Surja,

Yes, I know it can be frustrating. Strangely, this modem was working well on ubuntu 11.10. But somehow it stopped working on ubuntu 12.04. 

Xlearner

---

### Post by alexfish on 2012-07-11
Hi all


Not sure if this has any bearing on the subject but worth

looking at  POST #[**7**]("http://ubuntuforums.org/showpost.php?p=12084973&postcount=7")

had been on that thread , re serial port problem

but worth checking out

regards


alexfish

---

### Post by xlearner on 2012-07-12
Alexfish,

Something really intersting happened. I went through the other post and followed the steps suggested. I installed gnome-system-tools and invoked the command users-admin.

Then, as suggested I selected 'Groups'. But then, there were so many options that I did not know which one to select for usbmodem. But as suggested, I selected dialout. Apart from that I randomly chose a few more options.

Earlier, in the /etc/usb_modeswitch.conf file, I had set DisableSwitching=0. I changed it 1. 

Then I logged out & logged in. I plugged the device in. To my great surprise, I was able to connect to mobile broadband Internet through this device. It worked well. Later, I disconnected from the mobile Internet and disconnected the device. 

But after that I was never again able to connect to mobile broadband through the device. I am just not able to reproduce the steps that allowed me to connect to Internet. So I am back to square 1 :-(! Although for once I was able to connect to Internet through this device :-)!

Xlearner

---

### Post by alexfish on 2012-07-12
> **xlearner said:**
> Alexfish,

Something really intersting happened. I went through the other post and followed the steps suggested. I installed gnome-system-tools and invoked the command users-admin.

Then, as suggested I selected 'Groups'. But then, there were so many options that I did not know which one to select for usbmodem. But as suggested, I selected dialout. Apart from that I randomly chose a few more options.

Earlier, in the /etc/usb_modeswitch.conf file, I had set DisableSwitching=0. I changed it 1. 

Then I logged out & logged in. I plugged the device in. To my great surprise, I was able to connect to mobile broadband Internet through this device. It worked well. Later, I disconnected from the mobile Internet and disconnected the device. 

But after that I was never again able to connect to mobile broadband through the device. I am just not able to reproduce the steps that allowed me to connect to Internet. So I am back to square 1 :-(! Although for once I was able to connect to Internet through this device :-)!

Xlearner

what happens if change the .conf back to
DisableSwitching=0

Not sure if the tools are necessary , the commands for this used to be
list what you can access
```
id
```if not in the dip or dialout , then

```
sudo adduser <YOURUSERNAME> dip
sudo adduser <YOURUSERNAME> dialout
```alexfish

---

### Post by xlearner on 2012-07-17
Alexfish,

I am getting back on this thread after sometime. I found a machine with Ubutnu 11.10 installed. On that machine, I tested this device. As said earlier, it was working perfectly fine. 

I was seeing the output of the commands. Let me show the outputs of these devices:

Output of 'usb-devices' for this device:

> 
Ubuntu 12.04:
*************
T: Bus=03 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#= 3 Spd=12 MxCh= 0
D: Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs= 1
P: Vendor=12d1 ProdID=1446 Rev=00.00
S: Manufacturer=HUAÿWEI TECHNOLOGIES
S: Product=HUAWEI Mobile
S: SerialNumber=ÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿ
C: #Ifs= 1 Cfg#= 1 Atr=a0 MxPwr=500mA
I: If#= 0 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=(none)

Ubuntu 11.10:
*************
T:  Bus=02 Lev=02 Prnt=02 Port=03 Cnt=02 Dev#=  6 Spd=12  MxCh= 0
D:  Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=12d1 ProdID=140b Rev=00.00
S:  Manufacturer=HUAÿWEI TECHNOLOGIES
S:  Product=HUAWEI Mobile
S:  SerialNumber=ÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿ
C:  #Ifs= 4 Cfg#= 1 Atr=a0 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I:  If#= 1 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I:  If#= 2 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I:  If#= 3 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage


It can be seen that ubuntu 12.04 is seeing this device differently from ubuntu 11.10. On 12.04, the Vendor=12d1, ProdID=1446. But on 11.10, it is Vendor=12d1, ProdID=140b. This is little strange to me. For the same device, the product id is different!!

Next, I checked the output of /var/log:

> 
Ubuntu 12.04:
*************
Jul 7 02:52:51 sath-VPCSA35GG mtp-probe: checking bus 2, device 13: "/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.3"
Jul 7 02:52:51 sath-VPCSA35GG mtp-probe: bus: 2, device: 13 was not an MTP device
Jul 7 02:53:12 sath-VPCSA35GG kernel: [18025.266834] CPU3: Package power limit notification (total events = 76333)
Jul 7 02:53:12 sath-VPCSA35GG kernel: [18025.266837] CPU2: Package power limit notification (total events = 76333)
Jul 7 02:53:12 sath-VPCSA35GG kernel: [18025.266841] CPU1: Package power limit notification (total events = 75807)
Jul 7 02:53:12 sath-VPCSA35GG kernel: [18025.266843] CPU0: Package power limit notification (total events = 75791)
Jul 7 02:53:12 sath-VPCSA35GG kernel: [18025.266924] CPU1: Package power limit normal
Jul 7 02:53:12 sath-VPCSA35GG kernel: [18025.266927] CPU3: Package power limit normal
Jul 7 02:53:12 sath-VPCSA35GG kernel: [18025.266929] CPU2: Package power limit normal
Jul 7 02:53:12 sath-VPCSA35GG kernel: [18025.266931] CPU0: Package power limit normal
---------------------------------------------------------------------------------------------------------------------------------------------------------------
# The device was plugged at this instant
---------------------------------------------------------------------------------------------------------------------------------------------------------------
Jul 7 02:55:43 sath-VPCSA35GG kernel: [18175.795452] usb 3-1: new full-speed USB device number 5 using xhci_hcd
Jul 7 02:55:43 sath-VPCSA35GG mtp-probe: checking bus 3, device 5: "/sys/devices/pci0000:00/0000:00:1c.2/0000:04:00.0/usb3/3-1"
Jul 7 02:55:43 sath-VPCSA35GG mtp-probe: bus: 3, device: 5 was not an MTP device
Jul 7 02:55:43 sath-VPCSA35GG kernel: [18175.837011] scsi9 : usb-storage 3-1:1.0
Jul 7 02:55:43 sath-VPCSA35GG kernel: [18175.920135] usbcore: registered new interface driver usbserial
Jul 7 02:55:43 sath-VPCSA35GG kernel: [18175.920144] USB Serial support registered for generic
Jul 7 02:55:43 sath-VPCSA35GG kernel: [18175.920162] usbcore: registered new interface driver usbserial_generic
Jul 7 02:55:43 sath-VPCSA35GG kernel: [18175.920163] usbserial: USB Serial Driver core
Jul 7 02:55:43 sath-VPCSA35GG kernel: [18175.940683] USB Serial support registered for GSM modem (1-port)
Jul 7 02:55:43 sath-VPCSA35GG kernel: [18175.940757] usbcore: registered new interface driver option
Jul 7 02:55:43 sath-VPCSA35GG kernel: [18175.940758] option: v0.7.2:USB Driver for GSM modems
Jul 7 02:55:44 sath-VPCSA35GG kernel: [18176.838650] scsi 9:0:0:0: CD-ROM HUAWEI Mass Storage 2.31 PQ: 0 ANSI: 0
Jul 7 02:55:44 sath-VPCSA35GG kernel: [18176.851555] sr1: scsi-1 drive
Jul 7 02:55:44 sath-VPCSA35GG kernel: [18176.851691] sr 9:0:0:0: Attached scsi CD-ROM sr1
Jul 7 02:55:44 sath-VPCSA35GG kernel: [18176.851822] sr 9:0:0:0: Attached scsi generic sg4 type 5
Jul 7 02:55:45 sath-VPCSA35GG usb_modeswitch: switching device 12d1:1446 on 003/005


Ubuntu 11.10:
*************
Jul 16 22:24:26 sathya-Vostro-3400 acpid: 1 client rule loaded
Jul 16 22:24:26 sathya-Vostro-3400 kernel: [11211.427187] r8169 0000:13:00.0: eth0: link down
Jul 16 22:24:26 sathya-Vostro-3400 kernel: [11211.428132] ADDRCONF(NETDEV_UP): eth0: link is not ready
Jul 16 22:24:26 sathya-Vostro-3400 NetworkManager[902]: <info> (wlan0): supplicant interface state: starting -> ready
Jul 16 22:24:26 sathya-Vostro-3400 NetworkManager[902]: <info> (wlan0): device state change: unavailable -> disconnected (reason 'supplicant-available') [20 30 42]
Jul 16 22:24:26 sathya-Vostro-3400 NetworkManager[902]: <info> (wlan0): supplicant interface state: ready -> inactive
Jul 16 22:24:28 sathya-Vostro-3400 kernel: [11213.467528] EXT4-fs (sda7): re-mounted. Opts: errors=remount-ro,commit=600
Jul 16 22:25:16 sathya-Vostro-3400 xscreensaver: pam_ecryptfs: pam_sm_authenticate: /home/sathya is already mounted
Jul 16 22:25:25 sathya-Vostro-3400 kernel: [11270.310529] ieee80211 phy0: wl0: wlc_recv: dropping a frame with invalid src mac address, a2: 00:00:00:00:00:00
Jul 16 22:25:29 sathya-Vostro-3400 kernel: [11275.093407] ieee80211 phy0: wl0: wlc_recv: dropping a frame with invalid src mac address, a2: 00:00:00:00:00:00
Jul 16 22:25:47 sathya-Vostro-3400 kernel: [11292.395648] ieee80211 phy0: wl0: wlc_recv: dropping a frame with invalid src mac address, a2: 00:00:00:00:00:00
Jul 16 22:25:53 sathya-Vostro-3400 kernel: [11299.124328] ieee80211 phy0: wl0: wlc_recv: dropping a frame with invalid src mac address, a2: 2f:72:75:6e:20:74
Jul 16 22:25:56 sathya-Vostro-3400 kernel: [11301.485540] ieee80211 phy0: wl0: wlc_recv: dropping a frame with invalid src mac address, a2: 00:00:00:00:00:00
Jul 16 22:26:06 sathya-Vostro-3400 kernel: [11311.685389] ieee80211 phy0: wl0: wlc_recv: dropping a frame with invalid src mac address, a2: 00:00:00:00:00:00
Jul 16 22:26:18 sathya-Vostro-3400 kernel: [11323.568614] ieee80211 phy0: wl0: wlc_recv: dropping a frame with invalid src mac address, a2: 00:00:00:00:00:00
Jul 16 22:26:22 sathya-Vostro-3400 kernel: [11327.542950] ieee80211 phy0: wl0: wlc_recv: dropping a frame with invalid src mac address, a2: 00:00:00:00:00:00
Jul 16 22:26:23 sathya-Vostro-3400 kernel: [11328.264762] ieee80211 phy0: wl0: wlc_recv: dropping a frame with invalid src mac address, a2: 00:00:00:00:00:00
Jul 16 22:26:23 sathya-Vostro-3400 kernel: [11328.739137] ieee80211 phy0: wl0: wlc_recv: dropping a frame with invalid src mac address, a2: 00:00:00:00:00:00
Jul 16 22:26:25 sathya-Vostro-3400 kernel: [11330.476324] ieee80211 phy0: wl0: wlc_recv: dropping a frame with invalid src mac address, a2: ef:ff:ef:ef:ef:ff
---------------------------------------------------------------------------------------------------------------------------------------------------------------
# The device was plugged at this instant
---------------------------------------------------------------------------------------------------------------------------------------------------------------
Jul 16 22:26:42 sathya-Vostro-3400 kernel: [11347.478438] usb 2-1.1: new full speed USB device number 12 using ehci_hcd
Jul 16 22:26:42 sathya-Vostro-3400 kernel: [11347.573070] scsi26 : usb-storage 2-1.1:1.0
Jul 16 22:26:42 sathya-Vostro-3400 mtp-probe: checking bus 2, device 12: "/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.1"
Jul 16 22:26:42 sathya-Vostro-3400 mtp-probe: bus: 2, device: 12 was not an MTP device
Jul 16 22:26:43 sathya-Vostro-3400 usb_modeswitch: switching device 12d1:1446 on 002/012
Jul 16 22:26:43 sathya-Vostro-3400 kernel: [11348.431744] usb 2-1.1: USB disconnect, device number 12
Jul 16 22:26:46 sathya-Vostro-3400 kernel: [11351.950689] usb 2-1.1: new full speed USB device number 13 using ehci_hcd
Jul 16 22:26:46 sathya-Vostro-3400 kernel: [11352.045605] option 2-1.1:1.0: GSM modem (1-port) converter detected
Jul 16 22:26:46 sathya-Vostro-3400 kernel: [11352.045790] usb 2-1.1: GSM modem (1-port) converter now attached to ttyUSB0
Jul 16 22:26:46 sathya-Vostro-3400 mtp-probe: checking bus 2, device 13: "/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.1"
Jul 16 22:26:46 sathya-Vostro-3400 kernel: [11352.046661] option 2-1.1:1.1: GSM modem (1-port) converter detected
Jul 16 22:26:46 sathya-Vostro-3400 kernel: [11352.046839] usb 2-1.1: GSM modem (1-port) converter now attached to ttyUSB1
Jul 16 22:26:46 sathya-Vostro-3400 kernel: [11352.047584] option 2-1.1:1.2: GSM modem (1-port) converter detected
Jul 16 22:26:46 sathya-Vostro-3400 kernel: [11352.047744] usb 2-1.1: GSM modem (1-port) converter now attached to ttyUSB2
Jul 16 22:26:46 sathya-Vostro-3400 kernel: [11352.048314] scsi30 : usb-storage 2-1.1:1.3
Jul 16 22:26:47 sathya-Vostro-3400 mtp-probe: bus: 2, device: 13 was not an MTP device
Jul 16 22:26:47 sathya-Vostro-3400 modem-manager[897]: <info>  (ttyUSB0) opening serial port...
Jul 16 22:26:47 sathya-Vostro-3400 logger: usb_modeswitch: switched to 12d1:140b on 002/013
Jul 16 22:26:47 sathya-Vostro-3400 modem-manager[897]: <info>  (ttyUSB0) closing serial port...
Jul 16 22:26:47 sathya-Vostro-3400 modem-manager[897]: <info>  (ttyUSB0) serial port closed
Jul 16 22:26:47 sathya-Vostro-3400 modem-manager[897]: <info>  (ttyUSB0) opening serial port...
Jul 16 22:26:47 sathya-Vostro-3400 modem-manager[897]: <info>  (Huawei): CDMA modem /sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.1 claimed port ttyUSB0
Jul 16 22:26:47 sathya-Vostro-3400 kernel: [11353.046601] scsi 30:0:0:0: CD-ROM            HUAWEI   Mass Storage     2.31 PQ: 0 ANSI: 0
Jul 16 22:26:47 sathya-Vostro-3400 kernel: [11353.048544] scsi 30:0:0:1: Direct-Access     HUAWEI   SD Storage       2.31 PQ: 0 ANSI: 2
Jul 16 22:26:47 sathya-Vostro-3400 kernel: [11353.065720] sr1: scsi-1 drive
Jul 16 22:26:47 sathya-Vostro-3400 kernel: [11353.065991] sr 30:0:0:0: Attached scsi CD-ROM sr1
Jul 16 22:26:47 sathya-Vostro-3400 kernel: [11353.066204] sr 30:0:0:0: Attached scsi generic sg2 type 5
Jul 16 22:26:47 sathya-Vostro-3400 kernel: [11353.066687] sd 30:0:0:1: Attached scsi generic sg3 type 0
Jul 16 22:26:47 sathya-Vostro-3400 modem-manager[897]: <info>  (ttyUSB0) closing serial port...
Jul 16 22:26:47 sathya-Vostro-3400 modem-manager[897]: <info>  (ttyUSB0) serial port closed
Jul 16 22:26:48 sathya-Vostro-3400 kernel: [11353.074492] sd 30:0:0:1: [sdb] Attached SCSI removable disk
Jul 16 22:26:50 sathya-Vostro-3400 modem-manager[897]: <info>  (ttyUSB1) opening serial port...
Jul 16 22:26:50 sathya-Vostro-3400 modem-manager[897]: <info>  (ttyUSB2) opening serial port...
Jul 16 22:26:50 sathya-Vostro-3400 modem-manager[897]: <info>  (ttyUSB2) closing serial port...
Jul 16 22:26:50 sathya-Vostro-3400 modem-manager[897]: <info>  (ttyUSB2) serial port closed
Jul 16 22:26:50 sathya-Vostro-3400 modem-manager[897]: <info>  (Huawei): CDMA modem /sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.1 claimed port ttyUSB2
Jul 16 22:27:02 sathya-Vostro-3400 modem-manager[897]: <info>  (ttyUSB1) closing serial port...
Jul 16 22:27:02 sathya-Vostro-3400 modem-manager[897]: <info>  (ttyUSB1) serial port closed
Jul 16 22:27:02 sathya-Vostro-3400 modem-manager[897]: <info>  (ttyUSB1) opening serial port...
Jul 16 22:27:05 sathya-Vostro-3400 modem-manager[897]: <info>  (ttyUSB1) closing serial port...
Jul 16 22:27:05 sathya-Vostro-3400 modem-manager[897]: <info>  (ttyUSB1) serial port closed
Jul 16 22:27:05 sathya-Vostro-3400 modem-manager[897]: <info>  (Huawei): CDMA modem /sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.1 claimed port ttyUSB1
Jul 16 22:27:05 sathya-Vostro-3400 NetworkManager[902]: <warn> (ttyUSB0): failed to look up interface index
Jul 16 22:27:05 sathya-Vostro-3400 NetworkManager[902]: <info> WWAN now disabled by management service
Jul 16 22:27:05 sathya-Vostro-3400 NetworkManager[902]: <info> (ttyUSB0): new CDMA/EVDO device (driver: 'option1' ifindex: 0)
Jul 16 22:27:05 sathya-Vostro-3400 NetworkManager[902]: <info> (ttyUSB0): exported as /org/freedesktop/NetworkManager/Devices/6
Jul 16 22:27:05 sathya-Vostro-3400 NetworkManager[902]: <info> (ttyUSB0): now managed
Jul 16 22:27:05 sathya-Vostro-3400 NetworkManager[902]: <info> (ttyUSB0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Jul 16 22:27:05 sathya-Vostro-3400 NetworkManager[902]: <info> (ttyUSB0): deactivating device (reason 'managed') [2]
Jul 16 22:27:05 sathya-Vostro-3400 NetworkManager[902]: nm_system_iface_flush_routes: assertion `ifindex > 0' failed
Jul 16 22:27:05 sathya-Vostro-3400 NetworkManager[902]: nm_system_iface_flush_addresses: assertion `ifindex > 0' failed
Jul 16 22:27:05 sathya-Vostro-3400 NetworkManager[902]: <info> (ttyUSB0): device state change: unavailable -> disconnected (reason 'none') [20 30 0]
Jul 16 22:27:09 sathya-Vostro-3400 kernel: [11374.054357] ieee80211 phy0: wl0: wlc_recv: dropping a frame with invalid src mac address, a2: 00:00:00:00:00:00
Jul 16 22:27:09 sathya-Vostro-3400 kernel: [11374.753277] ieee80211 phy0: wl0: wlc_recv: dropping a frame with invalid src mac address, a2: e7:ff:dd:e4:e7:ff
Jul 16 22:27:09 sathya-Vostro-3400 kernel: [11374.905414] ieee80211 phy0: wl0: wlc_recv: dropping a frame with invalid src mac address, a2: e5:ff:da:e1:e5:ff
Jul 16 22:27:09 sathya-Vostro-3400 kernel: [11374.923346] ieee80211 phy0: wl0: wlc_recv: dropping a frame with invalid src mac address, a2: e9:ff:e1:e7:e9:ff
Jul 16 22:27:12 sathya-Vostro-3400 kernel: [11377.427090] ieee80211 phy0: wl0: wlc_recv: dropping a frame with invalid src mac address, a2: 00:00:00:00:00:00
Jul 16 22:27:18 sathya-Vostro-3400 kernel: [11383.589891] ieee80211 phy0: wl0: wlc_recv: dropping a frame with invalid src mac address, a2: 00:00:00:00:00:00


So any suggestions on the difference? Is this a bug? Thanks!

---

### Post by alexfish on 2012-07-17
Think had already mentioned this device has many guises

depending on various environments

suggest use Sakis3g

disable the mode switching , in the ".conf"

then try sakis3g

see what happens

regards

alexfish

---

### Post by xlearner on 2012-07-18
Alexfish,

Thanks for the tip. Actually the device that I have works on CDMA. But sadly sakis 3G does not support CDMA currently. So this does not work. 

In any case, I have posted on USB_ModeSwitch forum. Let me see if Josua can figure out this riddle :-)!

Thanks
Xlearner

---

### Post by alexfish on 2012-07-18
> **xlearner said:**
> Alexfish,

Thanks for the tip. Actually the device that I have works on CDMA. But sadly sakis 3G does not support CDMA currently. So this does not work. 

In any case, I have posted on USB_ModeSwitch forum. Let me see if Josua can figure out this riddle :-)!

Thanks
Xlearner

you only need to use sakis3g to prepare the modem

look at the menus

---

### Post by surja on 2012-07-22
> **alexfish said:**
> Hi surga

I am not sure if this a specific as in "Ubuntu" , if it were , then I would have presumed to have seen a lot more , "Can't  Connect" , Threads ,

Lets see what the out come is between the two version + the out come , if any,  via usb_modeswitch forum 

alexfish

I suppose this just affects a few specific devices. But it is quite strange that it doesn't get detected as a modem in Ubuntu 12.04. It's also interesting that I have faced the same modem detection problem when using the Linux Mint 13, which is based on Ubuntu 12.04. The modem problem did not exist in earlier versions of Linux Mint which were based on earlier versions of Ubuntu. So I suppose it would be safe to infer that something did break in this new 12.04 version which has not been resolved yet, since it affects just a few devices (e.g. the modem that I use, Capitel EVDO modem, device id 1c9e:9e00). Yet this device works perfectly in Fedora 17.

---

### Post by xlearner on 2012-07-24
Alexfish,

I posted this topic on usb_modesetich forum. There I have got interesting replies: [http://www.draisberghof.de/usb_modeswitch/bb/viewtopic.php?t=960](http://www.draisberghof.de/usb_modeswitch/bb/viewtopic.php?t=960)

So as I understand, there is a bug in 12.04. It was suggested that we have to re-install usb_modeswitch in 12.04 (like what you suspected). I trying the suggestions by Josh. 

Xlearner

---

### Post by surja on 2012-07-24
> **xlearner said:**
> Alexfish,

I posted this topic on usb_modesetich forum. There I have got interesting replies: [http://www.draisberghof.de/usb_modeswitch/bb/viewtopic.php?t=960](http://www.draisberghof.de/usb_modeswitch/bb/viewtopic.php?t=960)

So as I understand, there is a bug in 12.04. It was suggested that we have to re-install usb_modeswitch in 12.04 (like what you suspected). I trying the suggestions by Josh. 

Xlearner

If it works it would be wonderful. Would be very grateful if you can explain in detail how to uninstall the default Ubunru 12.04 package and install the Debian version.

---

### Post by xlearner on 2012-07-25
Dear Surja,

I was able to figure out how to make it work on Ubuntu 12.04 using the instructions from this forum: [http://www.draisberghof.de/usb_modeswitch/bb/viewtopic.php?t=960](http://www.draisberghof.de/usb_modeswitch/bb/viewtopic.php?t=960). 

I hope you are also using the same distribution. But installing the debian package did not work. For some reason it failed. I had to do it manually. 

Here are the steps:

1. Go to folder: /usr/share/usb_modeswitch. In this folder, there is one zipped file: configPack.tar.gz.

The next step depends on this configPack.tar.gz. So, if you do not have this file, then I suggest you reinstall usb_modeswitch along with the data files from synaptic package manager. 

2. Copy this file into a folder of your choice. Say, home/test.

```

$ cp /usr/share/usb_modeswitch/configPack.tar.gz /home/test 

```

3. Then unzip the file configPack.tar.gz
```

$ cd /home/test 
$ tar -xvf configPack.tar.gz

```

4. After unzipping, invoke the following command:
```

$ sudo /usr/sbin/usb_modeswitch -I -W -s 10 -c "<path-to>/12d1:1446" -v 12d1 -p 1446

```
where <path-to> in this case is /home/test. 

After a few minutes my usb modem switched. Once it has switched, connecting to the Internet is simple. I believe that you can easily figure out the steps.

Xlearner

---

### Post by alexfish on 2012-07-25
> **xlearner said:**
> Dear Surja,

I was able to figure out how to make it work on Ubuntu 12.04 using the instructions from this forum: [http://www.draisberghof.de/usb_modeswitch/bb/viewtopic.php?t=960](http://www.draisberghof.de/usb_modeswitch/bb/viewtopic.php?t=960). 

I hope you are also using the same distribution. But installing the debian package did not work. For some reason it failed. I had to do it manually. 

Here are the steps:

1. Go to folder: /usr/share/usb_modeswitch. In this folder, there is one zipped file: configPack.tar.gz.

The next step depends on this configPack.tar.gz. So, if you do not have this file, then I suggest you reinstall usb_modeswitch along with the data files from synaptic package manager. 

2. Copy this file into a folder of your choice. Say, home/test.

```

$ cp /usr/share/usb_modeswitch/configPack.tar.gz /home/test 

```3. Then unzip the file configPack.tar.gz
```

$ cd /home/test 
$ tar -xvf configPack.tar.gz

```4. After unzipping, invoke the following command:
```

$ sudo /usr/sbin/usb_modeswitch -I -W -s 10 -c "<path-to>/12d1:1446" -v 12d1 -p 1446

```where <path-to> in this case is /home/test. 

After a few minutes my usb modem switched. Once it has switched, connecting to the Internet is simple. I believe that you can easily figure out the steps.

Xlearner

sorted in one way , but Can suggest downloading the source files from the site,

the instructions to install are easy to follow , do know that **Debian packages will break Ubuntu version ,** it is Mentioned at the site.

before installing source , un-install the Ubuntu version including the data

see what happens

regards

alexfish

---

### Post by yktan on 2012-07-27
> **alexfish said:**
> Here is a sample
 Remember to change the ID's according to the device Highlighted in blue , as listed by the (lsusb) command
```

sudo su
``````
gedit /usr/bin/option_[COLOR=Blue]1C9E[/COLOR]:[COLOR=Blue]9605[/COLOR]
```add code : Remember to change the ID's according to the device Highlighted in blue , as listed by the (lsusb) command
```

#! /bin/bash
echo [COLOR=Blue]1C9E 9605[/COLOR] > /sys/bus/usb-serial/drivers/option1/new_id
```save the file and exit gedit
```
chmod +x /usr/bin/[COLOR=Blue]option_1C9E:9605[/COLOR]
``````
gedit /etc/udev/rules.d/option.rules
```add the code: Remember to edit the device Id's according to your device , note the lowercase letters !!!! IE , [COLOR=Blue]c[/COLOR] , not C :
 ```
ATTRS{idVendor}=="[COLOR=Blue]1c9e[/COLOR]", ATTRS{idProduct}=="[COLOR=Blue]9605[/COLOR]", RUN+="/sbin/modprobe option"
ATTRS{idVendor}=="[COLOR=Blue]1c9e[/COLOR]", ATTRS{idProduct}=="[COLOR=Blue]9605[/COLOR]", RUN+="/usr/bin/[COLOR=Blue]option_1C9E:9605[/COLOR]"
```save and exit

if not loading try re-plugging the device

Thanks, this solved my problem with my modem (D-Link DWM-156 with ID 07d1:7e11) :popcorn:

---

### Post by xlearner on 2012-07-27
Alexfish,

I uninstalled the usb_modeswitch installed by ubuntu. Then, I downloaded and compiled the code. Now, the modem connects automatically and everythings works fine :-)!! 

So looks like there is a bug in Ubuntu 12.04. 

Thanks
Xlearner

---

### Post by mithlesh on 2012-08-17
Plz help me I am new to ubuntu platform.
I am want to use samsung mobile as mobile modem in ubuntu 11.04 but not able do it.
i use this code
```

  lsusb

```
and get this
get usb info 04e8:6795 Samsung Electronics Co. Ltd, S5230

and also use this code
```

 ls -al/dev/serial/by-id

```
and get this
```

  Usb_Samsung_Electronics_Mobile_USB_Modem_1.0_335411803284587_9_if00../../ttyACM0

```

when i use 
```

  gnome-ppp

```
and try setup modem didn't get tty/ACM0 modem 

plz help...

---

### Post by djibrilcoulibaly on 2012-09-25
is ALexfish is would like help here also [http://ubuntuforums.org/showthread.php?t=2061631&page=2](http://ubuntuforums.org/showthread.php?t=2061631&page=2) ?
I won't post same thing any where that why I just give my post link .

---

### Post by gstephen on 2012-09-30
> **rienesl said:**
> Hi,
got exactly the same Problem with the XS Stick P14 (1c9e:9605). After hours of searching for a solution, I did the following:
1) First tell networtk-manager, he should remember the PIN for the SIM-Card. This will be important for step 3!
2) Adding the following line in /etc/rc.local:
```
modprobe usbserial vendor=0x1c9e product=0x9605
```This switches the stick from datastore-mode into the modem-mode.
3) Added a script with the following in auto-start:
```

#!/bin/sh
sleep 75
nmcli nm wwan on

```This gets around the bug of the network-manager, which disables the mobile broadband after every restart. Don't be suprised about the 75 seconds wait. The USB-Stick takes up to 55 Seconds to initialisize after typing in the pin for the sim. Additionally the networkmanager is launched after the script started and it will need a few seconds to start itself. So adding at this point 20 seconds is safe, you might try up to 10 seconds, but that might fail. Will definitive fail, if you skipped point 1!
4) (Optional) Configure the mobile connection to connect automatically

Works so far, but fails, when unplugging the stick. I thought, I'll have to live with this, but then I was searching for something different and found this. I tried your advise which is described in post 11 and now replugging works. OK, it woks not 100% I still have to re-enable mobile broadband, by typing in ```
nmcli nm wwan on
``` but hey, I don't have to restart the whole machine anymore ;)

you mean edit the "rc.local" file and add the lines anywhere

---

### Post by bise on 2012-10-30
> **alexfish said:**
> Here is a sample
 Remember to change the ID's according to the device Highlighted in blue , as listed by the (lsusb) command
```

sudo su
``````
gedit /usr/bin/option_[COLOR=Blue]1C9E[/COLOR]:[COLOR=Blue]9605[/COLOR]
```add code : Remember to change the ID's according to the device Highlighted in blue , as listed by the (lsusb) command
```

#! /bin/bash
echo [COLOR=Blue]1C9E 9605[/COLOR] > /sys/bus/usb-serial/drivers/option1/new_id
```save the file and exit gedit
```
chmod +x /usr/bin/[COLOR=Blue]option_1C9E:9605[/COLOR]
``````
gedit /etc/udev/rules.d/option.rules
```add the code: Remember to edit the device Id's according to your device , note the lowercase letters !!!! IE , [COLOR=Blue]c[/COLOR] , not C :
 ```
ATTRS{idVendor}=="[COLOR=Blue]1c9e[/COLOR]", ATTRS{idProduct}=="[COLOR=Blue]9605[/COLOR]", RUN+="/sbin/modprobe option"
ATTRS{idVendor}=="[COLOR=Blue]1c9e[/COLOR]", ATTRS{idProduct}=="[COLOR=Blue]9605[/COLOR]", RUN+="/usr/bin/[COLOR=Blue]option_1C9E:9605[/COLOR]"
```save and exit

if not loading try re-plugging the device

Your Advice helps me also. Thanks Alexfish. :)

---

### Post by surja on 2012-10-30
> **xlearner said:**
> Alexfish,

I uninstalled the usb_modeswitch installed by ubuntu. Then, I downloaded and compiled the code. Now, the modem connects automatically and everythings works fine :-)!! 

So looks like there is a bug in Ubuntu 12.04. 

Thanks
Xlearner

I think this is the best solution and works perfectly for 12.04 and it's derivatives like Mint 13 etc.

---

### Post by Tomoto91 on 2013-06-20
hi all, 

im new here came to this bye using google, i have a 3g dongle from vodafone code k4305 it says on the box.
i was trying to connect it bye using this guide but when i type sudo su in terminal i must type my password but i cant type ? 
i can type normal but when i must type my password after i typed sudo su i cant type...

please help,

thanks in advance

---

### Post by malakar.subhendu on 2013-06-21
It is not a problem. You are typing the password but u cannot see it. This is enabled by default in linux distros to avoid any chance of getting the password by people behind your back.(the normal * would also do the same thing but it will reveal the length of it). So you should type the password as it is and press enter, it will work.

---

