---
title: "aircrack-ng: cant fakeauth"
date: 2010-11-12
forum: Networking &amp; Wireless
---

### Post by nodyarg on 2010-11-12
I read forums and the wiki but I have been unable to resolve this issue. When i use the aireplay-ng -1 command i keep getting the Sending Authentication Request (Open System) message over and over. Occasionally (but very rarely) the authentication request will be accepted and it will send an association request, but that association request is never accepted. I am running aircrack-ng 1.1 svn with the channel negative one patch installed. My wireless card is an intel 4965, i am using the latest compat wireless "iwlwifi" driver. Mac filtering is disabled on the router and this problem occurs on every router i have tried aircrack on. Also i have tested packet injection using sudo aireplay-ng -9 mon0 and it is always successful. This is the code that i am using:

[PHP]sudo service network-manager stop
sudo service avahi-daemon stop
sudo killall dhclient
sudo killall wpa_supplicant
sudo airmon-ng check kill


sudo airmon-ng start wlan0 <channel>

sudo airodump-ng mon0

sudo airodump-ng --channel <channel> --bssid <target mac> --write <file_name> mon0

sudo aireplay-ng -1 0 -e <target_essid> -a <target mac> -h <my mac> mon0 [/PHP]any ideas?

---

