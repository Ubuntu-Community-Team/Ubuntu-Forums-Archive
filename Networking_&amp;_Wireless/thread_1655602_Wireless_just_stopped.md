---
title: "Wireless just stopped"
date: 2010-12-29
forum: Networking &amp; Wireless
---

### Post by Sailor5 on 2010-12-29
Greetings!

So I'm able to get back on the internet via ethercable but would preferably use wireless. for the last few days or so it's kept every now and then asking for the ecryption key to connect to our orange live box. However today no wireless connections appear under the right click menu. It just says Dissconnected under wireless networks.

iwconfid```
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:0  Noise level:0
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

vboxnet0  no wireless extensions.

```ifconfig```
eth0      Link encap:Ethernet  HWaddr 60:eb:69:35:4d:b5  
          inet addr:192.168.1.180  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::62eb:69ff:fe35:4db5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1037 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1095 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:957536 (957.5 KB)  TX bytes:265630 (265.6 KB)
          Interrupt:42 Base address:0xa000 

eth1      Link encap:Ethernet  HWaddr 00:26:82:91:c6:05  
          inet6 addr: fe80::226:82ff:fe91:c605/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

```Anyone know what the dillyo is going on?

---

### Post by PatchesTheCaveman on 2010-12-29
What version of Ubuntu are you running?

Also copy the output of:
```
lspci -v
```

---

### Post by Sailor5 on 2010-12-29
I'm using 10.10```
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge Alternate
    Subsystem: Hewlett-Packard Company Device 1604
    Flags: bus master, 66MHz, medium devsel, latency 0
    Capabilities: <access denied>

00:01.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (int gfx) (prog-if 00 [Normal decode])
    Flags: bus master, 66MHz, medium devsel, latency 64
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    I/O behind bridge: 00003000-00003fff
    Memory behind bridge: d0200000-d03fffff
    Prefetchable memory behind bridge: 00000000c0000000-00000000cfffffff
    Capabilities: <access denied>
    Kernel modules: shpchp

00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    I/O behind bridge: 00001000-00001fff
    Memory behind bridge: d0100000-d01fffff
    Prefetchable memory behind bridge: 00000000d0500000-00000000d06fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
    I/O behind bridge: 00002000-00002fff
    Memory behind bridge: d0700000-d07fffff
    Prefetchable memory behind bridge: 00000000d0000000-00000000d00fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode] (prog-if 01 [AHCI 1.0])
    Subsystem: Hewlett-Packard Company Device 1604
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 19
    I/O ports at 4038 [size=8]
    I/O ports at 404c [size=4]
    I/O ports at 4030 [size=8]
    I/O ports at 4048 [size=4]
    I/O ports at 4010 [size=16]
    Memory at d0408000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ahci
    Kernel modules: ahci

00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller (prog-if 10 [OHCI])
    Subsystem: Hewlett-Packard Company Device 1604
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
    Memory at d0407000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller (prog-if 20 [EHCI])
    Subsystem: Hewlett-Packard Company Device 1604
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
    Memory at d0408600 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller (prog-if 10 [OHCI])
    Subsystem: Hewlett-Packard Company Device 1604
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
    Memory at d0406000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller (prog-if 20 [EHCI])
    Subsystem: Hewlett-Packard Company Device 1604
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
    Memory at d0408500 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 41)
    Subsystem: Hewlett-Packard Company Device 1604
    Flags: 66MHz, medium devsel
    Kernel modules: i2c-piix4

00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA) (rev 40)
    Subsystem: Hewlett-Packard Company Device 1604
    Flags: bus master, slow devsel, latency 64, IRQ 16
    Memory at d0400000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller (rev 40)
    Subsystem: Hewlett-Packard Company Device 1604
    Flags: bus master, 66MHz, medium devsel, latency 0

00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge (rev 40) (prog-if 01 [Subtractive decode])
    Flags: bus master, 66MHz, medium devsel, latency 64
    Bus: primary=00, secondary=04, subordinate=04, sec-latency=64

00:14.5 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller (prog-if 10 [OHCI])
    Subsystem: Hewlett-Packard Company Device 1604
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
    Memory at d0405000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:16.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller (prog-if 10 [OHCI])
    Subsystem: Hewlett-Packard Company Device 1604
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
    Memory at d0404000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:16.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller (prog-if 20 [EHCI])
    Subsystem: Hewlett-Packard Company Device 1604
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
    Memory at d0408400 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration
    Flags: fast devsel
    Capabilities: <access denied>

00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Address Map
    Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller
    Flags: fast devsel

00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control
    Flags: fast devsel
    Capabilities: <access denied>
    Kernel driver in use: k10temp
    Kernel modules: k10temp

00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Link Control
    Flags: fast devsel

01:05.0 VGA compatible controller: ATI Technologies Inc M880G [Mobility Radeon HD 4200] (prog-if 00 [VGA controller])
    Subsystem: Hewlett-Packard Company Device 1604
    Flags: bus master, fast devsel, latency 0, IRQ 18
    Memory at c0000000 (32-bit, prefetchable) [size=256M]
    I/O ports at 3000 [size=256]
    Memory at d0300000 (32-bit, non-prefetchable) [size=64K]
    Memory at d0200000 (32-bit, non-prefetchable) [size=1M]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: <access denied>
    Kernel driver in use: fglrx_pci
    Kernel modules: fglrx, radeon

02:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g LP-PHY (rev 01)
    Subsystem: Hewlett-Packard Company Device 145c
    Flags: bus master, fast devsel, latency 0, IRQ 17
    Memory at d0100000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: wl
    Kernel modules: wl

03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
    Subsystem: Hewlett-Packard Company Device 1604
    Flags: bus master, fast devsel, latency 0, IRQ 42
    I/O ports at 2000 [size=256]
    Memory at d0010000 (64-bit, prefetchable) [size=4K]
    Memory at d0000000 (64-bit, prefetchable) [size=64K]
    Expansion ROM at d0020000 [disabled] [size=64K]
    Capabilities: <access denied>
    Kernel driver in use: r8169
    Kernel modules: r8169

```

---

### Post by PatchesTheCaveman on 2010-12-29
Did you recently install updates?

The 2.6.35-24-generic kernel update broke Broadcom wireless cards among nineteen thousand other things.  To check your kernel version, run ```
uname -r
```  If it says 2.6.35-24-generic, you have the broken kernel.

If you dual boot with Windows, look in your GRUB menu and find the 2.6.35-23-generic kernel and boot with that.  If you don't dual boot, you'll need to reboot and hold SHIFT before Ubuntu starts to get the GRUB menu.

If it says 2.6.35-23-generic or something lower, you're cool.  Let us know and maybe we can figure out what else it could be.  But don't install that upgrade no mattter what you do!

---

### Post by Bucky Ball on 2010-12-29
Get ESSID and security key (WEP, WPA, whatever) of your router. Then right click network icon and edit connections. Go to wireless, edit, and make sure you have the ESSID and security key in there, along with the details for your static IP if you are using one (gateway, mask, etc ...).

The new kernel is breaking Broadcom configs so also possible if you're using 2.6.35-24 kernel.

---

### Post by Sailor5 on 2010-12-29
> **PatchesTheCaveman said:**
> Did you recently install updates?

The 2.6.35-24-generic kernel update broke Broadcom wireless cards among nineteen thousand other things.

If you dual boot with Windows, look in your GRUB menu and find the 2.6.35-23-generic kernel and boot with that.  If you don't dual boot, you'll need to reboot and hold SHIFT before Ubuntu starts to get the GRUB menu.

I've done what you said however the wireless still doesn't see any connections. The outcome of uname -r is 2.6.35-23-generic

---

### Post by PatchesTheCaveman on 2010-12-29
> **Bucky Ball said:**
> The new kernel is breaking Broadcom configs so also possible if you're using 2.6.35-24 kernel.

The 2.6.35-24 kernel breaks all kinds of hardware, including Broadcom and Realtek wireless cards:

[http://ubuntuforums.org/showthread.php?t=1653568](http://ubuntuforums.org/showthread.php?t=1653568)

---

### Post by Sailor5 on 2010-12-29
> **PatchesTheCaveman said:**
> The 2.6.35-24 kernel breaks all kinds of hardware, including Broadcom and Realtek wireless cards:

[http://ubuntuforums.org/showthread.php?t=1653568](http://ubuntuforums.org/showthread.php?t=1653568)
I've booted into the kernel you suggested however I still can't connect to any wireless connections.

---

### Post by PatchesTheCaveman on 2010-12-29
> **Sailor5 said:**
> I've done what you said however the wireless still doesn't see any connections. The outcome of uname -r is 2.6.35-23-generic

It said that before you tried rebooting?  You don't have the 2.6.35-24 kernel in your GRUB menu at all?  In that case you have something else going on.  Make sure you don't install that update though.

Try right-clicking on your wireless icon, going to Edit Connections, switching to the wireless tab, erasing your wireless connection, then clicking on the wireless icon again and reconnecting and reentering your WEP/WPA key.  I've noticed I have to do that on occasion or it flat out refuses to connect to my Linksys router.

I'd reset your router before that too just in case.

---

### Post by Sailor5 on 2010-12-29
> **PatchesTheCaveman said:**
> It said that before you tried rebooting?  You don't have the 2.6.35-24 kernel in your GRUB menu at all?  In that case you have something else going on.  Make sure you don't install that update though.

Try right-clicking on your wireless icon, going to Edit Connections, switching to the wireless tab, erasing your wireless connection, then clicking on the wireless icon again and reconnecting and reentering your WEP/WPA key.  I've noticed I have to do that on occasion or it flat out refuses to connect to my Linksys router.

I'd reset your router before that too just in case.

There is both the 2.6.35-23 and the 2.6.35-24 kernel entries. After I selected the -23 one like you suggested I still can't see any wireless networks. I've now tried Manuely entering the SSID and wireless key but to no avail.

** I've left clicked the icon and selected 'connect to hidden wireless network' and entered the details and now it's constantly trying to connect. No joy :-(

---

### Post by PatchesTheCaveman on 2010-12-29
That's really strange.  When I went back to the 2.6.35-23 kernel everything Just Worked again.

As a matter of fact I booted into the busted kernel earlier to run some logs for the bug report and booted back into -23 and everything came back just fine.

I don't know if this will help but you can try uninstalling and reinstalling the  Broadcom wireless STA driver through System > Administration > Additional Drivers.  You might have better luck with the b43 driver in there too, although most of us usually do better with the STA driver.

---

### Post by sph on 2010-12-30
STA driver works for me where the b43 driver does not. When I wanted to activate the STA driver via system > administration > hardware drivers it responded with an error about my software source. 
I had it pointing to a Netherlands server and this server obviously is not the right one. Changing the software source to "main server" resolved this issue. In order to do this you need a working Internet connection, cable in my case.

Looking back the language setting had produced some error messages earlier on when I was installing 10.04 from CD.

---

### Post by Sailor5 on 2010-12-30
> **PatchesTheCaveman said:**
> That's really strange.  When I went back to the 2.6.35-23 kernel everything Just Worked again.

As a matter of fact I booted into the busted kernel earlier to run some logs for the bug report and booted back into -23 and everything came back just fine.

I don't know if this will help but you can try uninstalling and reinstalling the  Broadcom wireless STA driver through System > Administration > Additional Drivers.  You might have better luck with the b43 driver in there too, although most of us usually do better with the STA driver.

Removed and installed the driver again to no avail. Damn you wireless it seems to have a grudge with me. Also booted into ubuntu 9.04 live cd. Again no wireless.

** Anyone know anything else I can try do to get wireless back?

---

### Post by PatchesTheCaveman on 2010-12-30
Open a Terminal and run this:
```
dmesg | grep -i b43 && dmesg | grep -i wl
```

Copy and paste that into a reply here.  That'll show us if the kernel drivers are reporting any errors.

---

### Post by Sailor5 on 2010-12-30
> **PatchesTheCaveman said:**
> Open a Terminal and run this:
```
dmesg | grep -i b43 && dmesg | grep -i wl
```Copy and paste that into a reply here.  That'll show us if the kernel drivers are reporting any errors.

I entered what you said but it didn't come back with anything. Are you on ubuntu's irc network? It would be lot quicker to communicate.

---

### Post by PatchesTheCaveman on 2010-12-30
I just tried to see if ircii would let me connect to freenode (which hosts Ubuntu's IRC) but it's not cooperating.  I'm away for the holidays and only have dialup Internet at the present.  I have a proxy setup that accelerates the Web enough to be bearable but pretty much everything else is useless. :-/

I guess I screwed up that command I gave you though.  Sorry about that.  Just try:
```
dmesg | grep -i wl
```

---

### Post by Sailor5 on 2010-12-30
> **PatchesTheCaveman said:**
> I just tried to see if ircii would let me connect to freenode (which hosts Ubuntu's IRC) but it's not cooperating.  I'm away for the holidays and only have dialup Internet at the present.  I have a proxy setup that accelerates the Web enough to be bearable but pretty much everything else is useless. :-/

I guess I screwed up that command I gave you though.  Sorry about that.  Just try:
```
dmesg | grep -i wl
```

```
[   14.789827] wl: module license 'MIXED/Proprietary' taints kernel.
[   14.841793] wl 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   14.841800] wl 0000:02:00.0: setting latency timer to 64

```

If I left click it and select 'connect to hidden wireless network' and enter the details needed it just keeps trying to connect to my router. After every minute or so it will prompt me for the wireless key. Rinses and then repeats.

---

### Post by PatchesTheCaveman on 2010-12-30
Well nothing's going wrong with your driver.

Try:
```
sudo iwconfig eth1 scan
```

That scans for any wireless networks in the area.  Does that turn up anything?

If so it might just be NetworkManager that's FUBAR.

---

### Post by Sailor5 on 2010-12-30
> **PatchesTheCaveman said:**
> Well nothing's going wrong with your driver.

Try:
```
sudo iwconfig eth1 scan
```That scans for any wireless networks in the area.  Does that turn up anything?

If so it might just be NetworkManager that's FUBAR.

iwconfig has no command 'scan'. Which kernel version should I be booting into now? Still -23 or -24?

---

### Post by PatchesTheCaveman on 2010-12-30
Stick with -23.  -24 breaks the Broadcom STA driver.

And I'm sorry, the correct command is:
```
sudo iwlist eth1 scan
```

---

### Post by PatchesTheCaveman on 2010-12-30
If you want to, you can remove the broken kernel by running this command:
```
sudo apt-get remove linux-image-2.6.35-24-generic
```

I got a strange error when I did that, so out of an abundance of caution I also force reinstalled the working version of the kernel to make sure it will work okay next time I reboot:
```
sudo apt-get --reinstall install linux-image-2.6.35-23-generic
```

The error appeared to be harmless but I'd rather be safe than sorry.

---

### Post by Sailor5 on 2010-12-30
> **PatchesTheCaveman said:**
> Stick with -23.  -24 breaks the Broadcom STA driver.

And I'm sorry, the correct command is:
```
sudo iwlist eth1 scan
```

```
eth1      Failed to read scan data. :  Invaild argument
```

---

### Post by PatchesTheCaveman on 2010-12-30
Try flipping the wireless switch, or press the wireless button, or press the Fn key and the wireless button at the top of your keyboard.

That error almost always means the wireless switch is off.

I believe that busted kernel update is switching everyone's wireless off because we've been getting a lot of these recently.

---

### Post by Sailor5 on 2010-12-30
> **PatchesTheCaveman said:**
> Try flipping the wireless switch, or press the wireless button, or press the Fn key and the wireless button at the top of your keyboard.

That error almost always means the wireless switch is off.

I believe that busted kernel update is switching everyone's wireless off because we've been getting a lot of these recently.

A-Ha! It's come back on now! After all this a simple key press would have sufficed. I never even knew you could turn the wireless of via that way. Thanks a lot for your help! I would post a positive visitor message but I don't have enough posts.

---

### Post by electroken on 2010-12-30
I am new at this but I also installed Ubuntu 10.10 and I have that version of the kernel. I have not been able to reboot using the .24 which it installed I think at the first install nor the other one that is available ending in .22
I do not have the .23 version on my install as far as I can tell.
Is there any hope for me to restore my install? I wonder if I can use the 10.10 installation disk to make a repair to it? I have been trying to do that but no success so far.

I suppose I will have to re-install 10.10 or should I go back and install 10.04? 

If I go for a reinstall, will I be able to save all the installed programs I have put on the computer or will I be forced to start all over again?

This is not a good position to be in for a rookie...........

---

### Post by PatchesTheCaveman on 2010-12-30
Hi electroken!  I'm sorry you got bit by this irritating bug.

Do you have a working Internet connection?  If your wireless doesn't work try and plug in to a wired Ethernet connection.  Once you get a working Internet connection, you can remove the bad kernel and install a known working one pretty easily.

Just go to Applications > Accessories > Terminal on your top panel.  In the black box that appear, type in these three commands, pressing Enter after each one:
```
sudo apt-get update
sudo apt-get remove linux-image-2.6.35-24-generic
sudo apt-get install linux-image-2.6.35-23-generic
```

Let me know if you have any trouble.

---

### Post by electroken on 2010-12-31
Since I could not boot up in the installed version anymore I had to use a live boot disk and work from there and I think that it needs to do those things to the actual install and not the virtual disk. I get a response saying it could not find either of those linux images so i assume it is because they are not in the virtual install. How do I do that if I can only boot to the live disk etc? Can I install over the bad install and keep my added programs or do I have to start all over again? Can I do a repair? I am going to attempt to do that from the original disk I used to install ubuntu 10.10 as I suppose any other distro will only try to install over or alongside of the other one and not repair it or replace it.
Am I on the right track here? Thanks for the help so far.

---

### Post by electroken on 2011-01-01
Later in the day after trying to get this to work and getting nowhere........
I can boot up into the linux live version of 10.10 from the same disk I had used to install. Is it maybe possible to do what you wish to have me do from that session? I am not sure how to get to the correct place to do it but I have managed to mount all the computers drives including the one where I installed ubuntu in the first place. If it were an old dos system i could probably do this but this is pretty new to me. I would require a detailed step by step to get to the proper place to run those commands you gave me earlier so that they would work. Possible?

---

### Post by PatchesTheCaveman on 2011-01-01
I'm a little confused.  You can't boot your regular Ubuntu installation at all?

If so, you can follow these instructions to fix Ubuntu booting:
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#Overwriting%20the%20Master%20Boot%20Record](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#Overwriting%20the%20Master%20Boot%20Record)

Click on *1.4 Recovering the Master Boot Record*.  (I tried to link directly to that section but the forum software is clobbering the anchor tag.)  I know it says it's for recovering after a Windows install but it should fix it nonetheless.

If you are getting the GRUB linux bootloader but it's not booting properly, let me know what error you're getting and we can try and figure out what's going on.

---

### Post by electroken on 2011-01-01
Yeah I do get the option to load ubuntu of the various images such as the linux-image-2.6.35.24 (i think that is the one) and the restore for that one plus the image 2.6.35.22 etc
I am not able to boot up using them - not any of them at all - I get a stalled screen at some point with no progress after waiting for it to do something a couple of hours.
I was able to boot up using the install disk for Ubuntu 10.10 and then was able to mount all the disk drives. But I am sure I cannot, at the point, carry out the instructions given me earlier as it will be trying to write to the dvd i used for the boot up. 
I presume it might work if I could get to the correct directory etc
Is my easiest solution to re-install 10.10 or should I forgo doing that and just install 10.04 instead? I am not sure if I will be aware enough to prevent the 10.10 install from doing that update which will cause the problem over again. Any advice is appreciated.

---

### Post by perspectoff on 2011-01-01
Are you running your microwave oven (lol) ?

I personally hate Network Manager and only use Wicd.

I got tired of my wireless quitting, so I uninstalled all Network Manager-related modules and installed Wicd instead.

I have not had a single wireless problem since.

I did this on all my computers (whether they needed it or not). Much happier.

---

### Post by Bucky Ball on 2011-01-01
10.04 LTS is the current long term release and is supported until April 2013, one year longer than 10.10. Unless you really must have the latest release, I would give it a try. Different kernel, bit more stable, and the updates won't break your system. :)

---

### Post by electroken on 2011-01-01
Thank you. I guess that is what I will do then. I don't really have any data I will miss on the drive so I will overwrite it all. I want Ubuntu to be my system so it is worth the effort put forth here to make it happen. I would like to know someone close to my area in Mpls Minn to help me get through learning the ropes on Ubuntu. I have read all I can but there is nothing like doing to make it sink in. It would help a lot to have a group to meet or a mentor. I am at [email]kenlynes@usa.net[/email] if you have any suggestions.
Ken

---

### Post by Bucky Ball on 2011-01-02
Might try here:

[http://loco.ubuntu.com/](http://loco.ubuntu.com/)

(Edit: I did find a Minnesota team at that link but not very active by the looks. Chase up the contact. You could also post something in Community Cafe for people in your area. Feel free to post on the forums in future for any problems, of course. That's what it's here for! :))

You have a clean system so you can experiment with that for awhile (unless you need it up and running immediately!). 

If you have a blank drive, I would suggest partitioning something like this at least as basic:

/ = root partition where OS lives.
/home = all your stuff. 
/swap = swap partition (2Gb should do it).

You will find all of these as default selections but you can add whatever partitions you like to this with whatever names you choose. When you get to the partitioning section of the install choose the manual partitioning option, delete your current partitions then fire away. Choose EXT4 as the format for the partitions. Up to you to choose which size you want things to be, but the / partition for the OS really doesn't need to be that big. I usually go for about 12Gb but 20Gb might be nice if you have the space.

Good luck with it and keep us posted.

---

### Post by electroken on 2011-01-05
Thanks for the information.
I did reinstall and have the system running under 10.04 now. I have installed a number of programs including the wicd one but have seen on another link to wireless problems that the fellow who was helping the guy with the wireless problem said to use wicd but to uninstall the regular network manager which comes in the distro. He said he never had issues after he did that. I am wondering if, since I still have them both running on my machine it might account for he seemingless random disconnects i get for my wireless. I am using a D-link DIR-655 and a linksys wireless pci card WMP54GX with mimo and it has this remote antenna unit with the 3 antenna arms on it. It was a fancy one I got a few years ago and works really well.
One other item. I have a dvd copier program called Magic Dvd Copier and it is a legit copy which I bought btw. I am trying to use it within WINE on the Ubuntu install and I think it must require some special driver in order to use the dvd/RW to burn the disk copy. I get the following error when I try to run the program: DDE Failure
Magic DVD Copier will not let me specify the dvd-rom as the target drive and only lets me copy the vr mode video disk onto the computer but not burn the video mode copy Iam trying to make. The program is used to convert a vr mode video to the normal format. If you use a stand-alone dvd burner to record tv shows etc you will find that the recorders will only make vr recordings with a video_vr folder and a video_ts folder but nero nor any other copy program other than magic dvd copier will be able to make a copy of the disk and always shows a checksum error. 
Anyway I need to make the program work under ubuntu and so far it will not and gives me the error: DDE failure. I figure that is xp does not have the correct driver for the dvd burner.
Ahhhh aren't computers wonderful?

---

### Post by Bucky Ball on 2011-01-05
If you install wicd via Synaptics Package Manager (System->Admin) it removes Network Manager when it installs. Not sure why people give other instructions (especially to new users) when it is that easy. Wicd was not in the repositories in earlier versions so maybe they don't realise it is there now. ;)

As for your DVD issue: Post a separate thread. The title of the one bears no relation so you won't get a lot of help way back here in the thread. Much more in new one with descriptive title. ;)

(There is a WINE forum [here]("http://ubuntuforums.org/forumdisplay.php?f=313") which will be a lot more helpful.)

Have you tried Applications->Sound and Video->Brasero? You are better looking for a native app that can fit your needs. There's plenty out there.

---

### Post by electroken on 2011-01-07
I have been having some success and thank you very much for what you told me. I am going to one of the other sites you showed me and see if they have an answer. 
I was hesitant about using ubuntu and have now concluded that I will not use it as a dual boot at all as I can always have one of my computers which never gets on line, be used as a dos rat I have had great success so far and with almost no hands on guidance. Way better support than was ever there with a windows install. 
I have also been able to make a distro disk of my install using something called remastersys. It works like a charm and will enable me to spread ubuntu to several more users.

---

### Post by PatchesTheCaveman on 2011-01-07
> If you install wicd via Synaptics Package Manager (System->Admin) it removes Network Manager when it installs. Not sure why people give other instructions (especially to new users) when it is that easy.

Installing *wicd* via Synaptics does **not** automatically remove NetworkManager, at least on Maverick.

---

### Post by Bucky Ball on 2011-01-07
> **PatchesTheCaveman said:**
> Installing *wicd* via Synaptics does **not** automatically remove NetworkManager, at least on Maverick.

+1. Yep I just discovered that myself! It did on 8.04 LTS but that was a manual install and not through Synaptics. ;)

---

