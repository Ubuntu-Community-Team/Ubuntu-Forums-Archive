---
title: "wicd and wpa_supplicant.conf"
date: 2009-03-23
forum: Networking &amp; Wireless
---

### Post by afeasfaerw23231233 on 2009-03-23
I am using wicd and WPA1 encrypted connection. 
If I trigger the wifi on (fn-f10) before the notebook booting into Ubuntu, the connection can be established successfully. But if my wifi is off and I trigger it after entering X then I cannot get wicd connected to the router. 
I check the router log page and find out it should be a WPA authentication failure
```
Disassociated: xx-xx-xx-xx-xx-xx because WPA retey failed
```

I think there might be some problem with my /etc/wpa_supplicant.conf file
Here's the content
```

ap_scan=1
ctrl_interface=/var/run/wpa_supplicant

network={
        ssid="router"
        scan_ssid=0
        proto=WPA
        key_mgmt=WPA-PSK
        psk="abcdefgh"
        pairwise=TKIP
        group=TKIP
} 
```

In the "Preferences > General Settings" of Wicd I've tried 'wext' and 'ndiswrapper', nothing works. 

Would anyone please tell me what's the relationship between Wicd and wpa_supplicant and how could I fix this problem? 
And if anyone who are using Wicd with WPA would you please post your 
```
cat /etc/wpa_supplicant.conf
``` as a reference for me?

Thanks!

Below are my /etc/wicd/encryption/templates/wpa and wpa-psk. I didn't touch it and I think they are the default values.
```
cat wpa
name = WPA 1/2 (Passphrase)
author = Adam Blackburn
version = 1
require key *Key
-----
ctrl_interface=/var/run/wpa_supplicant
network={
       ssid="$_ESSID"
       scan_ssid=$_SCAN
       proto=WPA RSN
       key_mgmt=WPA-PSK
       pairwise=CCMP TKIP
       group=CCMP TKIP
       psk=$_PSK
}

```
```
cat wpa-psk
name = WPA 1/2 (Preshared Key)
author = Adam Blackburn
version = 1
require apsk *Preshared_Key
-----
ctrl_interface=/var/run/wpa_supplicant
network={
       ssid="$_ESSID"
       scan_ssid=$_SCAN
       proto=WPA RSN
       key_mgmt=WPA-PSK
       pairwise=CCMP TKIP
       group=CCMP TKIP
       psk="$_APSK"
}

```

---

### Post by kevdog on 2009-03-23
> If I trigger the wifi on (fn-f10) before the notebook booting into Ubuntu, the connection can be established successfully.

This has nothing to do with wicd or networking.  I believe it is a problems with the pci bus not notifying udev or something.  I think its going to have to be a problem you are going to live with for now.  Its more kernel related and not wicd related.

---

### Post by afeasfaerw23231233 on 2009-03-23
But if I use unencrypted connection it just fine no matter when I switch the wireless lan card on.


p.s. It's a internal usb wireless lan card.

---

### Post by afeasfaerw23231233 on 2009-03-28
bump

---

### Post by kevmitch on 2009-03-28
I myself have very little knowledge of wicd, though it sounds pretty superflous to me. I use only wpa_supplicant and control it through wpa_gui, though once you get wpa_supplicant configured the way you want it everything should pretty much happen automatically. 

Just to make sure you are making a concious choice NOT to use network manager correct? This would be by far the easiest way, though I sympathise if you'd rather get your hands dirty ;). 

If you do want to do things the l337 way, you should get rid of network manager completely as it only has the potential to confuse things.

```
aptitude remove network-manager
```

Then you should make sure that your /etc/network/interfaces file has a stanza like

```

noauto wlan0
allow-hotplug wlan0

iface wlan0 inet manual
      wpa-roam /etc/wpa_supplicant.conf

iface default inet dhcp

```

"noauto wlan0" means don't bring it up on boot automatically (you may or may not want to replace that with "auto wlan0" depending on what works for you). 

"allow-hotplug wlan0" should tell it to bring up the interface whenever the hardware becomes ready. hopefully, this means when you hit the fn-f10 switch. It also happens if you have just probed the module for your card. 

"iface wlan0 inet manual"
means you want wpa_supplicant to handle the interface and the line after that tells it where wpa_supplicants conf file is. 

Finally, "iface default inet dhcp" means that you want to get an ip address via dhcp from any wireless network that you connect to. 

My wpa_supplicant.conf file looks like 

```

ctrl_interface=DIR=/var/run/wpa_supplicant GROUP=netdev
ctrl_interface_group=netdev
update_config=1

network={
        ssid="networkgoeshere"
        psk="passwordgoeshere"
        key_mgmt=WPA-PSK
        pairwise=CCMP
        priority=5
}

network={
        key_mgmt=NONE
}

```
The first line tells wpa_supplicant says where to keep the socket that is used to control it and makes it accessible to anyone in the group "netdev". Of course, you're going to want to be a member of this group
```
adduser <you> netdev
```

I believe the second line may be redundant, but hey, everything is working fine for me. 

"update_config=1" means that you're going to allow changes made in the wpa_gui to be saved to the wpa_supplicant.conf file. Note that any comments you put in this file will be annihilated if you have this enabled.

Of course your network stanzas will depnend on the particular configuration of your network. The surest thing is to let wpa_gui autodetect as much as possible and add the stanzas itself and then tweak them further by hand if necessary. 

The last stanza says to connect to any open AP. 

If you want more info/examples, take a look in the /usr/share/doc/wpasupplicant/ directory.

---

### Post by afeasfaerw23231233 on 2009-03-28
Thanks for your help. I use wicd because network manager doesn't work with the ndiswrapper driver.

I followed your steps but still nothing work. 

/etc/network/interfaces
```


auto wlan0
allow-hotplug wlan0

iface wlan0 inet manual
      wpa-roam /etc/wpa_supplicant.conf

iface default inet dhcp


```

/etc/wpa_supplicant.conf
```


ctrl_interface=DIR=/var/run/wpa_supplicant GROUP=netdev
ctrl_interface_group=netdev
update_config=1


network={
        ssid="homerouter269"
        scan_ssid=0
        proto=WPA
        key_mgmt=WPA-PSK
        psk="abcdefghijk"
        pairwise=TKIP
        group=TKIP
}
```

When I run sudo wpa_gui in terminal it says ```

Failed to open control connection to wpa_supplicant.
PING failed - trying to reconnect
PING failed - trying to reconnect
PING failed - trying to reconnect
PING failed - trying to reconnect
PING failed - trying to reconnect
PING failed - trying to reconnect
PING failed - trying to reconnect
PING failed - trying to reconnect


```
I get a screenshot of wpa_gui

EDIT: While it failed to connect, these messages appeared on the log page of the router:
```
 

Associated: xx-xx-xx-xx-xx-xx st=0
Disassociated: xx-xx-xx-xx-xx-xx because WPA retey failed
Associated: xx-xx-xx-xx-xx-xx st=0
Disassociated: xx-xx-xx-xx-xx-xx because WPA retey failed
Associated: xx-xx-xx-xx-xx-xx st=0
Disassociated: xx-xx-xx-xx-xx-xx because WPA retey failed
Associated: xx-xx-xx-xx-xx-xx st=0
Disassociated: xx-xx-xx-xx-xx-xx because WPA retey failed
Associated: xx-xx-xx-xx-xx-xx st=0
Disassociated: xx-xx-xx-xx-xx-xx because WPA retey failed


```

---

### Post by afeasfaerw23231233 on 2009-03-28
My problem solved. I need to add a preconnection scripts of "su" in Wicd. It works perfectly now. 
But why "su" is needed?

---

### Post by ducksun43 on 2009-06-16
hmmm ... imho network manager is a pita ... it does what it wants, when it wants, how it wants ... 

I don't like that, rather I'd like for myself to decide when and where to use wifi. This [http://sunoano.name/ws/public_xhtml/ggm.html#wifi_and_debian](http://sunoano.name/ws/public_xhtml/ggm.html#wifi_and_debian) is a pretty good article about how to use wpa_supplicant in order to set up wifi.

---

