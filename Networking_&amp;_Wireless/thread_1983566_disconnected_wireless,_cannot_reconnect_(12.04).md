---
title: "disconnected wireless, cannot reconnect (12.04)"
date: 2012-05-20
forum: Networking &amp; Wireless
---

### Post by plethodon on 2012-05-20
After disconnecting wireless connection I could not reconnect. I rebooted computer several times. I rebooted the wireless equipment (Comcast cable modem, Linksys VoIP phone adapter and router, Linksys WRT54GL router). The router's name is "capeblanco". Below are outputs from debugging commands listed in a similar post. Thanks for any help.

(Cannot post text command output because it thinks I have images embedded. I copied output from commands into a text file and copied that into here...)

---

### Post by plethodon on 2012-05-20
The commands for which I have output are:

cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
lsusb
iwconfig
rfkill list all
lsmod
nm-tool
sudo iwlist scan
cat /var/lib/NetworkManager/NetworkManager.state
sudo cat /var/log/syslog | grep -e ath -e firmware -e wpa -e wlan -e etork | tail -n55

---

### Post by plethodon on 2012-05-20
Debugging output is posted at launchpad, same message title

---

