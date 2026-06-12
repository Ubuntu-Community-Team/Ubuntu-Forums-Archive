---
title: "do not let wpasupplicant connect to unencrypted networks"
date: 2006-03-04
forum: Networking &amp; Wireless
---

### Post by magisterludi on 2006-03-04
Hello,

I search a while for a solution for this but didn't find anything.
For me it is annoying that wpasupplicant connects to every unencrypred (unsecure) wlan out there if you start the daemon(starting it is integrated in my boot scripts). 
I have only one configuration in the wpa_supplicant.conf. This one is for a WPA network. Sometimes my laptop is connected to an unencrypted network and I do not notice it because this stuff with dhcp just works. So all my traffic is sniffable by just everyone.
I tried to get rid of it by setting priorities, didn't work either.
Some clue?

thank you

---

### Post by matthew on 2006-03-08
[quote=magisterludi]Hello,

I search a while for a solution for this but didn't find anything.
For me it is annoying that wpasupplicant connects to every unencrypred (unsecure) wlan out there if you start the daemon(starting it is integrated in my boot scripts). 
I have only one configuration in the wpa_supplicant.conf. This one is for a WPA network. Sometimes my laptop is connected to an unencrypted network and I do not notice it because this stuff with dhcp just works. So all my traffic is sniffable by just everyone.
I tried to get rid of it by setting priorities, didn't work either.
Some clue?

thank you[/quote]Can you post a copy of your wpa_supplicant.conf file? I'll take a look and see if I can see something specific. I only have one in mine and it will not connect to anything except the configured network unless I disable the wpa_supplicant process.

---

### Post by magisterludi on 2006-03-10
Hello again,

here is a copy of my wpasupplicant. It is really nothing special about it:
```

ctrl_interface=/var/run/wpa_supplicant
eapol_version=1
ap_scan=2
network={
      ssid="someAP"
      scan_ssid=1
      priority=10
      proto=WPA
      key_mgmt=WPA-PSK
      pairwise=TKIP
      group=TKIP CCMP
      psk=---hidden---
}

```

There is no configuration for other access points.

---

### Post by matthew on 2006-03-10
Here's mine.
```
ctrl_interface=/var/run/wpa_supplicant

network={
    ssid="networkname"
    scan_ssid=1
    proto=WPA
    key_mgmt=WPA-PSK
    pairwise=TKIP    
    psk="ssh--it's a secret!"
}
```There are very few differences between yours and mine...in fact the only real differences are a few extra lines in yours that I don't have.

Here's what the documentation (found in /usr/share/doc/wpasupplicant/examples) says about each line you have that I don't.
```
# IEEE 802.1X/EAPOL version
# wpa_supplicant was implemented based on IEEE 802-1X-REV-d8 which defines
# EAPOL version 2. However, there are many APs that do not handle the new
# version number correctly (they seem to drop the frames completely). In order
# to make wpa_supplicant interoperate with these APs, the version number is set
# to 1 by default. This configuration value can be used to set it to the new
# version (2).
eapol_version=1
``` I don't see why that would make a difference... You could try commenting it out and see what happens.

```
# AP scanning/selection
# By default, wpa_supplicant requests driver to perform AP scanning and then
# uses the scan results to select a suitable AP. Another alternative is to
# allow the driver to take care of AP scanning and selection and use
# wpa_supplicant just to process EAPOL frames based on IEEE 802.11 association
# information from the driver.
# 1: wpa_supplicant initiates scanning and AP selection
# 0: driver takes care of scanning, AP selection, and IEEE 802.11 association
#    parameters (e.g., WPA IE generation); this mode can also be used with
#    non-WPA drivers when using IEEE 802.1X mode; do not try to associate with
#    APs (i.e., external program needs to control association). This mode must
#    also be used when using wired Ethernet drivers.
# 2: like 0, but associate with APs using security policy and SSID (but not
#    BSSID); this can be used, e.g., with ndiswrapper and NDIS drivers to
#    enable operation with hidden SSIDs and optimized roaming; in this mode,
#    the network blocks in the configuration file are tried one by one until
#    the driver reports successful association; each network block should have
#    explicit security policy (i.e., only one option in the lists) for
#    key_mgmt, pairwise, group, proto variables
ap_scan=1
```I don't have this line so I'm guessing it is automatically set to 0. In that case the driver takes care of scanning rather than wpa_supplicant. This might make a difference. Try commenting it out and see what happens.

```
# priority: priority group (integer)
# By default, all networks will get same priority group (0). If some of the
# networks are more desirable, this field can be used to change the order in
# which wpa_supplicant goes through the networks when selecting a BSS. The
# priority groups will be iterated in decreasing priority (i.e., the larger the
# priority value, the sooner the network is matched against the scan results).
# Within each priority group, networks will be selected based on security
# policy, signal strength, etc.
# Please note that AP scanning with scan_ssid=1 and ap_scan=2 mode are not
# using this priority to select the order for scanning. Instead, they try the
# networks in the order that used in the configuration file.
```This line just doesn't seem necessary in your config file since you are using scan_ssid=1 so it isn't doing anything. Do what you want. I suppose you could try commenting it out and see what happens.

```
# group: list of accepted group (broadcast/multicast) ciphers for WPA
# CCMP = AES in Counter mode with CBC-MAC [RFC 3610, IEEE 802.11i/D7.0]
# TKIP = Temporal Key Integrity Protocol [IEEE 802.11i/D7.0]
# WEP104 = WEP (Wired Equivalent Privacy) with 104-bit key
# WEP40 = WEP (Wired Equivalent Privacy) with 40-bit key [IEEE 802.11]
# If not set, this defaults to: CCMP TKIP WEP104 WEP40
```I don't have this one either, but all you are doing here is limiting which ciphers are available to WPA. I have mine using the default whereas you only allow two. I can't see this making any difference.

Well, I'm not sure how helpful that was, but at least you can look at the differences between yours and mine. You also now know where the documentation for wpa_supplicant is found so you can read through that at your leisure and do some further experimentation if you want to. I recommend starting off by commenting out each line not present in my config file (one at a time), then stopping the wpa_supplicant process and restarting it and see if any of those changes make a difference for you. If not, I guess some reading will be required.

Let us know how it goes in case someone else has this problem as well.

**I just realized you might not know how to start/stop the wpa_supplicant process. Here's how in Gnome.
To stop: ```
go to the menu and choose Applications->System Tools->System Monitor
Select the Processes tab and scroll down to find the wpa_supplicant process.
Highlight it and click "End Process" at the bottom right of the window.
You will need your password to complete this.
``` To start: Open a terminal and use the same command that is issued to start it normally. For my computer:```
Applications->Accessories->Terminal
sudo wpa_supplicant -B -i eth1 -c /etc/wpa_supplicant.conf -D ipw -w -dd
enter password when requested
```

---

### Post by magisterludi on 2006-03-11
Well, thank you.

Quoting the documentation was really not necessary.

I will try to commenting out lines and post here about it.
This may take some time, because. wpasupplicant shows this
behavior quite randomly.

---

### Post by matthew on 2006-03-11
[quote=magisterludi]Well, thank you.

Quoting the documentation was really not necessary.[/quote]I did it in the interest of helping new users who may not be as adept that may stumble on this thread. Sorry if it made you feel a little less respected. Anyway, I hope this helps you out...

---

### Post by magisterludi on 2006-03-13
Hi again,

I tried several tweaks in the wpasupplicant.conf.
The problem is most certainly cause by the ap_scan option.

Here are my results:

using ap_scan=2 as I have before connects fine, but might disconnect
 and then reconnect to some other network at random times or after suspend.

ap_scan=0 and ap_scan=1 won't connect to the encrypted network
or any other (I do not have configured any others) networks.

The other options make no difference.

Since the ap_scan option controls the scan behaviour I think it might
be a problem with the madwifi driver I use.

But it might be cause by my network scripts, too. So I post them:

/etc/network/interfaces
```

iface ath0 inet dhcp

auto home
iface home inet static
        address 192.168.1.55
        netmask 255.255.255.0
        network 192.168.1.0
        broadcast 192.168.1.255
        gateway 192.168.1.1
        pre-up /etc/network/if-pre-up.d/madwifiup
        pre-up /etc/init.d/wpasupplicant stop
        post-up /etc/init.d/wpasupplicant start
        post-up cp /etc/resolv.conf.norm /etc/resolv.conf
        post-down /etc/init.d/wpasupplicant stop
        post-down /etc/network/if-post-down.d/madwifidown

```

/etc/network/if-pre-up.d/madwifiup:

```

#!/bin/sh

modprobe ath_pci

```

post-down /etc/network/if-post-down.d/madwifidown:
```

#!/bin/sh
rmmod ath_pci
rmmod ath_rate_sample
rmmod wlan_tkip
rmmod wlan_ccmp
rmmod wlan
rmmod ath_hal

```

---

### Post by matthew on 2006-03-15
Well, I'm glad a little progress was made in figuring out the problem. Since I don't use madwifi I hate to admit I have no idea what to do next.

I should have thought of this earlier, but I'm going to move this thread to the networking forum in the hopes someone with more experience will see it and have an idea of what to do.

Anyone else want to jump in here?

---

