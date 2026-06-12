---
title: "Acer Laptop - Atheros AR5B93 Wireless not found 10.04"
date: 2010-05-08
forum: Networking &amp; Wireless
---

### Post by harry003 on 2010-05-08
Chili - 

Let's just reconsider this. I tried to backtrack and uninstall some of the stuff, useless.

I am a Windows user, and have resigned myself to the concept that when things get completely FUBAR you need to just take a deep breath and start over.

Is there a procedure to completely delete and re-install Ubuntu, or should I delete its partition altogether, and re-create and re-install it? I can do that if I really have to.

I have not accumulated enough stuff here that I could not just make a clean start, if that will fix this mess. Somehow I imagined that this would be different from Windows, but maybe it really isn't.

What holds me back is seeing the multitude of people having trouble with wireless in 10.04. Is this a widespread problem that has a good chance of really getting fixed, soon?

At the minimum, can you help me get my ethernet back? It has fallen off the radar screen, although the hotel's system might have gone down, as it often does.

---

### Post by chili555 on 2010-05-08
I am not persuaded you have done so much that you have foobared your install. You installed and added backports and that's about it, yes?

Before we exercise the nuclear option, let's do a full exploratory. First, I think this is supposed to work with the module ath5k. Let's verify. Please do:```
lspci -nn
```Post the line relevant to your wireless. Next, let's load the module and see what happens:```
sudo modprobe ath5k
iwconfig
```Did your wireless spring to life? Please post:```
dmesg | grep -i ath
```Let me try to figure out what's not happening.

---

### Post by harry003 on 2010-05-08
Chili - 

I really appreciate your help in trying to figure this out.

First, I performed each of the things you recommended and they all returned "no wireless extensions"

Second, whenever I look for a wireless opportunity (eg right-clicking on the ethernet icon or asking under System/Preferences/Network connections) the tab is always blank.

<By the way, uninstalling the linux-backports business got me my ethernet connection back.>

Third, the laptop has a little button that turns the wireless off and on with a LED. The switch is active and working under Windows but seems dead in Linux. Surely it is on by default when I boot up.

As for my experimentation, I have tried approximately a dozen solutions over the past few weeks, things like essential build, make, install, get, and various attempts to download and install Madwifi and its drivers. (That produced dozens of junk files all around!)

Almost every aspect of Ubuntu Lucid has operated swimmingly (except for my multiple attempts to download and install Google Earth and Guayadeque which have consistently failed) and I am quite pleased overall except for these 3 problems.

I do not think that my installation has any huge systemic problems, but I do think that there must be a few tiny gremlins in there somewhere that are roadblocking my efforts.

The failure of wireless is almost a deal-killer, so I need to get that fixed.

---

### Post by chili555 on 2010-05-09
> Please post:
Code:

dmesg | grep -i ath

Let me try to figure out what's not happening.> 
Code:

lspci -nn

Post the line relevant to your wireless. I think this will be very helpful. May I see it please?

---

### Post by harry003 on 2010-05-09
harry@harry-laptop:~$ dmesg | grep -i ath
[    0.166034] CPU0: AMD Athlon(tm) X2 Dual Core Processor L310 stepping 02
[    0.320126] CPU1: AMD Athlon(tm) X2 Dual Core Processor L310 stepping 02
[    1.307250] device-mapper: multipath: version 1.1.0 loaded
[    1.307255] device-mapper: multipath round-robin: version 1.0.0 loaded
[    1.309934] powernow-k8: Found 1 AMD Athlon(tm) X2 Dual Core Processor L310 processors (2 cpu cores) (version 2.20.00)

---

### Post by harry003 on 2010-05-09
harry@harry-laptop:~$ lspci -nn
00:00.0 Host bridge [0600]: Advanced Micro Devices [AMD] RS780 Host Bridge [1022:9600]
00:01.0 PCI bridge [0604]: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (int gfx) [1022:9602]
00:04.0 PCI bridge [0604]: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0) [1022:9604]
00:05.0 PCI bridge [0604]: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1) [1022:9605]
00:11.0 SATA controller [0106]: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode] [1002:4391]
00:12.0 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller [1002:4397]
00:12.1 USB Controller [0c03]: ATI Technologies Inc SB700 USB OHCI1 Controller [1002:4398]
00:12.2 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB EHCI Controller [1002:4396]
00:13.0 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller [1002:4397]
00:13.2 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB EHCI Controller [1002:4396]
00:14.0 SMBus [0c05]: ATI Technologies Inc SBx00 SMBus Controller [1002:4385] (rev 3c)
00:14.1 IDE interface [0101]: ATI Technologies Inc SB700/SB800 IDE Controller [1002:439c]
00:14.2 Audio device [0403]: ATI Technologies Inc SBx00 Azalia (Intel HDA) [1002:4383]
00:14.3 ISA bridge [0601]: ATI Technologies Inc SB700/SB800 LPC host controller [1002:439d]
00:14.4 PCI bridge [0604]: ATI Technologies Inc SBx00 PCI to PCI Bridge [1002:4384]
00:14.5 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller [1002:4399]
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
01:05.0 VGA compatible controller [0300]: ATI Technologies Inc RS780M/RS780MN [Radeon HD 3200 Graphics] [1002:9612]
02:00.0 Network controller [0280]: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) [168c:002a] (rev 01)
08:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 02)
harry@harry-laptop:~$

---

### Post by chili555 on 2010-05-10
> Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) [168c:002a] (rev 01)This card should work with the driver module *ath9k*. Please do:```
sudo modprobe ath9k
iwconfig
```Do you have a wireless interface, wlan0, perhaps? Can you connect?

If so, we can take steps to get it to load on boot. If not, after you load *ath9k*, run:```
dmesg | grep ath
```Post the results, please.

---

### Post by harry003 on 2010-05-24
Chili - 

I'm back. I got a week and a half off from my out-of-state work deployment and spent it with my family. Now I am back in my lonely hotel room with my spiffy month-old laptop and want to try to get my built-in wireless working for the first time ever under Ubuntu.

BTW - although the specs say that it is an Atheros AR5B93, asking directly returns Atheros AR928X and/or AMD RS780. But maybe none of that matters anyway. 

Here is what it spit out when I asked it your questions:



wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
harry@harry-laptop:~$ dmesg | grep ath
[    1.294839] device-mapper: multipath: version 1.1.0 loaded
[    1.294843] device-mapper: multipath round-robin: version 1.0.0 loaded
[ 2549.766832] ath9k 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[ 2549.766847] ath9k 0000:02:00.0: setting latency timer to 64
[ 2550.203706] ath: EEPROM regdomain: 0x65
[ 2550.203710] ath: EEPROM indicates we should expect a direct regpair map
[ 2550.203717] ath: Country alpha2 being used: 00
[ 2550.203720] ath: Regpair used: 0x65
[ 2550.268682] phy0: Selected rate control algorithm 'ath9k_rate_control'
[ 2550.269880] Registered led device: ath9k-phy0::radio
[ 2550.269918] Registered led device: ath9k-phy0::assoc
[ 2550.269965] Registered led device: ath9k-phy0::tx
[ 2550.269994] Registered led device: ath9k-phy0::rx


I keep running update and Update Manager in hopes that somebody will magically solve this and incorporate it into the great big Ubuntu world for all of us suffering newbies.

Thank you again.

---

