---
title: "DHCP works on every WIFI netwrk except my uni network! PLS HELP!! :)"
date: 2009-05-06
forum: Networking &amp; Wireless
---

### Post by shrewd.user on 2009-05-06
hi all :)

i'm having a strange issue only when trying to connect to my university wireless...

i have a new laptop with a newer ralink wifi-n card, and it connects to most networks just fine, but something goes awry with my university wifi.

on my old laptop i used to be able to connect just fine, via the console or network manager.

```
# IEEE 802.1X with dynamic WEP keys using EAP-PEAP/MSCHAPv2

ctrl_interface=/var/run/wpa_supplicant

network={
    ssid="UNIwireless"
    key_mgmt=IEEE8021X
    eap=PEAP
    phase2="auth=MSCHAPV2"
    identity="students\jsmith"
    password="888883888"    
}

```the strange thing is that i can actually connect, however when i (or network manager) tries to use DHCP (dhclient) it just can't see anything / get an ip... this didn't happen on my older hardware and dhcp works fine on all my other wifi networks...


any of you seasoned professionals know whats going on?

---

### Post by shrewd.user on 2009-05-06
just pulled this out of my system log, this is where it appears to go awry
```
arnlap dhclient: DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 3
May  6 11:19:00 arnlap dhclient: DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 7
May  6 11:19:07 arnlap dhclient: DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 7
May  6 11:19:08 arnlap kernel: [  283.646626] ===>rt_ioctl_giwscan. 20(20) BSS returned, data->length = 3015
May  6 11:19:14 arnlap dhclient: DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 11
May  6 11:19:25 arnlap dhclient: DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 12
May  6 11:19:37 arnlap dhclient: DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 20
May  6 11:19:41 arnlap NetworkManager: <info>  Device 'ra0' DHCP transaction took too long (>45s), stopping it. 
May  6 11:19:41 arnlap NetworkManager: <info>  ra0: canceled DHCP transaction, dhcp client pid 3683 
May  6 11:19:41 arnlap NetworkManager: <info>  Activation (ra0) Stage 4 of 5 (IP Configure Timeout) scheduled... 
May  6 11:19:41 arnlap NetworkManager: <info>  Activation (ra0) Stage 4 of 5 (IP Configure Timeout) started... 
May  6 11:19:41 arnlap NetworkManager: <info>  Activation (ra0/wireless): could not get IP configuration for connection 'Auto LTUWireless'. 
```

---

### Post by shrewd.user on 2009-05-06
bump?

---

### Post by dandnsmith on 2009-05-06
Looks like you need to extend the time for which it tries to get the address from the server, and perhaps get it to retry automatically.

I've no idea where the relevant script is, but try /etc/init.d

---

### Post by gocek on 2009-05-06
There also might be an issue with RaLink cards in Jaunty, not sure which distribution you're currently at.
But as for me it looks like that: I have two wifi cards, one is RaLink chipset (rt73usb) and one is Realtek's (rtl8180). The first one hangs when negotiating IP address (doesn't get any DHCP offer, just like in your case) and the second one (which has worse signal) gets IP at once and works flawlessly.
Same computer, same access point. Different behaviour ;) I also have to try ndiswrapper for my RaLink card, maybe it will be better, but I must say that it worked pretty well on ubuntu 8.10...
As a siednote: my RaLink card used to connect, even on Ubuntu 9.04. But after I've upgraded firmware in my access point, it never got any dhcp offer, that's weird. Oh, and it still works ok on Windows Vista.

---

