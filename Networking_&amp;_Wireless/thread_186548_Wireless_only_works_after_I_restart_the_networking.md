---
title: "Wireless only works after I restart the networking service"
date: 2006-06-02
forum: Networking &amp; Wireless
---

### Post by kmkittre on 2006-06-02
I have setup my wireless card with wpa and it works great.  However, after booting I have to do this:
```

/etc/init.d/networking restart
```

Can anyone tell me how to get the wireless to work at boot?

This is my /etc/network/interfaces file:

```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp
        wpa-driver madwifi
        wpa-ssid transmatrix
        wpa-key-mgmt WPA-PSK
        wpa-psk <hidden for obvious reasons, but my passkey is here>

auto wlan0
iface wlan0 inet dhcp
```

thanks!

---

### Post by minio on 2006-06-02
Try this:
```
auto ath0
iface ath0 inet dhcp
        wpa-driver madwifi
        wpa-conf /etc/wpa_supplicant/wpa_supplicant.conf
```

but you have to create wpa_supplicant.conf file and copy it to /etc/wpa_supplicant
The file should look like this:
```
ctrl_interface=/var/run/wpa_supplicant
ctrl_interface_group=0

eapol_version=1
ap_scan=2
fast_reauth=1

network={
        ssid="transmatrix"
        proto=WPA
        key_mgmt=WPA-PSK
	wep_key=<hidden for obvious reasons, but your passkey is here>
}
```

for details about wpa_supplicant.conf:
 ```
man wpa_supplicant.conf
```
 
Using conf file works for me much better then setup parameters directly in /etc/network/interfaces (well settings in interfaces don't work for me at all, but i have ipw2200 card)

---

### Post by kmkittre on 2006-06-11
That did it!

Thanks, man.

I hope they find out why Network Manager doesn't work with the Cisco cards...
I'm a little hard-coded to my home wireless network with this setup.

---

### Post by joerenes on 2006-09-24
Just in case someone else finds this thread, I also had this problem, and resolved it by following a tip from [http://technically.us/n8/articles/2006/06/04/ubuntu-dapper-upgrade-wpa-upheaval]("http://technically.us/n8/articles/2006/06/04/ubuntu-dapper-upgrade-wpa-upheaval")

Just dump everything into /etc/network/interfaces and then add 
pre-up sleep 10 
before anything else in the stanza

---

### Post by Remasis on 2006-09-24
I'm having the same issue with a broadcom 4306 card. The wirless card won't show up in nm-applet and wifi-radar can't get an IP address until after I envoke a restart. I tried putting the "pre-up sleep" in my /etc/network/interfaces folder to no avail. Anyone have ideas?

Here's the post I made yesterday that didn't get any replies:

> Thanks in advance for any advice. Here is the issue:

I have had wireless working fine with WEP on my system before using the nm-applet. I have ndiswrapper working and the device shows up in ifconfig and iwconfig fine along with the properly loaded modules. This happened once before for a few reboots but then it worked fine and now it's happening again but it's more persistant than the first time.

I don't have any wireless options in the nm-applet. It's not a problem with the applet itself as I have also used wifi-radar to attempt to connect to networks. I can iwlist and scan available networks and they show up perfectly. The problem comes with attempting to actually connect with the networks. wifi-radar hangs on the "acquiring IP address" box and returns with a message "could not get IP address." Then wifi-radar shows "Connected to <my essid> ip(None)"

I've connected on my home network before as well as other ones. There are also a lot of other AP's in my area. I just can't figure out why it's having trouble with nm-applet and wifi-radar. Any help is GREATLY appreciated.

Update:
I seem to be able to get it to work if I run "invoke-rc.d networking restart" it manages to get an IP from my router then. If I attempt to connect via wifi-radar after this however, I still cannot get an IP. Any ideas??

---

