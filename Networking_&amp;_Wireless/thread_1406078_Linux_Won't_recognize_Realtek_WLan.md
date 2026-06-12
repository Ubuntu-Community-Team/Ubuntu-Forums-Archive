---
title: "Linux Won't recognize Realtek WLan"
date: 2010-02-13
forum: Networking &amp; Wireless
---

### Post by bogan on 2010-02-13
Last year I installed a cut-down version of Ubuntu as a recovery disk, but it would not recognize the external HDD to which the backup program had saved it's output, so I ditched it.

Last month I installed Ubuntu 9.1, according to the articles in Computer Shopper, and it worked a treat recognizing the RAL wireless card  and connecting imediately without my having to do more than edit the connection settings. So I was able to use the Ubuntu updates OK. That was on a Medion MD8822 with Windows Vista.

Now I have bought a Medion MD8341 with Windows7, an Intel i3-530,3GB of DDR3 ram an nVidia G210, and a Realtek RTL8186 WLan adapter. I had trouble getting Windows to make and keep an Internet connection, but installing the latest drivers - a completely automatic process - got it running reasonably if not trouble-free.

Unfortunately,Ubuntu 9.1, installed from the same DVD, but on an external HDD - Ubuntu9.1 recognized it OK - would not, and will not recognize any Wireless connection at all.
[LEFT]
[/LEFT]
I assume the problem has nothing to do with the change from Windows Vista to Win7, except that the two computers have different WLan adapters; different drivers are needed and Ubuntu does not know how to use them.

 There is a Linux driver listed on the Realtek website, but I am quite horrified at the accounts I've read in the few threads I've found here, of  the appalling complexity of long commands needed to download and install one.

Trying to download the updated version of Firefox was bad enough - I  gave up at the fifth attempt after I got error messages that there was no Key,k as it was unable to connect with server.ubuntu.com or somesuch - so I am hoping someone knows a simpler means of getting the wireless connection to work - [B]anyone got any ideas?.
[/B] 
In the meantime I've got an ethernet connection going with a power plug adapter giving me access via the house mains circuit. Ubuntu recognizes that without adding a driver for the Realtek PCIe Family adapter.

[LEFT][ I know it is not the proper place, but I have just found that the Hot-Keys for Cut and Paste don't work in your compose window - the menu items do - and though Ctrl-Shift-X cut out the highlighted text, it also puts the whole text into Right-aligned and the Icons will not correct it - only for the current paragraph. ]

I only hope I will not need to update the nVidia drivers for Linux - so far, so good.
[/LEFT]

---

### Post by bogan on 2010-02-14
re:Additional info from bogan.

Having read the 'Stickies' at the top of this section - as I should have done beforehand - I can report after running the listed check command in a terminal, that none gave any response at all, except for 'iwlist scan'.

That listed Auto eth0 and lo with the note: 'No Wireless Connectivity' alongside each - no mention of a WLan device, nor wl3.

This rather suggests to me that the problem is not just that a specific new RTLWLan driver is needed; but I really do not know anything to do about it.

 The ndiswrapper site does not seem very accessible for a Linux novice.

---

### Post by chili555 on 2010-02-14
> I am quite horrified at the accounts I've read in the few threads I've found here, of the appalling complexity of long commands needed to download and install one.Dr. Chili is here to help. Just inhale some of this anesthetic and you'll feel just fine.

Seriously, let's see exactly what kind of wireless card you have. Please open a terminal and do:```
lspci -nn | grep Network
```That little pipe symbol | is over on the right side of my US keyboard, with \.

---

### Post by bogan on 2010-02-16
As I wrote above, with the RTL card, none of the commands in your Sticky gave any response connected with wireless, just returned to the prompt. To repeat, neither lspci, nor lshw, nor lsmod, nor iwconfig gave any response.
As I also wrote above, the wireless card fitted is a RealTek RTL8191su Wireless Lan USB2.0 Network Adapter. I had fitted an updated Win7 driver and today installed the latest version: 1086.10.206.2010 dated 06/02/2010.
Network Manager only listed 'Enable Networking' for Auto eth0 with a tick.
When I still had WLan problems in Win7, with the driver originally installed as new, I ordered a getnet USB Wlan Adapter, (ie. a dongle) and this worked well with WIn7.
With this device, Network Manager also listed 'Enable Wireless' with tick but would not connect despite editing in Network Connections. ( It would not allow me to alter the Gateway address from the default 0.0.0.0, changing it back as I pressed Apply.)

lshw -c network gave ( after the ethernet text):
description:Wireless interface
physical id: 3
logical name: wlan0
serial:00:1f:1f:67:27:3d
capabilities: ethernet physical wireless
configuration: broadcast=yes multicast=yeswireless=802.11bgn


iwconfig wlan0 gave:
wlan0   IEEE 802.11bgn ESSID:""
Mode:Managed  Frequency:2.412 GHz Access Point: Not-Associated
Tx-Power=11 dBm
Retry  long limit:7  RTS thr:off  Fragment thr:off
Power Management:on
Link Quality:0  Signal level:0  Noise level:0
Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0  Missed beacon:0

lspci  -nn | grep Network, and lsmod | grep wlan_module_name, gave no response:

I hope that may give you some clue as to what needs to be done with either card.
It appears that the getnet dongle is at least being recognised by Ubuntu 9.1; even if it will not connect to it. There is a Lunix driver on the CD, but the opague jargon and long complex commands in the readme file put me off trying to install it.
Unfortunately, I have swapped the dongle for a HomePlug Ethernet adapter which I am using now. However,I have ordered another and expect  it to come tomorrow.

Thanks for your response and sorry for the delay in my answer.
 ( I dont know how the Smilies got in inplace of colons!!)

---

### Post by chili555 on 2010-02-16
> Unfortunately, I have swapped the dongle for a HomePlug Ethernet adapter which I am using now. However,I have ordered another and expect it to come tomorrow.When you are ready to configure it, please let us see:```
iwconfig
lspci -nn
```I am sure we can get it going.

---

### Post by bogan on 2010-02-17
17/02/10 After installing an even newer driver for the RTL WLan Adapter, which works well in WIN7 but not in Linux.
I plugged in the new getnet dongle, after UBUNTU9.1 was running, as the book said, and after a fairly long pause the Network Manager added: 'Enable Wireless' with a tick, ( on RightTick) and 'Wireless Networks' with underneath, ghosted: 'disconnected'. With the Ethernet unplugged, the connection information' entry was ghosted. When it was plugged in, it showed only Auto eth0 as the Active Network Connection.

System/Admin/Network Tools, in the dropdown menu for Network device, showed: Loopback Interface(lo), Ethernet Interface(eth0), unknown Interface (wmaster0), and Wireless Interface (wlan1). The later showed IPv4 data as 0.0.0.0 and when highlighted could not be edited; so I altered  the entry in Network Connections from wlan0 to wlan1. It also showed Multicast as 'enabled' and MTU as '1500', ( as it did for eth0 ) whereas, for wmaster0 it showed disabled and 0.

However, there was still no active wireless connection.

iwconfig showed the same as in my reply above, except that it identified wlan1 instead of wlan0, and the dBm figure was 14 instead of 11.

lspci -nn gives a huge list including:
Ethernet Controller RealTek RT8111/8168 B PCI Express Gigabit Ethernet controller [10ec:8168] (rev  and one for the Firewire, but nothing for a Wireless connection adapter; the rest are nearly all Intel or nVidia,

---

### Post by bogan on 2010-02-17
alan@alan-desktop7:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Clarkdake DRAM Controller [8086:0040] (rev 12)
00:01.0 PCI bridge [0604]: Intel Corporation Clarkdale PCI Express x16 Root Port [8086:0041] (rev 12)
00:1a.0 USB Controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller [8086:3b3c] (rev 05)
00:1b.0 Audio device [0403]: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio [8086:3b56] (rev 05)
00:1c.0 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 [8086:3b42] (rev 05)
00:1c.2 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 3 [8086:3b46] (rev 05)
00:1d.0 USB Controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller [8086:3b34] (rev 05)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev a5)
00:1f.0 ISA bridge [0601]: Intel Corporation 5 Series Chipset LPC Interface Controller [8086:3b02] (rev 05)
00:1f.2 SATA controller [0106]: Intel Corporation 5 Series/3400 Series Chipset 6 port SATA AHCI Controller [8086:3b22] (rev 05)
00:1f.3 SMBus [0c05]: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller [8086:3b30] (rev 05)
01:00.0 VGA compatible controller [0300]: nVidia Corporation GT200 [GeForce G210] [10de:0a60] (rev a2)
01:00.1 Audio device [0403]: nVidia Corporation Device [10de:0be3] (rev a1)
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 03)
03:00.0 FireWire (IEEE 1394) [0c00]: VIA Technologies, Inc. Device [1106:3403]
mind boggling!!

---

### Post by chili555 on 2010-02-17
I guess I missed the USB part! Sorry. Please plug in the device and post:```
lsusb
```Thanks.

---

### Post by bogan on 2010-02-19
Hi Chili555! I'm not so hopeful as I was; as the getnet USB card is not performing at all well when installed either in my laptop with its own drivers, or in my Desktop with the RAL drivers from Win7.
With getnet installed in Windows7 it shows in Devices as: 802.11 USB Wireless Card and connects, but only shows a Fair/Good connection where the RealTek card gives Excellent.

However, here is what you asked for, taken with both the RealTek and getnet installed and showing as active in Win7:

alan@alan-desktop7:~$ lshw -C network shows: ( Omitting the Ethernet data ):
 *-network
       description: Wireless interface
       physical id: 2
       logical name: wlan1
       serial: 00:1f:1f:75:bc:45
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bgn

alan@alan-desktop7:~$ lsusb  shows:
Bus 001 Device 003: ID 04f2:0718 Chicony Electronics Co., Ltd 
Bus 001 Device 002: ID 8087:0020  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 005: ID 0424:2228 Standard Microsystems Corp. 9-in-2 Card Reader
Bus 002 Device 006: ID 13d3:3306 IMC Networks 
Bus 002 Device 003: ID 0424:2602 Standard Microsystems Corp. 
Bus 002 Device 004: ID 148f:3070 Ralink Technology, Corp. 
Bus 002 Device 002: ID 8087:0020  
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
alan@alan-desktop7:~$ 
Also iwconfig wlan1 shows the same as last reported.

Hope that signifies something to you, it does not mean much to me.

---

### Post by chili555 on 2010-02-19
> Bus 002 Device 004: ID 148f:3070 Ralink Technology, Corp. This card has a fairly well known issue. Two different and, presumably conflicting drivers load for it. With the Ralink inserted, please run:```
lsmod | grep rt2
```You might see all of the following drivers installed:```
rt2870sta rt2x00usb rt2800usb
```If so, please do:```
sudo gedit /etc/modprobe.d/blacklist.conf
```Use any other text editor, nano or kate or vim, if you don't have gedit. Add two new lines:```
blacklist rt2800usb
blacklist rt2x00usb
```Proofread carefully, save and close gedit. Now reboot. Does the Ralink device now work as expected?

If you see other rt2xx drivers in lsmod different from what I have listed here, please post your findings and we'll fix it.

---

### Post by bogan on 2010-02-20
Hi Chili555!
Thanks for your efforts, results below.
You will not believe this but,( Good News,) I finally found a way to get Ubuntu to connect to the getnet dongle and,( Bad News,) there is a tiny padlock icon above the Strength Bars which says 0%; Firefox returns: Trouble with Loading Page.
Network Connections Shows the wireless connection as BTHomeHub-4886 and Last Used as 'Now', whereas it always previously showed both Auto eth0 and wLan0/1 as 'never.' Curiosity?
This despite editing the security entry to 'none'.

 It is a long story, but if you want to know how I did it, let me know.
We will see what happens after rebooting. ( In fact the story is partly included below in events after that).
                               I seem to have mixed up something here,
:~$ lsmod | grep rt2 gave: rt2870sta             488820  0
 but this command now, after reboot gives: rt2870sta    488820  1

lsmod | grep rt2 gave:
rt2800usb              37372  0    
rt2x00usb              11548  1       rt2800usb
rt2x00lib                 29756  2      rt2800usb,rt2x00usb
led_class              4096  1           rt2x00lib
input_polldev        3716  1     rt2x00lib
mac80211             181140  2  rt2x00usb,rt2x00lib
cfg80211              93052  2       rt2x00lib,mac80211
crc_ccitt               1852  1            rt2800usb
                                              I do not see how the result above came from                                           the same command;
 or are they in the wrong order?

I added:
blacklist rt2800usb
blacklist rt2x00usb
 to the modeprobe.d file and rebooted.

Now, after rebooting, left-click on the Network Manager showed Wireless Networks disconnected, but lists the two networks as available, with two bars highlighted, (previously there were none) but with the tiny padlock over the one I need to connect to. 
After about two minutes a window opened asking for the key to the network, (which I entered,) and the Network Manager's Icon rotated for some time and another window opened asking for the key to the encryption - which we do not use. 
After a lot of editing the network connections entries and repeated reboots, including without the Ethernet adapter plugged in, I clicked on the available networks in the Left-Click window of Network Manager; which produced new connection entries suffixed by Auto.

 The one for BTOpenzone now connects, seems to operate correctly in Firefox, and reconnects if disconnected. Unfortunately, I do not have access to that account and its owner ( to whom I am a guest ) has never activated it.
Clicking on the BTHomeHub entry gets an insistant demand for an encryption key, that I do not get in Windows7, and do not see how to overcome; deleting all the connection entries does not help as the Auto effect just creates a new one.

BTOpenzone connects almost immediately on rebooting without the Ethernet connection. Whereas BTHomeHub seems to take ages and then does not connect.

Sorry if this seems confusing, as it is confusing me too.

---

### Post by bogan on 2010-02-20
Hi Chili555!
Thanks for your efforts, results below.
You will not believe this but,( Good News,) I finally found a way to get Ubuntu to connect to the getnet dongle and,( Bad News,) there is a tiny padlock icon above the Strength Bars which says 0%; Firefox returns: Trouble with Loading Page.
Network Connections Shows the wireless connection as BTHomeHub-4886 and Last Used as 'Now', whereas it always previously showed both Auto eth0 and wLan0/1 as never. Curiosity?
This despite editing the security to entry to 'none'.

 It is a long story but if you want to know how I did it, let me know.
We will see what happens after rebooting. ( In fact the story is partly included below in events after that).

I seem to have mixed up something here,
:~$ lsmod | grep rt2 gave: rt2870sta  488820  0,
 but this command now, after reboot gives: rt2870sta 488820  1
lsmod | grep rt2 gave:                
rt2800usb              37372  0           
rt2x00usb              11548  1 rt2800usb
rt2x00lib              29756  2 rt2800usb,rt2x00usb
led_class               4096  1 rt2x00lib
input_polldev           3716  1 rt2x00lib
mac80211              181140  2 rt2x00usb,rt2x00lib
cfg80211               93052  2 rt2x00lib,mac80211
crc_ccitt               1852  1 rt2800usb
I do not see how the result above came from the same command; or are they in the wrong order?

I added:
blacklist rt2800usb
blacklist rt2x00usb
 to the modeprobe.d file and rebooted.

Now, after rebooting, left-click on the Network Manager showed Wireless Networks disconnected but lists the two networks as available, with two bars highlighted, (previously there were none) but with the tiny padlock over the one I need to connect to. 
After about two minutes a window opened asking for the key to the network, (which I entered,) and the Network Manager's Icon rotated for some time and another window opened asking for the key to the encryption - which we do not use. 
After a lot of editing the network connections entries and repeated reboots, including without the Ethernet adapter plugged in, I clicked on the available networks in the Left-Click window of Network Manager; which produced new connection entries suffixed by Auto.

 The one for BTOpenzone now connects, seems to operate correctly in Firefox, and reconnects if disconnected. Unfortunately, I do not have access to that account and its owner ( to whom I am a guest ) has never activated it.
Clicking on the BTHomeHub entry gets an insistant demand for an encryption key, that I do not get in Windows7, and do not see how to overcome; deleting all the connection entries does not help as the Auto effect just creates a new one.

BTOpenzone connects almost immediately on rebooting without the Ethernet connection. Whereas BTHomeHub seems to take ages an then does not connect.

There is still no sign of the RealTek USB card being used, or even recognised.

Sorry if this seems confusing, as it is confusing me too.

---

### Post by bogan on 2010-02-21
Apologies again, that last post got sent twice - My finger slipped.

First, I forgot to mention that when AutoBTOpenZone connected, Connection Information showed the Interface as: '802.11 WiFi (ra0)', and Network Tools showed the Wireless Network Device as: 'Unknown Interface (ra0)'.
Second, I had decided to give up on the getnet USB dongle and rely on the Ethernet cable for Lunix, but in trying again to confirm the above references, I stumbled on a way to get the proper connection going.
BTHomeHub-4886 still shows the tiny Padlock above the strength bars but it connects and works in Firefox, taking precedence over AutoBTOpenZone.
Network Connections shows it as wLan1, the driver as usb and security as WEP, interface as above (ra0).

lshw -C Network now (for the Wireless part) shows: 
 *-network
       description: Wireless interface
       physical id: 2
       logical name: ra0
       serial: 00:1f:1f:75:bc:45
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.1.73 multicast=yes wireless=RT2870 Wireless

I see from searching other forums that there several others have the same problem with the RealTek RLT8192 WLan usb card working in Windows but not in Ubuntu. They do not appear to have reached any solution with Ubuntu9.1.

---

