---
title: "Cannot use ZTE Tu25 4G broadband modem with 10.4"
date: 2010-08-05
forum: Networking &amp; Wireless
---

### Post by coolmac on 2010-08-05
Hi guys,

I'm a web developer and i made up my mind to finally ditch Windows. After installing Ubuntu 10.4, I'm not able to connect to the internet in Ubuntu and i have to download LAMP asap! 

I've done some research and stumbled on Wine but it seems I can't install it when i'm not logged into Linux (and i'm not too sure if it will work anyways). I'm now wondering if there exits any way I can make my modem work inside Ubuntu.

It's a ZTE TU25 4G WiMAX broadband modem. I'd appreciate any help.

Thanks.

---

### Post by alexfish on 2010-08-05
hi

don't know this modem , or even if there are any linux drivers

but lets see if the system sees the device

from the terminal enter these codes and post the results

Code:
lsusb

Code:
ls -al /dev/serial/by-id/usb*

Code:
dmesg | grep -e "modem" -e "tty"

---

### Post by coolmac on 2010-08-05
Thanks for the quick reply...here is the feedback:

```

legend@legendary-station:~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 19d2:0007 ONDA Communication S.p.A. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

legend@legendary-station:~$ ls -al /dev/serial/by-id/usb*
lrwxrwxrwx 1 root root 13 2010-08-06 03:31  /dev/serial/by-id/usb-ZTE Corporation_ZTE Mobile WiMAX USB Ad_0-if00-port0  -> ../../ttyUSB0

legend@legendary-station:~$ dmesg | grep -e "modem" -e "tty"
[    0.000000] console [tty0] enabled
[  114.476113] USB Serial support registered for GSM modem (1-port)
[  114.476190] option 1-1:1.0: GSM modem (1-port) converter detected
[  114.476382] usb 1-1: GSM modem (1-port) converter now attached to ttyUSB0
[  114.476416] option: v0.7.2:USB Driver for GSM modems


```

Thanks..I hope that helps!

---

### Post by alexfish on 2010-08-05
from the info it is recognized by the system and has loaded the option driver { dont know if it is the correct one }

lets see if system  can communicate with the device 

open up the terminal and enter this command to monitor the replies {hopefully}

CODE:
tr -s "\n" < /dev/ttyUSB0

now open up a second terminal and enter this code and post the results {if any }

 echo -e "ATZ\r" > /dev/ttyUSB0
 
 also see if the network manager can configure the device : edit vpn connections / mobile broadband
 
 if the modem is responding to the terminal commands then we might find what the device capabilities are

---

### Post by coolmac on 2010-08-05
the terminal didn't respond at all. I opened two like you said and the cursor was just sort-of blinking there...

I stumbled onto this maybe it will be of help in solving the problem:
[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1476264](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1476264)

I'm ashamed to say i'm not at all familiar with what virtual box can do or how to install it in linux.

Hope it helps.

Thanks

---

### Post by alexfish on 2010-08-05
virtual box may be a way to do it

[http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)

from this install winXXX 

then you may have to configure the network to communicate with linux {there are help files to assist you } 

also look here

[IMG]http://1.2.3.10/bmi/ubuntu-ky.ubuntuforums.org/images/statusicon/subforum_new.gif[/IMG] [Virtualization]("http://ubuntu-ky.ubuntuforums.org/forumdisplay.php?f=308")the main problem is to get the usb device recognised and setting the user permission
 somewhere in there I did a post on how to do this

but if you get stuck send a PM

I would not give up on this device yet as I read somewhere that linux drivers are in progress for such devices 

but i was wondering if removing the loaded driver and then forcing another driver may work , IE CDMA or the bog standard usb serial .I will look further

regards

alexfish

---

### Post by alexfish on 2010-08-05
just had a though

see attachments

its a script file for usb-devices

it may shed some light { but can't say }

also if you could zip the windows drivers and post them { would'nt mind a geek } may be able to spot something

ADDED nearest at present as regards wimax drivers

[http://www.linuxwimax.org/Download](http://www.linuxwimax.org/Download)

---

### Post by coolmac on 2010-08-06
Sorry alexfish, i lost you somewhere buddie. I'm a total noob at this.

> 
[http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)

from this install winXXX which package do I install and how? the files have a .deb extension [i'm assuming it stands for debian?] so i'm kinda clueless how i should deal with them.

I'm interested in zipping the drivers so this can be sorted for everybody...I'm in the process of zipping it right now!

Regards.

Post Update: Uploaded the drivers.

---

### Post by alexfish on 2010-08-06
Ubuntu 10.04 ("Lucid Lynx") [i386]("http://download.virtualbox.org/virtualbox/3.2.6/virtualbox-3.2_3.2.6-63112%7EUbuntu%7Elucid_i386.deb") | [AMD64]("http://download.virtualbox.org/virtualbox/3.2.6/virtualbox-3.2_3.2.6-63112%7EUbuntu%7Elucid_amd64.deb")

to find version match

Code:

uname -m

output may show i386 or i686 for 32bit

---

### Post by coolmac on 2010-08-06
I download the package and managed to find my way around installing it but it didn't finish through because it needs some other packages?

I'm getting a feeling i'm meddling in deep waters now but i'm gonna try and install the missing packages and see how it goes. 

If anyone can help please advise!

---

### Post by alexfish on 2010-08-06
hi  if it is for virtual box you may have to be connect to the net

if problem persist then advise going to the virtulisations in the link above

regards

alexfish

---

### Post by alexfish on 2010-08-06
Just an update on the wimax drivers

since I don't know the device and the site mentioned indicates the drivers are wimax

since these drivers appear to be ones that have to be compiled 

I have put a few feelers out as regards this and if they know of a success on compiling them and how they work etc. 

so for now it looks like virtual box may offer a solution , 

so as regards to the above , it may be a question of watch this space , unless someone else with knowledge of these devices and the linux drivers spots this thread ,and can hopefully assist.

let us know of your progress with virtualbox

regards

alexfish

---

### Post by alexfish on 2010-08-07
have done a kernel search on Ubuntu 10.04 the WIMAX drivers may be  on the system search for files " wimax  " and find wimax.ko

so I could suggest this

remove the option module

CODE:
sudo modprobe -v -r option

and load the wimax module

CODE:

sudo modprobe wimax


view the responses in the log file viewer messages
regards
ADDED think these may be for wireless/but can try/

cdc-wdm are supposed to be for 4g 

                                 As previously posted  link wimax linux
 

 have searched and found
 

 

 Mac OS X support is available on the [Clear download site]("http://www.clear.com/support/download"), and Linux drivers are easily found in places such as SourceForge. Credit goes to Clearwire for opting to go well beyond Windows-only driver support for the device.
 

 Leeds to
 

 **For Intel Computers with WiMAX**

 Intel® provides software, drivers, and technical support information for Intel® wireless products.
 In order for your Intel® computer to properly operate in all Clear network locations, it is strongly recommended you upgrade your device software to version 1.5 or later.
 Failure to upgrade to version 1.5 may cause an interruption in your Clear service.
 For the latest software and support information, or for questions and issues regarding the upgrade of your current system check [here]("http://www.intel.com/support/wireless/wmax/5350_5150/sb/CS-030306.htm").
 
To build and install this software, follow the instructions on each package.  
 ***** The software here is not meant for commercial use and should be treated as experimental. WiMAX based devices typically need to go through rigorous carrier certification tests to be endorsed. Please contact Intel [[EMAIL="linux-wimax@intel.com"]linux-wimax@intel.com[/EMAIL]] if you need an officially supported WiMAX product.  [http://www.intel.com/support/wireless/wmax/5350_5150/sb/CS-030306.htm](http://www.intel.com/support/wireless/wmax/5350_5150/sb/CS-030306.htm)
 RE: linux wimax.org

alexfish

---

### Post by coolmac on 2010-08-08
> **alexfish said:**
> Just an update on the wimax drivers

since I don't know the device and the site mentioned indicates the drivers are wimax

since these drivers appear to be ones that have to be compiled 

I have put a few feelers out as regards this and if they know of a success on compiling them and how they work etc. 

so for now it looks like virtual box may offer a solution , 

so as regards to the above , it may be a question of watch this space , unless someone else with knowledge of these devices and the linux drivers spots this thread ,and can hopefully assist.

let us know of your progress with virtualbox

regards

alexfish

I didn't manage to install virtualbox but i'm sure its the solution that will work. My main worry is that on my hdd i have windows 7 and Linux Ubuntu 10.04. Is't safe for me to have so many OSs??

Can I rely on running Virtual box as my windows installation and get rid of Windows 7 completely? I don't have much space btw so I'm just wondering...

> have done a kernel search on Ubuntu 10.04 the WIMAX drivers may be  on the system search for files " wimax  " and find wimax.ko

so I could suggest this

remove the option module

CODE:
sudo modprobe -v -r option

and load the wimax module

CODE:

sudo modprobe wimax


view the responses in the log file viewer messages
regards
ADDED think these may be for wireless/but can try/

cdc-wdm are supposed to be for 4g 

Will I be able to have wireless access after disabling the option module?

Thanks a lot Alexfish, you've been a real help mate.

---

### Post by alexfish on 2010-08-08
Just came up with this

but it,big $ for a router

                                 **Search wimax/cradle point/compat/linux**

 **Cradlepoint MBR1000 3G/4G Mobile Broadband Router (MBR-1000)**

 **WiFi:** IEEE802.11b/g/n
**Connections:** Ethernet: 1 WAN, 4 LAN
**Cellular:** 2 USB ports/1 Express Card slot
**Firewall:** NAT with SPI
**Encryption:** 64/128 bit WEP, WPA/WPA2, WPA-PSK/WPA2-PSK
**Compatibility:** Windows 98SE+, Mac OS X, Linux, and WiFi-enabled devices
**Device Management:** Via Web Browser
**Certifications:** FCC, RoHS


 **Compatible Devices**:

 **_BridgeMAXX WiMAX_**

 **USB**

 ZTE TU-25
 [http://www.cradlepoint.com/products/mbr1000-mobile-broadband-039n039-router-3g4g-wireless-router](http://www.cradlepoint.com/products/mbr1000-mobile-broadband-039n039-router-3g4g-wireless-router)

---

### Post by alexfish on 2010-08-08
> **coolmac said:**
> I didn't manage to install virtualbox but i'm sure its the solution that will work. My main worry is that on my hdd i have windows 7 and Linux Ubuntu 10.04. Is't safe for me to have so many OSs??

Can I rely on running Virtual box as my windows installation and get rid of Windows 7 completely? I don't have much space btw so I'm just wondering...



Will I be able to have wireless access after disabling the option module?

Thanks a lot Alexfish, you've been a real help mate.

as regards of the wimax driver it may not work , most drivers have device recognition,
if did then there are other tools required "From reading the searches" as it appears to rely on scanning for the service similar to any wireless device,

Been doing a lot of searching / all thing point to the intel side and no search came up with
ZTE , but the drivers point to the wimax protocol etc

from the win drivers section
[ZTEFilter.NT.Services] 
Include=usbstor.inf 
Needs=USBSTOR_BULK.NT.Services 
AddService = usbws320,, filter_Service_Inst 
 
[filter_Service_Inst] 
DisplayName    = %filter.SvcDesc%                             
ServiceType    = 1                  ; SERVICE_KERNEL_DRIVER 
StartType      = 3                  ; SERVICE_DEMAND_START 
ErrorControl   = 1                  ; SERVICE_ERROR_NORMAL 
ServiceBinary  = %12%\usbws320.sys 
LoadOrderGroup = PnP Filter 
 
[Strings] 
ZTE                  = "ZTE Corporation" 
ZTESRCDISK           = "ZTE WiMAX USB NIC Driver Disk" 
StdMfg               = "ZTE Corporation" 
ZTEFilter.DeviceDesc = "ZTE USB WiMAX NIC Switch" 
filter.SvcDesc       = "ZTE USB WiMAX NIC Switch Driver"

Part of above and looking through rest of inf in the windows , driver section look similar to the " cdc-wdm.ko"

next pointer came up with the above post / this cost money

anyway since you got Virtual box sorted

you can load windows as to which version is a matter of choice / smaller the platform the better , Virtual box can recommend the size for the hard disc  or you can define what you want , 

to get rid of windows is a matter of choice , if it works in virtual box then you all options available , especially if the device works and the network configures

at present the virtual box solution may be the best option for these devices until a official kernel driver is released , or until I get feedback on other drivers

or if you have the money and willing to take the plunge , Cradlepoint

Forgot any chance of posting the resusts of the script file usb-devices

regards

alexfish

---

### Post by alexfish on 2010-08-18
Hi

this may be of interest to your quest

RE:Virtual Box

[SOLVED] [Build a small network in Virtualbox]("http://ubuntuforums.org/showthread.php?t=1552202")

regards

alexfish

---

### Post by alexfish on 2010-08-19
done a bit of delving

all pointers for the wimax drivers = i2400

but still don't know if heading in the right direction

found these drivers on the 
Ubuntu 10.04 system 

i2400.ko
i2400-sdio.ko
i2400-usb.ko

So there should be no need to download (there again may be not)

REF:

[http://www.linuxwimax.org/WiMAX-Network-Service-1.3.3-mainline-README.txt](http://www.linuxwimax.org/WiMAX-Network-Service-1.3.3-mainline-README.txt)

This page describes the steps needed to build and use release 1.3.x of the WiMAX Network Service with the kernel stack that has been merged with Linux kernel v2.6.29-rc*.

You need:

    * kernel 2.6.29 (currently only release candidates)
    * Intel 2400 Wireless WiMAX Connection card 

Steps:

   1.

      kernel and drivers: clone the mainline linux kernel tree (2.6.29-rc1 and beyond) or the linux-wimax kernel tree from git://git.kernel.org/pub/scm/linux/kernel/git/inaky/wimax.git, enable the WiMAX drivers (Networking Options > WiMAX, Device Drivers > Network Drivers > WiMAX devices, build, install and reboot into the kernel.
   2.

      wimax-tools: clone the wimax-tools package from git://git.kernel.org/pub/scm/linux/kernel/git/inaky/wimax-tools.git, configure, build and install. You will have to specify the linux source's location that wimax-tools needs for the definitions of the user/kernel space protocol, for that, when running configure, use:

      ./configure --with-i2400m=/path/to/linux-wimax/tree \
                      --sysconfdir=/etc \
                      --localstatedir=/var \
                      --mandir=/usr/share/man \
                      --prefix=/usr
      make
      make install
      ldconfig

   3.

      wimax network service: obtain the 1.3.3 release of the WiMAX-Network-Service, unpack and apply this patch:

      cd WiMAX-Network-Service-1.3.3/
      patch -p1 < ../WiMAX-Network-Service-1.3-mainline0.patch

      Then configure and build.

      ./configure --with-i2400m=/path/to/linux-wimax/tree
      make
      make install

      You need to make sure that the configuration process says something like:

      Using libwimax from /usr/local

      Or the prefix where wimax-tools was installed (which defaults to /usr/local).
   4.

      Firmware: Download and place i2400m-fw-usb.sbcf in /lib/firmware.
   5.

      Supplicant: Download and install according to the instructions in the supplicant package.
   6.

      OMA-DM client: [optional] Download and install according to instructions in the package. 

Now you can start the network service after loading the driver:
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
I have inserted this bit if the option drivers have loaded , then they will have to be removed

so I could suggest this

remove the option module

CODE:
sudo  modprobe -v -r option
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Don't enter the $
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

$ modprobe i2400m-usb

Verify the device is detected: Have a look at the logfile viewer / messages

$ ifconfig wmx0

wmx0      Link encap:Ethernet  HWaddr 00:1d:e1:01:94:32  
          NOARP  MTU:1400  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:5 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

If that is not printing something like what is shown, check your kernel log; could it be wmx1?

Start the network service:

$ wimaxd

Query the status of the card:

$ wimaxcu status

System Status: Ready

If this fails, complaining wimaxd is not running, verify that the daemon hasn't left over a pid file in /var/run, remove it if so and restart wimaxd. This is going to be fixed in the next release.

If the radio was off, turn it on:

$ wimaxcu ron

SW Radio is turned ON.

And scan

$ wimaxcu scan

NSP : XOHM
        ID          : 4
        Signal      : Good
        RSSI        : -33 dBm
        CINR        : 15 dB
        Network Type: Home Network
        Activated

Now you are ready to connect:

$ wimaxcu connect network 4
Connecting to XOHM Network...
Connection Status: Connected.

And run dhclient on the interface:

$ dhclient wmx0

Ready to go! 

anyone willing to try . I don't possess A wimax dongle

alexfish

---

