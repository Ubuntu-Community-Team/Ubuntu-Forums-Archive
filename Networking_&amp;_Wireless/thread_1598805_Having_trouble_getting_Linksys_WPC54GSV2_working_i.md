---
title: "Having trouble getting Linksys WPC54GSV2 working in Meerket"
date: 2010-10-17
forum: Networking &amp; Wireless
---

### Post by rudi246 on 2010-10-17
I'm running Ubuntu 10.10 Maverick on a Toshiba 2435-S255 laptop with a WPC54GSV2 PCMIA wireless-g adapter. I have ndiswrapper installed, and installed the driver (I know it works because it's the same driver I used with Win XP). When I type sudo ndiswrapper -l it tells me this:```
lsbcmnds : driver installed
      device (14E4:4318) present (alternate driver: ssb)
```I think I am supposed to blacklist something but I don't know what. I added b43 to blacklist.conf and that just took away the wireless connections in the network connections. In the Device Manager under CardBus Bridge it has Network Controller and info.linux.driver's string is ndiswrapper. I wanted to uninstall the driver to see what the Device Manager would show but I don't know the name of the driver. I did sudo ndiswrapper -r 14E4:4318 and it just said there was no driver by that name. So after all of that, that leaves me here. Please help an Ubuntu noob out!

---

### Post by chili555 on 2010-10-17
> I did sudo ndiswrapper -r 14E4:4318What are you trying to do? Are you trying to get the native driver b43 working or ndiswrapper working? Or nothing working?

This is telling you that *ssb* is probably conflicting with ndiswrapper:> alternate driver: ssbYou can stop it by blacklisting it. However, many computers also have a Broadcom ethernet card that also requires *ssb*, so that may not be ideal.

If it were me, I'd get the native driver going by downloading and installing the firmware. Do you have an ethernet connection available? What does System > Administration > Additional Drivers say?

The ndiswrapper driver is:> [COLOR="Red"]lsbcmnds[/COLOR] : driver installed
      device (14E4:4318) present (alternate driver: ssb)

---

### Post by rudi246 on 2010-10-17
I am trying to get ndiswrapper working. I have the same driver I used in Windows XP. When I click the network icon it shows under wireless networks: device not ready (firmware missing).

I do not have an ethernet connection available, I just download what I need on my other computer and transfer files with a usb disk.

Additional drivers tells me there are no proprietary drivers in use on my system.

The problem I think is, I was following a tutorial that said to find the default driver with the device manager and blacklist that driver before installing the Windows one, but I said the hell with it because I didn't have device manager so I just went and installed the driver. Now I have device manager to see what's going on and under CardBus Bridge it shows Network Controller and under that there are a bunch of blue icons with question marks. The first one says subsystem: ssb and there are more under that. Three of those say subsystem: leds, one says WLAN Interface, and the last one says phy0 wlan Killswitch.

Would it be easier to uninstall then reinstall the driver after blacklisting the other one?

---

### Post by chili555 on 2010-10-17
Let's edit the blacklist file:```
sudo gedit /etc/modprobe.d/blacklist.conf
```Make sure it has these lines:```
blacklist b43
blacklist ssb
```Proofread, save and close gedit. Now let's make sure the modules are unloaded and load ndiswrapper:```
sudo rmmod -f b43 ssb
sudo modprobe ndiswrapper
iwconfig
```Now do you have a wireless interface, wlan0 perhaps?

---

### Post by rudi246 on 2010-10-17
for sudo rmmod -f b43 ssb I get, "No such file or directory."

and for iwconfig I get:

lo       no wireless extensioins
eth0   no wireless extensions
irda0  no wireless extensions

---

### Post by chili555 on 2010-10-17
Please let me see:```
dmesg | grep ndis
```You may have to transfer it on a USB key or similar.

---

### Post by rudi246 on 2010-10-17
This is what that gave me:

[   20.852784] ndiswrapper version 1.56 loaded (smp=yes, preempt=no)
[   21.426968] usbcore: registered new interface driver ndiswrapper
[   21.964615] ndiswrapper (load_wrap_driver:108): couldn't load driver lsbcmnds; check system log for messages from 'loadndisdriver'


edit: not sure why that smily is there. lol. must be tha code

---

### Post by chili555 on 2010-10-17
Let's do as it suggests; check the syslog:```
sudo cat /var/log/syslog | grep ndis
```Did you load a .sys file in addition to the .inf?

---

### Post by rudi246 on 2010-10-17
I don't know if it loaded a .sys or .inf but it gave me this whole mess of crap:

```
Oct 16 18:57:09 dickanus &#65279;<30>AptDaemon: INFO: InstallFile() was called: /media/ATTACH/Linksys WPC54GSV2/ndiswrapper-utils-1.9_1.56-3_i386.deb
Oct 16 18:57:14 dickanus &#65279;<30>AptDaemon.Worker: INFO: Installing local package file: /media/ATTACH/Linksys WPC54GSV2/ndiswrapper-utils-1.9_1.56-3_i386.deb
Oct 16 23:29:09 dickanus kernel: [   20.785822] ndiswrapper version 1.56 loaded (smp=yes, preempt=no)
Oct 16 23:29:09 dickanus kernel: [   21.241550] usbcore: registered new interface driver ndiswrapper
Oct 16 23:29:09 dickanus loadndisdriver: loadndisdriver: load_driver(325): too many .sys files for driver lsbcmnds
Oct 16 23:29:09 dickanus kernel: [   21.696830] ndiswrapper (load_wrap_driver:108): couldn't load driver lsbcmnds; check system log for messages from 'loadndisdriver'
Oct 16 23:29:09 dickanus loadndisdriver: loadndisdriver: load_driver(358): couldn't load driver lsbcmnds
Oct 16 23:34:27 dickanus kernel: [  339.349079] usbcore: deregistering interface driver ndiswrapper
Oct 16 23:34:34 dickanus kernel: [  346.690104] ndiswrapper version 1.56 loaded (smp=yes, preempt=no)
Oct 16 23:34:34 dickanus loadndisdriver: loadndisdriver: load_driver(325): too many .sys files for driver lsbcmnds
Oct 16 23:34:34 dickanus loadndisdriver: loadndisdriver: load_driver(358): couldn't load driver lsbcmnds
Oct 16 23:34:34 dickanus kernel: [  346.710688] ndiswrapper (load_wrap_driver:108): couldn't load driver lsbcmnds; check system log for messages from 'loadndisdriver'
Oct 16 23:34:34 dickanus kernel: [  346.710791] usbcore: registered new interface driver ndiswrapper
Oct 16 23:45:24 dickanus loadndisdriver: loadndisdriver: load_driver(325): too many .sys files for driver lsbcmnds
Oct 16 23:45:24 dickanus loadndisdriver: loadndisdriver: load_driver(358): couldn't load driver lsbcmnds
Oct 16 23:45:24 dickanus kernel: [  996.447506] ndiswrapper (load_wrap_driver:108): couldn't load driver lsbcmnds; check system log for messages from 'loadndisdriver'
Oct 16 23:47:19 dickanus kernel: [ 1111.009229] usbcore: deregistering interface driver ndiswrapper
Oct 16 23:47:34 dickanus kernel: [ 1126.558620] ndiswrapper version 1.56 loaded (smp=yes, preempt=no)
Oct 16 23:47:34 dickanus kernel: [ 1126.645214] usbcore: registered new interface driver ndiswrapper
Oct 17 00:44:41 dickanus kernel: [ 4553.000204] usbcore: deregistering interface driver ndiswrapper
Oct 17 00:44:53 dickanus kernel: [ 4565.691471] ndiswrapper version 1.56 loaded (smp=yes, preempt=no)
Oct 17 00:44:53 dickanus kernel: [ 4565.734508] usbcore: registered new interface driver ndiswrapper
Oct 17 01:03:58 dickanus kernel: [   20.685361] ndiswrapper version 1.56 loaded (smp=yes, preempt=no)
Oct 17 01:03:58 dickanus kernel: [   21.277464] usbcore: registered new interface driver ndiswrapper
Oct 17 01:03:58 dickanus loadndisdriver: loadndisdriver: load_driver(325): too many .sys files for driver lsbcmnds
Oct 17 01:03:58 dickanus kernel: [   21.789894] ndiswrapper (load_wrap_driver:108): couldn't load driver lsbcmnds; check system log for messages from 'loadndisdriver'
Oct 17 01:03:58 dickanus loadndisdriver: loadndisdriver: load_driver(358): couldn't load driver lsbcmnds
Oct 17 01:12:01 dickanus loadndisdriver: loadndisdriver: load_driver(325): too many .sys files for driver lsbcmnds
Oct 17 01:12:01 dickanus loadndisdriver: loadndisdriver: load_driver(358): couldn't load driver lsbcmnds
Oct 17 01:12:01 dickanus kernel: [  504.164760] ndiswrapper (load_wrap_driver:108): couldn't load driver lsbcmnds; check system log for messages from 'loadndisdriver'
Oct 17 01:39:24 dickanus kernel: [   20.922774] ndiswrapper version 1.56 loaded (smp=yes, preempt=no)
Oct 17 01:39:24 dickanus kernel: [   21.422599] usbcore: registered new interface driver ndiswrapper
Oct 17 01:39:24 dickanus loadndisdriver: loadndisdriver: load_driver(325): too many .sys files for driver lsbcmnds
Oct 17 01:39:24 dickanus kernel: [   21.924914] ndiswrapper (load_wrap_driver:108): couldn't load driver lsbcmnds; check system log for messages from 'loadndisdriver'
Oct 17 01:39:24 dickanus loadndisdriver: loadndisdriver: load_driver(358): couldn't load driver lsbcmnds
Oct 17 01:47:09 dickanus kernel: [   20.821496] ndiswrapper version 1.56 loaded (smp=yes, preempt=no)
Oct 17 01:47:09 dickanus kernel: [   21.349063] usbcore: registered new interface driver ndiswrapper
Oct 17 01:47:09 dickanus loadndisdriver: loadndisdriver: load_driver(325): too many .sys files for driver lsbcmnds
Oct 17 01:47:09 dickanus loadndisdriver: loadndisdriver: load_driver(358): couldn't load driver lsbcmnds
Oct 17 01:47:09 dickanus kernel: [   21.770358] ndiswrapper (load_wrap_driver:108): couldn't load driver lsbcmnds; check system log for messages from 'loadndisdriver'
Oct 17 01:48:18 dickanus loadndisdriver: loadndisdriver: load_driver(325): too many .sys files for driver lsbcmnds
Oct 17 01:48:18 dickanus loadndisdriver: loadndisdriver: load_driver(358): couldn't load driver lsbcmnds
Oct 17 01:48:18 dickanus kernel: [   90.845040] ndiswrapper (load_wrap_driver:108): couldn't load driver lsbcmnds; check system log for messages from 'loadndisdriver'
Oct 17 16:32:00 dickanus kernel: [   20.684778] ndiswrapper version 1.56 loaded (smp=yes, preempt=no)
Oct 17 16:32:00 dickanus kernel: [   21.335776] usbcore: registered new interface driver ndiswrapper
Oct 17 16:32:00 dickanus loadndisdriver: loadndisdriver: load_driver(325): too many .sys files for driver lsbcmnds
Oct 17 16:32:00 dickanus loadndisdriver: loadndisdriver: load_driver(358): couldn't load driver lsbcmnds
Oct 17 16:32:00 dickanus kernel: [   21.885603] ndiswrapper (load_wrap_driver:108): couldn't load driver lsbcmnds; check system log for messages from 'loadndisdriver'
Oct 17 16:52:34 dickanus loadndisdriver: loadndisdriver: load_driver(325): too many .sys files for driver lsbcmnds
Oct 17 16:52:34 dickanus loadndisdriver: loadndisdriver: load_driver(358): couldn't load driver lsbcmnds
Oct 17 16:52:34 dickanus kernel: [ 1255.277074] ndiswrapper (load_wrap_driver:108): couldn't load driver lsbcmnds; check system log for messages from 'loadndisdriver'
Oct 17 16:58:00 dickanus kernel: [   20.765551] ndiswrapper version 1.56 loaded (smp=yes, preempt=no)
Oct 17 16:58:00 dickanus kernel: [   21.255279] usbcore: registered new interface driver ndiswrapper
Oct 17 16:58:00 dickanus loadndisdriver: loadndisdriver: load_driver(325): too many .sys files for driver lsbcmnds
Oct 17 16:58:00 dickanus kernel: [   21.767943] ndiswrapper (load_wrap_driver:108): couldn't load driver lsbcmnds; check system log for messages from 'loadndisdriver'
Oct 17 16:58:00 dickanus loadndisdriver: loadndisdriver: load_driver(358): couldn't load driver lsbcmnds
Oct 17 18:02:14 dickanus kernel: [   21.945342] ndiswrapper version 1.56 loaded (smp=yes, preempt=no)
Oct 17 18:02:14 dickanus kernel: [   22.603056] usbcore: registered new interface driver ndiswrapper
Oct 17 18:02:15 dickanus loadndisdriver: loadndisdriver: load_driver(325): too many .sys files for driver lsbcmnds
Oct 17 18:02:15 dickanus kernel: [   23.091539] ndiswrapper (load_wrap_driver:108): couldn't load driver lsbcmnds; check system log for messages from 'loadndisdriver'
Oct 17 18:02:15 dickanus loadndisdriver: loadndisdriver: load_driver(358): couldn't load driver lsbcmnds
Oct 17 20:19:12 dickanus kernel: [   20.852784] ndiswrapper version 1.56 loaded (smp=yes, preempt=no)
Oct 17 20:19:12 dickanus kernel: [   21.426968] usbcore: registered new interface driver ndiswrapper
Oct 17 20:19:12 dickanus loadndisdriver: loadndisdriver: load_driver(325): too many .sys files for driver lsbcmnds
Oct 17 20:19:13 dickanus loadndisdriver: loadndisdriver: load_driver(358): couldn't load driver lsbcmnds
Oct 17 20:19:13 dickanus kernel: [   21.964615] ndiswrapper (load_wrap_driver:108): couldn't load driver lsbcmnds; check system log for messages from 'loadndisdriver'
Oct 17 22:00:30 dickanus kernel: [   20.853147] ndiswrapper version 1.56 loaded (smp=yes, preempt=no)
Oct 17 22:00:30 dickanus kernel: [   21.450914] usbcore: registered new interface driver ndiswrapper
Oct 17 22:00:31 dickanus loadndisdriver: loadndisdriver: load_driver(325): too many .sys files for driver lsbcmnds
Oct 17 22:00:31 dickanus loadndisdriver: loadndisdriver: load_driver(358): couldn't load driver lsbcmnds
Oct 17 22:00:31 dickanus kernel: [   21.976373] ndiswrapper (load_wrap_driver:108): couldn't load driver lsbcmnds; check system log for messages from 'loadndisdriver'
Oct 17 22:07:42 dickanus kernel: [   20.771904] ndiswrapper version 1.56 loaded (smp=yes, preempt=no)
Oct 17 22:07:42 dickanus kernel: [   21.410252] usbcore: registered new interface driver ndiswrapper

```...and yes the computer's name is daickanus

---

### Post by chili555 on 2010-10-17
```
too many .sys files for driver lsbcmnds
```It looks like you did load a .sys file; or two or three!

Please do:```
ls /etc/ndiswrapper/lsbcmnds
```You will probably find several .sys files. I hope one of them is named wpc54gsv2.sys. If so, we will rename the others:```
cd /etc/ndiswrapper/lsbcmnds
sudo mv whatever.sys whatever.sys.bak
```Continue through all the wrong files leaving only the file that seems to apply to your device.

Reboot and let us have a good report. I will check in tomorrow.

Please see [http://newyork.ubuntuforums.org/showpost.php?p=6233873&postcount=14](http://newyork.ubuntuforums.org/showpost.php?p=6233873&postcount=14)
.

---

### Post by rudi246 on 2010-10-17
Awesome! Thanks a lot, man. I do all of my ebay stuff on my laptop and just got rid of Windows XP because it was really slow. You are a life saver... kind of!

---

### Post by rudi246 on 2010-10-18
Hey, thanks a lot, man! That saved me a lot of trouble. The funny thing is I posted the same thread on linuxquestions.org and I got a completely different response that wasn't near as helpful. He said to uninstall the ndiswrapper driver, blacklist b43legacy and use b43. But anyway, thanks again!

edit: I didn't realize the above post went on the second page sorry for the double post

---

### Post by chili555 on 2010-10-18
Glad it's working! Have fun.

---

