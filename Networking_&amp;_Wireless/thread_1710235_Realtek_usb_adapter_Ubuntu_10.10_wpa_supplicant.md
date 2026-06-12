---
title: "Realtek usb adapter Ubuntu 10.10 wpa_supplicant?"
date: 2011-03-19
forum: Networking &amp; Wireless
---

### Post by uqueia on 2011-03-19
[FONT=Times New Roman][SIZE=3]Hello,
 
Ubuntu 10.10 - the Maverick Meerkat – (Installed .iso from cd)
 
The router has a password that I'm not sure if is wep or wpa.
When I manually put in the address, netmask,gateway, dns,domain my Realtek usb adapter is connecting to the router but is not receiving packets.
 
I got the driver installed with ndiswrapper.
 
I'm trying to figure out wpa_supplicant
 
I tested out an unlocked network and it loaded internet up just fine.
 
Any pointers?
 
Thanks
[/SIZE][/FONT]

---

### Post by chili555 on 2011-03-19
> Any pointers?Yes.> manually put in the address, netmask,gateway, dns,domain Take all that stuff out and reboot. Now click the Network Manager icon and see your network. Click it and the pop-up should ask for the right password in the right format. In other words, if the network is WEP, it will ask for your WEP key, etc. Provide it and connect.

Less is more.

---

### Post by pygo on 2011-03-20
I'm also currently having difficulties.
Sorry, but network manager is a pile of ... well, I'll leave that talk for outside. 

First, run this: sudo apt-get purge network-manager ; sudo apt-get remove network-manager
There, now you can manually edit information in /etc/network/interfaces for wifi and normal ethernet adapters in the regular fashion. And magically, it all comes up at boot, without having to login. If you're a developer, please fix network-manager so it actually works. Thanks!

Now for wifi to come up at boot, before any user logs in I understand I need the following in my /etc/network/interfaces file.

Currently I've got the following in /etc/network/interfaces Sometimes eth0 will grab an IP (if I have a network cable plugged in, currently for troubleshooting from my laptop. Othertimes it won't bring up eth0 (as if "auto eth0" were commented out) but bring up the wlan0 interface and properly connect to my selected wifi network.
```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp
#address 192.168.2.2
#netmask 255.255.255.0

pre-up wpa_supplicant -Dwext -iwlan0 -c/etc/wpa_supplicant.conf
post-down killall -q wpa_supplicant
auto wlan0
iface wlan0 inet dhcp

```Here's what's in /etc/wpa_supplicant.conf
```

#ap_scan=1
ctrl_interface=/var/run/wpa_supplicant

network={
        ssid="wifi"
        scan_ssid=1
        proto=WPA RSN
        key_mgmt=WPA-PSK
        pairwise=TKIP
        group=TKIP
        psk=(generated key from running the below command)
}

```To generate the psk, run the following.
```

root@xbmc:~# wpa_passphrase ssid ascii_password
network={
    ssid="ssid"
    #psk="ascii_password"
    psk=5680bcf2e9bb90deb51b9a67a759f3bfb6a048c78cb5c22c2fc46ca99e363a90
}
root@xbmc:~# 


```Note: I've come to the above config from a few different posts while searching on ubuntu forums. My conclusion is that there isn't really a clean cut and easy way to make wifi connect at startup, before any users login. I find it best, as mentioned above, to completely remove network-manager.

sudo dhclient (interface) is the command to use to grab a dhcp address. Be careful though as every so often whatever you have stored in network-manager settings, or /etc/network/interfaces file will override your settings from the CLI.

P.S. Sorry for venting. Been having some issues with networking and it's not limited to Ubuntu. Best to just go wired if you can, but sadly my dd-wrt router I was using as an AP has kicked the bucket. And yes, I spent $65 to "solve" this issue by going wired and not using broken wireless. Ho hum.
EDIT: Oh, and I see this is my first post. Guess I've been lurking a lot and not posting. Hopefully my first post is helpful.


EDIT2: Scratch that, the wireless isn't really connecting so I've removed the config altogether. I'll splurge on a new AP as soon as I have some extra cash. And just to confirm, yes, the wireless adapter connects just fine after I've logged in and do it manually. I even get decent signal strength out of it.

---

### Post by uqueia on 2011-03-23
I tried making the /etc/wpa_supplicant.conf but the name of the network is two words instead of one. When I ran

```
root@xbmc:~# wpa_passphrase ssid ascii_passwordnetwork={    ssid="ssid"    #psk="ascii_password"    psk=5680bcf2e9bb90deb51b9a67a759f3bfb6a048c78cb5c22c2fc46ca99e363a90}root@xbmc:~#
```
it put the first word of my ssid into the ssid="" field and it put the second word of my ssid into the #psk="" field.
 
Do I have to change my ssid to one word as this is my roommates network?

---

### Post by uqueia on 2011-03-24
[FONT=Times New Roman][SIZE=2][FONT=Verdana]> [FONT=Times New Roman][SIZE=2][FONT=Verdana]Take all that stuff out and reboot. Now click the Network Manager icon and see your network. Click it and the pop-up should ask for the right password in the right format. In other words, if the network is WEP, it will ask for your WEP key, etc. Provide it and connect.[/FONT]
[/SIZE][/FONT][/FONT][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT] 
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT] 
[FONT=Times New Roman][SIZE=3]I did but I get disconnected from the router.[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]The little network icon is searching and the password window keeps popping up every minute or two.[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]I'm using the standard wep 40/i28 passcode.[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]My friends ipod touch connects just fine with the password.[/SIZE][/FONT]

---

### Post by pygo on 2011-03-28
So, I've done some more troubleshooting.
It appears that eth0 won't come up if I have entries for wlan0 in /etc/network/interfaces. I think more specifically the pre-up and post-down entries may be breaking it. If I remove the pre-up and post-down entries, eth0 is able to come up. I think a possible "solution" would be to add a @reboot entry to run the wpa_supplicant command in crontab. This didn't work as expected though since randomly it would disconnect from the wireless and wpa_supplicant would need restarting. I don't have the output handy, but it went on an endless loop of trying to connect and not connecting.

To solve the issue once and for all I have ordered a refurbished wrt54gl from ncix.com for $35. It should be arriving within the next few days.

If any one wants log message outputs or anything else that may be helpful, please let me know as I would greatly like this issue to be solved.

---

