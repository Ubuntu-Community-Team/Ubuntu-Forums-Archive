---
title: "Can´t find any wireless connection"
date: 2009-10-12
forum: Networking &amp; Wireless
---

### Post by D4rkV3n0M on 2009-10-12
_[SIZE=5]**Hi everyone**[/SIZE]_
I installed Ubuntu 8.10 at my EEE PC 900 and when the installation was completed and i logged in I couldn´t connect to the internet, only if I plugged a internet cable to my pc. 
Is it any step that I have forgot??

Thx for any answers :P

---

### Post by shredder12 on 2009-10-12
If you are trying to connect to a wireless network and if you wireless switch is on.. then ubuntu should automatically detect the networks...
left click on the network manager icon (a computer or a bar graph icon) on the right top corner on the screen.
This will show you the wireless networks. click on the one you want to connect.

---

### Post by D4rkV3n0M on 2009-10-12
There isn´t any connections in the list it´s empty

---

### Post by shredder12 on 2009-10-12
Go to System->Administration->hardware drivers
and see if the wireless driver is enabled..

Plz.. check if your wireless switch is on( i know it sounds insane but anyone can make such a mistake)
I think it should be a driver issue..

---

### Post by D4rkV3n0M on 2009-10-12
It says "Support for Atheros 802.11 wireless LAN cards" and a there is a green light. A little bit below there is another green light there it says "the driver is activated and currently in use"

---

### Post by jward3010 on 2009-10-12
I'm gonna repeat something similar to shredder12 and ask is there any Fn key that you need to press as well with an F1 - F12 key to switch on the wireless, sometimes there are two places to enable it.

After that, go to a terminal and type the following and paste what you get:
```
sudo lshw -C nework
```
```
sudo iwconfig scan
```

---

### Post by D4rkV3n0M on 2009-10-12
it says "scan   no such device" but the little blue light is glowing and there is a wireless symbol above it so i guess its turned on

---

### Post by shredder12 on 2009-10-12
I think jward3010 either meant just
```
sudo iwconfig
```
or
```
sudo iwlist scanning
```
the 2nd one will show you the list of scanned networks

---

### Post by D4rkV3n0M on 2009-10-12
the wireless connection isn´t in the list, but i tryed in school  and it didn´t find that one either, before the problem started I was able to connect to both the one at home and in scool

---

### Post by jward3010 on 2009-10-12
Thank YOU shredder, I did indeed - it's been a long day.

---

### Post by shredder12 on 2009-10-12
> **D4rkV3n0M said:**
> _[SIZE=5]**Hi everyone**[/SIZE]_
I installed Ubuntu 8.10 at my EEE PC 900 and when the installation was completed and i logged in I couldn´t connect to the internet, only if I plugged a internet cable to my pc. 


You said that you haven't been able to connect since the installation. So, I guess you were able to access wireless before installation on some previous version..

If it worked on a pervious version of ubuntu then it should work in the later versions too. Btw, paste the output of 
```
sudo iwconfig
```
and
```
lspci
```

---

### Post by jward3010 on 2009-10-12
> **D4rkV3n0M said:**
> it says "scan   no such device" but the little blue light is glowing and there is a wireless symbol above it so i guess its turned on

This doesn't mean that the OS is recognising it. Could you paste exactly what you got from the terminal.

> **D4rkV3n0M said:**
> the wireless connection isn´t in the list, but i tryed in school  and it didn´t find that one either, before the problem started I was able to connect to both the one at home and in scool

Did it work in the past one the same Ubuntu?

---

### Post by D4rkV3n0M on 2009-10-12
when i write "sudo iwconfig" I get the following text :


00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 04)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 04)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 04)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 04)
00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 04)
00:1c.2 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 3 (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 04)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 04)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 04)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 04)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d4)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 04)
00:1f.2 IDE interface: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 04)
01:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
03:00.0 Ethernet controller: Attansic Technology Corp. L2 100 Mbit Ethernet Adapter (rev a0)

---

### Post by PrePenguin on 2009-10-12
Disable the lan in bios and then see if the wireless works since no driver issue there is sometimes a IRQ conflict with ubuntu due to sharing a resource. If that dont work just change it back in the bios no harm no foul just a few minutes of time and 1 more thing to checkoff. Also notice its showing youre wireless card plain as day another reason I suspect this..

---

### Post by D4rkV3n0M on 2009-10-12
Tryed to disable lan in bios but still no Internet :(

---

### Post by PrePenguin on 2009-10-12
Ok have you tried to install ubuntu-resctricted-extras?

---

### Post by D4rkV3n0M on 2009-10-12
how to install it is it any code i can write in terminal??

---

### Post by PrePenguin on 2009-10-12
> **D4rkV3n0M said:**
> how to install it is it any code i can write in terminal??
 
 
 
sudo apt-get install ubuntu-restricted-extras

---

### Post by jward3010 on 2009-10-13
> Ok have you tried to install ubuntu-resctricted-extras?
The "ubuntu-restricted-extras" package has nothing to do with getting a wireless connection!

---

### Post by jward3010 on 2009-10-13
> **D4rkV3n0M said:**
> when i write "sudo iwconfig" I get the following text :


00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 04)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 04)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 04)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 04)
00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 04)
00:1c.2 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 3 (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 04)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 04)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 04)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 04)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d4)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 04)
00:1f.2 IDE interface: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 04)
01:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
03:00.0 Ethernet controller: Attansic Technology Corp. L2 100 Mbit Ethernet Adapter (rev a0)

I think you mean the "lspci" command produces the above. If you wouldn't mind posting both of my suggested commands in the one post and to make it even easier to read put them in "code" tags, like this:

{code}Information output{/code} but change the curly brackets to square brackets.

---

### Post by D4rkV3n0M on 2009-10-13
I have installed it but still no internet:(

---

### Post by shredder12 on 2009-10-13
were you ever able to run wireless after installation or on a previous version of Ubuntu ??

---

### Post by jward3010 on 2009-10-13
> **D4rkV3n0M said:**
> I have installed it but still no internet:(
If you're referring to installing "ubuntu-restricted-extras", you're wasting your time. It's similar to installing Word on your PC thinking your car might start afterwards. There not related AT ALL.

I feel your not reading the posts we're putting in, I hope your not getting overly frustrated. If you give us the output of 
```
sudo iwlist scan
```
and
```
sudo iwconfig
```
...we can help.

---

### Post by cvan84 on 2009-10-13
I'm having the exact same problem. I just installed Ubuntu last night. Where do I go to type in that code to receive an output? 
Thanks

edit: found the terminal. 
I typed in the sudo lshw -C network and got this:
*network
description: Network Controller
poduct: BCM4328 802.11a/b/g/n
vendor:Broadcom Corporation
physical id: 0
bus info: pci@0000:03:00.0
version: 03
width 64 bits
clock: 33MHz
capabilities: pm msi pciexpress bus_master cap list
Config: driver=b43-pci-bridge latency=0 module=ssb

*network DISABLED
description: Ethernet interface
physical id: 1
logical name pan0
serial: 0e:97:c2:ad:3d:cd
capabilities: ethernet physical
configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes


The other thing:

sudo iwconfig scan
scan  No such device


The Network Manager (the 4 bars at the top right) has a red x on the icon. when I right click, Enable Networking is checked. My wireless button on my keyboard is also ON. 

When I goto Hardware Drivers, Broadcom STA wireless driver is Enabled. It also says this driver is activated but not currently in use

I have tried restarting the computer, also. 

Any help would be much appreciated. Thanks

---

### Post by D4rkV3n0M on 2009-10-13
> **shredder12 said:**
> were you ever able to run wireless after installation or on a previous version of Ubuntu ??


I had no problems at all with wireless until I started to upgrade to 9.04 or whatever, but I cancelled it in the middle of the update and rebootet and started to install the older version once again. From that moment I haven´t  got any wireless connections.

---

### Post by D4rkV3n0M on 2009-10-16
When i try type in "sudo iwlist scan" then the following text appears

```
root@lill-pluttin:~# sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

pan0      Interface doesn't support scanning.
```


then i type in "sudo iwconfig" then the following text appears

```
root@lill-pluttin:~# sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

root@lill-pluttin:~# 

```

---

### Post by shredder12 on 2009-10-18
Lets see... your system->administration->hardware drivers shows that the wireless driver is installed and activaed but still you don't see a wireless interface..

I don't know the exact method of solving this problem but i guess somehow adding an interaface and configuring it to support wireless communication should do the job..

Lets see what others have to say.. may be they can suggest some solution..

---

### Post by jward3010 on 2009-10-18
If you say that Ubuntu updated at some stage, didn't finish, reverted to old versions then if you even have an ethernet connection try a:
```
sudo apt-get install -f
```
This will try and fix broken upgrades.

```
sudo dpkg --configure -a
```
This will do something similar.

```
sudo apt-get update && sudo apt-get dist-upgrade
```
This will update your repositories and then do a distribution upgrade, which will get packages which are due for later upgrading, maybe you're behind on some updates.

---

### Post by D4rkV3n0M on 2009-11-12
I installed the latest version (9,10) and then when the installation was completed it picked up wireless signals so now i can use wireless again :D


thanks for all your help guys :KS

---

