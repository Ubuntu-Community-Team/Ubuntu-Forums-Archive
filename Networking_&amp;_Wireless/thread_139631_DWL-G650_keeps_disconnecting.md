---
title: "DWL-G650 keeps disconnecting"
date: 2006-03-04
forum: Networking &amp; Wireless
---

### Post by other on 2006-03-04
First of all, when I start Ubuntu (Xubuntu), it stops at the part where it's setting up the network interfaces. It takes a really long while before it continues. Then when I log in, internet isn't working, but if I run *sudo dhclient*, internet works temporarily. Then I have to run this about every 30 seconds to keep the internet connection alive.

My /etc/network/interfaces:
```
auto lo
iface lo inet loopback

mapping hotplug
        script grep
        map eth0
        map ath0

auto eth0
iface eth0 inet dhcp

auto ath0
iface ath0 inet dhcp
wireless_essid <my ssid>
wireless_ap <ap's MAC address>
wireless_channel 11
#wireless_mode master
```

/etc/defaults/wpasupplicant:
```
ENABLED=1

OPTIONS="-w"
OPTIONS="-i ath0 -D madwifi -c /etc/wpa_supplicant.conf -w"
```

/etc/wpa_supplicant.conf:
```
ctrl_interface=/var/run/wpa_supplicant
ctrl_interface_group=0

eapol_version=1
ap_scan=1
fast_reauth=1

network={
	ssid="<my ssid>"
	scan_ssid=1
	proto=WPA
	key_mgmt=WPA-PSK
	psk=<my WPA key>
}
```

Any idea what I can do?

EDIT: I installed and ran pump, and now it seems to keep the connection alive.

---

### Post by other on 2006-03-05
Now the internet connection works fine, I don't have to do anything when I boot up. But it still gets stuck at "Configuring network interfaces" during bootup (though I just ctrl-C my way by it), how do I get rid of it? Or how do I configure it so that it doesn't get stuck?

---

### Post by bobnutfield on 2006-03-05
Just a thought.....I have had similar problems and discovered it was being caused by another wireless device being used in the house.  Routers are using 2.4Ghz band as do most other home wireless devices.  In my case, it was a using to send my TV signal upstairs.  When it was plugged in, it would intermittently knock me offline and fail to let an IP address be assigned at boot even though I was using a wired ethernet because the router is wireless (for my laptop).  I searched through the OS for days before I found that even the cordless telephone would know me offline.  When this happened, I could reboot the router and, BINGO, back on line just to be knocked off again in about 10 mins.  Frustrating before I figured it out.

Don't know if this will help, but thought I would suggest it.

Bob

---

### Post by other on 2006-03-05
[QUOTE=bobnutfield]Just a thought.....I have had similar problems and discovered it was being caused by another wireless device being used in the house.  Routers are using 2.4Ghz band as do most other home wireless devices.  In my case, it was a using to send my TV signal upstairs.  When it was plugged in, it would intermittently knock me offline and fail to let an IP address be assigned at boot even though I was using a wired ethernet because the router is wireless (for my laptop).  I searched through the OS for days before I found that even the cordless telephone would know me offline.  When this happened, I could reboot the router and, BINGO, back on line just to be knocked off again in about 10 mins.  Frustrating before I figured it out.

Don't know if this will help, but thought I would suggest it.

Bob[/QUOTE]

It turned out that it was just dhclient that was crappy, since I installed pump everything is working perfectly. My only problem now is:
> Now the internet connection works fine, I don't have to do anything when I boot up. But it still gets stuck at "Configuring network interfaces" during bootup (though I just ctrl-C my way by it), how do I get rid of it? Or how do I configure it so that it doesn't get stuck?

---

### Post by Lambert on 2006-03-05
[quote=other]It turned out that it was just dhclient that was crappy, since I installed pump everything is working perfectly. My only problem now is:

Now the internet connection works fine, I don't have to do anything when I boot up. But it still gets stuck at "Configuring network interfaces" during bootup (though I just ctrl-C my way by it), how do I get rid of it? Or how do I configure it so that it doesn't get stuck?[/quote] 
I've seen may people with this problem and I'm just wondering, did you also remove/uninstall dhclient?

There's got to be something odd with dhclient and certain routers. I've used a dwl-g650 and recently it's replacement the wna-2330 with dhclient and never had a problem.

You have two interfaces set with auto stanzas in your interfaces file. What might be happening is one inteface has no connection so it takes a minute before it stops trying and moves on in the bootup process. If you mainly use your wireless interface, remove the auto eth0 stanza from that file.

---

### Post by other on 2006-03-05
[QUOTE=Lambert]I've seen may people with this problem and I'm just wondering, did you also remove/uninstall dhclient?[/QUOTE]

No, I did not remove dhclient.

> You have two interfaces set with auto stanzas in your interfaces file. What might be happening is one inteface has no connection so it takes a minute before it stops trying and moves on in the bootup process. If you mainly use your wireless interface, remove the auto eth0 stanza from that file.

It still gets stuck. Could it be because wpa_supplicant isn't started until later?

EDIT: Yes, that was it. I did what was said in [this thread](http://www.ubuntuforums.org/showthread.php?t=90450):
> **5. Configure wpasupplicant to start when booting**

It is essential that wpasupplicant run after your wireless card driver is loaded but before Ubuntu attempts to configure it via DHCP or whatever. Since the scripts in /etc/rcS.d are executed in ascending alphanumeric order, this meant, in the case of my setup, after the hotplug (run level 40) but before networking (also run level 40). Therefore, I needed the startup script to be alphabetically between "hotplug" and "networking", so I called it "iwpa":

```
cd /etc/rcS.d
sudo ln -s ../init.d/wpasupplicant S40iwpa
```

Now wpasupplicant will startup at the appropriate time each time you have to reboot.

...and now it works. Though wpa_supplicant is trying to start again later, but it doesn't since it's already started. Just out of curiosity, how do I remove that?

---

### Post by jdmpike on 2006-09-15
I gotta tell you guys, this was just the post that I needed to correctly configure my WPA enabled wireless card in Xubuntu.

This change to /etc/network/interfaces was the other magic

```

auto ath0
iface ath0 inet dhcp
pre-up wpa_supplicant -Bw -Dmadwifi -iath0 -c/etc/wpa_supplicant.conf
post-down killall -q wpa_supplicant

```

I also set my eth0 interface is now defined as allow-hotplug rather than auto because it isn't ever plugged in... My machine boots so much faster now, it is brilliant!

Thanks for the help getting me connected and helping me stay that way!

Peace, love, and ubuntu,

jdmpike

---

