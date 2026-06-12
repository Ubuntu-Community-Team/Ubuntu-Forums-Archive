---
title: "Ethernet device not working right"
date: 2010-02-23
forum: Networking &amp; Wireless
---

### Post by octopus22 on 2010-02-23
Have some strange issues on my Acer Aspire 5100 laptop running Ubuntu 9.10 i386.

No wifi device installed in computer now (it was).

Network manager says: "No network devices available"

I want to have shared internet connection from Vista computer, but ethernet not works.


> ~$ sudo lshw -C network
  *-network UNCLAIMED     
       description: Ethernet controller
       product: Zonet Zen3200
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 1
       bus info: pci@0000:06:01.0
       version: 10
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=64 maxlatency=64 mingnt=32
       resources: ioport:a000(size=256) memory:48001000-480010ff

~$ sudo ethtool eth0
Settings for eth0:
Cannot get device settings: No such device
Cannot get wake-on-lan settings: No such device
Cannot get message level: No such device
Cannot get link status: No such device
No data available

~$ lspci
00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:04.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:05.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:12.0 IDE interface: ATI Technologies Inc IXP SB400 Serial ATA Controller (rev 80)
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 83)
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller (rev 80)
00:14.2 Audio device: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller (rev 01)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS482 [Radeon Xpress 200M]
06:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. Zonet Zen3200 (rev 10)



---

### Post by chili555 on 2010-02-23
I think this is supposed to work with a module *8139too*. These cards often also load an unnecessary module 8139cp. Let's find out. Please open a terminal and do:```
dmesg | grep 8139
```Post the result and we'll have a better idea of how to proceed.

---

### Post by octopus22 on 2010-02-23
thank you for rapid answer!


nothing happened, just fresh terminal line appeared. seems as command has no output.

---

### Post by chili555 on 2010-02-23
That simply means there is nothing in the dmesg log at all with '8139' in the listing. Let's see if we can trigger it. Please do:```
sudo modprobe 8139too
ifconfig
```Do you now have an eth0 interface? Let's also see the PCI ID for the card and try to verify that it's an 8139xx card:```
lspci -nn | grep Ethernet
```Is this machine, by any chance, dual-booting with Windows?

---

### Post by octopus22 on 2010-02-23
> ~$ sudo modprobe 8139too
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.

~$ ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

~$ lspci -nn | grep Ethernet
06:01.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. Zonet Zen3200 [10ec:0139] (rev 10)


looks like eth0 is exist, but don't sure mod probe doing all right

---

### Post by chili555 on 2010-02-23
We have a real problem here. Neither the 8139too or 8139cp modules support 10ec:0139. Both support 10ec:[COLOR="Red"]8[/COLOR]139, as you might expect. 

I found this: [http://www.linuxquestions.org/hcl/showproduct.php/product/1519/cat/158](http://www.linuxquestions.org/hcl/showproduct.php/product/1519/cat/158)

It seems to agree that the 8139cp driver is correct. However, it isn't, obviously.

I have grepped /lib/modules/`uname -r`/modules.pcimap and find no match for 10ec ***AND*** 0139. The pci.id *is* shown in /usr/share/hwdata/pci.ids

I have added some of these details so that searchers or others may learn from our research.

I am continuing to google.

Do you, by chance, have another ethernet card laying around?

---

### Post by octopus22 on 2010-02-23
Thank you for help!

This laptop is not dual-boot. Pure linux.
I have no eth card around, thinking about buying a usb wifi to be online.

Btw, pci bus controller send some strange info on computer startup, friend of my tell it can be broken on motherboard. But computer works good, only can't get Eth to work.

---

### Post by chili555 on 2010-02-23
> pci bus controller send some strange info on computer startupLet's see if the kernel has any errors or warnings:```
dmesg | grep 06:01
```

---

### Post by octopus22 on 2010-02-23
> dmesg | grep 06:01
[    0.211520] pci 0000:06:01.0: reg 10 io port: [0xa000-0xa0ff]
[    0.211531] pci 0000:06:01.0: reg 14 32bit mmio: [0x000000-0x0000ff]
[    0.211600] pci 0000:06:01.0: supports D1 D2
[    0.211602] pci 0000:06:01.0: PME# supported from D1 D2 D3hot
[    0.211608] pci 0000:06:01.0: PME# disabled
[    0.295011] pci 0000:06:01.0: BAR 1: error updating (0x48001000 != 0x40001000)


some errors exist!

---

### Post by chili555 on 2010-02-23
Please reboot your computer. Whe the computer is first starting, you will see a reference to GRUB. You will have three seconds to press Esc and then you will see a menu like the attached. Highlight the top line and press e (for edit). Scroll down to the long line that contains 'quiet splash' and press e. Edit that line to add [COLOR="Red"]nolapic[/COLOR]. Press Enter to accept the edit and b (for boot).

After the machine boots fully, run:```
dmesg | grep 06:01
ifconfig
```Any improvement?

---

### Post by octopus22 on 2010-02-23
Can't get to this screen, i have mono-boot system, so on ESC GRUB just skips graphic loading and shows command lines.

---

### Post by chili555 on 2010-02-24
> i have mono-boot systemThat has nothing to do with it; all my Ubuntu-only systems have this editable menu available. Nonetheless, let's try this the other way:```
sudo gedit /etc/default/grub
```Use nano, kate or vim if you don't have gedit. Find this line:> GRUB_CMDLINE_LINUX=""
Change it to this:> GRUB_CMDLINE_LINUX="nolapic"Proofread carefully, save and close gedit. Next, do:```
sudo grub-mkconfig -o /boot/grub/grub.cfg
```Now reboot and see if the troubling messages are present in *dmesg* as posted above. Also run:```
ifconfig
```Did an ethernet interface appear, eth0, perhaps?

---

### Post by octopus22 on 2010-02-24
Nothing happens...


I bought D-link DWA-110 and it works from the box, not need any driver. So, i'm online and happy.

Thanks for help!

---

### Post by schreck494 on 2010-02-24
I am actually having a similar problem right now getting Ubuntu to recognize my second ethernet adapter on an 8.04 64 bit machine.  The card is an Intel 82574L Gigabit card.  
When I search lspci, I get this:
```

01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 02)
02:00.0 Ethernet controller [0200]: Intel Corporation 82574L Gigabit Network Connection [8086:10d3]

```
The Realtek card is eth0, and is working properly.  The Intel card doesn't seem to have been assigned an eth# designation, and I haven't found a way to activate it yet.
When I use
```

/sbin/ip link

```
it only shows eth0 and the loopback interface.

---

### Post by chili555 on 2010-02-24
> [COLOR="Red"]02:00.0[/COLOR] Ethernet controller [0200]: Intel Corporation 82574L Gigabit Network Connection [8086:10d3]Let's see what's happening under the hood. Please post:```
dmesg | grep 02:00
```Thanks.

---

### Post by schreck494 on 2010-02-25
There is no output at all.

---

### Post by chili555 on 2010-02-25
That's pretty weird! Let's just look at the whole dmesg. Please do:```
dmesg > dmesg.txt
zip dmesg.zip dmesg.txt
```You will find a file in your user directory named dmesg.zip. Please attach it to your reply for our study.

---

### Post by schreck494 on 2010-02-25
Here is the dmesg

---

### Post by chili555 on 2010-02-25
In your dmesg, I see this:> [   27.759405] Error attaching device data
[   27.759467] Error attaching device data
[   27.759526] Error attaching device data
[   27.759588] Error attaching device data
--- snip ---
[   27.771580] ACPI Warning (tbutils-0217): Incorrect checksum in table [OEMB] -  99, should be 8C [20070126]I also saw this: [http://ubuntuforums.org/showthread.php?t=858244&page=2](http://ubuntuforums.org/showthread.php?t=858244&page=2)> I updated the BIOS from version 1.1 to 1.3 and had the AHCI option afterwards. Switched "Raid Mode" setting from IDE to AHCI and everything is instantly recognized!
I am not sure you have a RAID setup, but you might check your BIOS to see if changing ACHI to IDE options fixes your issue.

In your dmesg, your Intel card is not recognized at all. The bus number 02:00etc. is not mentioned. I am frankly surprised it shows up in lspci.

---

### Post by schreck494 on 2010-02-26
There is no RAID, or any hard drives at all, as this machine does a PXE boot.

---

### Post by Eathray on 2010-03-22
Thanks for this thread. I was having an ethernet card problem.

In reading through, something told me to check my bio settings. There is a setting for the cpi slots to be enabled as 'master bus' boot devices. I enabled that option, booted, and immediately my connection was established as soon as I booted.

I know this may not be the answer for everyone, but check your bios, just in case.

thanks for posting this thread. [solved]

Eathray

---

