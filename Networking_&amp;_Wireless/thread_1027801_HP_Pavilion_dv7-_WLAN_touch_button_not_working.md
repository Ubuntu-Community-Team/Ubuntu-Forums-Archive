---
title: "HP Pavilion dv7- WLAN touch button not working"
date: 2009-01-01
forum: Networking &amp; Wireless
---

### Post by Phazonx on 2009-01-01
Hi.  I've been trying to get my wireless to work in my laptop for awhile now.  I've tried most of the atheros wireless solutions, but none of them worked.  The hardware is there, but it doesn't show up when I try to use it from nm-applet.  And I think its cause the little touch button won't turn blue ( which means "on") when I touch it.

How would I get it to work?

lspci:

00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:01.0 PCI bridge: Hewlett-Packard Company Device 9602
00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0)
00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1)
00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2)
00:07.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 3)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 11h HyperTransport Configuration (rev 40)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 11h Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 11h DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 11h Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 11h Link Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS780M/RS780MN [Radeon HD 3200 Graphics]
01:05.1 Audio device: ATI Technologies Inc RS780 Azalia controller
08:00.0 System peripheral: JMicron Technologies, Inc. SD/MMC Host Controller
08:00.2 SD Host controller: JMicron Technologies, Inc. Standard SD Host Controller
08:00.3 System peripheral: JMicron Technologies, Inc. MS Host Controller
08:00.4 System peripheral: JMicron Technologies, Inc. xD Host Controller
09:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
0a:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)

---

### Post by StuartZ on 2009-01-02
I have the same problem.  lshw shows it as being disabled.  Ubuntu docs say that it may possibly be disabled in Windows.  I have not been able to figure it out yet.  Hope someone has the answer!

---

### Post by Phazonx on 2009-01-04
I did a few simple steps.  I'm not really experienced with this, or know much about it, but this is what I did and it works now.

First I downloaded this Madwifi thing I heard about.  Get it here [http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6/madwifi-hal-0.10.5.6-r3875-20081105.tar.gz](http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6/madwifi-hal-0.10.5.6-r3875-20081105.tar.gz)

extract the stuff into your home folder

Then open terminal and go to the directory.  


cd /home/phazonx/madwifi-hal-0.10.5.6

then, I did this

 sudo make install

well, thats what I did.  sorry its so vague. lol. oh well.  
the touch button doesn't work, but the wireless card now functions. :)

and btw, can someone tell me how you make code be in a box when you post it here? thanks

---

### Post by 2hot6ft2 on 2009-01-04
> **Phazonx said:**
> 
and btw, can someone tell me how you make code be in a box when you post it here? thanks
Sure, you highlight the text you want wrapped in a code and click on the # in the options at the top of the box you're typing in.


Well there are 388 models that are HP Pavilion dv7's as shown here. [http://h10025.www1.hp.com/ewfrf/wc/pfinder?query=HP+Pavilion+dv7&lc=en&cc=us&lc=en&dlc=en&cc=us&lang=en](http://h10025.www1.hp.com/ewfrf/wc/pfinder?query=HP+Pavilion+dv7&lc=en&cc=us&lc=en&dlc=en&cc=us&lang=en)
So you'll have to be more specific than that. I have a HP Pavilion G60-125NR while it's not the same in some aspects in others it is. Mine has the AR5009 wifi card which uses the AR928x chipset. It works so if yours has the same card and chipset yours should work in 8.10 Intrepid.

In ```
gksudo gedit /etc/modeprobe.d/madwifi
``` I have ath5k and hal_pci blacklisted meaning there is no # before them.
I get best results using kernel 2.6.27-7 at the grub kernel selection screen when booting up.
If I use kernel 2.6.27-9 my connection will drop off from time to time.

If your kernel # is lower than 2.6.27-7 you can use this to get it in a terminal.
Applications>Accessories>Terminal
```
sudo apt-get install linux-backports-modules-intrepid-generic
```

The button does not work in ubuntu for turning the wifi on and off. If you used the button in windows to turn it of you need to go back into windows and turn it back on for your wifi card to work in ubuntu.

The light will not stay blue in ubuntu but will flicker showing there is activity in ubuntu and will be orange when there is none.

Hope you find this helpful.

---

### Post by Phazonx on 2009-01-04
hehe. thanks for the help.

I also forgot to mention this works with ONLY atheros cards(I think).

lol. sorry for the vague informatino.  its either that, or I don't post anything at all.  every little bit counts. :)

---

