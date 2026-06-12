---
title: "No Wireless Controller on HP ProBook 6550b"
date: 2011-08-20
forum: Networking &amp; Wireless
---

### Post by NCMS on 2011-08-20
I am running **Windows 7  32-bit** on my  laptop  [COLOR=black]**HP ProBook 6550b**[/COLOR]   and installed in dual boot mode  **ubuntu 10.04.3**   
 
The wireless not started and I noticed that when I ran the **sudo lspci  **command, I don't Wireless controller, etc., but I believe it is listed as 
**Network controller: Broadcom Corporation Device 4727**
 
**[COLOR=red]NOTE:[/COLOR]**
on Windows 7  the Wireless adapter is working fine, and I have just noticed that it is **Broadcom 4313** 802.11b/g/n
 
 
**[COLOR=darkred]:confused:  ANY HELP IN MAKING THIS WORK IN UBUNTU  :confused:[/COLOR]**
 
 
***cat /etc/issue***
ubuntu 10.04.3 LTS
 
***uname -a***
Linux ncms-laptop 2.6.32-33-generic #70-Ubuntu SMP Thu Jul 7 21:09:46 UTC 2011 i686 GNU/Linux

***uname -r***
2.6.32-33-generic

***uname -m***
i686

***sudo lscpu***
Architecture:          
i686
CPU op-mode(s):        32-bit, 64-bit

 
***THE SUDO LSPCI OUTPUT***
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation Core Processor PCI Express x16 Root Port (rev 02)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:19.0 Ethernet controller: Intel Corporation 82577LC Gigabit Network Connection (rev 05)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 05)
00:1c.2 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 3 (rev 05)
00:1c.3 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 4 (rev 05)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 6 port SATA AHCI Controller (rev 05)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 05)
01:00.0 VGA compatible controller: ATI Technologies Inc M93 [Mobility Radeon HD 4500 Series]
01:00.1 Audio device: ATI Technologies Inc RV710/730
44:00.0 SD Host controller: Ricoh Co Ltd Device e822 (rev 01)
44:00.1 System peripheral: Ricoh Co Ltd Device e230 (rev 01)
44:00.2 System peripheral: Ricoh Co Ltd Device e852 (rev 01)
44:00.3 FireWire (IEEE 1394): Ricoh Co Ltd Device e832 (rev 01)
45:00.0 **Network controller: Broadcom Corporation Device 4727 **(rev 01)
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)
ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 02)
ff:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
ff:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
 
**THANKS**

---

### Post by chili555 on 2011-08-20
Please run:```
lspci -nn | grep 0280
```If the pci.id is 14e4:4727, please proceed. If not stop and post it and we'll decide how to proceed.

If you have a temporary wired ethernet connection, please run in a terminal:```
sudo apt-get install bcmwl-kernel-source
```After it installs, detach the ethernet cable and do:```
sudo modprobe wl
```Enjoy your new wireless!

---

### Post by NCMS on 2011-08-20
THANKS here is the output, and note 0 upgraded and 0 newly installed message and tried to install   bcmwl-kernel-source   
AND the problem still the same NO WIRELESS :(
 
[EMAIL="ncms@ncms-laptop:~$"]ncms@ncms-laptop:~$[/EMAIL] sudo lspci -nn | grep 0280
45:00.0 Network controller [0280]: Broadcom Corporation Device [14e4:4727] (rev 01)
 

[EMAIL="ncms@ncms-laptop:~$"]ncms@ncms-laptop:~$[/EMAIL] sudo apt-get install bcmwl-kernel-source
Reading package lists... Done
Building dependency tree       
Reading state information... Done
bcmwl-kernel-source is already the newest version.
**0 upgraded, 0 newly installed, 0 to remove and 8 not upgraded.**
 
 
[EMAIL="ncms@ncms-laptop:~$"]ncms@ncms-laptop:~$[/EMAIL] sudo modprobe wl

 
[COLOR=red]THANSK...[/COLOR]

---

### Post by chili555 on 2011-08-20
Let's look at a couple of other things:```
dmesg | grep wl
rfkill list all
```Thanks.

---

### Post by NCMS on 2011-08-20
**dmesg | grep wl**
[   23.101628] wl: module license 'MIXED/Proprietary' taints kernel.
[   23.108850] wl 0000:45:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[   23.108858] wl 0000:45:00.0: setting latency timer to 64
 
 
 **rfkill list all**
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

---

### Post by chili555 on 2011-08-20
> rfkill list all
0: hci0: Bluetooth
Soft blocked: no
Hard blocked: noThat's it?? No phy wireless listing?? Interesting.

Let's dig deeper:```
lsmod | grep wmi
dmesg | grep 45:00
```

---

### Post by NCMS on 2011-08-20
Here you go;
 
**lsmod | grep wmi**
snd_rawmidi 19056 1 snd_seq_midi
snd_seq_device 5700 5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd 54244 16
snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
&#12288;
**dmesg | grep 45:00**
[ 0.619178] pci 0000:45:00.0: reg 10 64bit mmio: [0xd0100000-0xd0103fff]
[ 0.619271] pci 0000:45:00.0: supports D1 D2
[ 23.108850] wl 0000:45:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[ 23.108858] wl 0000:45:00.0: setting latency timer to 64
&#12288;
******&#12288;
* just remembered earlier, I have ACTIVATED the **Broadcom STA wireless driver**  under **Hardware Drivers**  
I believe its a proprietary driver as stated on the menu and it is for Broadcoms's BCM4311-, BCM4312-, BCM4321-, AND  bcm4322- based hardware.
 
**I hope has not effect on what we are trying to solve.**
 
**[COLOR=red]THANK YOU[/COLOR]**

---

### Post by chili555 on 2011-08-20
> * just remembered earlier, I have ACTIVATED the Broadcom STA wireless driver under Hardware Drivers ^^^ Is exactly the same as:```
$ sudo apt-get install bcmwl-kernel-source
```That's why it said it was already installed. 

When you press the wireless switch or key combination, does anything happen? What happens in Windows? In Ubuntu, please do:```
sudo tail -f /var/log/syslog
```Manipulate the wireless switch or key combination and note any messages in the terminal. You can copy and paste from the terminal to a text document so you can post it here. Get out of syslog with Ctrl+c.

Also, try:```
sudo modprobe hp-wmi
rfkill list all
```Any change? Any interesting messages?

---

### Post by NCMS on 2011-08-20
[I][B][COLOR=SandyBrown]>> When you press the wireless switch or key combination,[/COLOR]
[/B][/I]
How can I do that exactly?!  sorry I didn't get it

---

### Post by chili555 on 2011-08-20
Please see attached. Don't you have that button (4)? Does the light go on and off when you press it? After you press it and run:```
rfkill list all
```Is there any change?

---

### Post by NCMS on 2011-08-20
Without doing so, it is working now .:confused:. 

Here what I did;
1. Switch off my laptop
2. went home
3. Switched ON my laptop
4. double click on the Wireless Signal indicator 
5. and  WALA  all the 3 access points at home are visible and my neighbors' as well :) 


**CHILI555,**  would you please tell me what saved my day and what step resolved this issue !!

---

### Post by chili555 on 2011-08-20
I wish I knew. Without analyzing the system logs extensively, it's hard to know. I'm just glad it's working. Have fun!

---

### Post by NCMS on 2011-08-20
Chili555,
   [SIZE=3][COLOR=Red]THANK YOU very much for your time and assistance[/COLOR][/SIZE]

Good Day

---

