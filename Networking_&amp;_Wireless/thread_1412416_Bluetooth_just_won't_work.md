---
title: "Bluetooth just won't work"
date: 2010-02-21
forum: Networking &amp; Wireless
---

### Post by Kruptein on 2010-02-21
I have ubuntu 9.10 and bluetooth won't work at all.
after doing:  sudo /etc/init.d/bluetooth start
-sudo /etc/init.d/bluetooth status  returns: bluetooth is not running
-bluetooth daemon is not shown

I use a bluetooth dongle btw

---

### Post by Kruptein on 2010-02-22
Bump*

My dongle is from Idream bluetooth
should I install something?
-gnome-bluetooth and bluez-gnome are installed

:confused:

---

### Post by tlcstat on 2010-02-22
Greetings,
I would start out by installing Blueman from the package manager. If your dongle won't load I suggest the Trendnet from Walmart for $15. It works just fine in my Toshiba and my Dell. The model is TBW-105UB but all of the Trendnet adapters should work fine. Just plug it in and open Blueman. Search for you device. Had my wife on the internet over my Motorola W845 in 5 minutes. 
tlcstat

Greetings,
In addition to the above the IO Gear GBU421W adapter from Walmart for $20 is plug and play in Ubuntu Karmic. It has a 30ft range, exceeds all speed standards and is very compact. You can plug it in and leave it installed. It is barely noticeable.
tlcstat

---

### Post by Kruptein on 2010-02-23
I already had blueman installed, but it always gave the error (and still gives) that bluez-deamon is not started

---

### Post by tlcstat on 2010-02-23
Greetings,
Add the following line to Administration/Software Sources/Other
No key is needed.
[B]ppa:blueman/blueman-dailie

[/B]Run update to ensure that the latest version of Blueman is installed.
Plug-in your adapter and the Blueman control should appear in the top panel.
If not you probably have and unsupport adapter.

tlcstat

---

### Post by Kruptein on 2010-02-24
if I do that, I get an error package not available, but it worked with ppa:blueman/ppa

although after update it still gave me the daemon error :s

---

### Post by tlcstat on 2010-02-24
Greetings,
At this point I would open the Synaptic Package Manager and make sure that the Blueman Graphical interface is installed. Else could be you have an unsupported dongle.
tlcstat

---

### Post by Kruptein on 2010-02-24
I'm talking about blueman actually :f, it was blueman that gave me the daemon error.

but it is definitly something with /etc/init.d/bluetooth

cause I remember the first time I plugged in my dongle it worked and I could transfer files to my gsm,
but after a reboot it didn't anymore

and that's because /etc/init.d/bluetooth status
always gives: bluetooth is not running
how can I solve this?
I already tried multiple times to reinstall everything related with bluetooth but no luck either :(

---

### Post by tlcstat on 2010-02-27
Greetings,
If you have $15 bucks to spare I would still suggest that you get a Trendnet Bluetooth adapter from Walmart. It works perfect in Ubuntu. The IO Gear adapter did the same as yours. It worked to start with and then quit with an error. If I turn the Trendnet off I have to pull it out of the usb port and then plug it back in. Otherwise it does fine.
tlcstat

---

### Post by dragonboss on 2010-02-27
I don't know the exact fix to this problem but the same thing happens with my bluetooth dongle from time to time(actually, its doing it now...) but just fiddle with it,  take it out and put it back then if it does not show or the applet says its off then reboot with it out and put it back in. That usually works for me but i cant be bothered to reboot right now.

---

### Post by Kruptein on 2010-02-28
Tclstat: It does not have something to do with my dongle!

It's /etc/init.d/bluetooth that does not want to start, this should not be something that depends on my dongle.

Can someone give me a copy of that file to be sure mine isn't damaged.
?

---

### Post by tlcstat on 2010-02-28
Here it is!

#! /bin/sh
### BEGIN INIT INFO
# Provides: bluetooth
# Required-Start: $local_fs $syslog $remote_fs dbus
# Required-Stop: $local_fs $syslog $remote_fs
# Default-Start: 2 3 4 5
# Default-Stop: 0 1 6
# Short-Description: Start bluetoothd
### END INIT INFO

. /lib/lsb/init-functions

set -e

case "$1" in
start)
#currently this init script exists only because of what appears to be
#an egg and chicken problem
# bluetoothd normally starts up by udev rules. it needs dbus to function,
# but dbus doesn't start up until after udev finishes triggering
#
if [ ! -f /sbin/udevadm.upgrade ]; then
udevadm trigger --subsystem-match=bluetooth
fi
;;
stop)
pkill -TERM bluetoothd || true
;;
restart|force-reload)
$0 stop
$0 start
;;
status)
status_of_proc "bluetoothd" "bluetooth" && exit 0 || exit $?
;;
*)
N=/etc/init.d/bluetooth
# echo "Usage: $N {start|stop|restart|reload|force-reload|status}" >&2
echo "Usage: $N {start|stop|restart|force-reload|status}" >&2
exit 1
;;
esac

exit 0

---

### Post by Kruptein on 2010-02-28
Thanks,
but it is the same =(

so I really don't see why
/etc/init.d/bluetooth start
does not work :confused:

---

### Post by mark bower on 2010-03-04
You can save a heap of frustration by getting the Belkin F5D7050 USB wireless adapter (on line for about $US 30.  A large number of persons have had success with it.  I can practically guarantee it working for you "out of the box" in Ubuntu 8.10, 9.04 and 9.10.  I have used the F5D7050 with the Ubu versions mentioned and on three different motherboards - with absolutely no problems.  

I purchased the F5D7050 because my PCI wireless adapters require ndiswrapper and my Netgear USB adapter did not work.  Going thru 3 thick plaster walls at my residence to reach the router, the F5D7050 works just fine with a signal strength of about 30/100.    

If you switch to it, please post your success for others to see.

mark

---

### Post by Kruptein on 2010-03-04
> **mark bower said:**
> You can save a heap of frustration by getting the Belkin F5D7050 USB wireless adapter (on line for about $US 30.  A large number of persons have had success with it.  I can practically guarantee it working for you "out of the box" in Ubuntu 8.10, 9.04 and 9.10.  I have used the F5D7050 with the Ubu versions mentioned and on three different motherboards - with absolutely no problems.  

I purchased the F5D7050 because my PCI wireless adapters require ndiswrapper and my Netgear USB adapter did not work.  Going thru 3 thick plaster walls at my residence to reach the router, the F5D7050 works just fine with a signal strength of about 30/100.    

If you switch to it, please post your success for others to see.

mark

1.I think you misunderstood me, I'm talking about bluetooth dongles, not about wireless internet adapters.
2. Even if I buy a bluetooth dongle from the internet, it still won't work if bluetooth does not want to start  or am I wrong in that?

---

### Post by tlcstat on 2010-03-04
Greetings,
Kruptein, you are wrong on that! I have two bluetooth usb adapters. One will start randomly and then not start no matter what I do. The other will start and work perfectly every single time. Neither actually say that they support Linux on the package. The reason I tried the Trendnet adapter is because it was reported as working on the forums. I bought one at Walmart for fifteen dollars and indeed it does work on both my Dell and my Toshiba with Ubuntu Karmic. I learned from my beginning experience with Linux in general that I needed supported devices. I personally think you are using an unsupported device. But thats just my opinion. It is entirely possible that with some future upgrade of the kernel or driver package that your dongle will start working. Thats what happened to me with my bcmwl5 wifi adapter. It wouldn't work in any distro and then a couple of years later it worked with native Linux drivers. I simply upgraded into a solution. In either case this is the joy of Linux. It isn't the fault of Ubuntu, the product developers just don't support linux. I think the Linux developers do a great job of trying to backward engineer drivers for all of the devices that they do. But just remember this is a luxury you are getting from the Linux community and not from the product manufacturer in most cases. To be fair, there are some manufacturers that do support Linux in their products, such as the HP printers. 
tlcstat

---

### Post by Kruptein on 2010-03-04
Okay, if u say so I will believe you, but one last thing: my dongle did work the first time and I was able to transfer files from my pc to my gsm
but from the moment I restarted it didn't work again

---

### Post by tlcstat on 2010-03-04
Greetings,
Kruptein, you are wrong on that! I have two bluetooth usb adapters. One will start randomly and then not start no matter what I do. The other will start and work perfectly every single time. Neither actually say that they support Linux on the package. The reason I tried the Trendnet adapter is because it was reported as working on the forums. I bought one at Walmart for fifteen dollars and indeed it does work on both my Dell and my Toshiba with Ubuntu Karmic. I learned from my beginning experience with Linux in general that I needed supported devices. I personally think you are using an unsupported device. But thats just my opinion. It is entirely possible that with some future upgrade of the kernel or driver package that your dongle will start working. Thats what happened to me with my bcmwl5 wifi adapter. It wouldn't work in any distro and then a couple of years later it worked with native Linux drivers. I simply upgraded into a solution. In either case this is the joy of Linux. It isn't the fault of Ubuntu, the product developers just don't support linux. I think the Linux developers do a great job of trying to backward engineer drivers for all of the devices that they do. But just remember this is a luxury you are getting from the Linux community and not from the product manufacturer in most cases. To be fair, there are some manufacturers that do support Linux in their products, such as the HP printers. 
tlcstat

---

### Post by mark bower on 2010-03-04
Kruptein

I was apparently asleep.  I can only say that the dongles that work for me out of the box (Ubu 8.10 to 9.10) are the Hawking HBTC2, Cirago BTA-6210 and a cheapy called Vakoss (about $US 6).  It is my impression that most dongles should work, but then ticsat has stated it well - no guarantees.  When you get a dongle to work, you might want to visit my post "bluetooth signal strenth".  Didn't get any help in this forum, so sort of worked it out on my own.  

mark

---

### Post by tlcstat on 2010-03-04
Greetings,
Its like this. If a bluetooth adapter used in Windows complies with the Microsoft bluetooth stack built into the system then it will work without drivers. Of course the Microsoft BT stack isn't really all that great so most will want to use the supplied drivers for better functionality. Same with Linux, if the BT adapter is supported by the kernel or built in driver package then it will work but the problem is that if it won't work at the kernel level and no driver support is included with the distro then you are out of luck since most hardware manufacturers don't supply linux drivers. Since the device will surely comply at some level because of an attempt at standardization it may work sporadically but it will be a time consuming headache. 
tlcstat

---

