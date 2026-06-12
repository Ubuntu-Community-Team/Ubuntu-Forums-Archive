---
title: "Advice on how to obtain access point information quickly"
date: 2012-07-24
forum: Networking &amp; Wireless
---

### Post by bgagnon on 2012-07-24
Hello everyone,

I'm working on a project essentially alone and was hoping to find some advice here, maybe even advice on where to ask. I'm not sure if this is the best place.

I need to capture data from my wireless card about access points in the vicinity. The only information I'm looking for is the address, SSID and signal strength. I have written a python program that runs "sudo iwlist wlan0 scan" command and retrieves the output, parses it and gives it in a nice clean format. 

This works great, but the only problem is that it can take as long as 5 seconds to run the command when I've got other things running. I'm using a brand new ePC with Ubuntu 10.04 on it so I'm not worried about processing power. I think the slow speed problem lies in how my other programs interact with it. But that's not my question.

My question is: Is there an alternative to "iwlist" that is fast? Or, what is the best (quickest) way for me to obtain access point information? Perhaps there are other programs out there. Any help would be greatly appreciated. Thank you.

Blair

---

### Post by bakegoodz on 2012-07-28
```
sudo apt-get install wavemon
sudo wavemon
```

press F3

---

### Post by bgagnon on 2012-07-31
Unfortunately that doesn't work on my card. I get the response, "Wlan0 does not have a list of peers/aps" 

Also, I need to be able to export the data about the APs to another program. I'm writing a python program that will have to some how retrieve that data either by directly communicating with the wlan program or by running it through a terminal and catching the output.

Any more ideas? Thanks!

Blair

---

### Post by steeldriver on 2012-07-31
if you're using network-manager (default on current desktop configs - not sure about 10.04) you could try nmcli

```
nmcli dev wifi list
```

---

### Post by bgagnon on 2012-08-02
I don't seem to have that on my computer and I'm having trouble finding which package it is in so I can download it. 

Where I could I find this nmcli?

---

### Post by steeldriver on 2012-08-02
it's part of the current network-manager package - it seems it's not in the 10.04 version of the package - you could try installing a newer network-manager from the launchpad ppa 

[https://launchpad.net/~network-manager/+archive/ppa]("https://launchpad.net/%7Enetwork-manager/+archive/ppa")

---

### Post by Cheesehead on 2012-08-02
I use the dbus-send command to query Network Manager. You can do the same thing with the dbus module in python. Since it reads values that NM already tracks, it's fast. It takes a bit of coding and logic to make it work, but it also doesn't require any new dependencies.


```
WHICH INTERFACE IS THE ACTIVE CONNECTION USING?
$ dbus-send --system --print-reply \
            --dest=org.freedesktop.NetworkManager \
            /org/freedesktop/NetworkManager/ActiveConnection/18 \
            org.freedesktop.DBus.Properties.Get \
            string:"org.freedesktop.NetworkManager.Connection.Active" \
            string:"Devices"

method return sender=:1.4 -> dest=:1.331 reply_serial=2
   variant       array [
         object path "/org/freedesktop/NetworkManager/Devices/0"
         # THIS TELLS ME NETWORK DEVICE 0 HAS AN ACTIVE CONNECTION


GET THE LIST OF ALL VISIBLE WIRELESS ACCESS POINTS
$ dbus-send --system --print-reply \
            --dest=org.freedesktop.NetworkManager 
            /org/freedesktop/NetworkManager/Devices/0 \
            org.freedesktop.NetworkManager.Device.Wireless.GetAccessPoints

method return sender=:1.4 -> dest=:1.333 reply_serial=2
   array [
      object path "/org/freedesktop/NetworkManager/AccessPoint/209"
      object path "/org/freedesktop/NetworkManager/AccessPoint/208"
      object path "/org/freedesktop/NetworkManager/AccessPoint/207"
      object path "/org/freedesktop/NetworkManager/AccessPoint/206"


READ THE SSID OF AN ACTIVE WIRELESS ACCESS POINT
$ dbus-send --system --print-reply \
            --dest=org.freedesktop.NetworkManager \
            /org/freedesktop/NetworkManager/AccessPoint/209 \
            org.freedesktop.DBus.Properties.Get \
            string:"org.freedesktop.NetworkManager.AccessPoint" \
            string:"Ssid"

method return sender=:1.4 -> dest=:1.335 reply_serial=2
   variant       array of bytes "NETGEAR"
   # Access Point 209's SSID is NETGEAR 


READ THE SIGNAL STRENGTH OF AN ACTIVE WIRELESS ACCESS POINT
$ dbus-send --system --print-reply \
            --dest=org.freedesktop.NetworkManager \
            /org/freedesktop/NetworkManager/AccessPoint/209 \
            org.freedesktop.DBus.Properties.Get \
            string:"org.freedesktop.NetworkManager.AccessPoint" \
            string:"Strength"

method return sender=:1.4 -> dest=:1.340 reply_serial=2
   variant       byte 54
   # 54 in byte (hexadecimal) = 84 in decimal. Strength = 84%

```

---

