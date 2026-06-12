---
title: "Wireless Not at all working"
date: 2012-10-31
forum: Networking &amp; Wireless
---

### Post by 7Starphy on 2012-10-31
These are the problems I am facing with my wireless while starting with Ubuntu 12.04 . I am stuck ,not able to find a solution :( . People please help .


tried lspci -v and this was my following output
```


00:00.0 Host bridge: Intel Corporation Ivy Bridge DRAM Controller (rev 09)
	Subsystem: Dell Device 056a
	Flags: bus master, fast devsel, latency 0
	Capabilities: <access denied>
	Kernel driver in use: agpgart-intel

00:01.0 PCI bridge: Intel Corporation Ivy Bridge PCI Express Root Port (rev 09) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=06, sec-latency=0
	I/O behind bridge: 00003000-00003fff
	Memory behind bridge: c0000000-c0ffffff
	Prefetchable memory behind bridge: 00000000a0000000-00000000afffffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:02.0 VGA compatible controller: Intel Corporation Ivy Bridge Graphics Controller (rev 09) (prog-if 00 [VGA controller])
	Subsystem: Dell Device 056a
	Flags: bus master, fast devsel, latency 0, IRQ 44
	Memory at c1000000 (64-bit, non-prefetchable) [size=4M]
	Memory at b0000000 (64-bit, prefetchable) [size=256M]
	I/O ports at 4000 [size=64]
	Expansion ROM at <unassigned> [disabled]
	Capabilities: <access denied>
	Kernel driver in use: i915
	Kernel modules: i915

00:14.0 USB controller: Intel Corporation Panther Point USB xHCI Host Controller (rev 04) (prog-if 30 [XHCI])
	Subsystem: Dell Device 056a
	Flags: bus master, medium devsel, latency 0, IRQ 42
	Memory at c1600000 (64-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>
	Kernel driver in use: xhci_hcd

00:16.0 Communication controller: Intel Corporation Panther Point MEI Controller #1 (rev 04)
	Subsystem: Dell Device 056a
	Flags: bus master, fast devsel, latency 0, IRQ 45
	Memory at c1614000 (64-bit, non-prefetchable) [size=16]
	Capabilities: <access denied>
	Kernel driver in use: mei
	Kernel modules: mei

00:1a.0 USB controller: Intel Corporation Panther Point USB Enhanced Host Controller #2 (rev 04) (prog-if 20 [EHCI])
	Subsystem: Dell Device 056a
	Flags: bus master, medium devsel, latency 0, IRQ 16
	Memory at c1619000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:1b.0 Audio device: Intel Corporation Panther Point High Definition Audio Controller (rev 04)
	Subsystem: Dell Device 056a
	Flags: bus master, fast devsel, latency 0, IRQ 46
	Memory at c1610000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: snd_hda_intel
	Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 1 (rev c4) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=07, subordinate=07, sec-latency=0
	I/O behind bridge: 00002000-00002fff
	Prefetchable memory behind bridge: 00000000c1400000-00000000c14fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 2 (rev c4) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=08, subordinate=08, sec-latency=0
	Memory behind bridge: c1500000-c15fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1d.0 USB controller: Intel Corporation Panther Point USB Enhanced Host Controller #1 (rev 04) (prog-if 20 [EHCI])
	Subsystem: Dell Device 056a
	Flags: bus master, medium devsel, latency 0, IRQ 23
	Memory at c1618000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:1f.0 ISA bridge: Intel Corporation Panther Point LPC Controller (rev 04)
	Subsystem: Dell Device 056a
	Flags: bus master, medium devsel, latency 0
	Capabilities: <access denied>
	Kernel modules: iTCO_wdt

00:1f.2 SATA controller: Intel Corporation Panther Point 6 port SATA Controller [AHCI mode] (rev 04) (prog-if 01 [AHCI 1.0])
	Subsystem: Dell Device 056a
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 41
	I/O ports at 4088 [size=8]
	I/O ports at 4094 [size=4]
	I/O ports at 4080 [size=8]
	I/O ports at 4090 [size=4]
	I/O ports at 4060 [size=32]
	Memory at c1617000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: <access denied>
	Kernel driver in use: ahci

00:1f.3 SMBus: Intel Corporation Panther Point SMBus Controller (rev 04)
	Subsystem: Dell Device 056a
	Flags: medium devsel, IRQ 10
	Memory at c1615000 (64-bit, non-prefetchable) [size=256]
	I/O ports at 4040 [size=32]
	Kernel modules: i2c-i801

01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Thames XT/GL [Radeon HD 7600M Series] (prog-if 00 [VGA controller])
	Subsystem: Dell Device 056a
	Flags: bus master, fast devsel, latency 0, IRQ 47
	Memory at a0000000 (64-bit, prefetchable) [size=256M]
	Memory at c0000000 (64-bit, non-prefetchable) [size=128K]
	I/O ports at 3000 [size=256]
	Expansion ROM at c0020000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: radeon
	Kernel modules: radeon

07:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 05)
	Subsystem: Dell Device 056a
	Flags: bus master, fast devsel, latency 0, IRQ 43
	I/O ports at 2000 [size=256]
	Memory at c1404000 (64-bit, prefetchable) [size=4K]
	Memory at c1400000 (64-bit, prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: r8169
	Kernel modules: r8169

08:00.0 Network controller: Broadcom Corporation Device 4365 (rev 01)
	Subsystem: Dell Device 0016
	Flags: bus master, fast devsel, latency 0, IRQ 11
	Memory at c1500000 (64-bit, non-prefetchable) [size=32K]
	Capabilities: <access denied>

```

 And the following outputs

This is the output for ```
 lspci -nnk | grep -iA3 net 
```

```


lspci -nnk | grep -iA3 net
07:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
	Subsystem: Dell Device [1028:056a]
	Kernel driver in use: r8169
	Kernel modules: r8169
08:00.0 Network controller [0280]: Broadcom Corporation Device [14e4:4365] (rev 01)
	Subsystem: Dell Device [1028:0016]

```

And the output for ```
lspci -nn | grep 0280 
```

is 

```


08:00.0 Network controller [0280]: Broadcom Corporation Device [14e4:4365] (rev 01)

```

---

### Post by Hadaka on 2012-10-31
Thanks Chill555, This should be a fun one, I will follow along
to see the end results.  GOOD LUCK !

---

### Post by chili555 on 2012-10-31
Boy, oh boy! This is your lucky day. You have an unsupported device where the fix is tricky and experimental! Congratulations!

Please see here: [http://askubuntu.com/questions/175104/how-do-i-install-bcm43142-wireless-drivers-for-dell-vostro-3460-3560](http://askubuntu.com/questions/175104/how-do-i-install-bcm43142-wireless-drivers-for-dell-vostro-3460-3560)

Notice your device is the same as described there:> Broadcom Corporation Device [[COLOR="Red"]14e4:4365[/COLOR]]Please hook up the ethernet cable temporarily and do:```
sudo apt-get install linux-headers-generic build-essential dkms
```Find out if you have a 32- or 64-bit install:```
arch
```32-bit will return i686 and 64-bit will be x86_64. Download the appropriate file to your desktop. Back to the terminal and do:```
cd Desktop
sudo dpkg -i wireless*.deb
```Reboot with the ethernet detached and it should be working.

Post back any errors or stumbling blocks.

---

### Post by 7Starphy on 2012-11-01
Hi Chili555 :)

Can you please tell what code I should type for 64-bit operating system ? I didnt follow the last code fragment :( My OS is 64-bit and the command arch returned x86_64.

The ```
sudo apt-get install linux-headers-generic build-essential dkms 
``` , gave the following output .
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
dkms is already the newest version.
build-essential is already the newest version.
linux-headers-generic is already the newest version.
The following package was automatically installed and is no longer required:
  lib32gcc1
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

---

### Post by Hadaka on 2012-11-01
Hi, use the 64 bit deb file in the link he posted at the top of his
reply.

[http://askubuntu.com/questions/175104/how-do-i-install-bcm43142-wireless-drivers-for-dell-vostro-3460-3560](http://askubuntu.com/questions/175104/how-do-i-install-bcm43142-wireless-drivers-for-dell-vostro-3460-3560)

also..run the autoremove you got in your last post.

---

### Post by 7Starphy on 2012-11-01
That link is not working :(

And I did the autoremove....now what should I do ?

---

### Post by Hadaka on 2012-11-01
Hi, it works for me no problem, are you accessing the net
with the ethernet cable via Ubuntu or windows?

---

### Post by 7Starphy on 2012-11-01
Ethernet cable via ubuntu ..for me it is coming ''webpage is not available" .


I am using Internet via my University Proxy server..it is blocking Dropbox.com , I think :(

---

### Post by Hadaka on 2012-11-01
Well....shame on them :D. Looks like you get to hang at 
Mcdonalds or starbucks....Do you know how to drag the deb file from the Download
folder to the desktop? when you finally get it...thats what you need to do, then
issue the last commands Chill555 gave you.

---

### Post by 7Starphy on 2012-11-01
Thanks :)

For that I need to download..now how do I download...have to ask some students who can bypass the university proxy :D

---

### Post by Hadaka on 2012-11-01
Let me see if i can load it...zip it and send it to you.

---

### Post by 7Starphy on 2012-11-01
yes ,that would be lovely ..thanks a lot :)

---

### Post by Hadaka on 2012-11-01
first time zipping with ubuntu

---

### Post by Hadaka on 2012-11-01
zip file exceedes the alloted size

---

### Post by Hadaka on 2012-11-01
ok sent via e-mail, let me know when you have it and i can guide you
through install.

---

### Post by 7Starphy on 2012-11-01
Thanks a lot :)

I have put the folder in Desktop..now what command should i type ?

---

### Post by Hadaka on 2012-11-01
great !...ok..drag it to the actual desktop..so you can see th eicon of it///then
right click and choose open here...thats it

then do the last comands from chilli555

---

### Post by 7Starphy on 2012-11-01
Do you want to extract the deb folder ? Oh my god..I am confused ,I am sorry :(

I put the .deb file in desktop ...after that can you tell what command I should type ..I followed Chili555's command ,but it is returning an error :( Sorry I am new, so I am finding it pretty complicated...

---

### Post by Hadaka on 2012-11-01
Hi...ok..drag the file from the desktop folder to the actual purple desktop
and dump it there....then right click it...and choose......open here,extract here
one of those.

---

### Post by 7Starphy on 2012-11-01
I extracted it ..now I have a folder which has two subfolders within it ...

---

### Post by Hadaka on 2012-11-01
thats ok...now do the last 2 commands in post 2 of this thread...:P

---

### Post by 7Starphy on 2012-11-01
Ok I know I am being very dumb :D ,but this is what I am getting

```


sudo dpkg -i wireless*.deb
dpkg: regarding wireless-bcm43142-dkms-6.20.55.19_amd64(1).deb containing wireless-bcm43142-oneiric-dkms:
 wireless-bcm43142-oneiric-dkms conflicts with bcmwl-kernel-source
  bcmwl-kernel-source (version 5.100.82.38+bdcom-0ubuntu6.1) is present and installed.
dpkg: error processing wireless-bcm43142-dkms-6.20.55.19_amd64(1).deb (--install):
 conflicting packages - not installing wireless-bcm43142-oneiric-dkms
Errors were encountered while processing:
 wireless-bcm43142-dkms-6.20.55.19_amd64(1).deb

```

---

### Post by Hadaka on 2012-11-01
looks like you might have some stuff from before in there.
please post ...

```
lspci -nnk | grep -iA3 net 
```

---

### Post by 7Starphy on 2012-11-01
```


 lspci -nnk | grep -iA3 net
07:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
	Subsystem: Dell Device [1028:056a]
	Kernel driver in use: r8169
	Kernel modules: r8169
08:00.0 Network controller [0280]: Broadcom Corporation Device [14e4:4365] (rev 01)
	Subsystem: Dell Device [1028:0016]

```

---

### Post by Hadaka on 2012-11-01
try this, then try to load the deb file again

```
sudo apt-get remove --purge bcmwl-kernel-source
 
```

---

### Post by 7Starphy on 2012-11-01
Wow :) I think the installation worked fine ...this was the output I got 
```


sudo dpkg -i wireless*.deb
(Reading database ... 181315 files and directories currently installed.)
Unpacking wireless-bcm43142-oneiric-dkms (from wireless-bcm43142-dkms-6.20.55.19_amd64(1).deb) ...
Setting up wireless-bcm43142-oneiric-dkms (6.20.55.19~bdcom0602.0400.1000.0400-0somerville1) ...
Loading new wireless-bcm43142-oneiric-dkms-6.20.55.19~bdcom0602.0400.1000.0400 DKMS files...
First Installation: checking all kernels...
Building only for 3.2.0-32-generic
Building for architecture x86_64
Building initial module for 3.2.0-32-generic
Done.

wl:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.2.0-32-generic/updates/dkms/

depmod....

DKMS: install completed.
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.2.0-32-generic

```

Now what should I do ?

---

### Post by Hadaka on 2012-11-01
run the last 2 commands in post #2 of this thread,remove the ethernet
cable..boot and see if it works

---

### Post by 7Starphy on 2012-11-01
Wow! 

Yes ! It is working fine :) 

Thanks a lot friends :)

---

### Post by Hadaka on 2012-11-01
Great ! fun learning experience.
be sure to mark this SOLVED
click thread tools to mark solved

---

### Post by 7Starphy on 2012-11-01
Yes sure :)

But can you tell me what exactly the problem was ..why things didnt work before and why things work now ? Shouldnt these wireless drivers come pre-installed...or something like that?

---

### Post by Hadaka on 2012-11-01
preinstalled??   where would the fun it that be?
alot of cards, video and network are created for 
the masses,,,a.k.a windows users...and dont supply
linux drivers. Your card is a rare one, but...it was interesting
and hopefully the next person stuck will find this thread
and not have to jump through so many hoops.

---

### Post by 7Starphy on 2012-11-01
Oh..wow..this is really adventurous and getting fun :)

---

### Post by chili555 on 2012-11-01
Wow! You two have been having great fun while I slept! I'm very glad it's working.

By the way, the original link works for me. If any searchers have trouble with it, post back and we'll help.

---

