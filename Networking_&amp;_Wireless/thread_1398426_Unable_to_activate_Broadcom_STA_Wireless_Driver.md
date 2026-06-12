---
title: "Unable to activate Broadcom STA Wireless Driver"
date: 2010-02-04
forum: Networking &amp; Wireless
---

### Post by bitterfriend99 on 2010-02-04
[SIZE=2]Hello.

I am using Linux Mint 8 Helena x64 Edition on Dell Studio 15 laptop which has Dell 1520 Wireless-N Mini Card. It does work when I boot from Live CD of Helena, connect to a wired network and download & install the proprietary drivers when prompted. But on the installed system, I am unable to activate the Broadcom STA driver. [/SIZE][SIZE=2]I tried completely removing and then reinstalling **bcmwl-kernel-source** and **dkms** packages from package manager.

[/SIZE][SIZE=2]When I go to **Administration -> Hardware Drivers** and click on Activate for Broadcom driver, at first there used to be a window which said *Downloading* and it used to go away after few seconds and nothing used to happen. Then I installed few updates. [/SIZE][SIZE=2]At the time of writing, I have installed all the available updates. [/SIZE][SIZE=2]Now after clicking on *Activate*, I get this error :
```
Sorry, installation of this driver failed.
Please have a look at the log file for detains: /var/log/jockey.log
```

[/SIZE][SIZE=2]I am attaching the *jockey.log* file with this post.

After googling, I found that it is a known bug in Ubuntu 9.10. Hasn't it been fixed yet? I badly need to use wireless network. What do I have to do to get my wireless working?

[Newbie] PS : It hasn't been long since I've been using a Linux distro. [/Newbie]
[/SIZE]

---

### Post by Iowan on 2010-02-04
[Here]("http://ubuntuforums.org/showthread.php?p=8770781#post8770781") is a similar thread - perhaps some of the suggestions will help solve your problem.

---

### Post by bitterfriend99 on 2010-02-05
Thank you [[COLOR=#339900]**Iowan**[/COLOR]]("http://ubuntuforums.org/member.php?u=65323") for your time.

Sadly, that thread couldn't solve my problem.

Actually my wireless card is BCM 4353, which I couldn't find listed on any of such bcm related threads.

Here is the result when I ran lspci :
```
[SIZE=2]xxxxx@xxxxx-laptop ~ $ lspci
00:00.0 Host bridge: Intel Corporation Arrandale DRAM Controller (rev 12)
00:01.0 PCI bridge: Intel Corporation Arrandale PCI Express x16 Root Port (rev 12)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 06)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 06)
00:1c.3 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 4 (rev 06)
00:1c.4 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 5 (rev 06)
00:1c.5 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 6 (rev 06)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a6)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 06)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 06)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 06)
02:00.0 VGA compatible controller: ATI Technologies Inc M92 [Mobility Radeon HD 4500 Series]
02:00.1 Audio device: ATI Technologies Inc R700 Audio Device [Radeon HD 4000 Series]
04:00.0 Network controller: Broadcom Corporation Device 4353 (rev 01)
07:00.0 SD Host controller: Ricoh Co Ltd Device e822 (rev 01)
07:00.1 System peripheral: Ricoh Co Ltd Device e230 (rev 01)
07:00.2 System peripheral: Ricoh Co Ltd Device e852 (rev 01)
07:00.3 FireWire (IEEE 1394): Ricoh Co Ltd Device e832 (rev 01)
09:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
ff:00.0 Host bridge: Intel Corporation QuickPath Architecture Generic Non-core Registers (rev 02)
ff:00.1 Host bridge: Intel Corporation QuickPath Architecture System Address Decoder (rev 02)
ff:02.0 Host bridge: Intel Corporation QPI Link 0 (rev 02)
ff:02.1 Host bridge: Intel Corporation QPI Physical 0 (rev 02)
ff:02.2 Host bridge: Intel Corporation Device 2d12 (rev 02)
ff:02.3 Host bridge: Intel Corporation Device 2d13 (rev 02)
[/SIZE]
```

And relevant part of result of lspci -vvnn :
```
[SIZE=2]04:00.0 Network controller [0280]: Broadcom Corporation Device [14e4:4353] (rev 01)
   Subsystem: Dell Device [1028:000e]
   Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
   Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
   Latency: 0, Cache Line Size: 64 bytes
   Interrupt: pin A routed to IRQ 7
   Region 0: Memory at f0500000 (64-bit, non-prefetchable) [size=16K]
   Capabilities: <access denied>[/SIZE]
```


After referring the tutorial [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx) (which I found in the thread pointed by you), I installed **b43-fwcutter** package (though 4353 is not listed there *particularly*). Also ran apt update on bcmwl-kernel-source and dkms. bcmwl-kernel-source was updated, while dkms was already up-to-date. I still get the same error. The current jockey.log file (after installing fwcutter and running apt update) is here : [http://pastebin.com/f3cf50669](http://pastebin.com/f3cf50669)

---

### Post by bkratz on 2010-02-05
I did find this interesting thread that says that this device is 
usable with the "wl" driver which is what the 4311,12,21,22 use.
[http://forums.fedoraforum.org/showthread.php?t=230901](http://forums.fedoraforum.org/showthread.php?t=230901)

So maybe something here will work ( I hope)
[http://ubuntuforums.org/showthread.php?t=1368699](http://ubuntuforums.org/showthread.php?t=1368699)
Will keep looking though

---

### Post by bkratz on 2010-02-05
This might also be helpful ( still looking) see the readme.

[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)


Here is another

[http://forums.opensuse.org/network-internet/wireless/424101-broadcom-4353-a.html](http://forums.opensuse.org/network-internet/wireless/424101-broadcom-4353-a.html)

---

### Post by bitterfriend99 on 2010-02-05
> **bkratz said:**
> This might also be helpful ( still looking) see the readme.

[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)


Can't thank you enough bkratz! Are you a doctor? If you are, I could use your help *again*, because I just broke my head while jumping excitedly... :lolflag:

Here is how to get the Broadcom BCM4353 card to work :

]
[LIST]
[*][SIZE=2]Do not install any proprietary drivers when prompted. Remove the bcmwl-kernel-source package if it is installed.[/SIZE]
[*][SIZE=2]Download the appropriate driver (for x86 or x64) from here : [/SIZE][SIZE=2][http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)[/SIZE]
[*][SIZE=2]Follow the instructions in README.txt.[/SIZE]
[*][SIZE=2]Note : In instruction **4** in README, you will need root's privilege to execute *modprobe* and *insmod*. You can issue sudo.
[/SIZE]
[*][SIZE=2]However, you have to load the module (issue modprobe and insmod) *every time *you boot. You may write a shell script and set it to execute at every boot.[/SIZE]
[/LIST]

---

### Post by bkratz on 2010-02-05
> **bitterfriend99 said:**
> [SIZE=2]

Can't thank you enough bkratz! Are you a doctor? If you are, I could use your help *again*, because I just broke my head while jumping excitedly... :lolflag:

Here is how to get the Broadcom BCM4353 card to work :

[/SIZE]
[LIST]
[*][SIZE=2]Do not install any proprietary drivers when prompted. Remove the bcmwl-kernel-source package if it is installed.[/SIZE]
[*][SIZE=2]Download the appropriate driver (for x86 or x64) from here : [/SIZE][SIZE=2][http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)[/SIZE]
[*][SIZE=2]Follow the instructions in README.txt.[/SIZE]
[*][SIZE=2]Note : In instruction **4** in README, you will need root's privilege to execute *modprobe* and *insmod*. You can issue sudo.
[/SIZE]
[*][SIZE=2]However, you have to load the module (issue modprobe and insmod) *every time *you boot. You may write a shell script and set it to execute at every boot.[/SIZE]
[/LIST]

No, the only doctor around here is Chili555! Anyway, I am happy that you got it working and appreciate your directions on how to do so. I am going to file this one away for future reference.

---

### Post by paradox82 on 2010-02-08
I had very similar problem on my HP mini 210 and managed to fix it by running "sudo apt-get dist-upgrade". Seems its fixed in the new kernel 31.19.

---

### Post by Caps18 on 2010-06-21
> **paradox82 said:**
> I had very similar problem on my HP mini 210 and managed to fix it by running "sudo apt-get dist-upgrade". Seems its fixed in the new kernel 31.19.

It seems like they broke it again in 32.22 (Linux Mint 9).  All I did was install the audio drivers, and it made my wireless card stop working.

---

### Post by soxos on 2010-07-26
Hi,
had the same problem with my new Dell Vostro 3500
Broadcom 4543

The matter was just to go to System -> Administration -> Hardware Drivers

The driver was there, but waiting a confirmation to be installed as it was not developed by Ubuntu devs.

pretty sweet.

---

### Post by REDII on 2011-10-18
Okay I am at a loss here I've tried several things. this actually went through right away on ubuntu but i'm having some problems with it on mint 11 I know this isn't a forum for mint but I've been running around like crazy looking for a fix I tried to use virtual box to open windows 7 and then turn on the hardware switch but I couldn't get it to boot windows from my hdd. then I tried the update and even to take the files and install them from the flash drive. I am just not finding a way to get my computers wireless hardware switch to turn on. - - - on a side note it even states that my Broadcom STA wireless driver is activated...

---

