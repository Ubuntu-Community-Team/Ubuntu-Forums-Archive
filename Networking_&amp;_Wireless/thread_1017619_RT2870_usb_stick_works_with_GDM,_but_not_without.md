---
title: "RT2870 usb stick works with GDM, but not without"
date: 2008-12-21
forum: Networking &amp; Wireless
---

### Post by kellner on 2008-12-21
I am trying to connect the D-LINK DWA-140 wireless usb adapter to the D-LINK DIR-635 router, with WPA2 encryption. 

This works with the rt2870sta module on Intrepid Ibex within Gnome, using the Network Manager applet. 

Problem is: I want to reconfigure the computer to a server within the local network. No graphical interface, no X running, just a LAMP setup with ssh access. 

So the challenge is to make the wlan configuration work at startup, without Gnome. I haven’t been able to achieve this and would appreciate any help – especially, if someone could post a working configuration file RTA2870.DAT! 

I downloaded the latest driver from [http://www.ralinktech.com](http://www.ralinktech.com), built and installed it, following instructions in the README file. 

The module rt2870sta is properly loaded at boot-time and shows up under usbcore with lsmod. So this much is covered – it’s just the connection that doesn’t work without GDM, so there must be something wrong with the parameters I entered in the configuration files. 

The router is set to DHCP mode with 192.168.0.1. 

/etc/network/interfaces contains: 
iface ra0 inet dhcp
auto ra0

The wireless parameters are stored in /etc/Wireless/RT2870STA/RT2870STA.dat (also tried moving this into /etc/Wireless/, but this didn’t help). 
These are the parameters I changed in the *.dat file: 

SSID=myessid
AuthMode=WPA
EncrypType=TKIP
WPAPSK=my_wpa2_key_in_hex

I also have a wpa_supplicant.conf in /etc, but this doesn’t seem to be necessary (removed it – no change).

iwconfig shows the device ra0 with the proper ESSID and Nickname, but Access Point “not associated”. 

ifconfig shows ra0 without an IP address, and a device ra0:avahi with IP 169.254.9.199. 

ifdown ra0, followed  by ifup ra0 has DHCPDISCOVER on ra0 to 255.255.255.255 port 67 time out. 

I also tried using a static address (192.168.0.198), but to no avail. The connection with the AP just isn’t established, even though iwlist scan shows the AP with a sufficiently strong signal. 

I suspect that something is wrong with the way I entered the wpa2-psk key in the *.dat file.

I tried various possibilities: 

1.) enter hex key in WPAPSK
2.) do not enter anything in WPAPSK, set DefaultKeyID=1, Key1Type=0, Key1Str=my_key_in_hex, or Key1Type=1 and Key1Str=”my_key_in_ascii”. Both settings resulted in error messages that the key didn’t have the right length (it’s 8 in ascii, 64 in hex). 

Boot protocol ends with: “eth0: link is not ready”.

As I said: the strange thing is that it works within the GUI, but not from the command-line. 

Thanks in advance for any hints how to resolve this,

---

### Post by kellner on 2008-12-22
I managed to get it to work in the end. 

1.) When compiling the driver, change settings in os/linux/config.mk to: 

```
HAS_WPA_SUPPLICANT=y
HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=n
``` 

2.) completely remove NetworkManager: 
```

sudo apt-get –purge remove network-manager network-manager-gnome
```

3.) use wpa supplicant: edit /etc/wpa_supplicant/wpa_supplicant.conf according to the network's setup

4.) enter use of wpa supplicant in /etc/network/interfaces:

```
iface ra0 inet dhcp
wpa-driver wext
wpa-conf /etc/wpa_supplicant/wpa_supplicant.conf
```

That's it.

---

