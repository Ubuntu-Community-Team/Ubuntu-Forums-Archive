---
title: "atheros based usb wifi dongle?"
date: 2006-02-22
forum: Networking &amp; Wireless
---

### Post by tukster on 2006-02-22
hello
has anyone been able to make it work?
as i understand madwifi doesn't support usb dongles.

mine is TP-Link wn260g.


> 
$ sudo lshw

*-usb UNCLAIMED
                description: Generic USB device
                product: TL-WN620G
                vendor: Atheros Communications Inc
                physical id: 7
                bus info: usb@2:7
                version: 0.01
                serial: 1.0
                capabilities: usb-2.00
                configuration: maxpower=500mA speed=480.0MB/s


so ubuntu doesn't even recognize it as network device :confused:
ndiswrapper can be made to install a win driver. but the wlan0 doesn't appear in networking settings panel (nor in iwlist).

anyone here knows how to make it work???

---

### Post by CleverID on 2006-02-26
I've got the same issue...
Anyone have some advice?  I've been through wiki, installed ndiswrapper, etc.  Could really use an assist here.

Thanks, y'all

-C

---

### Post by sorairo on 2007-05-09
I'm afraid to say it's one year later and I'm having the same issue as these guys...

I'm using ndiswrapper 1.43, and have a fresh install of Ubuntu Fiesty, but I just can't get the TL-WN620G to create an interface!

I have installed ndiswrapper, and installed the latest drivers (in fact I've done reinstalls of the entire OS and tried older drivers too), and I still don't get a wlan0 or ath0 interface.

When I try ndiswrapper -l it gives:

athfmwdl: driver installed
device (0CF3:0002) present

net5523: driver installed
device (0CF3:0002) present

So the system knows the USB wireless adapter is there, and it knows how to use it, but it doesn't give me an interface to use.
The link light on the device starts flashing when I fire it up with modprobe ndiswrapper, but no amount of ejecting/reinserting/rebooting seems to help.

I know people have this TL-WN620G device working, but I'm afraid I might be too much of a n00b.
If anyone can give me a hand, I'd be really grateful!

---

### Post by stchman on 2007-05-11
> **tukster said:**
> hello
has anyone been able to make it work?
as i understand madwifi doesn't support usb dongles.

mine is TP-Link wn260g.




so ubuntu doesn't even recognize it as network device :confused:
ndiswrapper can be made to install a win driver. but the wlan0 doesn't appear in networking settings panel (nor in iwlist).

anyone here knows how to make it work???

Yes, you are correct madwifi does not support USB devices.  I am going to assume this is a laptop.  I would get a PCMCIA wireless card.  Feisty supports them very well and if not you can make the madwifi drivers.

---

### Post by Dino Rastoder on 2007-06-07
[LIST]
[*]Ubuntu 7.04
[*]TP-Link TL-WN620G USB Wireless card
[/LIST]
I have the same problem. I solved it doing this:
**_[COLOR="Red"]1. Installation of NdisWrapper[/COLOR]_**
    *1.1. Requirements for NdisWrapper*
```
$: sudo apt-get update
$: sudo apt-get install build-essential
$: sudo apt-get install linux-headers-`uname -r`
```
    *1.2. Download & compile NdisWrapper-a*
```
$: wget http://heanet.dl.sourceforge.net/sourceforge/ndiswrapper/ndiswrapper-1.45.tar.gz
$: tar -xzvf ndiswrapper-1.41.tar.gz
$: cd ndiswrapper-1.41/
$: sudo make uninstall
$: make
$: sudo make install
```
**_[COLOR="Red"]2.Installation of  TL-WN620G[/COLOR]_**
   *2.1. Requirements for drivers*
You have to copy drivers to your desktop. You can find it [here](http://www.tp-link.com/product/download/Driver_Utility/TL-WN620G_060614.zip)
Copy to folder  *wi-fi*.
   *2.2. Installation of drives*
Move to folder with drivers:
```
$ cd wi-fi
```Drivers installing:
```
$ ndiswrapper -i TL-WN620G.inf
$ ndiswrapper -i athfmwdl.inf
$ sudo ndiswrapper -m
$ sudo modprobe ndiswrapper
```
To check is everything OK
```
$ ndiswrapper -l
```

---

### Post by enator on 2008-01-23
Anybody know how to do it ? I have the same driver and problem like sorairo  :(

---

### Post by olddave on 2008-03-08
Hi all i no this is an old post but just installed ubuntu on a old laptop, Trying to get wireless usb modem working followed the instructions given by Dino Rastoder and the out put i get dave@dave-laptop:~/wifi$ ndiswrapper -l
athfmwdl : invalid driver!
tl-wn620g : invalid driver!
can any one tell me how to get this working.
Thanks olddave

---

