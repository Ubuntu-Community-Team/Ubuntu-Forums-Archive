---
title: "Driver for Intel Wireless 6200 LAN card"
date: 2010-02-13
forum: Networking &amp; Wireless
---

### Post by Ufulum on 2010-02-13
Hi!

I've just bought a Dell Studio 15. In my stupidity I checked off for [FONT=arial][SIZE=1]Intel® Wireless LAN 6200 2x2 802.11a/b/g/n card instead of having [/SIZE][/FONT][FONT=arial][SIZE=1]Dell Wireless 1397 minicard (802.11 b/g) without checking if it was compatible with Linux. 

I've been searching around, but I haven't found any drivers for it. Does anyone know if there is a driver that will work with this card? 

When I type iwconfig it recognizes that there is a wireless card, but it doesn't find my access point or any of my neighbours access points. 

I can post you the output of iwconfig, lspci and others if you like, will just have to find a network cable for my Dell Studio 15. 
[/SIZE][/FONT]

---

### Post by janderpola on 2010-02-13
I´ve the same problem, i bought a Dell Studio 15 1558 with that card and I did´t found drivers for it. As it´s a very new hardware i spect drivers will be avaible soon...

The extrage thing is that if you look at [this PDF]("http://download.intel.com/network/connectivity/products/prodbrf/323016.pdf") from Intel, in the operating systems sections Ubuntu Linux is mentioned... what does that mean?

[http://download.intel.com/network/connectivity/products/prodbrf/323016.pdf](http://download.intel.com/network/connectivity/products/prodbrf/323016.pdf)

---

### Post by chili555 on 2010-02-13
> When I type iwconfig it recognizes that there is a wireless cardIf it shows up in iwconfig, then I think it has a driver. Please post:```
sudo lshw -C network
sudo iwlist wlan0 scan
rfkill list
```Thanks.

---

### Post by janderpola on 2010-02-13
Here is my result for that:

```
plaos@plaos-laptop:~$ sudo lshw -C network
  *-network DISABLED      
       description: Wireless interface
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: wmaster0
       version: 35
       serial: 00:23:14:14:1e:08
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn latency=0 multicast=yes wireless=IEEE 802.11abgn
       resources: irq:36 memory:f0500000-f0501fff
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 03
       serial: 00:26:b9:22:65:02
       size: 10MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
       resources: irq:35 ioport:5000(size=256) memory:f0404000-f0404fff(prefetchable) memory:f0400000-f0403fff(prefetchable) memory:f0420000-f043ffff(prefetchable)
  *-network DISABLED
       description: Ethernet interface
       physical id: 4
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes
plaos@plaos-laptop:~$ sudo iwlist wlan0 scan
wlan0     Interface doesn't support scanning : Network is down

plaos@plaos-laptop:~$ rfkill list
0: dell-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
```

---

### Post by chili555 on 2010-02-13
Just a stab in the dark, but let's see if we can get rid of:>  *-network [COLOR="Red"]DISABLED [/COLOR]     
       description: Wireless interface
       product: Intel Corporation
       vendor: Intel Corporation
Please try:```
sudo rmmod -f dell-laptop
sudo lshw -C network
```Is DISABLED still there?

---

### Post by janderpola on 2010-02-13
mmmmm, no luck, just the same message:

```

plaos@plaos-laptop:~$ sudo rmmod -f dell-laptop
[sudo] password for plaos: 
plaos@plaos-laptop:~$ sudo lshw -C network
  *-network DISABLED      
       description: Wireless interface
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: wmaster0
       version: 35
       serial: 00:23:14:14:1e:08
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn latency=0 multicast=yes wireless=IEEE 802.11abgn
       resources: irq:36 memory:f0500000-f0501fff
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 03
       serial: 00:26:b9:22:65:02
       size: 10MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
       resources: irq:35 ioport:5000(size=256) memory:f0404000-f0404fff(prefetchable) memory:f0400000-f0403fff(prefetchable) memory:f0420000-f043ffff(prefetchable)
  *-network DISABLED
       description: Ethernet interface
       physical id: 4
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes
plaos@plaos-laptop:~$

```


Why could this be disabled? and, just curious, what is dell_laptop, and why to remove it?

Check this PDF from Intel:

[http://download.intel.com/network/connectivity/products/prodbrf/323016.pdf]("http://download.intel.com/network/connectivity/products/prodbrf/323016.pdf")

Ubuntu Linux is there in Operating Systems (with XP, Vista and 7)... 

Thanks!

---

### Post by janderpola on 2010-02-13
I have just downloaded Ubuntu 10.04 alpha 2, and burned to a CD.

When I boot it in live, i do have wireless and i´m able to connect to wifi networks.

I also have sound! (i don´t have sound on 9.10). So... i think i will install this although is alpha version. Just have to wait two months for a final version.

---

### Post by Ufulum on 2010-02-14
Oh, perhaps I should try that too. Though, if the wireless works there, the driver should be avalible. Might just need to probe it into the kernel.

---

### Post by Ufulum on 2010-02-18
I've tried installing the 10.04 version several times. It solves the wlan problem, and for the first five seconds, everything seemed fine. But it's way to unstable. If I'm able to get X up and going, it crashes when it goes on standby. And the multimedia keys are a sure way to start an everlasting loop. 

So, is it in any way possible to get the driver for 9.10?

---

### Post by saku100 on 2010-02-19
Hi i've received a laptop today with this wireless card. I was all day trying to find any driver to solve the problem. Finally i saw that this intel driver is now merged in the kernel of linux [http://git.kernel.org/?p=linux/kernel/git/iwlwifi/iwlwifi-2.6.git](http://git.kernel.org/?p=linux/kernel/git/iwlwifi/iwlwifi-2.6.git) instead of recompiling the kernel y have just downloaded todays build of ubuntu (in my case kubuntu) and it worked; you can download here:
[http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)

I don't know if this build has enough stability to work with, but for my is ok.

---

### Post by openxs on 2010-02-21
@ Ufulum & janderpola, Hi guys, I'm pleased to hear you are having success with the Dell Studio 15 & Ubuntu. I'm about to buy one as they are on offer, i-5 processor,  512MB ATI Mobility RADEON HD 4570 Graphics Card and more... very good price for the specs, I'll be adding the Intel wireless card myself. What do you think of it, are you happy? I will be installing a Linux distro on it in the same hour it arrives :) 

Are the function keys working? Sound? Anything playing up apart from what you originally posted? would you be so kind as to post the results of lspci + lshw o PM them to me? 

Thanks in advance!

---

### Post by Ufulum on 2010-02-22
As I said in the post before, I also got the driver working in the unstable version. Problem is that it is way to unstable. Need a more stable version before I can run 10.04.

Except from the wireless card, things seemed to work quite well in 9.10. Though, I'd rather not run it with a cable going through my apartment. Either I have to find some driver for the card, or I have to wait until 10.04 becomes more stable.

The pc itself is quite good. I chose the 1080p screen which is wonderful.

---

### Post by mamangtubero on 2010-02-26
I have a Dell Studio 1458 (14") with Intel WiFi Link 6200. This worked for me.

sudo apt-get install linux-backports-modules-karmic-generic
Then reboot.

The information came from [http://ubuntuforums.org/showthread.php?p=8840137](http://ubuntuforums.org/showthread.php?p=8840137)

---

### Post by Ufulum on 2010-03-02
Thanks! Then wireless is working with kernel 2.6.31.

I also got it working by upgrading the kernel. Just follow the guide here:
[www.ramoonus.nl/2009/12/03/linux-kernel-2-6-32-installation-guide-for-ubuntu-linux/]("http://http://www.ramoonus.nl/2009/12/03/linux-kernel-2-6-32-installation-guide-for-ubuntu-linux/")

---

### Post by openxs on 2010-03-03
> **Ufulum said:**
> Thanks! Then wireless is working with kernel 2.6.31.

I also got it working by upgrading the kernel. Just follow the guide here:
[http://www.ramoonus.nl/2009/12/03/linux-kernel-2-6-32-installation-guide-for-ubuntu-linux/]("http://http://www.ramoonus.nl/2009/12/03/linux-kernel-2-6-32-installation-guide-for-ubuntu-linux/")

Great stuff, my new Studio 15 arrived today, I quickly followed this post and now I have sound and wireless working, well found guys! In a nutshell, it's a simple upgrade of the kernel to 2.6.32. I'll post the instructions here in case anyone else needs them, these instructions point to the 64-bit kernel too: 

Install the files in the following order:
1) [linux-headers-2.6.32-020632_2.6.32-020632_all.deb]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.32/linux-headers-2.6.32-020632_2.6.32-020632_all.deb")

2) for I386:  [linux-headers-2.6.32-020632-generic_2.6.32-020632_i386.deb]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.32/linux-headers-2.6.32-020632-generic_2.6.32-020632_i386.deb") 
or if AMD64: [linux-headers-2.6.32-020632-generic_2.6.32-020632_amd64.deb]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.32/linux-headers-2.6.32-020632-generic_2.6.32-020632_amd64.deb")

3) for I386: [linux-image-2.6.32-020632-generic_2.6.32-020632_i386.deb]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.32/linux-image-2.6.32-020632-generic_2.6.32-020632_i386.deb") 
or for AMD64: [linux-image-2.6.32-020632-generic_2.6.32-020632_amd64.deb]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.32/linux-image-2.6.32-020632-generic_2.6.32-020632_amd64.deb")

Finally, in the terminal run:
# sudo update-grub

Reboot and select the kernel from the bootloader menu
For those who want to do their &#8220;own&#8221; compiles, the source is available [here]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.32/linux-source-2.6.32_2.6.32-020632_all.deb").

The original tute was by: [Ramon Van Belzen]("http://www.ramoonus.nl/2009/12/03/linux-kernel-2-6-32-installation-guide-for-ubuntu-linux/")

With much thanks to the guys who started this thread and sussed out the issues, perhaps you can mark this as solved now? :)

*** One final note, on my Studio 15 the fan was constantly running, I discovered that installing the proprietary drivers from ATI fixed this. My card is a Radeon Mobility HD 4 series, I got the driver here: [http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.2&product=2.4.2.3.32&lang=English]("http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.2&product=2.4.2.3.32&lang=English")

Hope this helps someone else, so far everything else is working pretty well, what I have tried at least...

---

### Post by Ufulum on 2010-03-06
Ah, seems the link I posted is kind of defective. Thanks for posting the content so people can find it more easily.

It seems by the way that the fan is running most of the time, even when the cpu is quite cold. That and the multimedia keys causing an everlasting loop are the main problems I have with Ubuntu now.

---

### Post by openxs on 2010-03-07
> **Ufulum said:**
> Ah, seems the link I posted is kind of defective. Thanks for posting the content so people can find it more easily.

It seems by the way that the fan is running most of the time, even when the cpu is quite cold. That and the multimedia keys causing an everlasting loop are the main problems I have with Ubuntu now.

Yeah, I've fixed my fan issue with the proprietary ATI graphics driver, I added that to the end of my last post, but sounds like you missed it. The multimedia keys are as you say, loopy. I haven't even bothered looking in to that problem yet, decided I can wait until the end of next month for 10.04 to be released.

Here are a couple of useful links for anyone else who buys a Dell 1558:

[http://www.ubuntuhcl.org/browse/product+dell-studio-1558?id=7125]("http://www.ubuntuhcl.org/browse/product+dell-studio-1558?id=7125")
[http://ubuntuforums.org/showthread.php?t=1401746]("http://ubuntuforums.org/showthread.php?t=1401746")

The following link is to fix the volume keys, however, it didn't work for me so I can't verify it:
[http://ubuntuforums.org/showthread.php?t=974723&page=6](http://ubuntuforums.org/showthread.php?t=974723&page=6)[http://ubuntuforums.org/showthread.php?t=974723&page=6]("http://ubuntuforums.org/showthread.php?t=974723&page=6")

---

### Post by yisroel6 on 2010-07-04
> **Ufulum said:**
> Hi!

I've just bought a Dell Studio 15. In my stupidity I checked off for [FONT=arial][SIZE=1]Intel® Wireless LAN 6200 2x2 802.11a/b/g/n card instead of having [/SIZE][/FONT][FONT=arial][SIZE=1]Dell Wireless 1397 minicard (802.11 b/g) without checking if it was compatible with Linux. 

I've been searching around, but I haven't found any drivers for it. Does anyone know if there is a driver that will work with this card? 

When I type iwconfig it recognizes that there is a wireless card, but it doesn't find my access point or any of my neighbours access points. 

I can post you the output of iwconfig, lspci and others if you like, will just have to find a network cable for my Dell Studio 15. 
[/SIZE][/FONT]

I have the same problem! Dell studio 1558. Intel centrino advanced wireless-N w/WiMax 2x2 mini card.
When in Linux ubuntu, my wireless is "disabled".
I also get the responce in the terminal that my wireless card is Disabled! On top of that, my headphones slot doesn't produce any sound. I can only hear sound from my speakers.

---

### Post by yisroel6 on 2010-07-04
> **openxs said:**
> Great stuff, my new Studio 15 arrived today, I quickly followed this post and now I have sound and wireless working, well found guys! In a nutshell, it's a simple upgrade of the kernel to 2.6.32. I'll post the instructions here in case anyone else needs them, these instructions point to the 64-bit kernel too: 

Install the files in the following order:
1) [linux-headers-2.6.32-020632_2.6.32-020632_all.deb]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.32/linux-headers-2.6.32-020632_2.6.32-020632_all.deb")

2) for I386:  [linux-headers-2.6.32-020632-generic_2.6.32-020632_i386.deb]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.32/linux-headers-2.6.32-020632-generic_2.6.32-020632_i386.deb") 
or if AMD64: [linux-headers-2.6.32-020632-generic_2.6.32-020632_amd64.deb]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.32/linux-headers-2.6.32-020632-generic_2.6.32-020632_amd64.deb")

3) for I386: [linux-image-2.6.32-020632-generic_2.6.32-020632_i386.deb]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.32/linux-image-2.6.32-020632-generic_2.6.32-020632_i386.deb") 
or for AMD64: [linux-image-2.6.32-020632-generic_2.6.32-020632_amd64.deb]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.32/linux-image-2.6.32-020632-generic_2.6.32-020632_amd64.deb")

Finally, in the terminal run:
# sudo update-grub

Reboot and select the kernel from the bootloader menu
For those who want to do their “own” compiles, the source is available [here]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.32/linux-source-2.6.32_2.6.32-020632_all.deb").

The original tute was by: [Ramon Van Belzen]("http://www.ramoonus.nl/2009/12/03/linux-kernel-2-6-32-installation-guide-for-ubuntu-linux/")

With much thanks to the guys who started this thread and sussed out the issues, perhaps you can mark this as solved now? :)

*** One final note, on my Studio 15 the fan was constantly running, I discovered that installing the proprietary drivers from ATI fixed this. My card is a Radeon Mobility HD 4 series, I got the driver here: [http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.2&product=2.4.2.3.32&lang=English]("http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.2&product=2.4.2.3.32&lang=English")

Hope this helps someone else, so far everything else is working pretty well, what I have tried at least...
Horrible.... now neither does my mouse or keyboard work! Someone help please.

---

### Post by Aitaix on 2010-09-25
> **openxs said:**
> Great stuff, my new Studio 15 arrived today, I quickly followed this post and now I have sound and wireless working, well found guys! In a nutshell, it's a simple upgrade of the kernel to 2.6.32. I'll post the instructions here in case anyone else needs them, these instructions point to the 64-bit kernel too: 

Install the files in the following order:
1) [linux-headers-2.6.32-020632_2.6.32-020632_all.deb]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.32/linux-headers-2.6.32-020632_2.6.32-020632_all.deb")

2) for I386:  [linux-headers-2.6.32-020632-generic_2.6.32-020632_i386.deb]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.32/linux-headers-2.6.32-020632-generic_2.6.32-020632_i386.deb") 
or if AMD64: [linux-headers-2.6.32-020632-generic_2.6.32-020632_amd64.deb]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.32/linux-headers-2.6.32-020632-generic_2.6.32-020632_amd64.deb")

3) for I386: [linux-image-2.6.32-020632-generic_2.6.32-020632_i386.deb]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.32/linux-image-2.6.32-020632-generic_2.6.32-020632_i386.deb") 
or for AMD64: [linux-image-2.6.32-020632-generic_2.6.32-020632_amd64.deb]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.32/linux-image-2.6.32-020632-generic_2.6.32-020632_amd64.deb")

Finally, in the terminal run:
# sudo update-grub

Reboot and select the kernel from the bootloader menu
For those who want to do their “own” compiles, the source is available [here]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.32/linux-source-2.6.32_2.6.32-020632_all.deb").

The original tute was by: [Ramon Van Belzen]("http://www.ramoonus.nl/2009/12/03/linux-kernel-2-6-32-installation-guide-for-ubuntu-linux/")

With much thanks to the guys who started this thread and sussed out the issues, perhaps you can mark this as solved now? :)

*** One final note, on my Studio 15 the fan was constantly running, I discovered that installing the proprietary drivers from ATI fixed this. My card is a Radeon Mobility HD 4 series, I got the driver here: [http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.2&product=2.4.2.3.32&lang=English](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.2&product=2.4.2.3.32&lang=English)

Hope this helps someone else, so far everything else is working pretty well, what I have tried at least...


can't boot my laptop after :( 

any ideas? running 9.10

Warning: unable to find a suitable fs in /proc/mounts, is it mounted? Use --subdomainfs to override.

---

### Post by markden on 2010-10-04
i have a windows driver ( mercury kob503 wireless lan) is thier a way to convert it to linux ( ubuntu 10.04) or a driver that will do the job for me

---

### Post by Jack Kelly on 2013-01-15
Please can someone confirm whether the [ Intel Centrino Wireless Advance-N 6200 LAN card]("http://www.intel.com/products/wireless/adapters/6200/index.htm") works on Ubuntu 12.10?  I assume it does.

edit: [this thread]("http://forums.opensuse.org/english/get-technical-help-here/hardware/434646-intel-centrino-advanced-linux-compatible.html") suggests that the Intel 6200 LAN card does work with Linux but a confirmation that it works on 12.10 would be great ;)

---

### Post by chili555 on 2013-01-15
> **Jack Kelly said:**
> Please can someone confirm whether the [ Intel Centrino Wireless Advance-N 6200 LAN card]("http://www.intel.com/products/wireless/adapters/6200/index.htm") works on Ubuntu 12.10?  I assume it does.

edit: [this thread]("http://forums.opensuse.org/english/get-technical-help-here/hardware/434646-intel-centrino-advanced-linux-compatible.html") suggests that the Intel 6200 LAN card does work with Linux but a confirmation that it works on 12.10 would be great ;)Mine works perfectly:> *-network
       description: Wireless interface
       product: Centrino Advanced-N 6200
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 35
       serial: xx:94:6b:99:55:xx
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=3.5.0-21-generic firmware=9.221.4.1 build 25532 ip=192.168.1.12 latency=0 link=yes multicast=yes wireless=IEEE 802.11abgn
       resources: irq:43 memory:f2400000-f2401fffThe driver in question, *iwlwifi*, often will not do N speeds, but I don't stream Blu-Ray to my laptop over the LAN so it's not an issue for me. If you are considering a laptop with an Intel wireless chipset vs. a Realtek, the Intel is what I'd recommend.

---

### Post by Jack Kelly on 2013-01-15
Brilliant, thank you!

---

