---
title: "Configuring wireless from console"
date: 2010-06-08
forum: Networking &amp; Wireless
---

### Post by synclpz on 2010-06-08
I tried to find any information / convenient method connecting to wireless netwok from console, without X/window manager. Some research on man pages and google let me produce a small bash script :) Just wanted to share it with others.

[FONT=Lucida Console]#!/bin/bash
pkill wpa_supplicant
pkill dhclient
ifconfig wlan0 up
sleep 7 #wait to perform ifup
echo "Select network:"
iwlist wlan0 scan | egrep "ESSID|WPA"
echo -n "type network name: "
read -e NETWORK

echo -n "Is network WPA-PSK encrypted? (y/n): "
read -e WPAENC

PSK=

if [ "$WPAENC" == "y" ]
then
        echo -n "Type network Pre-Shared key: "
        read -e PSK
        wpa_passphrase "$NETWORK" "$PSK"  > /tmp/wpa_supplicant.conf
fi

ifconfig wlan0 down
sleep 1
iwconfig wlan0 essid "$NETWORK"
ifconfig wlan0 up
sleep 3
if [ "$WPAENC" == "y" ]
then
        wpa_supplicant -B -Dwext -iwlan0 -c/tmp/wpa_supplicant.conf
fi
dhclient -d wlan0 &
echo "Press ENTER to exit"


[/FONT]

---

