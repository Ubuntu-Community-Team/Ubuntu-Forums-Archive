---
title: "Another Netgear wg311v2 problem..."
date: 2006-06-17
forum: Networking &amp; Wireless
---

### Post by flintflake on 2006-06-17
Ok...  I tried my best to get my wireless running without posting a new thread.  After reading several other posts and going through the wiki's, I have given up.   I've reinstalled Ubuntu 3 times to no avail.  Here's my issue:

Running ndiswrapper -l, it says "Driver Present, Hardware present".  

Iwconfig says that my Access Point is "Not-Associated".  I couldn't find any threads about that.  :(

Also, when i run the dmesg command, wlan0 line says "Driver using old /proc/net/wireless support, please fix driver!".    I have no idea what this means.  

I have WEP turned off and I have assigned a valid IP address in the scope of my Wireless Router.   I have a Linksys BEFW11S4 Wireless B router with all security disabled and broadcasting my ESSID.  This card works flawlessly with Windows 2000.

Help!  I'm at my wits end.

---

### Post by Macchi on 2006-06-21
Hello,
I have also a similar problem with a Netgear WG311v2 54Mbps Wireless PCI adapter card that was working perfectly under 5.10 Breezy but now doesn't  work att all on 6.06 Dapper. 

I will be thankful for suggestions on solving the problem.

Initially I thought the problem could be related to "garbage" or glitch after a dist-upgrade. Then after two additional clean installations (to exclude some other factors) I just realized that the problem was not related to my network environment and seems to be a kernel issue.
This struggle to make hardware work with Linux is understandable but very very frustrating.


PS: By the way the wireless card is on my son's computer, he is 6 years old and has a green PC running Edubuntu, mainly for the Gcompris suite and Tuxpaint.

---

### Post by tempo500 on 2006-06-21
on breeze it work out of the box
with dapper i had to ad an entry to a file.... 

sudo gedit /etc/modprobe.d/options
add line: options acx firmware_ver=1.2.1.34 or 1.2.0.30

phil

---

### Post by noname101 on 2006-06-21
If you want to use ndiswrapper, you'll have to blacklist acx_pci.
```
sudo gedit /etc/modprobe.d/blacklist
```
Add at the bottom blacklist acx_pci. If you don't want to reboot do this:
```
sudo modprobe -r ndiswrapper
sudo modprobe -r acx_pci
sudo modprobe ndiswrapper
```
Setup wireless in System | Networking | Administration.

---

### Post by Macchi on 2006-06-22
Thanks for the workaround!
[QUOTE=tempo500]One new line on /etc/modprobe.d/options:

options acx firmware_ver=1.2.1.34
[/QUOTE]
...and wireless communications are working again on my son's computer.


Now I will continue to setup Edubuntu and hopefully later even set DansGuardian+Squid on the server for safer surfing since I have small kids.
But before that I will have to solve two other hardware configuration problems on other machines that appeared after upgrades to Dapper on my home and small office environment (5 Ubuntu clients and a SuSE Server). The statistics is quite bad: one serious hardware configuration problem per machine upon upgrade, impairing networking, acpi and sound. Because of the lower reliability upon upgrade I will have to wait a couple of months before deploying Ubuntu to some of my business clients. 

I sincerely hope that these issues with ACX wireless modules will be fixed soon since they may be a serious barrier for many new Ubuntu users. Considering the importance of networking I am surprised to see these bugs rated as "medium severity". But I am not blaming Canonical or the Ubuntu comunity for that. Building reliable systems requires hard work.
I am just sad for having underestimated the risk for serious module or kernel issues upon an upgrade.
Thanks again for all help!

---

### Post by Agent86 on 2006-06-22
This is help for Dapper only, I never tried getting the WG311v2 up using Breezy.

Try opening up a terminal and typing in this command
```
iwlist scan
```If you don't see any access points, you probably need to blacklist the acx module as noname101 mentions, since the acx driver interferes with the ndiswrapper/Windows driver combo. However, in my installation, for some reason I had to blacklist acx instead of acx_pci. I guess you could blacklist both modules by adding the lines
```
blacklist acx
blacklist acx_pci
```to the end of /etc/modprobe.d/blacklist

If you're not using WPA encryption, I think it's much easier just to use the native Linux ACX driver instead of messing around with ndiswrapper.

---

### Post by bigken on 2006-06-26
[quote=tempo500]on breeze it work out of the box
with dapper i had to ad an entry to a file.... 

sudo gedit /etc/modprobe.d/options
add line: options acx firmware_ver=1.2.1.34 or 1.2.0.30

phil[/quote]


this worked for me cheers ;)

using 1,2,1,34

---

### Post by MTigerV on 2006-07-06
Thanks alot! This worked great for me too. I used 1.2.1.34.

---

