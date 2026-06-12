---
title: "No Network On Laptop When No User Logged In"
date: 2009-01-15
forum: Networking &amp; Wireless
---

### Post by PointyWombat on 2009-01-15
Hi,

Just wondering how I can activate the wireless network on my Thinkpad w/gOS (8.04) prior to logging in with a user account. At the login screen, if I open a separate console(<ctrl>-<alt>-F1) and try to start networking, (/etc/init.d/networking start), it show's OK, but no dice... probably something simple, but I can't find it.. any help appreciated. This is in efforts to get autofs working w/wireless. Autofs with wired network in no problem.

Thanks,

---

### Post by Chas_E_Erath on 2009-01-15
I've futzed around with this issue on one of my desktops and I finally have it connecting and nfs-mounting /home automagically.  But what I did was to put the following into my /etc/rc.local file.  

(Please note:  I really don't know what the h*ll I'm doing...  I've only just found a method to bring up the wireless at boot and haven't gotten around to cleaning things up yet (which is to say, there are a lot of loose ends))

So, first thing - I have this at the end of my rc.local file:

```

#
#  First, shut things down.
# 
/etc/init.d/networking stop
ifconfig wlan1 down
/etc/init.d/avahi-daemon stop
/etc/init.d/NetworkManager stop
#
#  Next, bring things back up
#
iwconfig wlan1 essid NETWORK-NAME
ifconfig wlan1 192.168.1.3 up
wpa_supplicant -dd -Dwext -iwlan1 -c /etc/wpa_supplicant/wpa_supplicant.conf &
mount.nfs skink:/home /home
/etc/rc.wireless_init.dhclient


```

My wpa_supplicant.conf file looks like this:

```


chas@franky:~$ cat /etc/wpa_supplicant/wpa_supplicant.conf 
ctrl_interface=/var/run/wpa_supplicant 
ctrl_interface_group=0
network={
  ssid="NETWORK-NAME"
  proto=RSN
  key_mgmt=WPA-PSK
  pairwise=CCMP TKIP
  group=CCMP TKIP
  psk="NETWORK-PASSWORD"
}


```


I found I had to put dhclient into a different script - maybe to give the wireless card some time to settle down.  That file then, looks like this:

```


chas@franky:~$ cat /etc/rc.wireless_init.dhclient 
dhclient wlan1


```


I've found that the avahi thingy, and the network-manager thingy are great for connecting to something after you're logged in.  But like you, I want it to connect at boot.  That's all I have to say - some of it might help, some might not - hopefully it will help.

Chas.

---

