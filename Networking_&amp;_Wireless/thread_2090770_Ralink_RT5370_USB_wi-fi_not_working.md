---
title: "Ralink RT5370 USB wi-fi not working"
date: 2012-12-03
forum: Networking &amp; Wireless
---

### Post by triugan on 2012-12-03
New to Linux/Ubuntu.
* I have just spent 4+ hours trying to get a wi-fi adapter working without success. 
* I was shocked the driver was not "double-click and *off-you-go*" like Windows.
* I've have gone from knowing zero to learning the basics fast, but I'm still way out of my element.

**The details**
**lsusb ** nearly always doesn't show the attached wi-fi USB. When it did show it (just twice, randomly) it had this info in the ID field:
~~~~~~~~~~~~~~~
*ID 148f:5370 Ralink Technology, Corp.*


USB ports and wi-fi adapter both worked fine under XP; it's definitely not a hardware problem. So anyway, right now **lsusb **is not showing any adapter connected (and nearly always doesn't show the adapter connected to USB).

**uname -r**
~~~~~~~~~~~~~~~~
*3.2.0-29-generic-pae*
~~~~~~~~~~~~~~~~


Ralink RT5370 driver has been downloaded
[http://www.ralinktech.com/en/04_support/license.php?r=5016&sn=5016](http://www.ralinktech.com/en/04_support/license.php?r=5016&sn=5016)
...after agreeing to their terms here.

I have extracted it to the desktop and renamed the folder to *RT5370*. I have gone inside this folder: 
~~~~~~~~~~~~~~~~
*Desktop/RT5370/os/linux*



I have opened **config.mk** here and set two lines to y (yes):
~~~~~~~~~~~~~~~~~
[I]HAS_WPA_SUPPLICANT_SUPPORT=y
HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y[/I]

If somebody can explain why the user has to do this in 2012, I'd appreciate it. WPA is not built-in or enabled...why? I've also followed some makefile instructions in another thread but I'm in **way over my head** and there are too many threads from years ago which I'm not sure are still relevant. Regardless, the wi-fi adapter still isn't working.

**Please help me get this wireless adapter working. **
I need very basic and deliberate instructions if possible. I'm not afraid to do what I have to do as long as it's explained clearly and/or assumes no prior knowledge.

Thanks so much for any hints.

---

### Post by chili555 on 2012-12-03
> If somebody can explain why the user has to do this in 2012, I'd appreciate it. WPA is not built-in or enabled...why? Not managed by Network Manager, no. Because not every Linux distribution uses or includes NM, Ubuntu Server Edition for example. Not every user wants or needs NM, and especially NM to manage wpa_supplicant, even if it *is* included; my wife removes it immediately. She's a daredevil.

Any competent driver you download and compile from source is written to try to work with Suse, Mandriva, Ubuntu, LFS, Debian, CentOS, the wacky kids at Gentoo and many more. They do not all work exactly the same. Some customization, known in my part of the country as whittling, is required.

Let's get it installed. First, make sure the prerequisites are installed:```
sudo apt-get install linux-headers-generic build-essential
```Now, let's compile the driver:```
cd Desktop/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.3_DPO  [COLOR="Red"]<--or wherever you downloaded and extracted the package[/COLOR]
sudo su
make
make install
modprobe rt5370sta
exit
```Your wireless should be working.

---

### Post by triugan on 2012-12-03
Hi Chili555
Thanks for responding.

Re: the first step.

The machine can't be connected to the net unfortunately. All I can do is transfer any important files to the machine manually (via another computer which is connected to the net). 

Is there something I should be looking for?

**Sidenote**
I just totally re-installed Ubuntu 12.0.4 and what's really bizarre is the adapter is detected during setup and asks if I want to connect to local networks it sees (neighbours) but basically is not working after that initial stage. Truly odd...

Anyway, if I should be looking for some particular files I need, please let me know where I can find them. Thanks!

---

### Post by chili555 on 2012-12-03
> I just totally re-installed Ubuntu 12.0.4 and what's really bizarre is the adapter is detected during setup and asks if I want to connect to local networks it sees (neighbours) but basically is not working after that initial stage. Truly odd...Odd, indeed! Can you please run the install CD live; that is, 'Try Ubuntu' and run this terminal command:```
lshw -C network
```You will see two listings, one for ethernet and one for wireless. Look under wireless and note the driver. Here is a sample from my computer:> *-network
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       <snip> ethernet physical wireless
       configuration: broadcast=yes [COLOR="Red"]driver=iwl3945[/COLOR] driverversion=3.5.0-18-generic firmware=15.32.2.9 ip=192.168.1.8 latency=0 multicast=yes wireless=IEEE 802.11abg
       resources: irq:47 memory:edf00000-edf00fff
We are interested in what driver works live but not installed. We suspect rt2800usb.

---

### Post by triugan on 2012-12-03
double post

---

### Post by triugan on 2012-12-03
Chili555, 
I did what you said (run the thing as a LiveCD) and it only seems to detect my onboard (non-wireless) nic (Realtek). 

Did that command both with and without **sudo **preceding it. However, during normal setup it definitely detects the wireless adapter (the only one on this system). 

Anyway, the results of the command:

```
ubuntu@ubuntu:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 1
       bus info: pci@0000:05:01.0
       logical name: eth0
       version: 10
       serial: (snipped)
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=64 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10Mbit/s
       resources: irq:21 ioport:2000(size=256) memory:d0000800-d00008ff
```

---

### Post by chili555 on 2012-12-03
On your installed partition, please run:```
modinfo rt2800usb | grep 5370
```Hopefully, you will see something like this:> $ modinfo rt2800usb | grep 5370
alias:          usb:v148Fp[COLOR="Red"]5370[/COLOR]d*dc*dsc*dp*ic*isc*ip*If so, that indicates that the already installed driver rt2800usb supports your device. > ID [COLOR="Red"]148f:5370[/COLOR] Ralink Technology, Corp.If that's the case, let's load it and see what happens:```
sudo modprobe rt2800usb
iwconfig
sudo iwlist wlan0 scan
```Thanks.

---

### Post by triugan on 2012-12-04
Thanks so much for your help. 

```
usb:v148Fp5370d*dc*dsc*dp*ic*isc*ip* 
```
Done. This is exactly what I get. 

> If so, that indicates that the already installed driver rt2800usb supports your device. 
Great.

```
sudo modprobe rt2800usb
```
I'm asked to enter my password. I enter it. Then I am returned to the login prompt again, like usual. I assume something has been done in the background.

```
iwconfig
```
Here is what I get:
```
lo        no wireless extensions.

wlan1     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          
eth0      no wireless extensions.

rename3   IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
```

It's Wlan1 instead of wlan0 because I since I last wrote I've been playing with another wi-fi adapter to see if it works. Apparently when it's disconnected it's been renamed to "rename3". I don't know why.

Anyway, I think those results show that the adapter is working judging form the **tx-power**. If that's the case, I found no easy way to scan for networks.

```
sudo iwlist wlan0 scan
```
Interface doesn't support scanning. 

Fair enough. I tried this instead:
```
sudo iwlist **wlan1 **scan
```
No scan results.

If I do: 
```
sudo iwlist rename3 scan
```
I get:
```
Interface doesn't support scanning : Network is down
```
I assume that's because the other adapter has been unplugged with only the Ralink one connected to USB again.

At this point, if I go into **Settings **and then **Network** I see two Wireless instances in the white box on the left. If I click on one it says **Disconnected**. If I click on the other it says **Unavailable**.

Both are marked ON with the orange-background ON switch. Airplane mode is marked as OFF with the grey background.

There appears to be no easy way (or obvious way) to scan for networks in a GUI-type thing, too.

Thanks again for your help. I hope I can get this going.

---

### Post by chili555 on 2012-12-04
Oh, my!! This is my most interesting thread so far this month. Fascinating.

It is clear to see that there are some conflicts going on here. Please decide which wireless device you want to try to coax to life and put the other in the drawer in the garage because we are going to try to restore sanity and order to your setup by deleting a number of settings. When you have decided and placed the non-starter far away, please insert your favorite and post:```
lsusb
cat /etc/network/interfaces
cat /etc/udev/rules.d/70-persistent-net.rules
dmesg | grep -e wlan -e rename -e rt2
cat /etc/NetworkManager/NetworkManager.conf
```Whew!

---

### Post by triugan on 2012-12-04
> When you have decided and placed the non-starter far away, please insert your favorite and post:
Ralink 5370 nightmare is ready and waiting ;) 

Restarted computer since then. No wireless devices showing up under **Settings  > Network** despite Ralink being plugged in.

**lsusb**
```
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

**cat /etc/network/interfaces**
```
auto lo
iface lo inet loopback
```


**dmesg | grep -e wlan -e rename -e rt2**
When inputtting this I get returned to the prompt. I assume something is done in the background.


**cat /etc/NetworkManager/NetworkManager.conf**
```

[main]
plugins=ifupdown,keyfile
dns=dnsmasq

no-auto-default=00:00:00:00:00:00,

[ifupdown]
managed=false
```

Mac ID listed normally but blanked with zeroes here.
Thanks again for your help.

---

### Post by chili555 on 2012-12-04
> dmesg | grep -e wlan -e rename -e rt2
When inputtting this I get returned to the prompt. I assume something is done in the background.Yes. The current message log was read and any instances of the pattern 'wlan' or 'rename' or 'rt2' were printed in the terminal. In this case, there are none and so none were printed. In many cases, not only are the specific messages informative, but absence is informative as well. It tells us the driver rt2800usb didn't load automagically. I wonder if you have blacklisted it. Let's load it and see what happens:```
sudo modprobe rt2800usb
iwconfig
dmesg | grep -e wlan -e rt2
```Now we hope we see some clues as to why rt2800usb is not performing as expected.

---

### Post by triugan on 2012-12-05
FWIW, I haven't blacklisted anything, though I did try some of that on my first Ubuntu install a few days ago (before losing my mind). Anyway, this is a completely new installation done from scratch and I haven't tried to even install the Ralink driver on it (I wonder if I could?), let alone anything else. 


**sudo modprobe rt2800usb**
asks for password; I input password then returns me to the prompt

**iwconfig**
```
lo        no wireless extensions.

eth0      no wireless extensions.
```

**dmesg | grep -e wlan -e rt2**
```
[  171.006461] usbcore: registered new interface driver rt2800usb
```

Thanks again.

---

### Post by chili555 on 2012-12-05
Weird! Are you sure the Ubuntu version you re-installed includes your device in rt2800usb? Please check again:```
lsusb
modinfo rt2800usb | grep 5370
```Thanks.

---

### Post by triugan on 2012-12-05
I'm using ubuntu 12.04 LTS (according to System > Details). I'm using the gnome interface (I think! ... I'm not crazy about the interface), x86 version. Nothing added or changed.

**lsusb**
```
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

**modinfo rt2800usb | grep 5370**
I get:
```
alias:          usb:v148Fp5370d*dc*dsc*dp*ic*isc*ip*
```

---

### Post by chili555 on 2012-12-05
> Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hubIsn't your wireless device inserted?

---

