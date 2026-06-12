---
title: "Error while installing USB modem software (Huawey EC 167)"
date: 2011-09-05
forum: Networking &amp; Wireless
---

### Post by jujiyangasli on 2011-09-05
hello, i am a beginner in ubuntu
my dist: Ubuntu 11.04


Please help me.
i was trying to install a USB modem software for my Huawey EC 167-EVDO, and got some error.

the software functions as a dialer for the modem. (e.g sending/recieving sms, etc..)


while installing i got the following error:

```
Install NDIS driver failed.
The compiling environment is not all ready.
Please check gcc, make and kernel buid (/lib/modules/2.6.38-11-generic/build) to be all installed?
```


Result:
The modem software (dialer) cannot detect my modem. Thus i can't send /receive sms.

can somebody hep me fix this error.

---

### Post by jujiyangasli on 2011-09-05
if this is usefull, my full installation output:

```
Installing AHA Dialer...             [ done ] 

Installing Driver...

/usr/local/Mobile_Partner/driver/ndis_driver
Usage: modinfo [-0][-F field][-k kernelversion][-b basedir]  module...
 Prints out the information about one or more module(s).
 If a fieldname is given, just print out that field (or nothing if not found).
 Otherwise, print all information out in a readable form
 If -0 is given, separate with nul, not newline.
 If -b is given, use an image of the module tree.
ERROR: Removing 'cdc_ether': No such file or directory
ERROR: Removing 'usbnet': No such file or directory
ERROR: Removing 'hw_cdc_driver': No such file or directory
make -C src/ clean
make[1]: Entering directory `/usr/local/Mobile_Partner/driver/ndis_driver/ndis_src/src'
rm -rf *.o *.ko *~ core* .dep* .*.d .*.cmd *.mod.c *.a *.s .*.flags .tmp_versions Module.symvers Modules.symvers *.order
/usr/local/Mobile_Partner/driver/ndis_driver/ndis_src/src/add_header.sh  "clean" "/lib/modules/2.6.38-11-generic/build/include/linux/usb"
rmmod -f hw_cdc_driver
ERROR: Removing 'hw_cdc_driver': No such file or directory
make[1]: *** [clean] Error 1
make[1]: Leaving directory `/usr/local/Mobile_Partner/driver/ndis_driver/ndis_src/src'
make: *** [clean] Error 2
make -C src/ modules
make[1]: Entering directory `/usr/local/Mobile_Partner/driver/ndis_driver/ndis_src/src'
#/usr/local/Mobile_Partner/driver/ndis_driver/ndis_src/src/add_header.sh  "modules" "/lib/modules/2.6.38-11-generic/build/include/linux/usb"
make -C /lib/modules/2.6.38-11-generic/build SUBDIRS=/usr/local/Mobile_Partner/driver/ndis_driver/ndis_src/src modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.38-11-generic'
  CC [M]  /usr/local/Mobile_Partner/driver/ndis_driver/ndis_src/src/hw_cdc_driver.o
/usr/local/Mobile_Partner/driver/ndis_driver/ndis_src/src/hw_cdc_driver.c: In function ‘rx_tlp_parse’:
/usr/local/Mobile_Partner/driver/ndis_driver/ndis_src/src/hw_cdc_driver.c:602:7: warning: ISO C90 forbids mixed declarations and code
/usr/local/Mobile_Partner/driver/ndis_driver/ndis_src/src/hw_cdc_driver.c: At top level:
/usr/local/Mobile_Partner/driver/ndis_driver/ndis_src/src/hw_cdc_driver.c:2011:2: error: unknown field ‘ioctl’ specified in initializer
make[3]: *** [/usr/local/Mobile_Partner/driver/ndis_driver/ndis_src/src/hw_cdc_driver.o] Error 1
make[2]: *** [_module_/usr/local/Mobile_Partner/driver/ndis_driver/ndis_src/src] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.38-11-generic'
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/usr/local/Mobile_Partner/driver/ndis_driver/ndis_src/src'
make: *** [modules] Error 2
make -C src/ install
make[1]: Entering directory `/usr/local/Mobile_Partner/driver/ndis_driver/ndis_src/src'
#install -m 744 -c hw_cdc_driver.ko /lib/modules/2.6.38-11-generic/kernel/drivers/usb/net
#depmod -a
#modprobe hw_cdc_driver
/usr/local/Mobile_Partner/driver/ndis_driver/ndis_src/src/add_header.sh  "install"
modprobe hw_cdc_driver
FATAL: Module hw_cdc_driver not found.
make[1]: *** [install] Error 1
make[1]: Leaving directory `/usr/local/Mobile_Partner/driver/ndis_driver/ndis_src/src'
make: *** [install] Error 2

Install NDIS driver failed.
The compiling environment is not all ready.
Please check gcc, make and kernel buid(/lib/modules/2.6.38-11-generic/build) to be all installed?
Now please enter any key to finish other installations.

NDIS is disabled, and only Modem can be used.



```

---

### Post by praseodym on 2011-09-05
Hi,

> ```
Please check gcc, make and kernel buid(/lib/modules/2.6.38-11-generic/build) to be all installed?
```

Did you install the necessary tools before compiling?

```
sudo apt-get install linux-headers-generic build-essential dkms
```
Then try again:

```
cd /path/to/folder/
make clean  #cleaning up the mess ;-)
make
sudo make uninstall
sudo make install
```

---

### Post by pdc on 2011-09-06
so it sounds as though you want to use one of these

[http://modem-techno.blogspot.com/2010/07/huawei-ec-167-cdma-usb-modem-2000-1x.html](http://modem-techno.blogspot.com/2010/07/huawei-ec-167-cdma-usb-modem-2000-1x.html)

........well...........plug it into your computer;

type 

> lsusb

........I'm betting you're going to see

> 12d1:1446 ONDA Communication S.p.A. 

......if.........your modem is seen only as a storage device;

.........well.........if so...........................

you need to install usb_modeswitch

(and its data package)

here is some reading

[http://www.draisberghof.de/usb_modeswitch/#download](http://www.draisberghof.de/usb_modeswitch/#download)

and get the **_TWO_** packages.......from here

[http://packages.debian.org/sid/usb-modeswitch](http://packages.debian.org/sid/usb-modeswitch)

go to the BOTTOM of the page and select the right file for your processor; install this first

and go here

[http://packages.debian.org/sid/usb-modeswitch-data](http://packages.debian.org/sid/usb-modeswitch-data)

and again;...........go to the BOTTOM of the page.............for the data package

as you click to download for both, gdebi will hopefully jump in and offer to install

then we hope your device will be "unmasked" and seen as a modem..

---

### Post by jujiyangasli on 2011-09-06
Guys, thanks alot for your replies... :)

**@praseodym**

yes, the package is new...

```
build-essential is already the newest version.
dkms is already the newest version.
dkms set to manually installed.
linux-headers-generic is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 5 not upgraded.
```




**@pdc**
yes, i'm using [_[COLOR="DarkRed"]that modem[/COLOR]_]("http://modem-techno.blogspot.com/2010/07/huawei-ec-167-cdma-usb-modem-2000-1x.html")

i found this in my *lsusb* output:
```
Bus 001 Device 012: ID 12d1:140c Huawei Technologies Co., Ltd. 
```

i tried *[COLOR="Blue"]# usb_modeswitch[/COLOR]*
and it showed the *[COLOR="blue"]usb_modeswitch[/COLOR]* help content in my terminal. so i guess it's already installed. 

and ubuntu software center view the packages as "installed"
(usb-modeswitch and usb-modeswitch-data)


My modem has already identified as a "modem", i guess. 
(i'm connecting to the internet via the modem right now).


my main problem is, i can't send or receive any sms without the dialer software, 
and my monthly subscription is done via sms (including warnings on bandwidth-quota and etc)



i don't really know much about linux script... 
but i think the installer made some errors (or, somehow, is not compatible with natty). 
Will i help myself if upload the 'install' script?


fyi: the "dialer" install command:

```
# sudo bash install
```

---

### Post by pdc on 2011-09-07
> _**my main problem is, i can't send or receive any sms without the dialer software**_,
and my monthly subscription is done via sms (including warnings on bandwidth-quota and etc)



........that sort of gets lost in the rest,.............

there ain't any easy programmes I know of to send SMS in linux;

folks refer to wammu

[https://wammu.eu/](https://wammu.eu/)

.......I tried it with an old Huawei E220 modem: I couldn't get it to send SMS messages.......

When I need to check balances; I take a simcard (as I have GSM) and put that in a phone, and text from the phone;

a utility to send SMS would be good;

......google on it .......

---

### Post by jujiyangasli on 2011-10-03
update: 
never succeed to send SMS via gammu or wammu. don't know why..

my installation has a windows version. so, i'm using virtual machine instead.

case closed--

---

