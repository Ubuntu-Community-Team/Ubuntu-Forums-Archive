---
title: "Further Problems: d-link DWA-125"
date: 2010-03-17
forum: Networking &amp; Wireless
---

### Post by Turbo_2 on 2010-03-17
Alright: 
lsmod | grep -e rt2 -e rt3
rt2870sta             547324  0 
rt2800usb              37372  0 
rt2x00usb              11548  1 rt2800usb
rt2x00lib              29756  2 rt2800usb,rt2x00usb
led_class               4096  1 rt2x00lib
input_polldev           3716  1 rt2x00lib
mac80211              181140  2 rt2x00usb,rt2x00lib
cfg80211               93052  2 rt2x00lib,mac80211
crc_ccitt               1852  1 rt2800usb

then I tried sudo modprobe rt2800usb and ran iwconfig
lo no wireless extensions.
eth0 no wireless extensions.
and wlan1 is there only when the adaptor is plugged in. no signal, not-associated

---

### Post by chili555 on 2010-03-17
Did your search not find this?

[http://ubuntuforums.org/showthread.php?t=1425564&page=4&highlight=dwa-125](http://ubuntuforums.org/showthread.php?t=1425564&page=4&highlight=dwa-125)

Please see and follow post #37. If you have not downloaded and compiled a driver, you can omit this part:> Uninstall any drivers you compiled from source:
Code:

cd Desktop/2009_RTL3070etc.

Change to the directory of whatever file you compiled.
Code:

sudo make uninstall

Post back if you get stuck.

---

### Post by Turbo_2 on 2010-03-17
I have downloaded and installed both the rt2870 driver and the 3070...I'm just confused that I'm supposed to uninstall those, then sudo modprobe rt3070sta
every time I try that I get FATAL: module rt3070sta not found

---

### Post by chili555 on 2010-03-18
What does this tell you your device is?```
lsusb
```Thanks.

---

### Post by Turbo_2 on 2010-03-18
lsusb tells me
07d1:3c0d D-link System

now iwconfig tells me 
lo no wireless extensions

eth0 no wireless extensions 

then ls /etc/Wireless 
RT2870STA RT3070STA

Also, on my own I ran ifconfig ra0 up
and then:  iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ra0       Ralink STA  ESSID:""  Nickname:"RT2870STA"
          Mode:Auto  Frequency=2.412 GHz  Bit Rate=1 Mb/s   
          RTS thr: off   Fragment thr: off
          Link Quality=10/100  Signal level:0 dBm  Noise level:-97 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by chili555 on 2010-03-18
This is exactly what you need to do:

[http://ubuntuforums.org/showpost.php?p=8966294&postcount=37](http://ubuntuforums.org/showpost.php?p=8966294&postcount=37)

Please post back if you get stuck.

---

### Post by Turbo_2 on 2010-03-18
sudo modprobe rt3070sta
FATAL: Module rt3070sta not found.

---

### Post by chili555 on 2010-03-18
Please post:```
sudo updatedb
locate 3070 | grep .ko
cat /etc/udev/rules.d/network_drivers.rules
```Thanks.

---

### Post by Turbo_2 on 2010-03-18
aren@aren-desktop:~$ sudo updatedb
[sudo] password for aren: 
aren@aren-desktop:~$ locate 3070 | grep .ko
/home/aren/RT3070_LinuxSTA_V2.3.0.1_20100208/os/linux/.rt3070sta.ko.cmd
/home/aren/RT3070_LinuxSTA_V2.3.0.1_20100208/os/linux/rt3070sta.ko
/lib/modules/2.6.31-14-generic/kernel/drivers/staging/rt3070/rt3070sta.ko
aren@aren-desktop:~$ cat /etc/udev/rules.d/network_drivers.rules
ACTION=="add", SUBSYSTEM=="usb", ATTR{idVendor}=="07d1", ATTR{idProduct}=="3c0d", RUN+="/sbin/modprobe -qba rt3070sta"

---

### Post by chili555 on 2010-03-18
Let's try to load it explicitly:```
sudo modprobe /lib/modules/2.6.31-14-generic/kernel/drivers/staging/rt3070/rt3070sta.ko
```If that doesn't work, post the error and reboot. Let me know if there is any improvement.

---

### Post by Turbo_2 on 2010-03-18
FATAL: Module /lib/modules/2.6.31-14-generic/kernel/drivers/staging/rt3070/rt3070sta.ko not found.

on reboot...network manager does not see wireless connection as an option 
iwconfig
lo no wireless extensions
eth0 no wireless extensions

---

### Post by chili555 on 2010-03-18
Please do:```
sudo apt-get install --reinstall linux-image-`uname -r`
sudo modprobe rt3070sta
```Those tickmarks are on the same key with ~ on my US keyboard. Any errors?

---

### Post by Turbo_2 on 2010-03-18
aren@aren-desktop:~$ sudo apt-get install --reinstall linux-image-`uname -r`
[sudo] password for aren: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.31-14 linux-headers-2.6.31-14-generic
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 11 not upgraded.
Need to get 28.8MB of archives.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main linux-image-2.6.31-19-generic 2.6.31-19.56
  Could not resolve 'us.archive.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main linux-image-2.6.31-19-generic 2.6.31-19.56
  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-image-2.6.31-19-generic_2.6.31-19.56_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-image-2.6.31-19-generic_2.6.31-19.56_i386.deb)  Could not resolve 'security.ubuntu.com'
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
aren@aren-desktop:~$ sudo modprobe rt3070sta
FATAL: Module rt3070sta not found.

---

### Post by chili555 on 2010-03-18
> Could not resolve 'us.archive.ubuntu.com'Do you not have an ethernet connection? You need to be connected to the internet for this to work correctly.

---

### Post by Turbo_2 on 2010-03-18
Hmmm...this will take a minute...but I can get it done.  Will post back with results in half hour...I have to move my computer into the living room.

---

### Post by chili555 on 2010-03-18
This is wierd. You are running:> linux-image-2.6.31-[COLOR="Red"]19[/COLOR]-genericHowever, when we serached for rt3070sta, all we found was:> /lib/modules/2.6.31-[COLOR="Red"]14[/COLOR]-generic/kernel/drivers/staging/rt3070/rt3070sta.koVery strange.

---

### Post by Turbo_2 on 2010-03-18
FATAL: Error inserting rt3070sta (/lib/modules/2.6.31-19-generic/kernel/drivers/staging/rt3070/rt3070sta.ko): Device or Resource Busy

Yes, this all seems slightly out of place to me...I wonder if I did something really wrong when I started trying to figure this out

---

### Post by chili555 on 2010-03-18
> Device or Resource BusyAh, ha! It may already be inserted! Please check with:```
lsmod | grep rt3
```If it is there, we are making good progress. Please look at:```
iwconfig
```If you have an interface, ra0 or wlan0, please detach the wire and try to connect.

---

### Post by Turbo_2 on 2010-03-18
aren@aren-desktop:~$ lsmod | grep rt3
aren@aren-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ra0       Ralink STA  
          
rt3070sta isn't there...ra0 is...I can get it active if I iwconfig ra0 up but haven't done so yet

---

### Post by chili555 on 2010-03-18
> ra0 Ralink STAI wonder what is driving this thing! Let's see:```
lsmod | grep rt2
```If you get nothing, please post:```
lsmod
```I need about three aspirins.

---

### Post by Turbo_2 on 2010-03-18
aren@aren-desktop:~$ lsmod | grep rt2
rt2870sta             547324  0

---

### Post by chili555 on 2010-03-18
> rt2870sta 547324 0Did you also build rt2870sta from a .tar.bz2 file? If so, we need to uninstall it, too, like this:> Uninstall any drivers you compiled from source:
Code:

cd Desktop/RTL2870etc.

Change to the directory of whatever file you compiled.
Code:

sudo make uninstallThat is only the approximate procedure; I don't know the exact place you downloaded the file, nor the exact name of the file.

Also, is it getting explicitly loaded?```
cat /etc/modules
```We are getting closer!

---

### Post by Turbo_2 on 2010-03-18
looks like it:
aren@aren-desktop:~$ cat /etc/modules
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
rt2870sta

not sure what I should replace rt2870sta with though

---

### Post by chili555 on 2010-03-18
Please change it to:> # /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
rt3070staIf you did the process to uninstall rt2870sta from the file you downloaded, then reboot and give us a good report, please.

---

### Post by Turbo_2 on 2010-03-18
SUCCESS
wifi is working...detecting many wireless networks. only my password doesn't work now...stupid thing won't connect to it.  So frusterating

Quick question though.  How did you find out the dwa-125 was the 3070 chipset in the first place?

---

### Post by chili555 on 2010-03-18
> Quick question though. How did you find out the dwa-125 was the 3070 chipset in the first place?I googled the usb.id numbers. It also is claimed, but doesn't actually work with RT2800usb. Getting it all sorted out and working was a maddening, long process that challenged every geek fiber in my body. With the help of a few other posts and a few "duh" moments on my part, it works!

I am very glad it's working for you. Enjoy!

---

