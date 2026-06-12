---
title: "Ubuntu 11.04 Wireless network is very slow"
date: 2011-04-24
forum: Networking &amp; Wireless
---

### Post by joaopr on 2011-04-24
Hello Guys.
I'm using the Ubuntu 11.04 Beta 2(unity) with a USB Wireless adapter Tenda W311U.
My wireless connection is very slow in Ubuntu 11.04, i tried to disconnect and reconnect, but the issue persist.
The W311U in the Windows 7 is working properly.

Could you help me what i need to do to fixed it ?
Thanks a lot !!

---

### Post by majorawesome on 2011-04-24
Go into firefox and type about:config in the address bar. once there look for
```
network.dns.disableIPv6
```
set that value to true exit and reboot then walla!

---

### Post by joaopr on 2011-04-24
Yes, i checked the Firefox and is OK.
Sorry, my problem is happing in the Ubuntu network wireless, i cannot update the ubuntu or use the internet.
When i tried to use the Update manager, the manager start to download the updates but after few seconds is stopping.
I don't know, the signal in the wireless is full.

---

### Post by conualfy on 2011-04-24
I just upgraded to Ubuntu 11.4 and the problem is still here. There are a lot of threads about the slow WIFI connection under Ubuntu. It's one of the bugs that makes you switch to another OS.

As I think people working on this are having hard time to reproduce the  bug, I can allow some Ubuntu/Linux specialist to connect to my computer  to debug it on this machine. If there is anyone interested, please email  me personally on   florin [at] drumliber [dot] ro

---

### Post by ivanovnegro on 2011-04-24
Till now I did not have luck to connect to wireless with Ubuntu 11.04 Beta, and I have a laptop that is totally open source, funny, I can use whatever OS and it works even here on Kubuntu 11.04 but no way with Ubuntu.

---

### Post by dineshs on 2011-04-25
Pl see if the following link can help.
[http://peppermintos.net/viewtopic.php?f=39&t=311](http://peppermintos.net/viewtopic.php?f=39&t=311)
Note:Instead of sudo leafpad /etc/rc.local you may try sudo gedit /etc/rc.local

---

### Post by JoZ3 on 2011-04-30
I have the same problem with ubuntu 11.04, the wifi is very slow, with 10.10 work fine.

I have a SD-Link System DWA-125 Wireless 150 USB Adapter, and the solution posted by dineshs not work for me :(

---

### Post by thomashsu on 2011-05-01
You should try to install the new wireless driver.

here is the link:

[http://wireless.kernel.org/en/users/Download#Directly_downloading_the_tarball](http://wireless.kernel.org/en/users/Download#Directly_downloading_the_tarball)

make and install the driver as the instruction in above link.

This fixed the wireless issue for me.

---

### Post by shimanotaka on 2011-05-02
> **thomashsu said:**
> You should try to install the new wireless driver.

here is the link:

[http://wireless.kernel.org/en/users/Download#Directly_downloading_the_tarball](http://wireless.kernel.org/en/users/Download#Directly_downloading_the_tarball)

make and install the driver as the instruction in above link.

This fixed the wireless issue for me.

I also use a W311U for my desktop computer and the net has been extremely slow since upgrading to 11.04. It worked fine in 10.10 and my laptop has no network problems running 11.04. I got errors when I tried to build like the instructions suggested. Is there anything more I need to do?

```
user@host:~/Desktop/compat-wireless-2011-05-01$ makemake -C /lib/modules/2.6.38-8-generic-pae/build M=/home/user/Desktop/compat-wireless-2011-05-01 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.38-8-generic-pae'
  CC [M]  /home/user/Desktop/compat-wireless-2011-05-01/drivers/staging/brcm80211/brcmfmac/dhd_sdio.o
/home/user/Desktop/compat-wireless-2011-05-01/drivers/staging/brcm80211/brcmfmac/dhd_sdio.c: In function ‘dhdsdio_sdiod_drive_strength_init’:
/home/user/Desktop/compat-wireless-2011-05-01/drivers/staging/brcm80211/brcmfmac/dhd_sdio.c:6366:3: error: ‘chn’ undeclared (first use in this function)
/home/user/Desktop/compat-wireless-2011-05-01/drivers/staging/brcm80211/brcmfmac/dhd_sdio.c:6366:3: note: each undeclared identifier is reported only once for each function it appears in
make[4]: *** [/home/user/Desktop/compat-wireless-2011-05-01/drivers/staging/brcm80211/brcmfmac/dhd_sdio.o] Error 1
make[3]: *** [/home/user/Desktop/compat-wireless-2011-05-01/drivers/staging/brcm80211/brcmfmac] Error 2
make[2]: *** [/home/user/Desktop/compat-wireless-2011-05-01/drivers/staging/brcm80211] Error 2
make[1]: *** [_module_/home/user/Desktop/compat-wireless-2011-05-01] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.38-8-generic-pae'
make: *** [modules] Error 2

```

---

### Post by errors on 2011-05-02
> **shimanotaka said:**
> I also use a W311U for my desktop computer and the net has been extremely slow since upgrading to 11.04. It worked fine in 10.10 and my laptop has no network problems running 11.04. I got errors when I tried to build like the instructions suggested. Is there anything more I need to do?

```
user@host:~/Desktop/compat-wireless-2011-05-01$ makemake -C /lib/modules/2.6.38-8-generic-pae/build M=/home/user/Desktop/compat-wireless-2011-05-01 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.38-8-generic-pae'
  CC [M]  /home/user/Desktop/compat-wireless-2011-05-01/drivers/staging/brcm80211/brcmfmac/dhd_sdio.o
/home/user/Desktop/compat-wireless-2011-05-01/drivers/staging/brcm80211/brcmfmac/dhd_sdio.c: In function &#8216;dhdsdio_sdiod_drive_strength_init&#8217;:
/home/user/Desktop/compat-wireless-2011-05-01/drivers/staging/brcm80211/brcmfmac/dhd_sdio.c:6366:3: error: &#8216;chn&#8217; undeclared (first use in this function)
/home/user/Desktop/compat-wireless-2011-05-01/drivers/staging/brcm80211/brcmfmac/dhd_sdio.c:6366:3: note: each undeclared identifier is reported only once for each function it appears in
make[4]: *** [/home/user/Desktop/compat-wireless-2011-05-01/drivers/staging/brcm80211/brcmfmac/dhd_sdio.o] Error 1
make[3]: *** [/home/user/Desktop/compat-wireless-2011-05-01/drivers/staging/brcm80211/brcmfmac] Error 2
make[2]: *** [/home/user/Desktop/compat-wireless-2011-05-01/drivers/staging/brcm80211] Error 2
make[1]: *** [_module_/home/user/Desktop/compat-wireless-2011-05-01] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.38-8-generic-pae'
make: *** [modules] Error 2

```

Don't compile all the drivers, select the only one you need, and the compile.
./scripts/driver-select [driver-name] or [driver-group-name]

them run make and install it worked for me to.

Thanks! :D

---

### Post by nospam@sparx on 2011-06-06
Maybe this is an old thread, but this worked for me:

[http://www.hitxp.com/articles/software/ubuntu-fix-slow-wireless-internet-connection-speed-upgrading-11-04-natty-narwhal/](http://www.hitxp.com/articles/software/ubuntu-fix-slow-wireless-internet-connection-speed-upgrading-11-04-natty-narwhal/)

---

### Post by GSF1200S on 2011-06-21
> **JoZ3 said:**
> I have the same problem with ubuntu 11.04, the wifi is very slow, with 10.10 work fine.

I have a SD-Link System DWA-125 Wireless 150 USB Adapter, and the solution posted by dineshs not work for me :(

I had the same problem installing 11.04 tonight- my DWA-125 consistently dropped calls with skype, I noticed very slow resolution with Ubuntu servers (updates, installs), and I noticed that my download speeds seemed pathetic. For us, it turns out this is due to a new driver in use for the DWA-125.

Run:
```
lsmod
```
in a terminal and youll likely see a module named rt2800usb. However, on 10.10, the module is rt2870sta. I fixed it by blacklisting the rt2800usb module- first open the module blacklist file:
```
sudo gedit /etc/modprobe.d/blacklist.conf
```
Then, append the following to the file:
```
blacklist rt2800usb
```
Simply reboot, and it will automatically use rt2870sta. 

If you dont want to reboot, kill X:
Ctrl+Alt+F1, login, and then run:
```
sudo service gdm stop
sudo killall Xorg
sudo rmmod rt2800usb
sudo modprobe rt2870sta
```

I strongly suggest for everyone to run lsmod, and paste the results here in a quote box. A simple google search of the wireless line (mine for instance is D-Link which I immediately recognized as my wireless card manufacturer) will tell you what chipset and module/driver it uses. If you have a DWA-125, the above procedure is your fix..

**EDIT** If you had no issues on 10.10, but suddenly do on 11.04, your issue is likely a wireless driver. A good approach would be to use a 10.10 livecd, boot to desktop, check lsmod to see what modules are loaded, and then compare them with your 11.04 lsmod results. Use lsusb (for usb wireless cards) or lspci (for wireless devices on the PCI bus) to find out what kind of chipset it uses, and combine the relevant line with Ubuntu in a google search to give you the different modules that are used in various Ubuntu releases.

---

### Post by kirkl on 2011-06-23
I have struggled with this for 2 days now, slow wireless after upgrading from 10.10 to 11.4.  I tried all the manual fixes, disabling power management, disabling ipv6, etc.  None of these worked.  In the end, I dragged my unbuntu box into another room where I could make a wired connection and let ubuntu Update Manager perform it's normal update, rebooted and the wireless works like a charm.  My wireless driver is rt61pci.  Hope this helps.

---

