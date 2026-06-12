---
title: "Can't get wireless network to work"
date: 2013-02-03
forum: Networking &amp; Wireless
---

### Post by DerpishCat on 2013-02-03
Hello Ubuntu Forums, this is my first post here so let's hope I don't make any huge mistakes!

I currently have Ubuntu 12.10 installed on my mothers computer, and today we were going to get a WiFi USB adapter, so we don't have to have one long cable going from the router.

We decided to get a [Netgear WNA3100 ]("http://www.netgear.com/home/products/wireless-adapters/work-and-play/WNA3100.aspx#"), after plugging it in.. nothing happend at all.
I can find it in lsusb, but that's it.
```
Bus 002 Device 016: ID 0846:9020 NetGear, Inc. WNA3100(v1) Wireless-N 300 [Broadcom BCM43231]
```I searched Google for drivers, but only found something called "ndiswrapper" and something on YouTube, but that was from 2008.
Neither of them worked, only threw errors at me.

I'd really appreciate any help on this, because I can't seem to figure this out.
Maybe I'm just forgetting something, or just not skilled enough.

---

### Post by chili555 on 2013-02-03
There are dozens of posts about this same device; here, for instance: [http://ubuntuforums.org/showthread.php?t=1946875&highlight=WNA3100](http://ubuntuforums.org/showthread.php?t=1946875&highlight=WNA3100)

It even includes the files you require.

---

### Post by DerpishCat on 2013-02-03
> **chili555 said:**
> There are dozens of posts about this same device; here, for instance: [http://ubuntuforums.org/showthread.php?t=1946875&highlight=WNA3100](http://ubuntuforums.org/showthread.php?t=1946875&highlight=WNA3100)

It even includes the files you require.
Oh damn it, my mistake there, guess this shows my googling skills :/

EDIT: Gaah, I **still** can't get this to work!
I followed some of the guide (it got very confusing because it was like 3 guides...) and it said it was installed, but I can still not connect to the internet!
```
annika@annika-desktop:~$ sudo ndiswrapper -i /home/annika/Skrivbord/WNA3100/bcmwlhigh5.inf
installing bcmwlhigh5 ...
annika@annika-desktop:~$
```
It shows up in ndisgtk and tells me "Hardware in the system: Yes" (In Swedish, just translated this) But it's not visible in the networking manager or anything!

---

### Post by chili555 on 2013-02-03
The next step is to look for any informative clues in the message log:```
dmesg | grep ndis
ndiswrapper -l
rfkill list all
```

---

### Post by DerpishCat on 2013-02-03
> **chili555 said:**
> The next step is to look for any informative clues in the message log:```
dmesg | grep ndis
ndiswrapper -l
rfkill list all
```
dmesg | grep ndis didn't display anything at all
```
annika@annika-desktop:~$ dmesg | grep ndis
annika@annika-desktop:~$
```ndiswrapper -l displayed this:
```
annika@annika-desktop:~$ ndiswrapper -l
bcmwlhigh5 : driver installed
        device (0846:9020) present
annika@annika-desktop:~$
```
rfkill list all didn't display anything either
```
annika@annika-desktop:~$ rfkill list all
annika@annika-desktop:~$
```
Not sure what I am doing wrong...
Thanks for all the help so far at least!

---

### Post by chili555 on 2013-02-03
Hmmm. dmesg ought to at least have some recognition. Let's try a bit harder:```
sudo modprobe ndiswrapper
dmesg | grep ndiswrapper
```> annika@annika-desktop:~$ ndiswrapper -l
bcmwlhigh5 : driver installed
        device (0846:9020) presentLooks perfect so far!

---

### Post by DerpishCat on 2013-02-03
> **chili555 said:**
> Hmmm. dmesg ought to at least have some recognition. Let's try a bit harder:```
sudo modprobe ndiswrapper
dmesg | grep ndiswrapper
```Looks perfect so far!
sudo modprobe ndiswrapper:
```
annika@annika-desktop:~$ sudo modprobe ndiswrapper
[sudo] password for annika: 
FATAL: Module ndiswrapper not found.
annika@annika-desktop:~$
```
I can't find anywhere in the guide where it tells me to install any modules?

dmesg | grep ndiswrapper:
```
annika@annika-desktop:~$ dmesg | grep ndiswrapper
annika@annika-desktop:~$
```

---

### Post by chili555 on 2013-02-03
It's very hard to understand how ndiswrapper isn't installed correctly when you have ndisgtk and can load the inf file without error or drama:> annika@annika-desktop:~$ sudo ndiswrapper -i /home/annika/Skrivbord/WNA3100/bcmwlhigh5.inf
installing bcmwlhigh5 ...Let's try to repair it. Assuming you have a wired ethernet connection, please do:```
sudo apt-get install --reinstall ndiswrapper-utils-1.9
sudo apt-get install --reinstall ndiswrapper-common
sudo apt-get install --reinstall ndiswrapper-dkms
```After it's done, try again:```
sudo modprobe ndiswrapper
dmesg | grep ndis
```

---

### Post by DerpishCat on 2013-02-03
> **chili555 said:**
> It's very hard to understand how ndiswrapper isn't installed correctly when you have ndisgtk and can load the inf file without error or drama:Let's try to repair it. Assuming you have a wired ethernet connection, please do:```
sudo apt-get install --reinstall ndiswrapper-utils-1.9
sudo apt-get install --reinstall ndiswrapper-common
sudo apt-get install --reinstall ndiswrapper-dkms
```After it's done, try again:```
sudo modprobe ndiswrapper
dmesg | grep ndis
```
When reinstalling ndiswrapper-dkms I got this error at the end:
```
------------------------------
Deleting module version: 1.57
completely from the DKMS tree.
------------------------------
Done.
Packar upp ersättande ndiswrapper-dkms ...
Ställer in ndiswrapper-dkms (1.57-1ubuntu1) ...
Loading new ndiswrapper-1.57 DKMS files...
Building only for 3.5.0-22-generic
Module build for the currently running kernel was skipped since the
kernel source for this kernel does not seem to be installed.
```
However neither modprobe or dmesg showed anything different.

---

### Post by chili555 on 2013-02-03
> Module build for the currently running kernel was skipped since the
kernel source for this kernel does not seem to be installed.What a stubborn little thing!```
sudo apt-get install linux-headers-generic
sudo apt-get install --reinstall ndiswrapper-dkms
sudo modprobe ndiswrapper
sudo gimme some wireless now [COLOR="Red"]<-- just kidding here[/COLOR]
```

---

### Post by DerpishCat on 2013-02-03
> **chili555 said:**
> What a stubborn little thing!```
sudo apt-get install linux-headers-generic
sudo apt-get install --reinstall ndiswrapper-dkms
sudo modprobe ndiswrapper
sudo gimme some wireless now [COLOR=Red]<-- just kidding here[/COLOR]
```
Installed linux-headers-generic, seemed to have installed just fine, but still getting the same result with that reinstall of ndiswrapper-dkms and running modprobe!

EDIT: Oh and, I also tried restarting between, still no luck.

---

### Post by chili555 on 2013-02-03
Is there any result from:```
sudo modprobe ndiswrapper
dmesg | grep ndis
```Stubborn!

---

### Post by DerpishCat on 2013-02-03
> **chili555 said:**
> Is there any result from:```
sudo modprobe ndiswrapper
dmesg | grep ndis
```Stubborn!
```
annika@annika-desktop:~$ sudo modprobe ndiswrapper
FATAL: Module ndiswrapper not found.
annika@annika-desktop:~$
```
```
annika@annika-desktop:~$ dmesg | grep ndis
annika@annika-desktop:~$
```

This computer is getting on my nerves haha

---

### Post by chili555 on 2013-02-03
```
sudo dpkg -s linux-headers-`uname -r`
```Those tickmarks are on the left side of my US keyboard on the same key with ~. If it reports the package is not installed, then do:```
sudo apt-get install linux-headers-`uname -r`
sudo apt-get install --reinstall ndiswrapper-dkms
sudo modprobe ndiswrapper

```...hoping and praying I get to keep my sanity/mojo/talent...

---

### Post by DerpishCat on 2013-02-03
> **chili555 said:**
> ```
sudo dpkg -s linux-headers-`uname -r`
```Those tickmarks are on the left side of my US keyboard on the same key with ~. If it reports the package is not installed, then do:```
sudo apt-get install linux-headers-`uname -r`
sudo apt-get install --reinstall ndiswrapper-dkms
sudo modprobe ndiswrapper

```...hoping and praying I get to keep my sanity/mojo/talent...
At the end of the install of linux-headers-`uname -r` I got this:
```
Error! Bad return status for module build on kernel: 3.5.0-22-generic (x86_64)
Consult /var/lib/dkms/ndiswrapper/1.57/build/make.log for more information.
```
Reinstall of ndiswrapper-dkms gives me the same error.

And, surprise surprise... modprobe tells me it can't find ndiswrapper. :rolleyes:

---

### Post by chili555 on 2013-02-03
I was quite afraid of that. It is a well known, long standing bug that affects some 12.10 installs. For testing and reference purposes, I have ndiswrapper installed myself and I'm similarly affected. Here is what we can do. Get this package and get it to your desktop: [http://sourceforge.net/projects/ndiswrapper/files/testing/](http://sourceforge.net/projects/ndiswrapper/files/testing/)

Right-click it and select 'Extract Here.' Open a terminal and do:```
sudo apt-get install build-essential
cd Skrivbord/ndiswrapper-1.58rc1
sudo su
make
make install
modprobe ndiswrapper
exit
```*NOW* does it load?

---

### Post by DerpishCat on 2013-02-03
> **chili555 said:**
> I was quite afraid of that. It is a well known, long standing bug that affects some 12.10 installs. For testing and reference purposes, I have ndiswrapper installed myself and I'm similarly affected. Here is what we can do. Get this package and get it to your desktop: [http://sourceforge.net/projects/ndiswrapper/files/testing/](http://sourceforge.net/projects/ndiswrapper/files/testing/)

Right-click it and select 'Extract Here.' Open a terminal and do:```
sudo apt-get install build-essential
cd Skrivbord/ndiswrapper-1.58rc1
sudo su
make
make install
modprobe ndiswrapper
exit
```*NOW* does it load?
It now does load, lists all the networks around here, but I can't seem to connect to any of them.
Just tells me wrong password, even when I know it's the correct one, tried with 2 devices.

---

### Post by chili555 on 2013-02-03
> **DerpishCat said:**
> It now does load, lists all the networks around here, but I can't seem to connect to any of them.
Just tells me wrong password, even when I know it's the correct one, tried with 2 devices.Now let's check for informative clues:```
dmesg | grep -e ndis -e wlan
```

---

### Post by DerpishCat on 2013-02-03
> **chili555 said:**
> Now let's check for informative clues:```
dmesg | grep -e ndis -e wlan
```
```
annika@annika-desktop:~$ dmesg | grep -e ndis -e wlan
[    2.657185] ndiswrapper version 1.58rc1 loaded (smp=yes, preempt=no)
[    2.894420] ndiswrapper: driver bcmwlhigh5 (Netgear,03/28/2011, 5.100.68.46) loaded
[    2.899534] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90021cc8000, 16000, 4
[    2.899536] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90021ccbe80, 16000, 5
[    2.899538] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90021ccfd00, 16000, 5
[    2.899539] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90021cd3b80, 16000, 5
[    2.899540] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90021cd7a00, 16000, 5
[    2.899542] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90021cdb880, 16000, 5
[    2.899543] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90021cdf700, 16000, 5
[    2.899544] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90021ce3580, 16000, 5
[    2.899545] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90021ce7400, 16000, 5
[    2.899547] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90021ceb280, 16000, 5
[    2.899548] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90021cef100, 16000, 4
[    2.899549] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90021cf2f80, 16000, 5
[    2.899550] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90021cf6e00, 16000, 5
[    2.899551] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90021cfac80, 16000, 5
[    2.899553] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90021cfeb00, 16000, 5
[    2.899554] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90021d02980, 16000, 5
[    2.899555] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90021d06800, 16000, 5
[    2.899556] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90021d0a680, 16000, 5
[    2.899559] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90021d0e500, 16000, 5
[    2.899560] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90021d12380, 16000, 5
[    2.899561] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90021d16200, 16000, 5
[    2.899562] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90021d1a080, 16000, 4
[    2.899563] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90021d1df00, 16000, 5
[    2.899564] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90021d21d80, 16000, 5
[    2.899565] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90021d25c00, 16000, 5
[    2.899567] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90021d29a80, 16000, 5
[    2.899568] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90021d2d900, 16000, 5
[    2.899569] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90021d31780, 16000, 5
[    2.899570] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90021d35600, 16000, 5
[    2.899572] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90021d39480, 16000, 5
[    2.899573] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90021d3d300, 16000, 5
[    2.899574] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90021d41180, 16000, 4
[    2.899575] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90021d45000, 16000, 4
[    2.899576] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90021d48e80, 16000, 5
[    2.899577] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90021d4cd00, 16000, 5
[    2.899579] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90021d50b80, 16000, 5
[    2.899580] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90021d54a00, 16000, 5
[    2.899582] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90021d58880, 16000, 5
[    2.899583] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90021d5c700, 16000, 5
[    2.899584] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90021d60580, 16000, 5
[    2.899585] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90021d64400, 16000, 5
[    2.899586] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90021d68280, 16000, 5
[    2.899588] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90021d6c100, 16000, 4
[    2.899589] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90021d6ff80, 16000, 5
[    2.899590] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90021d73e00, 16000, 5
[    2.899591] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90021d77c80, 16000, 5
[    2.899592] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90021d7bb00, 16000, 5
[    2.899593] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90021d7f980, 16000, 5
[    2.899595] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90021d83800, 16000, 5
[    2.899596] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90021d87680, 16000, 5
[    2.914998] ndiswrapper (ndis_encode_setting:383): unknown type: 3
[    3.198743] wlan0: ethernet device 00:8e:f2:75:77:31 using NDIS driver: bcmwlhigh5, version: 0x564442e, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 0846:9020.F.conf
[    3.207842] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2-PSK; AES/CCMP with WPA, WPA2, WPA2-PSK
[    3.210203] usbcore: registered new interface driver ndiswrapper
[    3.432505] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[    3.432617] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   28.039902] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
annika@annika-desktop:~$
```

---

### Post by chili555 on 2013-02-03
Off for a few hours; I'll check back later.

---

### Post by chili555 on 2013-02-04
If you have read a few of the many other threads about this device, you will see that 64-bit is hit or miss; some report it works fine, some report it *never* works. I haven't been able to spot a pattern yet. You have: > kernel: 3.5.0-22-generic ([COLOR="Red"]x86_64[/COLOR])Which of the many inf files floating around on the forum did you download and install? We might try another, such as attached. It would involve removing what you have now:```
sudo nidiswrapper -e bcmwlhigh5
sudo rm -rf /etc/ndiswrapper/*
```Then install the files from this package.```
cd Skrivbord/Broadcom_bcm43xx_USB_32_64bit_v2_amended
sudo ndiswrapper -i bcmn43xx64.inf
sudo modprobe -r ndiswrapper
sudo modprobe ndiswrapper
```...assuming you've downloaded the file to your desktop and extracted it there.

I also wonder if the creaky old Windows XP driver has trouble with N speeds. Is 802.11N enabled in your router? If you disable it, can you connect?

---

### Post by DerpishCat on 2013-02-04
> **chili555 said:**
> If you have read a few of the many other threads about this device, you will see that 64-bit is hit or miss; some report it works fine, some report it *never* works. I haven't been able to spot a pattern yet. You have: Which of the many inf files floating around on the forum did you download and install? We might try another, such as attached. It would involve removing what you have now:```
sudo nidiswrapper -e bcmwlhigh5
sudo rm -rf /etc/ndiswrapper/*
```Then install the files from this package.```
cd Skrivbord/Broadcom_bcm43xx_USB_32_64bit_v2_amended
sudo ndiswrapper -i bcmn43xx64.inf
sudo modprobe -r ndiswrapper
sudo modprobe ndiswrapper
```...assuming you've downloaded the file to your desktop and extracted it there.

I also wonder if the creaky old Windows XP driver has trouble with N speeds. Is 802.11N enabled in your router? If you disable it, can you connect?
[This]("http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=Netgear_WNA3100") is the one I downloaded.

I removed the old one, and when installing the new one (had to specify exact directory, else it would just keep looking in /usr/sbin/ndiswrapper) it gave me this error:
```
couldn't find SourceDisksFiles section - continuing anyway...
```
It then came up with the same crap as before, listing the networks, tries to connect but then just tells me the password is incorrect.

Also I have no idea how to disable 802.11N speeds, or if I even have it.
[This]("http://www.tp-link.com/us/products/details/?categoryid=&model=TL-WR1043ND") is the router I have, if it helps you in any way.

A thought I just got, is... does this wireless adapter support WPA-PSK/WPA2-PSK security?

---

### Post by chili555 on 2013-02-04
I'm fairly certain it does support the common encryption modes. Find out:```
sudo iwlist wlan0 auth
```Your router certainly does N speeds. Look in the administration pages in Wireless > Mode. Here is a screenshot from the User Guide. I suggest, as a trial, you select **11bg mixed**; that is, not N.

---

### Post by DerpishCat on 2013-02-04
> **chili555 said:**
> I'm fairly certain it does support the common encryption modes. Find out:```
sudo iwlist wlan0 auth
```Your router certainly does N speeds. Look in the administration pages in Wireless > Mode. Here is a screenshot from the User Guide. I suggest, as a trial, you select **11bg mixed**; that is, not N.
Found the option, and it's set to 11bgn right now.
I'll look more into this tomorrow, as it is midnight right now, and I do not currently have access to the computer.

---

### Post by DerpishCat on 2013-02-06
> **chili555 said:**
> I'm fairly certain it does support the common encryption modes. Find out:```
sudo iwlist wlan0 auth
```Your router certainly does N speeds. Look in the administration pages in Wireless > Mode. Here is a screenshot from the User Guide. I suggest, as a trial, you select **11bg mixed**; that is, not N.
I've been quite busy, but now finally got some time to get back into this.

Anyway, I tried changing it to 11bg mixed, and bam it works!
[http://fuskbugg.se/file/WY62sj/Skrmbild%20frn%202013-02-06%20131852.png](http://fuskbugg.se/file/WY62sj/Skrmbild%20frn%202013-02-06%20131852.png)
Is there anything else than the speed I'll loose by choosing to use this? (Doesn't really matter as it's just my phone, laptop and mom's computer using the wireless, but still...)

Thanks for all the help by the way, pretty rare to find such nice and helpful people out there! ;)

---

### Post by chili555 on 2013-02-06
> Is there anything else than the speed I'll loose by choosing to use this?None that I am aware of. N speeds are mainly useful to stream video, etc. over a network. Very few of us have an internet connection where 54 Mb/s, the maximum afforded by 802.11G, is insufficient. There are, of course, exceptions. > Thanks for all the help by the way, pretty rare to find such nice and helpful people out there! Thank you for your very kind words. I had trouble finding any help of any kind when I started in Linux 200 years ago. I vowed to help as much as I could if I ever could.

I'm very glad it's working! Your experience added data to the knowledge base: ndiswrapper, WNA3100 and 802.11N probably doesn't work.

Would you please use thread tools at the top to mark solved. The searchers will appreciate it.

Finally, in post #16, we had to compile ndiswrapper from source. Every time you get a new kernel version, also known as linux-image, you'll need to re-compile:```
cd Skrivbord/ndiswrapper-1.58rc1
sudo su
make clean
make
make install
modprobe ndiswrapper
exit
```Please retain these instructions and the ndiswrapper-1.58rc1 folder for that day.

Have fun!

---

