---
title: "Is my wireless working ! Ubuntu 9.10 wireless gui"
date: 2010-02-08
forum: Networking &amp; Wireless
---

### Post by Slates on 2010-02-08
Im following [https://help.ubuntu.com/community/WifiDocs/WiFiHowTo](https://help.ubuntu.com/community/WifiDocs/WiFiHowTo) to get my wireless card working. Im unsure of the next steps to finally get connected :

ifconfig reports :
wlan0     IEEE 802.11bg  ESSID:""
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated
          Tx-Power=20 dBm
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

From this Im assuming my wireless card is recognised OK.

dmesg reports :

dmesg:
[   13.795506] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   13.808664] phy0: Selected rate control algorithm 'minstrel'
[   13.809735] b43legacy-phy0 debug: Ignoring unconnected 802.11 core
[   13.809769] Broadcom 43xx-legacy driver loaded [ Features: PLID, Firmware-ID: FW10 ]

from which I conclude its up but not yet connected.

The above link suggests I use system->admin->networking. In Ubuntu  9.10 GUI I only have network tools. But in there I see wlan0 listed as active.

I dont see any option to activate and deactivate.

I have also been into Prefs->network connections and enetered details of my wireless AP.

But here Im stuck. How do I connect to that, or the second wirelss AP ive added details for ? Am I expecting a connection icon in the desktop GUI ? Or an activate option in network connections ? I dont see one in there ... so Im struggling to find a way to actually connect to a network, and if so which one if I have enetered a couple of options ?

---

### Post by chili555 on 2010-02-08
> Am I expecting a connection icon in the desktop GUI ?Yes, it's called Network Manager. It's at the upper right and looks like two computer monitors with an [SIZE="2"][COLOR="Red"]**X**[/COLOR][/SIZE]. Click it and it will guide you. If you don't see one, right-click the tray, select Add to Panel and add Network Manager.

---

### Post by Slates on 2010-02-09
Thankyou very much Chili. That is indeed what I was looking for .. can you tell Im a ubuntu newbie !!

many thanks, my network is now indeed connected :p

---

### Post by 786souljah on 2010-02-10
I'll post here in an effort to reduce redundant threads:

To keep things short I don't have the network icon at the top right so I did a right-click -> add to panel, however there is no network manager or any network tool listed. 

How can I get the icon back?

---

### Post by bkratz on 2010-02-10
> **786souljah said:**
> I'll post here in an effort to reduce redundant threads:

To keep things short I don't have the network icon at the top right so I did a right-click -> add to panel, however there is no network manager or any network tool listed. 

How can I get the icon back?

See this thread

[http://ubuntuforums.org/showthread.php?t=1311790&highlight=notification](http://ubuntuforums.org/showthread.php?t=1311790&highlight=notification)

---

