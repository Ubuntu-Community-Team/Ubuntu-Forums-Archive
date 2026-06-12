---
title: "wifi connect script"
date: 2009-12-01
forum: Networking &amp; Wireless
---

### Post by mo.reina on 2009-12-01
i'm not sure if this is the correct place to put this in.  i wrote a script for connecting to a wifi network.  it allows for WPA encryption, though i've only tested it with WPA 1.  it doesn't allow for ad-hoc systems, since i've never managed to manually connect to one.

if people had some free time to take a look at it and maybe clean it up, or clear up the features it would be great.  it's not the cleanest code, partly because i figured out some stuff along the way, and partly because i'm still not very familiar with bash syntax and all the available tools.  

oh, for the WPA to work, since the script will configure the settings without WPA supplicant, you'll have to make the following changes in the /etc/NetworkManager//nm-system-settings.conf (if you're using network manager)

```
[ifupdown]
managed=**false**
```

anyway here it is.  let me know what you guys think!

```
#!/bin/bash

#removing possible previous temp file
rm list.temp 2>/dev/null

#scans for wifi connections & isolates wifi AP name
# **thanks to jonjgc for the array solution**
# **thanks to ghostdog74 for the AWK suggestion**

eval list=( $(sudo iwlist scan 2>/dev/null | awk -F":" '/ESSID/{print $2}') )

#sets prompt
PS3="Choose wifi connection: "

#tests for number of wifi connections, exits if none
if [ -z "${list[0]}" ]; then
	clear
	echo "No available wifi connection"
	exit 1
fi

#menu of wifi connections
select item in "${list[@]}"; do

#sets essid as value for WIFI variable and displays information about the AP
	wifi=$(echo $item)

	sudo iwlist scan 2>/dev/null | sed -n "/$wifi/, +9p" > list.temp
	echo "$(cat list.temp | sed 's/^[ \t]*//')"

#sets channel as value for CHANNEL variable
	channel=$(grep Channel: list.temp | sed 's/.*Channel://g')

#test for mode, if mode = master, sets MODE variable to managed
	mode=$(grep Mode list.temp | sed 's/.*Mode://g')
	if [ "$mode" == "Master" ]; then
		mode="managed"
	else
		clear
		echo "Cannot connect"
		exit
	fi

#tests for encryption key
	key=$(grep key: list.temp | sed 's/.*key://g')
	if [ $key == "on" ]; then
		echo -n "Enter encryption key: "
		read key
	fi

#checks encryption algorithm
	IE=$(grep IE list.temp | sed 's/^ .*IE: \(...\).*/\1/')

#writes to /etc/network/interfaces file for WPA encryption: essid, key, protocols, etc.
	if [ "$IE" == "WPA" ]; then
		sudo cp /etc/network/interfaces /etc/network/interfaces.bakup
		sudo sed -i 's/iface wlan0 inet manual/iface wlan0 inet dhcp/' /etc/network/interfaces
		sudo sed -i -e "/dhcp/a\wpa-passphrase $key" \
	-e "/dhcp/a\wpa-driver wext" \
	-e "/dhcp/a\wpa-key-mgmt WPA-PSK" \
	-e "/dhcp/a\wpa-proto WPA" \
	-e "/dhcp/a\wpa-ssid \"$wifi\"" /etc/network/interfaces
	sudo /etc/init.d/networking restart
	sudo cp /etc/network/interfaces.bakup /etc/network/interfaces
	sudo rm /etc/network/interfaces.bakup
	exit

	else

#sets the wireless configuration for non WPA: essid, channel, mode, key, etc
		sudo iwconfig wlan0 essid \""$wifi"\" channel $channel mode $mode key $key
		echo "------------------------------------------------"
		echo "Connecting to: $wifi at channel: $channel, mode: $mode"
		echo "------------------------------------------------"

#connects to wifi connection
		sudo dhclient
		exit
	fi
done
```

---

### Post by mo.reina on 2009-12-01
any feedback? bugs, features, etc.?

---

### Post by wmcbrine on 2009-12-01
Could you explain more about the purpose of this script? Like, why someone would want to use it rather than clicking on the Network Manager icon and selecting an access point?

---

### Post by openuniverse on 2009-12-01
.

---

### Post by mo.reina on 2009-12-02
> **wmcbrine said:**
> Could you explain more about the purpose of this script? Like, why someone would want to use it rather than clicking on the Network Manager icon and selecting an access point?

well there were several reasons i coded this.  one was that i've had bad experiences with network manager in the past.  at one point i switched to wicd, network manager was so unreliable.  

another reason was to give more options to others who've had problems with wpa supplicant, the script doesn't use it at all since it deals directly with the interfaces file, using only wireless-tools.

and lastly to see if i could do it and because it was fun.  writing scripts and posting them is also a great way to see how your code can be simplified, which in turns improves your skill as a programmer.

---

