---
title: "No wireless connectivity using broadcom nic"
date: 2013-09-04
forum: Networking &amp; Wireless
---

### Post by ezee2 on 2013-09-04
Hi,  I have an acer aspire 5750Z and a broadcom NIC. My OS is windows xp pro however i have created a bootable pendrive with backtrack 5 r3 using unetbootin. When i boot my laptop to backtrack i dnt have any wireless connections detected, however i have internet using ethernet. Im a newbie when it comes to linux.    some more steps taken as fluke to solve the issue- installed backtrack live on the backtrack interface whch now gives me an option at startup to choose between linux and windows pro (my moms gonna kill me cuz im using her laptop for the time being)    tried commands in terminal that i read from other forums -  sudo apt-get install linux-headers-generic  sudo apt-get install --reinstall bcmwl-kernel-source  sudo modprobe wl    I need help :(  my entire course is help up because of this ...

---

### Post by kc-koellein on 2013-09-04
There are volumes of threads about fixing broadcom and other wireless chipsets...

...I'd look at this a different way though. You are obviously a little new to linux. I would steer clear of BackTrack. It is an awesome tool, and v5 is based on Ubuntu, great. But! It's not meant to be a Prime-Time desktop OS for your Acer. Take a crack at Ubuntu 12.04 or later and see if the issue is still there. It sounds like you're in a jam that doesn't have time for troubleshooting...

(Also, all the tools from BackTrack can be installed on any Ubuntu flavor... try not to get distracted and/or overwhelmed by the goodies this early. :-) I know it's hard! Just get a good stable distro like Ubuntu 12.04 or 13.04, and then branch out and explore from there!)

Also, don't worry about the dual-boot. It won't break anything and CAN be removed or you cab just shorten the menu screen time.

Google for "grub" and set the filter to within the last year... tons of hits. Or, "grub 2 set default".

(Problem is, it usually gets reset when there's an update... so you have to modify grub again. but it takes less than a minute... and there's probably a solution for that anyway! I haven't bothered to look cause it works for me.)

Or just look here. [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

If you wanna be really stealth about it, you can set it to boot Windows by default, with, say, maybe a 3 second timeout on a black screen. If you hit a key during that 3 seconds, that menu shows up, otherwise, it takes a 1 or 2 or 3 second pause and then boots into Windows anyway. 
[URL="http://ubuntuforums.org/showthread.php?t=1195275"]
http://ubuntuforums.org/showthread.php?t=1195275[/URL] 

You can set: 
[LIST]
[*]**GRUB_HIDDEN_TIMEOUT=0**
[LIST]
[*]Wait X seconds for a key to be pressed before displaying the menu. If no key is pressed during that time, boot immediately.
[/LIST]



[*]**GRUB_HIDDEN_TIMEOUT_QUIET=true**
[LIST]
[*]Used with the GRUB_HIDDEN_TIMEOUT setting.
[*]true - No countdown is displayed. The screen will be blank.
[*]false - A counter will display on a blank screen for the duration of the GRUB_HIDDEN_TIMEOUT value.
[*]This feature currently appears to be broken; the timeout counter isn't appearing when set to 'false' or not set.
[/LIST]
[/LIST]

This way Mom won't have to freak out...! I went through the same scenario with my wife! :-)

HTH
K9SPY

---

### Post by ezee2 on 2013-09-08
> **kc-koellein said:**
> There are volumes of threads about fixing broadcom and other wireless chipsets...

...I'd look at this a different way though. You are obviously a little new to linux. I would steer clear of BackTrack. It is an awesome tool, and v5 is based on Ubuntu, great. But! It's not meant to be a Prime-Time desktop OS for your Acer. Take a crack at Ubuntu 12.04 or later and see if the issue is still there. It sounds like you're in a jam that doesn't have time for troubleshooting...

(Also, all the tools from BackTrack can be installed on any Ubuntu flavor... try not to get distracted and/or overwhelmed by the goodies this early. :-) I know it's hard! Just get a good stable distro like Ubuntu 12.04 or 13.04, and then branch out and explore from there!)

Also, don't worry about the dual-boot. It won't break anything and CAN be removed or you cab just shorten the menu screen time.

Google for "grub" and set the filter to within the last year... tons of hits. Or, "grub 2 set default".

(Problem is, it usually gets reset when there's an update... so you have to modify grub again. but it takes less than a minute... and there's probably a solution for that anyway! I haven't bothered to look cause it works for me.)

Or just look here. [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

If you wanna be really stealth about it, you can set it to boot Windows by default, with, say, maybe a 3 second timeout on a black screen. If you hit a key during that 3 seconds, that menu shows up, otherwise, it takes a 1 or 2 or 3 second pause and then boots into Windows anyway. 
[URL="http://ubuntuforums.org/showthread.php?t=1195275"]
http://ubuntuforums.org/showthread.php?t=1195275[/URL] 

You can set: 
[LIST]
[*]**GRUB_HIDDEN_TIMEOUT=0**
[LIST]
[*]Wait X seconds for a key to be pressed before displaying the menu. If no key is pressed during that time, boot immediately.
[/LIST]

[*]**GRUB_HIDDEN_TIMEOUT_QUIET=true**
[LIST]
[*]Used with the GRUB_HIDDEN_TIMEOUT setting.
[*]true - No countdown is displayed. The screen will be blank.
[*]false - A counter will display on a blank screen for the duration of the GRUB_HIDDEN_TIMEOUT value.
[*]This feature currently appears to be broken; the timeout counter isn't appearing when set to 'false' or not set.
[/LIST]
[/LIST]

This way Mom won't have to freak out...! I went through the same scenario with my wife! :-)

HTH
K9SPY


[HR][/HR]
Hi, 
Thnks for the reply. But i guess the problem is not the dual-boot. I got tht sorted. The real problem is the initial bit. I tried evrything for the wireless .... chked other forums as well ... no go :( 
 
 
 it does not detect the wireless whatsoever .... Im sure there are some drivers tht i need to install .. i dnt know where to get them ...

---

### Post by varunendra on 2013-09-09
Welcome to the Forums ezee2 !! :)
> **ezee2 said:**
> I tried evrything for the wireless .... chked other forums as well ... no go :(

It sounds like you really have tried too many things. So it warrants a deep diagnostics. Please follow the "Wireless Script" link in my signature, follow the instructions in the linked post (you'd probably need the "No Internet" method) to download and run the script, and post back the report the script generates.

---

### Post by ezee2 on 2013-09-10
ok ... il follow ur "wireless script" ... and should i post the report back here ??? ... 

also to add to this ... i have internet via ethernet... so i guess i can use the cable internet method right ???

---

### Post by varunendra on 2013-09-10
Right, you should use the 1st method, although you can use any one, doesn't matter.

Post back the result file (or its contents, enclosed within "Code" tags) for us to see.

---

### Post by ezee2 on 2013-09-10
This is what i got after following the "wireless script" from ur signature... ive copied and pasted the info frm the wireless-info.txt file below :

```

*************** info trace ***************

***** uname -a *****

Linux bt 3.2.6 #1 SMP Fri Feb 17 10:40:05 EST 2012 i686 GNU/Linux

***** lsb_release *****

Distributor ID:    Ubuntu
Description:    Ubuntu 10.04.3 LTS
Release:    10.04
Codename:    lucid

***** lspci *****

02:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM57785 Gigabit Ethernet PCIe [14e4:16b5] (rev 10)
    Kernel driver in use: tg3
    Kernel modules: tg3
02:00.1 SD Host controller [0805]: Broadcom Corporation NetXtreme BCM57765 Memory Card Reader [14e4:16bc] (rev 10)
    Kernel driver in use: sdhci-pci
    Kernel modules: sdhci-pci
--
03:00.0 Network controller [0280]: Broadcom Corporation BCM43227 802.11b/g/n [14e4:4358]

***** lsusb *****

Bus 002 Device 003: ID 04f3:02f4 Elan Microelectronics Corp. 2.4G Cordless Mouse
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 04fc:2801 Sunplus Technology Co., Ltd 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

***** PCMCIA Card Info *****


***** iwconfig *****


***** rfkill *****

0: acer-wireless: Wireless LAN
    Soft blocked: no
    Hard blocked: no

***** lsmod *****


***** nm-tool *****

***** NetworkManager.state *****

***** NetworkManager.conf *****


***** interfaces *****

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp


***** iwlist *****


***** resolv.conf *****

nameserver 192.168.1.1

***** blacklist *****

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/blacklist-bt.conf]
blacklist rt2870sta
blacklist rt2860sta

[/etc/modprobe.d/blacklist.conf]
blacklist evbug
blacklist ar9170usb
blacklist r8187
blacklist ath_pci
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist i2c_i801
blacklist prism54
blacklist bcm43xx
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac

***** modinfo *****


***** udev rules *****

# PCI device 0x14e4:0x16b5 (tg3)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

***** dmesg *****

[   10.587088] psmouse serio1: elantech: assuming hardware version 3 (with firmware version 0x450f01)

****************** done ******************


```

---

### Post by varunendra on 2013-09-10
> **ezee2 said:**
> 
```
Distributor ID:    Ubuntu
Description:    **[COLOR="#FF0000"]Ubuntu 10.04.3 LTS[/COLOR]**
Release:    10.04
Codename:    lucid
```

I should say - "Game Over". The version you have installed is outdated and you won't normally get support or packages for it.

The first advice is - download the ISO of 12.04 ([via torrent]("http://www.ubuntu.com/download/alternative-downloads")), burn a CD or create a live USB from the iso and install it.

Both the wired and wireless connections will work while installing (it will always work in live mode). So make sure to check the checkboxes for "Install Updates" and "Install third party software" when you get to that screen. This will download the proprietary driver that works with your card, and will install it. After installation is finished, you'll have a working wireless connection.

If however, for whatever reasons, you wish to make the current one work, you will need to change the source of software packages, then you can install the driver for it. It is not recommended, but let me know if you wish to go that way anyway.

---

