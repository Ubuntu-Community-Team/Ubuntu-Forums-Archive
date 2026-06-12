---
title: "Ubuntu 11.04 Won't Connect to Internet through Ethernet"
date: 2011-07-11
forum: Networking &amp; Wireless
---

### Post by JackYuseiConan on 2011-07-11
I'm really new to Ubuntu and stuff. I just installed it on to my Dell Dimension 3100 alongside Windows XP. The Windows XP part of the computer can connect to the internet using the Ethernet cable normally so that's fine. But when I use the Ubuntu bit, it tries to connect to "Auto eth0", fails then just disconnects. I've clicked on "Edit Connections" and under Wired, when I click "Edit" for Auto eth0, the "Device MAC Address" is the exact same as the one get when I type in "ifconfig" or "ifconfig -a" in terminal. As I understand Linux's version of MAC Address is HWaddr right? (Just making sure I'm looking at the right thing). If yes, then I'm sure the correct MAC address is the box... However if no, then please tell me what I *should* be looking at. :\ Also, the Cloned MAC Address is empty, not *too* sure what a Cloned MAC Address is but I've just left it empty. MTU is on automatic. I haven't touched any other settings (802.1x Security/IPv4/IPv6), I assume I don't need to touch those? And before anyone asks, the Dell Dimension 3100 can't connect wirelessly unless you buy a PCI card or something... I think. So nothing is under Wireless. And ditto for Mobile Broadband, VPN and DSL.

Please help.

Thanks JYC

---

### Post by JackYuseiConan on 2011-07-11
Oh and I've also installed Ubuntu 11.04 on a laptop and it can connect wirelessly to the internet fine. So it's definitely not Ubuntu and probably just me being me. :P I'm not the sharpest tool in the box when it comes to this sort of stuff unfortunately. :\

---

### Post by JackYuseiConan on 2011-07-11
And *another* thing... Sorry to be such a pain.

I read another post and a guy suggested to type "sudo mii-tool eth0" and it came up with "eth0: negotiated 100baseTx-FD flow-control, link ok"

Thanks JYC

---

### Post by chili555 on 2011-07-11
Let's have a look at what you have. Please open a terminal and run and post:```
lspci -nn | grep -e 0200 -e 0280
sudo lshw -C network
```The latter command will take a few moments; please be patient.

You can copy and paste from the terminal to a text editor and transfer it with a USB key or similar to post it here.

---

### Post by JackYuseiConan on 2011-07-12
For > lspci -nn | grep -e 0200 -e 0280 it says:

> 03:08.0 Ethernet controller [0200]: Intel Corporation 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller [8086:1064] (rev 04)

And for > sudo lshw -C network it says:

> *-network               
       description: Ethernet interface
       product: 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:03:08.0
       logical name: eth0
       version: 04
       serial: 00:13:20:e1:52:ab
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=full firmware=N/A latency=64 link=yes maxlatency=56 mingnt=8 multicast=yes port=MII speed=100Mbit/s
       resources: irq:20 memory:dfcff000-dfcfffff ioport:d8c0(size=64)

---

### Post by chili555 on 2011-07-12
So far, so good. You have a driver and an interface, e100 and eth0 respectively. You should not have to fill in anything at all in Network Manager > Edit Connections. The system should figure out all the details for you. If you have added some settings, remove them and press Save.

Let's see what the system logs have to say. Plug in the ethernet cable, click the Network Manager icon and click on Auto eth0. Please see attached. Does it try to connect and fail? Let's see what is happening. Please run and post:```
sudo cat /var/log/syslog | grep -e etwork -e e100 | tail -n20
```Thanks.

---

### Post by JackYuseiConan on 2011-07-12
I haven't edited anything.

And when I click on Auto Eth0, it tries to connect for about 30 seconds aprox. and then comes up with the message:
"Wired network

Disconnected - you are now offline"

Here's the log:

> Jul 12 15:44:18 JYC-PC NetworkManager[452]: <info> (eth0): device state change: 4 -> 5 (reason 0)
Jul 12 15:44:18 JYC-PC NetworkManager[452]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) successful.
Jul 12 15:44:18 JYC-PC NetworkManager[452]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled.
Jul 12 15:44:18 JYC-PC NetworkManager[452]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) complete.
Jul 12 15:44:18 JYC-PC NetworkManager[452]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) started...
Jul 12 15:44:18 JYC-PC NetworkManager[452]: <info> (eth0): device state change: 5 -> 7 (reason 0)
Jul 12 15:44:18 JYC-PC NetworkManager[452]: <info> Activation (eth0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Jul 12 15:44:18 JYC-PC NetworkManager[452]: <info> dhclient started with pid 1734
Jul 12 15:44:18 JYC-PC NetworkManager[452]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) complete.
Jul 12 15:44:18 JYC-PC NetworkManager[452]: <info> (eth0): DHCPv4 state changed nbi -> preinit
Jul 12 15:45:03 JYC-PC NetworkManager[452]: <warn> (eth0): DHCPv4 request timed out.
Jul 12 15:45:04 JYC-PC NetworkManager[452]: <info> (eth0): canceled DHCP transaction, DHCP client pid 1734
Jul 12 15:45:04 JYC-PC NetworkManager[452]: <info> Activation (eth0) Stage 4 of 5 (IP4 Configure Timeout) scheduled...
Jul 12 15:45:04 JYC-PC NetworkManager[452]: <info> Activation (eth0) Stage 4 of 5 (IP4 Configure Timeout) started...
Jul 12 15:45:04 JYC-PC NetworkManager[452]: <info> (eth0): device state change: 7 -> 9 (reason 5)
Jul 12 15:45:04 JYC-PC NetworkManager[452]: <info> Marking connection 'Auto eth0' invalid.
Jul 12 15:45:04 JYC-PC NetworkManager[452]: <warn> Activation (eth0) failed.
Jul 12 15:45:04 JYC-PC NetworkManager[452]: <info> Activation (eth0) Stage 4 of 5 (IP4 Configure Timeout) complete.
Jul 12 15:45:04 JYC-PC NetworkManager[452]: <info> (eth0): device state change: 9 -> 3 (reason 0)
Jul 12 15:45:04 JYC-PC NetworkManager[452]: <info> (eth0): deactivating device (reason: 0).

---

### Post by JackYuseiConan on 2011-07-12
Oh and btw, I tried running Ubuntu on the USB stick I used to instal it and it still doesn't connect, never did. It didn't the first time and it doesn't now.

---

### Post by chili555 on 2011-07-12
I wonder if there any kernel messages about the driver:```
dmesg | grep e100
```Thanks.

---

### Post by JackYuseiConan on 2011-07-12
> [    0.803161] pci 0000:03:08.0: Firmware left e100 interrupts enabled; disabling
[    1.991421] e100: Intel(R) PRO/100 Network Driver, 3.5.24-k2-NAPI
[    1.991428] e100: Copyright(c) 1999-2006 Intel Corporation
[    1.991497] e100 0000:03:08.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    2.028044] e100 0000:03:08.0: PME# disabled
[    2.029344] e100 0000:03:08.0: eth0: addr 0xdfcff000, irq 20, MAC addr 00:13:20:e1:52:ab
[   13.380161] e100 0000:03:08.0: eth0: NIC Link is Up 100 Mbps Full Duplex

With every "e100" in red. Not sure if that means anything but just thought I should mention it.

---

### Post by chili555 on 2011-07-12
I am troubled by this:> *-network
description: Ethernet interface
product: 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller
vendor: Intel Corporation
physical id: 8
bus info: pci@0000:03:08.0
logical name: eth0
version: 04
serial: 00:13:20:e1:52:ab
size: 100Mbit/s
capacity: 100Mbit/s
width: 32 bits
clock: 33MHz
capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=full [COLOR="Red"]firmware=N/A[/COLOR] latency=64 link=yes maxlatency=56 mingnt=8 multicast=yes port=MII speed=100Mbit/s
resources: irq:20 memory:dfcff000-dfcfffff ioport:d8c0(size=64) However, the driver requires firmware:```
$ modinfo e100
filename:       /lib/modules/2.6.38-8-generic/kernel/drivers/net/e100.ko
[COLOR="Red"]firmware:       e100/d102e_ucode.bin
firmware:       e100/d101s_ucode.bin
firmware:       e100/d101m_ucode.bin[/COLOR]
version:        3.5.24-k2-NAPI
license:        GPL
<snip>

```Can you please confirm that you have the firmware?```
ls /lib/firmware/e100
```

---

### Post by JackYuseiConan on 2011-07-12
> d101m_ucode.bin  d101s_ucode.bin  d102e_ucode.bin

... Is this good or bad?

---

### Post by JackYuseiConan on 2011-07-12
And for the modinfo e100 thing:

> filename:       /lib/modules/2.6.38-8-generic/kernel/drivers/net/e100.ko
firmware:       e100/d102e_ucode.bin
firmware:       e100/d101s_ucode.bin
firmware:       e100/d101m_ucode.bin
version:        3.5.24-k2-NAPI
license:        GPL
author:         Copyright(c) 1999-2006 Intel Corporation
description:    Intel(R) PRO/100 Network Driver
srcversion:     CA8851CBD54453A98F5FAB4
alias:          pci:v00008086d000027DCsv*sd*bc02sc00i*
alias:          pci:v00008086d0000245Dsv*sd*bc02sc00i*
alias:          pci:v00008086d00002459sv*sd*bc02sc00i*
alias:          pci:v00008086d00002449sv*sd*bc02sc00i*
alias:          pci:v00008086d00001229sv*sd*bc02sc00i*
alias:          pci:v00008086d00001209sv*sd*bc02sc00i*
alias:          pci:v00008086d000010FEsv*sd*bc02sc00i*
alias:          pci:v00008086d00001095sv*sd*bc02sc00i*
alias:          pci:v00008086d00001094sv*sd*bc02sc00i*
alias:          pci:v00008086d00001093sv*sd*bc02sc00i*
alias:          pci:v00008086d00001092sv*sd*bc02sc00i*
alias:          pci:v00008086d00001091sv*sd*bc02sc00i*
alias:          pci:v00008086d0000106Bsv*sd*bc02sc00i*
alias:          pci:v00008086d0000106Asv*sd*bc02sc00i*
alias:          pci:v00008086d00001069sv*sd*bc02sc00i*
alias:          pci:v00008086d00001068sv*sd*bc02sc00i*
alias:          pci:v00008086d00001067sv*sd*bc02sc00i*
alias:          pci:v00008086d00001066sv*sd*bc02sc00i*
alias:          pci:v00008086d00001065sv*sd*bc02sc00i*
alias:          pci:v00008086d00001064sv*sd*bc02sc00i*
alias:          pci:v00008086d00001059sv*sd*bc02sc00i*
alias:          pci:v00008086d00001057sv*sd*bc02sc00i*
alias:          pci:v00008086d00001056sv*sd*bc02sc00i*
alias:          pci:v00008086d00001055sv*sd*bc02sc00i*
alias:          pci:v00008086d00001054sv*sd*bc02sc00i*
alias:          pci:v00008086d00001053sv*sd*bc02sc00i*
alias:          pci:v00008086d00001052sv*sd*bc02sc00i*
alias:          pci:v00008086d00001051sv*sd*bc02sc00i*
alias:          pci:v00008086d00001050sv*sd*bc02sc00i*
alias:          pci:v00008086d0000103Esv*sd*bc02sc00i*
alias:          pci:v00008086d0000103Dsv*sd*bc02sc00i*
alias:          pci:v00008086d0000103Csv*sd*bc02sc00i*
alias:          pci:v00008086d0000103Bsv*sd*bc02sc00i*
alias:          pci:v00008086d0000103Asv*sd*bc02sc00i*
alias:          pci:v00008086d00001039sv*sd*bc02sc00i*
alias:          pci:v00008086d00001038sv*sd*bc02sc00i*
alias:          pci:v00008086d00001034sv*sd*bc02sc00i*
alias:          pci:v00008086d00001033sv*sd*bc02sc00i*
alias:          pci:v00008086d00001032sv*sd*bc02sc00i*
alias:          pci:v00008086d00001031sv*sd*bc02sc00i*
alias:          pci:v00008086d00001030sv*sd*bc02sc00i*
alias:          pci:v00008086d00001029sv*sd*bc02sc00i*
depends:        
vermagic:       2.6.38-8-generic SMP mod_unload modversions 686 
parm:           debug:Debug level (0=none,...,16=all) (int)
parm:           eeprom_bad_csum_allow:Allow bad eeprom checksums (int)
parm:           use_io:Force use of i/o access mode (int)

---

### Post by JackYuseiConan on 2011-07-12
Should I just reinstall Ubuntu and then see what's what?

---

### Post by chili555 on 2011-07-12
> **JackYuseiConan said:**
> Should I just reinstall Ubuntu and then see what's what?I almost never suggest the nuclear option. Of course, if you have the install CD around for 10.10 or 10.04 and it works as expected, by all means, go for it. 

Your firmware files are in place. Where firmware is needed and present, I usually see some variation of:> configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.3.10a-NAPI [COLOR="Red"]firmware=0.5-1[/COLOR] latency=0 link=no multicast=yes port=twisted pairI guess yours is an exception.

You might look in the BIOS; are IRQs set to Auto Detect? Is Wake-on-LAN on or off? Whichever it is, reverse it. You might also try:```
sudo rmmod -f e100
sudo modprobe e100 use_io=1
```Any improvement?

---

### Post by JackYuseiConan on 2011-07-12
Well, by looking in the BIOS, I just assumed you meant the setup page thing that appears when you press F2 on the boot screen or something and I couldn't find anything related to IRQ's or Wake-on-LAN. Sorry, I'm pretty stupid and don't know what those are or where to find them...

Now for the commands in Terminal,

sudo rmmod -f e100 just disables the networking bit.

sudo modprobe e100 use_io=1 re-enables it, but my computer makes no attempt to connect to Auto Eth0... it may have given up. So I clicked on Auto eth0 and it tried again but failed again...

Also, I only have Ubuntu 11.04 ... I'm new to Ubuntu and Linux so I wouldn't have any discs. I just have a USB stick I used.

---

### Post by chili555 on 2011-07-12
> I just assumed you meant the setup page thing that appears when you press F2 on the boot screenExactly correct. If you look around in there, you'll find a menu that allows you to scroll down and see and change various settings. Here is and example of the IRQ page.

You might try downloading an earlier version of Ubuntu and trying it. By the way, if you are capable of running Ubuntu on a USB stick and asking about it on this forum, I don't believe you're stupid at all. You may be inexperienced but even I was inexperienced at one time. Nobody knows everything on their first week or so.

---

### Post by JackYuseiConan on 2011-07-12
Um... Yeah just to be really sure we're on the same page (literally) when I press F2, there is a setup page with a list on the left (including System, Drives, Onboard Drives, Video, Performance, Security, Power Mgmt, Maintenance and POST Behaviour). I've thoroughly looked, and I cannot find a PCI page not anything about IRQ... :\

Aha thanks, yeah inexperienced sounds good. ^.^ I'll go with that. Better than stupid any day. :D

---

### Post by chili555 on 2011-07-12
And if you use th arrow keys to scroll down to System, what are the options?

---

### Post by JackYuseiConan on 2011-07-12
System Info
Processor Info
Memory Info
Date/Time
Boot Sequence

---

### Post by chili555 on 2011-07-12
Hmmm. What's within Performance?

---

### Post by JackYuseiConan on 2011-07-12
Hyper-Threading "This field specifies whether each physical processor will appear as one or two logical processors. The performance of some applications will improve with additional logical processors."

HDD Acoustic Mode... Basically controlling the noise level of the computer or something.

---

### Post by JackYuseiConan on 2011-07-12
I noticed your screenshot had "PCI" written all over it. Am I right in thinking that this "PCI" is the same the the "PCI" in PCI cards and PCI express cards? If yes, then would it not be in Onboard Devices or Video? And if yes or either one;

Onboard Devices: Integrated NIC, Integrated Audio, USB Controller and Card Reader. (NIC being Network Interface Controller).

Video: Primary Video, Video Memory Size.

This is just a hunch, but if under Onboard Devices, I'm thinking towards Integrated NIC as that actually has something to do with newtorks etc.?

---

### Post by chili555 on 2011-07-12
> I'm thinking towards Integrated NIC as that actually has something to do with newtorks etc.?Yes, exactly! What settings are in place and what are available?> Am I right in thinking that this "PCI" is the same the the "PCI" in PCI cards and PCI express cards?Yes, exactly.

---

### Post by JackYuseiConan on 2011-07-12
Setting Available: Off On On w/PXE

On w/PXE is for booting an OS from a server, so I'm assuming that's out of the question.

On just means NIC is enabled which was what the default is and what it was on.

Off is well, off. :P

I tried off, dead end.
On w/PXE is also dead end and as you already know, the default wasn't working anyway.

---

### Post by wvcoalminer on 2011-07-12
Hello, I had the same problem. Use your networking tools and edit,... un-check the /IPv4/IPv6 settings. Save and see if that helps.

---

### Post by JackYuseiConan on 2011-07-12
Tried that, didn't work. I tried everything. Enabling both IPv4 and IPv6, Enabling one and disabling the other. Disabling both. Thanks but it didn't really work. :\

---

### Post by theozzlives on 2011-07-12
> **chili555 said:**
> Exactly correct. If you look around in there, you'll find a menu that allows you to scroll down and see and change various settings. Here is and example of the IRQ page.

You might try downloading an earlier version of Ubuntu and trying it. By the way, if you are capable of running Ubuntu on a USB stick and asking about it on this forum, I don't believe you're stupid at all. You may be inexperienced but even I was inexperienced at one time. Nobody knows everything on their first week or so.

That was a screen shot of an IBM BIOS! A Dell BIOS is different. I suggest that you install 10.04.2 it's a long term release and it works fine.

---

### Post by chili555 on 2011-07-12
> Firmware left e100 interrupts enabled; disablingI am Googling this; it looks mysterious and I've never seen it previously. It may (or may not) be a clue.

---

### Post by theozzlives on 2011-07-12
> **chili555 said:**
> I am Googling this; it looks mysterious and I've never seen it previously. It may (or may not) be a clue.

I've been through versions and alphas since 7.04. 11.04 does not do networking well, so I well to 10.04 since it's a long term release. I suggest you do the same (at least on the Dell).

---

### Post by JackYuseiConan on 2011-07-13
Yeah I'm downloading 10.04 now. I may as well, if it fixes things. I'm really sorry about the fuss I've caused and @chili555 thank you so much for helping. :) I really appreciate it.

---

### Post by JackYuseiConan on 2011-07-13
Okay... Ubuntu just seems to dislike my computer... :\ Do I need to instal drivers or something?

---

### Post by chili555 on 2011-07-13
> Do I need to instal drivers or something?See post #5. The driver for your ethernet comes preinstalled.

---

### Post by JackYuseiConan on 2011-07-13
Oh... Well in that case, Ubuntu just dislikes my computer. :\

---

### Post by JackYuseiConan on 2011-07-13
So should I just leave Ubuntu?

---

### Post by JackYuseiConan on 2011-07-13
... I should explain. By leave I meant leave it alone on my desktop. :P I'll still have it on my laptop.

---

### Post by chili555 on 2011-07-13
> **JackYuseiConan said:**
> ... I should explain. By leave I meant leave it alone on my desktop. :P I'll still have it on my laptop.I still don't understand. Isn't your laptop the computer with the Intel e100 non-functioning ethernet card? Did you download and burn to disk the 10.04 version? Did you run it live and try the ethernet?

---

### Post by JackYuseiConan on 2011-07-13
No, I have a laptop and a desktop computer. My laptop can connect to the Internet using wi-fi, ergo no need for ethernet. Although I haven't tried. But my desktop computer is the one that's not working.

Also, I did download 10.04 and I ran it straight off the USB, i.e. I didn't install it.

---

### Post by chili555 on 2011-07-13
> my desktop computer is the one that's not working.OK, now I think I've got it. I thought those Intels were laptop parts but, as I often say, I learn something new every day! I am not sure I have any other suggestions aside from a new card. They're cheap and easy to install. You might try switching the PCI slot with the card you have now, however.

---

### Post by JackYuseiConan on 2011-07-13
Really? But the card is working... I am dual-booting Ubuntu and Windows XP on it and Windows can connect to it perfectly. It's just something with Ubuntu for some reason... :\ Idk, I'll probably get a new PC. I mean I like my Dell Dimension, but I've maxed out the ram (2Gb), the processor can't be upgraded to much, same with most of the other things. I was gonna get a new Mobo, but apparently, Dell's are designed to fit certain Dell Mobos which is kinda stupid. <_< So I might just get a new Desktop.

---

### Post by Fedupera on 2012-07-17
I did experience a similar problem with an error resolving the address.

When I upgraded from Lubuntu 11.10 to Lubuntu 12.04, the network was re-established but it was not possible to browse the web. The browser could not find the DNS servers at my I.S.P. and hence could not resolve the address. This was so even though D.H.C.P. was enabled in the network preferences.

I resolved the issue by adding an extra line to the file /etc/network/interfaces for the gateway address. My gateway router had the i.p. address 192.168.0.1 and it connected to the ISP gateway address of 77.101.xx.xx. Oddly, it was this address I had to use.

interfaces file entries

# The primary network interface
auto eth0
iface eth0 inet dhcp
Gateway 77.101.xx.xx

Maybe this will work for you.

---

### Post by wildmanne39 on 2012-07-17
Hi, thanks for sharing, the thread has been closed, please do not post in a thread that has been inactive for a year or more.
Thanks

---

