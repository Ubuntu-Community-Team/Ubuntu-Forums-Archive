---
title: "Problems with madwifi-hal-0.10.5.6-r3875-20081105"
date: 2008-12-26
forum: Networking &amp; Wireless
---

### Post by Vendettaseve on 2008-12-26
Hey everyone

It was recommended by another user earlier that I get the Madwifi Hal thing it deal with the lack of wireless IM currecntly having, When I do an Iwconfig I get these results

vendettaseve@vendettaseve-laptop:~$ sudo iwconfig
[sudo] password for vendettaseve: 
lo        no wireless extensions.

eth0      no wireless extensions.

vendettaseve@vendettaseve-laptop:~$ 

Im not sure why it isnt even seeing my wireless card :(

I have gone through and done make, make install and modprobe ath_pci like it tells me to in the install instructions for Madwifi, it all reports as working properly when i do Make etc but it doesnt load any programs and it doesnt give me any wifi options anywhere. Can anyone give me a hand with this, its very frustrating.

Thank you.

---

### Post by Jakey_TheSnake on 2008-12-26
I get the same output from your command under those sections, too, yet my wireless works. 

After rebooting, click on the network connection icon on the main menu bar and you should see a list of wireless routers you can connect to, no?

---

### Post by Vendettaseve on 2008-12-26
No, I cant as previously stated. There are no wireless networks listed, it doesnt even mention anything about wireless, just gives me the option to configure my wired connection.

---

### Post by kevdog on 2008-12-26
Ok, so from what I can gather you manually compiled the madwifi driver from source (likely svn).  You compiled the module. Did you install the module (sudo make install), and then did you load the module (sudo modprobe ath_pci) and then make sure it loads everytime at boot by adding it to the /etc/modules file?

---

### Post by Vendettaseve on 2008-12-26
I have fully installed the Madwifi thing, does not seem to be functional. THis is the readout I get when I check my wifi thing.
vendettaseve@vendettaseve-laptop:~$ lshw -C Network
WARNING: you should run this program as super-user.
PCI (sysfs)  

  *-network               
       description: Ethernet interface
       product: RTL8101E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:1e:33:6b:8f:5d
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.2LK latency=0 module=r8169 multicast=yes
  *-network UNCLAIMED
       description: Network controller
       product: Atheros Communications Inc.
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:04:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0


Can someone direct me to some drivers that will accualy work -_- or tell me what it is thats going wrong here.

---

### Post by Vendettaseve on 2008-12-26
> **kevdog said:**
> Ok, so from what I can gather you manually compiled the madwifi driver from source (likely svn).  You compiled the module. Did you install the module (sudo make install), and then did you load the module (sudo modprobe ath_pci) and then make sure it loads everytime at boot by adding it to the /etc/modules file?

When I modprobe the ath_pci it doesnt do anything... or at least it doesnt appear to, gives me no feedback, just a fresh line on my terminal. Is that how its supposed to work?

Also, how would I go about adding it to etx/modules. thanks

---

### Post by kevdog on 2008-12-26
Ok, so it sounds like there may be a problem.

First lets just see if the madwifi driver is compiled properly

sudo updatedb
locate ath_pci

modinfo ath_pci

Then pop open two terminals.  You might need three.  You want to continuously monitor a couple of logs to see if there are errors produced when you use certain commands

In one terminal
tail -f /ver/log/dmesg

In other
tail -f /var/log/syslog

If you want to view any other log files -- they are all located in /var/log

In the next terminal

sudo modprobe ath_pci

Do any errors appear?

---

### Post by kevdog on 2008-12-26
See previous post.  A successful modprobe doesn't return any feedback except for information posted in the logs.

sudo lshw -C network

That will show you actually however if the driver has been "claimed" by the driver.

Also

lsmod | grep ath

That will actually show you if the module is loaded in the user space.

---

### Post by Vendettaseve on 2008-12-26
OK I typed in that stuff you asked. Im not sure what it all means, THe ones you asked me to type in to check for errors could not be found, file missing or some business like that.

Here are the results from your second post.

vendettaseve@vendettaseve-laptop:~$ sudo lshw -C network
[sudo] password for vendettaseve: 
  *-network               
       description: Ethernet interface
       product: RTL8101E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:1e:33:6b:8f:5d
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.2LK duplex=full ip=192.168.0.104 latency=0 link=yes module=r8169 multicast=yes port=twisted pair speed=100MB/s
  *-network UNCLAIMED
       description: Network controller
       product: Atheros Communications Inc.
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:04:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list
       configuration: latency=0
vendettaseve@vendettaseve-laptop:~$ lsmod | grep ath
ath_pci               100896  0 
wlan                  206960  1 ath_pci
ath_hal               192592  1 ath_pci

---

### Post by kevdog on 2008-12-26
Please post the following

lspci -nn
modinfo ath_pci

For some reason your driver is not claiming your card.

---

### Post by Vendettaseve on 2008-12-26
vendettaseve@vendettaseve-laptop:~$ lspci -nn
00:00.0 Host bridge [0600]: ATI Technologies Inc RS690 Host Bridge [1002:7910]
00:01.0 PCI bridge [0604]: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx) [1002:7912]
00:04.0 PCI bridge [0604]: ATI Technologies Inc Unknown device [1002:7914]
00:05.0 PCI bridge [0604]: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 1) [1002:7915]
00:06.0 PCI bridge [0604]: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 2) [1002:7916]
00:12.0 SATA controller [0106]: ATI Technologies Inc SB600 Non-Raid-5 SATA [1002:4380]
00:13.0 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI0) [1002:4387]
00:13.1 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI1) [1002:4388]
00:13.2 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI2) [1002:4389]
00:13.3 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI3) [1002:438a]
00:13.4 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI4) [1002:438b]
00:13.5 USB Controller [0c03]: ATI Technologies Inc SB600 USB Controller (EHCI) [1002:4386]
00:14.0 SMBus [0c05]: ATI Technologies Inc SBx00 SMBus Controller [1002:4385] (rev 14)
00:14.1 IDE interface [0101]: ATI Technologies Inc SB600 IDE [1002:438c]
00:14.2 Audio device [0403]: ATI Technologies Inc SBx00 Azalia [1002:4383]
00:14.3 ISA bridge [0601]: ATI Technologies Inc SB600 PCI to LPC Bridge [1002:438d]
00:14.4 PCI bridge [0604]: ATI Technologies Inc SBx00 PCI to PCI Bridge [1002:4384]
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
01:05.0 VGA compatible controller [0300]: ATI Technologies Inc RS690M [Radeon X1200 Series] [1002:791f]
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
04:00.0 Network controller [0280]: Atheros Communications Inc. Unknown device [168c:002a] (rev 01)
vendettaseve@vendettaseve-laptop:~$ 


vendettaseve@vendettaseve-laptop:~$ modinfo ath_pci
filename:       /lib/modules/2.6.24-22-generic/net/ath_pci.ko
license:        Dual BSD/GPL
version:        0.9.4
description:    Support for Atheros 802.11 wireless LAN cards.
author:         Errno Consulting, Sam Leffler
srcversion:     D3FD3BD11169A96DBCFF8DE
alias:          pci:v0000168Cd00009013sv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000001Dsv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000001Csv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000001Bsv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000001Asv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000019sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000018sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000017sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000016sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000015sv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000101Asv*sd*bc*sc*i*
alias:          pci:v0000168Cd00001014sv*sd*bc*sc*i*
alias:          pci:v000010B7d00000013sv*sd*bc*sc*i*
alias:          pci:v0000A727d00000013sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000013sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000012sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000007sv*sd*bc*sc*i*
depends:        ath_hal,wlan
vermagic:       2.6.24-22-generic SMP mod_unload 586 
parm:           countrycode:Override default country code (int)
parm:           maxvaps:Maximum VAPs (int)
parm:           outdoor:Enable/disable outdoor use (int)
parm:           xchanmode:Enable/disable extended channel mode (int)
parm:           rfkill:Enable/disable RFKILL capability (int)
parm:           autocreate:Create ath device in [sta|ap|wds|adhoc|ahdemo|monitor] mode. defaults to sta, use 'none' to disable (charp)
parm:           ratectl:Rate control algorithm [amrr|minstrel|onoe|sample], defaults to 'sample' (charp)
parm:           ath_debug:Load-time debug output enable (int)
vendettaseve@vendettaseve-laptop:~$

---

### Post by kevdog on 2008-12-26
Is this an HP machine and what version of Ubuntu are you running

Can you repost

lspci -nnm

---

### Post by Vendettaseve on 2008-12-26
Nope, this is a Toshiba Satellite L300D - 028 Pro

Here is the Data you requested.



vendettaseve@vendettaseve-laptop:~$ lspci -nnm
00:00.0 "Host bridge [0600]" "ATI Technologies Inc [1002]" "RS690 Host Bridge [7910]" "Toshiba America Info Systems [1179]" "Unknown device [ff68]"
00:01.0 "PCI bridge [0604]" "ATI Technologies Inc [1002]" "RS690 PCI to PCI Bridge (Internal gfx) [7912]" "" ""
00:04.0 "PCI bridge [0604]" "ATI Technologies Inc [1002]" "Unknown device [7914]" "" ""
00:05.0 "PCI bridge [0604]" "ATI Technologies Inc [1002]" "RS690 PCI to PCI Bridge (PCI Express Port 1) [7915]" "" ""
00:06.0 "PCI bridge [0604]" "ATI Technologies Inc [1002]" "RS690 PCI to PCI Bridge (PCI Express Port 2) [7916]" "" ""
00:12.0 "SATA controller [0106]" "ATI Technologies Inc [1002]" "SB600 Non-Raid-5 SATA [4380]" -p01 "Toshiba America Info Systems [1179]" "Unknown device [ff68]"
00:13.0 "USB Controller [0c03]" "ATI Technologies Inc [1002]" "SB600 USB (OHCI0) [4387]" -p10 "Toshiba America Info Systems [1179]" "Unknown device [ff68]"
00:13.1 "USB Controller [0c03]" "ATI Technologies Inc [1002]" "SB600 USB (OHCI1) [4388]" -p10 "Toshiba America Info Systems [1179]" "Unknown device [ff68]"
00:13.2 "USB Controller [0c03]" "ATI Technologies Inc [1002]" "SB600 USB (OHCI2) [4389]" -p10 "Toshiba America Info Systems [1179]" "Unknown device [ff68]"
00:13.3 "USB Controller [0c03]" "ATI Technologies Inc [1002]" "SB600 USB (OHCI3) [438a]" -p10 "Toshiba America Info Systems [1179]" "Unknown device [ff68]"
00:13.4 "USB Controller [0c03]" "ATI Technologies Inc [1002]" "SB600 USB (OHCI4) [438b]" -p10 "Toshiba America Info Systems [1179]" "Unknown device [ff68]"
00:13.5 "USB Controller [0c03]" "ATI Technologies Inc [1002]" "SB600 USB Controller (EHCI) [4386]" -p20 "Toshiba America Info Systems [1179]" "Unknown device [ff68]"
00:14.0 "SMBus [0c05]" "ATI Technologies Inc [1002]" "SBx00 SMBus Controller [4385]" -r14 "Toshiba America Info Systems [1179]" "Unknown device [ff68]"
00:14.1 "IDE interface [0101]" "ATI Technologies Inc [1002]" "SB600 IDE [438c]" -p8a "Toshiba America Info Systems [1179]" "Unknown device [ff68]"
00:14.2 "Audio device [0403]" "ATI Technologies Inc [1002]" "SBx00 Azalia [4383]" "Toshiba America Info Systems [1179]" "Unknown device [ff68]"
00:14.3 "ISA bridge [0601]" "ATI Technologies Inc [1002]" "SB600 PCI to LPC Bridge [438d]" "Toshiba America Info Systems [1179]" "Unknown device [ff68]"
00:14.4 "PCI bridge [0604]" "ATI Technologies Inc [1002]" "SBx00 PCI to PCI Bridge [4384]" -p01 "" ""
00:18.0 "Host bridge [0600]" "Advanced Micro Devices [AMD] [1022]" "K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1100]" "" ""
00:18.1 "Host bridge [0600]" "Advanced Micro Devices [AMD] [1022]" "K8 [Athlon64/Opteron] Address Map [1101]" "" ""
00:18.2 "Host bridge [0600]" "Advanced Micro Devices [AMD] [1022]" "K8 [Athlon64/Opteron] DRAM Controller [1102]" "" ""
00:18.3 "Host bridge [0600]" "Advanced Micro Devices [AMD] [1022]" "K8 [Athlon64/Opteron] Miscellaneous Control [1103]" "" ""
01:05.0 "VGA compatible controller [0300]" "ATI Technologies Inc [1002]" "RS690M [Radeon X1200 Series] [791f]" "Toshiba America Info Systems [1179]" "Unknown device [ff68]"
03:00.0 "Ethernet controller [0200]" "Realtek Semiconductor Co., Ltd. [10ec]" "RTL8101E PCI Express Fast Ethernet controller [8136]" -r02 "Toshiba America Info Systems [1179]" "Unknown device [ff68]"
04:00.0 "Network controller [0280]" "Atheros Communications Inc. [168c]" "Unknown device [002a]" -r01 "Askey Computer Corp. [144f]" "Unknown device [7141]"
vendettaseve@vendettaseve-laptop:~$

---

### Post by Vendettaseve on 2008-12-26
Nope, this is a Toshiba Satellite L300D - 028 Pro

Here is the Data you requested.



vendettaseve@vendettaseve-laptop:~$ lspci -nnm
00:00.0 "Host bridge [0600]" "ATI Technologies Inc [1002]" "RS690 Host Bridge [7910]" "Toshiba America Info Systems [1179]" "Unknown device [ff68]"
00:01.0 "PCI bridge [0604]" "ATI Technologies Inc [1002]" "RS690 PCI to PCI Bridge (Internal gfx) [7912]" "" ""
00:04.0 "PCI bridge [0604]" "ATI Technologies Inc [1002]" "Unknown device [7914]" "" ""
00:05.0 "PCI bridge [0604]" "ATI Technologies Inc [1002]" "RS690 PCI to PCI Bridge (PCI Express Port 1) [7915]" "" ""
00:06.0 "PCI bridge [0604]" "ATI Technologies Inc [1002]" "RS690 PCI to PCI Bridge (PCI Express Port 2) [7916]" "" ""
00:12.0 "SATA controller [0106]" "ATI Technologies Inc [1002]" "SB600 Non-Raid-5 SATA [4380]" -p01 "Toshiba America Info Systems [1179]" "Unknown device [ff68]"
00:13.0 "USB Controller [0c03]" "ATI Technologies Inc [1002]" "SB600 USB (OHCI0) [4387]" -p10 "Toshiba America Info Systems [1179]" "Unknown device [ff68]"
00:13.1 "USB Controller [0c03]" "ATI Technologies Inc [1002]" "SB600 USB (OHCI1) [4388]" -p10 "Toshiba America Info Systems [1179]" "Unknown device [ff68]"
00:13.2 "USB Controller [0c03]" "ATI Technologies Inc [1002]" "SB600 USB (OHCI2) [4389]" -p10 "Toshiba America Info Systems [1179]" "Unknown device [ff68]"
00:13.3 "USB Controller [0c03]" "ATI Technologies Inc [1002]" "SB600 USB (OHCI3) [438a]" -p10 "Toshiba America Info Systems [1179]" "Unknown device [ff68]"
00:13.4 "USB Controller [0c03]" "ATI Technologies Inc [1002]" "SB600 USB (OHCI4) [438b]" -p10 "Toshiba America Info Systems [1179]" "Unknown device [ff68]"
00:13.5 "USB Controller [0c03]" "ATI Technologies Inc [1002]" "SB600 USB Controller (EHCI) [4386]" -p20 "Toshiba America Info Systems [1179]" "Unknown device [ff68]"
00:14.0 "SMBus [0c05]" "ATI Technologies Inc [1002]" "SBx00 SMBus Controller [4385]" -r14 "Toshiba America Info Systems [1179]" "Unknown device [ff68]"
00:14.1 "IDE interface [0101]" "ATI Technologies Inc [1002]" "SB600 IDE [438c]" -p8a "Toshiba America Info Systems [1179]" "Unknown device [ff68]"
00:14.2 "Audio device [0403]" "ATI Technologies Inc [1002]" "SBx00 Azalia [4383]" "Toshiba America Info Systems [1179]" "Unknown device [ff68]"
00:14.3 "ISA bridge [0601]" "ATI Technologies Inc [1002]" "SB600 PCI to LPC Bridge [438d]" "Toshiba America Info Systems [1179]" "Unknown device [ff68]"
00:14.4 "PCI bridge [0604]" "ATI Technologies Inc [1002]" "SBx00 PCI to PCI Bridge [4384]" -p01 "" ""
00:18.0 "Host bridge [0600]" "Advanced Micro Devices [AMD] [1022]" "K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1100]" "" ""
00:18.1 "Host bridge [0600]" "Advanced Micro Devices [AMD] [1022]" "K8 [Athlon64/Opteron] Address Map [1101]" "" ""
00:18.2 "Host bridge [0600]" "Advanced Micro Devices [AMD] [1022]" "K8 [Athlon64/Opteron] DRAM Controller [1102]" "" ""
00:18.3 "Host bridge [0600]" "Advanced Micro Devices [AMD] [1022]" "K8 [Athlon64/Opteron] Miscellaneous Control [1103]" "" ""
01:05.0 "VGA compatible controller [0300]" "ATI Technologies Inc [1002]" "RS690M [Radeon X1200 Series] [791f]" "Toshiba America Info Systems [1179]" "Unknown device [ff68]"
03:00.0 "Ethernet controller [0200]" "Realtek Semiconductor Co., Ltd. [10ec]" "RTL8101E PCI Express Fast Ethernet controller [8136]" -r02 "Toshiba America Info Systems [1179]" "Unknown device [ff68]"
04:00.0 "Network controller [0280]" "Atheros Communications Inc. [168c]" "Unknown device [002a]" -r01 "Askey Computer Corp. [144f]" "Unknown device [7141]"
vendettaseve@vendettaseve-laptop:~$

---

### Post by kevdog on 2008-12-26
What version of Ubuntu (if it is Ubuntu) are you running and kernel version

uname -r

---

### Post by Vendettaseve on 2008-12-26
I believe Im running 8.10 Hardy. 

vendettaseve@vendettaseve-laptop:~$ uname -r
2.6.24-22-generic

---

### Post by kevdog on 2008-12-26
Your chipset is the following (Note for reference)
AR9281

Its really weird it didnt show up on the bus scan, however that is definitely your chipset

The driver solution you require is going to make use of the ath9k driver, and not specifically madwifi

I really need to now what version of ubuntu you are running or kernel version, since in more recent kernel (Ibex and beyond), this driver is built-into the kernel since its purely open source:
[http://linuxwireless.org/en/users/Drivers/ath9k](http://linuxwireless.org/en/users/Drivers/ath9k)

---

### Post by kevdog on 2008-12-26
Here is a post that will definitely help you out:

[http://ubuntuforums.org/showpost.php?p=5535562&postcount=3](http://ubuntuforums.org/showpost.php?p=5535562&postcount=3)

You are not running a custom kernel (ie you did not compile it yourself).  Hopefully this will work.

---

### Post by kevdog on 2008-12-26
Just to put my mind at ease -- let me know if you get it working.  Thanks.

---

### Post by Vendettaseve on 2008-12-26
Created and installed the package, did not seem to do anything, still no wireless functionality even after a couple restarts etc.

Is there something I need to configure?

---

### Post by kevdog on 2008-12-27
Ok can you post the following:

lshw -C network

lsmod | grep ath

---

### Post by Vendettaseve on 2008-12-27
vendettaseve@vendettaseve-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: RTL8101E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:1e:33:6b:8f:5d
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.2LK ip=192.168.0.104 latency=0 module=r8169 multicast=yes
  *-network UNCLAIMED
       description: Network controller
       product: Atheros Communications Inc.
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:04:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
vendettaseve@vendettaseve-laptop:~$ 


The second code does nothing, Simply produces another line in the Terminal for me to type on.

---

### Post by kevdog on 2008-12-27
Ok so post the following

modinfo ath9k

lsmod

---

### Post by Vendettaseve on 2008-12-27
vendettaseve@vendettaseve-laptop:~$ modinfo ath9k
filename:       /lib/modules/2.6.24-22-generic/kernel/drivers/net/wireless/ath9k/ath9k.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     A4910585605A4EEF935C41B
alias:          pci:v0000168Cd0000002Asv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000029sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000027sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000024sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000023sv*sd*bc*sc*i*
depends:        led-class,mac80211
vermagic:       2.6.24-22-generic SMP mod_unload 586 
vendettaseve@vendettaseve-laptop:~$ 



vendettaseve@vendettaseve-laptop:~$ lsmod
Module                  Size  Used by
ipv6                  267780  10 
af_packet              23812  2 
rfcomm                 41744  2 
l2cap                  25728  13 rfcomm
bluetooth              61156  4 rfcomm,l2cap
ppdev                  10372  0 
powernow_k8            16704  1 
cpufreq_stats           7104  0 
cpufreq_conservative     8712  0 
cpufreq_userspace       5284  0 
cpufreq_ondemand        9740  1 
freq_table              5536  3 powernow_k8,cpufreq_stats,cpufreq_ondemand
cpufreq_powersave       2688  0 
sbs                    15112  0 
dock                   11280  0 
sbshc                   7680  1 sbs
container               5632  0 
iptable_filter          3840  0 
ip_tables              14820  1 iptable_filter
x_tables               16132  1 ip_tables
parport_pc             36260  0 
lp                     12324  0 
parport                37832  3 ppdev,parport_pc,lp
joydev                 13120  0 
uvcvideo               58116  0 
compat_ioctl32          2304  1 uvcvideo
videodev               29440  1 uvcvideo
v4l1_compat            15492  2 uvcvideo,videodev
v4l2_common            18304  2 uvcvideo,videodev
snd_hda_intel         344856  4 
snd_hwdep              10500  1 snd_hda_intel
snd_pcm_oss            42144  0 
snd_pcm                78596  2 snd_hda_intel,snd_pcm_oss
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
psmouse                40336  0 
serio_raw               7940  0 
snd_mixer_oss          17920  2 snd_pcm_oss
fglrx                1555468  26 
ndiswrapper           192920  0 
snd_seq_dummy           4868  0 
snd_seq_oss            35584  0 
snd_seq_midi            9376  0 
video                  19856  0 
output                  4736  1 video
snd_rawmidi            25760  1 snd_seq_midi
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
battery                14212  0 
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24836  2 snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
button                  9232  0 
ac                      6916  0 
snd                    56996  17 snd_hda_intel,snd_hwdep,snd_pcm_oss,snd_pcm,snd_mixer_oss,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i2c_piix4               9612  0 
ati_agp                 9996  0 
evdev                  13056  7 
shpchp                 34452  0 
pci_hotplug            30880  1 shpchp
k8temp                  6656  0 
i2c_core               24832  1 i2c_piix4
soundcore               8800  2 snd
agpgart                34760  2 fglrx,ati_agp
pcspkr                  4224  0 
ext3                  136840  1 
jbd                    48404  1 ext3
mbcache                 9600  1 ext3
ide_cd                 32544  0 
cdrom                  37408  1 ide_cd
pata_acpi               8320  0 
ata_generic             8324  0 
pata_atiixp             8960  0 
usb_storage            73664  0 
libusual               19108  1 usb_storage
sg                     36880  0 
sd_mod                 30720  3 
atiixp                  5648  0 [permanent]
ide_core              113996  2 ide_cd,atiixp
ehci_hcd               37900  0 
ohci_hcd               26640  0 
usbcore               146412  7 uvcvideo,ndiswrapper,usb_storage,libusual,ehci_hcd,ohci_hcd
ahci                   28548  2 
libata                159344  4 pata_acpi,ata_generic,pata_atiixp,ahci
scsi_mod              151436  4 usb_storage,sg,sd_mod,libata
r8169                  33156  0 
thermal                16796  0 
processor              37384  2 powernow_k8,thermal
fan                     5636  0 
fbcon                  42912  0 
tileblit                3456  1 fbcon
font                    9472  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3072  1 bitblit
fuse                   50708  3 
vendettaseve@vendettaseve-laptop:~$

---

### Post by rixtr66 on 2008-12-27
Sorry my post didnt help!!but it seems you still have ndiswrapper installed?
in order for ath9k to work you have to remove the ndis driver.
regards
Rick

---

### Post by Vendettaseve on 2008-12-27
Ah that makes sence, How do I uninstall NDISwrapper?

THanks mate

---

### Post by kevdog on 2008-12-27
Just try this

sudo rmmod ndiswrapper
sudo modprobe ath9k

Then post the following
tail -20 dmesg

This should tell us if the modules were unsuccessfully loaded or unloaded.

---

### Post by Vendettaseve on 2008-12-27
vendettaseve@vendettaseve-laptop:~$ tail -20 dmesg
tail: cannot open `dmesg' for reading: No such file or directory
vendettaseve@vendettaseve-laptop:~$ 


Cant open the file, Also I get no feed back on the NDISWrapper thing, is it supposed to not say anything after you put it in?

---

### Post by kevdog on 2008-12-27
What happens when you just type dmesg?  This is the system log.  tail -20 is just a shortcut to posting the last 20 lines of the log since new stuff is always added at the end of the file.

If you have removed the ndiswrapper module nothing will result on the command line as far as feedback.  You either need to check the system log (dmesg) for verification of the action, or recheck lsmod (which is a short cut for list (ls) loaded modules (mod)) and make sure on this list that ndiswrapper is not loaded.

The same process could be done with the ath9k driver making sure it was loaded by checking the system log or checking lsmod.

Wait 
tail -20 /var/log/dmesg
That should work -- sorry about that -- have to give the entire path to the file

Within the /var/log directory are the various logs that are active in the system.

---

### Post by Vendettaseve on 2008-12-27
Modprobing the ath thing made it work :D

Now I just need to know how to get it  to do that on startup :D


vendettaseve@vendettaseve-laptop:~$ tail -20 /var/log/dmesg
[   44.469578] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   44.588051] [fglrx] Maximum main memory to use for locked dma buffers: 2770 MBytes.
[   44.588083] [fglrx] ASYNCIO init succeed!
[   44.588394] [fglrx] PAT is enabled successfully!
[   44.590348] [fglrx] module loaded - fglrx 8.47.3 [Feb 25 2008] on minor 0
[   44.831433] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[   44.902947] usbcore: registered new interface driver ndiswrapper
[   44.903021] Linux video capture interface: v2.00
[   44.981569] uvcvideo: Found UVC 1.00 device CNF7051 (04f2:b070)
[   44.997337] usbcore: registered new interface driver uvcvideo
[   44.997342] USB Video Class driver (v0.1.0)
[   45.028681] ACPI: PCI Interrupt 0000:00:14.2[A] -> GSI 16 (level, low) -> IRQ 17
[   45.064841] hda_codec: Unknown model for ALC268, trying auto-probe from BIOS...
[   45.652380] Synaptics Touchpad, model: 1, fw: 6.3, id: 0x9280b1, caps: 0xa04711/0xa04000
[   45.652387] synaptics: Toshiba Satellite L300D detected, limiting rate to 40pps.
[   45.729837] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input9
[   46.116270] lp: driver loaded but no devices found
[   46.210679] Adding 8739320k swap on /dev/sda5.  Priority:-1 extents:1 across:8739320k
[   46.751690] EXT3 FS on sda1, internal journal
[   47.776538] ip_tables: (C) 2000-2006 Netfilter Core Team
vendettaseve@vendettaseve-laptop:~$

---

### Post by kevdog on 2008-12-27
Ok Im glad things are working for you, but by the output you posted it would seem you are using ndiswrapper.

Can you do a couple of things for me and post the following:

lsmod
lshw -C network


Getting it to work on startup is easy by just removing and adding things to the /etc/modules file.  I need to confirm you really are using the ath9k driver however, then onto the next step.  Troubleshooting is a pain but it comes down to one philosophy.  Verify that every step you do, actually did what it was intended to do before moving onto the next step.

---

### Post by Vendettaseve on 2008-12-27
vendettaseve@vendettaseve-laptop:~$ lsmod
Module                  Size  Used by
arc4                    2944  2 
ecb                     4480  2 
blkcipher               8324  1 ecb
ath9k                 252088  0 
mac80211              229364  1 ath9k
cfg80211               36192  1 mac80211
led_class               6020  1 ath9k
af_packet              23812  2 
ipv6                  267780  10 
rfcomm                 41744  2 
l2cap                  25728  13 rfcomm
bluetooth              61156  4 rfcomm,l2cap
ppdev                  10372  0 
powernow_k8            16704  1 
cpufreq_stats           7104  0 
cpufreq_conservative     8712  0 
cpufreq_userspace       5284  0 
cpufreq_ondemand        9740  1 
freq_table              5536  3 powernow_k8,cpufreq_stats,cpufreq_ondemand
cpufreq_powersave       2688  0 
sbs                    15112  0 
dock                   11280  0 
sbshc                   7680  1 sbs
container               5632  0 
iptable_filter          3840  0 
ip_tables              14820  1 iptable_filter
x_tables               16132  1 ip_tables
parport_pc             36260  0 
lp                     12324  0 
parport                37832  3 ppdev,parport_pc,lp
joydev                 13120  0 
snd_hda_intel         344856  4 
snd_hwdep              10500  1 snd_hda_intel
snd_pcm_oss            42144  0 
uvcvideo               58116  0 
snd_pcm                78596  2 snd_hda_intel,snd_pcm_oss
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
snd_mixer_oss          17920  2 snd_pcm_oss
compat_ioctl32          2304  1 uvcvideo
videodev               29440  1 uvcvideo
v4l1_compat            15492  2 uvcvideo,videodev
v4l2_common            18304  2 uvcvideo,videodev
ndiswrapper           192920  0 
snd_seq_dummy           4868  0 
psmouse                40336  0 
serio_raw               7940  0 
snd_seq_oss            35584  0 
fglrx                1555468  26 
snd_seq_midi            9376  0 
snd_rawmidi            25760  1 snd_seq_midi
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
video                  19856  0 
snd_timer              24836  2 snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
output                  4736  1 video
battery                14212  0 
ac                      6916  0 
button                  9232  0 
snd                    56996  17 snd_hda_intel,snd_hwdep,snd_pcm_oss,snd_pcm,snd_mixer_oss,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i2c_piix4               9612  0 
shpchp                 34452  0 
ati_agp                 9996  0 
evdev                  13056  7 
i2c_core               24832  1 i2c_piix4
pci_hotplug            30880  1 shpchp
agpgart                34760  2 fglrx,ati_agp
k8temp                  6656  0 
soundcore               8800  2 snd
pcspkr                  4224  0 
ext3                  136840  1 
jbd                    48404  1 ext3
mbcache                 9600  1 ext3
sg                     36880  0 
ide_cd                 32544  0 
cdrom                  37408  1 ide_cd
sd_mod                 30720  3 
pata_acpi               8320  0 
ata_generic             8324  0 
pata_atiixp             8960  0 
usb_storage            73664  0 
libusual               19108  1 usb_storage
usbhid                 32128  0 
hid                    38784  1 usbhid
ahci                   28548  2 
libata                159344  4 pata_acpi,ata_generic,pata_atiixp,ahci
scsi_mod              151436  4 sg,sd_mod,usb_storage,libata
ehci_hcd               37900  0 
atiixp                  5648  0 [permanent]
ide_core              113996  2 ide_cd,atiixp
ohci_hcd               26640  0 
usbcore               146412  8 uvcvideo,ndiswrapper,usb_storage,libusual,usbhid,ehci_hcd,ohci_hcd
r8169                  33156  0 
thermal                16796  0 
processor              37384  2 powernow_k8,thermal
fan                     5636  0 
fbcon                  42912  0 
tileblit                3456  1 fbcon
font                    9472  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3072  1 bitblit
fuse                   50708  3 
vendettaseve@vendettaseve-laptop:~$ 


vendettaseve@vendettaseve-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: RTL8101E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:1e:33:6b:8f:5d
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.2LK ip=192.168.0.104 latency=0 module=r8169 multicast=yes
  *-network
       description: Wireless interface
       product: Atheros Communications Inc.
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: wmaster0
       version: 01
       serial: 00:21:63:80:86:a6
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath9k latency=0 module=ath9k multicast=yes wireless=IEEE 802.11bgn
vendettaseve@vendettaseve-laptop:~$

---

### Post by kevdog on 2008-12-27
Well congratulations, the module is loaded and claiming the device.  Great.

Here is what to do to make the driver load on startup


Edit the /etc/modules file as root

Make sure any reference to ndiswrapper is either deleted or put a # in front of the line

Add ath9k on a line all by itself.


The /etc/modules file is simply a file read at boot.  Each module that needs to be loaded at boot is listed on a separate line. 

There may be a catch however in your case.  There is a distinction between internal modules (modules that were compiled at the time of kernel compilation), and external modules -- modules compiled after the kernel was compiled.  If you ever get around to compiling a kernel -- the difference between the two will be very apparent.  

Anyway -- beginning with I believe the intrepid kernel -- sorry I dont know the exact kernel version -- I believe the ath9k module is an internal module.  Prior to the intrepid kernel, if you wanted the ath9k modules, you needed to compile it -- making it an external module

All internal modules are loaded during boot.  They do not need to be explicitly listed in the /etc/modules file.  They are built-in.  Only external modules need to be listed in the /etc/modules file.  If you do not want to load an external module, simply remove it from the /etc/modules file.

On the other hand -- say you do not want an internal module to load.  This is a common situation.  You need to specifically blacklist this module to prevent it from loading.  This module would be named in the /etc/modprobe.d/blacklist file on a separate line something like:
blacklist ath9k
If you want the internal module to load, you would simply remove the blacklist line in the blacklist file.

I believe in your situation -- since you are using Hardy, you would need to explicitly list ath9k in the /etc/modules file, and remove reference to ndiswrapper -- since ndiswrapper is an external module as well.

And just for the record, although we have been talking about drivers -- such as in windows -- the real name of these drivers within linux are kernel modules.  ndiswrapper is a custom kernel module -- since you had to externally add it (customize your kernel).  I believe ath9k in your case is considered a custom compiled kernel module.  I'm only mentioning the term "custom kernel module" since it makes you sound more intelligent when speaking about drivers in linux.  Although everyone will know what you mean when you say -- I need the wireless driver, or video driver -- the correct term is that you need to load the correct kernel module (custom = external, or internal != custom since its built-into the kernel).

Hopefully that wasn't too much rambling.


And just in case if it wasn't apparently obvious.  If and when you upgrade to Intrepid, Jaunty, or later version -- the ath9k module will come with the kernel so it should work out of the box.

---

### Post by Vendettaseve on 2008-12-27
thank you very much for all your hard work. It is very appriciated :)

One last quick question, How do I load the modules file as root -_- never asks me to put a password in or anything like that... SHould I be doing it via terminal?

THanks

---

### Post by kevdog on 2008-12-27
This depends.

If talking about the boot sequence, the file /etc/modules is owned by root so the modules will be loaded by root.

If wanting to add these after the boot process (or remove them) via the terminal, the commands would be:

sudo modprobe <module_name>
sudo rmmod <module_name>  or sudo modprobe -r <module_name>

Invoking sudo should ask you for the root passphrase unless you are logging in as root -- which is a definite no-no!

---

### Post by Vendettaseve on 2008-12-27
So to add it so it stays in the modules file I cant just browse over and open the file, I have to type Sudo rmmod ath9k

right?

---

### Post by kevdog on 2008-12-27
You need to open the file as root

gksu gedit /etc/modules

and then add the line

Or 

echo ath9k | sudo tee -a /etc/modules

that would be a one step command appending it to the /etc/modules file.

You dont have to remove the module to do this
The /etc/modules file is only read at boot.  Any subsequent module loading/unloading is done at the terminal.

---

### Post by Vendettaseve on 2008-12-27
OK mate all done :D


Thanks so much for your help over the last few days :D.


One small issue however, it runs very slow on my home network that is WEP protected. Is there any reason for this/fix to make it run at normal speed (Im sitting right next to the router, has full bars etc)

Thanks.

---

### Post by kevdog on 2008-12-27
The driver is experimental or still in beta stage so I can't vouch for its performance.  I don't have a card that is compatible with the driver.  Possibly a kernel upgrade might work.  You might want to try a Live Intrepid CD to see if that works better.  That has an updated kernel, and working from a Live CD you don't have to install anything, and it should work without any configuration.

---

### Post by Vendettaseve on 2008-12-28
OK mate I will give that a shot sometime soon :D For now Il just deal with it, or buy a supported external USB style WIFI thing. Whatever works IM not terribly worried.

Thanks again for all your help :D

---

### Post by sieger007 on 2009-07-13
[COLOR="DarkRed"]I have been catching up on this very informative thread.
I beleive I am using that open source driver . 

 modinfo ath_pci
filename:       /lib/modules/2.6.28-13-generic/volatile/ath_pci.ko
srcversion:     D3FD3BD11169A96DBCFF8DE
alias:          pci:v0000168Cd00009013sv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000001Dsv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000001Csv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000001Bsv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000001Asv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000019sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000018sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000017sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000016sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000015sv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000101Asv*sd*bc*sc*i*
alias:          pci:v0000168Cd00001014sv*sd*bc*sc*i*
alias:          pci:v000010B7d00000013sv*sd*bc*sc*i*
alias:          pci:v0000A727d00000013sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000013sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000012sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000007sv*sd*bc*sc*i*
depends:        ath_hal,wlan
vermagic:       2.6.28-13-generic SMP mod_unload modversions 
license:        Dual BSD/GPL
version:        0.9.4
description:    Support for Atheros 802.11 wireless LAN cards.
author:         Errno Consulting, Sam Leffler
parm:           countrycode:Override default country code (int)
parm:           maxvaps:Maximum VAPs (int)
parm:           outdoor:Enable/disable outdoor use (int)
parm:           xchanmode:Enable/disable extended channel mode (int)
parm:           rfkill:Enable/disable RFKILL capability (int)
parm:           autocreate:Create ath device in [sta|ap|wds|adhoc|ahdemo|monitor] mode. defaults to sta, use 'none' to disable (charp)
parm:           ratectl:Rate control algorithm [amrr|minstrel|onoe|sample], defaults to 'sample' (charp)
parm:           ath_debug:Load-time debug output enable (int)

This is a 802.11N Card. But so far the speed is far slower than I get in Vista.
Now I found another driver here  and I beleive that is the same as the Mad-Wifi Mess :
[http://www.atheros.cz/](http://www.atheros.cz/)
which the is the faster one ..?
How do I know if that Mad Driver is being used or the the Open source one and which one can gimme better speeds ?
Please help 
Thx
Sam[/COLOR]

---

