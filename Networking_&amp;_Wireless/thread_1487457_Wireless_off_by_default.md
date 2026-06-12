---
title: "Wireless off by default"
date: 2010-05-19
forum: Networking &amp; Wireless
---

### Post by Kevbert on 2010-05-19
I'm using Ubuntu 10.04 and have a wireless adapter installed. Due to problems elsewhere I'm now using a LAN connection (homeplug) Eth0. When I boot up into Ubuntu I would like wireless to be turned off until I need it. I also want to keep the password for the WLAN saved so when I turn on wireless it will automatically connect to my wireless router.
Every time I boot up at present wireless is re-enabled (after disabling it previously) and connects, as well as the WLAN.

---

### Post by dahlheim on 2010-05-22
(bump) same dilemma here.

---

### Post by dahlheim on 2010-05-27
(bumpiddybump again?)

---

### Post by dahlheim on 2010-06-04
ok, i've created (read: hacked) my own solution and thought i'd share in case anyone wants it:

1.  create scripts for turning the wireless on/off in NetworkManager:

  a.  wireless_up.sh:
```
dbus-send --system --type=method_call --dest=org.freedesktop.NetworkManager /org/freedesktop/NetworkManager org.freedesktop.DBus.Properties.Set string:org.freedesktop.NetworkManager string:WirelessEnabled variant:boolean:true
```

  b.  wireless_down.sh:
```
dbus-send --system --type=method_call --dest=org.freedesktop.NetworkManager /org/freedesktop/NetworkManager org.freedesktop.DBus.Properties.Set string:org.freedesktop.NetworkManager string:WirelessEnabled variant:boolean:false
```

2.  create script for detecting wireless state:
  2a.  get-wireless-state-from-lshw.sh:
```
lshw -C network -disable pci -disable scsi -disable pcilegacy | awk -f get-wireless-state-from-lshw.awk
```
  2b.  get-wireless-state-from-lshw.awk:
```
{
  if(($1=="description:") && ($2=="Wireless") && ($3=="interface")) {
    if(ll) {
      print ll
      } else {
      print "ENABLED"
      }
   }
  ll=$2
 }
```

3.  Create script which is called automatically during sleep/wake:
  3a.  /etc/pm/sleep.d/15-wireless:
```
#!/bin/bash
case "$1" in
    hibernate|suspend)
	echo `/(location of above scripts)/get-wireless-state-from-lshw` > /(your home)/temp/wireless-state
        ;;
    thaw|resume)
	if [ "`cat /(your home)/temp/wireless-state`" == "ENABLED" ]
		then /(location of above scripts)/wireless_up.sh
		else /(location of above scripts)/wireless_down.sh
	fi
        ;;
    *)
        ;;
esac
exit $?

```

hope that helps somebody.

---

### Post by simplygades on 2010-06-04
Works great!! Thank you!!

---

### Post by dahlheim on 2010-06-04
:)  great!  hearing it helps someone else makes the work of posting the solution totally worthwhile.

---

### Post by Kevbert on 2010-06-05
Thanks dahlheim. This should be a function of Network Manager.

---

### Post by qwerty_7564 on 2010-08-17
Using the code from dahlheim's wireless_up.sh and wireless_down.sh scripts as well as other information found on the internet, I have created upstart job definitions to automatically turn on and off the wireless whenever the network cable is plugged and unplugged.

/etc/init/wirelessoff.conf
```
# wireless - wireless adapter off

description    "wireless adapter off"

start on net-device-up IFACE=eth0
stop on net-device-down IFACE=eth0

script
        dbus-send --system --type=method_call --dest=org.freedesktop.NetworkManager /org/freedesktop/NetworkManager     org.freedesktop.DBus.Properties.Set string:org.freedesktop.NetworkManager string:WirelessEnabled variant:boolean:false
end script
```/etc/init/wirelesson.conf
```
# wireless - wireless adapter on

description    "wireless adapter on"

start on net-device-down IFACE=eth0
stop on net-device-up IFACE=eth0

script
        dbus-send --system --type=method_call --dest=org.freedesktop.NetworkManager /org/freedesktop/NetworkManager org.freedesktop.DBus.Properties.Set string:org.freedesktop.NetworkManager string:WirelessEnabled variant:boolean:true
end script
```

---

### Post by grahammechanical on 2010-08-17
Using network manager (left click) you can edit connections, select the wireless connection and uncheck "Connect automatically." Then when you boot up you do not get a wireless connection. Then when you to use wireless you right click and select your wireless connection, network manager will connect to it with out needing a password because it already has it recorded somewhere. I have just tried this out and it works. Is this what you wanted to do?

Regards.

---

### Post by s8472 on 2010-08-17
> **grahammechanical said:**
> Using network manager (left click) you can edit connections, select the wireless connection and uncheck "Connect automatically." Then when you boot up you do not get a wireless connection. Then when you to use wireless you right click and select your wireless connection, network manager will connect to it with out needing a password because it already has it recorded somewhere. I have just tried this out and it works. Is this what you wanted to do?

Regards.
Thank you, grahammechanical.  With 4 wlan connections on my laptop, I was looking for something like this.  Now, why didn't I think of this myself?..

---

### Post by Rei Malebario on 2010-11-01
> **grahammechanical said:**
> Using network manager (left click) you can edit connections, select the wireless connection and uncheck "Connect automatically." Then when you boot up you do not get a wireless connection. Then when you to use wireless you right click and select your wireless connection, network manager will connect to it with out needing a password because it already has it recorded somewhere. I have just tried this out and it works. Is this what you wanted to do?

Regards.

This may be a stupid question but has Network Manager been renamed in Maverick? I can't find anything called Network Manager anywhere and the things I *can* find that are called something with "Network" don't seem to have any "Connect automatically" boxes for me to uncheck.

---

