---
title: "ubuntu 7.04 wireless drivers not working"
date: 2010-12-31
forum: Networking &amp; Wireless
---

### Post by vase070 on 2010-12-31
i have ubuntu 7.04 and i have wireless driver 
Atheros Hardware Access Layer (HAL)
but i cant get it to work 
in restricted drivers it's checked as enabled but status is not in use how do i fix this 
see here 
[IMG]http://www.postimg.com/27000/26423.jpg[/IMG]

---

### Post by PatchesTheCaveman on 2010-12-31
Hi vase070!  Sorry you're having trouble with your Atheros wireless network card.

Go to Applications > Accessories > Terminal on your top panel.  In the black box that appears, type the following and press Enter:
```
lspci -v
```

Copy and paste what appears into a reply to this thread.  That will help us figure out what's going on.

---

### Post by ajgreeny on 2010-12-31
Ubuntu 7.04!  Really 7.04?

You should update really, as 7.04 is not supported any more, so you will not get updates or be able to add any packages from repositories.

---

### Post by PatchesTheCaveman on 2010-12-31
> you will not get updates or be able to add any packages from repositories

They disable the repos for older versions?  I know they won't give any future updates but you ought to still be able to download the old packages.

---

### Post by ajgreeny on 2010-12-31
> **PatchesTheCaveman said:**
> They disable the repos for older versions?  I know they won't give any future updates but you ought to still be able to download the old packages.
Yes, you can still install old packages but not using the repositories as the system will have by default.  The sources.list file will have to be a custom version, which points to the end of life repos.

have a long look at [https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades) and you may decide that it is quicker and easier to start again with a clean install

---

### Post by vase070 on 2010-12-31
guys guys i don't care much about updates and resporitories  i just like to get my wireless driver working if possible :confused:

---

### Post by ajgreeny on 2010-12-31
> **vase070 said:**
> guys guys i don't care much about updates and resporitories  i just like to get my wireless driver working if possible :confused:
Well, I'm sorry but that is not going to be straightforward with no repositories available.  You may be able to get the package needed from nvidia direct, but even they are unlikely to have one for 7.04.

I'll have to bow out here, as I don't even have an nvidia card which I can use so as to know more about the drivers needed and available for them.

---

### Post by PatchesTheCaveman on 2010-12-31
Well I'll give it a shot, but I'll still need the output of that command I asked you to run in my previous post.

---

### Post by vase070 on 2011-01-01
is there a google chrome version for ubuntu 7.04  :neutral::neutral:

---

### Post by vase070 on 2011-01-26
[PatchesTheCaveman]("http://ubuntuforums.org/member.php?u=922660") today i will post the output of that command i hope you will be able to help me

---

### Post by vase070 on 2011-01-26
00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02)
        Subsystem: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub
        Flags: bus master, fast devsel, latency 0
        Capabilities: <access denied>

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
        Subsystem: Micro-Star International Co., Ltd. Unknown device 7267
        Flags: bus master, fast devsel, latency 0, IRQ 16
        Memory at cfe3c000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        Memory behind bridge: c7c00000-cbcfffff
        Prefetchable memory behind bridge: 00000000cff00000-00000000efefffff
        Capabilities: <access denied>

00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 01) (prog-if 00 [UHCI])
        Subsystem: Micro-Star International Co., Ltd. Unknown device 7267
        Flags: bus master, medium devsel, latency 0, IRQ 20
        I/O ports at ec00 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 01) (prog-if 00 [UHCI])
        Subsystem: Micro-Star International Co., Ltd. Unknown device 7267
        Flags: bus master, medium devsel, latency 0, IRQ 18
        I/O ports at e880 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 01) (prog-if 00 [UHCI])
        Subsystem: Micro-Star International Co., Ltd. Unknown device 7267
        Flags: bus master, medium devsel, latency 0, IRQ 17
        I/O ports at e800 [size=32]

00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 01) (prog-if 00 [UHCI])
        Subsystem: Micro-Star International Co., Ltd. Unknown device 7267
        Flags: bus master, medium devsel, latency 0, IRQ 16
        I/O ports at e480 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01) (prog-if 20 [EHCI])
        Subsystem: Micro-Star International Co., Ltd. Unknown device 7267
        Flags: bus master, medium devsel, latency 0, IRQ 20
        Memory at cfe3bc00 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1) (prog-if 01 [Subtractive decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=32
        I/O behind bridge: 0000c000-0000cfff
        Memory behind bridge: cbd00000-cfdfffff
        Prefetchable memory behind bridge: 0000000088000000-00000000880fffff
        Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
        Subsystem: Micro-Star International Co., Ltd. Unknown device 7267
        Flags: bus master, medium devsel, latency 0
        Capabilities: <access denied>

00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01) (prog-if 8a [Master SecP PriP])
        Subsystem: Micro-Star International Co., Ltd. Unknown device 7267
        Flags: bus master, medium devsel, latency 0, IRQ 17
        I/O ports at 01f0 [size=8]
        I/O ports at 03f4 [size=1]
        I/O ports at 0170 [size=8]
        I/O ports at 0374 [size=1]
        I/O ports at ffa0 [size=16]

00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) Serial ATA Storage Controller IDE (rev 01) (prog-if 8f [Master SecP SecO PriP PriO])
        Subsystem: Micro-Star International Co., Ltd. Unknown device 7267
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 18
        I/O ports at e400 [size=8]
        I/O ports at e080 [size=4]
        I/O ports at e000 [size=8]
        I/O ports at dc00 [size=4]
        I/O ports at d880 [size=16]
        Capabilities: <access denied>

00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
        Subsystem: Micro-Star International Co., Ltd. Unknown device 7267
        Flags: medium devsel, IRQ 5
        I/O ports at 0400 [size=32]

01:00.0 VGA compatible controller: nVidia Corporation Unknown device 016a (rev a1) (prog-if 00 [VGA])
        Subsystem: Unknown device 1642:3598
        Flags: bus master, fast devsel, latency 0, IRQ 10
        Memory at ca000000 (32-bit, non-prefetchable) [size=16M]
        Memory at d0000000 (64-bit, prefetchable) [size=256M]
        Memory at c9000000 (64-bit, non-prefetchable) [size=16M]
        Expansion ROM at cbce0000 [disabled] [size=128K]
        Capabilities: <access denied>

02:00.0 Multimedia video controller: Unknown device aa55:0025
        Flags: medium devsel, IRQ 16
        Memory at ce000000 (32-bit, non-prefetchable) [size=16M]

02:01.0 Multimedia video controller: Unknown device aa55:0025
        Flags: medium devsel, IRQ 21
        Memory at cd000000 (32-bit, non-prefetchable) [size=16M]

02:02.0 Ethernet controller: Atheros Communications, Inc. AR5005G 802.11abg NIC (rev 01)
        Subsystem: Atheros Communications, Inc. Unknown device 2052
        Flags: bus master, medium devsel, latency 64, IRQ 3
        Memory at cfdf0000 (32-bit, non-prefetchable) [size=64K]
        Capabilities: <access denied>

02:04.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8169SC Gigabit Ethernet (rev 10)
        Subsystem: Micro-Star International Co., Ltd. Unknown device 267c
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 19
        I/O ports at c800 [size=256]
        Memory at cfdefc00 (32-bit, non-prefetchable) [size=256]
        Expansion ROM at 88000000 [disabled] [size=128K]
        Capabilities: <access denied>

---

### Post by walt.smith1960 on 2011-01-26
Were it me, I'd download a live CD of 10.04 or 10.10 if possible. I think that your Atheros 5005G might work without further messing.  If not, no harm done.  Hardware support has improved in more recent versions.  If your wireless works from a live CD, it should work if installed permanently.

---

### Post by vase070 on 2011-01-27
i know it does work from a live cd but i need to get it to work for ubuntu 7.04 that is my job i've seen the same pc hardware on ubuntu 7.04 on another pc and aheros wireless works perfectly with no error so there must be a way to make it work on my ubuntu 7.04 pc i will give you a picture of the other pc than has  7.04 and the same atheros wireless card as my pc and you will see for your self

---

### Post by walt.smith1960 on 2011-01-27
hi Vase 70

If you have no choice but to use an obsolete and unsupported version of ubuntu, I assume you'd need to download the driver source code and compile it yourself.  I have no knowledge of that, others here do.

---

### Post by grahammechanical on 2011-01-27
The screen shot says that the Atheros driver is enabled but not working. Why would it say the driver is enabled if the driver was not installed?

If you have access to another PC with exactly the same hardware and the same version of Ubuntu can you not compare the setting configuration of the working machine with the non-working machine, You might notice something slightly different. Perhaps you have already done this. If so, then please forgive me for stating the obvious.

Regards.

P.S. I cannot see on the screen shot a network manager icon. Is network manager installed? I never used any kind of networking in 7.04 so I can tell you how to install it. I guess you have to load Synaptic Package Manager and search for Network Manager to see if it is installed. Perhaps you need to re-install it. I think that Network Manager was first used in Ubuntu with 7.04.

P.P.S. Sorry, my mistake. I have just had another look and it is there as an image of two monitors. Is that Network Manager? Or is it Network Monitor?

---

### Post by vase070 on 2011-01-27
it's the network manager when i click it it only shows  (wired) it doesnt show wireless damm

---

### Post by vase070 on 2011-02-01
as you can see here this is ubuntu 10.10 running from a live cd and i have wireless connections i did not install any driver or anything like that how can i have wireless from a live cd but not from installed ubuntu system explain that this is still on atheros hardware access layer (hal) wireless card

[IMG]http://www.postimg.com/28000/27765.jpg[/IMG]

---

### Post by vase070 on 2011-02-09
guys guys i found the problem the driver ath-pci atheros wireless lan drivers was blacklisted in etc/modprobe/blacklist.cfg i can see it at the buttom of the file 
how do i un blacklist the driver from blacklist.cfg i don't want to make any mistakes by messing around with any system files i just want everything back to normal any ideas :confused:

---

### Post by spiritfly on 2011-09-07
I'm in the same boat as vase. I HAVE to install the 7.04 ubunti to the same asus eeePC 900HA, but the wireless and ethernet do not work. The Atheros is showed in the Restricted Drivers Manager as enabled, but it still doesn't work, so I cannot get this netbook on the internet.

PLEASE HELP US WITH THIS UBUNTU GURUS!

---

### Post by MARP1961 on 2011-09-07
I'm not following all this. Why do you not just download an iso for 10.04 (or a later version of Ubuntu), burn a CD from it, backup all your data then do a fresh install?

7.04 is so old and out of date I had to look it up to remind myself it was codenamed Feisty Fawn! Support ended on 19th October, 2008! Updates are vital to the correct running of your operating system. If you install Lucid Lynx (10.04) you stand a very good chance that your wireless will work without any problems or at least easily fixable ones.

---

