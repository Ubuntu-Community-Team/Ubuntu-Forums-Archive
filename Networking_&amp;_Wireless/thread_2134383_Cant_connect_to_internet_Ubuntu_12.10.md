---
title: "Cant connect to internet Ubuntu 12.10"
date: 2013-04-11
forum: Networking &amp; Wireless
---

### Post by Trublet on 2013-04-11
[COLOR=#333333]I'm having a problem connecting to internet on Ubuntu 12.10(just installed after giving up with 12.04 issues with graphics card) with a wireless and with a wired connection. I have looked into solving this problem myself but after much trouble and frustration I could use some help.
[/COLOR]
[COLOR=#333333]To my understanding I believe its because i have an AR8161 Ethernet controller and don't have the proper driver packages. This is where i'm having trouble, i don't know which packages to install or how to. I tried the download links people posted for people with a very similar issue. Either they don't work or i'm not installing them right. The way i tried to install them was i downloaded them on this computer and used a USB drive(key?) to transfer to the laptop without the internet connection and then opened them with the Ubuntu software center which led me to an error every time. Please be clear in your instructions because like i stated earlier i'm not computer savvy...yet :)
[/COLOR]
[COLOR=#333333]Any help will be greatly appreciated and any information you need from me i will post.[/COLOR]
[COLOR=#333333]
Thanks

[/COLOR]

---

### Post by chili555 on 2013-04-11
Your device uses the relatively new driver *alx* as I'm sure you've determined in your research. It is included in the latest kernel version, 3.5.0-27 by default. I'm very confident you could download the packages linux-image-3.5.0-27-generic and also linux-image-extra-3.5.0-27-generic appropriate to your architecture, either 32- or 64-bit, install them, reboot and be done. Of course, you could install the latest daily build for 13.04 and be done as well. The advantage to 13.04 is that you can try the live DVD and be sure everything is working as expected before you install it.

Which do you prefer? I will be happy to help you in either case. 

Please tell us the following from the terminal.```
arch
lspci -nn
```Thanks.

---

### Post by Trublet on 2013-04-11
Yeah thats what i read about, but the problem is i don't know what packages or how to install the packages. Most instructions are vague because its probably common knowledge for most ubuntu users, but if your not familiar with ubuntu its extremely vague. I have to transfer all the files from computer to computer with a usb. I explained how i tried to install them in the first post(probably the wrong way). I'll just try to finish fixing 12.10. I appreciate the help! :) Also if you don't mind im trying to learn more about computers so if you don't mind explaining why we are doing things i would greatly appreciate that!! The first command i know was to check if its a 32bit or 64bit. 

> :~$ arch 
x86_64
 

> :~$ lspci-nn 
00:00.0 Host bridge [0600]: IntelCorporation 3rd Gen Core processor DRAM Controller [8086:0154] (rev09) 
00:01.0 PCI bridge [0604]: IntelCorporation Xeon E3-1200 v2/3rd Gen Core processor PCI Express RootPort [8086:0151] (rev 09) 
00:14.0 USB controller [0c03]: IntelCorporation 7 Series/C210 Series Chipset Family USB xHCI HostController [8086:1e31] (rev 04) 
00:16.0 Communication controller[0780]: Intel Corporation 7 Series/C210 Series Chipset Family MEIController #1 [8086:1e3a] (rev 04) 
00:1a.0 USB controller [0c03]: IntelCorporation 7 Series/C210 Series Chipset Family USB Enhanced HostController #2 [8086:1e2d] (rev 04) 
00:1b.0 Audio device [0403]: IntelCorporation 7 Series/C210 Series Chipset Family High Definition AudioController [8086:1e20] (rev 04) 
00:1c.0 PCI bridge [0604]: IntelCorporation 7 Series/C210 Series Chipset Family PCI Express Root Port1 [8086:1e10] (rev c4) 
00:1c.1 PCI bridge [0604]: IntelCorporation 7 Series/C210 Series Chipset Family PCI Express Root Port2 [8086:1e12] (rev c4) 
00:1d.0 USB controller [0c03]: IntelCorporation 7 Series/C210 Series Chipset Family USB Enhanced HostController #1 [8086:1e26] (rev 04) 
00:1f.0 ISA bridge [0601]: IntelCorporation HM76 Express Chipset LPC Controller [8086:1e59] (rev 04) 
00:1f.2 SATA controller [0106]: IntelCorporation 7 Series Chipset Family 6-port SATA Controller [AHCImode] [8086:1e03] (rev 04) 
00:1f.3 SMBus [0c05]: Intel Corporation7 Series/C210 Series Chipset Family SMBus Controller [8086:1e22] (rev04) 
01:00.0 VGA compatible controller[0300]: Advanced Micro Devices [AMD] nee ATI Thames XT/GL [Radeon HD7600M Series] [1002:6840] 
01:00.1 Audio device [0403]: AdvancedMicro Devices [AMD] nee ATI Turks/Whistler HDMI Audio [Radeon HD 6000Series] [1002:aa90] 
07:00.0 Ethernet controller [0200]:Atheros Communications Inc. AR8161 Gigabit Ethernet [1969:1091] (rev10) 
08:00.0 Network controller [0280]:Realtek Semiconductor Co., Ltd. Device [10ec:8723]

---

### Post by Trublet on 2013-04-12
Ok well i finally figured out how to install packages (i didn't know you had to go to the directory of where the file was before using a command). So i installed those 2 packages and rebooted and idk if that fixed the problem but i have a completely new one now, the screen just flashes with the purple background and i can't see anything.

---

### Post by chili555 on 2013-04-12
> **Trublet said:**
> Ok well i finally figured out how to install packages (i didn't know you had to go to the directory of where the file was before using a command). So i installed those 2 packages and rebooted and idk if that fixed the problem but i have a completely new one now, the screen just flashes with the purple background and i can't see anything.Which packages? The linux-image packages? I assume you downloaded and installed the 64-bit versions.> :~$ arch
[COLOR="#FF0000"]x86_64[/COLOR]

I suggest you reboot, interrupt the boot process with the shift key to get to the GRUB menu and boot into the earlier kernel; I suspect you want 3.5.0-17 instead of -27. Please see attached. Then look in the logs to see what went wrong:```
less /var/log/dmesg.0
```dmesg is a log of kernel messages that's created at every boot. The current log can be accessed with:```
dmesg
```You can scroll back and forth with the arrow keys with:```
dmesg | less
```Get out of less with q.

The message log for the prior boot, presumably the flashing screen boot, is stored at /var/log/dmesg[COLOR="#FF0000"]**.0**[/COLOR]. Again, scroll with the arrow keys. ```
cat /var/log/Xorg.0.log | grep EE
```The Xorg log is all about graphics; that is the screen. We pipe | our command through 'grep' so it looks for a pattern; in this case EE for errors. 

Find the error and we'll work to correct it. You can actually remove the 3.5.0-27 packages at that point if that's the error:```
sudo dpkg -P linux-image-3.5.0-27*
```Almost every command has a manual page (RTFriendlyM). In this case you can see what we're doing with:```
man dpkg
```Let me know how it goes. I suspect we can easily fix this.

---

### Post by Trublet on 2013-04-12
Yes, the 2 packages you listed in your first post, but before I continue i want you to know that after I got the black screen after boot( sometimes flashy purple) i read how to get into the grub, like you explained and get into recovery mode on the 3.5.0-27 kernel without graphics and the internet was working so i used the following commands to get recent updates and upgrades which to my understanding was going to fix the problem...but it didn't. 

```
sudo apt-get update
```
```
sudo apt-get upgrade
```


I don't know if that changes anything from what you are telling me so im letting you know. After doing what you explained ( I didn't understand much of what was in the less log for dmesg.0 but thanks for explaining it to me!) this is what i got when using the command to find errors. It looked to me like this wasn't due to the the 3.5.0-27 packages so i didn't proceed with your instructions.

```
$ cat /var/log/Xorg.0.log | grep EE    (WW) warning, (EE) error, (NI) notimplemented, (??) unknown. 
[    18.280] Initializing built-inextension MIT-SCREEN-SAVER 
[    18.398] (EE) Failed to load module"fglrx" (module does not exist, 0) 
[    18.461] (EE) Failed to load module"fglrx" (module does not exist, 0)
```

Anyways that's where i'm currently at and i greatly appreciate all of your help!

Thanks

---

### Post by chili555 on 2013-04-12
> (EE) Failed to load module"fglrx" (module does not exist, 0)As we suspected, fglrx is a video driver for AMD (formerly ATI) video cards. Is that what you have?```
sudo lshw -C display
```Is fglrx installed?```
sudo dpkg -s fglrx
```We are quickly getting out of my area of expertise, so if you have a video issue, you'll probably want to post it over on General Help.> and the internet was working That's good news!

---

### Post by Trublet on 2013-04-13
> [COLOR=#000000]As we suspected, fglrx is a video driver for AMD (formerly ATI) video cards. Is that what you have?[/COLOR]

Yes i have the Radeon 7670M Series.

> [COLOR=#000000]Is fglrx installed?[/COLOR]

No it wasn't, i tried installing fglrx and after following directions on a Ubuntu how to page tried fglrx fglrx-amdcccle both resulting in the ubuntu loading screen popping up after boot (never did before) but immediately skipping that and not loading the 3.5.0.-27 Kernel at all. So i used those commands you previously told me about to uninstall those and am now back to the fglrx errors problem.

---

### Post by chili555 on 2013-04-13
> **Trublet said:**
>  So i used those commands you previously told me about to uninstall those and am now back to the fglrx errors problem.Ouch! I suggest you ask over on General Help and get that fixed first. Once that's done, we can re-address the later kernel version.

---

### Post by Trublet on 2013-04-13
What was the 13.04 option would that fix everything?

---

### Post by chili555 on 2013-04-13
> **Trublet said:**
> What was the 13.04 option would that fix everything?I believe so!> $ modinfo [COLOR="#FF0000"]alx[/COLOR]
filename:       /lib/modules/[COLOR="#FF0000"]3.8.0-17-generic[/COLOR]/kernel/ubuntu/alx/alx.ko
version:        1.2.3
license:        Dual BSD/GPL
description:    Qualcomm Atheros Gigabit Ethernet Driver
author:         Qualcomm Corporation, <nic-devel@qualcomm.com>
srcversion:     DEB551A4F9D0281F98F5F10
alias:          pci:v00001969d000010A0sv*sd*bc*sc*i*
alias:          pci:v00001969d000010A1sv*sd*bc*sc*i*
alias:          pci:v00001969d00001090sv*sd*bc*sc*i*
alias:          pci:v0000[COLOR="#FF0000"]1969[/COLOR]d0000[COLOR="#FF0000"]1091[/COLOR]sv*sd*bc*sc*i*
depends:        mdio
intree:         Y
vermagic:       3.8.0-17-generic SMP mod_unload modversions 
I'm running the current beta and, at least for me, it's perfect.  [http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)

---

