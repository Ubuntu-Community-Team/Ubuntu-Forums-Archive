---
title: "USB modem flooding kernel log with errors"
date: 2012-04-09
forum: Networking &amp; Wireless
---

### Post by Noccy on 2012-04-09
Hi All,

Just discovered this completely flooding my kernel log. My guess is this is the card reader in the modem causing trouble. Is there any way to make this go away?

I am using usb_modeswitch, and the modem part works great. It just seems the kernel is constantly polling the card reader even after switching it into modem mode.

*Edit: I am on Ubuntu 11.10 (with kernel 3.2.0-17), not 10.04 as the sidebar states. It does appear I can't edit most of my details before I hit 50 posts. Interesting...*

```
[185808.008191] sr 30:0:0:0: rejecting I/O to offline device
[185808.008205] sr 30:0:0:0: rejecting I/O to offline device
[185808.697352] option: option_instat_callback: error -71
[185809.463370] option: option_instat_callback: error -71
[185810.006368] sr 30:0:0:0: rejecting I/O to offline device
[185810.006383] sr 30:0:0:0: rejecting I/O to offline device
[185810.187395] option: option_instat_callback: error -71
[185810.997423] option: option_instat_callback: error -71
[185811.793455] option: option_instat_callback: error -71
[185812.006860] sr 30:0:0:0: rejecting I/O to offline device
[185812.006873] sr 30:0:0:0: rejecting I/O to offline device
[185812.679477] option: option_instat_callback: error -71
[185813.519503] option: option_instat_callback: error -71
[185814.006436] sr 30:0:0:0: rejecting I/O to offline device
[185814.006450] sr 30:0:0:0: rejecting I/O to offline device
[185814.389537] option: option_instat_callback: error -71
[185815.231561] option: option_instat_callback: error -71
[185816.006474] sr 30:0:0:0: rejecting I/O to offline device
[185816.006487] sr 30:0:0:0: rejecting I/O to offline device
[185816.189597] option: option_instat_callback: error -71
[185816.957615] option: option_instat_callback: error -71
[185817.811644] option: option_instat_callback: error -71
[185818.008462] sr 30:0:0:0: rejecting I/O to offline device
[185818.008474] sr 30:0:0:0: rejecting I/O to offline device
[185818.609670] option: option_instat_callback: error -71
[185819.347698] option: option_instat_callback: error -71
[185820.008270] sr 30:0:0:0: rejecting I/O to offline device
[185820.008280] sr 30:0:0:0: rejecting I/O to offline device
[185820.113719] option: option_instat_callback: error -71
[185821.013750] option: option_instat_callback: error -71
```

---

### Post by alexfish on 2012-04-10
Seems to be a recurrence of bug  "possible regression in the kernel". this usually gets sorted with updates

Possible causes[FONT=monospace]
[/FONT]> sr 30:0:0:0: rejecting I/O to offline device
Modem Devices : When Ejecting the SR* bit of the device normally switches to SD*

Some Huawie devices want to re-mount with the SR*  . so posible the system is trying to eject the device

Can use the Disk Utility , see what shows as the SR* and the SD* , if the SR* shows try  Safely Remove of SR*  , see what happens
> option: option_instat_callback: error -71
possible due to the above , with modem-manager probing the device , see if it disappears

---

### Post by Noccy on 2012-04-10
Thanks for your reply :) I took a look in Disk Utility, and the card reader as well as the virtual cd device are present in the list, but interestingly enough as /dev/sdd and /dev/sr1 -- no reference anywhere to sr30. Attempting to eject or safely remove either gives an error about being unable to open the device like this:

```
Error detaching: helper exited with exit code 1: Detaching device /dev/sr1
USB device: /sys/devices/pci0000:00/0000:00:1d.7/usb1/1-4)
Cannot open /dev/sr1: No such device or addres
```

It seems the modem works, but the cd/sd turns into ghost devices.

If modem-manager is causing the problem, is it safe to remove this as I am using wvdial to connect? I have only ever really got this stick to work with Ubuntu 8.04s network management tools probably due to it borking out on some of the default init strings. The only way to get wvdial to work was to remove all but the ATZ as any subsequent AT* would make the device hang or bail out with "NO CARRIER".

---

### Post by alexfish on 2012-04-10
Leave modem-manager as is , generally not a good thing to remove ,at some stage you may need to connect with other modems 

Do know some of these devices fail to respond to certain AT commands or been probed for the status lines
 usually return as segmentation fault , depends on the serial configuration (front end ) to the driver

sakis3g is usually best option for alternate connection , as seen wvdial is producing errors as well ,
with sakis3g, can try with the option "-nostorage" and "-noprobe" if there are still problems.

need some info first

can post details of these commands from the terminal

```
usb-devices
``````
lsusb -t
```locate the lines which indicate the device and post only those lines

can also ask if your comp is desktop or laptop

also can go to this thread
[How To : Mobile Broadband Connections [ Ubuntu 11.04 : 10.10 : 10.04 : 9.10]]("http://ubuntuforums.org/showthread.php?t=1466490")

should be some info on how to stop modem-manager daemon running

post #[**62**]("http://ubuntuforums.org/showpost.php?p=11585976&postcount=62") , the is a script for testing modem-manager , can post the results

also look at post #[**61**]("http://ubuntuforums.org/showpost.php?p=11458739&postcount=61")
there is a serial driver in the script "usually works with these devices, can use the argv tty , look for the outputs of the status lines , and post only those lines 
can also use the argv sr , this may find the device on the system , will also indicate if the device is in switch-able state or not

if no tclsh on system the there is a link at the post show how to get it on the system , any problems can send PM

but post the results of the two commands from the terminal first

---

### Post by Noccy on 2012-04-11
I have tried sakis3g, but it was unable to connect, probably due to initstrings there as well :( The system is a desktop box, but I have experienced the same problem on both netbook and laptop where modem-manager haven't been successful in connecting since 8.04.

usb-devices output:
```
T:  Bus=01 Lev=01 Prnt=01 Port=03 Cnt=01 Dev#= 53 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=12d1 ProdID=1001 Rev=00.00
S:  Manufacturer=HUAWEI Technology
S:  Product=HUAWEI Mobile
C:  #Ifs= 5 Cfg#= 1 Atr=e0 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I:  If#= 1 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I:  If#= 2 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I:  If#= 3 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage
I:  If#= 4 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage
```

lsusb -t output:
```
/:  Bus 01.Port 1: Dev 1, Class=root_hub, Driver=ehci_hcd/8p, 480M
    |__ Port 4: Dev 53, If 0, Class=vend., Driver=option, 480M
    |__ Port 4: Dev 53, If 1, Class=vend., Driver=option, 480M
    |__ Port 4: Dev 53, If 2, Class=vend., Driver=option, 480M
    |__ Port 4: Dev 53, If 3, Class=stor., Driver=usb-storage, 480M
    |__ Port 4: Dev 53, If 4, Class=stor., Driver=usb-storage, 480M
```

From what I can gather, everything looks in order here. The output from the nm test script gives this output:

```
 ----*-----* MM-TEST DEVICE_ENABLE_DISABLE *-----*----

 DEVICE ENABLED : true
 ACTION :disconnect
 DEVICE ENABLED : false
 ACTION :enable
 DEVICE ENABLE : true

 ----*-----* MM-TEST DEVICE_INFO *-----*----

 DEVICE :1
 MASTER_DEVICE :/sys/devices/pci0000:00/0000:00:1d.7/usb1/1-4
 ENUMERATED DEVICE TYPE :1
 DEVICE INFO :huawei E1750 11.126.07.04.00
 MODEM TYPE :GSM
 DIAL COMMAND :*99#
 NETWORK MCC :SWE
 NETWORK MNC :DEN

 ----*-----* MM-TEST MM-INFO *-----*-----

 DRIVER :option1
 DEVICE :/dev/ttyUSB0
 PIN STATUS :""
 ENUMERATED IP METHOD :Use PPP to get the address.
 DEVICE ENABLED : true
 ACTION :disconnect
 DEVICE ENABLE : false
```

Do you know where the initstrings for modem-manager are located and If there is a way to override these? I killed wvdial, tried network manager with no success, and went back to wvdial which connected instantly.

Also, the sr* warnings have suddenly stopped in the dmesg log. The option_instat_callback warnings are still showing up however.

---

### Post by alexfish on 2012-04-12
This device as it is does not like been probed , the MM test would have revealed a lot more info

IE: the MNC and MCC numbers
so not surprised Network Manager would be able to connect. .. also proven by sakis3g

but does show the device can be enabled and disabled , so need to ask if it is an old or new device
Does it work with windows. / it may need a firmware update ?

Can at this point think it may be the sim card , or the device is faulty  but not sure , would have like to have seen the state of the Status lines from the eject script ,
 or even if the script sees the device , also this would prove if UDEV is working , or if the device is continually connecting or disconnecting from the system

as to the errors in the log file , do they show in other versions of Ubuntu ? .. Would like to see if removing or disable MM helps with errors in the log file , this would prove one thing

at present can continue using wvdial but delete any init strings , have you try ppp ,, Does it connect 100% of the time ,

Just had a thought
Have you tried Network Manager using the dial command "*99***1# " and omit the APN
> Also, the sr* warnings have suddenly stopped in the dmesg log.Wonder if this due to Modem-Manager disabling from the device? RE from the last lines of the script output[FONT=monospace]
[/FONT]> DRIVER Option1  
DEVICE :/dev/ttyUSB0  
PIN STATUS :""  
ENUMERATED IP METHOD :Use PPP to get the address. 
 DEVICE ENABLED : true  
ACTION :disconnect  
DEVICE ENABLE : falsealexfish

---

### Post by Noccy on 2012-04-12
> **alexfish said:**
> This device as it is does not like been probed , the MM test would have revealed a lot more info IE: the MNC and MCC numbers

That's weird, as wvdial gives me this as I add a few additional initstrings to probe the device. How come modem-manager is unable to resolve this configuration?

```
--> Sending: AT+COPS?
AT+COPS?
+COPS: 0,2,"24004",2
OK
--> Sending: AT+CSQ
AT+CSQ
+CSQ: 5,99
OK
--> Sending: AT+GMM
AT+GMM
E1750
OK
```

The modem works with Windows, using the Telenor software from the ISP. I did have a go at the Huawei modem tool, but didn't get further than being able to read the text messages received, most probably due to it throwing an insane amount of errors during the install and appears to have a bundled pppd with a hardcoded location that was incorrect (no pppd in the requested location). The version I tried was 21.003.28.00.03 (from the archive name).

As for UDEV, it does the switching properly, and I am using the modem right now to write this post, so it appears to stay connected. I unfortunately don't have any other version of Ubuntu to test on -- all my systems are running 11.10. 

> **alexfish said:**
> Have you tried Network Manager using the dial command "*99***1# " and omit the APN.

I have tried leaving the APN blank as well as filling in the proper APN, but MM still won't connect. It tries for a few seconds and then tells me the connection was disconnected. Repeated attempts (without unplugging) render the same result. 

The dial command I haven't tried, but wvdial works fine with *99#. If I'm not mistaken the additional **1 indicates that the first (and in the case of a dongle I would think only?) profile is to be used? I remember having to tweak this when I tethered with my phone a few years ago to have it not connect using the MMS profile :) Will try changing this later tonite to see what the outcome is.

Is it possible to knock modem-manager into debug mode to see what exactly it is doing as it attempts to connect?

My current kernel version is 3.2.0-17-generic #27-Ubuntu SMP as provided by [http://ppa.launchpad.net/francisbrwn9/kernels/ubuntu](http://ppa.launchpad.net/francisbrwn9/kernels/ubuntu).

---

### Post by alexfish on 2012-04-12
Interesting , can have a go with these

in this sequence


```
ATZ

AT+CGDCONT? should reveal the CGDCONT registers

AT+COPS=0,2
AT+COPS?     should reveal mcc and mnc numbers

ATZ
AT+COPS=?  should reveal the operators available / not sure if wvdial will time out with this one
```What happens if you delete the existing config in NM then make a new connection.

Note:[FONT=monospace]
[/FONT]> +CSQ: 5,99the signal strength is not good / try moving the device to get nearer to "10,99" or more , 15 is reasonably good

---

