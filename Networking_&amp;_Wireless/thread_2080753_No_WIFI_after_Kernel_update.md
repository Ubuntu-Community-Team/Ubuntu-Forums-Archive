---
title: "No WIFI after Kernel update"
date: 2012-11-04
forum: Networking &amp; Wireless
---

### Post by CShaum on 2012-11-04
I lost my WIFI connection after kernel 2.6.32.42 update.  I have a BCM4311 and been using the STA Wireless driver for several yrs now and been working fine did the kernel update it quit working. I tried to activate it and the error messages says it failed to load and also it says it's not supported and so what changed?? And it appears as though my wired connection quit too. Thanks for your help.

---

### Post by chili555 on 2012-11-05
Let's troubleshoot:```
lspci -nn | grep -e 0200 -e 0280
```Thanks.

---

### Post by CShaum on 2012-11-05
I guess I wrote a bit to quick. I got it to work by installing firmware b43 installer and b43 fwcutter. The wireless works. I should double check my ethernet card. Thanks for wanting to help:). Hmmm... how do I mark that its solved??

---

### Post by pccampos on 2012-11-06
The same happened to me after the 3.5.0-18-generic update. Installing b43 installer and b43 fwcutter didn't solved the issue. Here is the debug code:

```
$ lspci -nn | grep -e 0200 -e 0280
02:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01)
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 06)
04:00.0 USB controller [0c03]: NEC Corporation uPD720200 USB 3.0 Host Controller [1033:0194] (rev 04)

```

---

### Post by chili555 on 2012-11-06
> **pccampos said:**
> The same happened to me after the 3.5.0-18-generic update. Installing b43 installer and b43 fwcutter didn't solved the issue. Here is the debug code:

```
$ lspci -nn | grep -e 0200 -e 0280
02:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01)
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 06)
04:00.0 USB controller [0c03]: NEC Corporation uPD720200 USB 3.0 Host Controller [1033:0194] (rev 04)

```Please hook up the ethernet and do:```
sudo apt-get install bcmwl-kernel-source
```Reboot and you should be all set.

---

### Post by pccampos on 2012-11-06
It is already installed.

---

### Post by chili555 on 2012-11-06
Does your wireless come to life when you do:```
sudo modprobe wl
```

---

### Post by Oral B Sonic Complete on 2012-11-06
I have a similar problem with a Broadcom BCM4313 WLAN controller. 5 minutes ago, before Ubuntu ran some updates, it was fine. 
Here is the Code shown after entering *lspci -nn | grep -e 0200 -e 0280* :

04:00.0 Network Controller [[COLOR="Red"]0280[/COLOR]]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727 (rev 01)
06:00.0 Ethernet controller [[COLOR="red"]0200[/COLOR]]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)

I already tried the second solution provided in this thread, but it did not change anything. wireless is still broken. :( 
I am using 12.10 Quantal Desktop. 
I am new here, so just assume that i have never ever worked with ubuntu.. i know bits and pieces, but thats about it.

---

### Post by chili555 on 2012-11-06
> **Oral B Sonic Complete said:**
> I have a similar problem with a Broadcom BCM4313 WLAN controller. 5 minutes ago, before Ubuntu ran some updates, it was fine. 
Here is the Code shown after entering *lspci -nn | grep -e 0200 -e 0280* :

04:00.0 Network Controller [[COLOR="Red"]0280[/COLOR]]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727 (rev 01)
06:00.0 Ethernet controller [[COLOR="red"]0200[/COLOR]]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)

I already tried the second solution provided in this thread, but it did not change anything. wireless is still broken. :( 
I am using 12.10 Quantal Desktop. 
I am new here, so just assume that i have never ever worked with ubuntu.. i know bits and pieces, but thats about it.Please make sure the ethernet is hooked up.Open a terminal and do:```
sudo apt-get install --reinstall bcmwl-kernel-source
sudo modprobe wl
```Let us know if it's fixed or if there is an error or warning.

---

### Post by Oral B Sonic Complete on 2012-11-06
I get an Error when entering the first sudo command. 

E: Unable to locate package bcwml-kernel-source

sudo modprobe wl gives me this message: 

FATAL: Module wl not found. 

I tried to install Wine 1.4 before i restarted due to updates. However, i couldnt finish because i couldnt agree to Microsofts terms and conditions. The OK button wouldnt respond, and enter wouldnt do anything either. 
Could that be part of the problem??

---

### Post by chili555 on 2012-11-06
Anything's possible but, in this case, I think it's doubtful.> E: Unable to locate package bcwml-kernel-sourceAre you sure you have an internet connection? It is certainly in the Ubuntu repositories.

---

### Post by Oral B Sonic Complete on 2012-11-06
It certainly does. I am writing this post from ubuntu with my ethernet cable plugged in.

---

### Post by chili555 on 2012-11-06
Oops! I said:> sudo apt-get install --reinstall [COLOR="Red"]bcmwl[/COLOR]-kernel-source
sudo modprobe wlYou evidently said something else:> E: Unable to locate package bc[COLOR="Red"]wm[/COLOR]l-kernel-sourcePlease try again.

---

### Post by Oral B Sonic Complete on 2012-11-06
Okay, no errors this time, but it still does not work. Bluetooth does though, and I am not sure whether this is relevant , but i think the Windows drivers are distributed as one .exe.

---

### Post by chili555 on 2012-11-06
> I am not sure whether this is relevant , but i think the Windows drivers are distributed as one .exe.Why might it be relevant? Are you trying or have you tried to install the Windows drivers under ndiswrapper?

What does this tell us?```
sudo modprobe ndiswrapper
iwconfig
dmesg | grep -e wl -e eth1
rfkill list all
```

---

### Post by hofko on 2012-11-06
Same problem here and none of the solutions above don't seem to work. 
And I get these messages:

sudo modprobe wl
FATAL: Module wl not found.

sudo modprobe ndiswrapper
FATAL: Module ndiswrapper not found.

---

### Post by Oral B Sonic Complete on 2012-11-06
No, i havent tried to install any drivers... 
here is what i got: 

sudo modprobe ndiswrapper
FATAL: Module ndiswrapper not found.
R252B:~$ iwconfig
eth0      no wireless extensions.

lo        no wireless extensions.

R252B:~$ dmesg | grep -e wl -e ethl
[COLOR=SeaGreen]*(Is there supposed to be nothing below this??)*[/COLOR]
R252B:~$ rfkill list all
0: asus-wlan: Wireless LAN
    Soft blocked: yes
    Hard blocked: no
1: asus-bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: no

---

### Post by chili555 on 2012-11-06
I wanted to find out if ndiswrapper was present and therefor interfering. Evidently not. Try this, both of you:```
sudo modprobe wl
dmesg | grep wl
```Any errors or warnings are significant, please post them.

---

### Post by hofko on 2012-11-07
After first command it says:
> FATAL: Module wl not found.
And after second:
> [    0.000000] DMI: Hewlett-Packard HP Pavilion dv6 Notebook PC/3628, BIOS F.36 10/09/2009
[    0.000000] BIOS vendor: Hewlett-Packard; Ver: F.36; Product Version: Rev 1
[   19.181766] ACPI Error: [_T_1] Namespace lookup failure, AE_ALREADY_EXISTS (20120320/dswload2-316)
[   19.184254] ACPI Error: [_T_1] Namespace lookup failure, AE_ALREADY_EXISTS (20120320/dswload2-316)
[  535.039322] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  535.040521] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  537.140852] wlan0: authenticate with c0:c1:c0:2b:6b:8c
[  537.234875] wlan0: send auth to c0:c1:c0:2b:6b:8c (try 1/3)
[  537.236693] wlan0: authenticated
[  537.284029] wlan0: associate with c0:c1:c0:2b:6b:8c (try 1/3)
[  537.286427] wlan0: RX AssocResp from c0:c1:c0:2b:6b:8c (capab=0x411 status=0 aid=4)
[  537.292773] wlan0: associated
[  537.293569] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  550.847264] wlan0: deauthenticating from c0:c1:c0:2b:6b:8c by local choice (reason=3)
[  559.452942] wlan0: authenticate with c0:c1:c0:2b:6b:8c
[  559.551179] wlan0: send auth to c0:c1:c0:2b:6b:8c (try 1/3)
[  559.553905] wlan0: authenticated
[  559.600028] wlan0: associate with c0:c1:c0:2b:6b:8c (try 1/3)
[  559.602530] wlan0: RX AssocResp from c0:c1:c0:2b:6b:8c (capab=0x411 status=0 aid=4)
[  559.607487] wlan0: associated
[  565.071928] wlan0: deauthenticating from c0:c1:c0:2b:6b:8c by local choice (reason=3)
[  572.972038] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  572.973406] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  575.064932] wlan0: authenticate with c0:c1:c0:2b:6b:8c
[  575.159957] wlan0: send auth to c0:c1:c0:2b:6b:8c (try 1/3)
[  575.161932] wlan0: authenticated
[  575.216073] wlan0: associate with c0:c1:c0:2b:6b:8c (try 1/3)
[  575.218405] wlan0: RX AssocResp from c0:c1:c0:2b:6b:8c (capab=0x411 status=0 aid=4)
[  575.223254] wlan0: associated
[  575.223854] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 3290.314258] wlan0: deauthenticating from c0:c1:c0:2b:6b:8c by local choice (reason=3)
[ 3298.286258] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 3300.388762] wlan0: authenticate with c0:c1:c0:2b:6b:8c
[ 3300.460991] wlan0: send auth to c0:c1:c0:2b:6b:8c (try 1/3)
[ 3321.107898] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 3321.108239] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 3323.180712] wlan0: authenticate with c0:c1:c0:2b:6b:8c
[ 3323.279091] wlan0: send auth to c0:c1:c0:2b:6b:8c (try 1/3)
[ 3323.280959] wlan0: authenticated
[ 3323.328102] wlan0: associate with c0:c1:c0:2b:6b:8c (try 1/3)
[ 3323.330587] wlan0: RX AssocResp from c0:c1:c0:2b:6b:8c (capab=0x411 status=0 aid=5)
[ 3323.335539] wlan0: associated
[ 3323.336035] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready

And that was done an usb wifi adapter was plugged in, if it matters.

---

### Post by chili555 on 2012-11-07
> And that was done an usb wifi adapter was plugged in, if it matters.So you don't have and are not trying to troubleshoot an internal Broadcom device??? These fixes aren't going to help you then. Am I missing something?

---

### Post by Oral B Sonic Complete on 2012-11-07
Okay, sorry for taking some time, but here are my results: 
R252B:~$ sudo modprobe wl
[sudo] password for shaarred: 
FATAL: Module wl not found.
R252B:~$ dmesg | grep wl

nothing else.

---

### Post by chili555 on 2012-11-07
With the ethernet hooked up, please do:```
sudo apt-get install linux-headers-generic
sudo apt-get install --reinstall bcmwl-kernel-source
sudo modprobe wl
```*Now* does it load and does your wireless work as expected?

---

### Post by Oral B Sonic Complete on 2012-11-07
YES!! After the second command, lots of things happened on the console, and about 1,5 minutes later the Wireless connection just popped up. Thank you so much... 
:) Happiness!!

---

### Post by chili555 on 2012-11-07
Awesome! Glad it's working.

---

### Post by Oral B Sonic Complete on 2012-11-07
I just rebooted, itts still working and the Laptop boots somewhat faster now. :)

---

### Post by unitedoceanic on 2012-11-24
is there a way to do this without internet connection?

i installed 12.10 64bit on a lenovo s205 netbook the problem is that it only has wifi no lan

---

### Post by chili555 on 2012-11-24
> **unitedoceanic said:**
> is there a way to do this without internet connection?

i installed 12.10 64bit on a lenovo s205 netbook the problem is that it only has wifi no lanDo you still have your install CD? Drop it in the tray and navigate to pool > restricted > b > bcmwl. Right-click the package and select 'Open with Ubuntu Software Center.'

Do you have the exact same device?```
lspci -nn | grep 0280
```

---

### Post by unitedoceanic on 2012-11-25
thank you for the quick response

the output of 

```
lspci -nn | grep 0280
```

is 

```
03:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n/ Wireless LAN Controller [14e4:4727] (rev01)
```

i have a 12.10 64 bit live usb stick and found the package, opened it with the software center but could not install it the button "reinstall" is greyed out

---

### Post by chili555 on 2012-11-25
It apparently is missing a dependency. Please drag and drop the file to your desktop. Open a terminal and do:```
sudo dpkg -i Desktop/bcm*.deb
```If there is something missing, the terminal will tell us and we'll go get it.

---

### Post by unitedoceanic on 2012-11-25
it seems there pretty much missing

not sure if its relevant to this issue, ubuntu does not boot ever time, it freezes a few moments before the desktop should show up.

here is the terminal output:

```
ingrid@Red-Princess:~/Arbeitsfläche$ sudo dpkg -i bcm*.deb
(Lese Datenbank ... 149596 Dateien und Verzeichnisse sind derzeit installiert.)
Vorbereitung zum Ersetzen von bcmwl-kernel-source 5.100.82.112+bdcom-0ubuntu3 (durch bcmwl-kernel-source_5.100.82.112+bdcom-0ubuntu3_amd64.deb) ...
Removing all DKMS Modules
Done.
Ersatz für bcmwl-kernel-source wird entpackt ...
bcmwl-kernel-source (5.100.82.112+bdcom-0ubuntu3) wird eingerichtet ...
Loading new bcmwl-5.100.82.112+bdcom DKMS files...
Building only for 3.5.0-18-generic
Building for architecture x86_64
Module build for the currently running kernel was skipped since the
kernel source for this kernel does not seem to be installed.
ERROR: Module b43 does not exist in /proc/modules
ERROR: Module b43legacy does not exist in /proc/modules
ERROR: Module ssb does not exist in /proc/modules
ERROR: Module bcm43xx does not exist in /proc/modules
ERROR: Module brcm80211 does not exist in /proc/modules
ERROR: Module brcmfmac does not exist in /proc/modules
ERROR: Module brcmsmac does not exist in /proc/modules
ERROR: Module bcma does not exist in /proc/modules
FATAL: Module wl not found.
update-initramfs: deferring update (trigger activated)
Trigger für initramfs-tools werden verarbeitet ...
update-initramfs: Generating /boot/initrd.img-3.5.0-18-generic

```

---

### Post by chili555 on 2012-11-25
> Module build for the currently running kernel was skipped since the
kernel source for this kernel does not seem to be installed.There we go! You will need to install the linux headers from here: [http://packages.ubuntu.com/quantal-updates/linux-headers-3.5.0-18](http://packages.ubuntu.com/quantal-updates/linux-headers-3.5.0-18)

Also this: [http://packages.ubuntu.com/quantal-updates/devel/linux-headers-generic](http://packages.ubuntu.com/quantal-updates/devel/linux-headers-generic)  Be sure to get the amd64 version, since you run a 64-bit system. Install those packages as above. Then remove and re-install bcmwl-kernel-source:```
sudo dpkg -P bcmwl-kernel-source
sudo dpkg -i bcmwl*.deb
```Hopefully, we have overcome the 'skipped' problem.

---

### Post by unitedoceanic on 2012-11-25
you are just awesome!! it works!

thank you very much for your help and your effort!!

---

### Post by chili555 on 2012-11-25
> **unitedoceanic said:**
> you are just awesome!! it works!

thank you very much for your help and your effort!!I'm very glad it's working. Have fun!

---

