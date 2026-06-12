---
title: "Can't get my wireless usb adapter to work in Ubuntu 10.04. :("
date: 2011-12-19
forum: Networking &amp; Wireless
---

### Post by SilentIdea on 2011-12-19
Hey guys,

I have just installed Ubuntu 10.04 and am struggling to connect to the internet via my wireless usb adapter.

My adapter is a Realtek RTL8188CU Wireless Lan 802.11n USB 2.0 Network Adapter. I am currently using it to connect to the internet (wireless) in Win7.

I have downloaded the driver rtl8192sfw.bin.

I placed this file in Home Folder in Ubuntu. Then entered the commands:-

sudo mkdir /lib/firmware/RTL8192SU

sudo cp  /lib/firmware/RTL8192SU

in terminal.

I then removed the usb and inserted it again, nothing happened. :(

Please, Please can someone help me?! Many Thanks!
Silent. x

---

### Post by chili555 on 2011-12-19
> sudo cp /lib/firmware/RTL8192SUI'm not sure that's going to do it. Let's see:```
ls /lib/firmware/RTL8192SU
lsusb
dmesg | grep 819
```The pipe symbol | is on the right side of my US keyboard on the same key with \. Thanks.

---

### Post by SilentIdea on 2011-12-19
> **chili555 said:**
> I'm not sure that's going to do it. Let's see:```
ls /lib/firmware/RTL8192SU
lsusb
dmesg | grep 819
```The pipe symbol | is on the right side of my US keyboard on the same key with \. Thanks.

```
apostolis@ubuntu:~$ ls /lib/firmware/RTL8192SU
rtl8192sfw.bin
apostolis@ubuntu:~$ lsusb
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 004: ID 413c:2106 Dell Computer Corp. 
Bus 002 Device 003: ID 046d:c068 Logitech, Inc. 
Bus 002 Device 002: ID 8087:0024  
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 0bda:8176 Realtek Semiconductor Corp. 
Bus 001 Device 003: ID 05dc:a701 Lexar Media, Inc. JumpDrive FireFly
Bus 001 Device 002: ID 8087:0024  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
apostolis@ubuntu:~$ dmesg | grep 819
[    0.000000] PERCPU: Embedded 30 pages/cpu @ffff88002c200000 s91864 r8192 d22824 u524288
[    0.000000] pcpu-alloc: s91864 r8192 d22824 u524288 alloc=1*2097152
apostolis@ubuntu:~$ 


```

Any ideas? :( Thankyou!

---

### Post by chili555 on 2011-12-19
The correct driver for your card is rtl8192cu which is not yet on your system as of 10.04. We have two alternatives. First, download and burn the live CD for 11.10. The driver is there and your device should spring to life. If everything else is working, install 11.10.

Second, we could download and install the package from Realtek, as well as all the compiling tools. Compiling form source is tricky but do-able. If you decide this is your choice, it will be a lot easier with a working ethernet connection. Is that available?

What would you like to try?> I have downloaded the driver rtl8192sfw.bin.This is only the firmware; not the driver.

---

### Post by SilentIdea on 2011-12-19
> **chili555 said:**
> The correct driver for your card is rtl8192cu which is not yet on your system as of 10.04. We have two alternatives. First, download and burn the live CD for 11.10. The driver is there and your device should spring to life. If everything else is working, install 11.10.

Second, we could download and install the package from Realtek, as well as all the compiling tools. Compiling form source is tricky but do-able. If you decide this is your choice, it will be a lot easier with a working ethernet connection. Is that available?

What would you like to try?This is only the firmware; not the driver.

Damn I don't have access to an ethernet cable is there a way where I could download everything I need in Win7 then transfer them via USB to Ubuntu?

How good is the latest version of Ubuntu? I'm only at this version because someone recommended this version over the latest one.

Thanks for all your help btw! :)

---

### Post by chili555 on 2011-12-19
I think the latest is the best. It uses the controversial Unity desktop, but you could download kubuntu 11.10 that uses KDE.> is there a way where I could download everything I need in Win7 then transfer them via USB to Ubuntu?It's tough but do-able. It would be a lot longer and harder than 11.10, in my opinion. I'll be glad to help in either case.

[http://unity.ubuntu.com/about/](http://unity.ubuntu.com/about/)

[http://www.techrepublic.com/blog/opensource/gnome-shell-vs-ubuntu-unity-which-desktop-wins/2291](http://www.techrepublic.com/blog/opensource/gnome-shell-vs-ubuntu-unity-which-desktop-wins/2291)

---

### Post by SilentIdea on 2011-12-19
> **chili555 said:**
> I think the latest is the best. It uses the controversial Unity desktop, but you could download kubuntu 11.10 that uses KDE.It's tough but do-able. It would be a lot longer and harder than 11.10, in my opinion. I'll be glad to help in either case.

[http://unity.ubuntu.com/about/](http://unity.ubuntu.com/about/)

[http://www.techrepublic.com/blog/opensource/gnome-shell-vs-ubuntu-unity-which-desktop-wins/2291](http://www.techrepublic.com/blog/opensource/gnome-shell-vs-ubuntu-unity-which-desktop-wins/2291)

Ahhh, I'm just going to go for the latest version. So if I install this it will recognize my usb adapter straight away etc?

Thankyou for your help! :)

---

### Post by chili555 on 2011-12-19
It certainly should. You might need to grab the correct firmware file; it now goes in /lib/firmware/rtlwifi. If it isn't included by default, I can supply it.```
chili@LAPTOP60:~$ modinfo rtl8192cu
filename:       /lib/modules/3.0.0-14-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192cu/rtl8192cu.ko
[COLOR="Red"]firmware:       rtlwifi/**rtl8192cufw.bin**[/COLOR]
description:    Realtek 8192C/8188C 802.11n USB wireless
license:        GPL
author:         Larry Finger	<Larry.Finger@lwfinger.net>
author:         Ziv Huang	<ziv_huang@realtek.com>
author:         Georgia		<georgia@realtek.com>
srcversion:     6CDAA0F2DC1FD3297EBA8A6
<snip>
alias:          usb:v[COLOR="Red"]0BDA[/COLOR]p[COLOR="Red"]8176[/COLOR]d*dc*dsc*dp*ic*isc*ip*
<snip>
depends:        rtlwifi,mac80211,rtl8192c-common
vermagic:       3.0.0-14-generic SMP mod_unload modversions 686 
```

---

