---
title: "Wireless network connections works on Ubuntu 10.10 but not on Kubuntu 10.10"
date: 2011-05-01
forum: Networking &amp; Wireless
---

### Post by judedawson on 2011-05-01
Hi All,

I have a slight wireless network connection problem which I hope can be easily resolved. 

O.K, here's what's happened. 

I'm running Ubuntu 10.10 on a HP laptop with no wireless connections problems at all. I've been curious about KDE for some time now and decided to install Kubuntu on my laptop this afternoon. I launched Synaptic, did a search for 'kubuntu desktop' and installed it. The download and install went well. There were no error messages. 

At the login page, I selected the KDE environment and logged in. Kubuntu loaded O.K. There was one slight problem - the Network Manager detects my wireless network but does not want to connect to it. So, I checked the settings and could not see anything different. 

I then logged out and logged into the GNOME Ubuntu Desktop environment. In this environment, my wireless connection was immediately established. 

I can't understand why Kubuntu doesn't connect to the wireless network while Ubuntu has no problems at all...

I'm an end-user and have been using Ubuntu for about 2 years now. This is my first time trying out Kubuntu. 

Any help in this is greatly appreciated.

Thanks, all.

From,
Jude

---

### Post by judedawson on 2011-05-01
***bump***

---

### Post by judedawson on 2011-05-01
The following is the lspci info:

00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 01)
00:1c.3 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 4 (rev 01)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 01)
01:00.0 VGA compatible controller: ATI Technologies Inc M56P [Radeon Mobility X1600]
02:06.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
02:06.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
02:06.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
02:06.3 SD Host controller: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller
02:06.4 Communication controller: Texas Instruments PCIxx12 GemCore based SmartCard controller
08:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5753M Gigabit Ethernet PCI Express (rev 21)
10:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)

Suggestions, anyone?

Thanks.

---

### Post by judedawson on 2011-05-01
ifconfig info:
eth1      Link encap:Ethernet  HWaddr 00:1a:4b:5c:5d:04  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1052 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1052 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:80560 (80.5 KB)  TX bytes:80560 (80.5 KB)

wlan0     Link encap:Ethernet  HWaddr 00:19:d2:d2:0b:2f  
          inet addr:192.168.1.5  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::219:d2ff:fed2:b2f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8078 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7553 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:9354572 (9.3 MB)  TX bytes:1363961 (1.3 MB)


iwconfig info:
lo        no wireless extensions.

eth1      no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:"JUDE DAWSON"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:1F:A4:89:F0:F3   
          Bit Rate=54 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr : off   Fragment thr : off
          Power Management : off
          Link Quality=56/70  Signal level=-54 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

Thanks, all.

---

### Post by northd_tech on 2011-05-01
> **judedawson said:**
> 
10:00.0 Network controller: **Intel** Corporation PRO/**Wireless 3945ABG** [Golan] Network Connection (rev 02)

I've never worked on one of those before, but that looks to be your Wireless controller type (Intel **PRO "3945ABG** [Golan]"  ).  Searching this forum for that should locate some helpful threads.

---

### Post by judedawson on 2011-05-01
Hi northd_tech,

Thanks for the info. I'll check it out.

---

### Post by judedawson on 2011-05-02
Still no luck with this. I'm wondering if it's a setting in Kubuntu. The wireless connection works perfectly fine in Ubuntu.

Ideas, anyone?

---

### Post by judedawson on 2011-05-02
I'm going to try connecting to another wireless network tomorrow at work and observe if it also cannot connect.

---

### Post by judedawson on 2011-05-03
Yep, same symptom with another wireless network. Kubuntu network manager detects and displays the network connection, prompts for password  but does not connect to the wireless network.

---

### Post by judedawson on 2011-05-03
Any ideas, anyone?

---

### Post by judedawson on 2011-05-05
The title should actually read 'Wireless network connections works on Ubuntu 10.10 default Ubuntu-GNOME desktop environment but not on Kubuntu desktop environment.'

---

### Post by judedawson on 2011-05-05
I tried something else today. 

I downloaded the ISO file for Kubuntu 11.04 (32bit). Checked and verified MD5sum checksum O.K. and booted from the CD. I clicked on 'Try Kubuntu'. Everything launched beautifully. The ONLY problem was that the wireless connection was detected but would not connect. 

The same symptom, again.

---

### Post by judedawson on 2011-05-13
It's been a busy week...

I've been trying out several things since the last post. Here's where I'm at now:

1.0 I have discovered that the wireless connection to my office wireless network CONNECTS in the Kubuntu desktop environment! I was able to surf the internet. It turns out that the password I had keyed in was wrong (I guess no one told me it had changed recently...).

1.1 This office wireless router is physically connected to an internet broadband modem. 

2.0 Unfortunately, I still cannot connect to my wireless connection at home. So, I plugged a CAT5 cable directly into the home wireless router's LAN port. To my surprise, my laptop, while in the Kubuntu desktop environment, immediately connected and was connected to the internet. 

2.1 The home wireless router is a 2-in-1. Firstly -it's an internet broadband modem. Secondly, it's a wireless router which enables connection to the internet. I shall refer to this device hereinafter as a '2-in-1'.

3.0 I know now that I am able to connect to the internet from my office's wireless router connection and from a direct connection from my home 2-in-1. 
 
4.0 So, last Friday, I formatted my laptop and installed Kubuntu 11.04 and I was able to repeat the fault described in points 1 & 2.

4.1. I am able to reproduce the fault. From hereonaafter, the fault descriptions refer to the new  OS I am running on my laptop - Kubuntu 11.04. 

5. I have observed one other thing and I think this has something to do with why I am having this problem. When I click on the network connection icon on the bottom-right corner of the desktop panel, I am able to view all available wireless networks. Each available network has a tiny 'shield' icon beside it. Some are green-coloured with a check in the centre, some are yellow/orange in colour with an exclamation mark in the centre and some are red in color with an 'x' in the centre.  

5.1 When I place the mouse cursor on the green icon, a dialogue box indicates it as a WAP connection. Similarly, the orange/yellow icon shows as a WEP connection and the red icon shows as an unsecured connection.

5.2 Now, here's the interesting part. My office wireless internet connection shows as a WAP connection. My home wireless internet connection shows as a WEP connection. 

5.3 Perhpas this this coincidence. Perhaps it is not. 

6.0 So, this has led me to believe that the problem is actually 'Kubuntu 11.04 wireless connection works for WAP but not WEP'. I googled this and found this interesting thread (Ref. [http://ubuntuforums.org/showthread.php?t=172810](http://ubuntuforums.org/showthread.php?t=172810)). Could this thread hold the solution to the problem?

Suggestions and ideas are welcome. 

Thanks, all.

From,
Jude

---

### Post by judedawson on 2011-05-13
Hi All,

I have made some progress yesterday evening. 

1.0    Before I had reformatted my laptop last Friday, I took and saved screnshots of the Ubuntu 10.10 Network Manager wireless connection settings for my home 2-in-1 (in one of my rare moments of clarity...) 

2.0    The current laptop settings in 'Edit Network Connection - KDE Control Module' for my home wireless connection are as follows:
WIRELESS
SSID - <correct connection name...really...>
Mode - Infrastructure
BSSID - <left empty>
Restrict to Interface - Any
MTU - Open

WIRELESS SECURITY 
Security - WEP
Key Type - Passphrase (for 128 bit)
Passphrase - <correct password...really...>
WEP Index - 1 (Default)
Authentication - Open System

IP ADDRESS
Basic Settings
Method - Automatic (DHCP)

3.0    With the above settings, I am to view and detect the wireless network but am unable to connect to it. 

3.1    After reading some past postings on issues faced with WEP connections, I decided to change the 'IP Address -> Method' field from 'Automatic (DHCP)' to 'Manual'. I then keyed in details into the following fileds:

IP Address - 192.168.1.5
Subnet Mask - 255.255.255.0
Gateway - 192.168.1.255
DNS Servers - 192.168.1.1
Search Domains - <left empty>

3.2    With the above settings, my laptop CONNECTS my home wireless network!!!!! Oh, joy! When I click on the Network Manager-like-thing icon on the bottom right corner of the desktop panel and view the WLAN Interface, the icon shows it is connected. 

3.3    However, I am unable to connect to the internet. What happens is this. When I launch the Firefox browser, I see a blank page and a message at the bottom of the page says that it's connecting to the default ubuntu home webpage. But it doesn't go anywhere.

3.4    So, I tried something else. I closed the web-browser, disconnected the WLAN connection, opened 'Edit Network Connection - KDE Control Module' and I left the 'DNS Server' field empty. 

3.5    Again, the WLAN connection CONNECTED. However, when I launched the web-browser, this time the webpage showed an error message which normally appears when we type a wrong URL or if the URL cannont be found. 

3.6    For both the above-tests, the browser's 'Advanced -> Network -> Connection Settings' selection is set to 'Use System Proxy Settings'. 

4.0    So, to summarize, after changing the  'IP Address -> Method' field from 'Automatic (DHCP)' to 'Manual', I am able to connect to my home 2-in-1 BUT am still UNABLE to connect to the interet.

I'm gonna check the forums for solutions and suggestion. 

Any help in this is greatly appreciated.

Thanks, all.

From,
Jude

---

### Post by judedawson on 2011-05-16
Hi All,

HOT DOG! It works now!!!! HALLELUJAH!!!!

I posted this same problem on the kubuntuforums.net last week and received a suggestion from Snowhog to change my ADSL wireless router security encryption to WPA.

I gave it a shot today morning. 

I plugged my laptop directly to my ADSL wireless router, accessed the settings page, changed the security encryption settings from 'WEP' to 'WPA2 mixed' & rebooted the router. I then unplugged the CAT5, switched on my wifi on my laptop. Almost immediately, the Network Manager detected the router and connected to it after I keyed in the password. 

In summary, I guess Kubuntu on my laptop - for whatever reason - didn't like to connect to neither the WEP nor unsecured wireless networks.


From,
Jude

---

### Post by columgaynor on 2012-05-25
> **judedawson said:**
> Hi All,

HOT DOG! It works now!!!! HALLELUJAH!!!!

I posted this same problem on the kubuntuforums.net last week and received a suggestion from Snowhog to change my ADSL wireless router security encryption to WPA.

I gave it a shot today morning. 

I plugged my laptop directly to my ADSL wireless router, accessed the settings page, changed the security encryption settings from 'WEP' to 'WPA2 mixed' & rebooted the router. I then unplugged the CAT5, switched on my wifi on my laptop. Almost immediately, the Network Manager detected the router and connected to it after I keyed in the password. 

In summary, I guess Kubuntu on my laptop - for whatever reason - didn't like to connect to neither the WEP nor unsecured wireless networks.


From,
Jude



:confused::confused::confused:
Hei Jude,

Your account of your experienced issues was most interesting and helpful. I sm making some experiments with Ubuntu 12.04 and Kubuntu 12.04 and hit on EXACTLY the same problem as you did. My problem is I cannot switch from WEP to WPA as it will disrupt other computer users sharing my Wireless Router. I have also exactly the same Wireless Adapter hardware model as you. Must I conclude therefore that Kubuntu 12.04 still simply does not support usage of WEP mode on the wireless router access point ?

Many thanks in advance for your assistance. -Colum 
:confused::confused::confused:

---

### Post by lisati on 2012-05-25
Old thread closed

---

