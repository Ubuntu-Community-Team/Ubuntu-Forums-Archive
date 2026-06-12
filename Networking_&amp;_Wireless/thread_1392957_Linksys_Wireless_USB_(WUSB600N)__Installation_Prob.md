---
title: "Linksys Wireless USB (WUSB600N)  Installation Problems..."
date: 2010-01-28
forum: Networking &amp; Wireless
---

### Post by jjrjr1 on 2010-01-28
Hi
 
Found a few threads addressing this but many are 6 months old or better.
 
There have been new drivers and new Ubuntu since any of the posts I have read.
 
I am trying to get a linksys WUSB600N up and running on Ubuntu Version 9.10.
 
I have downloaded the current driver versions from ralink.com
 
It compiled OK and I followed all the instructions that came with the driver. (incidentally other posts where drivers for this USB Adapter would not compile under Ubuntu 9.10.. Got error 2 from Make and Linux)
 
lsusb shows the device properly it shows a USD_DEVICE as 0x1737,0x0079
 
Some instructions mention adding those numbers to the rt2870.h file before compiling
In the latest driver download from ralink.com, there is no structure for this define. As I said, if I try to compile some of the older drivers found in the forum it will not compile. Get a make error 2..
 
after compile and install of the latest drivers, (complied fine)
 
I run the /sbin/insmod rt2870sta.ko
 
No errors yet....
 
If I run modprobe -l | grep rt2870
 
The module shows installed in the kernel like so
 
kernel/drivers/staging/RT2870STA/rt2870sta.ko
(all other wireless drivers seem to be located in kernel/drivers/wireless.. Not sure if this is significant)
 
Now here is where it fails...
 
I run 
 
/sbin/ifconfig ra0 inet 192.168.1.102 up
 
I get the following error
 
SIOCSIFADDR: No Such Device
ra0: Error while getting interface flags
ra0: Error while getting interface flags
No Such Device.
 
I have looked in the /dev directory and do not see a device ra0.. Should it show up there?
 
ifconfig shows only
 
eth0
 
lo
 
Running dmesg | grep rt2 shows
 
rt2870sta: no symbol version for module layout
usbcore: registered new interface driver rt2780sta
 
LOL I think I am close. Just need to find the right info..
 
Any ideas would be appreciated.
 
Thanks
 
John

---

### Post by chili555 on 2010-01-28
> ra0: Error while getting interface flags
No Such Device.Maybe the interface did not get created as ra0. Please do:```
iwconfig
```Is the interface wlan0 or eth1 or missing altogether? Incidentally, manual configuration, like this:> /sbin/ifconfig ra0 inet 192.168.1.102 upwill not work well, if at all, with Network Manager running. Can you click the Network manager icon and see networks and connect?

---

### Post by jjrjr1 on 2010-01-28
Hi
 
Thanks for the reply
 
I run  iwconfig
 
The response is
 
lo  no wireless extensions
 
eth0 no wireless extensions
 
Does this point me to the problem???
 
Thanks
 
John

---

### Post by chili555 on 2010-01-28
> Does this point me to the problem???Yes. No wireless interface was created.

Googling...

---

### Post by chili555 on 2010-01-28
I am very interested in this:  [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/408165](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/408165) especially post #38:> I built the RT3572 module like this:
1) download the RT3572 module source from RalinkTech website (filename: 2009_1222_RT3572_LinuxSTA_V2.3.0.0.tar.bz2)
2) execute the command "bunzip2 2009_1222_RT3572_LinuxSTA_V2.3.0.0.tar.bz2"
3) execute the command "tar -xvf 2009_1222_RT3572_LinuxSTA_V2.3.0.0.tar"
4) add the device and vendor id "{USB_DEVICE(0x1737,0x0079)}" between the "#ifdef RT35xx" and "#endif // RT35xx //" in the file "common/rtusb_dev_id.c"
5) modify the "os/linux/config.mk" like I described in my previous message
6) execute the command "sudo make"
7) execute the command "sudo make install"
8) execute the command "sudo modprobe rt3572sta" => a blue light will turn on and the network interface "ra0" will create (commands "ifconfig" and "iwconfig")

Notice: sometimes, my Ubuntu doesn't detect correctly my stick so I have to unplug and re-plug.Please try this approach. Let us know if you get stuck.

---

### Post by jjrjr1 on 2010-01-28
Hi
 
Thanks for the info.
 
I also am interested in getting this resolved and thanks so much for working with me on this.  I will keep you posted as to progress.
 
I, indeed, have V.2 of this thing.  Hell...  You don't have a choice when you buy the thing.
 
I tried with the RT8270 drivers I already downloaded.  Same Failure....
 
I will try the RT3572 driver now as he did and as the post suggests.
 
Thanks
 
John

---

### Post by jjrjr1 on 2010-01-28
Wow man....  That did it.
 
At least I have a blue lite and iwconfig shows ra0
 
Thanks so much.
 
Now I gotta figure out how to connect with it.
 
Any Ideas?  I am new to Ubuntu (fairly familiar with Linux/Unix)
 
Do you have a suggestion as to where I should put the
 
modprobe rt3572sta
 
command to cause the driver to load at startup??
 
Thanks again
 
John
 
I might have more questions about network manager if you do not mind later

---

### Post by jjrjr1 on 2010-01-28
Yo again man...
 
Connected WPA personal and I am connected wirelessly thru the WUSB600N
 
My next project is to get Skype linux running in the GUI
 
I will keep you posted
 
Thanks Again
 
John

---

### Post by chili555 on 2010-01-29
Please open a terminal and do:```
sudo gedit /etc/modules
```Add a single line:```
rt3572sta
```Proofread, save and close gedit. You should be all set.

When you get new updates and they include 'linux-image,' you will have to rebuild the driver module against the new linux-image, or kernel version as we old grey-beards call it. Go back to your 2009_1222_RT3572_LinuxSTA_V2.3.0.0 folder and run:```
sudo su
[COLOR="Red"]make clean[/COLOR]
make 
make install
modprobe rtrt3572sta
```

I am glad to hear of your success! So will the searchers. Enjoy!!!

---

### Post by jjrjr1 on 2010-01-29
Hi
 
Just wanted to post here a follow up, status, and supply the missing info from the unknown poster where he mentioned that it was in an earlier post.
 
Goal here was to get the LinkSys WUSB600N Network Adapter working on Ubuntu Linix V 9.10
 
Many thanks to Chili555 and the Unknown poster's info he found on Google. ( I googled for 2 days and never found the exact answer)
 
My environment: Pentium 4 2.8ghz, 2gig RAM, GeForce9400 Video, WUSB600N v.2. OS Ubuntu V. 9.10, Kernel 2.6.31-17-Generic (32 bit). (BTW. I am triple boot on this box... Win XP, Win 7, Linux)
 
Also, another note, after these steps are followed, The wireless card and network automatically come up at boot. Thanks for the info Chili!!! Does not appear you will need to make any changes to the init files. Also, again, I did the Ubuntu updates and found what Chili555 mentioned is true. Any updates to the Kernel does require you follow these steps again.
 
Some hardware information is, this USB adapter comes in two flavors, V 1 and V 2. You can determine which you have by looking at the Model Number on the device.
 
Note: These instructions work great and my connection has been fast and reliable using these instructions for my V 2 version of the adapter. I suspect (but can't prove it) that these instructions will also work on the V 1 version. If you try it on a V 1 version of the adapter you will need to run from the console "lsusb" and note the address/id pair & Vendor associated with your adapter. Where, in the instructions, you are editing the USB_DEVICE value you must use the pair detected by lsusb.
 
The first thing you need to do is download the drivers from RaLinkTech.
 
From Here: [http://www.ralinktech.com/support.php?s=2](http://www.ralinktech.com/support.php?s=2)
 
Select this driver package for download: RT3572USB
(Filename: 2009_1222_RT3572_LinuxSTA_V2.3.0.0.tar.bz2)
 
Put it somehwere you will be able to access it.
 
Follow these instructions found by Chilli555 on another board (modified by me a little).
 
1 ) execute the command "bunzip2 2009_1222_RT3572_LinuxSTA_V2.3.0.0.tar.bz2"
2 ) execute the command "tar -xvf 2009_1222_RT3572_LinuxSTA_V2.3.0.0.tar"
4 ) add the device and vendor id "{USB_DEVICE(0x1737,0x0079)}" between the "#ifdef RT35xx" and "#endif // RT35xx //" in the file "common/rtusb_dev_id.c"
Note1: Notice how the Vendor ID is set in these defines and duplicate that using the vendor found using lsusb. In my case of the V2 WUSB600N The vendor ID was Linksys and the address/id pair were 0x1737,0x0079.
Note2: If trying a V 1 of the adapter use the address/id pair & Vendor found by lsusb. I also added the define to the rt2870 data scructure as well just to be safe.
5 ) modify the "os/linux/config.mk" like I described in my previous message
Note: Here are the missing pieces...
In the root of the archive edit Makefile.
ensure that:
MODE = STA
TARGET = LINUX
PLATFORM = PC
are set.
Now edit os/linux/config.mk edit
HAS_WPA_SUPPLICANT=y
HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y
6 ) execute the command "sudo make"
7 ) execute the command "sudo make install"
8 ) execute the command "sudo modprobe rt3572sta" => a blue light will turn on and the network interface "ra0" will create (commands "ifconfig" and "iwconfig")
 
 
Now you can go to network manager and establish connection with your wireless router. (A re-boot may be necessary)
 
Also, Your machine will load and connect every time on re-boot.
 
An aside here regarding Getting Skype installed on Ubuntu V. 9.10....
 
Go Here: [http://blog.dipinkrishna.info/2009/08/how-to-install-skype-on-ubuntu-910.html](http://blog.dipinkrishna.info/2009/08/how-to-install-skype-on-ubuntu-910.html)
 
I used option 2 and downloaded the Debian Package for 32 bit.
 
Installed it using Ubuntu's package manager and had Skype up and running in 15 minutes. Really cool and easy.
 
Well that's it!!! Again Many, Many thanks to Chili....
 
This is just AWESOME... LOL
 
John

---

### Post by jjrjr1 on 2010-01-29
Done!!!

---

### Post by chili555 on 2010-01-29
> thanks to ChiliThank you for your kind words! I am very grateful it helped you, and by extension, perhaps dozens of searchers.

---

### Post by jjrjr1 on 2010-01-29
That's my intention.
 
Hope it helps many others.
 
Let's stay in touch man..
 
John

---

### Post by snugglenutz on 2010-03-19
Here is a how-to that DOES NOT involve source code or compiling.  Worked perfectly. 

[http://ubuntuforums.org/showpost.php?p=8591348&postcount=6](http://ubuntuforums.org/showpost.php?p=8591348&postcount=6)

---

### Post by geodanny on 2010-03-30
This worked for me. I have a WUSB100. I used the rt2870sta file instead since that is the correct file for the WUSB100.

---

### Post by geodanny on 2010-06-10
I am having issues after a new kernel update. My WUSB100 worked until then.

When the update came, I tried to recompile so it would work again. Chili555, I used your code. 
```
sudo su
make clean
make 
make install
modprobe rt2870sta
```

Network manager does not recognize that a wireless device is in place. The device is recognized by lsusb, the kernel module was created, and most everything looks in place. I know I'm missing something but have not figured out what it is, yet. Any help would be appreciated. Below are some of the outputs I think would be helpful to help me out. I should note that I did not get any errors or messages that seemed unusual when recompiling.

The machine is an older Compaq laptop running Ubuntu 8.04.,

```
brett@strawberries:~$ more /etc/modules
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

fuse
lp
rt2870sta

```

```
brett@strawberries:~$ more /etc/network/interfaces
auto ra0
iface ra0 inet dhcp

auto lo
iface lo inet loopback

```

```
brett@strawberries:~$ lsusb
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 003: ID 1737:0070  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

```

```
brett@strawberries:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:02:a5:b6:5f:f2  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1640 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1640 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:82188 (80.2 KB)  TX bytes:82188 (80.2 KB)

ra0       Link encap:Ethernet  HWaddr 00:1e:e5:e5:8b:cb  
          inet6 addr: fe80::21e:e5ff:fee5:8bcb/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:330 errors:0 dropped:0 overruns:0 frame:0
          TX packets:142 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:38269 (37.3 KB)  TX bytes:11440 (11.1 KB)

```

```
brett@strawberries:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ra0       Ralink STA  ESSID:"11n-AP"  Nickname:"RT2870STA"
          Mode:Auto  Frequency=2.412 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=10/100  Signal level:0 dBm  Noise level:-97 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


```


```
brett@strawberries:~$ dmesg | egrep 'rt28|usb|Phy'
[   16.474100] usbcore: registered new interface driver usbfs
[   16.474149] usbcore: registered new interface driver hub
[   16.498033] usbcore: registered new device driver usb
[   16.516320] usb usb1: configuration #1 chosen from 1 choice
[   16.619165] usb usb2: configuration #1 chosen from 1 choice
[   16.723134] usb usb3: configuration #1 chosen from 1 choice
[   17.016103] usb 2-1: new full speed USB device using uhci_hcd and address 2
[   17.212005] usb 2-1: configuration #1 chosen from 1 choice
[   29.115128] usbcore: registered new interface driver ndiswrapper
[   34.195717] rtusb init --->
[   34.197610] usbcore: registered new interface driver rt2870
[   35.700584] 1. Phy Mode = 5
[   35.700587] 2. Phy Mode = 5
[   35.719017] RTMPSetPhyMode: channel is out of range, use first channel=1 
[   35.731843] 3. Phy Mode = 9
[   35.778449] <==== rt28xx_init, Status=0
[   63.149521] usbcore: deregistering interface driver ndiswrapper
[   63.215766] usbcore: registered new interface driver ndiswrapper
[  244.267783] usb 2-1: USB disconnect, address 2
[  244.270323] rtusb_disconnect: unregister usbnet usb-0000:00:1d.1-1
[  244.582955] usb 2-1: new full speed USB device using uhci_hcd and address 3
[  244.587121] usb 2-1: configuration #1 chosen from 1 choice
[  246.244165] 1. Phy Mode = 5
[  246.244173] 2. Phy Mode = 5
[  246.266982] RTMPSetPhyMode: channel is out of range, use first channel=1 
[  246.282062] 3. Phy Mode = 9
[  246.320405] <==== rt28xx_init, Status=0

```


```
brett@strawberries:~$ sudo modinfo rt2870sta
filename:       /lib/modules/2.6.24-28-generic/kernel/drivers/net/wireless/rt2870sta.ko
version:        2.3.0.0
license:        GPL
description:    RT2870 Wireless Lan Linux Driver
author:         Paul Lin <paul_lin@ralinktech.com>
srcversion:     BFE72125F5BC16053AC2BDE
alias:          usb:v0DB0p6899d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v100Dp9031d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp815Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0411p00E8d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1737p0071d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1737p0070d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v7392p7717d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v7392p7718d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v5A57p0282d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v5A57p0280d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1690p0740d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v04E8p2018d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C09d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1482p3C09d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp815Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp805Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v157Ep300Ed*dc*dsc*dp*ic*isc*ip*
alias:          usb:v129Bp1828d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0E66p0003d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0E66p0001d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v15C5p0008d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083Ap6618d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3247d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C25d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0471p200Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p9702d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p9701d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0CDEp0025d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0586p3416d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0CDEp0022d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083Ap7522d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083Ap8522d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083ApA618d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083ApB522d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v15A9p0006d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1044p800Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07AAp003Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07AAp003Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07AAp002Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C27d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C23d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp8053d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C07d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C11d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C09d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2019pED06d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C28d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C06d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p002Dd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p002Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p002Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0017d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0B05p1742d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0B05p1732d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0B05p1731d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v177Fp0302d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0789p0164d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0789p0163d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0789p0162d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083Ap7512d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p003Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0039d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8p2770d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8p2870d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp2870d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp2770d*dc*dsc*dp*ic*isc*ip*
depends:        usbcore
vermagic:       2.6.24-28-generic SMP mod_unload 586 
parm:           mac:rt28xx: wireless mac addr (charp)

```

---

### Post by chili555 on 2010-06-10
Network Manager will not recognize interfaces, in your case ra0, that are listed in */etc/network/interfaces.* Please amend your *interfaces* file to:```
auto lo
iface lo inet loopback
```Also, I notice this:> [   63.149521] usbcore: deregistering interface driver ndiswrapper
[   63.215766] usbcore: registered new interface driver ndiswrapper
Please run:```
ndiswrapper -l
```That's a lower case L for 'list.'  Whatever driver you find, rt2870, probably, needs to be erased:```
ndiswrapper -e <driveryoufound>
```It may then benefit from a reboot. Is it working?

---

### Post by geodanny on 2010-06-10
Thanks, the first step solved it. Network Manager found the AP as soon as I saved the /etc/network/interfaces file. Reboot was not even necessary.

This computer does not have ndiswrapper installed so I'm not sure why that message is appearing in the log. Perhaps it was installed at one time. I'll worry about it later; wifi is up. :-)

---

