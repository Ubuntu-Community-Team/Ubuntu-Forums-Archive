---
title: "Acer Aspire 4820T (wireless card: Atheros AR928x) need help"
date: 2010-04-13
forum: Networking &amp; Wireless
---

### Post by lazyguy77 on 2010-04-13
Still unable to get the wireless connection and ethernet connection (LAN) with this new laptop.
 
Can someone guide me step-by-step to solve the problem? I'm new to Ubuntu, I wanna to switch from Windows 7 to Ubuntu, please explain in basic term.
 
System Info as following:
 
Ubuntu 9.10 i386
 
---------------------------------------------------------------------------------------------
lspci -nn
 
result: 
02.00.0 Network Controller [0280]: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) [168c:002a] (rev 01)
---------------------------------------------------------------------------------------------
 
lshw -C Network
 
result:
 *-network UNCLAIMED     
       description: Ethernet controller
       product: Attansic Technology Corp.
       vendor: Attansic Technology Corp.
       physical id: 0
       bus info: [EMAIL="pci@0000:01:00.0"]pci@0000:01:00.0[/EMAIL]
       version: c0
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list
       configuration: latency=0
       resources: memory:93400000-9343ffff ioport:2000(size=128)
  *-network
       description: Wireless interface
       product: AR928X Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: [EMAIL="pci@0000:02:00.0"]pci@0000:02:00.0[/EMAIL]
       logical name: wlan0
       version: 01
       serial: f0:7b:cb:40:5b:93
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k latency=0 multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:92400000-9240ffff
 
-----------------------------------------------------------------------------------------
 
Thank you.

---

### Post by chili555 on 2010-04-13
> *-network
description: Wireless interface
product: AR928X Wireless Network Adapter (PCI-Express)
vendor: Atheros Communications Inc.
physical id: 0
bus info: pci@0000:02:00.0
logical name: [COLOR="Red"]wlan0[/COLOR]
version: 01
serial: f0:7b:cb:40:5b:93
width: 64 bits
clock: 33MHz
capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
configuration: broadcast=yes [COLOR="Red"]driver=ath9k[/COLOR] latency=0 multicast=yes wireless=IEEE 802.11bgn
resources: irq:17 memory:92400000-9240ffff
It looks like your wireless is all set. Are you able to click the Network Manager icon and see your network? Does it try to connect?

---

### Post by lazyguy77 on 2010-04-13
When I right click with mouse on the NetworkManagerApplet icon (top panel), check the Enable Networking & check the Enable Wireless, I will connect to my router, but will disconnected after 30 seconds.

---

### Post by chili555 on 2010-04-13
Please try to connect and let it disconnect and then open a terminal and do:```
sudo tail -n25 /var/log/syslog
```Try to find the place where it fails and copy and paste the ten or so lines up to and including that spot into a text document (Applications > Accessories > gedit, for example) and post it here. Perhaps we can see what's going wrong.

If you do:```
iwconfig wlan0
```What does it say the signal strength and bit rate are?

---

### Post by lazyguy77 on 2010-04-13
sudo tail -n25 /var/log/syslog
 
result:
Apr 13 20:21:30 guis-laptop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP6 Configure Timeout) started...
Apr 13 20:21:30 guis-laptop NetworkManager: <info>  (wlan0): device state change: 7 -> 9 (reason 5)
Apr 13 20:21:30 guis-laptop NetworkManager: <info>  Activation (wlan0) failed for access point (Guis-linksys)
Apr 13 20:21:30 guis-laptop NetworkManager: <info>  Marking connection 'Auto Guis-linksys' invalid.
Apr 13 20:21:30 guis-laptop NetworkManager: <info>  Activation (wlan0) failed.
Apr 13 20:21:30 guis-laptop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP6 Configure Timeout) complete.
Apr 13 20:21:30 guis-laptop NetworkManager: <info>  (wlan0): device state change: 9 -> 3 (reason 0)
Apr 13 20:21:30 guis-laptop NetworkManager: <info>  (wlan0): deactivating device (reason: 0).
Apr 13 20:21:30 guis-laptop NetworkManager: <info>  (wlan0): canceled DHCP transaction, dhcp client pid 1806
Apr 13 20:21:30 guis-laptop kernel: [  227.853334] wlan0: deauthenticating from 00:1d:7e:aa:47:a0 by local choice (reason=3)
Apr 13 20:21:30 guis-laptop kernel: [  227.853404] wlan0: deauthenticating from 00:1d:7e:aa:47:a0 by local choice (reason=3)
Apr 13 20:21:30 guis-laptop wpa_supplicant[1133]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Apr 13 20:21:30 guis-laptop wpa_supplicant[1133]: CTRL-EVENT-SCAN-RESULTS 
Apr 13 20:21:59 guis-laptop wpa_supplicant[1133]: CTRL-EVENT-SCAN-RESULTS 
Apr 13 20:22:49 guis-laptop wpa_supplicant[1133]: CTRL-EVENT-SCAN-RESULTS 
Apr 13 20:23:49 guis-laptop wpa_supplicant[1133]: CTRL-EVENT-SCAN-RESULTS 
Apr 13 20:24:49 guis-laptop wpa_supplicant[1133]: CTRL-EVENT-SCAN-RESULTS 
Apr 13 20:25:49 guis-laptop wpa_supplicant[1133]: CTRL-EVENT-SCAN-RESULTS 
Apr 13 20:26:49 guis-laptop wpa_supplicant[1133]: CTRL-EVENT-SCAN-RESULTS 
Apr 13 20:27:49 guis-laptop wpa_supplicant[1133]: CTRL-EVENT-SCAN-RESULTS 
Apr 13 20:28:49 guis-laptop wpa_supplicant[1133]: CTRL-EVENT-SCAN-RESULTS 
Apr 13 20:29:49 guis-laptop wpa_supplicant[1133]: CTRL-EVENT-SCAN-RESULTS 
Apr 13 20:30:49 guis-laptop wpa_supplicant[1133]: CTRL-EVENT-SCAN-RESULTS 
Apr 13 20:31:49 guis-laptop wpa_supplicant[1133]: CTRL-EVENT-SCAN-RESULTS 
Apr 13 20:32:49 guis-laptop wpa_supplicant[1133]: CTRL-EVENT-SCAN-RESULTS

---

### Post by lazyguy77 on 2010-04-13
iwconfig wlan
 
result:
wlan0     IEEE 802.11bgn  Mode:Managed  Frequency:2.462 GHz  
          Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on

---

### Post by chili555 on 2010-04-13
Please try:```
sudo rmmod -f ath9k
sudo modprobe ath9k nohwcrypt=1
```Now try to connect and see if the behavior is better. If this works, we can make it permanent.

---

### Post by lazyguy77 on 2010-04-13
sudo rmmod -f ath9k
sudo modprobe ath9k nohwcrypt=1
 
result:
 
Network
Disconnected - you are offline

---

### Post by chili555 on 2010-04-13
> Network
Disconnected - you are offlineIt certainly would have done that when you removed the module (rmmod), but didn't it come back when you added it back in (modprobe) with a new parameter?

---

### Post by lazyguy77 on 2010-04-13
sudo rmmod -f ath9k
sudo modprobe ath9k nohwcrypt=1
 
after add back the parameter, the NetworkManager will re-connect the wireless, but unsuccess and displayed "Network - Disconnected, you are now offline" message on the screen.

---

### Post by chili555 on 2010-04-13
This bug report suggests that linux-backports-modules may be a suspect. Do you have it installed? If so, I'd remove it.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/461769](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/461769)

---

### Post by lazyguy77 on 2010-04-13
How can I check the modules has installed in the system? Also if I found it, how to remove it?

---

### Post by chili555 on 2010-04-14
The easiest way is to simply try to remove it. If it's there, it will be removed; if it's not, you will be informed.```
sudo apt-get remove linux-backports-modules-*
```Reboot and let us know.

---

### Post by lazyguy77 on 2010-04-14
sudo apt-get remove linux-backports-modules-*
 
Rebooted system
 
result:
System has removed few backports-modules, after reboot the problem still remain.
[LIST=1]
[*]Enable Wireless at NetworkManager
[*]Connected to wireless network, but few seconds later disconnected
[*]"Network Disconnected - you are now offline" message displayed on screen.
[/LIST]

---

### Post by Blu3Haz3 on 2010-04-14
I had a wonderful (horrible) time trying to get my AR928x card working properly on my Asus laptop. It originally *appeared* to work well, but would lock the entire computer up when I tried to download something.

I eventually followed [[COLOR="Green"]this guide[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1309072") to install MadWifi drivers for it. It now works without hanging, but gets terrible signal reception. I've never seen it above 65%.

Regardles, it's worth a shot if you've got nothing already.

---

### Post by chili555 on 2010-04-14
I saw this which may help:  [http://dimitar.me/madwifi-drivers-for-ubuntu-9-10-karmic-koala-or-linux-kernels-2-6-29-and-above/](http://dimitar.me/madwifi-drivers-for-ubuntu-9-10-karmic-koala-or-linux-kernels-2-6-29-and-above/)

---

### Post by lazyguy77 on 2010-04-15
Blu3Haz3,
Thanks for your guide, but my wired network also unable to connect to internet which will not able to update the sources.list

---

### Post by lazyguy77 on 2010-04-15
Finally I manage to get the wireless connected to internet. :)

Thanks for Erni S. post the solution:
[http://ubuntuforums.org/showthread.php?t=1447901](http://ubuntuforums.org/showthread.php?t=1447901)

Here what I have done:

Step 1:

[LIST]
[*]logon with root
[/LIST]

Step 2:

[LIST]
[*]Open folder /etc/modprobe.d
[*]copy file blacklist-ath_pci.conf to desktop as backup copy
[*]Open file blacklist-ath_pci.conf
[*]edit the content with add # in front of blacklist ath_pci
[/LIST]
[INDENT]# For some Atheros 5K RF MACs, the madwifi driver loads buts fails to
# correctly initialize the hardware, leaving it in a state from
# which ath5k cannot recover. To prevent this condition, stop
# madwifi from loading by default. Use Jockey to select one driver
# or the other. (Ubuntu: #315056, #323830)
[B][COLOR=Red]# blacklist ath_pci
[/COLOR][/B][/INDENT]
[LIST]
[*]Save and reboot the system
[/LIST]
Step 3:

[LIST]
[*]After system rebooted, login with my normal User ID
[*]Go to System > Preferences > Network Connections
[*]Under the Wireless tab, delete the existing profile (now is empty profile)
[/LIST]
Step 4:

[LIST]
[*]Open the NetworkManager Applet at the top panel and select your Wireless Connection Profile
[*]Enter the Wireless Security password
[/LIST]
Step 5:

[LIST]
[*]Enjoy!
[/LIST]

---

### Post by lazyguy77 on 2010-04-16
Need help again (another problem occur)
 
Well, I notice my router Linksys WAG200G keep disconnected & reconnect every 1 minute from ISP.
 
Any idea?

---

### Post by Sxooter on 2011-05-09
This sounds like a wireless router issue.  I had a buffalo WZR-HP-300N fail on me much like this.  Apparently it's a common failure mode for that router.  Anyway, I got a different wireless router (netgear 3500L) and have been happy as a clam since.

---

