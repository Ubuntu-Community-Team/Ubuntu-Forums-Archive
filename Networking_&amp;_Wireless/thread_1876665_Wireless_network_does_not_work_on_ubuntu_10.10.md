---
title: "Wireless network does not work on ubuntu 10.10"
date: 2011-11-06
forum: Networking &amp; Wireless
---

### Post by kaiwangc on 2011-11-06
Hi, I am a new user. My network manager stopped working from yesterday. Also the icon disappeared. 

I found some solutions online, but they did not help:
Method 1
Open the terminal type “sudo edit /etc/NetworkManager/nm-system-settings.conf” change the “managed=false” to “managed=true” and then save it.
//it is true when I open it
then in the terminal type “killall nm-system-settings”
//```
nm-system-settings: no process found
```
and then reboot.
Method 2
right click panel>add to panel>Notification Area
//still nothing appears

But if I run 
```
nm-applet
```

The icon appears and I am connected to the wireless network. I don't want to run it each time I log in. "Network Manager" is in the list of startup applications. I also added 
```
/usr/bin/nm-applet
```
to startup applications list. After I reboot, nothing changed.

Anybody can help me out? Thanks a lot!:)

---

### Post by optima4 on 2011-11-06
I am sorry I just posted in the wrong thread. With a similar title. Almost identical

---

### Post by bluexrider on 2011-11-06
[http://www.ubuntugeek.com/how-to-troubleshoot-wireless-network-connection-in-ubuntu.html](http://www.ubuntugeek.com/how-to-troubleshoot-wireless-network-connection-in-ubuntu.html)


That will help

---

### Post by kaiwangc on 2011-11-06
sudo iwconfig wlan0 key HEX_KEY <<<-------- If using ASCII Equivalent, this is s:ASCII_KEY (please make note of the prefix s:)


what does this mean?
Thanks

---

### Post by kaiwangc on 2011-11-06
Another question:
My wpa_supplicant.conf is empty. So, how to "for WPA(1)" and "for WPA(2)"?



Creation of /etc/wpa_supplicant.conf file
At command line:
gksu gedit /etc/wpa_supplicant.conf

Inside the file add the following for WPA(1):

ap_scan=1
ctrl_interface=/var/run/wpa_supplicant

network={
ssid="ESSID_IN_QUOTES"
scan_ssid=0
proto=WPA
key_mgmt=WPA-PSK
psk="ASCII PSK Password in Quotes"
pairwise=TKIP
group=TKIP
}

For WPA(2)

ctrl_interface=/var/run/wpa_supplicant

network={
ssid="ESSID_IN_QUOTES"
psk="ASCII PSK Password in Quotes"
key_mgmt=WPA-PSK
proto=RSN
pairwise=CCMP
}

---

