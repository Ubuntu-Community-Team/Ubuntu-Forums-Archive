---
title: "error fetching interface information: Device not found."
date: 2012-07-30
forum: Networking &amp; Wireless
---

### Post by FerasMoalla on 2012-07-30
Hello,

I have just installed Ubuntu 7.04 in my ASUS laptop, my kernel version is 2.6. However when I type the command "ifconfig wlan0" it says: 

wlan0: error fetching interface information: Device not found.

Note that I also get the exact same error when typing the command "ifconfig eth0"

eth0: error fetching interface information: Device not found

Bellow is the output of the command ifconfig -a:

lo          Link encap:Local Loopback
            inet addr:127.0.0.1 Mask:255.0.0.0
            UP LOOPBACK RUNNING MTU:16436 Metric:1
            PX packets:2136 error:0 dropped:0 overruns:0 frame:0
            TX packets:2136 error:0 dropped:0 overruns:0 carrier:0
            collisions:0 txqueuelen:0
            RX bytes:130392 (127.3 KiB) TX bytes:130392 (127.3 KiB)


Any suggestions? 

Thanks,

---

### Post by chili555 on 2012-07-30
> I have just installed Ubuntu 7.04 in my ASUS laptop,Oh, my! [COLOR="Red"]7[/COLOR].04?? 

Your error usually means that no such interface exists because a driver hasn't found the hardware and created a wlan0. You are much more likely to find appropriate drivers in a newer version of Ubuntu. A lot of drivers have been added to the kernel in the last five years!

I recommend 12.04. If your laptop has limited resources, I recommend xubuntu.

---

### Post by FerasMoalla on 2012-07-30
> **chili555 said:**
> Oh, my! [COLOR="Red"]7[/COLOR].04?? 

Your error usually means that no such interface exists because a driver hasn't found the hardware and created a wlan0. You are much more likely to find appropriate drivers in a newer version of Ubuntu. A lot of drivers have been added to the kernel in the last five years!

I recommend 12.04. If your laptop has limited resources, I recommend xubuntu.

I got this OS  in a CD from a book, I know its an old version but it is configured so it can help me with my studies, I must use it. Is there any way to fix this problem?

Thanks :)

---

### Post by BkkBonanza on 2012-07-30
Post output of **ifconfig -a**

---

### Post by FerasMoalla on 2012-07-30
> **BkkBonanza said:**
> Post output of **ifconfig -a**

ifconfig -a:

lo          Link encap:Local Loopback
            inet addr:127.0.0.1 Mask:255.0.0.0
            UP LOOPBACK RUNNING MTU:16436 Metric:1
            PX packets:2136 error:0 dropped:0 overruns:0 frame:0
            TX packets:2136 error:0 dropped:0 overruns:0 carrier:0
            collisions:0 txqueuelen:0
            RX bytes:130392 (127.3 KiB) TX bytes:130392 (127.3 KiB)

Thanks

---

### Post by BkkBonanza on 2012-07-30
Yup. Drivers for your device aren't loaded. You'll need to discover what network card / wifi adapter you have and then try to get drivers that will work with such an old version.

You can try posting output of **lspci** command here but it's pretty likely you'll have a really hard time getting newer hardware to work with really old software.

You would be much better off trying to locate a newer version of Ubuntu. Whatever your studies are will be helped even more with a new version.

---

### Post by FerasMoalla on 2012-07-30
> **BkkBonanza said:**
> Yup. Drivers for your device aren't loaded. You'll need to discover what network card / wifi adapter you have and then try to get drivers that will work with such an old version.

You can try posting output of **lspci** command here but it's pretty likely you'll have a really hard time getting newer hardware to work with really old software.

You would be much better off trying to locate a newer version of Ubuntu. Whatever your studies are will be helped even more with a new version.

The thing is this specific version includes some codes, files, programs and it is configured in an environment that helps programming in C and assembly in order to test security flaws, Is it possible to upgrade to a new version of Ubuntu without losing those files and configurations?

Thanks for being such great help.

---

### Post by BkkBonanza on 2012-07-30
It should be. I mean all newer versions build on the old one. Without knowing all details I couldn't say. As far as programming and security functionality hasn't been reduced over time but improved. If the stuff you need is in some known location on the old cd then after installing the a newer version I would expect you can copy that stuff onto the system and be able to use it the same.

The thing is with an older unsupported version you will be always be exposed to any security vulnerabilities that have since been fixed in newer versions. And that's all assuming you can even get it to work with newer hardware devices.

There are some backport packages that help people use newer drivers with older versions of OS. I don't think they go back that far but you may be able to find something. If you need to do that then running the lspci command would be a first step as it will list what PCI devices are in your system and you can then google and find info on using those devices with 7.04.

---

### Post by chili555 on 2012-07-30
I wonder if it's a customized version that has the -dev packages pre-installed.

Let's see how far we can get before we throw in the 'upgrade' card. Please open a terminal and run and post:```
lspci -nn | grep -e 0280 -e 0200
```The pipe symbol | is on the right side of my US keyboard on the same key with \.

Is this running in a virtual machine?

---

### Post by FerasMoalla on 2012-07-30
Well said BkkBonanza, I will look into that. Thanks for the support.

---

### Post by FerasMoalla on 2012-07-30
> **chili555 said:**
> I wonder if it's a customized version that has the -dev packages pre-installed.

Let's see how far we can get before we throw in the 'upgrade' card. Please open a terminal and run and post:```
lspci -nn | grep -e 0280 -e 0200
```The pipe symbol | is on the right side of my US keyboard on the same key with \.

Is this running in a virtual machine?

Its not running on a VM I have it installed on a partition. I am guessing it is a customized version, this is the output of the command lspci -nn | grep -e 0280 -e 0200:

03:00.0 Network controller [0280]: Atheros Communication, Inc. Unknown device [168c:002b] (rev01)
07:00.5 Ethernet controller [0200]: JMicron Technologies, Inc. Uknown device [197b:0250] (rev 03)

Thanks

---

### Post by BkkBonanza on 2012-07-30
It seems you may have an Atheros AR9285 Wifi adapter. That's a pretty good unit but the drivers are fairly new in ATH9K project. You may want to look thru this link to see if there's backport info for 7.04

[http://linuxwireless.org/en/users/Drivers/ath9k/](http://linuxwireless.org/en/users/Drivers/ath9k/)

"ath9k was announced to have been merged into Linux-2.6.27-rc3 by Linus on Tue, 12 Aug 2008"
Ubuntu 8.10 seems to be the first release that can use it.
Kernel 2.6.29 earliest for the AR9285.


The ethernet controller appears to be a JMicron JMC250. That's a Gigabit controller. Google tells me it's,

found in Linux kernels: 2.6.28&#8211;2.6.39, 3.0&#8211;3.1
module name: jme

I'd say it's not too likely to get that going in 7.04 unless it's compatible with some older card. You may be able to get the newer drivers and compile it. Kind of doubt it, not sure if Gigabit even existed back then.

---

