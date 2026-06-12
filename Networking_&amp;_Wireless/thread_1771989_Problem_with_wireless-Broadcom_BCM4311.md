---
title: "Problem with wireless-Broadcom BCM4311"
date: 2011-05-31
forum: Networking &amp; Wireless
---

### Post by dwilley on 2011-05-31
I'm new to Ubuntu and still getting used to the program. I've recently installed it on a Compaq Presario V6000. I got the wired ethernet port to work but the wireless won't show any wireless networks. I have already tried a few things and have mentioned them on pages 3 and 4 of [this thread]("http://ubuntuforums.org/showthread.php?t=1748677&page=3").

here is what i have in the terminal as we speak of things i have tried:

user@user-Presario-V6000-RG390UA-ABA:~$ rfkill list all
0: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
user@user-Presario-V6000-RG390UA-ABA:~$ grep|iw|
> sudo modprobe iw|3945
Usage: grep [OPTION]... PATTERN [FILE]...
Try `grep --help' for more information.
[sudo] password for user: The program 'iw' is currently not installed.  You can install it by typing:
sudo apt-get install iw
3945: command not found


[1]+  Stopped                 grep --color=auto | iw | sudo modprobe iw | 3945
user@user-Presario-V6000-RG390UA-ABA:~$ udo
The program 'udo' is currently not installed.  You can install it by typing:
sudo apt-get install udo
user@user-Presario-V6000-RG390UA-ABA:~$ sudo apt-get install iw
[sudo] password for user: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package iw
user@user-Presario-V6000-RG390UA-ABA:~$ dmesg | grep iwl
user@user-Presario-V6000-RG390UA-ABA:~$ sudo apt-get install udo
[sudo] password for user: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package udo
user@user-Presario-V6000-RG390UA-ABA:~$ sudo apt-get install iw
[sudo] password for user: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package iw
user@user-Presario-V6000-RG390UA-ABA:~$ sudo modprobe iw13945
FATAL: Module iw13945 not found.
user@user-Presario-V6000-RG390UA-ABA:~$ sudo modprobe iwl3945

and this is what i'm working with:
user@user-Presario-V6000-RG390UA-ABA:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Mobile 945GM/PM/GMS,  943/940GML and 945GT Express Memory Controller Hub [8086:27a0] (rev 03)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile  945GM/GMS, 943/940GML Express Integrated Graphics Controller [8086:27a2]  (rev 03)
00:02.1 Display controller [0380]: Intel Corporation Mobile  945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller  [8086:27a6] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation N10/ICH 7 Family High Definition Audio Controller [8086:27d8] (rev 02)
00:1c.0 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 1 [8086:27d0] (rev 02)
00:1c.1 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 2 [8086:27d2] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 [8086:27c8] (rev 02)
00:1d.1 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 [8086:27c9] (rev 02)
00:1d.2 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 [8086:27ca] (rev 02)
00:1d.3 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 [8086:27cb] (rev 02)
00:1d.7 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller [8086:27cc] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev e2)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge [8086:27b9] (rev 02)
00:1f.1 IDE interface [0101]: Intel Corporation 82801G (ICH7 Family) IDE Controller [8086:27df] (rev 02)
00:1f.2 SATA controller [0106]: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller [8086:27c5] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation N10/ICH 7 Family SMBus Controller [8086:27da] (rev 02)
02:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
05:08.0 Ethernet controller [0200]: Intel Corporation PRO/100 VE Network Connection [8086:1092] (rev 02)

and i've already tried this---->[http://ubuntuforums.org/showthread.php?t=1604868](http://ubuntuforums.org/showthread.php?t=1604868)
and got errors when i tried to install the package.

any help is appreciated. thank you.

---

### Post by walt.smith1960 on 2011-05-31
Hi

Your wireless chip is Broadcom.  The module iwl3945 is to drive an Intel wireless adapter.  Does anything Broadcom related show up when you go System -> Administration -> Additional Drivers? If yes, try activating it.  If no, can you temporarily plug into a wired network?  If so, plug in and run System -> Administration -> Update Manager, install any updates then check additional drivers again. That may find and install your required Broadcom software.  If this doesn't work, I would search in the networking & wireless forum using the search criteria BCM4311.  You may find what you need there. I'm no expert when it comes to Broadcom but I think you should be able to get up and running without building your own drivers.  There are several Broadcom packages about.  The trick is to pick the right one.

---

### Post by dFlyer on 2011-05-31
This may or may not work for you. It works for me. Start synaptic. Enter bcm in quick filter. If bcmwl-kernel-source is installed right click on it and mark for reinstallation. To do this you will need to be hardwired to the network. Apply changes and reboot. Hopefully it works for you to.

---

### Post by chili555 on 2011-05-31
> Broadcom Corporation BCM4311 802.11b/g WLAN [[COLOR="Red"]14e4:4311[/COLOR]] (rev 01)You need the firmware for the driver combination b43 and ssb:```
$ modinfo ssb | grep 4311
alias:          pci:v000014E4d0000[COLOR="Red"]4311[/COLOR]sv*sd*bc*sc*i*
```This Broadcom card requires proprietary firmware. Since it's proprietary, it is not included on the GPL licensed install CD. It is, however, perfectly acceptable for you to download and install it yourself. There is a handy little program that goes out on the internet, finds the correct firmware and installs it in the right place. Please connect a temporary ethernet connection and open a terminal and do:```
sudo apt-get install b43-fwcutter
```After it is downloaded and installed it will go to work getting the firmware and installing it. After a reboot, you should be all set.

Post back if you get stuck or if any part of the process doesn't go as expected. Be careful with each command.

---

### Post by dwilley on 2011-05-31
i'll try it when i get home as i'm at work and they have all the ethernet ports shut off except the ones that are being used. last night i think i tried to install b43-fwcutter along with firmware-b43-lpphy-installer but it popped up with an error so i just backed out of the whole thing and decided to try it later. i did that with synaptic. i will try what you suggested tonight through the terminal when i'm able to get a wired connection and hopefully things will go better.

---

### Post by chili555 on 2011-05-31
Post back and let me know if you get stuck.

---

### Post by faraz.yashar on 2011-05-31
I've also had a ton of problems getting the card to work with 11.04 on a Dell Inspiron 6400.  I have a working ethernet connection, so anything needing the net shouldn't be a problem.
After the computer started up after the Ubu install, the Broadcom STA wireless driver was installed as recommended through the Additional Drivers dialogue.

```

$ lspci | grep WLAN
0b:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)
$ modinfo ssb | grep 4311
alias:          pci:v000014E4d00004311sv*sd*bc*sc*i*

```> This package contains Broadcom 802.11 Linux STA wireless driverfor [sic] use with Broadcom's BCM4311-, BCM4312-, BCM4313-, BCM4321-,BCM4322-, BCM43224-, and BCM43225-, BCM43227- and BCM43228-basedhardware.No wireless device was recognized by ifconfig or iwconfig. after a restart.

Using the toggle key combination (Fn+F2) switches blocking from no to yes:
/```

$ rfkill list
0: dell-wifi: Wireless LAN
    Soft blocked: no/yes
    Hard blocked: no/yes

```
bcmwl-kernel-source has been reinstalled as well.

After installing b43-fwcutter and firmware-b43-installer, and removing the STA driver the solution isn't entirely resolved either although it looks like more progress has been made.

iwconfig now has a wlan0:
```

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

```

The network button on the top menu bar now shows a section entitled  "Wireless Networks" with a notice below that states "wireless is  disabled by hardware switch."

The next logical move would be to check rfkill while toggling with Fn+F2:
```

$ rfkill list
0: dell-wifi: Wireless LAN
    Soft blocked: yes
    Hard blocked: no/yes
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

```

Note that soft blocked is now fixed at yes for dell-wifi , and a new phy0 has appeared.  The notice about "wireless is disabled by hardware switch" remains fixed despite the keyboard toggle.

Note that Fn+[Key]  works for other keys (e.g. brightness, battery life, volume.) rfkill seems responsive to the wifi toggle as well.

Cheers and thanks!

---

### Post by chili555 on 2011-05-31
@faraz.yashar--

Please start a new thread. Since I am about 209 years old, I have a bit of trouble jumping back and forth diagnosing two or more posters in one thread. When you post, include:```
lspci -nn | grep -i 14e4
lsmod | grep dell
```I'll jump right in.

Thanks.

---

### Post by tomcripps on 2011-05-31
Hi, 

I have similar problems to those listed below. Just wont recognise the wireless card. Help please.

Tom

Here's what I can see...

toms@toms-laptop:~$ rfkill list
0: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
toms@toms-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

toms@toms-laptop:~$ lspci -nn | grep -i 14e4
03:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)

---

### Post by chili555 on 2011-05-31
> **tomcripps said:**
> Hi, 

I have similar problems to those listed below. Just wont recognise the wireless card. Help please.

Tom

Here's what I can see...

toms@toms-laptop:~$ rfkill list
0: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
toms@toms-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

toms@toms-laptop:~$ lspci -nn | grep -i 14e4
03:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)Please see post #4 above. The card is the same and the answer is the same.

---

### Post by dwilley on 2011-06-01
> **chili555 said:**
> Post back and let me know if you get stuck.

tried the code in the terminal with ethernet plugged in and got this:
user@user-Presario-V6000-RG390UA-ABA:~$ sudo apt-get install b43-fwcutter
[sudo] password for user: 
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

---

### Post by chili555 on 2011-06-01
> E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?That usually means that Synaptic, Software Center or Update Manager is running but unused and probably minimized on your desktop. Just it close out and try again.

---

### Post by charlesorchard on 2011-06-01
This is a bugger.  I've been through several threads on this one and can't get a wireless connection.

Like others I've got Compaq Presario V6000:

user@user-Presario-V6000-EZ603UA-ABA:/$ lspci -nn | grep -i 14e4

> 
03:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
user@user-Presario-V6000-EZ603UA-ABA:/$ iwconfig
> 
lo        no wireless extensions.
eth0      no wireless extensions.
user@user-Presario-V6000-EZ603UA-ABA:/$ rfkill list
> 
0: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
It seems like I've tried every combination in the symantic package manger and nothing has produced any results. It currently looks like the image in the attachment.


and the blacklist.conf in /etc/modprobe.d has

# replaced by b43 and ssb.
# blacklist bcm43xx


Help please!

---

### Post by chili555 on 2011-06-01
It wouldn't be a good day unless I had a startling revelation. Your device is claimed by two drivers!```
chili@LAPTOP60:~$ modinfo ssb | grep 4311
alias:          pci:v000014E4d0000[COLOR="Red"]4311[/COLOR]sv*sd*bc*sc*i*
chili@LAPTOP60:~$ modinfo wl | grep 4311
alias:          pci:v000014E4d0000[COLOR="Red"]4311[/COLOR]sv*sd*bc*sc*i*
```Most Broadcom devices use either b43 and ssb *OR* wl. _Both_ evidently claim your device. Let's try wl first. Get an ethernet connection and do:```
sudo su
apt-get install bcmwl-kernel-source
echo "blacklist b43" >> /etc/modprobe.d/blacklist.conf
exit
```Reboot and tell us how it's working.

If you have a Broadcom ethernet card that uses b44 and ssb; then ssb may drag b43 back in even though it's blacklisted. Please run:```
lspci -nn
```Do you have a Broadcom ethernet card? If so, run:```
lsmod | grep b4
```Did b43 load and conflict anyway?

---

### Post by charlesorchard on 2011-06-01
At least it created the wl.ko file this time.  The laptop hung upon reboot.

lspci -nn    gives 

```

00:00.0 RAM memory [0500]: nVidia Corporation C51 Host Bridge [10de:02f0] (rev a2)
00:00.1 RAM memory [0500]: nVidia Corporation C51 Memory Controller 0 [10de:02fa] (rev a2)
00:00.2 RAM memory [0500]: nVidia Corporation C51 Memory Controller 1 [10de:02fe] (rev a2)
00:00.3 RAM memory [0500]: nVidia Corporation C51 Memory Controller 5 [10de:02f8] (rev a2)
00:00.4 RAM memory [0500]: nVidia Corporation C51 Memory Controller 4 [10de:02f9] (rev a2)
00:00.5 RAM memory [0500]: nVidia Corporation C51 Host Bridge [10de:02ff] (rev a2)
00:00.6 RAM memory [0500]: nVidia Corporation C51 Memory Controller 3 [10de:027f] (rev a2)
00:00.7 RAM memory [0500]: nVidia Corporation C51 Memory Controller 2 [10de:027e] (rev a2)
00:02.0 PCI bridge [0604]: nVidia Corporation C51 PCI Express Bridge [10de:02fc] (rev a1)
00:03.0 PCI bridge [0604]: nVidia Corporation C51 PCI Express Bridge [10de:02fd] (rev a1)
00:05.0 VGA compatible controller [0300]: nVidia Corporation C51 [Geforce Go 6150] [10de:0244] (rev a2)
00:09.0 RAM memory [0500]: nVidia Corporation MCP51 Host Bridge [10de:0270] (rev a2)
00:0a.0 ISA bridge [0601]: nVidia Corporation MCP51 LPC Bridge [10de:0260] (rev a3)
00:0a.1 SMBus [0c05]: nVidia Corporation MCP51 SMBus [10de:0264] (rev a3)
00:0a.3 Co-processor [0b40]: nVidia Corporation MCP51 PMU [10de:0271] (rev a3)
00:0b.0 USB Controller [0c03]: nVidia Corporation MCP51 USB Controller [10de:026d] (rev a3)
00:0b.1 USB Controller [0c03]: nVidia Corporation MCP51 USB Controller [10de:026e] (rev a3)
00:0d.0 IDE interface [0101]: nVidia Corporation MCP51 IDE [10de:0265] (rev f1)
00:0e.0 IDE interface [0101]: nVidia Corporation MCP51 Serial ATA Controller [10de:0266] (rev f1)
00:10.0 PCI bridge [0604]: nVidia Corporation MCP51 PCI Bridge [10de:026f] (rev a2)
00:10.1 Audio device [0403]: nVidia Corporation MCP51 High Definition Audio [10de:026c] (rev a2)
00:14.0 Bridge [0680]: nVidia Corporation MCP51 Ethernet Controller [10de:0269] (rev a3)
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
03:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
07:05.0 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 IEEE 1394 Controller [1180:0832]
07:05.1 SD Host controller [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 19)
07:05.2 System peripheral [0880]: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter [1180:0592] (rev 0a)
07:05.3 System peripheral [0880]: Ricoh Co Ltd xD-Picture Card Controller [1180:0852] (rev 05)

```lsmod | grep b4 gives nothing

---

### Post by chili555 on 2011-06-01
Well, we're getting somewhere; maybe not where we want to be, but...somewhere. Can you get it to boot any way at all, even in recovery mode? I think we need to blacklist ssb. Your ethernet card is not a Broadcom.```
sudo su
echo "blacklist ssb" >> /etc/modprobe.d/blacklist.conf
exit
```Now does it reboot and does the wireless work?

---

### Post by charlesorchard on 2011-06-01
rebooted fine 
lspci -nn    gives 

```

00:00.0 RAM memory [0500]: nVidia Corporation C51 Host Bridge [10de:02f0] (rev a2)
00:00.1 RAM memory [0500]: nVidia Corporation C51 Memory Controller 0 [10de:02fa] (rev a2)
00:00.2 RAM memory [0500]: nVidia Corporation C51 Memory Controller 1 [10de:02fe] (rev a2)
00:00.3 RAM memory [0500]: nVidia Corporation C51 Memory Controller 5 [10de:02f8] (rev a2)
00:00.4 RAM memory [0500]: nVidia Corporation C51 Memory Controller 4 [10de:02f9] (rev a2)
00:00.5 RAM memory [0500]: nVidia Corporation C51 Host Bridge [10de:02ff] (rev a2)
00:00.6 RAM memory [0500]: nVidia Corporation C51 Memory Controller 3 [10de:027f] (rev a2)
00:00.7 RAM memory [0500]: nVidia Corporation C51 Memory Controller 2 [10de:027e] (rev a2)
00:02.0 PCI bridge [0604]: nVidia Corporation C51 PCI Express Bridge [10de:02fc] (rev a1)
00:03.0 PCI bridge [0604]: nVidia Corporation C51 PCI Express Bridge [10de:02fd] (rev a1)
00:05.0 VGA compatible controller [0300]: nVidia Corporation C51 [Geforce Go 6150] [10de:0244] (rev a2)
00:09.0 RAM memory [0500]: nVidia Corporation MCP51 Host Bridge [10de:0270] (rev a2)
00:0a.0 ISA bridge [0601]: nVidia Corporation MCP51 LPC Bridge [10de:0260] (rev a3)
00:0a.1 SMBus [0c05]: nVidia Corporation MCP51 SMBus [10de:0264] (rev a3)
00:0a.3 Co-processor [0b40]: nVidia Corporation MCP51 PMU [10de:0271] (rev a3)
00:0b.0 USB Controller [0c03]: nVidia Corporation MCP51 USB Controller [10de:026d] (rev a3)
00:0b.1 USB Controller [0c03]: nVidia Corporation MCP51 USB Controller [10de:026e] (rev a3)
00:0d.0 IDE interface [0101]: nVidia Corporation MCP51 IDE [10de:0265] (rev f1)
00:0e.0 IDE interface [0101]: nVidia Corporation MCP51 Serial ATA Controller [10de:0266] (rev f1)
00:10.0 PCI bridge [0604]: nVidia Corporation MCP51 PCI Bridge [10de:026f] (rev a2)
00:10.1 Audio device [0403]: nVidia Corporation MCP51 High Definition Audio [10de:026c] (rev a2)
00:14.0 Bridge [0680]: nVidia Corporation MCP51 Ethernet Controller [10de:0269] (rev a3)
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
03:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
07:05.0 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 IEEE 1394 Controller [1180:0832]
07:05.1 SD Host controller [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 19)
07:05.2 System peripheral [0880]: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter [1180:0592] (rev 0a)
07:05.3 System peripheral [0880]: Ricoh Co Ltd xD-Picture Card Controller [1180:0852] (rev 05)

```lsmod | grep b4 again gives nothing

---

### Post by chili555 on 2011-06-01
Alrighty, now hook up the ethernet cable and open a terminal and do:```
sudo apt-get install bcmwl-kernel-source
```When it's done, do:```
sudo modprobe wl
```Is your wireless working?

---

### Post by dwilley on 2011-06-02
tried what you said after closing synaptic and came up with this:

user@user-Presario-V6000-RG390UA-ABA:~$ sudo apt-get install b43-fwcutter
[sudo] password for user: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
b43-fwcutter is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 128 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up firmware-b43-lpphy-installer (4.174.64.19-5) ...
Not supported card here (PCI id 14e4:4311)!
Use proper b43 or b43legacy firmware.
Aborting.
dpkg: error processing firmware-b43-lpphy-installer (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 firmware-b43-lpphy-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)
user@user-Presario-V6000-RG390UA-ABA:~$ 

it looked like it was going to work this time until it came up with errors. wasn't sure if you were talking to me in the posts below that though.

---

### Post by chili555 on 2011-06-03
@dwilley--

Please run and post:```
sudo modprobe b43
dmesg | grep b43
```Thanks.

---

### Post by dwilley on 2011-06-05
```
user@user-Presario-V6000-RG390UA-ABA:~$ sudo modprobe b43
user@user-Presario-V6000-RG390UA-ABA:~$ dmesg | grep b43
[46383.472542] b43-pci-bridge 0000:02:00.0: setting latency timer to 64
[46383.627346] b43-phy0: Broadcom 4311 WLAN found (core revision 10)
[46383.845733] Registered led device: b43-phy0::tx
[46383.845762] Registered led device: b43-phy0::rx
[46383.845794] Registered led device: b43-phy0::radio
[46384.499814] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[46384.499820] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found
[46384.499824] b43-phy0 ERROR: You must go to http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware and download the correct firmware for this driver version. Please carefully read all instructions on this website.
```

---

### Post by dwilley on 2011-06-05
went the the site that it wanted me to go to and it let me install 

```
sudo apt-get install b43-fwcutter firmware-b43-installer
```

after installing i restarted it i still have nothing on the wireless.```

```

---

### Post by garvinrick4 on 2011-06-05
Open Synaptics and type in b43 in search and make sure you do not have more than
the 2 you need installed you can right click on and uninstall, hit apply arrow also.
Matter of fact you can also type in bcm just to make sure you only got the 2 broadcom
installations you need as in post 22. Have to reboot to take effect.

---

### Post by charlesorchard on 2011-06-25
> **garvinrick4 said:**
> Open Synaptics and type in b43 in search and make sure you do not have more than
the 2 you need installed you can right click on and uninstall, hit apply arrow also.
Matter of fact you can also type in bcm just to make sure you only got the 2 broadcom
installations you need as in post 22. Have to reboot to take effect.


I've been removing b43-fwcutter and firmware-b43-installer then re-installing from scratch and still no magic blue light. Nothing in iwconfig.

I've checked under the synaptic package manager under bcm and b43 and they are the only two packages installed.

Anyone else with insight?

---

### Post by chili555 on 2011-06-25
Please open a terminal and so:```
sudo modprobe b43
dmesg | grep b43
iwconfig
```The pipe symbol | is on the right side of my US keyboard on the same key with \. Thanks.

---

### Post by josephmills on 2011-06-25
> **chili555 said:**
> Please open a terminal and so:```
sudo modprobe b43
dmesg | grep b43
iwcinfig
```The pipe symbol | is on the right side of my US keyboard on the same key with \. Thanks.

i think that chilli means ```
iwconfig 
``` sorry post hungry

---

### Post by charlesorchard on 2011-06-27
> **chili555 said:**
> Please open a terminal and so:```
sudo modprobe b43
dmesg | grep b43
iwconfig
```The pipe symbol | is on the right side of my US keyboard on the same key with \. Thanks.


Monsier you are gentleman and genius (in spite of an occasional typo).

Little blue light is on and found my home network with no trouble at all.

Thank you.

---

### Post by bkratz on 2011-06-27
> **charlesorchard said:**
> Monsier you are gentleman and genius (in spite of an occasional typo).

Little blue light is on and found my home network with no trouble at all.

Thank you.

He certainly meets both criteria, but does it remain after a reboot? If not, post again.

---

### Post by nm_geo on 2011-06-27
> **bkratz said:**
> He certainly meets both criteria, but does it remain after a reboot? If not, post again.

I would nearly bet he will be back..

---

### Post by chili555 on 2011-06-27
> **nm_geo said:**
> I would nearly bet he will be back..+1

We have all seen a few b43s that need to be shotgunned into /etc/modules.

---

### Post by nm_geo on 2011-06-27
Yes Sir doctor.

I even did an experiment today to see if the new[FONT=Arial]er[/FONT] kernels had any help for the STA (wl) driver on my Natty install.  I just removed my working b43 and the firmware and tried an install of the STA (wl) driver.... heheh .. Well to make a long story longer I even added the other STA common and STA source just for flavor like spices.. Obviously, they did not make the the STA driver work :)..

So I motored over to /etc/modprobe.d to see exactly what those automatic blacklist files were..[SIZE=2]  blacklist-bcm43.conf and[/SIZE][FONT=monospace][FONT=Arial][SIZE=2]broadcom-sta-common.conf.  So I suited up my sudo and removed both.

Removed all that STA stuff and reloaded my b43-fwcutter and firmware-b43-installer.  Now my Natty works again ... I know I know.. dumb to expect anything else 

Pass me a cold one if you will..
[/SIZE][/FONT][SIZE=2]
[/SIZE]
[/FONT]

---

### Post by charlesorchard on 2011-06-27
> **nm_geo said:**
> I would nearly bet he will be back..

Of course I'll be back.  But hopefully now as an untethered and productive member of the community :)

So yes I had to add b43 to /etc/modules in order for the wireless fire up during start up.  

I'm not a  complete idiot, I just play one on TV. 

Thank you again.

---

### Post by nm_geo on 2011-06-27
> **charlesorchard said:**
> Of course I'll be back.  But hopefully now as an untethered and productive member of the community :)

So yes I had to add b43 to /etc/modules in order for the wireless fire up during start up.  

I'm not a  complete idiot, I just play one on TV. 

Thank you again.

You did well ... We are all glad..

---

### Post by josephmills on 2011-06-27
@ chilli555 & nm_geo 


[COLOR="Red"]W[/COLOR][COLOR="Magenta"]I[/COLOR][COLOR="SeaGreen"]N[/COLOR][COLOR="RoyalBlue"]N[/COLOR][COLOR="DarkSlateBlue"]E[/COLOR][COLOR="DarkOrange"]R[/COLOR]
[COLOR="Red"]W[/COLOR][COLOR="Magenta"]I[/COLOR][COLOR="SeaGreen"]N[/COLOR][COLOR="RoyalBlue"]N[/COLOR][COLOR="DarkSlateBlue"]E[/COLOR][COLOR="DarkOrange"]R[/COLOR]


Chicken Dinner 


@charlesorchard   Glad to see that you got it worked out !

---

### Post by chili555 on 2011-06-27
> So yes I had to add b43 to /etc/modules in order for the wireless fire up during start up.

I'm not a complete idiot, I just play one on TV. I don't think any of us thought that; I'm scratching my grey beard wondering why, seemingly all 'a sudden, b43 is a lazy module when it's supposed to load along with ssb which is supposed to load according to its aliases...er, alii..?? Most all other modules load obediently. Why is b43 lazy?

---

### Post by nm_geo on 2011-06-27
> **chili555 said:**
> I don't think any of us thought that; I'm scratching my grey beard wondering why, seemingly all 'a sudden, b43 is a lazy module when it's supposed to load along with ssb which is supposed to load according to its aliases...er, alii..?? Most all other modules load obediently. Why is b43 lazy?

From what i've seen new users try the STA driver and get the blacklist files created.  Then they try the b43 method and have all kinds of trouble.  The auto blacklists errr... suck

---

### Post by josephmills on 2011-06-28
> **chili555 said:**
> I don't think any of us thought that; I'm scratching my grey beard wondering why, seemingly all 'a sudden, b43 is a lazy module when it's supposed to load along with ssb which is supposed to load according to its aliases...er, alii..?? Most all other modules load obediently. Why is b43 lazy?

along with what nm_geo said I think that when they replaced the  bcmwl-modaliases  with the bcmwl-kernel-source boom. but I could be wrong all I know is I tell everyone to remove --purge the bcmwl-kernel-source then reboot and then install the b43 or wl or brcm80211 then put the bcmwl-kernel-source back after  but the mods  still needs to be moved to /ect/modules like 60% of the time ?????  soon enough I am going to have packages  for all of these and I am going to step into my time machine and  make everyone start compiling :D

---

