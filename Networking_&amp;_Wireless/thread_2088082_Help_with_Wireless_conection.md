---
title: "Help with Wireless conection"
date: 2012-11-25
forum: Networking &amp; Wireless
---

### Post by MrNewie on 2012-11-25
Hello I took the plunge & installed Ubuntu completely & standalone.


                                                                  [IMG]http://cdnsupport.gateway.com/images/ub/ub_clear.gif[/IMG]
**GemTek             Specifications**
[FONT=arial][SIZE=1]Part Number:             6008040RIntegrated Gemtek 802.11b/g Wireless Networking 4311E             (FRU) [/SIZE][/FONT]             
                                                                                                              [COLOR=#ffffff][SIZE=2]**Feature**[/SIZE][/COLOR]
                                                                   [COLOR=#ffffff][SIZE=2]**Description**[/SIZE][/COLOR]
                                                                                                     Manufacturer
                                                                   GemTek Technology Co.
                                                                                                     Model
                                                                   WMIB-184GW                          
                                                                                                     Host Interface                          
                                                                   PCI Express Mini PCI Express ExpressCard
                                                                                                     Network Standard                          
                                                                   IEEE 802.11b, and EEE 802.11g standard
                                                                                                     Data Rate                          
                                                                   
[LIST]
[*]802.11b: 11 Mbps, 5.5 Mbps, 2 Mbps, 1 Mbps
[*]802.11g: 54, 48, 36, 24, 18, 12, 9, 6 Mbps
[*]After Burner: 125 High Speed Mode™
[/LIST]
                                                                                                     Modulation                          
                                                                   
[LIST]
[*]802.11g: OFDM
[*]802.11b: CCK (11 Mbps, 5.5 Mbps), DQPSK (2 Mbps) and                             DBPSK (1 Mbps)
[/LIST]
                                                                                                     Network Architectures                          
                                                                   Infrastructure and ad hoc                          
                                                                                                     Operating Frequencies
                                                                   2.412 to 2.484 GHz
                                                                                                     Operating Channels                          
                                                                   
[LIST]
[*]802.11b and 802.11g: 11 channels for North America, 13                             for Europe (ETSI), 14 for Japan
[/LIST]
                                                                                                     RF Output Power                          
                                                                   14 dBm typical at OFDM Modulation
17.5 dBm typical at CCK                         Modulation                          
                                                                                                     Receive Sensitivity                          
                                                                   P.E.R. _<_ 10%                          
                         
[LIST]
[*]Rate: 54 - Sensitivity: -72
[*]Rate: 48 - Sensitivity: -74
[*]Rate: 36 - Sensitivity: -79
[*]Rate: 24 - Sensitivity: -81
[*]Rate: 18 - Sensitivity: -85
[*]Rate: 12 - Sensitivity: -88
[*]Rate: 9 - Sensitivity: -89
[*]Rate: 6 - Sensitivity: -90
[/LIST]
                         P.E.R. _<_ 8%                          
                         
[LIST]
[*]Rate: 11 - Sensitivity: -87
[*]Rate: 5.5 - Sensitivity: -89
[*]Rate: 2 - Sensitivity: -93
[*]Rate: 1 - Sensitivity: -96
[/LIST]
                                                                                                     Security                          
                                                                   802.1x, WEP, WEP2, WPA, WPA2, TKIP, Weak-key avoidance, CCX,                         CCX 2.0, 128-bit OCB mode AES, 802.11i                          
                                                                                                     Client Utility                          
                                                                   Automatic location profile, site monitor, current link                         status, and diagnostics                          
                                                                                                     Software Support                          
                                                                   Microsoft® WHQL-certified for Windows® XP, Windows® Me,                         Windows® 2000, and Windows® 98SE and Windows® 98. Portable                         to Linux®, and Windows® CE                          
                                                                                                     Certification                          
                                                                   IEEE 802.11 Compliant, Wi-Fi Certified, ACPI Power                         Management                          
                                                                                                     Temperatures                          
                                                                   
[LIST]
[*]Operating: 0 to 65° C
[*]Storage: -20 to 85° C
[/LIST]
                                                                                                     Humidity (non-condensing)                          
                                                                   Maximum 95%                          
                                                                    

I can not get it to recognize any wireless network?

---

### Post by wildmanne39 on 2012-11-25
Hi, copy and paste this command in the terminal (ctrl+alt+t) please:
```
wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a text file in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back  and attach the netinfo.txt file.
Thanks

---

### Post by MrNewie on 2012-11-25
Attatched, I Could Not get it to post but here it is:

---

### Post by wildmanne39 on 2012-11-25
Hi, please attach the netinfo.txt file using the paperclip in the text window not the actual wireless script.
Thanks

---

### Post by personalpc on 2012-11-25
The drivers are available in 12.10 in repos
launch terminal with ctrl+alt+t then run

rfkill list all

if it says there is a hardware switch that has the wireless turned off then try looking for a wireless button on the laptop it should be fn+X or a button on the side.

If that doesn't work then go to system settings -> software sources and enable all of the Ubuntu Updates and also all of the Other Software such as Partners and Independent. Then go back to terminal and run

sudo apt-get update

sudo apt-get upgrade

sudo apt-get dist-upgrade

sudo apt-get install jockey-text

sudo jockey-text

sudo shutdown -r now

---

### Post by MrNewie on 2012-11-25
E: Could not get lock /var/lib/apt/lists/lock - open (11: Resource temporarily unavailable)
E: Unable to lock directory /var/lib/apt/lists/
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

---

### Post by wildmanne39 on 2012-11-25
Hi, that message is usually caused by having two apt-get applications open at the same time like software center and the terminal.

I would not try that until you post the file we need to see.
Also please see my previous post.
Thanks

---

### Post by MrNewie on 2012-11-25
Sorry I see:)

---

### Post by wildmanne39 on 2012-11-25
Hi, please do:
```
sudo apt-get purge bcmwl-kernel-source broadcom-sta-common broadcom-sta-source
```
Then:
```
sudo apt-get install --reinstall linux-headers-$(uname -r) build-essential
```
```
sudo apt-get install b43-fwcutter firmware-b43-installer
```
Watch for errors.
Then:
```
sudo modprobe b43
```
Thanks

---

### Post by MrNewie on 2012-11-25
All Right it is done.

I am pretty sure you are the same person who helped me when i did WUBI install with XP. I decided to just use Ubuntu...._***. Thanks again for the help***_...I dont think I can every go back to windows except at work:)

---

### Post by wildmanne39 on 2012-11-25
Hi, that is possible, please use thread tools at the top of the page to mark the thread solved.
Thanks
Enjoy

---

