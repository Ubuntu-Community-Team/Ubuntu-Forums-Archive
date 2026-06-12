---
title: "Problem with Reliance Netconnect LG LXU-800 USB Modem"
date: 2009-07-27
forum: Networking &amp; Wireless
---

### Post by KushKashyap on 2009-07-27
Hello there,

My problem is that i just cant get my CDMA 1X LG LXU-800 USB modem to connect to the internet. 
I have been checking numerous websites, blogs and forums to get it sorted. Have tried every thing from wvdial, pppconfig, in built Network Manager and what not. But the results have been very very diasappointing.
 
First of all i try to install according to their user manual and i get this
 
root@kush-laptop:~/bin# bash setup.sh
FATAL: Error inserting LXU800Mdm (/lib/modules/2.6.28-11-generic/kernel/drivers/usb/LXU800Mdm.ko): Invalid module format
Kernel Modules are loaded.
 
and then i get following results with the following commands
 
root@kush-laptop:~# lsusb

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 005: ID 04b3:310b IBM Corp. Red Wheel Mouse
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 009: ID 0eab:9357  
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
 
 
root@kush-laptop:~# modprobe usbserial vendor=0xeab product=0x9357
FATAL: Module usbserial not found.
 
 
root@kush-laptop:~# dmesg
[ 1913.704103] usb 5-1: new full speed USB device using uhci_hcd and address 2
[ 1913.824091] usb 5-1: device descriptor read/64, error -71
[ 1914.104079] usb 5-1: device descriptor read/64, error -71
[ 1914.320089] usb 5-1: new full speed USB device using uhci_hcd and address 3
[ 1914.444103] hub 5-0:1.0: unable to enumerate USB device on port 1
[ 1915.216081] usb 5-1: new full speed USB device using uhci_hcd and address 4
[ 1915.434758] usb 5-1: configuration #1 chosen from 1 choice
[ 1915.446928] LXU800Mdm: disagrees about version of symbol struct_module
[ 1915.461789] LXU800Mdm: disagrees about version of symbol struct_module
[ 1915.475847] LXU800Mdm: disagrees about version of symbol struct_module
 
 
 
This is my wvdialconf [i checked it from [https://help.ubuntu.com/community/DialupModemHowto/LXU800](https://help.ubuntu.com/community/DialupModemHowto/LXU800)]
 
[Dialer Defaults]
Init1 = AT
Init2 = ATE0V1
Modem Type = Analog Modem
Baud = 115200
New PPPD = yes
Modem = /dev/ttyUSB0
ISDN = 0
Phone = "#777"
Password = <mypassword>
Username = <mynumber>
 
 
root@kush-laptop:~# wvdial
--> WvDial: Internet dialer version 1.60
--> Cannot open /dev/ttyUSB0: No such file or directory
--> Cannot open /dev/ttyUSB0: No such file or directory
--> Cannot open /dev/ttyUSB0: No such file or directory
 
I checked there is nothing like ttyUSB0 , but there is also nothing else..
 
So this is what my situation is, i am using Ubuntu 9.04 from my Dual boot  laptop and this USB Modem is my only source of internet connection.. So i cant do "apt-get" kind of thing also. Some people have got it working, but dont know how([http://ninadpundalik.co.cc/blog/2009/05/lg-lxu800-dialer-on-ubuntu-jaunty/](http://ninadpundalik.co.cc/blog/2009/05/lg-lxu800-dialer-on-ubuntu-jaunty/)) .
 
Please help me out..:confused:
I am stuck with it for 3 weeks now..and honestly i am feeling a bit let down with this otherwise wonderful OS...

---

### Post by GeorgeVita on 2009-07-28
Hi **KushKashyap**,
as this modem is your only possible connection to the internet (on the Ubuntu running PC) and you have the original Ubuntu 9.04 liveCD which has the **usbserial driver encapsulated into kernel**, you must first try those stated on:
[http://ubuntuforums.org/showpost.php?p=7455154&postcount=4](http://ubuntuforums.org/showpost.php?p=7455154&postcount=4)

This will solve:> root@kush-laptop:~# modprobe usbserial vendor=0xeab product=0x9357
FATAL: Module usbserial not found.

> **Pete Graner**:
"As a short term workaround until we can get it added pls try and report back with:
Built in modules can have module params passed on the kernel command line: can you try booting with:

usbserial.vendor=**0x0eab** usbserial.product=**0x9357**

You will need to press ESC during to grub pause upon restart/power on.
Arrow down to the kernel you wish to boot.
press "e" (for edit)
Arrow down to the 2nd line (the command line)
Press Enter to begin editing
Arrow to the end of the line and add:
usbserial.vendor=**0x0eab** usbserial.product=**0x9357**
When done press enter. Then press "b" to boot"

You have to '**extend**' the line with all parameters ending to '...quiet splash'
and make it '...quiet splash usbserial.vendor=0x0eab usbserial.product=0x9357'

I placed you modem's VendorID & productID.

If you get the serial-communication ports (/dev/tty...) you can proceed to the next step.

Regards,
George

---

### Post by KushKashyap on 2009-07-29
Thanks a lot [GeorgeVita]("http://ubuntuforums.org/member.php?u=638001"), I did exactly what you had told me to do at the booting time ... Now i had ttyUSB0 ... but for this do i have to type that line everytime i boot, because the next time they disaapeared.
Anyways i tried wvdial and the following things happened.

Carrier detected.  Waiting for prompt.
--> Connected, but carrier signal lost!  Retrying...



--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: AT
OK
--> Sending: ATE0V1
OK
--> Modem initialized.
--> Sending: ATDT#777
--> Waiting for carrier.
CONNECT
--> Carrier detected.  Waiting for prompt.
--> Connected, but carrier signal lost!  Retrying...
--> Sending: ATDT#777
--> Waiting for carrier.

But my connection is running absolutely fine on my Windows OS... I also double checked my UserName and Password

I also did modprobe but that resulred in a fatal Module error. Thanks a lot

---

### Post by GeorgeVita on 2009-07-29
Hi **KushKashyap**,
at this initial state it is better to add it at boot time, later after the connection you will do a full update from System > Administration > Update Manager which will restore the **usbserial** driver.

To connect try:```
sudo gedit /etc/wvdial.conf
``` and make it:```

[Dialer Defaults]
Init1 = ATZ
Init2 = ATE0V1
Stupid Mode = Yes
Modem Type = Analog Modem
Baud = 115200
New PPPD = yes
Modem = /dev/ttyUSB0
ISDN = 0
Phone = "#777"
Password = <mypassword>
Username = <mynumber>

```
Init1 changed to ATZ and 'Stupid mode = Yes' added to skip 'prompt at login'.

Post results to continue.

Regards,
George

---

### Post by KushKashyap on 2009-07-29
Thanks a lot [GeorgeVita]("http://ubuntuforums.org/member.php?u=638001"), with your efforts i am writing this post from my Ubuntu :-) 
Your changes worked like a charm.. 
Thanks a lot...

---

### Post by nikeldev on 2009-08-02
is this configuration will work on my Reliance LG 6600 cdma mobile ?

---

### Post by KushKashyap on 2009-08-02
> **nikeldev said:**
> is this configuration will work on my Reliance LG 6600 cdma mobile ?

What configuration wvdial?? Yes i think so... but plz check what is the number to be dialed... is it same #777; or *99# or *99***# as in other mobiles when using Dial Up

---

### Post by ninadsp on 2009-08-04
> **KushKashyap said:**
> Thanks a lot [GeorgeVita]("http://ubuntuforums.org/member.php?u=638001"), with your efforts i am writing this post from my Ubuntu :-) 
Your changes worked like a charm.. 
Thanks a lot...

Thanx both you guys for the wvdial settings.  I had been using that dialer with pppd for all these days(as i've noted in my post).  Will give wvdial a try when i get my hands on the dialer again. :)

---

### Post by Abhinav K Sahdev on 2009-08-19
i m having the same problems with mu zte mg880 usb reliance data card. also that i have tried all the other methods(i've been googling for 2 weeks now).there dosen't seem to be a ttyUSb port anywhere. mine is ubuntu 9.04 dual boot with windows xp. should i use the same method written up here.  kindly resolve my problem.

---

### Post by GeorgeVita on 2009-08-19
Hi **Abhinav K Sahdev**, please do some basic tests:

- boot without the modem
- wait for the system to load
- attach modem, wait 15 seconds
- open a terminal window (Applications > Accessories > Terminal)
- try```
dmesg
```
- copy here ONLY the LAST 10-15 lines of **dmesg** possibly shown system activity regarding your modem
- try```
lsusb
```
- copy here the output of **lsusb** to see actual vendorID : productID

Regards,
George

---

### Post by Abhinav K Sahdev on 2009-09-05
this is the result of dmesg
[   31.701285] input: b43-phy0 as /devices/virtual/input/input9
[   31.752118] b43 ssb0:0: firmware: requesting b43/ucode5.fw
[   31.755002] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[   31.755010] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the latest firmware (version 4).
[   76.394372] [drm:i915_getparam] *ERROR* Unknown parameter 6
[   80.957641] CPU0 attaching NULL sched-domain.
[   80.957742] CPU0 attaching NULL sched-domain.
[  212.688102] usb 3-2: USB disconnect, address 2
[  218.544047] usb 3-2: new full speed USB device using uhci_hcd and address 3
[  218.720047] usb 3-2: device descriptor read/64, error -71
[  218.944045] usb 3-2: device descriptor read/64, error -71
[  219.216048] usb 3-2: new full speed USB device using uhci_hcd and address 4
[  219.392042] usb 3-2: device descriptor read/64, error -71
[  219.616059] usb 3-2: device descriptor read/64, error -71
[  219.776087] hub 3-0:1.0: unable to enumerate USB device on port 2
[  220.256052] hub 3-0:1.0: unable to enumerate USB device on port 2
[  220.736046] usb 3-2: new full speed USB device using uhci_hcd and address 7
[  221.040610] usb 3-2: configuration #1 chosen from 1 choice





this is the result of lsusb

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 007: ID 19d2:fffd  
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

---

### Post by Abhinav K Sahdev on 2009-09-06
hi 
i have tried all you wrote u there
and after that when i ran the command
sudo wvdial in terminal this was the result.i need assistance.

--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATE0V1
ATE0V1
OK
--> Modem initialized.
--> Sending: ATDT#777
--> Waiting for carrier.
CONNECT
--> Carrier detected.  Starting PPP immediately.
--> Starting pppd at Sun Sep  6 16:56:20 2009
--> Pid of pppd: 4197
--> Using interface ppp0
--> pppd: &#65533;g&#65533;[08]he&#65533;[08]
--> pppd: &#65533;g&#65533;[08]he&#65533;[08]
--> pppd: &#65533;g&#65533;[08]he&#65533;[08]
--> pppd: &#65533;g&#65533;[08]he&#65533;[08]
--> Disconnecting at Sun Sep  6 16:56:25 2009
--> The PPP daemon has died: Authentication error.
--> We failed to authenticate ourselves to the peer.
--> Maybe bad account or password? (exit code = 19)
--> man pppd explains pppd error codes in more detail.
--> I guess that's it for now, exiting
--> The PPP daemon has died. (exit code = 19)

---

### Post by GeorgeVita on 2009-09-06
Hi **Abhinav K Sahdev**,
if you are trying to connect using:```
sudo wvdial
``` then the problem may be wrong APN and/or username/password.

Post here your /etc/wvdial.conf file and Country/Provider to check above data.

Regards,
George

---

### Post by Abhinav K Sahdev on 2009-09-06
hey
its working now. thanks for all the support.(m writin from ubuntu) 
i think the wvdialer had some problem but when i used ppp commands it started working.
thanks alot to you for all of that stuff above.

---

### Post by vikaskumargdra on 2009-09-18
> **GeorgeVita said:**
> Hi **KushKashyap**,
at this initial state it is better to add it at boot time, later after the connection you will do a full update from System > Administration > Update Manager which will restore the **usbserial** driver.

To connect try:```
sudo gedit /etc/wvdial.conf
``` and make it:```

[Dialer Defaults]
Init1 = ATZ
Init2 = ATE0V1
Stupid Mode = Yes
Modem Type = Analog Modem
Baud = 115200
New PPPD = yes
Modem = /dev/ttyUSB0
ISDN = 0
Phone = "#777"
Password = <mypassword>
Username = <mynumber>

```
Init1 changed to ATZ and 'Stupid mode = Yes' added to skip 'prompt at login'.

Post results to continue.

Regards,
George


Hi! George.I've just purchased LXU 800 modem & I done it as described in this thread & as u told.But when i tried to run the command 'sudo wvdial',it says 'command not found' & 'wvdial' ,it says 'wvdial is not installed' and the same as above'command not found'.
Please help me.

---

### Post by GeorgeVita on 2009-09-18
Hi **vikaskumargdra**, welcome to this forum!
To get **wvdial** working you need 5 .deb files (download and install).
If you have a working connection to the Ubuntu running pc, use System > Preferences > Synaptic to get it OR from terminal: ```
sudo apt-get install wvdial
```
If you are offline, follow [instructions]("http://ubuntuforums.org/showthread.php?p=7245790#post7245790")
It is better  to use files made for your Ubuntu version and CPU architecture. If you have Ubuntu 9.04 running on 32 bit Intel get [my zip file]("http://acomelectronics.com/GeorgeVita/wvdial_904_i386.zip") unzip it on desktop and double click on each .deb icon in the following manner:

1. libxplc0.3.13
2. libwvstreams4.4-base
3. libwvstreams4.4-extras
4. libuniconf4.4
5. wvdial

If you have any problem/question post it to follow up.

Regards,
George

---

### Post by vikaskumargdra on 2009-09-18
Thanks a lot George.Your method was excellent.It worked for me.Im posting this from ma Ubuntu!,but I've a little problem.
I hv to add the line **quiet splash usbserial.vendor=0x0eab usbserial.product=0x9357** at kernel editing  every time I restart my computer otherwise when I dial wvdial it gives the following error:-

--> WvDial: Internet dialer version 1.60
--> Cannot open /dev/ttyUSB0: No such file or directory
--> Cannot open /dev/ttyUSB0: No such file or directory
--> Cannot open /dev/ttyUSB0: No such file or directory

and if i've added the line at restart,it is working great.
can u tell me how to fix this.
Also if u r on yahoo messenger or g talk,pls give me ur id.I have a lot of questions want to share.
Thanks

---

### Post by GeorgeVita on 2009-09-18
Hi **vikaskumargdra**,
you must use this method to connect, then you are going to do a full (and long!) update which will make the usbserial a driver. From this point the command will become: ```
sudo modprobe usbserial vendor=0x0eab product=0x9357
``` Later you can try to add a udev rule (automatic 'run' of above command when the modem is attached) or better try to make Network Manager useable (more difficult, more internet searching).

>>> udev rule creation: ```
gksudo gedit /etc/udev/rules.d/90-newmodem.rules
```and copy into that file the following:  ```
ACTION!="add", GOTO="modemEnd"
#
SUBSYSTEM=="usb", SYSFS{idProduct}=="9357", SYSFS{idVendor}=="0eab", GOTO="newModem"
#
LABEL="newModem"
RUN+="/sbin/modprobe usbserial vendor=0x0eab product=0x9357, MODE="660", GROUP="dialout"
#
LABEL="modemEnd"

``` Save and Exit from gedit. After reboot it must be OK.

Regards,
George

P.S. I am not using any 'online messenger'

---

### Post by vikaskumargdra on 2009-09-18
> **GeorgeVita said:**
> Hi **vikaskumargdra**,
you must use this method to connect, then you are going to do a full (and long!) update which will make the usbserial a driver. From this point the command will become: ```
sudo modprobe usbserial vendor=0x0eab product=0x9357
``` Later you can try to add a udev rule (automatic 'run' of above command when the modem is attached) or better try to make Network Manager useable (more difficult, more internet searching).

>>> udev rule creation: ```
gksudo gedit /etc/udev/rules.d/90-newmodem.rules
```and copy into that file the following:  ```
ACTION!="add", GOTO="modemEnd"
#
SUBSYSTEM=="usb", SYSFS{idProduct}=="9357", SYSFS{idVendor}=="0eab", GOTO="newModem"
#
LABEL="newModem"
RUN+="/sbin/modprobe usbserial vendor=0x0eab product=0x9357, MODE="660", GROUP="dialout"
#
LABEL="modemEnd"

``` Save and Exit from gedit. After reboot it must be OK.

Regards,
George

The problem is still there.
here is the output:

vikas@Searching:~$ sudo wvdial
[sudo] password for vikas: 
--> WvDial: Internet dialer version 1.60
--> Cannot open /dev/ttyUSB0: No such file or directory
--> Cannot open /dev/ttyUSB0: No such file or directory
--> Cannot open /dev/ttyUSB0: No such file or directory
vikas@Searching:~$ sudo modprobe usbserial vendor=0x0eab product=0x9357
FATAL: Module usbserial not found.

Have I do a full OS update???

---

### Post by GeorgeVita on 2009-09-18
Yes, you did not update the system. Try: ```
uname -a
``` this will show you the kernel version which is the initial (old) for 9.04 which has the usbserial encapsulated. You must use the 'edit grub' way to gain access to the modem, connect to internet, fully update from System > Administration > Update manager (long enough!) or from terminal: ```
sudo apt-get update && sudo apt-get dist-upgrade
```

After rebooting the new kernel version (from **2.6.28-13-generic** and later) you can use 'modprobe usbserial' as a command.

Regards,
George

---

### Post by vikaskumargdra on 2009-09-18
Thanks! I am sure this'll work.I'll post the results soon.
I've one more problem about lxu-800,but it is regarding Windows.
Whenever I use lxu-800 modem in Windows Vista or XP,it gives BSOD & my com. gets restart.The problem becomes when i use modem for 2-3 hours.If u know how to overcome it,pls tell me.Im waiting.

---

### Post by GeorgeVita on 2009-09-18
> **vikaskumargdra said:**
> ...I've one more problem about lxu-800,but it is regarding Windows. Whenever I use lxu-800 modem in Windows Vista or XP,it gives BSOD & my com. gets restart.The problem becomes when i use modem for 2-3 hours.

... completely 'off topic', not for windows but as it would be a h/w problem
 and you can check it running it on Ubuntu for the same time period. Just for reference read: [http://forum.huawei.com/jive4/thread.jspa?threadID=323666&tstart=0&orderStr=9](http://forum.huawei.com/jive4/thread.jspa?threadID=323666&tstart=0&orderStr=9)

I cannot be sure if above is similar/close to your problem, but from my experience most problems are '3G provider' oriented.

G

---

### Post by vikaskumargdra on 2009-09-18
> **GeorgeVita said:**
> Yes, you did not update the system. Try: ```
uname -a
``` this will show you the kernel version which is the initial (old) for 9.04 which has the usbserial encapsulated. You must use the 'edit grub' way to gain access to the modem, connect to internet, fully update from System > Administration > Update manager (long enough!) or from terminal: ```
sudo apt-get update && sudo apt-get dist-upgrade
```

After rebooting the new kernel version (from **2.6.28-13-generic** and later) you can use 'modprobe usbserial' as a command.

Regards,
George
The Result is:

vikas@Searching:~$ sudo apt-get update && sudo apt-get dist-upgrade
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty Release.gpg    
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty/main Translation-en_IN
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty/restricted Translation-en_IN
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty/universe Translation-en_IN
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty/multiverse Translation-en_IN
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty Release
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty/main Packages
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty/restricted Packages
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty/main Sources
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty/restricted Sources
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty/universe Packages
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty/universe Sources
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty/multiverse Packages
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty/multiverse Sources
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

what this means???

---

### Post by GeorgeVita on 2009-09-18
Check **uname -a** and be sure that you have an active internet connection to get all updates. This must be an installation and not a liveCD.

Also check system > Administration > Software Sources for your 'local server'.


G

---

### Post by vikaskumargdra on 2009-09-18
> **GeorgeVita said:**
> Check **uname -a** and be sure that you have an active internet connection to get all updates. This must be an installation and not a liveCD.

Also check system > Administration > Software Sources for your 'local server'.


G

Thanks again George.It was my mistake.I hv diabled updates in System-->Administration-->Software sources.Now its all right.Your knowledge is amazing.Keep it up!

---

### Post by raju50 on 2010-09-10
Hi. I have Problem with Reliance Netconnect LG LXU-800 USB Modem. I tried many solutions but those couldn't work for me. This is the error I keep getting no matter what solution I try:
FATAL: Error inserting LXU800Mdm (/lib/modules/2.6.32-24-generic/kernel/drivers/usb/LXU800Mdm.ko): Invalid module format

This error I see whenever I boot up my linux 2.6.32.24-generic. (This error I see on the black screen that appears before the desktop comes up.) I also see this error when I do 'bash setup.sh' (when I follow the instruction in the manual for installing the lxu-800 modem driver on linux).

---

