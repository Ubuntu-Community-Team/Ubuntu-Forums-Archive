---
title: "RTL8187 native module for Realtek is working, but..."
date: 2009-03-25
forum: Networking &amp; Wireless
---

### Post by robinz77 on 2009-03-25
.... the connection speed is so [COLOR="Red"][SIZE="4"]**slow**[/SIZE][/COLOR], comparing with xp. Large files copy in the wireless LAN takes 5 times longer. Ndiswrapper with xp driver works, sometimes, but it hangs my laptop so often that I removed it. 

Description:
Toshiba Satellite L300 with Ubuntu 8.10 (kernel 2.6.27-11-generic)
Access point (router): 802.11g

[I]somebody@laptop:~$ iwconfig wlan0 
wlan0     IEEE 802.11bg  ESSID:"myaccesspoint"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: xx: xx: xx: xx: xx: xx   
          Bit Rate=54 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr: off   Fragment thr=2352 B   
          Power Management: off
          Link Quality=100/100  Signal level:-19 dBm  
          Rx invalid nwid: 0  Rx invalid crypt: 0  Rx invalid frag: 0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

somebody@laptop:~$ lsusb
Bus 007 Device 002: ID XXX:XXXX Realtek Semiconductor Corp. RTL8187B Wireless Adapter[/I]

**The Question: Is there a possibility to fine tune something to make it work faster?**

---

### Post by pytheas22 on 2009-03-25
It's no guarantee, but you might have better luck if you compiled the driver using the latest source code from [http://wireless.kernel.org/](http://wireless.kernel.org/), rather than using Ubuntu's stock module.  I don't have time now to provide full instructions for compiling, but if you can't figure it out, let me know.

---

### Post by freeztar on 2009-03-26
I'm having the same exact problem. Same kernel. Same device.

I for one would certainly appreciate instructions on how to compile the kernel. :)

---

### Post by robinz77 on 2009-03-26
I've tried to switch to the previous kernel. It is the same. 
It looks like it's working in the 801.11b mode.

---

### Post by freeztar on 2009-03-26
Good to know. How do you switch it to b mode?

---

### Post by pytheas22 on 2009-03-26
Take a look at [this page]("http://michael-peeters.blogspot.com/2008/12/getting-realtek-rtl8187b-wifi-stable.html"), which says that setting the card to operate at 5.5 megabits/second (rather than 54) makes it stable.  This goes along with the finding that it works better in 11b mode, because the maximum speed in that mode is also slower.

---

### Post by freeztar on 2009-03-27
Thanks, but I've tried that multiple times. Last time I tried it, it worked, but it is extremely slow and most pages time out before loading. A page like this would take it around 3-4 minutes to load. I might as well be using dial-up at that point.

Actually, I've tried almost every hack I could find for this chip. I'm beginning to wonder if I may have damaged it in the process or perhaps the new kernel driver got overwritten at some point. I'm new to linux so I'm not even sure how to check for this. I did check the kernel/wireless directory and there is a file for rtl8187. Is it possible that one of the hacks I tried overwrote the original 2.6.27 kernel file for rtl8187? In other words, when I run files like makedrv and install, does it write over the file originally supplied with the kernel? Is there a way to check this?

---

### Post by pytheas22 on 2009-03-27
> Is it possible that one of the hacks I tried overwrote the original 2.6.27 kernel file for rtl8187? In other words, when I run files like makedrv and install, does it write over the file originally supplied with the kernel? Is there a way to check this?

Depending on what you did, you might have overwritten the default driver.  To check, run the command 'modinfo rtl8187'.  The output for the default module in the 2.6.27-11 Ubuntu kernel should look like this (I'm not sure if the 'alias' lines are supposed to match, but the 'srcversion' line in particular should):
```

filename:       /lib/modules/2.6.27-11-generic/updates/rtl8187.ko
license:        GPL
description:    RTL8187/RTL8187B USB wireless driver
author:         Larry Finger <Larry.Finger@lwfinger.net>
author:         Hin-Tak Leung <htl10@users.sourceforge.net>
author:         Herton Ronaldo Krzesinski <herton@mandriva.com.br>
author:         Andrea Merello <andreamrl@tiscali.it>
author:         Michael Wu <flamingice@sourmilk.net>
srcversion:     290F0D334BA1A0FDE730BF6
alias:          usb:v13D1pABE6d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0028d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p000Dd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v03F0pCA02d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0846p4260d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0846p6A00d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0846p6100d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0BDAp8198d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0BDAp8197d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0BDAp8189d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0BDAp8187d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp705Ed*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0B05p171Dd*dc*dsc*dp*ic*isc*ip*
depends:        eeprom_93cx6,lbm_cw-mac80211,usbcore,lbm_cw-cfg80211
vermagic:       2.6.27-11-generic SMP mod_unload modversions 
```

If your output is different, it's probably a different build of the module (or you're using an older version of the kernel, but as of today, you should have 2.6.27-11 if you've applied all Ubuntu updates).

If you can't get this card to work satisfactorily  using the native driver, another option would be ndiswrapper, which uses Windows drivers to power the device.  If you tell me the output of the 'lspci -nn' command, I'll try to find you instructions for setting up ndiswrapper.

---

### Post by freeztar on 2009-03-27
Thanks again. Here's the output of modinfo:

```
filename:       /lib/modules/2.6.27-11-generic/kernel/drivers/net/wireless/rtl8187.ko
license:        GPL
description:    RTL8187/RTL8187B USB wireless driver
author:         Andrea Merello <andreamrl@tiscali.it>
author:         Michael Wu <flamingice@sourmilk.net>
srcversion:     7E229F3124D51DF4700B9CF
alias:          usb:v13D1pABE6d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0028d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p000Dd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v03F0pCA02d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0846p4260d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0846p6A00d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0846p6100d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0BDAp8198d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0BDAp8197d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0BDAp8189d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0BDAp8187d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp705Ed*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0B05p171Dd*dc*dsc*dp*ic*isc*ip*
depends:        mac80211,eeprom_93cx6,cfg80211,usbcore
vermagic:       2.6.27-11-generic SMP mod_unload modversions 586 

```

So, apparently, it's another version. Hmm..

I tried ndiswrapper before, using the tutorial here at ubuntuforums, and it showed it as installed (win98 driver), but it would not work.

Here's my output for lspci -nn:

```
00:00.0 Host bridge [0600]: ATI Technologies Inc RS690 Host Bridge [1002:7910]
00:01.0 PCI bridge [0604]: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx) [1002:7912]
00:05.0 PCI bridge [0604]: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 1) [1002:7915]
00:07.0 PCI bridge [0604]: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 3) [1002:7917]
00:12.0 SATA controller [0106]: ATI Technologies Inc SB600 Non-Raid-5 SATA [1002:4380]
00:13.0 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI0) [1002:4387]
00:13.1 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI1) [1002:4388]
00:13.2 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI2) [1002:4389]
00:13.3 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI3) [1002:438a]
00:13.4 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI4) [1002:438b]
00:13.5 USB Controller [0c03]: ATI Technologies Inc SB600 USB Controller (EHCI) [1002:4386]
00:14.0 SMBus [0c05]: ATI Technologies Inc SBx00 SMBus Controller [1002:4385] (rev 14)
00:14.1 IDE interface [0101]: ATI Technologies Inc SB600 IDE [1002:438c]
00:14.2 Audio device [0403]: ATI Technologies Inc SBx00 Azalia (Intel HDA) [1002:4383]
00:14.3 ISA bridge [0601]: ATI Technologies Inc SB600 PCI to LPC Bridge [1002:438d]
00:14.4 PCI bridge [0604]: ATI Technologies Inc SBx00 PCI to PCI Bridge [1002:4384]
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
01:05.0 VGA compatible controller [0300]: ATI Technologies Inc RS690M [Radeon X1200 Series] [1002:791f]
01:05.2 Audio device [0403]: ATI Technologies Inc Radeon X1200 Series Audio Controller [1002:7919]
08:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 01)

```

Again, I sincerely appreciate your help.

---

### Post by pytheas22 on 2009-03-27
When you installed ndiswrapper before, you may have forgotten to blacklist the rtl8187 module, which would have prevented ndiswrapper from working.  Please run these commands and post the output (some of them may not have any output):
```

ndiswrapper -l
sudo rmmod rtl8187
sudo depmod -a
sudo modprobe ndiswrapper
lshw -C Network
dmesg | grep -e ndis -e wlan
```

At this point, your device should be running under ndiswrapper, provided it's installed correctly.  Try connecting now.  If it works better, we can remove rtl8187 permanently so that ndiswrapper will always take control.

---

### Post by freeztar on 2009-03-27
Ok, I definitely want to try this, but I should point out something first. I'm able to get online currently because I'm using a Hawking wireless dongle (ralink chip). I'll have to unplug it (and reboot?) to get ndiswrapper going. Will I need to blacklist it as well, or should it not matter as long as I reboot without the card inserted?

---

### Post by pytheas22 on 2009-03-27
> Ok, I definitely want to try this, but I should point out something first. I'm able to get online currently because I'm using a Hawking wireless dongle (ralink chip). I'll have to unplug it (and reboot?) to get ndiswrapper going. Will I need to blacklist it as well, or should it not matter as long as I reboot without the card inserted?

Just unplug the card.  There should be no need to reboot.

---

### Post by freeztar on 2009-03-29
Ok, I tried ndiswrapper again and then entered the commands you listed and it will not connect to my router with WEP. Though, without encryption, it seems to work good so far. I haven't tried WPA yet. With WEP, it just hangs and then asks me for the key again. I enter the key and it loops back. Any ideas?

---

### Post by pytheas22 on 2009-03-29
You might have better luck connecting if you use wicd instead of NetworkManager.  You can install wicd by running these commands (you will need to be online for them to work):
```

echo 'deb http://apt.wicd.net hardy extras' | sudo tee -a /etc/apt/sources.list
wget -q http://apt.wicd.net/wicd.gpg -O- | sudo apt-key add -
sudo apt-get update
sudo apt-get install wicd
```

Then launch wicd from the Applications>Internet menu.  Can you connect to WPA with it?  Sometimes it works in situations where NetworkManager doesn't.

(Note that installing wicd will force the uninstallation of NetworkManager.  If you want NM back later, run this command: 'sudo apt-get install network-manager-gnome'.)

---

