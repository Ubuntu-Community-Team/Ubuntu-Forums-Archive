---
title: "Connecting to wifi through a terminal"
date: 2011-11-16
forum: Networking &amp; Wireless
---

### Post by th1rt3en on 2011-11-16
I know this has been asked several times, but none of the dozen solved threads I found fixed it for me. I'm following this guide: [http://www.ghacks.net/2009/04/14/connect-to-a-wireless-network-via-command-line/](http://www.ghacks.net/2009/04/14/connect-to-a-wireless-network-via-command-line/)I followed the guide in tty1 without a single error message, other than maybe "sudo dhclient wlan0" taking a long time before I can enter another prompt, but when I ran: 

```
w3m google.com
```I got "w3m: Can't load google.com" I figure it might have something to do with my GUI desktop running at the same time. I tried running it before I logged in from my Desktop, but that didn't help. Do I have to completely disable my desktop? The most I found on GUI conflict was somebody telling me to run:

```
sudo service network-manager stop
```Which also didn't fix it. Another source told me to remove network-manager, which I haven't tried out of fear of not being able to connect through a GUI later; and I don't have any Ethernet cords on hand. Some additional information; I'm running Ubuntu 11.04, and I'm connecting to a "WEP 40/128-bit Key (Hex or ASCII)" connection.

Any help would be greatly appreciated.

---

### Post by jonobr on 2011-11-16
Heres a dopey question on my part,
can you ping google.com from your terminal

---

### Post by praseodym on 2011-11-16
Your /etc/network/interfaces needs following lines additionally (here for WPA2 with CCMP in pairwise and group):

```
auto wlan0
iface wlan0 inet dhcp
     wpa-driver wext
     wpa-ssid YourSSID
     wpa-ap-scan 1
     wpa-proto RSN
     wpa-pairwise CCMP
     wpa-group CCMP
     wpa-key-mgmt WPA-PSK
     wpa-psk "swordfish"
```
And you should change "false" to "true" in **/etc/NetworkManager/NetworkManager.conf** otherwise the NM will not work anymore if you are going back to the GUI because it ignores the interface **wlan0** if it is manually configured

---

