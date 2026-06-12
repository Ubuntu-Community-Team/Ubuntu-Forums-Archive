---
title: "Ubuntu 9.10 Sound Problem"
date: 2009-11-22
forum: Multimedia Software
---

### Post by kiran88pnjr on 2009-11-22
I've upgraded to Ubuntu 9.10 yesterday from 9.04. Everything was perfect in 9.04. But, after upgrading to 9.10 no sound is working. 

When I used the command : 'lspci -v' to list my sound card.

In terminal I got :






kiran@Ubuntu:~$ aplay -l
aplay: device_list:223: no soundcards found...
kiran@Ubuntu:~$ lspci -v
00:00.0 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a1)
	Subsystem: ASUSTeK Computer Inc. Device 8234
	Flags: bus master, 66MHz, fast devsel, latency 0
	Capabilities: <access denied>

00:01.0 ISA bridge: nVidia Corporation MCP61 LPC Bridge (rev a2)
	Subsystem: ASUSTeK Computer Inc. Device 8234
	Flags: bus master, 66MHz, fast devsel, latency 0
	I/O ports at 0900 [size=256]

00:01.1 SMBus: nVidia Corporation MCP61 SMBus (rev a2)
	Subsystem: ASUSTeK Computer Inc. Device 8234
	Flags: 66MHz, fast devsel, IRQ 10
	I/O ports at 0e00 [size=64]
	I/O ports at 0600 [size=64]
	I/O ports at 0700 [size=64]
	Capabilities: <access denied>
	Kernel driver in use: nForce2_smbus
	Kernel modules: i2c-nforce2

00:01.2 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a2)
	Subsystem: ASUSTeK Computer Inc. Device 8234
	Flags: 66MHz, fast devsel

00:02.0 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3) (prog-if 10)
	Subsystem: ASUSTeK Computer Inc. Device 8234
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 5
	Memory at dffff000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: ohci_hcd

00:02.1 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3) (prog-if 20)
	Subsystem: ASUSTeK Computer Inc. Device 8234
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 11
	Memory at dfffec00 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:04.0 PCI bridge: nVidia Corporation MCP61 PCI bridge (rev a1) (prog-if 01)
	Flags: bus master, 66MHz, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
	Capabilities: <access denied>

00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)
	Subsystem: ASUSTeK Computer Inc. Device 8290
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 10
	Memory at dfff8000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:06.0 IDE interface: nVidia Corporation MCP61 IDE (rev a2) (prog-if 8a [Master SecP PriP])
	Subsystem: ASUSTeK Computer Inc. (Wrong ID) Device 8234
	Flags: bus master, 66MHz, fast devsel, latency 0
	[virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
	[virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
	[virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
	[virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
	I/O ports at ffa0 [size=16]
	Capabilities: <access denied>
	Kernel driver in use: pata_amd

00:07.0 Bridge: nVidia Corporation MCP61 Ethernet (rev a2)
	Subsystem: ASUSTeK Computer Inc. Device 8234
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 2300
	Memory at dfffd000 (32-bit, non-prefetchable) [size=4K]
	I/O ports at e480 [size=8]
	Capabilities: <access denied>
	Kernel driver in use: forcedeth
	Kernel modules: forcedeth

00:08.0 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2) (prog-if 85 [Master SecO PriO])
	Subsystem: ASUSTeK Computer Inc. Device 8234
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 11
	I/O ports at e400 [size=8]
	I/O ports at e080 [size=4]
	I/O ports at e000 [size=8]
	I/O ports at dc00 [size=4]
	I/O ports at d880 [size=16]
	Memory at dfffc000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: sata_nv

00:09.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:0b.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:0c.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:0d.0 VGA compatible controller: nVidia Corporation C61 [GeForce 6150SE nForce 430] (rev a2)
	Subsystem: ASUSTeK Computer Inc. Device 8234
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 11
	Memory at de000000 (32-bit, non-prefetchable) [size=16M]
	Memory at c0000000 (64-bit, prefetchable) [size=256M]
	Memory at dd000000 (64-bit, non-prefetchable) [size=16M]
	[virtual] Expansion ROM at dffc0000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: nvidia
	Kernel modules: nvidia, nvidiafb

00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
	Flags: fast devsel
	Capabilities: <access denied>

00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
	Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
	Flags: fast devsel

00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
	Flags: fast devsel
	Capabilities: <access denied>
	Kernel driver in use: k8temp
	Kernel modules: k8temp






My sound preferences shows this no hardware to configure. 



[http://lh3.ggpht.com/_yZ0F4QNxAgE/Swnj9oyn3wI/AAAAAAAAA8E/pW_yi8ZfU4Y/s640/Screenshot-8.png](http://lh3.ggpht.com/_yZ0F4QNxAgE/Swnj9oyn3wI/AAAAAAAAA8E/pW_yi8ZfU4Y/s640/Screenshot-8.png)





**My Kernel is : Linux Ubuntu 2.6.28-11-generic**




Synaptic shows another installed kernel too as installed : 




**linux-image-2.6.31-14-generic**




**My firefox not working too.**




I don't know what to do. Please help me.

:confused::confused::confused::confused::confused::confused:

---

### Post by Mr Nemo on 2009-11-22
I'm very very new to ubuntu, but I had the same problems when I upgraded to 9.10. They resolved themselves when I did a fresh install of 9.10. If reinstalling ubuntu 9.10 won't be a giant pain in the ***, then I suggest that. I was told by a more ubuntu experienced friend that because of the switch from ext3 to ext4 it would be better to do a fresh install of the OS. Sorry if that didn't help at all.

---

### Post by p110011 on 2009-11-22
> **kiran88pnjr said:**
> 
**linux-image-2.6.31-14-generic**




**My firefox not working too.**




I don't know what to do. Please help me.

:confused::confused::confused::confused::confused::confused:

Go back to Synaptic and install that latest Linux-headers and Linux-image
Reboot and if it works you can remove 2.6.28

---

### Post by kiran88pnjr on 2009-11-23
> **Mr Nemo said:**
> I'm very very new to ubuntu, but I had the same problems when I upgraded to 9.10. They resolved themselves when I did a fresh install of 9.10. If reinstalling ubuntu 9.10 won't be a giant pain in the ***, then I suggest that. I was told by a more ubuntu experienced friend that because of the switch from ext3 to ext4 it would be better to do a fresh install of the OS. Sorry if that didn't help at all.

Mine is a dualboot linux system that includes Debian Lenny. It's default partition is ext3 & 9.10's ext4. When I installed 9.04 using ext4 partition it don't detect Debian Lenny at the time of Grub Configuration. My bro want to use Lenny & I need Ubuntu. I fear that a fresh installation may cause the lose of Debian. That's why I've upgraded from internet though I've purchased disc from Ubuntu. 
:confused::confused::confused::confused::confused::confused:

---

### Post by kiran88pnjr on 2009-11-23
> **p110011 said:**
> Go back to Synaptic and install that latest Linux-headers and Linux-image
Reboot and if it works you can remove 2.6.28

Mine is a dual boot system & using Debian's Grub. It still shows the name of Ubuntu 9.04 that I used previously. Grub not showing newly installed 2.6.28. Though I install 2.6.31, I may not be able to boot into that.

:confused::confused::confused::confused::confused:

---

### Post by poohman on 2009-11-23
Try doing a update-grub, may solve the problem of sound as karmic maybe using the old kernel. If the kernel is not getting updated, try renaming /boot/grub/menu.lst and then do a update-grub.

---

### Post by kiran88pnjr on 2009-11-23
> **poohman said:**
> Try doing a update-grub, may solve the problem of sound as karmic maybe using the old kernel. If the kernel is not getting updated, try renaming /boot/grub/menu.lst and then do a update-grub.

I don't know hw to do it. :confused::confused::confused:

---

### Post by poohman on 2009-11-24
Open Terminal
sudo mv /boot/grub/menu.lst /boot/grub/menubackup.lst
sudo update-grub

---

### Post by kiran88pnjr on 2009-11-24
> **poohman said:**
> Open Terminal
sudo mv /boot/grub/menu.lst /boot/grub/menubackup.lst
sudo update-grub

I've decided to have a fresh installation.

My thread regarding that :

[http://ubuntuforums.org/showthread.php?p=8381072#post8381072](http://ubuntuforums.org/showthread.php?p=8381072#post8381072)

:confused::confused::confused:

---

### Post by HippieDave on 2009-11-24
I have same problem, my upgrade to 9.10 won't recognize my M Audio 2496 card, and so far the tech solutions are way over my head.

If I use the aplay -l command, I get the following, which at least recognizes my sound card:

[I][B]card 1: M2496 [M Audio Audiophile 24/96], device 0: ICE1712 multi [ICE1712 multi]
  Subdevices: 1/1
  Subdevice #0: subdevice #0[/B]
[/I]
But if I use the  'lspci -v'command, it doesn't include the MAudio device at all.

That's all I have been able to determine so far. Please! Any help?

---

### Post by kiran88pnjr on 2009-11-25
> **HippieDave said:**
> I have same problem, my upgrade to 9.10 won't recognize my M Audio 2496 card, and so far the tech solutions are way over my head.

If I use the aplay -l command, I get the following, which at least recognizes my sound card:

[I][B]card 1: M2496 [M Audio Audiophile 24/96], device 0: ICE1712 multi [ICE1712 multi]
  Subdevices: 1/1
  Subdevice #0: subdevice #0[/B]
[/I]
But if I use the  'lspci -v'command, it doesn't include the MAudio device at all.

That's all I have been able to determine so far. Please! Any help?

I don't know what to do. I googled abt it & I've a forum search too. But all of it suggested to have a reinstallation. It is the only way now to solve the problem.   

:confused::confused::confused:

---

### Post by p110011 on 2009-11-25
> **HippieDave said:**
> I have same problem, my upgrade to 9.10 won't recognize my M Audio 2496 card, and so far the tech solutions are way over my head.

If I use the aplay -l command, I get the following, which at least recognizes my sound card:

[I][B]card 1: M2496 [M Audio Audiophile 24/96], device 0: ICE1712 multi [ICE1712 multi]
  Subdevices: 1/1
  Subdevice #0: subdevice #0[/B]
[/I]
But if I use the  'lspci -v'command, it doesn't include the MAudio device at all.

That's all I have been able to determine so far. Please! Any help?

You could do what Poohman suggested or like I did was to get the new Kernel through Synaptic or you can upgrade to grub2

---

### Post by kiran88pnjr on 2009-11-26
> **p110011 said:**
> You could do what Poohman suggested or like I did was to get the new Kernel through Synaptic or you can upgrade to grub2

My Synaptic suggests the installations of both kernels, 2.6.28 & 2.6.31. But the Grub currently using is of Debian Lenny's 0.97.After upgradation too it still shows the name as 'Ubuntu 9.04 2.6.28'. 

I don't know to update grub & boot to 2.6.31. Fear I may not able too boot again to either OS'. 

Do I need to install Grub 2 instead of Debian' 0.97 ? 

:confused::confused::confused::confused::confused:

---

### Post by p110011 on 2009-11-26
> **kiran88pnjr said:**
> My Synaptic suggests the installations of both kernels, 2.6.28 & 2.6.31. But the Grub currently using is of Debian Lenny's 0.97.After upgradation too it still shows the name as 'Ubuntu 9.04 2.6.28'. 

I don't know to update grub & boot to 2.6.31. Fear I may not able too boot again to either OS'. 

Do I need to install Grub 2 instead of Debian' 0.97 ? 

:confused::confused::confused::confused::confused:

Well, I'm not too sure what Ubuntu you are having problems with. Your first post, you said you upgraded to 9.10. If you're using 9.04 then I don't know, sorry.

---

### Post by IamKamekaze on 2009-11-26
> **kiran88pnjr said:**
> I've upgraded to Ubuntu 9.10 yesterday from 9.04. Everything was perfect in 9.04. But, after upgrading to 9.10 no sound is working. 



Did you try going into prefrences?
I searched far and wide before I figured out that I needed to be using the sterio duplex 7.0 But I've got an onboard soundcard. =P

---

### Post by HippieDave on 2009-11-27
OK. Progress but no success.  I upgraded the asla 1.0.20 file to 1.0.21 and I now get sound when playing internet stuff (you tube) AND when playing Audacity recordings off my hard drive. But no sound when trying to play mp3 files off the hard drive or off of CDs.  Any thoughts?

---

### Post by kiran88pnjr on 2009-11-28
Hey Guys............. 

Just check out your 9.10 live. I've it & can hear sound using it.

TC :p

---

### Post by duanedesign on 2010-01-04
[Here is a guide]("https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats") for troubleshooting sound in Karmic.

[This thread]("http://ubuntuforums.org/showthread.php?t=789578") is also a good resource for sound problems
-
-
-

---

