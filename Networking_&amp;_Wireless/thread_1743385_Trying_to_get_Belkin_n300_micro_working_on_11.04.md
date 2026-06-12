---
title: "Trying to get Belkin n300 micro working on 11.04"
date: 2011-04-29
forum: Networking &amp; Wireless
---

### Post by SeanStar on 2011-04-29
So I'm trying to get this to work on ubuntu 11.04.

Belkin n300 micro (Model: F7D2102) 050d:2103
It is a usb adapter.

I never tried to get it to work with ubuntu 10.10, but I'm sure it would probably work with a slight modification.. considering 10.10 comes with the rtl8192su driver which is what I need (I'm pretty sure).

I found a thread on a product very similar to this this: [http://ubuntuforums.org/showthread.php?t=1515747](http://ubuntuforums.org/showthread.php?t=1515747)

Second post has instructions, and I figured I could edit the product id and be fine.. problem is, 11.04 doesn't come with that driver.

I already tried ndiswrapper to no avail.
Using ndiswrapper, I'm able to see networks, but when I try to connect to my home network (It has WEP), it doesn't work.

Any ideas?

---

### Post by SeanStar on 2011-04-29
Bump? Anyone?

---

### Post by psychetician on 2011-04-30
I'm having the same problem.  I'll try looking elsewhere, but thought I'd add my voice to the clamor here.

---

### Post by yedidyah on 2011-05-29
I would like to third the issue (except on Lucid).

---

### Post by dabl on 2011-08-10
I have been working with a couple of Debian developers on this device, which I was trying to get working on a Debian (sid) system.

[http://ircbots.debian.net/factoid.php?key=f7d2102](http://ircbots.debian.net/factoid.php?key=f7d2102)

The driver is rtl8192cu -- it has been introduced in kernel 2.6.39 and 3.0.  You have to install the Realtek firmware (in Debian the package name is "firmware-realtek". With the firmware installed, the driver should load automatically, and also pulls in the rtlwifi module.  This much is working correctly on my 32-bit Debian installation -- it scans and detects available routers, shows signal strength and encrytion status, etc.

However, a bug remains which prevents the device from authenticating with my wireless router, (and my neighbor's also), even when running with no encryption.  Not sure whether the problem is software or firmware. So we are waiting for the bug to be fixed, then with kernel 2.6.39 or later, it should work.

FYI.

---

### Post by StApnea on 2011-10-13
I got an n300 micro to work under ndiswrapper using the XP driver.

---

### Post by FireFighter on 2011-10-27
StApnea, how well does it perform? Was it hard to get it working? I have an old Toshiba laptop and am looking at this adapter. Using Ubuntu 10.04LTS at the present time.

---

### Post by praseodym on 2011-10-27
Hi,

this stick works with the native driver, if the firmware is copied to the right place:

```
sudo mkdir /lib/firmware/RTL8192SU
sudo cp /lib/firmware/RTL8192SE/rtl8192sfw.bin /lib/firmware/RTL8192SU/ 
```
If ndiswrapper was used before, uninstall it completely:


```
sudo modprobe -rf ndiswrapper
sudo apt-get remove --purge ndiswrapper-common ndiswrapper-utils-1.9 ndisgtk
sudo rm /etc/modprobe.d/ndiswrapper.conf
sudo rm -r /etc/ndiswrapper/* 
sudo depmod -a
sudo update-initramfs -u
```

and reboot.

Driver installation/actualisation:

## Installing the compilation tools:

```
sudo apt-get install --reinstall linux-headers-$(uname -r) build-essential dkms
```

## until Ubuntu 11.04
```
wget http://media.cdn.ubuntu-de.org/forum/attachments/2844083/rtl8192cu-3.1.2590_dkms.tar.gz
sudo tar xvf rtl8192cu-3.1.2590_dkms.tar.gz -C /usr/src
```

## for Ubuntu 11.10
```
wget http://media.cdn.ubuntu-de.org/forum/attachments/2844083/rtl8192cu-3.1.2590_11.10_dkms.tar.gz
sudo tar xvf rtl8192cu-3.1.2590_11.10_dkms.tar.gz -C /usr/src
```

## Installation with dkms
```
sudo dkms add -m rtl8192cu -v 3.1.2590
sudo dkms build -m rtl8192cu -v 3.1.2590
sudo dkms install -m rtl8192cu -v 3.1.2590
sudo depmod -a
```
## Load the module:

```
sudo modprobe rtl8192cu
```
and replug the stick.

You should install the **metapackage** of the kernel headers (e.g. **linux-headers-generic** or **linux-headers-generic-pae** or ... whatever "uname -r" shows you). The driver will **then** be build automatically if the kernel is upgraded.

---

### Post by FireFighter on 2011-10-27
Whew, that looks a little difficult. I understand until I get to this part:

Driver installation/actualisation:

## Installing the compilation tools:

Code:

sudo apt-get install --reinstall linux-headers-$(uname -r) build-essential dkms

## until Ubuntu 11.04
Code:

wget [http://media.cdn.ubuntu-de.org/forum/attachments/2844083/rtl8192cu-3.1.2590_dkms.tar.gz](http://media.cdn.ubuntu-de.org/forum/attachments/2844083/rtl8192cu-3.1.2590_dkms.tar.gz)
sudo tar xvf rtl8192cu-3.1.2590_dkms.tar.gz -C /usr/src

## for Ubuntu 11.10
Code:

wget [http://media.cdn.ubuntu-de.org/forum/attachments/2844083/rtl8192cu-3.1.2590_11.10_dkms.tar.gz](http://media.cdn.ubuntu-de.org/forum/attachments/2844083/rtl8192cu-3.1.2590_11.10_dkms.tar.gz)
sudo tar xvf rtl8192cu-3.1.2590_11.10_dkms.tar.gz -C /usr/src

## Installation with dkms
Code:

sudo dkms add -m rtl8192cu -v 3.1.2590
sudo dkms build -m rtl8192cu -v 3.1.2590
sudo dkms install -m rtl8192cu -v 3.1.2590
sudo depmod -a

## Load the module:

Code:

sudo modprobe rtl8192cu

and replug the stick.

(Just an old country boy here!)

I guess you are saying that I have to re-compile the kernel to get this to work. I have been using ndiswrapper for a card that went out on me. Do I still need to remove it even though it was not used for this device? No problem if I have to, just asking

Thanks!

---

### Post by praseodym on 2011-10-27
No, only ndiswrapper is uninstalled and the driver for the stick is compiled. Ndiswrapper and native (other) drivers dont work properly in parallel

---

### Post by Unterseeboot_234 on 2011-10-27
I built ndiswrapper for Natty (11.04),it worked with the N300 and using the supplied CD driver on a single-core AMD64. The adapter would not work on a hexacore AMD64 Natty, yet works fine with Win7.

I noticed ndiswrapper is like a zombie. I reformatted the single-core AMD; and re-installed Natty; my settings persisted. After about 30 days Natty became unstable. I tried Ocelot as a clean install. Again my networks were still available for selection, I had to type in the serial number to join the LAN. But essentially the N300 was plug-n-play. Ocelot has ndiswrapper included.

Not sure if my twiddling prior to Ocelot has anything to do with the N300 working.

I dread Ubuntu upgrades to Ocelot.

I look forward to re-formatting the multi-core AMD64, installing Ocelot, and see if I have the same success. The hexacore is an office machine and the workers very much prefer Ubuntu over Win, but all have since gone over to Win7 boots while I sort out wireless issues.

One other thing, I have a tower box. The N300 works only with the front-panel USB. My guess is: RFI garbles the adapter in the rear panel.

---

### Post by shalamigri on 2011-11-12
Seanstar, thanks for starting this thread and praseodym, thanks for the detailed info on getting this device to work.

My adapter is now reporting 300 mb/s.

I had to search on updating kernel headers, but it was a snap and after rebooting my pc, the adapter was recognized.

Thanks again.

---

### Post by praseodym on 2011-11-13
You should install the metapackage of the kernel headers (e.g. linux-headers-generic, depends on the kernel). The headers will then be updated automatically

---

### Post by Buckwheat469 on 2011-12-18
On Ubuntu 11.10, Linux 3.0.0-14-generic, the Belkin n300 works out of the box. I give it 5 stars, very happy. This is my second attempt at a USB wireless N adapter. The Linksys/Cisco ae2500 didn't work, while the Belkin n300 just works without any configuration issues.

dmesg:


```
[205626.756562] usb 1-1.3: new high speed USB device number 5 using ehci_hcd
[205626.944334] r8712u: module is from the staging directory, the quality is unknown, you have been warned.
[205626.945938] r8712u: DriverVersion: v7_0.20100831
[205626.945953] r8712u: register rtl8712_netdev_ops to netdev_ops
[205626.945956] r8712u: USB_SPEED_HIGH with 4 endpoints
[205626.946429] r8712u: Boot from EFUSE: Autoload OK
[205627.346264] r8712u: CustomerID = 0x0000
[205627.346269] r8712u: MAC Address from efuse = 94:44:52:da:79:f1
[205627.346731] usbcore: registered new interface driver r8712u
[205627.420466] r8712u: Loading firmware from "rtlwifi/rtl8712u.bin"
[205628.076069] r8712u: 1 RCR=0x153f00e
[205628.076816] r8712u: 2 RCR=0x553f00e
[205628.185763] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[205697.510659] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[205697.733019] r8712u: [r8712_got_addbareq_event_callback] mac = 00:23:69:03:88:c3, seq = 32, tid = 0
[205707.775821] wlan0: no IPv6 routers present
```

ifconfig (MAC and IPv6 addresses removed):


```
wlan0     Link encap:Ethernet  HWaddr xx:xx:xx:xx:xx:xx  
          inet addr:192.168.1.106  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: ffff::ffff:ffff:ffff:ffff/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:10 errors:0 dropped:29 overruns:0 frame:0
          TX packets:41 errors:0 dropped:2 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2376 (2.3 KB)  TX bytes:13183 (13.1 KB)

```

---

### Post by clueblue on 2011-12-21
Thank you, praseodym.  You're off the chain, mate! Works on KDE Platform Version 4.7.3 (4.7.3)  - Tommy

---

### Post by cptrohn on 2012-01-06
> **Buckwheat469 said:**
> On Ubuntu 11.10, Linux 3.0.0-14-generic, the Belkin n300 works out of the box. I give it 5 stars, very happy. This is my second attempt at a USB wireless N adapter. The Linksys/Cisco ae2500 didn't work, while the Belkin n300 just works without any configuration issues.

dmesg:


```
[205626.756562] usb 1-1.3: new high speed USB device number 5 using ehci_hcd
[205626.944334] r8712u: module is from the staging directory, the quality is unknown, you have been warned.
[205626.945938] r8712u: DriverVersion: v7_0.20100831
[205626.945953] r8712u: register rtl8712_netdev_ops to netdev_ops
[205626.945956] r8712u: USB_SPEED_HIGH with 4 endpoints
[205626.946429] r8712u: Boot from EFUSE: Autoload OK
[205627.346264] r8712u: CustomerID = 0x0000
[205627.346269] r8712u: MAC Address from efuse = 94:44:52:da:79:f1
[205627.346731] usbcore: registered new interface driver r8712u
[205627.420466] r8712u: Loading firmware from "rtlwifi/rtl8712u.bin"
[205628.076069] r8712u: 1 RCR=0x153f00e
[205628.076816] r8712u: 2 RCR=0x553f00e
[205628.185763] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[205697.510659] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[205697.733019] r8712u: [r8712_got_addbareq_event_callback] mac = 00:23:69:03:88:c3, seq = 32, tid = 0
[205707.775821] wlan0: no IPv6 routers present
```

ifconfig (MAC and IPv6 addresses removed):


```
wlan0     Link encap:Ethernet  HWaddr xx:xx:xx:xx:xx:xx  
          inet addr:192.168.1.106  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: ffff::ffff:ffff:ffff:ffff/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:10 errors:0 dropped:29 overruns:0 frame:0
          TX packets:41 errors:0 dropped:2 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2376 (2.3 KB)  TX bytes:13183 (13.1 KB)

```

Yours worked out of the box?If you don't mind would you post the sn of the usb device?  Mine is a Belkin F9L100v1 that I just bought today  and it isn't recognized by ubuntu for me... I am wondering if mine might have a different firmware version or chipset.    I am curious as to why mine isn't working, a co worker also told me he had one and it was recognized by ubuntu in this kernel as well...   My device is working in my Win7Pro partition so it's not a bad device..

---

### Post by Buckwheat469 on 2012-01-06
Model F7D2101 v1, sn 12104212112726 (I think?)

---

### Post by cptrohn on 2012-01-09
> **Buckwheat469 said:**
> Model F7D2101 v1, sn 12104212112726 (I think?)

Ok, thanks a lot for taking the time to do that....  It's odd for me I guess because mine isn't recognized in just a straight Ubuntu 11.10 version, but I fired up a liveUSB of Kubuntu 11.10 and it was recognized....  So thinking it might be the kernel upgrade in 11.10 I went ahead and installed kubuntu 11.10 just to see for myself if that was the isseu and it still worked after the kernel upgrade....  Just a little odd that it wouldn't work at all (or even be recognized in the stock Ubuntu 11.10 and it is in K..)

Oh well I am rambling now lol, but thanks much for that,

---

### Post by RickDanger on 2012-01-11
I can't get this adapter to work either. I just downloaded the latest Ubuntu ISO and installed it, did all the updates and installed linux-headers-generic (I have 3.0.0-14-generic installed).

'lsusb' I get;

> Bus 001 Device 002: ID 050d:2103 Belkin Components 

But 'ifconfig -a' doesn't show it and 'ifconfig wlan up' gives me the message

> wlan: ERROR while getting interface flags: No such device

What should I try next?

---

### Post by Buckwheat469 on 2012-01-11
> What should I try next?

Do you see anything out of the ordinary when you use dmesg? Note the driver version that I'm using. You may not have this driver available:

```
r8712u: module is from the staging directory, the quality is unknown, you have been warned.
[205626.945938] r8712u: DriverVersion: v7_0.20100831
```

---

### Post by HiGhLaNdR on 2012-01-19
Any1 got this to work?
It worked before I upgraded to the latest kernel 3.0.0-14-generic ...
After the upgrade I get this error:
 
8192cu: disagrees about version of symbol filp_open
8192cu: Unknown symbol filp_open (err -22)
 
Any ideias?

---

### Post by praseodym on 2012-01-19
How did you install the driver? Manually? Or is it the default one?

---

### Post by HiGhLaNdR on 2012-01-19
Manually. Used your suggestion in the first page of this thread.
It worked after the Ubuntu installation but when I did the software upgrade it stopped working giving me that error. I guess it has something todo with the new kernel ...


Solved:
Reinstalled the Ubuntu, made the updates and compiled your "stuff".
I guess that a cleanup of your suggestion and a re-compile of the driver would do the job.
Thanks!!

---

### Post by sosaudio1 on 2012-02-01
> **HiGhLaNdR said:**
> Manually. Used your suggestion in the first page of this thread.
It worked after the Ubuntu installation but when I did the software upgrade it stopped working giving me that error. I guess it has something todo with the new kernel ...


Solved:
Reinstalled the Ubuntu, made the updates and compiled your "stuff".
I guess that a cleanup of your suggestion and a re-compile of the driver would do the job.
Thanks!!

OK Reinstalled Ubuntu did the instructions...Can see the network...it won't authenticate. 

Changed router security to WPA2 AES only....no change...can see activity on the USB Micro ie LED is working. ifconfig shows it as up but it won't connect....I have been having some problems with the router but most of my other hardware has been connecting to it. Is there anything I need to rule out on the computer side? I want to make sure I can say...yes...this is the problem of the router or, I need to adjust a setting here or there to make it work.

FYI:
Ubuntu 11.10 64 Bit
Latest kernel 3.0.0.15 
Belkin n300 Micro USB adapter


Thanks
Rich

---

### Post by Buckwheat469 on 2012-02-02
Try open authentication on your router temporarily. At one point in time the Atheros drivers (not related to our issue but still a valid test) that encrypted connections wouldn't work but open connections would.

Try a different wireless router and see if you have the same problems. I've found that some DLink an Netgear routers work differently than Linksys/Cisco routers.

If there's a Windows 7 machine on the wireless network be sure to disable IPv6 on it. Some routers don't support the way Windows 7 authenticates with IPv6 and will kick off all other authenticated machines while authenticating the Windows 7 machine.

---

### Post by sohlinux on 2012-09-05
> **Buckwheat469 said:**
> Try open authentication on your router temporarily. At one point in time the Atheros drivers (not related to our issue but still a valid test) that encrypted connections wouldn't work but open connections would.

Try a different wireless router and see if you have the same problems. I've found that some DLink an Netgear routers work differently than Linksys/Cisco routers.

If there's a Windows 7 machine on the wireless network be sure to disable IPv6 on it. Some routers don't support the way Windows 7 authenticates with IPv6 and will kick off all other authenticated machines while authenticating the Windows 7 machine.

I dont see what the router has to do with it, its the same on my other router too, and its only in ubuntu not in windows, anyway it works if I leave the wireless switch turned on so its ok for now.

---

