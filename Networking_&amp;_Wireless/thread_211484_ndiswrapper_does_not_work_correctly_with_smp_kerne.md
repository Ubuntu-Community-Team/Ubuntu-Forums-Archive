---
title: "ndiswrapper does not work correctly with smp kernel"
date: 2006-07-08
forum: Networking &amp; Wireless
---

### Post by munsell on 2006-07-08
Hello,
I am having problems with the K7, 32-bit, SMP kernel (2.6.15-25) and ndiswrapper.  When I first boot up the machine ndiswrapper works correctly but after a few minutes (please note that the time varies) my wireless network connection stops working.  This problem only occurs when I use the K7 SMP kernel.  When I use the standard 386 Ubuntu kernel, I do not experience the problem.

Background Information:

I have the following wireless card:
```

0000:01:00.0 Network controller: Broadcom Corporation BCM4310 UART (rev 01)
        Subsystem: Hewlett-Packard Company: Unknown device 1360
        Flags: bus master, fast devsel, latency 0, IRQ 233
        Memory at c3000000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <available only to root>

```
Please note that I am using the driver that is referenced on the ndiswrapper Wiki.

ndiswrapper version:
```

utils version: 1.8
driver version:        1.19
vermagic:       2.6.15-25-k7 SMP preempt K7 gcc-4.0

```
Some information from /var/log/kern.log:
Loading information:
```

kernel: [17179591.492000] ndiswrapper version 1.19 loaded (preempt=yes,smp=yes)
kernel: [17179591.584000] ndiswrapper: driver bcmwl5 (Broadcom,11/02/2005, 4.10.40.0) loaded
kernel: [17179591.584000] **** SET: Misaligned resource pointer: f7754402 Type 07 Len 0
kernel: [17179591.584000] ACPI: PCI Interrupt Link [LK2E] enabled at IRQ 19
kernel: [17179591.584000] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [LK2E] -> GSI 19 (level, high) -> IRQ 233
kernel: [17179591.584000] PCI: Setting latency timer of device 0000:01:00.0 to 64
kernel: [17179591.592000] ndiswrapper: using irq 233
kernel: [17179592.272000] wlan0: vendor: ''
kernel: [17179592.272000] wlan0: ndiswrapper ethernet device 00:14:a5:a0:d5:62 using driver bcmwl5, 14E4:4312.5.conf
kernel: [17179592.272000] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK

```
Information after ndiswrapper stops working:
```

kernel: [17179786.488000] irq 233: nobody cared (try booting with the "irqpoll" option)
kernel: [17179786.488000]  [__report_bad_irq+42/144] __report_bad_irq+0x2a/0x90
kernel: [17179786.488000]  [handle_IRQ_event+61/112] handle_IRQ_event+0x3d/0x70
kernel: [17179786.488000]  [note_interrupt+135/224] note_interrupt+0x87/0xe0
kernel: [17179786.488000]  [__do_IRQ+252/272] __do_IRQ+0xfc/0x110
kernel: [17179786.488000]  [do_IRQ+25/48] do_IRQ+0x19/0x30
kernel: [17179786.488000]  [common_interrupt+26/32] common_interrupt+0x1a/0x20
kernel: [17179786.488000] handlers:
kernel: [17179786.488000] [pg0+944745616/1069179904] (ohci_irq_handler+0x0/0x8c0 [ohci1394])
kernel: [17179786.488000] [pg0+947342368/1069179904] (ndis_isr+0x0/0xd0 [ndiswrapper])
kernel: [17179786.488000] Disabling IRQ #233

```
I took a stab in the dark and removed the 1394 modules but still got the following:
```

kernel: [17179964.260000] irq 233: nobody cared (try booting with the "irqpoll" option)
kernel: [17179964.260000]  [__report_bad_irq+42/144] __report_bad_irq+0x2a/0x90
kernel: [17179964.260000]  [handle_IRQ_event+61/112] handle_IRQ_event+0x3d/0x70
kernel: [17179964.260000]  [note_interrupt+135/224] note_interrupt+0x87/0xe0
kernel: [17179964.260000]  [__do_IRQ+252/272] __do_IRQ+0xfc/0x110
kernel: [17179964.260000]  [do_IRQ+25/48] do_IRQ+0x19/0x30
kernel: [17179964.260000]  [common_interrupt+26/32] common_interrupt+0x1a/0x20
kernel: [17179964.260000]  [default_idle+0/96] default_idle+0x0/0x60
kernel: [17179964.260000]  [default_idle+44/96] default_idle+0x2c/0x60
kernel: [17179964.260000]  [cpu_idle+107/176] cpu_idle+0x6b/0xb0
kernel: [17179964.260000]  [start_kernel+410/512] start_kernel+0x19a/0x200
kernel: [17179964.260000]  [unknown_bootoption+0/480] unknown_bootoption+0x0/0x1e0
kernel: [17179964.260000] handlers:
kernel: [17179964.260000] [pg0+947350272/1069179904] (ndis_isr+0x0/0xd0 [ndiswrapper])
kernel: [17179964.260000] Disabling IRQ #233

```
I am not sure whether the problem is related to the Ubuntu kernel or ndiswrapper.  Any help you can provide would be much appreciated.

Thanks! =)

---

### Post by munsell on 2006-07-08
Please note that I did try combinations of the following kernel parameters: noapic,  pci=irqroute, pci=noacpi, acpi=noirq, acpi=off, irqpoll.  No matter what kernel parameter combinations I tried, the machine would boot up and wireless would work for a bit but eventually the machine would lock up.

---

### Post by beemer on 2006-07-21
I have the same issue.

I'm using a Linksys WUSB54G v1 wireless adapter.  If I use a 386 kernel, it all works fine.  If I try to use a 686 kernel, it locks the system after anywhere from 30 sec to several minutes of internet use.  

If I don't use the internet, system is fine.  Any ideas on this? Anyone?

Beemer

---

### Post by yarinb on 2006-12-01
same behavior here.
On my Dell Latitude D820, ndiswrapper will crash as soon as the wireless drivers comes up.
switching to uniprocessor 386 kernel seem to fix the issue.
since it's not a ndiswrapper problem, I guess it's Nvidia's fault or a kernel bug.
anyone with updates on this one?

Yarin

---

### Post by Skye on 2006-12-02
I have the same problem, on a Compaq v3000z laptop (Broadcom 4311 wifi, nvidia glx, and AMD Athlon 64 X2.)  There is apparently an IRQ conflict between the nvidia binary driver and ndiswrapper- and the Ubuntu team can't debug it because it's two proprietary drivers, (nvidia and the windows wireless driver) so there's no source available to modify.

Unfortunately, this makes Ubuntu unusable on my laptop, so I'm using windows on it until a fix emerges for this, or until the bcm43xx drivers work at something more than 14 kb/s.

---

### Post by kishd on 2006-12-02
I had a similar problem which was resolved downloading the latest ndiswrapper from [http://sourceforge.net/project/showfiles.php?group_id=93482](http://sourceforge.net/project/showfiles.php?group_id=93482)
compiling and installing it. Perhaps this could help. I run edgy.

---

### Post by stoopid1 on 2007-03-25
[SIZE="4"][COLOR="Red"]Edit: this does not solve the problem, it just allows you to browse the internet for more than 4 seconds (like maybe 20 mins)[/COLOR][/SIZE]

I had the same problem.  It began after i modified my xorg.conf file. I added the followng line Option "AddARGBGLXVisuals" under Section "Screen".  When i restarted i kept getting Disabling IRQ #233 after browsing the internet for no more than 5 seconds.  I updated ndiswrapper to 1.39 and the wifi drivers to sp34152.exe, but i still kept getting the problem.  So i commented out the line Option "AddARGBGLXVisuals" and the internet was working again

Edit your xorg.conf file:
```
sudo gedit /etc/X11/xorg.conf
```

find and delete or comment out:
```
Option "AddARGBGLXVisuals"
```
  
If this does not work, or if you don't have this option, try removing any other options you might have.
(Make sure you back up xorg.conf.  I leaned that the hard way.)

It seems to me that the rgb glx visuals conflict with the bcm4311 drivers.  I'm, a complete noob in linux so i wouldnt know much about thatt.

the reason why i added Option "AddARGBGLXVisuals" was because my window borders were not working while using beryl.  So, essentially, i had to sacrifice beryl.  Small price to pay, i suppose.

P.S i have a HP DV2020 laptop which uses nvidia go 6150 graphics and BCM4311 wireless. 

I used ndiswrapper 1.39 (tested with 1.34 as well) and sp34152.exe

PPS: I wrote this using my wireless, including the 10 times i edited it.

---

### Post by stoopid1 on 2007-03-26
I hate to double post, but the problem is fixed if you update the kernel to 2.6.20

Here is a links to instructions i have followed (they are essentially the same but i like the second one the most):
[http://ubuntuforums.org/showthread.php?p=2354449#post2354449](http://ubuntuforums.org/showthread.php?p=2354449#post2354449)
here are even better instruction on updating your kernel:
[http://ubuntuforums.org/showthread.php?t=56835&highlight=kernel+compilation](http://ubuntuforums.org/showthread.php?t=56835&highlight=kernel+compilation)

I unistalled ndiswrapper before following the instructions, (not sure if it is necessary).

---

