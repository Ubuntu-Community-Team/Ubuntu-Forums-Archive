---
title: "So slow booting"
date: 2011-02-07
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by jennybrew on 2011-02-07
I dont seem to be having as many problems as some posting here but wouldnt it be good if some attention was given to the boot process.
At this point I seem to be waiting a very long time for Ubuntu to boot and, even worst, I cant see if anything is happening. Just an otherwise blank purple screen. This has led me to believe on several occasions that everything had frozen. 
Perhaps its just my machines as no one else seems to have posted about it ... but if not just me ..does anyone know when this area of the system is due for some attention from the developers?

---

### Post by w3rt on 2011-02-07
I also got this, but installing nvidia drivers solved the problem

---

### Post by jennybrew on 2011-02-07
Thanks chaps but that wont work for me unfortunately as I am on ATI.

---

### Post by w3rt on 2011-02-07
Try installing the latest ATI drivers instead :)

---

### Post by dargaud on 2011-02-07
```
sudo aptitude install bootchart
```
Then reboot and look into /var/log/bootchart, there should be a graph of the boot sequence. See if anything is amiss (or post it here).

---

### Post by cariboo on 2011-02-07
@w3rt, how is installing the restricted drivers going to help aside from totally breaking the installation?

---

### Post by webme on 2011-02-07
> **jennybrew said:**
> Thanks chaps but that wont work for me unfortunately as I am on ATI.

Do you have keyboard led blinking (kernel panic) on boot? (this is also a common problem on Natty).
I think that we have to wait 2,3 weeks to see some stability (and boost in boot speed also).

---

### Post by xgt001 on 2011-02-08
i just switch off my pc and again switch on.... it boots properly then.... i am sure this is a bug...

---

### Post by jennybrew on 2011-02-08
Well, Ive attached the bootchart result and cant really see where the problem lies.
Sarcastic techie boyfriend here has a suggestion but its not something I would print :)
Any words of wisdom would be gratefully received.
Oh and yes, Cariboo907 , I totally agree.
Thanks in advance

---

### Post by jennybrew on 2011-02-08
So ..how do I get a good quality image to upload here  ... help!!

---

### Post by cariboo on 2011-02-08
Use [http://imgur.com/]("http://imgur.com/"), max size of attachments was set to 1024X768 some time ago, which is not very good for things like boot charts.

---

### Post by jennybrew on 2011-02-08
[[IMG]http://i.imgur.com/vjDVS.png[/IMG]]("http://imgur.com/vjDVS")


Wow!! Thanks Cariboo thats a link to remember.

---

### Post by dargaud on 2011-02-09
Does your system really only take 30s to boot ? If so I don't see why the complain.

---

### Post by jennybrew on 2011-02-09
> **dargaud said:**
> Does your system really only take 30s to boot ? If so I don't see why the complain.

Well, Im sure you mean well but you obviously havent read what I actually posted.
This is what I posted.

> 
At this point I seem to be waiting a very long time for Ubuntu to boot  and, even worst, I cant see if anything is happening. Just an otherwise  blank purple screen. This has led me to believe on several occasions  that everything had frozen. 
The problem is that I seem to be waiting a very long time for some evidence that anything is actually happening. All I get is a purple coloured blank screen with no indication of progress or anything else.

If this is the intended behaviour for a boot screen then fine. ;)
If its not the intended behaviour I am asking for words of wisdom . No complaints at all just a few simple questions.
Thanks again

---

### Post by Harry33 on 2011-02-09
> **jennybrew said:**
> Well, Im sure you mean well but you obviously havent read what I actually posted.
This is what I posted.

The problem is that I seem to be waiting a very long time for some evidence that anything is actually happening. All I get is a purple coloured blank screen with no indication of progress or anything else.

If this is the intended behaviour for a boot screen then fine. ;)
If its not the intended behaviour I am asking for words of wisdom . No complaints at all just a few simple questions.
Thanks again

Please tell us more about your system:
- what is your installation media (it is not very recent, you 2.6.37 kernel)?
- what graphics card do you have (model, like Radeon HD2600)?
- was this a clean install (Natty-alfa1) or an upgrade from Maverick (10.10)?

---

### Post by jennybrew on 2011-02-09
> **Harry33 said:**
> Please tell us more about your system:
- what is your installation media (it is not very recent, you 2.6.37 kernel)?
- what graphics card do you have (model, like Radeon HD2600)?
- was this a clean install (Natty-alfa1) or an upgrade from Maverick (10.10)?

Hi and thanks for the reply.
I think the snippet below states enough about this particular system and yes it was a clean install.
Probably worth mentioning that bot 10.04 and 10.10 show the boot screen without any problem on the same machine.

Thanks again:)

```
unity@Dell:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc Mobility Radeon HD 3400 Series
01:00.1 Audio device: ATI Technologies Inc RV620 Audio device [Radeon HD 34xx Series]
04:00.0 Network controller: Intel Corporation WiFi Link 5100
08:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5784M Gigabit Ethernet PCIe (rev 10)
09:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
09:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
09:01.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
09:01.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
unity@Dell:~$ 

```

---

### Post by Harry33 on 2011-02-09
> **jennybrew said:**
> Hi and thanks for the reply.
I think the snippet below states enough about this particular system and yes it was a clean install.
Probably worth mentioning that bot 10.04 and 10.10 show the boot screen without any problem on the same machine.

Thanks again:)
...


Well that list does not tell me what was your installation media (some Natty alfa1 snapshot).
It might be important, because ATI Radeon HD3400 should work out of the box.
Perhaps someone with that graphics card could post his/her experiences here.

---

### Post by ratcheer on 2011-02-09
> **jennybrew said:**
> 

The problem is that I seem to be waiting a very long time for some evidence that anything is actually happening. All I get is a purple coloured blank screen with no indication of progress or anything else.

If this is the intended behaviour for a boot screen then fine. ;)
If its not the intended behaviour I am asking for words of wisdom . No complaints at all just a few simple questions.
Thanks again

This happens to me fairly often when I boot Natty. I used to wait several minutes to see if it would continue and successfully complete starting up. It ***never*** did.

***Every time*** it has happened, if I press the hardware reset button and boot again, it has started successfully in a normal amount of time.

Tim

---

### Post by mc4man on 2011-02-09
You really should consider getting updated/upgraded, don't know when you stopped, the kernel showed is quite old. What you have now may not be too reflective of the current state of natty

If you wish maybe do a text boot, either remove the quiet splash from the /etc/default/grub GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" line, save and then run sudo update-grub 
or as a one time
from boot up > grub screen go e and remove 'quiet splash vt.handoff=7' from the boot line, then Crtl+x to boot
(if you're bypassing the grub screen then I think you need to hit the shift key right after the bios splash or something like that

---

### Post by cariboo on 2011-02-09
The boot chart says the system is up, but there may be a graphics problem, where the desktop isn't being displayed. On a couple of my systems, it takes more time to go from gdm to desktop, than it does to go from grub to gdm

---

### Post by afoglia on 2011-02-17
I'm having similar problems except (a) my screen is off, not purple, and (b) my boot takes one minute, which seems awfully long for a Core i5 that's not even 6 months old, especially compared to how quick maverick was.

From the below boot chart, I seem to spend over 10 seconds on some modprobes at the beginning of the boot.  Any ideas how to find out what modules are involved?  How else should I read the bootchart?

[[IMG]http://i.imgur.com/pPH8Sl.jpg[/IMG]](http://imgur.com/pPH8S)

---

### Post by Grendel336 on 2011-04-12
I just downloaded the iso for the beta release of 11.04 last week, and did a fresh install of it as a dual boot to Mint 9. 

After running update manager and restarting I am still having this same issue. 

I will get a specific time measurement on boot-up this afternoon. 

Once I select Ubuntu 11.04 the screen goes to the purplish color and just sits there for well over a minute with nothing audible or visual to tell me something is happening. 

I'm okay with this if this is just a Beta release thing, but I'd really like to know if it's normal or not. 

I'm using a 32-bit Toshiba laptop that's relatively old, but has never had any issues booting or running Mint 9. 

Once Ubuntu 11.04 loads it seems to run fine. I'm quite happy with it once things get started. It's just the booting process that baffles me.

---

### Post by rajeev1204 on 2011-04-12
Booting  is slow for me too , specially with the fglrx driver.OSS drivers usually boot real quick,now it seems unity takes a lifetime to load.

I am going to give bootchart thing a try.

---

### Post by lithopsian on 2011-04-12
> From the below boot chart, I seem to spend over 10 seconds on some  modprobes at the beginning of the boot.  Any ideas how to find out what  modules are involved?  How else should I read the bootchart?Absolutely, doesn't look right.  The rest of the boot doesn't look so bad for a fairly heavy desktop environment.

You can unpack your initrd file and see what is in there.  It is a gzipped cpio archive.  Just look in /boot for the right one.

That doesn't actually tell you what modules get loaded though, they will most likely just be the generic set of modules that everyone gets.  These are not logged either although you could add your own hook and output lsmod to somewhere.  I'm not entirely convinced that it is loading dozens of kernel modules because it doesn't seem to be doing much work.    What you could do as a first step is to watch the non-quiet output during boot and see where it is doing the waiting for that 10 seconds.

---

### Post by Grendel336 on 2011-04-12
Okay, started my computer up and from the time I selected Ubuntu 11.04 from my boot menu (my only other choice is Mint 9) until I got to the log in screen was a full 2 minutes and 57 seconds.

For the first 2 minutes and 30 seconds there was no noise or visible sign my computer was doing anything. 

At 2:30 the hard drive light came to life and then about 20 seconds later the screen blinked off the purple-ish background and went to the ubuntu screen before the log in screen. 

Waiting almost 3 minutes to just get a log in screen doesn't seem right. 

Is that what others are seeing?

---

### Post by VanR on 2011-04-12
My boot time seems to have sped up with the latest updates, but now I have been getting this strange blue screen pop up for a few seconds that I've never seen before with 11.04 or 10.10 even. I get this strange blue screen at every re-boot.

---

### Post by isdes on 2011-04-13
> **Grendel336 said:**
> 
Waiting almost 3 minutes to just get a log in screen doesn't seem right. 


I experience similar behavior. It was about 20-25 seconds on 10.10, and now it is over 2 minutes.

I see a strange gap in the dmesg output:
```

0.964857] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.965103] TCP: Hash tables configured (established 524288 bind 65536)
[    0.965105] TCP reno registered
[    0.965111] UDP hash table entries: 2048 (order: 4, 65536 bytes)
[    0.965135] UDP-Lite hash table entries: 2048 (order: 4, 65536 bytes)
[    0.965220] NET: Registered protocol family 1
[   84.175419] pci 0000:00:08.0: Enabling HT MSI Mapping
[   84.175515] pci 0000:00:09.0: Enabling HT MSI Mapping
[   84.175616] pci 0000:00:0a.0: Enabling HT MSI Mapping

```

I believe it is related to the long boot problem.

[Here is my bootchart](http://img855.imageshack.us/i/phenomnatty201104132.png/)

There is my full dmesg attached along with lspci and lsusb output.

Can anyone tell something more about this?

---

### Post by lithopsian on 2011-04-14
Shouldn't be waiting 85 seconds to start booting :)  Looks like you have some sort of hardware issue related to a graphics card (?) perhaps not being recognised properly (by your BIOS?).    Have you booted OK with earlier Ubuntu versions?

---

### Post by Grendel336 on 2011-04-14
I have not run Ubuntu on my particular laptop, but I have Mint 9 on it which runs, and starts fine. Mint 9 is a version of Linux based on Ubuntu isn't it?

---

### Post by rbrick49 on 2011-04-14
> **jennybrew said:**
> I dont seem to be having as many problems as some posting here but wouldnt it be good if some attention was given to the boot process.
At this point I seem to be waiting a very long time for Ubuntu to boot and, even worst, I cant see if anything is happening. Just an otherwise blank purple screen. This has led me to believe on several occasions that everything had frozen. 
Perhaps its just my machines as no one else seems to have posted about it ... but if not just me ..does anyone know when this area of the system is due for some attention from the developers?
I have a slow boot to from reboot to login 35 second after password anothe 15 seconds
sck from util-linux-ng 2.17.2
/dev/sdb1: clean, 222703/60530688 files, 6503721/242093312 blocks
 * Starting Mount network filesystems[74G[ OK ]
 * Starting System V initialisation compatibility[74G[ OK ]
 * Starting Bridge socket events into upstart[74G[ OK ]
 * Stopping Mount network filesystems[74G[ OK ]
 * Starting mDNS/DNS-SD daemon[74G[ OK ]
 * Starting configure network device[74G[ OK ]
 * Starting network connection manager[74G[ OK ]
 * Stopping cold plug devices[74G[ OK ]
 * Stopping log initial device creation[74G[ OK ]
 * Starting load fallback graphics devices[74G[ OK ]
 * Starting enable remaining boot-time encrypted block devices[74G[ OK ]
 * Starting configure network device security[74G[ OK ]
 * Starting save udev log and update rules[74G[ OK ]
 * Stopping save udev log and update rules[74G[ OK ]
 * Stopping load fallback graphics devices[74G[ OK ]
 * Starting Ubuntu live CD installer[74G[ OK ]
 * Stopping Ubuntu live CD installer[74G[ OK ]
 * Starting GNOME Display Manager[74G[ OK ]
 * Stopping enable remaining boot-time encrypted block devices[74G[ OK ]
Skipping profile in /etc/apparmor.d/disable: usr.bin.firefox
 * Starting AppArmor profiles       [175G 
[169G[ OK ]
 * Starting CUPS printing spooler/server[74G[ OK ]

---

### Post by rbrick49 on 2011-04-14
my bootchart
/home/ron/Downloads/J5mY3 - Imgur.png

---

### Post by cariboo on 2011-04-14
@rbrick49, your bootchart is unreadable, use a service like [http://imgur.com/]("http://imgur.com/"), to upload your image. 

The forum limits image size to 1024X768.

---

### Post by rbrick49 on 2011-04-14
[[IMG]http://i.imgur.com/oKqawl.jpg[/IMG]](http://imgur.com/oKqaw)
ctrl+

---

### Post by rbrick49 on 2011-04-14
@ron:~$ lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:02.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (ext gfx port 0)
00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2)
00:11.0 SATA controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 SATA Controller [IDE mode]
00:12.0 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB7x0 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB7x0 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
00:14.1 IDE interface: ATI Technologies Inc SB7x0/SB8x0/SB9x0 IDE Controller
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB7x0/SB8x0/SB9x0 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:14.5 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI2 Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: ATI Technologies Inc Cayman PRO [AMD Radeon 6900 Series]
01:00.1 Audio device: ATI Technologies Inc Device aa80
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)

---

### Post by Aenima99x on 2011-04-14
> **rbrick49 said:**
> [[IMG]http://i.imgur.com/oKqawl.jpg[/IMG]](http://imgur.com/oKqaw)
ctrl+

:confused: 22 second boot is too long?

---

### Post by rbrick49 on 2011-04-14
I just did a reboot with auto login it took 40 secomd this time must be an amd problem

---

### Post by lithopsian on 2011-04-15
> :confused: 22 second boot is too long?
Yes, that boot is basically normal.  Each release of Ubuntu has more and more stuff in it and there are no major boot improvements since about Lucid.  You should remove any services that you don't need, reprofile ureadahead, and that should gain you a a few seconds.

Otherwise, your bootchart should be held up as an example of what a healthy boot looks like:KS

I do notice that your hostname and hwclock are being started concurrently with ureadahead and so are both slow themselves and possibly slowing ureadahead slightly.  The effect is probably tiny but you might try changing them to run after ureadahead.

---

### Post by Grendel336 on 2011-04-15
Anything less than 60 seconds would be refreshing. 

Less than 30 seconds would be worthy of a happy dance. 

I am consistently seeing 2:55 to 3:00 when I use a stopwatch. 

That's 2 minutes 55 seconds to 3 full minutes. 

Once the process finishes, everything runs quite well so I can't complain too loudly.

---

### Post by rbrick49 on 2011-04-15
> **Grendel336 said:**
> Anything less than 60 seconds would be refreshing. 

Less than 30 seconds would be worthy of a happy dance. 

I am consistently seeing 2:55 to 3:00 when I use a stopwatch. 

That's 2 minutes 55 seconds to 3 full minutes. 

Once the process finishes, everything runs quite well so I can't complain too loudly.
well I guess jennybrew and myself had better stop sooking thanks folks

---

### Post by h.aling on 2011-04-15
Same here. I upgraded to the 11.04 beta a couple of days ago and booting now takes up to 3 minutes with a purple screen.

My Phenom II hexacore with 4GiB RAM and a Vertex 2 SDD used to boot 10.10 a little faster ;)

I use a recent NVidia videcard with the binary driver.

---

### Post by fjgaude on 2011-04-15
> **rbrick49 said:**
> well I guess jennybrew and myself had better stop sooking thanks folks

In your BIOS you might make sure your CDROM is checked after your hard drive for the OS. 

I remember it took about 15 sec to check a CD that didn't have a bootable OS on it to have then the HD checked.

---

### Post by cariboo on 2011-04-15
With so many packages being updated, ureadahead probably needs updating everytime you reboot. My usual boot time look to be between 20 -30 seconds, I usually go grab a cup of coffee when I boot, and it's always done before I get back, I guess I'll have to install bootchart to get a more accurate  reading. Just as an aside, sleep works well on my netbook, I just close the lid, and it takes a couple of seconds to restart when I open it.

---

### Post by nashpd on 2011-04-15
I upgraded from 10.10 to 11.04 yesterday...i use an Acer Aspire 5742  (core i3-380M) @2.53GHz...i believe my boot time has tripled...any idea  what could be the reason?

---

### Post by Duncan Williams on 2011-04-15
I had problems with boots as per:

No proprietory drivers after last install of natty.
I was advised in additional drivers of:
experimental 3D support for NVIDIA cards.
This driver provides a highly experimental 3D acceleration for NVIDIA graphics cards, as a free alternative to the proprietary driver.
You need to restart your desktop session after installation.

Thats when my pc would boot to a blank screen in ubuntu mode.
(I used failsafe graphics mode to get into gnome)

After installing updates yesterday.
There were amongst the updates NVIDIA related and nouvea and experimental.

After a few reboots:
I am now booting straight into unity mode ubuntu with full support for my fx5200 card. and no noticeable problems.

Boot time is about 1 min.

---

### Post by Duncan Williams on 2011-04-15
I had problems with boots as per:
(14/4/2011)
No proprietory drivers after last install of natty.
I was advised in additional drivers of:
experimental 3D support for NVIDIA cards.
This driver provides a highly experimental 3D acceleration for NVIDIA graphics cards, as a free alternative to the proprietary driver.
You need to restart your desktop session after installation.

Thats when my pc would boot to a blank screen in ubuntu mode.
(I used failsafe graphics mode to get into gnome)

After installing updates yesterday.
There were amongst the updates NVIDIA related and nouvea and experimental.

After a few reboots:
I am now booting straight into unity mode ubuntu with full support for my fx5200 card. and no noticeable problems.

Boot time is about 1 min.

---

### Post by lucazade on 2011-04-15
My system boot up in 37 sec in a virtual machine,
so I expect it to be faster in a physical machine.

---

### Post by ndstate on 2011-04-17
> **Harry33 said:**
> Well that list does not tell me what was your installation media (some Natty alfa1 snapshot).
It might be important, because ATI Radeon HD3400 should work out of the box.
Perhaps someone with that graphics card could post his/her experiences here.

Mobility Radeon HD 3400 Series does not work with my laptop and Natty, I just get a black screen after a brief purple screen.

Any ideas?

---

