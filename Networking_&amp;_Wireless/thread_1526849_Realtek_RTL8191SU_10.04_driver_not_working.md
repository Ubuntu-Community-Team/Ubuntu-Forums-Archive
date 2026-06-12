---
title: "Realtek RTL8191SU 10.04 driver not working"
date: 2010-07-08
forum: Networking &amp; Wireless
---

### Post by anothermikemiller on 2010-07-08
I'm helping a friend whose old computer got the windows 2010 virus(?) and killed his install. I shrunk the partition and installed 10.04 but I couldn't get the usb wireless card to work properly.

brand: Zonet
model: zew2546
chipset: Realtek RTL8191SU

System is loading r8192s_usb for the device, but it just says "device not ready."

I compiled the drivers from Realtek's website by extracting the archives and using "make". The 8191su drivers do not work, but the 8192su drivers work fine (these are a package 8712, 8188, 8191, 8192su). This creates a module called 8712u.ko.

EDIT: I forgot to add that "make install" doesn't work. I get a "No rule to make target '/config'. Stop."

So I test the new drivers:

```
sudo insmod 8712u.ko
```

Nothing happens and lsmod shows it installed. I remove the conflicting module:

```
sudo rmmod r8192s_usb
```

Reinsert the card and it works.

This driver worked for both the 2.6.32 and 33 kernel. (I had tried the new kernel only to find that it doesn't include the r8192s driver or a replacement).

How do I make ubuntu use the correct driver on start up and where should I put my compiled driver?

I tried adding it to /etc/modules but I get an error on boot about creating dev/(null) or some such.

---

### Post by anothermikemiller on 2010-07-10
Well I still haven't quite figured this out. I apparently need to install the module into the correct folder for /etc/modules to see it and use some kind of config file.

I remember using a tool to add and remove kernel drivers, but it was back on edgy or hardy. I'll see if I can find some info about general kernel compilation.

Currently, I have a script that runs at logon issuing the remove and add commands. I really need this to run for all users, though.

---

### Post by anothermikemiller on 2010-07-14
There is a file to remove conflicting drivers so that something else (the one I built) is started instead.

Just edit the file and add a new line:

```
gksudo gedit /etc/modprobe.d/blacklist.conf
```

I added this at the end of the file:

```
#This driver doesn't work. Compiled and installed realtek 8712u.
blacklist r8192s_usb

```

---

### Post by anothermikemiller on 2010-07-14
This is my final solution.

I replaced the defective driver with the new one.

```

sudo mv '/lib/modules/2.6.32-23-generic/kernel/drivers/staging/rtl8192su/r8192s_usb.ko' '/lib/modules/2.6.32-23-generic/kernel/drivers/staging/rtl8192su/r8192s_usb.ko.original'

sudo cp '/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100625/8712u.ko' '/lib/modules/2.6.32-23-generic/kernel/drivers/staging/rtl8192su/r8192s_usb.ko 

```

You don't have to use blacklist.conf or any modprobe commands. You'll have to do this for each kernel version you have installed or if you update the kernel.

I don't believe this is the correct way to fix this problem, but hopefully the driver gets fixed in the next kernel update.

---

### Post by baguahsing on 2010-07-14
I was able to use the 8712u.ko driver using insmod.  However, once I reboot, my wlan0 no longer exists and I have to make and insmod again for it to show up.  I'm using an Asus n-10 usb wireless adaptor since I can't get my built in wireless to work.  Which by the way is listed as eth1.  How do I get usb adaptor to be the default as startup?

---

### Post by anothermikemiller on 2010-07-15
Did your 'make install' also fail? Actually, unless you do 'make clean' you won't have to run make again. You only need to build it once.

You have to add a line to /etc/modules so that it will load. You can put the module into the kernel directory:

lib/modules/2.6.XX-XX-generic/kernel/drivers/wireless/**8712u/8712u.ko**

(where the X's are your kernel version and the bold is what you add)

or somewhere in the /usr directory and symlink to it.

Then there is a command to tell the system there is a new driver but I don't know what it is. That is where I got stuck.

You can replace the broken driver like I did by just renaming the module.

---

### Post by baguahsing on 2010-07-17
bump

---

### Post by mikedep333 on 2010-08-15
Actually, it appears that the r8192s_usb module is the correct one but it is failing to download the firmware.

dmesg shows a number of lines like this:

```
rtl819xU: --->FirmwareDownload92S()

usb 1-1: firmware: requesting RTL8192SU/rtl8192sfw.bin
rtl819xU:request firmware fail!

rtl819xU:Firmware Download Fail!!a
```

These is a bug report for this here:
[https://bugs.launchpad.net/ubuntu/+source/linux-firmware/+bug/594248](https://bugs.launchpad.net/ubuntu/+source/linux-firmware/+bug/594248)
There is a link to a .deb linux-firmware package. It allowed me to scan but not to connect to my verizon actiontek WEP network. I posted some more details in that bug report. We should all click "This bug affects me." in that page.

---

### Post by jhawk on 2010-09-08
Ref: rl8191 usb doggle

Download drivers from realtek
Expand to a build directory
change directory to build directory/drivers extract *.tgz
in the new directory "sudo make && make install"

then:
     sudo gedit /etc/modprobe.d/blacklist.conf
     Add line "blacklist r8192s_usb"
     save and reboot
The wireless should now be working.....

---

### Post by Allxsan on 2010-09-23
the firmware must be in a folder named "RTL8192SU"
( "/lib/firmware/RTL8192SU")

Using this folder the firmware can be downloaded but with my Belkin RTL8192SU and kernel - staging drivers I'm always unable to gain a connection! 
After some time the password input box appear. There is no way to gain a connection, also tried putting the wifi router very near.

Using Realtek drivers works, but only on 32bit os ( with some small problem eg. netspeed can't detect any speed and the reported quality signal goes from 10% to 90/100% )
Amd64 os suddenly lock once the Realtek driver is loaded 

( also tried using gentoo, fedora and mandriva with the same results )

---

### Post by Allxsan on 2010-09-24
the problem was related to the firmware file, 

differents  .bin  that can be found in some archive  and/or on some site not always works

need to download "rtl8192sfw.bin" from svn.debian.org 

can be done using this command 

"wget http://svn.debian.org/wsvn/kernel/dists/trunk/firmware-nonfree/realtek/RTL8192SU/rtl8192sfw.bin"

put it in folder 
"/lib/firmware/RTL8192SU"

( I've found other bigger rtl8192sfw.bin  also in some other folder of svn.debian site but doesn't work ) 

After this the kernel ( staging ) driver works fine in 32 and 64 bit environment

---

### Post by DragonlordP on 2010-09-24
Well, here's my story. I was trying to get it working in 64bit for a couple of days, saw that there are solutions for 32bit so I installed 9.10 (I already had a burnt cd). I did the make/make install thingie and it worked with no problems. So, I upgraded to 10.04.1 and then to 10.10 beta. I tried make clean/make/make install, nothing - it had loaded the driver, saw the device as wlan1 but didn't find any networks and the lights were off. So, I read this thread and I saw that the folder in lib/firmware is called 8192SE and not 8192SU. I renamed the folder and, voila, it worked - found networks, that is. It still can't connect. I also tried replacing the firmware with the one from debian, no luck. Any ideas?

---

### Post by Allxsan on 2010-09-24
don't need to compile the Realtek drivers, just use the kernel driver 
( and the firmware from svc.debian.. 

"wget http://svn.debian.org/wsvn/kernel/dists/trunk/firmware-nonfree/realtek/RTL8192SU/rtl8192sfw.bin"

placed in "lib/firmware/RTL8192SU" )

---

### Post by DragonlordP on 2010-09-24
Well, I had already compiled them, you think this could be the problem? Should I remove them, and how? BTW, inside lib/firmware there is also a folder named RTL8192E with three files, boot.img, data.img, main.img, what should I do with that?

---

### Post by DragonlordP on 2010-09-24
btw, I disabled the driver from system>administration>restricted drivers and I still get the same problem
edit: the RTL8192SU folder also contains rtl8192sfw74.bin and rtl8192sfw492.bin

---

### Post by Allxsan on 2010-09-24
check that in the file "/etc/modprobe.d/blacklist.conf" 
there isn't a line with
"blacklist r8192s_usb"

check the file "/etc/modules"
if there is a line containing "8712u"
comment out with #  ( disable ) eg. "# 8712u"

then type in a terminal:

"rmmod -v 8712u"
"rmmod -v r8192s_usb"

( look the output on the screen 
you can see 
"rmmod r8192s_usb, wait=no"
or 
"rmmod 8712u, wait=no" )

then try

"modprobe -v r8192s_usb"
( look the output on the screen )

"dmesg"
( look the output on the screen, check if at the end there is some line complaining about the firmware )

must work without a reboot, but not always 
( sometimes still some connection problem, a reboot can do the job :) )

At the moment I'm using Ubuntu 10.10beta,  connected via a Belkin usb device based on Realtek RTL8192SU and using the kernel driver

---

### Post by DragonlordP on 2010-09-24
hmmm ok (thanks A LOT for your time btw!), I did all that, these lines were not in these files, 8712u didn't exist, r8192s_usb existed, was removed and then I did modprobe, output was
insmod /lib/modules/2.6.35-22-generic/kernel/drivers/staging/rtl8192su/r8192s_usb.ko
with dmesg I couldn't find anything related to firmware, the only lines that seemed like an error were:
[  611.865167] rtl819xU:rtl819x_watchdog_wqcallback(): AP is powered off,connect another one
and
[  619.931284] rtl819xU:SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth

---

### Post by DragonlordP on 2010-09-24
btw iwconfig returns this:

wlan0     IEEE 802.11bg  ESSID:"Forthnet@home"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:1D:68:76:65:1D   
          Bit Rate=5.5 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=14/100  Signal level=14/100  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

wlan1     802.11b/g  ESSID:"Forthnet@home"  
          Mode:Managed  Frequency=2.417 GHz  Access Point: 00:1D:68:76:65:1D   
          Bit Rate=54 Mb/s   
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/100  Signal level=0 dBm  Noise level=0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

(wlan0 is another wifi usb which I use to connect, but I have also tried the realtek without connecting it, in case there is some kind of conflict)

and lsusb gives

Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 046d:c03d Logitech, Inc. M-BT96a Pilot Optical Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 045e:00b0 Microsoft Corp. Digital Media Pro Keyboard
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005: ID 0ace:1215 ZyDAS ZD1211B 802.11g
Bus 001 Device 004: ID 0bda:8174 Realtek Semiconductor Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by Allxsan on 2010-09-24
this is my output using Realtek driver


"dmesg"

```
==DriverVersion: v2.6.0006.20100625==
register rtl8712_netdev_ops to netdev_ops
8712_usb_endpoint_descriptor(0):
bLength=7
bDescriptorType=5
bEndpointAddress=83
wMaxPacketSize=200
bInterval=0

8712_usb_endpoint_descriptor(1):
bLength=7
bDescriptorType=5
bEndpointAddress=4
wMaxPacketSize=200
bInterval=0
 
8712_usb_endpoint_descriptor(2):
bLength=7
bDescriptorType=5
bEndpointAddress=6
wMaxPacketSize=200
bInterval=0

8712_usb_endpoint_descriptor(3):
bLength=7
bDescriptorType=5
bEndpointAddress=d
wMaxPacketSize=200
bInterval=0
 
8712u : USB_SPEED_HIGH
nr_endpoint=4
Boot from EFUSE
Autoload OK!!
CustomerID = 0x  15
.....
.........
.........
.........

```


"iwconfig"

```
wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Frequency:2.457 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          
vboxnet0  no wireless extensions.

wlan2     IEEE 802.11bg  ESSID:"xxxxxxxxxxxxxxx"  
Nickname:"rtl_wifi"
          Mode:Managed  Frequency:2.457 GHz  Access Point: 00:1C:A2:BF:2F:90   
          Bit Rate:54 Mb/s   Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Encryption key:xxxx-xxxx-xx   Security mode:open
          Power Management:off
          Link Quality=10/100  Signal level=10/100  Noise level=0/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```


-----------------------

this is using kernel diver

"dmesg"


```
Linux kernel driver for RTL8192 based WLAN cards
Copyright (c) 2007-2008, Realsil Wlan
==>ep_num:4, in_ep_num:1, out_ep_num:3
==>RtInPipes:3  
==>RtOutPipes:4  6  13  
==>txqueue_to_outpipemap for BK, BE, VI, VO, HCCA, TXCMD, MGNT, HIGH, BEACON:
1  1  0  0  2  2  2  2  2  
Dot11d_Init()
usbcore: registered new interface driver rtl819xU
udev[22663]: renamed network interface wlan1 to wlan2
rtl819xU:FirmwareRequest92S(): signature: 8192, version: 902b, size: 30, imemsize: 7408, sram size: 9688
rtl819xU:FirmwareCheckReady(): LoadFWStatus(1), success
rtl819xU:FirmwareCheckReady(): LoadFWStatus(2), success
rtl819xU:FirmwareCheckReady(): DMEM code download success, CPUStatus(0x3f)
rtl819xU:FirmwareCheckReady(): polling load firmware ready, CPUStatus(ff)
rtl819xU:FirmwareCheckReady(): Current RCR settings(0x157e20e)
rtl819xU:FirmwareCheckReady(): LoadFWStatus(3), success
rtl819xU:FirmwareDownload92S(): Firmware Download Success
ADDRCONF(NETDEV_UP): wlan2: link is not ready

```

"iwconfig"


```
wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Frequency:2.457 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          
vboxnet0  no wireless extensions.

wlan2     802.11b/g  link  ESSID:"xxxxxxxxxxxxxxxxxxxxxxxx"  
          Mode:Managed  Frequency=2.457 GHz  Access Point: 00:1C:A2:BF:2F:90   
          Bit Rate=54 Mb/s   
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Encryption key:xxxx-xxxx-xx   Security mode:open
          Power Management:off
          Link Quality=65/100  Signal level=-70 dBm  Noise level=-102 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

-------------------------------------------------
the firmware is 68Kb ( the non working one is 80Kb )
the wlan0 is Ralink internal PCI card

---

### Post by DragonlordP on 2010-09-24
Well, I tried all that a few times and, guess what, it's now working! Thanks!

---

### Post by DragonlordP on 2010-09-25
Alright, this is getting ridiculous. I left the pc on all night, in the morning it was disconnected and won't connect again, I tried rebooting, disabling the driver from system>administation>drivers and rebooting, enabling it and rebooting, the thing just won't connect. And yesterday it had a great signal as well (I'm two floors down from the router, the wireless I'm using now gets 12-16% and with the realtek I had 78%!)

---

### Post by DragonlordP on 2010-09-25
wtf, I just tried again and it just connected, 71%, seriously, WTF.

---

### Post by Allxsan on 2010-09-25
here still online via Realtek/Belkin RTL8192SU and kernel driver.

The Realtek driver indicate a very strange signal strength , 
still at 10% for minutes and going to 90% for some seconds; the netspeed applet is able to detect the connection but the speed is always at 0. You can connect and disconnect, the Realtek driver NOT REQUIRE the firmware file
( on a 64bit os  this driver does not work at the 99% of the cases. Once loaded the driver, the screen become black and keyboard leds blink )


you are right
The kernel driver seems to show stable and realistic values, but once disconnected it's much difficult to connect again

---

### Post by jaysage on 2010-10-18
I downloaded and installed the drivers as described, but when I do an 'insmod 8712u.ko' my screen goes blank and the keyboard lights blink.  I'm on an amd64 machine and I've noticed that other people see crashes too.  Does anyone know a solution for building this driver on 64bit machines?

---

### Post by jaysage on 2010-10-18
My amd64 machine dies with a dark screen and blinking keyboard lights if I insmod the realtek drivers.  I downloaded the firmware file as per the /lib/firmware/RT8192SU instructions in previous posts but my USB dongle is not recognized at all.  Its the exact same Fry's dongle that everyone else is using, but I can't get my machine to recognize it at all, except for the 'lsusb' listing.  Does anyone know how to get the realtek drivers to work on amd64 processors?

---

### Post by oliford on 2010-11-02
I have just bought a RTL8191SU and am using it on 10.04 (lucid) on a 64-bit machine. The driver in the kernel (which is staging) seems to mostly work with that 67KB firmware BIN file from debian. However, it seems to briefly drop out for ~ a second, every now and then. It's not a huge problem browsing etc but is most evident on Skype etc. The 'dmesg' shows several lines like:
"rtl819xU:Error TX URB for zero byte -62, error -2"

Does anyone else see this? Anyone know of any existing bug reports to this effect? (I googled but nothing looks right)

I also compiled and installed the Realtek own drivers (8712u.ko) which just hangs the system entirely. It also stops my machine booting unless I remove it from the modules path. Maybe they wrote them in a way that cannot work in 64-bit.

Has anyone managed to get Realtek's own drivers to work on a 64-bit system?

It seems the staging drivers are in a better state than Realtek's, so I will file a bug for the dropping out and maybe, along with when the firmware is fixed ([https://bugs.launchpad.net/ubuntu/+source/linux-firmware/+bug/594248](https://bugs.launchpad.net/ubuntu/+source/linux-firmware/+bug/594248)), this can work out of the box in a couple of kernels time.

---

### Post by oliford on 2010-11-03
Ok, maybe not....

It seems that in the very latest kernels (2.6.36-rc3 ish), they've dropped the r8192s_usb driver in favour of a cleaned up version of Realtek's own (r8712u).

After hacking the kernel source around, I've managed to get this new driver to compile against the headers for my current Ubuntu kernel (2.6.32-25-generic) because the one it is actually in, is newer than is available in Ubuntu's development kernel git tree. 

This means a few things:
a) It will eventually just work out of the box.
b) This might be quite a while, I don't know if 11.04 will use 2.6.36.
c) I have a compiled and running version and it works so far without any problems :).

The **temporary hack**....

I've put the binary, built for my amd64 system against 2.6.32-25-generic here:
[http://www.oliford.co.uk/files/r8712u.ko](http://www.oliford.co.uk/files/r8712u.ko)

The only way I could get it to compile, was by pretending it was rtl8192su, so that all the configs Makefiles, and things I don't understand work.

To compile against your own, do this:

```

sudo apt-get install linux-headers-`uname -r`
wget http://www.oliford.co.uk/files/rtl8712-pretending-to-be-rtl8192su.tar.gz
tar xvzfp rtl8712-pretending-to-be-rtl8192su.tar.gz
cd rtl8712-pretending-to-be-rtl8192su/
make -C /usr/src/linux-headers-`uname -r` M=`pwd` modules
sudo make -C /usr/src/linux-headers-`uname -r` M=`pwd` modules_install
sudo depmod
sudo modprobe -rv r8712s_usb
sudo modprobe -v r8712u

```

That should produce r8712u.ko and place it in the appropriate place. You will probably need to add 'blacklist r8192s_usb' to /etc/modprobe.d/blacklist.conf as well, to stop it loading the old one.

---

### Post by oliford on 2010-11-03
When associated, my link quality is at 100%. If anyone else gets this to work, can you tell me if yours is.

---

### Post by mbeentjes on 2010-11-11
Just installed newest kernel. Did nothing yet, my internet driver (wireless) doesn't work, now trying oliford's method.

---

### Post by shenmeister on 2010-12-02
After reading the posts in this thread (which helped a lot), I just wanted to post my experience, in case it helps anyone else.

Here's my current setup:
Ubuntu 10.04 Lucid Desktop x86 (kernel 2.6.32-26-generic)
Patriot Wireless N USB Adapter (PCB0WAU2-N)

This wireless adapter also uses the RTL8191SU chipset. I found that the Linux driver that came with the CD and on the Patriot website had errors and would not compile properly (rtl8712_8188_8191_8192SU_usb_linux_v2.6.0005.20091229 when extracted). So I downloaded the latest drivers from Realtek (rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100625) which compiled properly without errors. Here are the steps I took to compiling and installing it:

1. Installing the driver:
(while in the downloaded driver directory)
```
$ sudo su
$ make
$ make install
```2. Remove r8192s_usb module:
```
$ rmmod r8192s_usb
```3. Blacklist the r8192s_usb module in blacklist.conf
```
$ cd /etc/modprobe.d
$ gedit blacklist.conf
```In gedit, add the following lines at the end of file and close and save:
# Add your comment here
blacklist r8192s_usb

4. Exit superuser
```
$ exit
```5. Plug in wireless adapter and setup the wireless connection.

Note: I didn't try using the kernel-included r8192s_driver with the firmware download, but it would have been my next step had my first steps failed. I only have a 802.11g network and I haven't had any connection problems. I haven't been able to test on an 802.11n network yet, so I don't know how well the driver works there.

---

### Post by walt.smith1960 on 2010-12-02
Getting my RealTek RTL8192SU based device working was easy once I found this on launchpad:   [http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg2620217.html](http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg2620217.html).  I did a fresh install of 10.04 32 bit then copied the firmware file referenced in the link above. Restarted and wifi came alive and connected. I'm a happy camper.  I messed with Maverick previously with no success.  I didn't try this firmware file.  I've read where Maverick has some Wifi issues and there's a new driver on its way for Narwahl according to the bug report.  The TrendNet TEW-649UB is a nice solution for notebooks-it only sticks out about 22 mm. and signal strength is as good as any other adapter I've used.

The TrendNet TEW649UB will also work with NDISwrapper but I had a problem with it resuming after suspend and never really tried to get the driver to load after resuming--using a native Linux solution seems preferable.

Edit:  This solution works in 64 bit maverick as well.  It also works on a Flintstone era Thinkpad with 32 bit Lucid & 'full speed' (12 mb./sec) USB though speed is of course reduced.

---

### Post by nealos on 2011-01-15
Thank you Walt.Smith1960!  The launchpad method you linked to worked on my 10.04 (32 bit, 2.6.32-27-generic) set up with an intellinet N150 usb adapter which lsub's as an rtl8188.  Much easier than compiling, downloading, blacklisting, etc.  Although I did have to create the folder /lib/firmware/RTL8192SU/ since it did not exist.  This is what worked for me (copied from your launchpad link):
```

$wget [http://launchpadlibrarian.net/37387612/rtl8192sfw.bin.gz](http://launchpadlibrarian.net/37387612/rtl8192sfw.bin.gz)
$gunzip rtl8192sfw.bin.gz
$sudo mv rtl8192sfw.bin /lib/firmware/RTL8192SU/
```

---

### Post by uksparky on 2011-01-20
> **nealos said:**
> Thank you Walt.Smith1960!  The launchpad method you linked to worked on my 10.04 (32 bit, 2.6.32-27-generic) set up with an intellinet N150 usb adapter which lsub's as an rtl8188.  Much easier than compiling, downloading, blacklisting, etc.  Although I did have to create the folder /lib/firmware/RTL8192SU/ since it did not exist.  This is what worked for me (copied from your launchpad link):
```

$wget [http://launchpadlibrarian.net/37387612/rtl8192sfw.bin.gz](http://launchpadlibrarian.net/37387612/rtl8192sfw.bin.gz)
$gunzip rtl8192sfw.bin.gz
$sudo mv rtl8192sfw.bin /lib/firmware/RTL8192SU/
```

The above seemed to work for me too, however it does appear to suffer from the occasional drop in connection. Interesting how well this works when 11.04 is released.

---

### Post by dyingdreams on 2011-02-13
The method of installation posted by walt.smith and confirmed by nealos worked effortlessly. As to the reports of the connection dropping, I have experienced some of this myself, and came up with this fix. 

[IMG]http://i53.tinypic.com/209neit.jpg[/IMG] 

I cannot say if this will work for all RTL8191SU based devices, but for this Azio Corp. product, the issue seemed to stem from overheating. So I removed the plastic housing, took a 10mm*10mm copper heatsink, cut a slightly smaller square hole in the housing directly over the chip, and applied a small amount of thermal paste between the heatsink and the chip. If done right the heatsink should fit snugly, and the dropped connections should be a thing of the past.

---

### Post by coolbrook on 2011-03-03
> **Allxsan said:**
> 
must work without a reboot, but not always 
( sometimes still some connection problem, a reboot can do the job :) )

At the moment I'm using Ubuntu 10.10beta,  connected via a Belkin usb device based on Realtek RTL8192SU and using the kernel driver

Thanks so much.  I have this (Zonet ZEW2546) working on 10.10 Meerkat 64 now.

---

### Post by fogNL on 2011-03-09
> **oliford said:**
> Ok, maybe not....

It seems that in the very latest kernels (2.6.36-rc3 ish), they've dropped the r8192s_usb driver in favour of a cleaned up version of Realtek's own (r8712u).

After hacking the kernel source around, I've managed to get this new driver to compile against the headers for my current Ubuntu kernel (2.6.32-25-generic) because the one it is actually in, is newer than is available in Ubuntu's development kernel git tree. 

This means a few things:
a) It will eventually just work out of the box.
b) This might be quite a while, I don't know if 11.04 will use 2.6.36.
c) I have a compiled and running version and it works so far without any problems :).

The **temporary hack**....

I've put the binary, built for my amd64 system against 2.6.32-25-generic here:
[http://www.oliford.co.uk/files/r8712u.ko](http://www.oliford.co.uk/files/r8712u.ko)

The only way I could get it to compile, was by pretending it was rtl8192su, so that all the configs Makefiles, and things I don't understand work.

To compile against your own, do this:

```

sudo apt-get install linux-headers-`uname -r`
wget http://www.oliford.co.uk/files/rtl8712-pretending-to-be-rtl8192su.tar.gz
tar xvzfp rtl8712-pretending-to-be-rtl8192su.tar.gz
cd rtl8712-pretending-to-be-rtl8192su/
make -C /usr/src/linux-headers-`uname -r` M=`pwd` modules
sudo make -C /usr/src/linux-headers-`uname -r` M=`pwd` modules_install
sudo depmod
sudo modprobe -rv r8712s_usb
sudo modprobe -v r8712u

```

That should produce r8712u.ko and place it in the appropriate place. You will probably need to add 'blacklist r8192s_usb' to /etc/modprobe.d/blacklist.conf as well, to stop it loading the old one.

Thank you so much for this!  Finally, my wireless is working correctly on 10.04.

---

### Post by calande on 2011-04-08
Hello guys, I have the same problem, I followed Allxsan's procedure (comment #16), my internet connection hardly stays up, I lose my connection and I have to reconnect very often. I have 3 bars out of 4 in the signal strengh level. If I connect a different wifi stick, the other stick connects in 2 seconds and stays up. My RTL8191SU stick works on W7. Do you know what may cause the problem not being able to connect to the network in Ubuntu? Thanks ;)

---

### Post by calande on 2011-04-08
> That should produce r8712u.ko and place it in the appropriate place.
Where should I place your r8712u.ko binary? Thanks ;)

---

### Post by calande on 2011-04-08
Hi, now, my Realtek RTL8191SU NIC displays all networks with just one bar, while under Windows, they all have different signal strenghs, many of them with 4 or 5 bars. Do you know why this happens under Ubuntu? Thanks.

---

### Post by calande on 2011-04-09
In the latest news, with my old G wifi dongle, I have two bars only but my connection is pretty fast. But with my RTL8191SU dongle, I have 3 bars, however my connection is very slow. Do you experience the same problem in Ubuntu?

---

### Post by kchilaka on 2011-10-02
The realtek provided drivers did not work for me as well. I followed your instructions to fix the problems I was having on my Debian Squeeze installation. Built my drivers using the source package from your link and now the wireless connection is 
rock stable. My kernel was 2.6.32-5-amd64
Thank you.. 

> **oliford said:**
> Ok, maybe not....

It seems that in the very latest kernels (2.6.36-rc3 ish), they've dropped the r8192s_usb driver in favour of a cleaned up version of Realtek's own (r8712u).

After hacking the kernel source around, I've managed to get this new driver to compile against the headers for my current Ubuntu kernel (2.6.32-25-generic) because the one it is actually in, is newer than is available in Ubuntu's development kernel git tree. 

This means a few things:
a) It will eventually just work out of the box.
b) This might be quite a while, I don't know if 11.04 will use 2.6.36.
c) I have a compiled and running version and it works so far without any problems :).

The **temporary hack**....

I've put the binary, built for my amd64 system against 2.6.32-25-generic here:
[http://www.oliford.co.uk/files/r8712u.ko](http://www.oliford.co.uk/files/r8712u.ko)

The only way I could get it to compile, was by pretending it was rtl8192su, so that all the configs Makefiles, and things I don't understand work.

To compile against your own, do this:

```

sudo apt-get install linux-headers-`uname -r`
wget http://www.oliford.co.uk/files/rtl8712-pretending-to-be-rtl8192su.tar.gz
tar xvzfp rtl8712-pretending-to-be-rtl8192su.tar.gz
cd rtl8712-pretending-to-be-rtl8192su/
make -C /usr/src/linux-headers-`uname -r` M=`pwd` modules
sudo make -C /usr/src/linux-headers-`uname -r` M=`pwd` modules_install
sudo depmod
sudo modprobe -rv r8712s_usb
sudo modprobe -v r8712u

```

That should produce r8712u.ko and place it in the appropriate place. You will probably need to add 'blacklist r8192s_usb' to /etc/modprobe.d/blacklist.conf as well, to stop it loading the old one.

---

### Post by md2406 on 2011-10-13
Download the latest drivers from RealTek website and follow this website [http://samiux.blogspot.com/2010/05/howto-realtek-8192su-usb-dongle.html]("http://samiux.blogspot.com/2010/05/howto-realtek-8192su-usb-dongle.html")

It worked for me and hope works for you.

---

### Post by giopas on 2011-10-15
Hi,

I have the following wifi-usb-key:

```
ID 06f8:e031 Guillemot Corp. Hercules HWNUm-300 Wireless N mini [Realtek RTL8191SU]
```

I am trying to make it work under Ubuntu 11.10.

The interface wlan0 seems to have been created, my SSID is discovered, but I can not properly connect to it.

Reading around (like [here]("http://wiki.debian.org/rtl819x")), I tried to compile [Realtek drivers]("http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=2&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#RTL8192SU") by my own, but I have this simple problem: I have a 3.0.0-12 linux kernel, but drivers only work for kernel < 2.6.37.

Ndiswrapper does not seem to work either.

Someone could help me/us, please?

enjoy, ;)
giopas

---

