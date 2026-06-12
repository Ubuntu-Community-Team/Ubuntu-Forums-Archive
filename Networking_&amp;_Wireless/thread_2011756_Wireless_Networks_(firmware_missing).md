---
title: "Wireless Networks (firmware missing)"
date: 2012-06-27
forum: Networking &amp; Wireless
---

### Post by jfkim on 2012-06-27
Hello,

I recently installed 12.04 on my macbook pro, and am unable to connect to my wifi network. It claims that the "device is not ready, firmware missing."
I'm connected through ethernet at the moment and when I try to use "Additional Drivers" from System Settings, it says "No proprietary drivers are in use on this system."
So I'm stumped as to what the problem is and what firmware I am missing. 

Any help would be greatly appreciated.
If it helps, after inputting "lspci" to terminal, I found this: 
03:00.0 Network controller: Broadcom Corporation BCM4331 802.11a/b/g/n (rev 02)

---

### Post by chili555 on 2012-06-27
We need just a bit more data. Please run and post:```
lspci -nn | grep 0280
```Thanks.

---

### Post by jfkim on 2012-06-27
Ok here is what I get after running lspci -nn | grep 0280

03:00.0 Network Controller [0280]: Broadcom Corporation BCM4331 802.11a/b/g/n [14e4:4331] (rev 02)

Thanks

---

### Post by chili555 on 2012-06-27
> Broadcom Corporation BCM4331 802.11a/b/g/n [[COLOR="Red"]14e4:4331[/COLOR]]Your device is supposed to work with the driver *bcma* that's already installed in 12.04. We wonder why it isn't working already. Please run and post:```
sudo modprobe bcma
dmesg | grep -e bcma -e wlan -e eth
```Thanks.

---

### Post by jfkim on 2012-06-27
This is what I get:

[    2.603960] i2c-core: driver [aat2870] using legacy suspend method
[    2.603961] i2c-core: driver [aat2870] using legacy resume method
[    4.993169] tg3 0000:02:00.0: eth0: Tigon3 [partno(BCM957765) rev 57785100] (PCI Express) MAC address 3c:07:54:03:10:d8
[    4.993173] tg3 0000:02:00.0: eth0: attached PHY is 57765 (10/100/1000Base-T Ethernet) (WireSpeed[1], EEE[1])
[    4.993176] tg3 0000:02:00.0: eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] TSOcap[1]
[    4.993178] tg3 0000:02:00.0: eth0: dma_rwctrl[00000001] dma_mask[64-bit]
[   18.588402] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   18.810378] bcma-pci-bridge 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   18.810393] bcma-pci-bridge 0000:03:00.0: setting latency timer to 64
[   18.810452] bcma: Core 0 found: ChipCommon (manuf 0x4BF, id 0x800, rev 0x25, class 0x0)
[   18.810477] bcma: Core 1 found: IEEE 802.11 (manuf 0x4BF, id 0x812, rev 0x1D, class 0x0)
[   18.810538] bcma: Core 2 found: PCIe (manuf 0x4BF, id 0x820, rev 0x13, class 0x0)
[   18.810683] bcma: PMU resource config unknown for device 0x4331
[   18.889200] bcma: Bus registered
[   20.703398] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   20.703778] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   20.752357] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   44.350594] tg3 0000:02:00.0: eth0: Link is up at 100 Mbps, full duplex
[   44.350597] tg3 0000:02:00.0: eth0: Flow control is off for TX and off for RX
[   44.350599] tg3 0000:02:00.0: eth0: EEE is disabled
[   44.350691] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   55.357911] eth0: no IPv6 routers present

---

### Post by chili555 on 2012-06-28
Please hook up the ethernet and try:```
sudo apt-get install linux-firmware-nonfree
sudo modprobe b43
dmesg | grep -e b43 -e bcma
```Thanks.

---

### Post by jfkim on 2012-06-28
Wow thank you so much, I am able to connect to wifi now. 

After inputting "dmesg | grep -e b43 -e bcma", It gives me this:
[   18.474782] bcma-pci-bridge 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   18.474798] bcma-pci-bridge 0000:03:00.0: setting latency timer to 64
[   18.474873] bcma: Core 0 found: ChipCommon (manuf 0x4BF, id 0x800, rev 0x25, class 0x0)
[   18.474902] bcma: Core 1 found: IEEE 802.11 (manuf 0x4BF, id 0x812, rev 0x1D, class 0x0)
[   18.474973] bcma: Core 2 found: PCIe (manuf 0x4BF, id 0x820, rev 0x13, class 0x0)
[   18.475145] bcma: PMU resource config unknown for device 0x4331
[   18.548891] bcma: Bus registered
[   18.688309] b43-phy0: Broadcom 4331 WLAN found (core revision 29)
[   20.624301] b43-phy0 ERROR: Firmware file "b43/ucode29_mimo.fw" not found
[   20.624306] b43-phy0 ERROR: Firmware file "b43-open/ucode29_mimo.fw" not found
[   20.624308] b43-phy0 ERROR: You must go to [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware for this driver version. Please carefully read all instructions on this website.

Do I need to follow these last instructions and download the firmware? The wifi is working perfectly now...

---

### Post by chili555 on 2012-06-28
> [ 20.624301] b43-phy0 ERROR: Firmware file "b43/ucode29_mimo.fw" not found
[ 20.624306] b43-phy0 ERROR: Firmware file "b43-open/ucode29_mimo.fw" not found
[ 20.624308] b43-phy0 ERROR: You must go to [http://wireless.kernel.org/en/users/...devicefirmware](http://wireless.kernel.org/en/users/...devicefirmware) and download the correct firmware for this driver version. Please carefully read all instructions on this website.

Do I need to follow these last instructions and download the firmware? The wifi is working perfectly now...If it's working perfectly, you probably don't need to do anything. If, on the other hand, you are an OCD nervous nellie like me that won't be able to sleep, I'd do so. Post back if you need assistance.

The 14e4:4331 is a new one to me. You will have helped quite a few searchers if you use thread tools at the top and mark Solved.

---

### Post by jfkim on 2012-06-28
Okay I followed the link, and it instructed me to input this command
sudo apt-get install firmware-b43-installer

And it came up with this: 

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  b43-fwcutter
The following NEW packages will be installed:
  b43-fwcutter firmware-b43-installer
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 22.4 kB of archives.
After this operation, 111 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/main b43-fwcutter i386 1:015-9 [18.9 kB]
Get:2 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/multiverse firmware-b43-installer all 1:015-9 [3,524 B]
Fetched 22.4 kB in 0s (58.3 kB/s)                   
Selecting previously unselected package b43-fwcutter.
(Reading database ... 167661 files and directories currently installed.)
Unpacking b43-fwcutter (from .../b43-fwcutter_1%3a015-9_i386.deb) ...
Selecting previously unselected package firmware-b43-installer.
Unpacking firmware-b43-installer (from .../firmware-b43-installer_1%3a015-9_all.deb) ...
Processing triggers for man-db ...
Setting up b43-fwcutter (1:015-9) ...
Setting up firmware-b43-installer (1:015-9) ...
No chroot environment found. Starting normal installation
Unsupported device(s) found: PCI id 14e4:4331 
Aborting.

However, this link: [http://wireless.kernel.org/en/users/Drivers/b43#Ubuntu.2FDebian](http://wireless.kernel.org/en/users/Drivers/b43#Ubuntu.2FDebian)
claims that it is supported..

---

### Post by chili555 on 2012-06-28
That's what we get for doing things the right way; wrong results! Oh, well.

Let's use the stone axe. Please download the attached file to your desktop and right-click it and select *Extract Here*. Now open a terminal and do:```
sudo cp Desktop/mimo/* /lib/firmware/b43
```Now we unload and reload the drivers so it sees the new firmware:```
sudo modprobe -r b43
sudo modprobe -r bcma
sudo modprobe b43
sudo modprobe bcma
```Are there any new messages?```
dmesg | grep -e b43 -e bcma
```Look later than your previous timestamp of [ [COLOR="Red"]20.624308[/COLOR]] b43-phy0 ERROR:

---

### Post by jfkim on 2012-06-28
Yes, the additional messages: 

[  341.390276] b43-phy0: Loading firmware version 666.2 (2011-02-23 01:15:07)
[ 2013.820740] bcma-pci-bridge 0000:03:00.0: PCI INT A disabled
[ 2015.460774] bcma-pci-bridge 0000:03:00.0: restoring config space at offset 0xf (was 0x100, writing 0x10b)
[ 2015.460817] bcma-pci-bridge 0000:03:00.0: restoring config space at offset 0x4 (was 0x4, writing 0xa0600004)
[ 2015.460825] bcma-pci-bridge 0000:03:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x40)
[ 2015.460837] bcma-pci-bridge 0000:03:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100006)
[ 2015.461521] bcma-pci-bridge 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[ 2015.461623] bcma: PMU resource config unknown for device 0x4331
[ 2018.765931] b43-phy0: Loading firmware version 666.2 (2011-02-23 01:15:07)
[ 2119.598180] b43-phy0: Loading firmware version 666.2 (2011-02-23 01:15:07)
[ 2246.764935] b43-phy0: Loading firmware version 666.2 (2011-02-23 01:15:07)
[ 3731.102952] b43-phy0: Loading firmware version 666.2 (2011-02-23 01:15:07)
[ 5778.827886] bcma-pci-bridge 0000:03:00.0: PCI INT A disabled
[ 5795.194549] bcma-pci-bridge 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[ 5795.194585] bcma-pci-bridge 0000:03:00.0: setting latency timer to 64
[ 5795.194695] bcma: Core 0 found: ChipCommon (manuf 0x4BF, id 0x800, rev 0x25, class 0x0)
[ 5795.194729] bcma: Core 1 found: IEEE 802.11 (manuf 0x4BF, id 0x812, rev 0x1D, class 0x0)
[ 5795.194797] bcma: Core 2 found: PCIe (manuf 0x4BF, id 0x820, rev 0x13, class 0x0)
[ 5795.194950] bcma: PMU resource config unknown for device 0x4331
[ 5795.267840] bcma: Bus registered
[ 5795.286018] b43-phy0: Broadcom 4331 WLAN found (core revision 29)

---

### Post by chili555 on 2012-06-28
Looks pretty solid! No errors or warnings. Is the wireless working well?

---

### Post by jfkim on 2012-06-28
It's working now, thanks so much for the help!

---

### Post by switchfoot123 on 2012-07-03
Okay. Newbie here.

I have an old Dell Inspiron 5100 that I installed linux on to get running again. It works through ethernet, as it is doing right now, but says that the wireless firmware is missing.

I don't know ANYTHING you guys just talked about (i don't really *do* much code), but would like a simple solution for those of you who are willing to help ;) thanks!

---

### Post by porterrakter on 2012-07-03
Coding is actually really easy.  Everything these guys just did here is done through Terminal/Command Line/whatever you like to call it.  You should be able to open it by pressing Ctrl+Alt+T or by finding it in an applications/accessories folder.  Simply type exactly the commands in terminal as instructed by this thread and you should get the results they have.  I just made my own wireless work five minutes ago by following their instructions.

Looks like a possible compressed solution would be simply to make sure your computer is hooked up to Ethernet (internet with cable), then open Terminal, type the following, and see if it works.  If it doesn't, go back through the thread and see if anything else can help.

```
sudo apt-get install linux-firmware-nonfree
sudo modprobe b43
```

Good luck!

---

### Post by switchfoot123 on 2012-07-03
i don't even know how to USE terminal. It keeps asking me for an admin password or something but I can't type. Haha. I need a "linux for dummies" :P

---

### Post by chili555 on 2012-07-03
It wants your user password. For security reasons, it's not echo'ed back. Just type it in and press Enter.

---

### Post by switchfoot123 on 2012-07-04
Yeah, that's not my issue though - the terminal physically won't let me enter my password. It won't let me type when it says [sudo] password for ____: -- but when i hit enter, it lets me type (obviously, that does no good).

---

### Post by chili555 on 2012-07-04
> **switchfoot123 said:**
> Yeah, that's not my issue though - the terminal physically won't let me enter my password. It won't let me type when it says [sudo] password for ____: -- but when i hit enter, it lets me type (obviously, that does no good).I assume you mean right here. Please see attached. Just type it in. You will *NOT* see any characters or even ****. Just type it in and press Enter. If the password you typed is correct, your command will proceed. If not, you will get a notification.

---

### Post by switchfoot123 on 2012-07-04
Okay, thanks! That worked.

I tried those lines of code - i did the first line, password, a whole bunch of stuff happened, then entered the second line. Wifi didn't work.

I then tried entering them both on the same line at the same time, and it was "unable to locate package modprobe" and the same with package b43. What now?

---

### Post by chili555 on 2012-07-04
Let's take a step back. You got a pretty quick answer above without verifying your exact device. Let's be sure that b43 is correct for your device. Please run and post:```
lspci -nn | grep 0280
```Put that all in one command. The pipe symbol | is on the right side of my US keyboard on the same key with \. You should get something, but not exactly like this:> 06:00.0 Network controller [0280]: [COLOR="Red"]Broadcom Corporation BCM4311 802.11b/g WLAN [**14e4:4311**][/COLOR] (rev 01)What I really most need is the parts I've highlighted. Post that and we'll get it fixed mighty quick!

---

### Post by switchfoot123 on 2012-07-04
Okay:

Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 02)

---

### Post by chili555 on 2012-07-04
> **switchfoot123 said:**
> Okay:

Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 02)b43 and nonfree firmware are, indeed, correct for your device. Let's see why it isn't working. Let's make sure the switch or key combination is set to enable wireless:```
rfkill list all
```Let's see if there are any interesting clues in the message file:```
dmesg | grep b43
```> i did the first line, password, a whole bunch of stuff happened,I assume it downloaded and installed firmware and *NOT* that it said 'eek, I can't.'

Thanks.

---

### Post by switchfoot123 on 2012-07-04
it's not being blocked, and i would paste the code, but now the firefox browser (even though it's hooked to ethernet) will not work. Server not found.

Here's the gist:

Firmware file "b43legecy/ucode4.fw" not found or load failed.
blah blah, you must go to linuxwireless.org/en/users/drivers/b43#devicefirmware and download the correct firmware (version 3).

---

### Post by chili555 on 2012-07-04
> Firmware file "[COLOR="Red"]b43legecy/ucode4.fw[/COLOR]" not found or load failed.b43legacy you say? Please do:```
sudo apt-get install firmware-b43legacy-installer
```Let it download and install the legacy firmware and when it's done, unload and reload the driver so it sees and grabs the shiny new firmware file:```
sudo modprobe -r b43
sudo modprobe b43
```Now is it working?

---

### Post by switchfoot123 on 2012-07-04
after the first line, i get "failed to fetch (url here) something wicked happened resolving us.archive.ubuntu.com.http (no address associated with hostname) unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

Could this have something to do that now my ethernet seems to be not working so I have no internet? At least in the browser it doesn't work

---

### Post by chili555 on 2012-07-04
> Could this have something to do that now my ethernet seems to be not working so I have no internet? Exactly. I suggest you click the Network Manager icon and disconnect and reconnect. If you are a fan of brute force like me, reboot.

---

### Post by switchfoot123 on 2012-07-04
Woohoo! That worked, the code worked, and everything is going good again! Thank you SO much for the help! Wifi is up!

---

### Post by chili555 on 2012-07-04
Awesome! Glad it's working.

---

### Post by Super Man on 2013-01-04
> **chili555 said:**
> That's what we get for doing things the right way; wrong results! Oh, well.

Let's use the stone axe. Please download the attached file to your desktop and right-click it and select *Extract Here*. Now open a terminal and do:```
sudo cp Desktop/mimo/* /lib/firmware/b43
```Now we unload and reload the drivers so it sees the new firmware:```
sudo modprobe -r b43
sudo modprobe -r bcma
sudo modprobe b43
sudo modprobe bcma
```Are there any new messages?```
dmesg | grep -e b43 -e bcma
```Look later than your previous timestamp of [ [COLOR="Red"]20.624308[/COLOR]] b43-phy0 ERROR:

Thanks to you, this works for me as well! But, after I reboot, I am back to square one and I have to redo all of the steps. Any ideas?

---

### Post by chili555 on 2013-01-04
> **Super Man said:**
> Thanks to you, this works for me as well! But, after I reboot, I am back to square one and I have to redo all of the steps. Any ideas?Please try this:```
sudo su
echo b43 >> /etc/modules
echo bcma >> /etc/modules
exit
```Now does it work as expected on reboot?

---

### Post by christopher1919 on 2013-01-14
> **chili555 said:**
> Please hook up the ethernet and try:```
sudo apt-get install linux-firmware-nonfree
sudo modprobe b43
dmesg | grep -e b43 -e bcma
```Thanks.

THIS WORKED 

OK, so have the Broadcom BCM4321 on a white macbook 4.1 (2.1 GHz, early 2008).  
I tried a few things to get the wifi to work and all the complicated instructions did not work, but the two lines above DID WORK (for me).

BUT TAKE NOTE others with a similar spec to mine: 
```
modprobe b43
``` killed the Ubuntu. At least the video died.:-({|= After a 

reboot from the power button I was surprised to find everything worked. :guitar: Wi-fi included. Seriously happy about this. I`m quite sure that the b43 driver isn`t even the correct one for this card, the recommended driver is the Linux STA from Broadcom.

I really wish there was some way to bring this thread to the attention of those in need, there is a lot of misleading info out there, and the Debian guide on getting wi-fi to work (I tried Deb before Ubu) is less than helpful.  

Additional: this was dualbooting with rEFInd (a fork of refit) which has a guide on how to dualboot Ubuntu on a mac here: [http://www.rodsbooks.com/ubuntu-efi/index.html](http://www.rodsbooks.com/ubuntu-efi/index.html)

---

