---
title: "get rtl8192se to work"
date: 2009-07-10
forum: Networking &amp; Wireless
---

### Post by vralfy on 2009-07-10
Hi,  i've a new laptop with a rtl8192se wireless card. Everything works well, except the wireless connection. I tried to install the interface with ndiswrapper but this didn't work. I was able to get an wlan0 interface but I wasn't able to set the essid or the key.  Is there a way to install the RTL8192SE with correct drivers (kernel modules)?  

Laptop: Medion akoya E1312  
lspci:
```

00:00.0 Host bridge: ATI Technologies Inc RS690 Host Bridge
00:01.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx)
00:04.0 PCI bridge: ATI Technologies Inc Device 7914
00:05.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 1)
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS690M [Radeon X1200 Series]
01:05.2 Audio device: ATI Technologies Inc Radeon X1200 Series Audio Controller
02:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8172 (rev 10)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)

```

lsusb:
```

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

lshw -C network
```

*-network UNCLAIMED     
       description: Network controller
       product: Realtek Semiconductor Co., Ltd.
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 10
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress cap_list
       configuration: latency=0
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:24:21:6e:7a:71
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.178.37 latency=0 link=yes module=r8169 multicast=yes port=MII speed=100MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: f2:d8:78:df:76:d5
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

```
i deinstalled the ndiswrapper drivers ... (i think thats why the first device ist UNCLAIMED)

---

### Post by Crafty Kisses on 2009-07-10
Some bad news here, the 8172 chipset is reported not to work on Linux. I've done some research myself on this chipset and I haven't seen much on it, and when I have seen information on it people have not got it up and running, but I guess I can provide with you some instructions to try, and some other options for wireless cards. You can get the .inf for the 8172 chipset right **[here.]("http://www-307.ibm.com/pc/support/site.wss/document.do?sitestyle=lenovo&lndocid=MIGR-72700")** Once you have that, extract the file, and look for the .inf file. Then you said you already had ndiswrapper installed, but just to make sure, run:
```
sudo apt-get install ndidswrapper-common
```
Once you have that, install the driver by running:
```
ndiswrapper -i filename.inf
```
Then make sure if the driver is recognized by the ndiswrapper by running:
```
ndiswrapper -l
```
Now if ndiswrapper recognizes the driver, run these commands:
```
depmod -a
ndiswrapper -m
```
Then once you have that, you need to make the ndiswrapper module, so you can run:
```
modprobe ndiswrapper
```
Then make sure the ndiswrapper module is list, you can run:
```
lsmod | grep ndis
```
Once you have done that, you can now reboot and see if this works. Now again I'll doubt if this will work, because not many people have got this card to work, and from what I've seen nobody has gotten it to work sadly. Look over this **[link.]("https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported")** Try to pick a USB card out of the list, they usually run pretty cheap probably at most around 25 dollars.

---

### Post by vralfy on 2009-07-10
i allready tried ndiswrapper and it didn't work.
There is a patch under [http://patchwork.kernel.org/patch/33956/](http://patchwork.kernel.org/patch/33956/) but i don't know how to install it (or if it's possible)
also there is a git repository under: [http://git.kernel.org/?p=linux/kernel/git/gregkh/staging-2.6.git;a=tree;f=drivers/staging/rtl8192su;h=6b723d41b403b7d31fb4a69dff993f65a0ca2f76;hb=HEAD](http://git.kernel.org/?p=linux/kernel/git/gregkh/staging-2.6.git;a=tree;f=drivers/staging/rtl8192su;h=6b723d41b403b7d31fb4a69dff993f65a0ca2f76;hb=HEAD)

P.S its a 8192SE Card not 8172

---

### Post by Crafty Kisses on 2009-07-10
According to the **lspci** output, these are the results showed:
```
Network controller: Realtek Semiconductor Co., Ltd. Device 8172 (rev 10)
```

---

### Post by Crafty Kisses on 2009-07-10
I almost forgot, you asked on how to apply a patch for the wireless card. It's pretty simple in fact. The link provided does give me a download link to the patch. I'm not sure if you caught the link, but here is the link: [http://patchwork.kernel.org/patch/33956/raw/](http://patchwork.kernel.org/patch/33956/raw/). Then once you have got the patch, you can apply it by running:
```
patch -p1 < (path to patch)
```
So in essence, if you downloaded the patch to your desktop and your username is "vralf" you would do:
```
patch -p1 < /home/vralfy/Desktop/patch
```
That should apply the patch. If the patch does not work as intended you can always remove the patch and go back to the original state, you can do this usually by running:
```
patch -R < (path to patch)
```
As stated thought I'm not sure if it's the card is the rtl8192se, but if it is, that's how you would apply the patch for this card.

---

### Post by phillw on 2009-07-10
New Install, as in how new & which flavour ?

As this is completely destructive of your existing Ubuntu installation, may I implore (nag, insist) that you take a back-up

[http://ubuntuforums.org/showthread.php?t=35087&highlight=backup+restore+Ubuntu](http://ubuntuforums.org/showthread.php?t=35087&highlight=backup+restore+Ubuntu)

PLEASE !!!!!!!

If it is 9.04 and it is new ... if you backup the stuff you need, try this - it may sound mad, indeed it is, but it worked for my RealTek unit when all the other methods failed .....

Bear in mind that:

A) it is not the same device
B) you need to do a fresh install - And I mean from the very beginning - use the manual disk partitioning to delete, re-create & format your ext3(4) and swap to how you want it.

If you are prepared to do that, when all else fails - As it did for me.

Do NOT have the ethernet cable plugged in when you re-install.

And, it is that mad !!! - I found out completely by accident - I was that narked over the wireless stuff & had tried that many 'fixes' I spat my dummy out & did a complete re-install - Only I didn't have the Ethernet lead plugged in. It came back asking me to connect by WPA (When it could only see  WEP before) - And has been a happy bunny ever since.

So far, no one else has either tried to replicate it, or simply hasn't replied to me saying how they got on. 

No win-wrapping stuff - Ubuntu, left alone, simply got on with job in hand.

Please let me know how you get on.

Regards,

Phill.

---

### Post by vralfy on 2009-07-11
The original Windows driver let me think its the 8192SE Card. So i have only one question: Do i have to apply the patch on the Ubuntu kernel source or do i have to get the kernel source from kernel.org and apply the patch there?  I'm gonna try it, because it's a new fresh ubuntu install, and if it fails i can install a new ubuntu. So i have nothing to loose.  Bye  vralfy

---

### Post by aidanjt on 2009-07-13
> **Codename said:**
> According to the **lspci** output, these are the results showed:
```
Network controller: Realtek Semiconductor Co., Ltd. Device 8172 (rev 10)
```
That's because the device is unknown to lspci.  It's the pciid of the device, not the model number.

---

### Post by aidanjt on 2009-07-13
> **vralfy said:**
> The original Windows driver let me think its the 8192SE Card. So i have only one question: Do i have to apply the patch on the Ubuntu kernel source or do i have to get the kernel source from kernel.org and apply the patch there?  I'm gonna try it, because it's a new fresh ubuntu install, and if it fails i can install a new ubuntu. So i have nothing to loose.
To avoid conflicts, it's advised to patch against the vanilla sources version the patch was made for.  I'm working on the same problem myself, not even the realtek wlan drivers in the staging area work with this laptops wlan card atm.

There's also issues with the powernow-k8 driver due to a missing ACPI object in the BIOS, so CPU power management isn't working.

If you've already got Ubuntu 9.04 installed, don't bother with a reinstall, it wont solve anything.

---

### Post by aidanjt on 2009-07-13
Ok, I've been googling around.  It turns out that the rtl8192se code is being stripped from the rtl8192su drivers.  Someone is probably in the middle of making separate rtl8192se drivers.  So we'll have to wait for wireless support.

---

### Post by mjdavis on 2009-07-31
Have NDISwrapper working with the rtl8192se using a very specific driver:

The driver link is here: [http://www.station-drivers.com/telec...ivers.com).exe]("http://www.station-drivers.com/telechargement/realtek/wifi/rtl-8191se_1080.7.0520%28www.station-drivers.com%29.exe")

I used wine to extract the exe directly in linux as i didn't have a usbkey handy to copy it over.

Same ndiswrapper commands as before, brought up wlan0 (not using Ubuntu, but the latest OpenSUSE milestone). Looks like encryption does not work, but I'll tinker a bit.

Lenovo TP T400

uname -a
Linux linux-cijc 2.6.30.2-1-default #1 SMP 2009-07-20 20:31:16 +0200 i686 i686 i386 GNU/Linux

lspci:
03:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8172 (rev 10)

ndiswrapper -l
net8192se : driver installed
        device (10EC:8172) present

[ 8433.024724] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
[ 8433.040021] ndiswrapper: driver net8192se (Realtek Semiconductor Corp.,05/20/2009,1080.7.0520.2009) loaded
[ 8433.040604] ndiswrapper 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[ 8433.041406] ndiswrapper 0000:03:00.0: setting latency timer to 64
[ 8433.376098] ndiswrapper: using IRQ 17
[ 8433.752147] wlan0 (ndiswrapper): not using net_device_ops yet
[ 8433.754259] wlan0: ethernet device 00:24:2c:e7:24:5a using NDIS driver: net8192se, version: 0x500a5, NDIS version: 0x500, vendor: 'Realtek RTL8192SE Wireless LAN PCI-E NIC ', 10EC:8172.5.conf
[ 8433.754304] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK

iwconfig:
wlan0     IEEE 802.11g  ESSID:eek:ff/any
          Mode:Managed  Frequency:2.457 GHz  Access Point: Not-Associated
          Bit Rate:130 Mb/s   Tx-Power:20 dBm   Sensitivity=0/3
          RTS thr:eek:ff   Fragment thr:eek:ff
          Encryption key:eek:ff
          Power Management:eek:ff
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by chessplayer on 2009-08-31
This is to let you guys know that [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/401126](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/401126) has the solution. For me, at least, it worked perfectly [:)!]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/401126")
Just make sure you have WLAN turned on properly (see post #10 by Sweevo in the link above!). After that, connection to a WPA2 encrypted WLAN automagically worked! :cool:

---

### Post by 4ebees on 2009-10-07
> **chessplayer said:**
> This is to let you guys know that [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/401126](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/401126) has the solution. For me, at least, it worked perfectly [:)!]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/401126")
Just make sure you have WLAN turned on properly (see post #10 by Sweevo in the link above!). After that, connection to a WPA2 encrypted WLAN automagically worked! :cool:

Ack! So cloooooooooose.

Lenovo Thinkpad X200
Same chip as you guys
Using the Win2k driver and I have a green light on the wifi card...but I cannot connect to my router at home. I use WEP (yes, yes) but cannot connect. 
I can see all the surrounding wifi routers in the area, I can see mine.
I cannot &*W(W%Q connect.

Bugger.

Any suggestions for something to check up on?

Thanks all.

---

### Post by 4ebees on 2009-10-07
> **4ebees said:**
> Ack! So cloooooooooose.

Lenovo Thinkpad X200
Same chip as you guys
Using the Win2k driver and I have a green light on the wifi card...but I cannot connect to my router at home. I use WEP (yes, yes) but cannot connect. 
I can see all the surrounding wifi routers in the area, I can see mine.
I cannot &*W(W%Q connect.

Bugger.

Any suggestions for something to check up on?

Thanks all.


So - in commenting on my own post :)

I removed kdenetwork, wpa_supplicant and the other apps which were automatically selected for deletion when deleting Kdenetwork.

I installed Wicd and my wireless now works...and after a reboot I can get both wired and wireless.

I had to install RutilT WLAN manager and Wicd to achieve this.

Thanks everyone for your efforts. I started out the evening being rather annoyed and frustrated and ended being very excited and happy :)))

---

### Post by Sweevo on 2009-10-19
Just a quick update for any of you who are still trying to get this card (rtl8192se) working...

David Woo has just posted a reply back to my launchpad bug here: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/401126]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/401126") which contains a driver from Realtek.

I've tried to compile it on Karmic with Kernel 2.6.31-14-generic but I get the following error when I try and "sudo make install" ("make" completes successfully):

```
make[2]: Entering directory `/usr/src/linux-headers-2.6.31-14-generic'
  CHK include/linux/version.h
  CHK include/linux/utsrelease.h
  SYMLINK include/asm -> include/asm-x86
**make[3]: *** No rule to make target `kernel/bounds.c', needed by `kernel/bounds.s'. Stop.**
make[2]: *** [prepare0] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.31-14-generic'
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/home/mark/Desktop/rtl8192se_linux_2.6.0010.1012.2009/HAL/rtl8192'
make: *** [install] Error 2
```

I've made sure that the kernel headers and source and also build-essential are all installed, but still no luck.

I'm really interested to see if it works for you because I'm not sure if the problem is with my Karmic install or not.

Sweevo

---

### Post by stilgar1 on 2009-11-18
As I read on the [french ubuntu forum]("http://forum.ubuntu-fr.org/viewtopic.php?pid=3003220#p3003220"), you'll have to run both "make" and "make install" as root. After that it seems to run perfectly.

---

### Post by LinuxFanBoi on 2009-12-06
> **Sweevo said:**
> Just a quick update for any of you who are still trying to get this card (rtl8192se) working...

David Woo has just posted a reply back to my launchpad bug here: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/401126]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/401126") which contains a driver from Realtek.

I've tried to compile it on Karmic with Kernel 2.6.31-14-generic but I get the following error when I try and "sudo make install" ("make" completes successfully):

```
make[2]: Entering directory `/usr/src/linux-headers-2.6.31-14-generic'
  CHK include/linux/version.h
  CHK include/linux/utsrelease.h
  SYMLINK include/asm -> include/asm-x86
**make[3]: *** No rule to make target `kernel/bounds.c', needed by `kernel/bounds.s'. Stop.**
make[2]: *** [prepare0] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.31-14-generic'
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/home/mark/Desktop/rtl8192se_linux_2.6.0010.1012.2009/HAL/rtl8192'
make: *** [install] Error 2
```

I've made sure that the kernel headers and source and also build-essential are all installed, but still no luck.

I'm really interested to see if it works for you because I'm not sure if the problem is with my Karmic install or not.

Sweevo

follow the steps provided in the readme file except first enter 'sudo su'.  I had the same issue.

---

