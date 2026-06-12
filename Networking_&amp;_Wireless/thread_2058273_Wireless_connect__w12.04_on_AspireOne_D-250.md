---
title: "Wireless connect  w/12.04 on AspireOne D-250"
date: 2012-09-15
forum: Networking &amp; Wireless
---

### Post by 8lackie on 2012-09-15
Hi, I know just enough to SNAFU things. I upgraded from 11,04 to 12.04. I have wired connection. Without I do not. This issue was happening on 11.04 also. I keep getting a dialog box asking for my security password. It accepts it (or seems to) then if i open a browser window I receive "can't find server" and security dialog box for my connection comes back up. 

I've nosed around here as much as i can and found that:
"sudo Ishw -C network" did nothing for me, "command not found", not that I actually  knew what I was typing.

Then I tried "lspci". I've pasted the result below. I'm hoping this is helpful. Any help is appreciated. Thank you 8lackie
[COLOR=#000066][FONT=verdana,sans-serif][B]00:00.0 Host bridge: Intel Corporation Mobile 945GSE Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GSE Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 4 (rev 02)
00:1d.0 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7-M Family) SATA Controller [AHCI mode] (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
01:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)
03:00.0 Ethernet controller: Atheros Communications Inc. AR8132 Fast Ethernet (rev c0)

[/B][/FONT][/COLOR]

---

### Post by 8lackie on 2012-09-15
[COLOR=Magenta]**Hi! Anyone know what I'm talking about or can help? I'd appreciate it. I put as much information as I have. Thanks**[/COLOR]

---

### Post by OM55 on 2012-09-15
I have 5 Acer Aspite One laptop in different sites, all with Ubuntu 12.04 and have seen a similar issue when the wireless connection has problems and sometimes repeatedly asks for the password.

After researching and trying a few things, I found that:
1. The Aspire One wireless reception is not as good as a full size laptop. As a result it is much more sensitive to bad reception issues. 

2. It has an issue with a combined cipher of AES & Tkip or just AES. It works well when I use Tkip only (this is a setting in the wireless router, under the wireless settings).

3. If you have a wireless range extender, sometimes those lose connection while the Aspire One connection is to the extender. That will kill your laptop's connection (you can avoid that by setting up on the laptop's network settings the BSSID to be that of the router you want to connect to always).


So to test these assumptions, I suggest the following:

1. Change in the wireless the cipher to be only Tkip.

2. Remove the wireless password on the router and confirm that the Aspire One can connect to the WiFi. Make sure the laptop is close enough to the router so you can rule out reception issues

3. Add the password back on the wireless router without moving the laptop away, and see if it connects now.

if no good connection is made, you may have a different problem. Try to upgrade the router's firmware to the latest.

If good connection is made, just continue to make sure you have good reception always.

Hope that helps!

---

### Post by 8lackie on 2012-09-16
[COLOR=Navy][B]Thanks for your help OM55. I'm bivouacked in the Balkans at the moment. My internet is a cablebox/wireless router in-one. I cant seem to get into it via 192.168...etc so for the time being I can't see what the setting are or mess with them.

No wireless range extender.

I've been sitting next to the router the whole time.  I did have Ubuntu 10.04 on here once upon a time and it worked fine. Of course the question is "what changed?" I don't know.

I found the 802.11 Linux STA driver. but don't know if this is already part of 12.04 nor do I understand how to install it, or if would be any benefit.

I also tried "sudo apt-get install firmware-b43-installer" This seemed to be already installed.

At least I have a good wired connection. I am stuck.




[/B][/COLOR]

---

### Post by Bucky Ball on 2012-09-16
[I]Thread moved to [B]Networking & Wireless


[/B][/I]Please avoid overusing coloured text. If you want to make code stand out and easier to read, please use [code] tags by typing them in or clicking 'Edit' then 'Go Advanced', mark out the code and click the # icon. Cheers.

Tried any of these?

[http://au.yhs4.search.yahoo.com/yhs/search;_ylt=A7exU8R5xFVQHXwAKxcK5gt.?p=BCM4312%20802.11b%2Fg%20LP-PHY%20ubuntu&fr=altavista&fr2=sfp]("http://au.yhs4.search.yahoo.com/yhs/search;_ylt=A7exU8R5xFVQHXwAKxcK5gt.?p=BCM4312%20802.11b%2Fg%20LP-PHY%20ubuntu&fr=altavista&fr2=sfp")

:?

---

### Post by bkratz on 2012-09-16
If you can find an ethernet connection you might try looking at the following thread--post 10. 

[http://ubuntuforums.org/showthread.php?t=2053243&highlight=BCM4312+802.11b%2Fg+LP-PHY](http://ubuntuforums.org/showthread.php?t=2053243&highlight=BCM4312+802.11b%2Fg+LP-PHY)

---

### Post by Bucky Ball on 2012-09-16
Yes, plugging in an ethernet cable, getting online and getting updates is generally the first thing to do. Then check 'Additional Drivers'. I have noticed the LP-PHY cards are problematic, though. Most older Broadcom work out-of-the-box nowadays and so probably just a matter of time til this one does, too.

Just to clarify; this is a straight Ubuntu 12.04 LTS desktop install? Not another flavour or derivative?

---

### Post by 8lackie on 2012-09-16
Just to clarify; this is a straight Ubuntu 12.04 LTS desktop install? Not another flavour or derivative?[/QUOTE]

[COLOR=Navy]**It is, although I upgraded it from 11.04, which I believe was a clean install originally.**[/COLOR]

---

### Post by 8lackie on 2012-09-26
Ive tried several solutions posted by chili555. So far nothing has worked

[http://ubuntuforums.org/showthread.php?t=2053243&highlight=BCM4312+802.11b%2Fg+LP-PHY](http://ubuntuforums.org/showthread.php?t=2053243&highlight=BCM4312+802.11b%2Fg+LP-PHY)

#10 also #2

This whole time i've had a fine wired connection. but as soon as I go wireless I'm asked to to authenticate my password. Sheer madness I tell you!

---

### Post by 8lackie on 2012-09-27
Now I've managed to install Broadcom STA wireless driver...not sure how I did it:KS, but I don't think I'm getting any closer to a wireless connection. Ive scoured this forum picking up on a lot of the suggestions for forcing a connection but to no avail
when I do a lspci -nn | grep 0280
I see I have BCM4312 802.11b/g LP-PHY 14e4:4315[rev 01]

Also tried update of bcmwl-kernel-source. My machine says I have the newest version.

I think I need more help, I'm getting lost and confused.

---

### Post by 8lackie on 2012-09-30
Hi  all, I'm still stuck w/out wireless here.  Further help or steps would be welcome. As I posted before I know just enough to get in trouble. I can follow directions, I'm just not clear on the results of some of my actions or even where to view results ](*,):confused::confused::confused:

---

### Post by 8lackie on 2012-10-01
hi y'all, I'm still stuck. Any and all help would be appreciated. -Thanks):P

---

### Post by chili555 on 2012-10-01
> **8lackie said:**
> Now I've managed to install Broadcom STA wireless driver...not sure how I did it:KS, but I don't think I'm getting any closer to a wireless connection. Ive scoured this forum picking up on a lot of the suggestions for forcing a connection but to no avail
when I do a lspci -nn | grep 0280
I see I have BCM4312 802.11b/g LP-PHY 14e4:4315[rev 01]

Also tried update of bcmwl-kernel-source. My machine says I have the newest version.

I think I need more help, I'm getting lost and confused.I believe the STA driver is correct for your device. Let's see what's loaded and what's not:```
lsmod | grep -e b43 -e wl
```Is *wl* loaded? If not, load it:```
sudo modprobe wl
```And look for errors or messages:```
dmesg | grep -e wlan -e eth1 -e wl
```Thanks.

---

### Post by ebnh on 2012-10-01
I dont know if this will help, but I read hundreds of posts and tried lots of fixes without success- usb detected but no wlan.  I finally downloaded the 12.04 precise image and did a clean install - the package has all the drivers to find the usb devices.  The wifi airlink 101 usb - compaq was immediately recognized and connected.  The upgrade from 10.4 to 12.04 left something behind.

I did have to perform sudo shutdown now -P once after the install to get the shutdown button to work.  goog luck.

---

### Post by 8lackie on 2012-10-01
[FONT=verdana,sans-serif]Thanks guys for responding. I'm sorry to be a pain in the butt.

I get:
[B]blackie@sherpa:~$ lsmod | grep -e b43 -e wl
[COLOR=Red]wl[/COLOR][/B] [B]                   2646601  0 
lib80211               14040  2 lib80211_crypt_tkip,[COLOR=Red]wl[/COLOR]
blackie@sherpa:~$[/B]

I'm not sure what this actually says....but took a chance it says wl is loaded so I ran dmesg | grep -e wlan -e eth1 -e wl
and I get:
[/FONT]
[FONT=verdana,sans-serif][COLOR=#000066][FONT=verdana,sans-serif][B]blackie@sherpa:~$ lsmod | grep -e b43 -e wl
wl                   2646601  0 
lib80211               14040  2 lib80211_crypt_tkip,wl
blackie@sherpa:~$ dmesg | grep -e wlan -e eth1 -e wl
[   20.799227] wl: module license 'MIXED/Proprietary' taints kernel.
[   20.989985] wl 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   20.990045] wl 0000:01:00.0: setting latency timer to 64
[   21.338123] eth1: Broadcom BCM4315 802.11 Hybrid Wireless Controller 5.100.82.38
[   22.716619] ADDRCONF(NETDEV_UP): eth1: link is not ready
blackie@sherpa:~$ 

[/B][COLOR=Black]What should be the next step?[/COLOR][/FONT][/COLOR]



[/FONT]

---

### Post by chili555 on 2012-10-04
You now have a wireless interface *eth1*. Does it scan?```
sudo iwlist eth1 scan
```Is the switch set correctly?```
rfkill list all
```If you are not hard- or soft-blocked and it sees networks, you ought to see networks when you click the Network Manager icon.

---

### Post by 8lackie on 2012-10-04
[COLOR=#000066][FONT=verdana,sans-serif][COLOR=Black]This is what I get.
Yes I do see networks. But then I always have. Yet I still get "authentication required" over and over but no connection. Frustrating!


[/COLOR][B]blackie@sherpa:~$ sudo iwlist eth1 scan
[sudo] password for blackie: 
eth1      Scan completed :
          Cell 01 - Address: 5C:35:3B:34:F8:D2
                    ESSID:"cbn-4F8CE"
                    Mode:Managed
                    Frequency:2.422 GHz (Channel 3)
                    Quality:5/5  Signal level:-39 dBm  Noise level:-92 dBm
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD960050F204104A00011010440001021057000101103B00010310470010630412531019200612285C353B34F8D21021001B5265616C74656B2053656D69636F6E647563746F7220436F72702E1023000752544C387878781024000D45562D323031302D30392D32301042000F3132333435363738393031323334371054000800060050F20400011011000643424E5F4150100800020086
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
          Cell 02 - Address: 00:18:F3:E6:0F:D0
                    ESSID:"WebSTAR"
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:1/5  Signal level:-85 dBm  Noise level:-92 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
          Cell 03 - Address: 10:9A:DD:8B:E3:E9
                    ESSID:"Jerry's Network"
                    Mode:Managed
                    Frequency:2.457 GHz (Channel 10)
                    Quality:4/5  Signal level:-58 dBm  Noise level:-92 dBm
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
          Cell 04 - Address: 16:9A:DD:8B:E3:E9
                    ESSID:"Jerry's Guest Network"
                    Mode:Managed
                    Frequency:2.457 GHz (Channel 10)
                    Quality:4/5  Signal level:-58 dBm  Noise level:-92 dBm
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s

blackie@sherpa:~$ rfkill list all
0: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: acer-wireless: Wireless LAN
    Soft blocked: no
    Hard blocked: no
blackie@sherpa:~$ 

[/B][/FONT][/COLOR]

---

### Post by Bucky Ball on 2012-10-04
@ 8lackie: I'll ask once again, this time with this from the forum Code of Conduct:

> Use color and font properties for highlighting portions of your text,  and not for all of the text in your post. Please use the default font  color and properties unless you need to highlight or draw attention to a  part of your post. ALL CAPS is interpreted as screaming. Funky  non-uniform font size/color is  difficult for those who are visually impaired. If you are having  problems with reading the font, please adjust your browser. There are good reasons to avoid the excessive use of colour. The excessive use of colour is discouraged. If you want to highlight code, put it between code tags. That is what they are for. They make code easier (not harder) to read and navigate.

BB

---

### Post by 8lackie on 2012-10-04
Will do. Sorry, it is a bad habit because I find bold easier to read. Apologies.

---

### Post by chili555 on 2012-10-05
> Cell 01 - Address: 5C:35:3B:34:F82
ESSID:"cbn-4F8CE"
Mode:Managed
Frequency:2.422 GHz (Channel 3)
Quality:5/5 Signal level:-39 dBm Noise level:-92 dBm
IE: IEEE 802.11i/[COLOR="Red"]WPA2 Version 1[/COLOR]
Group Cipher : TKIP
Pairwise Ciphers (2) : TKIP CCMP
Authentication Suites (1) : PSK
IE:[COLOR="Red"] WPA Version 1[/COLOR]
Group Cipher : TKIP
Pairwise Ciphers (2) : TKIP CCMP
Authentication Suites (1) : PSK
Encryption keyn
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
48 Mb/s; 54 Mb/sI think you will have better luck with the routers set to WPA2 only, not mixed mode WPA and WPA2.

---

### Post by Bucky Ball on 2012-10-05
> **8lackie said:**
> Will do. Sorry, it is a bad habit because I find bold easier to read. Apologies.

All good. ;)

---

### Post by 8lackie on 2012-10-06
My options on my wireless connection are:
none
WEP 40/128-bit Key (Hex or ASCII)
WEP 128-bit Passphrase
LEAP
Dynamic WEP (802.1x)
WPA & WPA2 Personal
WPA & WPA2 Enterprise

---

### Post by chili555 on 2012-10-06
> **8lackie said:**
> My options on my wireless connection are:
none
WEP 40/128-bit Key (Hex or ASCII)
WEP 128-bit Passphrase
LEAP
Dynamic WEP (802.1x)
WPA & WPA2 Personal
WPA & WPA2 EnterpriseGreat; we'll *have* to find a fix.> Now I've managed to install Broadcom STA wireless driver...not sure how I did itHow _did_ you do it? Did you compile the version you downloaded from Broadcom? If so, we'll probably need to remove it and start again.

---

### Post by 8lackie on 2012-10-06
.....don't know. I followed some the links around here and tried doing stuff. But I was working pretty blind as I was not sure what I was doing I'd type in the commands and then return to trying to start my wireless. Sadly clueless. 
Ok, so I should remove the Broadcom STA and reinstall it? What are the lines I need to type in?
Thanks again for your help and patience. You've been kind to take my idiocy on as a project:-\"

---

### Post by chili555 on 2012-10-06
No worries; we were all beginners at one time. Even me and even Linus! Let's dig deeper:```
sudo dpkg -s ndiswrapper-common
```If it what we hope it is, it will say, in part:> Package: ndiswrapper-common
Status: install ok installed
Priority: optional
Section: misc
Installed-Size: 71
Maintainer: [COLOR="Red"]Ubuntu Developers[/COLOR] <ubuntu-devel-discuss@lists.ubuntu.com>


---

### Post by 8lackie on 2012-10-07
[FONT=verdana,sans-serif]A bit of progress....

Package `ndiswrapper-common' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.

 then ran sudo apt-get install ndiswrapper-common and I get:

[/FONT]
[FONT=verdana,sans-serif][COLOR=#000066][FONT=verdana,sans-serif][COLOR=Black]Package: ndiswrapper-common
Status: install ok installed
Priority: optional
Section: misc
Installed-Size: 71
Maintainer: Ubuntu Developers <[EMAIL="ubuntu-devel-discuss@lists.ubuntu.com"]ubuntu-devel-discuss@lists.ubuntu.com[/EMAIL]>
Architecture: all
Source: ndiswrapper
Version: 1.57-1ubuntu1
Replaces: ndiswrapper-utils
Suggests: ndiswrapper-source
Description: Common scripts required to use the utilities for ndiswrapper
 Some vendors do not release specifications of the hardware or provide a
 Linux driver for their wireless network cards. This project implements
 Windows kernel API and NDIS (Network Driver Interface Specification) API
 within Linux kernel. A Windows driver for wireless network card is then
 linked to this implementation so that the driver runs natively, as though
 it is in Windows, without binary emulation.
 .
 This package contains wrapper scripts to call out to the proper
 versions of whatever -utils-X.X package is installed.
Original-Maintainer: Julian Andres Klode <[EMAIL="jak@debian.org"]jak@debian.org[/EMAIL]>
Homepage: [http://ndiswrapper.sourceforge.net/](http://ndiswrapper.sourceforge.net/)
blackie@sherpa:~$ [/COLOR]

[/FONT][/COLOR]

[/FONT]

---

### Post by chili555 on 2012-10-07
I guess that's what I get for trying to answer 27 posts while on vacation: confused! Sorry about my error. Please try:```
sudo dpkg -s bcmwl-kernel-source
```No matter what the answer, do not install anything further until we examine the result.

---

### Post by 8lackie on 2012-10-07
On vacation!? Jeepers, I'm grateful you even look at email.

Here's what I get per "sudo dpkg -s bcmwl-kernel-source"

[FONT=verdana,sans-serif]blackie@sherpa:~$ sudo dpkg -s bcmwl-kernel-source
[sudo] password for blackie: 
Package: bcmwl-kernel-source
Status: install ok installed
Priority: optional
Section: admin
Installed-Size: 3176
Maintainer: Ubuntu Developers <[EMAIL="ubuntu-devel-discuss@lists.ubuntu.com"]ubuntu-devel-discuss@lists.ubuntu.com[/EMAIL]>
Architecture: i386
Source: bcmwl
Version: 5.100.82.38+bdcom-0ubuntu6.1
Replaces: bcmwl-modaliases
Depends: dkms, linux-libc-dev, libc6-dev, linux-headers-generic-pae | linux-headers
Conflicts: bcmwl-modaliases
Description: Broadcom 802.11 Linux STA wireless driver source
 This package contains Broadcom 802.11 Linux STA wireless driver
 for use with Broadcom's BCM4311-, BCM4312-, BCM4313-, BCM4321-,
 BCM4322-, BCM43224-, and BCM43225-, BCM43227- and BCM43228-based
 hardware.
Modaliases: wl(pci:v000014E4d00000576sv*sd*bc*sc*i*, pci:v000014E4d00004311sv*sd*bc*sc*i*, pci:v000014E4d00004312sv*sd*bc*sc*i*, pci:v000014E4d00004313sv*sd*bc*sc*i*, pci:v000014E4d00004315sv*sd*bc*sc*i*, pci:v000014E4d00004328sv*sd*bc*sc*i*, pci:v000014E4d00004329sv*sd*bc*sc*i*, pci:v000014E4d0000432Asv*sd*bc*sc*i*, pci:v000014E4d0000432Bsv*sd*bc*sc*i*, pci:v000014E4d0000432Csv*sd*bc*sc*i*, pci:v000014E4d0000432Dsv*sd*bc*sc*i*, pci:v000014E4d00004353sv*sd*bc*sc*i*, pci:v000014E4d00004357sv*sd*bc*sc*i*, pci:v000014E4d00004358sv*sd*bc*sc*i*, pci:v000014E4d00004359sv*sd*bc*sc*i*, pci:v000014E4d0000435Asv*sd*bc*sc*i*, pci:v000014E4d00004727sv*sd*bc*sc*i*, pci:v000014E4d0000A99Dsv*sd*bc*sc*i*)
Original-Maintainer: Alberto Milone <[EMAIL="alberto.milone@canonical.com"]alberto.milone@canonical.com[/EMAIL]>
blackie@sherpa:~$ 
[/FONT]

---

### Post by chili555 on 2012-10-08
Ah, good. That's the STA driver we want...maybe.

Your Broadcom 4312 is one of those devices that has at least three methods to get it going. STA is one and evidently, not ideal. Hook up the ethernet temporarily and do:```
sudo apt-get install firmware-b43-lpphy-installer
sudo modprobe -r wl
sudo modprobe b43
```Any improvement? If so, we'll need to do some corrective surgery.

---

### Post by 8lackie on 2012-10-08
nix! No improvement. I first line installed firmware b43 etc.
When I ran the next two modprob lines, Nothing happened...or at least not that was evident

[FONT=verdana,sans-serif]blackie@sherpa:~$ sudo apt-get install firmware-b43 lpphy-installer
[sudo] password for blackie: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package firmware-b43
E: Unable to locate package lpphy-installer
blackie@sherpa:~$ sudo apt-get install firmware-b43-lpphy-installer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  firmware-b43-lpphy-installer
0 upgraded, 1 newly installed, 0 to remove and 33 not upgraded.
Need to get 3,390 B of archives.
After this operation, 34.8 kB of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/multiverse firmware-b43-lpphy-installer all 1:015-9 [3,390 B]
Fetched 3,390 B in 0s (9,124 B/s)                         
Selecting previously unselected package firmware-b43-lpphy-installer.
(Reading database ... 239888 files and directories currently installed.)
Unpacking firmware-b43-lpphy-installer (from .../firmware-b43-lpphy-installer_1%3a015-9_all.deb) ...
Setting up firmware-b43-lpphy-installer (1:015-9) ...
No chroot environment found. Starting normal installation
--2012-10-08 23:13:59--  [http://downloads.openwrt.org/sources/broadcom-wl-4.178.10.4.tar.bz2](http://downloads.openwrt.org/sources/broadcom-wl-4.178.10.4.tar.bz2)
Resolving [downloads.openwrt.org]("http://downloads.openwrt.org") ([downloads.openwrt.org]("http://downloads.openwrt.org"))... 78.24.191.177
Connecting to [downloads.openwrt.org]("http://downloads.openwrt.org") ([downloads.openwrt.org]("http://downloads.openwrt.org"))|78.24.191.177|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 5986780 (5.7M) [application/octet-stream]
Saving to: `broadcom-wl-4.178.10.4.tar.bz2'

100%[======================================>] 5,986,780   2.31M/s   in 2.5s    

2012-10-08 23:14:02 (2.31 MB/s) - `broadcom-wl-4.178.10.4.tar.bz2' saved [5986780/5986780]

Deleting old extracted firmware...
broadcom-wl-4.178.10.4/
broadcom-wl-4.178.10.4/config/
broadcom-wl-4.178.10.4/config/wlconfig_nomimo
broadcom-wl-4.178.10.4/config/wlconfig_lx_router_apsta_1chipG
broadcom-wl-4.178.10.4/config/wlconfig_lx_wl_sdstd
broadcom-wl-4.178.10.4/config/wlconfig_lx_shared
broadcom-wl-4.178.10.4/config/diffupdate.sh
broadcom-wl-4.178.10.4/config/wlconfig_lx_router_ap_1chipG
broadcom-wl-4.178.10.4/config/wlconfig_lx_router_ap
broadcom-wl-4.178.10.4/config/wlconfig_lx_router_ap_sdstd
broadcom-wl-4.178.10.4/config/[wl.mk]("http://wl.mk")
broadcom-wl-4.178.10.4/config/wltunable_lx_router.h
broadcom-wl-4.178.10.4/config/wlconfig_lx_router_sta
broadcom-wl-4.178.10.4/config/wl_default
broadcom-wl-4.178.10.4/config/wltunable_lx_router_1chipG.h
broadcom-wl-4.178.10.4/config/wl_hnd
broadcom-wl-4.178.10.4/config/wlconfig_lx_router_sta_1chipG
broadcom-wl-4.178.10.4/config/wlconfig_lx_router_apsta
broadcom-wl-4.178.10.4/config/wlconfig_apdef
broadcom-wl-4.178.10.4/README
broadcom-wl-4.178.10.4/linux/
broadcom-wl-4.178.10.4/linux/wl_sta.o
broadcom-wl-4.178.10.4/linux/wl.o
broadcom-wl-4.178.10.4/linux/wl_ap.o
broadcom-wl-4.178.10.4/linux/wl_apsta.o
This file is recognised as:
  filename   :  wl_apsta.o
  version    :  478.104
  MD5        :  bb8537e3204a1ea5903fe3e66b5e2763
Extracting b43/ucode5.fw
Extracting b43/pcm5.fw
Extracting b43/b0g0bsinitvals5.fw
Extracting b43/a0g0bsinitvals5.fw
Extracting b43/b0g0initvals5.fw
Extracting b43/a0g1initvals5.fw
Extracting b43/a0g0initvals5.fw
Extracting b43/a0g1bsinitvals5.fw
Extracting b43/ucode9.fw
Extracting b43/a0g1initvals9.fw
Extracting b43/a0g0bsinitvals9.fw
Extracting b43/b0g0bsinitvals9.fw
Extracting b43/b0g0initvals9.fw
Extracting b43/a0g1bsinitvals9.fw
Extracting b43/a0g0initvals9.fw
Extracting b43/ucode11.fw
Extracting b43/n0bsinitvals11.fw
Extracting b43/n0absinitvals11.fw
Extracting b43/n0initvals11.fw
Extracting b43/ucode13.fw
Extracting b43/b0g0initvals13.fw
Extracting b43/a0g1bsinitvals13.fw
Extracting b43/a0g1initvals13.fw
Extracting b43/lp0bsinitvals13.fw
Extracting b43/b0g0bsinitvals13.fw
Extracting b43/lp0initvals13.fw
Extracting b43/ucode14.fw
Extracting b43/lp0initvals14.fw
Extracting b43/lp0bsinitvals14.fw
Extracting b43/ucode15.fw
Extracting b43/lp0bsinitvals15.fw
Extracting b43/lp0initvals15.fw
Extracting b43/ucode16.fw
Extracting b43/n0bsinitvals16.fw
Extracting b43/sslpn0initvals16.fw
Extracting b43/n0initvals16.fw
Extracting b43/lp0initvals16.fw
Extracting b43/sslpn0bsinitvals16.fw
Extracting b43/lp0bsinitvals16.fw[/FONT]

---

### Post by chili555 on 2012-10-08
> When I ran the next two modprob lines, Nothing happened...or at least not that was evidentPlease run them again and let me see:```
iwconfig
sudo iwlist wlan0 scan
```Does it try to connect?

---

### Post by 8lackie on 2012-10-09
[COLOR=#000066][FONT=verdana,sans-serif][COLOR=Black]Yes, It tries to connect.  I get the "wireless network authentication required" Click, and it tries and fails and comes back and wants authentication again. Little icon comes up says im offline.

blackie@sherpa:~$ iwconfig
lo        no wireless extensions.

eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:219  Noise level:199
          Rx invalid nwid:0  invalid crypt:4  invalid misc:0

eth0      no wireless extensions.

blackie@sherpa:~$ sudo iwlist wlan0 scan
[sudo] password for blackie: 
Sorry, try again.
[sudo] password for blackie: 
wlan0     Interface doesn't support scanning.

blackie@sherpa:~$ [/COLOR][/FONT][/COLOR]

---

### Post by chili555 on 2012-10-09
If eth1 is showing as your wireless interface, then *wl*, possibly the wrong driver, is still loaded. Please try again:```
sudo modprobe -r wl
sudo modprobe b43
```Verify that *wl* is NOT loaded and *b43* is:```
lsmod | grep -e wl -e b43
```ONLY b43 should be listed. Now see if your interface is wlan0:```
iwconfig
```Now does it try to connect?

---

### Post by 8lackie on 2012-10-09
[FONT=verdana,sans-serif]I don't think I see what I'm supposed to.....? I'm guessing b43  0 means it's not loaded?


blackie@sherpa:~$ sudo modprobe -r wl
[sudo] password for blackie: 
blackie@sherpa:~$ sudo modprobe -r wl
blackie@sherpa:~$ sudo modprobe b43
blackie@sherpa:~$ lsmod | grep -e wl -e b43
b43                   342643  0 
mac80211              436455  1 b43
cfg80211              178679  2 b43,mac80211
bcma                   25651  1 b43
ssb                    50691  1 b43
blackie@sherpa:~$ iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          
eth0      no wireless extensions.

blackie@sherpa:~$ 
[/FONT]

---

### Post by chili555 on 2012-10-09
b43 *is* loaded correctly. You now have an interface wlan0. Does it scan?```
sudo iwlist wlan0 scan
```Does it try to connect?

---

### Post by 8lackie on 2012-10-10
Crumbs!

I get "Interface does not support scanning"

---

### Post by chili555 on 2012-10-10
Is b43 still loaded and not wl? Do you need to repeat the sequence first?```
sudo modprobe -r wl
sudo modprobe b43
```

---

### Post by 8lackie on 2012-10-10
Now I'm getting beyond confused (if that is possible:)) I'm not sure what you're asking me.... I ran these two commands and get:

[FONT=verdana,sans-serif]blackie@sherpa:~$ sudo modprobe -r wl
[sudo] password for blackie: 
blackie@sherpa:~$ sudo modprobe b43
blackie@sherpa:~$ suod modprobe -r wl
No command 'suod' found, did you mean:
 Command 'sudo' from package 'sudo' (main)
 Command 'sudo' from package 'sudo-ldap' (universe)
suod: command not found
blackie@sherpa:~$ sudo modprobe b43
blackie@sherpa:~$ [/FONT]

This doesn't look good I suspect

---

### Post by chili555 on 2012-10-10
> **8lackie said:**
> Now I'm getting beyond confused (if that is possible:)) I'm not sure what you're asking me.... I ran these two commands and get:

[FONT=verdana,sans-serif]blackie@sherpa:~$ sudo modprobe -r wl
[sudo] password for blackie: 
blackie@sherpa:~$ sudo modprobe b43
blackie@sherpa:~$ suod modprobe -r wl
No command 'suod' found, did you mean:
 Command 'sudo' from package 'sudo' (main)
 Command 'sudo' from package 'sudo-ldap' (universe)
suod: command not found
blackie@sherpa:~$ sudo modprobe b43
blackie@sherpa:~$ [/FONT]

This doesn't look good I suspectIt looks fine. *Now* do you have an interface wlan0?```
iwconfig
```Does it scan and connect?```
sudo iwlist wlan0 scan
```

---

### Post by 8lackie on 2012-10-10
blackie@sherpa:~$ iwconfig
lo        no wireless extensions.

eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:0  Noise level:0
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

eth0      no wireless extensions.

blackie@sherpa:~$ sudo iwlist wanl0 scan
[sudo] password for blackie: 
Sorry, try again.
[sudo] password for blackie: 
wanl0     Interface doesn't support scanning.

blackie@sherpa:~$ sudo modprobe -r wl
blackie@sherpa:~$ sudo modprobe b43
blackie@sherpa:~$

---

### Post by chili555 on 2012-10-10
We are getting nowhere fast. What I am trying to find out is whether the b43 driver and lp-phy firmware (wlan0) will drive your device better than the STA driver (eth1). You have not executed the commands in the order I requested for good reason and haven't even typed them correctly:> blackie@sherpa:~$ sudo iwlist [COLOR="Red"]wanl0[/COLOR] scan
[sudo] password for blackie:
Sorry, try again.
[sudo] password for blackie:
wanl0 Interface doesn't support scanning.Please help me help you.

---

### Post by 8lackie on 2012-10-11
I'm sorry. Yes you're right. I think doing this piecemeal is throwing me some. I'll go through what you've written and be more attentive to correct sequence and I'll get better results. I'll be right back....

---

### Post by 8lackie on 2012-10-11
Ok I ran everything again per your instructions being careful to follow the sequence and avoiding sloppy typing.

blackie@sherpa:~$ sudo dpkg -s bcmwl-kernel-source
[sudo] password for blackie: 
Package: bcmwl-kernel-source
Status: install ok installed
Priority: optional
Section: admin
Installed-Size: 3176
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: i386
Source: bcmwl
Version: 5.100.82.38+bdcom-0ubuntu6.1
Replaces: bcmwl-modaliases
Depends: dkms, linux-libc-dev, libc6-dev, linux-headers-generic-pae | linux-headers
Conflicts: bcmwl-modaliases
Description: Broadcom 802.11 Linux STA wireless driver source
 This package contains Broadcom 802.11 Linux STA wireless driver
 for use with Broadcom's BCM4311-, BCM4312-, BCM4313-, BCM4321-,
 BCM4322-, BCM43224-, and BCM43225-, BCM43227- and BCM43228-based
 hardware.
Modaliases: wl(pci:v000014E4d00000576sv*sd*bc*sc*i*, pci:v000014E4d00004311sv*sd*bc*sc*i*, pci:v000014E4d00004312sv*sd*bc*sc*i*, pci:v000014E4d00004313sv*sd*bc*sc*i*, pci:v000014E4d00004315sv*sd*bc*sc*i*, pci:v000014E4d00004328sv*sd*bc*sc*i*, pci:v000014E4d00004329sv*sd*bc*sc*i*, pci:v000014E4d0000432Asv*sd*bc*sc*i*, pci:v000014E4d0000432Bsv*sd*bc*sc*i*, pci:v000014E4d0000432Csv*sd*bc*sc*i*, pci:v000014E4d0000432Dsv*sd*bc*sc*i*, pci:v000014E4d00004353sv*sd*bc*sc*i*, pci:v000014E4d00004357sv*sd*bc*sc*i*, pci:v000014E4d00004358sv*sd*bc*sc*i*, pci:v000014E4d00004359sv*sd*bc*sc*i*, pci:v000014E4d0000435Asv*sd*bc*sc*i*, pci:v000014E4d00004727sv*sd*bc*sc*i*, pci:v000014E4d0000A99Dsv*sd*bc*sc*i*)
Original-Maintainer: Alberto Milone <alberto.milone@canonical.com>


blackie@sherpa:~$ lsmode | grep -e b43 -e wl
No command 'lsmode' found, did you mean:
 Command 'lsmod' from package 'module-init-tools' (main)
lsmode: command not found
blackie@sherpa:~$ lsmod | grep -e b43 -e wl
b43                   342643  0 
mac80211              436455  1 b43
cfg80211              178679  2 b43,mac80211
bcma                   25651  1 b43
ssb                    50691  1 b43

blackie@sherpa:~$ sudo modprobe wl
blackie@sherpa:~$ dmesg | grep -e eth1 -e wl
[   19.307637] wl: module license 'MIXED/Proprietary' taints kernel.
[   19.669623] wl 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   19.669648] wl 0000:01:00.0: setting latency timer to 64
[   20.059799] eth1: Broadcom BCM4315 802.11 Hybrid Wireless Controller 5.100.82.38
[   21.328539] ADDRCONF(NETDEV_UP): eth1: link is not ready
[  342.740348] wl 0000:01:00.0: PCI INT A disabled
[  361.957934] ADDRCONF(NETDEV_UP): wlan0: link is not ready
blackie@sherpa:~$ sudo iwlist eth1 scan
eth1      Interface doesn't support scanning.

blackie@sherpa:~$ rfkill list all
1: acer-wireless: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

blackie@sherpa:~$ sudo dpkg -s ndiswrapper-common
Package: ndiswrapper-common
Status: install ok installed
Priority: optional
Section: misc
Installed-Size: 71
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: all
Source: ndiswrapper
Version: 1.57-1ubuntu1
Replaces: ndiswrapper-utils
Suggests: ndiswrapper-source
Description: Common scripts required to use the utilities for ndiswrapper
 Some vendors do not release specifications of the hardware or provide a
 Linux driver for their wireless network cards. This project implements
 Windows kernel API and NDIS (Network Driver Interface Specification) API
 within Linux kernel. A Windows driver for wireless network card is then
 linked to this implementation so that the driver runs natively, as though
 it is in Windows, without binary emulation.
 .
 This package contains wrapper scripts to call out to the proper
 versions of whatever -utils-X.X package is installed.
Original-Maintainer: Julian Andres Klode <jak@debian.org>
Homepage: [http://ndiswrapper.sourceforge.net/](http://ndiswrapper.sourceforge.net/)
blackie@sherpa:~$ sudo dpkg -s bcmwl-kernel-source
Package: bcmwl-kernel-source
Status: install ok installed
Priority: optional
Section: admin
Installed-Size: 3176
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: i386
Source: bcmwl
Version: 5.100.82.38+bdcom-0ubuntu6.1
Replaces: bcmwl-modaliases
Depends: dkms, linux-libc-dev, libc6-dev, linux-headers-generic-pae | linux-headers
Conflicts: bcmwl-modaliases
Description: Broadcom 802.11 Linux STA wireless driver source
 This package contains Broadcom 802.11 Linux STA wireless driver
 for use with Broadcom's BCM4311-, BCM4312-, BCM4313-, BCM4321-,
 BCM4322-, BCM43224-, and BCM43225-, BCM43227- and BCM43228-based
 hardware.
Modaliases: wl(pci:v000014E4d00000576sv*sd*bc*sc*i*, pci:v000014E4d00004311sv*sd*bc*sc*i*, pci:v000014E4d00004312sv*sd*bc*sc*i*, pci:v000014E4d00004313sv*sd*bc*sc*i*, pci:v000014E4d00004315sv*sd*bc*sc*i*, pci:v000014E4d00004328sv*sd*bc*sc*i*, pci:v000014E4d00004329sv*sd*bc*sc*i*, pci:v000014E4d0000432Asv*sd*bc*sc*i*, pci:v000014E4d0000432Bsv*sd*bc*sc*i*, pci:v000014E4d0000432Csv*sd*bc*sc*i*, pci:v000014E4d0000432Dsv*sd*bc*sc*i*, pci:v000014E4d00004353sv*sd*bc*sc*i*, pci:v000014E4d00004357sv*sd*bc*sc*i*, pci:v000014E4d00004358sv*sd*bc*sc*i*, pci:v000014E4d00004359sv*sd*bc*sc*i*, pci:v000014E4d0000435Asv*sd*bc*sc*i*, pci:v000014E4d00004727sv*sd*bc*sc*i*, pci:v000014E4d0000A99Dsv*sd*bc*sc*i*)
Original-Maintainer: Alberto Milone <alberto.milone@canonical.com>

blackie@sherpa:~$ sudo apt-get install firmware-b43-lpphy-installer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
firmware-b43-lpphy-installer is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 15 not upgraded.
blackie@sherpa:~$ sudo modprobe -r wl
blackie@sherpa:~$ sudo modprobe b43
blackie@sherpa:~$ sudo modprobe -r wl
blackie@sherpa:~$ sudo modprobe b43
blackie@sherpa:~$ iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11bg  ESSIDoff/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS throff   Fragment throff
          Power Managementon
          
eth0      no wireless extensions.

blackie@sherpa:~$ sudo iwlist wlan0 scan
wlan0     Interface doesn't support scanning : Network is down

blackie@sherpa:~$ sudo modprobe -r wl
blackie@sherpa:~$ sudo modprobe b43
blackie@sherpa:~$ lsmod | grep -e wl -e b43
b43                   342643  0 
mac80211              436455  1 b43
cfg80211              178679  2 b43,mac80211
bcma                   25651  1 b43
ssb                    50691  1 b43
blackie@sherpa:~$ iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11bg  ESSIDoff/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS throff   Fragment throff
          Power Managementon
          
eth0      no wireless extensions.

blackie@sherpa:~$ sudo iwlist wlan0 scan
wlan0     Interface doesn't support scanning : Network is down

blackie@sherpa:~$ sudo modprobe -r wl
blackie@sherpa:~$ sudo modprobe b43
blackie@sherpa:~$ iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11bg  ESSIDoff/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS throff   Fragment throff
          Power Managementon
          
eth0      no wireless extensions.

blackie@sherpa:~$ sudo iwlist wlan0 scan
wlan0     Interface doesn't support scanning : Network is down

blackie@sherpa:~$

---

### Post by Bucky Ball on 2012-10-11
Have you tried a restart because this shows promise:

```
wlan0 Interface doesn't support scanning : Network is down
```Network down as opposed to up whereas before it was neither. 

Or try this to bring it up:

```
sudo ifup wlan0
```

I have been following this saga. Stick with it, both of you! ;)

---

### Post by 8lackie on 2012-10-11
Thanks, appreciate the encouragement, and cheering.

I tried a reboot and still no connection

I also tried: 
blackie@sherpa:~$ sudo ifup wlan0
Ignoring unknown interface wlan0=wlan0.
blackie@sherpa:~$ :cry:

---

### Post by wildmanne39 on 2012-10-11
Hi, I will try to help you while my good friend chili555 is off line.

Copy and paste this command in the terminal (ctrl+alt+t) please:
```
wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a text file in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back  and attach the netinfo.txt file.
Thanks

---

### Post by 8lackie on 2012-10-12
Thank you. Here is what I get:

---

### Post by wildmanne39 on 2012-10-12
Hi, I will keep this as simple as possible copy and paste the exact commands I give you into the terminal and watch for errors.

```
sudo apt-get purge bcmwl-kernel-source broadcom-sta-common broadcom-sta-source
```
Then:
```
sudo apt-get install b43-fwcutter firmware-b43-lpphy-installer
```
You will need a wire connection to the internet before running these commands.
Reboot
Thanks

---

### Post by 8lackie on 2012-10-12
I followed your instructions. Rebooted. Nothing seems to have changed. The machine still attempts to connect, and asks for the password and it does nothing but churn and tells me it can't connect.

blackie@sherpa:~$ sudo apt-get purge bcmwl-kernel-source broadcom-sta-common broadcom-sta-source
[sudo] password for blackie: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package broadcom-sta-common is not installed, so not removed
Package broadcom-sta-source is not installed, so not removed
The following packages were automatically installed and are no longer required:
  linux-headers-3.2.0-30 linux-headers-3.2.0-30-generic-pae dkms linux-headers-3.2.0-30-generic
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  bcmwl-kernel-source*
0 upgraded, 0 newly installed, 1 to remove and 15 not upgraded.
After this operation, 3,252 kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 239895 files and directories currently installed.)
Removing bcmwl-kernel-source ...
Removing all DKMS Modules
Done.
update-initramfs: deferring update (trigger activated)
Purging configuration files for bcmwl-kernel-source ...
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.2.0-31-generic

blackie@sherpa:~$ sudo apt-get install b43-fwcutter firmware-b43-lpphy-installer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
b43-fwcutter is already the newest version.
firmware-b43-lpphy-installer is already the newest version.
The following packages were automatically installed and are no longer required:
  linux-headers-3.2.0-30 linux-headers-3.2.0-30-generic-pae dkms linux-headers-3.2.0-30-generic
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 15 not upgraded.
blackie@sherpa:~$

---

### Post by wildmanne39 on 2012-10-12
Hi, remove the netinfo.text file from your home folder and run the script again and let's see what has changed since you ran my last commands.
Thanks

---

### Post by 8lackie on 2012-10-13
I hope this is helping. -Thanks

I see that the part where it talks about Wireless LAN soft and hard blocked has changed. Is this where the problem is?

oh yeah, and I don't know if this anything but now my "Wireless Network Authentication Required" window won't go away.

---

### Post by wildmanne39 on 2012-10-13
Hi, things are looking better, please do:
```
echo "blacklist acer_wmi" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
make sure your wireless switch is on and yes that is where the issue is at this time.
Thanks

---

### Post by 8lackie on 2012-10-13
blackie@sherpa:~$ echo "blacklist acer_wmi" | sudo tee -a /etc/modprobe.d/blacklist.conf
[sudo] password for blackie: 
blacklist acer_wmi
blackie@sherpa:~$

---

### Post by wildmanne39 on 2012-10-13
Hi, reboot please and tell us if it works if not post a new text file so we can see where your wireless is at now.
Thanks

---

### Post by 8lackie on 2012-10-13
Ok, this time i rebooted. I did it wireless. I'm not certain that helps but i thought it might seek a connection more quickly if I was not already on-line. It seemed to do no good however. Would there be any advantage to doing a clean install? 


*************** info trace ****************



**** uname -a ****


Linux sherpa 3.2.0-31-generic #50-Ubuntu SMP Fri Sep 7 16:17:36 UTC 2012 i686 i686 i386 GNU/Linux


**** lsb-release ****


DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04.1 LTS"


**** lspci ****


01:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
    Subsystem: Foxconn International, Inc. T77H106.00 Wireless Half-size Mini PCIe Card [105b:e01b]
    Kernel driver in use: b43-pci-bridge
--
03:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR8132 Fast Ethernet [1969:1062] (rev c0)
    Subsystem: Acer Incorporated [ALI] Device [1025:022f]
    Kernel driver in use: atl1c


**** lsusb ****


Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 046d:c51b Logitech, Inc. V220 Cordless Optical Mouse for Notebooks
Bus 001 Device 005: ID 04f2:b175 Chicony Electronics Co., Ltd 4-Port Hub


**** iwconfig ****


wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          


**** rfkill ****


0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no


**** lsmod ****


Module                  Size  Used by
joydev                 17393  0 
snd_hda_codec_realtek   174313  1 
snd_hda_intel          32765  3 
snd_hda_codec         109562  2 snd_hda_codec_realtek,snd_hda_intel
arc4                   12473  2 
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80845  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
b43                   342643  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
uvcvideo               67203  0 
videodev               86588  1 uvcvideo
mac80211              436455  1 b43
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
psmouse                96619  0 
serio_raw              13027  0 
bnep                   17830  2 
rfcomm                 38139  0 
parport_pc             32114  0 
bluetooth             158438  10 bnep,rfcomm
ppdev                  12849  0 
i915                  414939  3 
cfg80211              178679  2 b43,mac80211
snd                    62064  15 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm_kms_helper         45466  1 i915
drm                   197692  4 i915,drm_kms_helper
bcma                   25651  1 b43
binfmt_misc            17292  1 
soundcore              14635  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
i2c_algo_bit           13199  1 i915
video                  19068  1 i915
wmi                    18744  0 
mac_hid                13077  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
usbhid                 41906  0 
hid                    77367  1 usbhid
ssb                    50691  1 b43
atl1c                  36718  0 


**** nm-tool ****



NetworkManager Tool

State: connecting

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            atl1c
  State:             unavailable
  Default:           no
  HW Address:        <MAC address removed>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         off


- Device: wlan0  [cbn-4F8CE] ---------------------------------------------------
  Type:              802.11 WiFi
  Driver:            b43
  State:             connecting (configuring)
  Default:           no
  HW Address:        <MAC address removed>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    airspan:         Infra, <MAC address removed>, Freq 2452 MHz, Rate 11 Mb/s, Strength 25
    WebSTAR:         Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 27
    dlink:           Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 22 WPA WPA2
    cbn-4F8CE:       Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 100 WPA WPA2




**** NetworkManager.state ****



[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true


**** NetworkManager.conf ****


[main]
plugins=ifupdown,keyfile
dns=dnsmasq

[ifupdown]
managed=false


**** NetworkManager.conf-10.04 ****




**** interfaces ****


auto lo
iface lo inet loopback



**** iwlist ****


wlan0     Scan completed :
          Cell 01 - Address: <MAC address removed>
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=33/70  Signal level=-77 dBm  
                    Encryption key:off
                    ESSID:"airspan"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Mode:Master
                    Extra:tsf=000002379d41f2eb
                    Extra: Last beacon: 3672ms ago
                    IE: Unknown: 00076169727370616E
                    IE: Unknown: 010482040B16
                    IE: Unknown: 030109
                    IE: Unknown: 050400010000
                    IE: Unknown: DF20011E0000000002660902FC080000000000000000000000000000000000000000
          Cell 02 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"dlink"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000066da94529
                    Extra: Last beacon: 3880ms ago
                    IE: Unknown: 0005646C696E6B
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 32080C1218243048606C
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=-11 dBm  
                    Encryption key:on
                    ESSID:"cbn-4F8CE"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000066d7d5176
                    Extra: Last beacon: 1064ms ago
                    IE: Unknown: 000963626E2D3446384345
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030101
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0104
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1A6E181EFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601050000000000000000000000000000000000000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C336E181EFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3401050000000000000000000000000000000000000000
                    IE: Unknown: DD0600E04C020160
                    IE: Unknown: DD130050F204104A00011010440001021057000101



**** resolv ****


# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.0.1


**** blacklist.conf ****


# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp

# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac
blacklist acer_wmi


**** dmesg ****


[   89.912156] wlan0: authenticate with <MAC address removed> (try 1)
[   89.913775] wlan0: authenticated
[   89.916714] wlan0: associate with <MAC address removed> (try 1)
[   89.919238] wlan0: RX ReassocResp from <MAC address removed> (capab=0x411 status=0 aid=2)
[   89.919250] wlan0: associated
[   89.937873] wlan0: disassociated from <MAC address removed> (Reason: 14)
[   89.952705] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  136.463884] wlan0: authenticate with <MAC address removed> (try 1)
[  136.465468] wlan0: authenticated
[  136.466890] wlan0: associate with <MAC address removed> (try 1)
[  136.469391] wlan0: RX ReassocResp from <MAC address removed> (capab=0x411 status=0 aid=2)
[  136.469403] wlan0: associated
[  136.484340] wlan0: disassociated from <MAC address removed> (Reason: 14)
[  136.500628] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  137.885417] wlan0: authenticate with <MAC address removed> (try 1)
[  137.887163] wlan0: authenticated
[  137.889031] wlan0: associate with <MAC address removed> (try 1)
[  137.892536] wlan0: RX ReassocResp from <MAC address removed> (capab=0x411 status=0 aid=2)
[  137.892548] wlan0: associated
[  138.889200] wlan0: disassociated from <MAC address removed> (Reason: 14)
[  138.912666] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  140.314669] wlan0: authenticate with <MAC address removed> (try 1)
[  140.316270] wlan0: authenticated
[  140.317818] wlan0: associate with <MAC address removed> (try 1)
[  140.320327] wlan0: RX ReassocResp from <MAC address removed> (capab=0x411 status=0 aid=2)
[  140.320340] wlan0: associated
[  140.336220] wlan0: disassociated from <MAC address removed> (Reason: 14)
[  140.360663] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  141.757128] wlan0: authenticate with <MAC address removed> (try 1)
[  141.758763] wlan0: authenticated
[  141.759818] wlan0: associate with <MAC address removed> (try 1)
[  141.762377] wlan0: RX ReassocResp from <MAC address removed> (capab=0x411 status=0 aid=2)
[  141.762391] wlan0: associated
[  141.776734] wlan0: disassociated from <MAC address removed> (Reason: 14)
[  141.792645] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  143.181189] wlan0: authenticate with <MAC address removed> (try 1)
[  143.183512] wlan0: authenticated
[  143.185056] wlan0: associate with <MAC address removed> (try 1)
[  143.187593] wlan0: RX ReassocResp from <MAC address removed> (capab=0x411 status=0 aid=2)
[  143.187606] wlan0: associated
[  143.204649] wlan0: disassociated from <MAC address removed> (Reason: 14)
[  143.224525] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  144.616668] wlan0: authenticate with <MAC address removed> (try 1)
[  144.618248] wlan0: authenticated
[  144.619876] wlan0: associate with <MAC address removed> (try 1)
[  144.622435] wlan0: RX ReassocResp from <MAC address removed> (capab=0x411 status=0 aid=2)
[  144.622447] wlan0: associated
[  144.635716] wlan0: disassociated from <MAC address removed> (Reason: 14)
[  144.656659] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  146.053178] wlan0: authenticate with <MAC address removed> (try 1)
[  146.054757] wlan0: authenticated
[  146.056529] wlan0: associate with <MAC address removed> (try 1)
[  146.059026] wlan0: RX ReassocResp from <MAC address removed> (capab=0x411 status=0 aid=2)
[  146.059037] wlan0: associated
[  146.075897] wlan0: disassociated from <MAC address removed> (Reason: 14)
[  146.108461] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  147.499798] wlan0: authenticate with <MAC address removed> (try 1)
[  147.501439] wlan0: authenticated
[  147.503063] wlan0: associate with <MAC address removed> (try 1)
[  147.505636] wlan0: RX ReassocResp from <MAC address removed> (capab=0x411 status=0 aid=2)
[  147.505649] wlan0: associated
[  147.519911] wlan0: disassociated from <MAC address removed> (Reason: 14)
[  147.536710] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  148.924344] wlan0: authenticate with <MAC address removed> (try 1)
[  148.925939] wlan0: authenticated
[  148.927543] wlan0: associate with <MAC address removed> (try 1)
[  148.930063] wlan0: RX ReassocResp from <MAC address removed> (capab=0x411 status=0 aid=2)
[  148.930075] wlan0: associated
[  148.944977] wlan0: disassociated from <MAC address removed> (Reason: 14)
[  148.960622] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  150.349368] wlan0: authenticate with <MAC address removed> (try 1)
[  150.350963] wlan0: authenticated
[  150.352608] wlan0: associate with <MAC address removed> (try 1)
[  150.355146] wlan0: RX ReassocResp from <MAC address removed> (capab=0x411 status=0 aid=2)
[  150.355158] wlan0: associated
[  150.371650] wlan0: disassociated from <MAC address removed> (Reason: 14)
[  150.396630] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  151.791497] wlan0: authenticate with <MAC address removed> (try 1)
[  151.793078] wlan0: authenticated
[  151.794669] wlan0: associate with <MAC address removed> (try 1)
[  151.797210] wlan0: RX ReassocResp from <MAC address removed> (capab=0x411 status=0 aid=2)
[  151.797222] wlan0: associated
[  151.812509] wlan0: disassociated from <MAC address removed> (Reason: 14)
[  151.836455] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  153.224230] wlan0: authenticate with <MAC address removed> (try 1)
[  153.225788] wlan0: authenticated
[  153.227334] wlan0: associate with <MAC address removed> (try 1)
[  153.229866] wlan0: RX ReassocResp from <MAC address removed> (capab=0x411 status=0 aid=2)
[  153.229879] wlan0: associated
[  153.245682] wlan0: disassociated from <MAC address removed> (Reason: 14)
[  153.268634] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  154.655157] wlan0: authenticate with <MAC address removed> (try 1)
[  154.656788] wlan0: authenticated
[  154.658302] wlan0: associate with <MAC address removed> (try 1)
[  154.660823] wlan0: RX ReassocResp from <MAC address removed> (capab=0x411 status=0 aid=2)
[  154.660835] wlan0: associated
[  154.677562] wlan0: disassociated from <MAC address removed> (Reason: 14)
[  154.696741] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  156.082668] wlan0: authenticate with <MAC address removed> (try 1)
[  156.084258] wlan0: authenticated
[  156.085700] wlan0: associate with <MAC address removed> (try 1)
[  156.088523] wlan0: RX ReassocResp from <MAC address removed> (capab=0x411 status=0 aid=2)
[  156.088535] wlan0: associated
[  156.105286] wlan0: disassociated from <MAC address removed> (Reason: 14)
[  156.120634] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  157.508956] wlan0: authenticate with <MAC address removed> (try 1)
[  157.512251] wlan0: authenticated
[  157.525189] wlan0: associate with <MAC address removed> (try 1)
[  157.527701] wlan0: RX ReassocResp from <MAC address removed> (capab=0x411 status=0 aid=2)
[  157.527714] wlan0: associated
[  157.544952] wlan0: disassociated from <MAC address removed> (Reason: 14)
[  157.564520] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  158.948669] wlan0: authenticate with <MAC address removed> (try 1)
[  158.950242] wlan0: authenticated
[  158.951256] wlan0: associate with <MAC address removed> (try 1)
[  158.953754] wlan0: RX ReassocResp from <MAC address removed> (capab=0x411 status=0 aid=2)
[  158.953767] wlan0: associated
[  158.967850] wlan0: disassociated from <MAC address removed> (Reason: 14)
[  158.988711] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  160.377397] wlan0: authenticate with <MAC address removed> (try 1)
[  160.378995] wlan0: authenticated
[  160.380592] wlan0: associate with <MAC address removed> (try 1)
[  160.383090] wlan0: RX ReassocResp from <MAC address removed> (capab=0x411 status=0 aid=2)
[  160.383103] wlan0: associated
[  160.399991] wlan0: disassociated from <MAC address removed> (Reason: 14)
[  160.432470] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  161.821049] wlan0: authenticate with <MAC address removed> (try 1)
[  161.822644] wlan0: authenticated
[  161.823769] wlan0: associate with <MAC address removed> (try 1)
[  161.826321] wlan0: RX ReassocResp from <MAC address removed> (capab=0x411 status=0 aid=2)
[  161.826333] wlan0: associated
[  161.840998] wlan0: disassociated from <MAC address removed> (Reason: 14)
[  161.856647] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  163.243267] wlan0: authenticate with <MAC address removed> (try 1)
[  163.244872] wlan0: authenticated
[  163.246389] wlan0: associate with <MAC address removed> (try 1)
[  163.248942] wlan0: RX ReassocResp from <MAC address removed> (capab=0x411 status=0 aid=2)
[  163.248955] wlan0: associated
[  163.263972] wlan0: disassociated from <MAC address removed> (Reason: 14)
[  163.280717] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  164.675413] wlan0: authenticate with <MAC address removed> (try 1)
[  164.677014] wlan0: authenticated
[  164.678572] wlan0: associate with <MAC address removed> (try 1)
[  164.681113] wlan0: RX ReassocResp from <MAC address removed> (capab=0x411 status=0 aid=2)
[  164.681126] wlan0: associated
[  164.697574] wlan0: disassociated from <MAC address removed> (Reason: 14)
[  164.720639] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  166.107079] wlan0: authenticate with <MAC address removed> (try 1)
[  166.108636] wlan0: authenticated
[  166.110377] wlan0: associate with <MAC address removed> (try 1)
[  166.112913] wlan0: RX ReassocResp from <MAC address removed> (capab=0x411 status=0 aid=2)
[  166.112926] wlan0: associated
[  166.127752] wlan0: disassociated from <MAC address removed> (Reason: 14)
[  166.148645] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  167.539807] wlan0: authenticate with <MAC address removed> (try 1)
[  167.541449] wlan0: authenticated
[  167.542703] wlan0: associate with <MAC address removed> (try 1)
[  167.545432] wlan0: RX ReassocResp from <MAC address removed> (capab=0x411 status=0 aid=2)
[  167.545443] wlan0: associated
[  167.564107] wlan0: disassociated from <MAC address removed> (Reason: 14)
[  167.584631] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  168.969155] wlan0: authenticate with <MAC address removed> (try 1)
[  168.970751] wlan0: authenticated
[  168.971759] wlan0: associate with <MAC address removed> (try 1)
[  168.974292] wlan0: RX ReassocResp from <MAC address removed> (capab=0x411 status=0 aid=2)
[  168.974304] wlan0: associated
[  170.048597] wlan0: disassociated from <MAC address removed> (Reason: 14)
[  170.077623] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  171.467630] wlan0: authenticate with <MAC address removed> (try 1)
[  171.469225] wlan0: authenticated
[  171.470913] wlan0: associate with <MAC address removed> (try 1)
[  171.473436] wlan0: RX ReassocResp from <MAC address removed> (capab=0x411 status=0 aid=2)
[  171.473449] wlan0: associated
[  171.487754] wlan0: disassociated from <MAC address removed> (Reason: 14)
[  171.508631] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  172.902647] wlan0: authenticate with <MAC address removed> (try 1)
[  172.904297] wlan0: authenticated
[  172.905401] wlan0: associate with <MAC address removed> (try 1)
[  172.907933] wlan0: RX ReassocResp from <MAC address removed> (capab=0x411 status=0 aid=2)
[  172.907946] wlan0: associated
[  172.924970] wlan0: disassociated from <MAC address removed> (Reason: 14)
[  172.944616] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  174.352274] wlan0: authenticate with <MAC address removed> (try 1)
[  174.353877] wlan0: authenticated
[  174.355580] wlan0: associate with <MAC address removed> (try 1)
[  174.358121] wlan0: RX ReassocResp from <MAC address removed> (capab=0x411 status=0 aid=2)
[  174.358133] wlan0: associated
[  174.372138] wlan0: disassociated from <MAC address removed> (Reason: 14)
[  174.388934] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  175.773290] wlan0: authenticate with <MAC address removed> (try 1)
[  175.774877] wlan0: authenticated
[  175.784307] wlan0: associate with <MAC address removed> (try 1)
[  175.786842] wlan0: RX ReassocResp from <MAC address removed> (capab=0x411 status=0 aid=2)
[  175.786855] wlan0: associated
[  175.803680] wlan0: disassociated from <MAC address removed> (Reason: 14)
[  175.820644] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  177.205276] wlan0: authenticate with <MAC address removed> (try 1)
[  177.206865] wlan0: authenticated
[  177.208057] wlan0: associate with <MAC address removed> (try 1)
[  177.213235] wlan0: RX ReassocResp from <MAC address removed> (capab=0x411 status=0 aid=2)
[  177.213248] wlan0: associated
[  177.228802] wlan0: disassociated from <MAC address removed> (Reason: 14)
[  177.252630] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  178.639819] wlan0: authenticate with <MAC address removed> (try 1)
[  178.641446] wlan0: authenticated
[  178.649113] wlan0: associate with <MAC address removed> (try 1)
[  178.651645] wlan0: RX ReassocResp from <MAC address removed> (capab=0x411 status=0 aid=2)
[  178.651658] wlan0: associated
[  178.669014] wlan0: disassociated from <MAC address removed> (Reason: 14)
[  178.688715] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  180.072652] wlan0: authenticate with <MAC address removed> (try 1)
[  180.272110] wlan0: authenticate with <MAC address removed> (try 2)
[  180.472121] wlan0: authenticate with <MAC address removed> (try 3)
[  180.672107] wlan0: authentication with <MAC address removed> timed out
[  183.117682] wlan0: direct probe to <MAC address removed> (try 1/3)
[  183.199331] wlan0: direct probe responded


**************** done ********************

---

### Post by wildmanne39 on 2012-10-13
Hi, is this the network you are trying to connect too?> cbn-4F8CE
if so please remove the dash between n and 4 and go into your router settings and change encryption from wpa/wpa2 to just wpa2 if you have that option then reboot.

I doubt it will help to do a clean install and we have made progress.
Thanks

---

### Post by 8lackie on 2012-10-13
Yikes!Ok I changed the name of the connection. Which it permitted me to do however in the pulldown the name never stopped having a dash in it. I change the name everywhere then rebooted. Twice.
As far as the wpa/wpa2 I do not have the choice of one or the other only "wpa&wpa2 personal" or "wpa&wpa2 enterprise"
My wife is running a thinkpad (wireless) she has no trouble w/her connection (not that that proves anything ) At any rate the cbn-4F8CE is hardcoded into the router/modem.
I'm in the Balkans at the moment so I'm not sure what is up inside the hardware the local internet co. provide, except that, even with 192.168.1.1 it won't permit me to get into it.

---

### Post by wildmanne39 on 2012-10-13
Hi, usually to change your router settings it is 192.168.0.1 but not always.
Thanks

---

### Post by 8lackie on 2012-10-13
right, my mistake. Ok well I can get to that page but have no login to get into it. I think I may be stuck using a cable while I'm here. Y'all have been great walking  me through this. Thank you Wild Man and thanks to Chilli555, hopefully I didn't drive you both nuts

---

### Post by wildmanne39 on 2012-10-13
Hi, no problem here. It is having issues at the moment with connecting because of encryption or the network name according to the dmesg report in the file.
Thanks

---

### Post by 8lackie on 2012-10-15
:)I'm at a local coffee house. It connects just fine here. Good to know. Why it won't connect at my house nor how to torque it into doing so is beyond me. At any rate, next time I will check sooner if connection location is a problem instead of pulling y'all through hoops with me. Thanks again. 8lackie:)

---

