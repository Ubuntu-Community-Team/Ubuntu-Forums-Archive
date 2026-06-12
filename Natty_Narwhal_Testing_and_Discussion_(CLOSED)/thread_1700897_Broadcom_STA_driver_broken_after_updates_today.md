---
title: "Broadcom STA driver broken after updates today"
date: 2011-03-05
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Rifester on 2011-03-05
Broadcom 4312 wireless card working with STA driver is not functioning after updates today.  Tried un-installing the driver and re-installing, no luck.   Any suggestions?

Thanks!

---

### Post by wojox on 2011-03-05
A temporary work around may be to install [b43-fwcutter]("http://www.linuxwireless.org/en/users/Drivers/b43?action=show&redirect=en%2Fusers%2FDrivers%2Fbcm43xx#devicefirmware").

I prefer those over the official STA.

---

### Post by donniezazen on 2011-03-05
Welcome to the club no internet. Broadcom STA has been broken for my system since alpha1. Fw-cutter disconnects after every 5 minutes. Hope it works for you. I had filed bug report but no luck yet.

[https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/712053](https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/712053)

---

### Post by tjeremiah on 2011-03-06
this is going to be a huge problem for many come final release when they update to 11.04. I've managed to get mines to 'work' by installing the appropriate kernel (check my thread about Broadcom) but sometimes on startup, the internet doesnt work. So I have to play a little mini game with my netbook by restarting the machine until the blue light comes on. Very annoying.

---

### Post by nm_geo on 2011-03-06
> **Rifester said:**
> Broadcom 4312 wireless card working with STA driver is not functioning after updates today.  Tried un-installing the driver and re-installing, no luck.   Any suggestions?

Thanks!

Go to Synaptic and search for bcm  > enter

Then remove the bcmwl-kernel-source and bcmwl-modaliases and any other with sta in the package name.

You probably will need to check the blacklisted drivers. 

```
cat /etc/modprobe.d/* | egrep '8180|acx|at76|ath|b43|bcm|CX|eth|ipw|irmware|isl|lbtf|orinoco|ndiswrapper|NPE|p54|prism|rtl|rt2|rt3|rt6|rt7|witch|wl'
```The STA driver blacklist the B43 driver and the ssb module.  You will need to comment out those blacklist by placing # in front of the line. ( eg. #blacklist b43),  Changing these will require gksudo gedit open then go to root then /etc/modprobe.d/ *and find the files where you need to comment out the blacklist. 

I have the bcm4312 chip and run the b43 driver quite well with Natty, Maverick and Lucid. There was a time I ran with the STA driver but kernel upgrades have ruined my connection.  Now you need two file the installers can be either firmware-b43-installer or firmware-b43-lpphy-installer (Installer package for firmware for the b43 driver (LP-PHY version) Low Power Version. Then you need b43-fwcutter installed. Reboot and before the login page you should see your wifi led come on. Hope that works it does here.

---

### Post by nm_geo on 2011-03-06
> **tjeremiah said:**
> this is going to be a huge problem for many come final release when they update to 11.04. I've managed to get mines to 'work' by installing the appropriate kernel (check my thread about Broadcom) but sometimes on startup, the internet doesnt work. So I have to play a little mini game with my netbook by restarting the machine until the blue light comes on. Very annoying.
 
Hi tjeremiah.. You might check your blacklist as well :D.  Can't remember if we did that or not!! I recently installed Maverick again just to test the STA driver, but i could not get it going with the current kernel  2.6.35-27-generic-pae #48-Ubuntu SMP .  So I reverted to the b43 that works well on my laptop, but I had blacklist issues on b43 and ssb that were created during the sta driver install. They are not confined to the blacklist.conf but in the broadcom-sta-common.conf also.

---

### Post by cariboo on 2011-03-06
I was a little behind on updates on this system, so I just did them, after a reboot I still have a wireless connection using the Broadcom wl driver:

```
cariboo@redstone:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: BCM4312 802.11b/g LP-PHY
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth1
       version: 01
       serial: 90:4c:e5:41:e4:2f
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.100.82.38 ip=192.168.1.101 latency=0 multicast=yes wireless=IEEE 802.11
       resources: irq:16 memory:feafc000-feafffff
```

Here's the output of uname -a

```
cariboo@redstone:~$ uname -a
Linux redstone 2.6.38-5-generic #32-Ubuntu SMP Tue Feb 22 16:09:46 UTC 2011 i686 i686 i386 GNU/Linux
```

---

### Post by Rifester on 2011-03-06
> **nm_geo said:**
> Go to Synaptic and search for bcm  > enter

Then remove the bcmwl-kernel-source and bcmwl-modaliases and any other with sta in the package name.

You probably will need to check the blacklisted drivers. 

```
cat /etc/modprobe.d/* | egrep '8180|acx|at76|ath|b43|bcm|CX|eth|ipw|irmware|isl|lbtf|orinoco|ndiswrapper|NPE|p54|prism|rtl|rt2|rt3|rt6|rt7|witch|wl'
```The STA driver blacklist the B43 driver and the ssb module.  You will need to comment out those blacklist by placing # in front of the line. ( eg. #blacklist b43),  Changing these will require gksudo gedit open then go to root then /etc/modprobe.d/ *and find the files where you need to comment out the blacklist. 

I have the bcm4312 chip and run the b43 driver quite well with Natty, Maverick and Lucid. There was a time I ran with the STA driver but kernel upgrades have ruined my connection.  Now you need two file the installers can be either firmware-b43-installer or firmware-b43-lpphy-installer (Installer package for firmware for the b43 driver (LP-PHY version) Low Power Version. Then you need b43-fwcutter installed. Reboot and before the login page you should see your wifi led come on. Hope that works it does here.

I followed your instructions.   Thank you so much!  I did not have to reboot and my wireless light came on.  I have always used the STA diver with Ubuntu and not had problems.   This is a first.    Will try a reboot and see what happens.

Thank you again!

EDIT:  Wireless is running perfectly after reboot.

---

### Post by tankedere on 2011-03-06
My Lenovo S10e netbook wireless (BCM4312-LP) stopped working after upgrading kernel from 2.6.35-24 to 2.6.35-27 while installing "compat-wireless" related packages (cannot remember which ones)
I've just followed **nm_geo** instructions and i can confirm it has fixed the problem, thank you!! :)

---

### Post by bela42 on 2011-03-08
So we have to try our luck with b43 again? Sigh.
And the driver downloader will continue to suggest STA? Oh crp.

Sounds like Ubuntu 11.04 doesn't quite work on lots of notebooks out there. Again. FAIL.

---

### Post by Rifester on 2011-03-08
Just to update... My wireless is functioning but it does not turn on automatically.   I have to manually turn it on.   Does anybody know how to change this setting?

Thanks!

---

### Post by donniezazen on 2011-03-18
> **nm_geo said:**
> Go to Synaptic and search for bcm  > enter

Then remove the bcmwl-kernel-source and bcmwl-modaliases and any other with sta in the package name.

You probably will need to check the blacklisted drivers. 

```
cat /etc/modprobe.d/* | egrep '8180|acx|at76|ath|b43|bcm|CX|eth|ipw|irmware|isl|lbtf|orinoco|ndiswrapper|NPE|p54|prism|rtl|rt2|rt3|rt6|rt7|witch|wl'
```The STA driver blacklist the B43 driver and the ssb module.  You will need to comment out those blacklist by placing # in front of the line. ( eg. #blacklist b43),  Changing these will require gksudo gedit open then go to root then /etc/modprobe.d/ *and find the files where you need to comment out the blacklist. 

I have the bcm4312 chip and run the b43 driver quite well with Natty, Maverick and Lucid. There was a time I ran with the STA driver but kernel upgrades have ruined my connection.  Now you need two file the installers can be either firmware-b43-installer or firmware-b43-lpphy-installer (Installer package for firmware for the b43 driver (LP-PHY version) Low Power Version. Then you need b43-fwcutter installed. Reboot and before the login page you should see your wifi led come on. Hope that works it does here.


What drivers do i need to black list from the attached picture? My wifi worked before blacklisting any deriver. The biggest problem is that it disconnects after a while. I them have to logout to get it working again. Any solution?

---

### Post by cariboo on 2011-03-18
You don't need to worry about any of those drivers, as you are using a Broadcom chipset. When you install either of the Broadcom drivers, b43, or wl, blacklist files are automatically created for the driver you aren't using. On my system I have a /etc/modprobe.d/blacklist-bcm43.conf, that contains the following blacklisted drivers:

```
blacklist b43
blacklist b43legacy
blacklist ssb
blacklist bcm43xx
```

---

### Post by jedi-penguin on 2011-03-21
I solved the STA driver problem by removing the latest driver of 11.04, download and install the older STA driver of 10.10.

This link is [http://packages.ubuntu.com/maverick/bcmwl-kernel-source](http://packages.ubuntu.com/maverick/bcmwl-kernel-source)

---

### Post by donniezazen on 2011-03-21
> **jedi-penguin said:**
> I solved the STA driver problem by removing the latest driver of 11.04, download and install the older STA driver of 10.10.

This link is [http://packages.ubuntu.com/maverick/bcmwl-kernel-source](http://packages.ubuntu.com/maverick/bcmwl-kernel-source)

Thanks, It did solve my problem. I have pinned down the maverick version of broadcom so i don't lose it.

---

### Post by GreenRaccoon on 2011-03-31
> **jedi-penguin said:**
> I solved the STA driver problem by removing the latest driver of 11.04, download and install the older STA driver of 10.10.

This link is [http://packages.ubuntu.com/maverick/bcmwl-kernel-source](http://packages.ubuntu.com/maverick/bcmwl-kernel-source)

I tried running this package, but it says that "The package is of bad quality."  Any ideas?

---

### Post by donniezazen on 2011-03-31
> **GreenGuitar1 said:**
> I tried running this package, but it says that "The package is of bad quality."  Any ideas?

Yeah, use gdebi. Dropbox deb also gave me same problem but it installed perfectly with gdebi.

---

### Post by GreenRaccoon on 2011-03-31
> **soham_1207 said:**
> Yeah, use gdebi. Dropbox deb also gave me same problem but it installed perfectly with gdebi.

You're a lifesaver! It worked! Thank you!

Just to recap on how I fixed this, I downloaded the STA driver for Maverick here:
[http://packages.ubuntu.com/maverick/bcmwl-kernel-source]("http://packages.ubuntu.com/maverick/bcmwl-kernel-source")

Then I went into terminal, switched to my Downloads directory (~/Downloads), and typed "sudo gdebi bcmwl-kernel-source_5.60.48.36+bdcom-0ubuntu5_i386.deb"

Then I searched for the Additional Drivers application and just activated the STA driver.

---

### Post by sblatt on 2011-04-20
thx ALOT guys! Just installed it, hope it will work.

Just another quick tip:
to prevent package manager form updating the drivers back to the natty version run synaptic, search for the driver package, select package -> lock version

---

### Post by MasterNetra on 2011-04-27
> **jedi-penguin said:**
> I solved the STA driver problem by removing the latest driver of 11.04, download and install the older STA driver of 10.10.

This link is [http://packages.ubuntu.com/maverick/bcmwl-kernel-source](http://packages.ubuntu.com/maverick/bcmwl-kernel-source)

+1

Solved my problem with it. Granted it amounts to a work around but still. Did use synaptic to lock the version too.

---

