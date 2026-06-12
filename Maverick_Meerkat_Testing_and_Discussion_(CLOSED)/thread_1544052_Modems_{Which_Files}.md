---
title: "Modems {Which Files}"
date: 2010-08-02
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by alexfish on 2010-08-02
can anyone post the results of the following files
these are generally used by dialup connection software

#!/bin/sh
which lsusb 2> /dev/null
which lshal 2> /dev/null
which hal-device 2> /dev/null
which hal-find-by-property 2> /dev/null
which hal-get-property 2> /dev/null
which hal-set-property 2> /dev/null
which modprobe 2> /dev/null
which wvdial 2> /dev/null
which sudo 2> /dev/null
which gksu 2> /dev/null
which wget 2> /dev/null
which setsid 2> /dev/null
which netstat 2> /dev/null
which ps 2> /dev/null
which chat 2> /dev/null
which getent 2> /dev/null
which xterm 2> /dev/null
which pppd 2> /dev/null
which route 2> /dev/null
which su 2> /dev/null

###############################################

Thanks in advance

alexfish

---

### Post by mdurham on 2010-08-02
> **alexfish said:**
> can anyone post the results of the following files
these are generally used by dialup connection software

#!/bin/sh
which lsusb 2> /dev/null
which lshal 2> /dev/null
which hal-device 2> /dev/null
which hal-find-by-property 2> /dev/null
which hal-get-property 2> /dev/null
which hal-set-property 2> /dev/null
which modprobe 2> /dev/null
which wvdial 2> /dev/null
which sudo 2> /dev/null
which gksu 2> /dev/null
which wget 2> /dev/null
which setsid 2> /dev/null
which netstat 2> /dev/null
which ps 2> /dev/null
which chat 2> /dev/null
which getent 2> /dev/null
which xterm 2> /dev/null
which pppd 2> /dev/null
which route 2> /dev/null
which su 2> /dev/null

###############################################

Thanks in advance

alexfish

/usr/sbin/lsusb
/usr/bin/lshal
/usr/bin/hal-device
/usr/bin/hal-find-by-property
/usr/bin/hal-get-property
/usr/bin/hal-set-property
/sbin/modprobe
/usr/bin/wvdial
/usr/bin/sudo
/usr/bin/gksu
/usr/bin/wget
/usr/bin/setsid
/bin/netstat
/bin/ps
/usr/sbin/chat
/usr/bin/getent
/usr/bin/xterm
/usr/sbin/pppd
/sbin/route
/bin/su

what's it all mean?
Cheers, Mike

---

### Post by alexfish on 2010-08-04
Hi

thanks for the reply 

reason for the request is a follows , if not a little complex but it beholds reason

The new wave of 3g and cdma modems with the {drivers for windows installed on the mass storage device } here the events and
the problems now associated with Udev modem-modeswitch and the usb_modeswitch

1. some devices are automaticaly switch by the kernel via udev and the fdi { no usb_modeswitch required }
2. some devices require usb_modeswitch since they are not recgnized by the kernel { usb_modeswitch required }

the outcome of the having both the udev modem-modeswitch {nolonger } and the usb_modeswitch is as follows

3.1 Some devices that get switch by the kernel may get reset in two different ways , one that is present on boot and one that is present after connecting 
 
3.2 AT BOOT :the device that is connected at boot time will be recognized on the system as device having been switched ,yet present connection managers fail to recognize the correct port for the since the device it's self is not asserting the the CTS,DCD and DSR lines of the serial port { this in it's self is not a fault of the manager it's but that which relates to how the device is first recognised by the two methods of modeswitch } this leaves the problem of resting the device directly { there is a fix}

3.3 AFTER BOOT : some devices will get switch back to masstorage mode if it recognised by both the kernel and the usb_modeswitch so there for requires to be reset and switch back to modem mode this is hard to do since from the desktop as the device is not visible with present tools { only issuing the lsusb command will list the decice { sakis3g will resolve this situation } but not for 3.2

there are other problems that exit as regards user oops , 

all the above is fixable by command line or scripting

part of the above request was to assertain that the neccessary are available {and in the same local} for 9.04, 9.10 , 10,04 and the up and comming "Maverick Meerkat".

can ask if the version you are using is an upgrade or from install by cd or other

thanks again 

regards

alexfish

---

### Post by alexfish on 2010-08-04
Hi

thanks for the reply 

reason for the request is a follows , if not a little complex but it beholds reason

The new wave of 3g and cdma modems with the {drivers for windows installed on the mass storage device } here the events and
the problems now associated with Udev modem-modeswitch and the usb_modeswitch

1. some devices are automaticaly switch by the kernel via udev and the fdi { no usb_modeswitch required }
2. some devices require usb_modeswitch since they are not recgnized by the kernel { usb_modeswitch required }

the outcome of the having both the udev modem-modeswitch {nolonger } and the usb_modeswitch is as follows

3.1 Some devices that get switch by the kernel may get reset in two different ways , one that is present on boot and one that is present after connecting 
 
3.2 AT BOOT :the device that is connected at boot time will be recognized on the system as device having been switched ,yet present connection managers fail to recognize the correct port for the since the device it's self is not asserting the the CTS,DCD and DSR lines of the serial port { this in it's self is not a fault of the manager it's but that which relates to how the device is first recognised by the two methods of modeswitch } this leaves the problem of resting the device directly { there is a fix}

3.3 AFTER BOOT : some devices will get switch back to masstorage mode if it recognised by both the kernel and the usb_modeswitch so there for requires to be reset and switch back to modem mode this is hard to do since from the desktop as the device is not visible with present tools { only issuing the lsusb command will list the decice { sakis3g will resolve this situation } but not for 3.2

there are other problems that exit as regards user oops , 

all the above is fixable by command line or scripting

part of the above request was to assertain that the neccessary are available {and in the same local} for 9.04, 9.10 , 10,04 and the up and comming "Maverick Meerkat".

can ask if the version you are using is an upgrade or from install by cd or other

Forgot to mention / how to get route asserted in the routing tables in the presence of Ethernet or wirless connections
thanks again 

regards

alexfish

---

### Post by mdurham on 2010-08-04
> can ask if the version you are using is an upgrade or from install by cd or other

upgrade

---

