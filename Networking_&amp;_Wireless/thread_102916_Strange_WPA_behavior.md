---
title: "Strange WPA behavior"
date: 2005-12-13
forum: Networking &amp; Wireless
---

### Post by TrinitronX on 2005-12-13
I finally figured out how to get wpa_supplicant compiled/working with madwifi, and now I'm getting some strange connection behavior.  I have no idea what's going on, but it seems like some hardware fight is going on between wpa_supplicant and madwifi... or something... :p 
So.. here's what it does.. I start up my computer, and type the following command: 
trinitronx@Arcturus:~$ sudo wpa_supplicant -Dmadwifi -iath0 ```
-c/etc/wpa_supplicant.conf -dd
```
It spits out a bunch of stuff, finds my access point, and looks like it's connecting... but when I try to open up a page in firefox, and it says it can't connect.  I also notice that my network monitor tray icon says there are no active connections.  Ok.. so I click it and change it to ath0, and then the console spits out more stuff (the same basic stuff but with different keys)... but it still doesn't work.
So.. I stop wpa_supplicant with ctrl+C, disable my network connection, re-enable it, and try again.  It spits out more stuff, and sometimes it works... sometimes it doesn't.  I can't figure out what the problem is with it... the only thing I can think of right now is probably the network settings in the menu for ubuntu.  I previously had it set up for WEP, and didn't want to change anything... since trying to use DHCP with my router had previously been failing.  Instead I had to set it up as a static IP, and put in the dns servers reported by my router.
So... I have attached a log of the connection looking like it's working.. but not actually working, in the wap_debug_fail.txt file, and a log of it while it's really working in the wap_debug_success.txt file.

---

### Post by TrinitronX on 2005-12-13
Nevermind.  I finally figured out my problems.  I had to reconfigure my /etc/network/interfaces file so that there were no associated values for my ath0 interface, and so it was using dhcp.

So.. once I got everything configured correctly in there, wpa supplicant worked!
I also figured out how to configure WPA2 encryption using AES!

For reference to those still struggling with this, here are my configuration files:
/etc/network/interfaces  (only the part that pertains to my ath0 interface)
```

auto ath0

iface ath0 inet dhcp
# these two lines set up wpasupplicant to start in the boot sequence
# only use these after making sure you can connect using terminal commands
pre-up /etc/init.d/wpasupplicant start
pre-up sleep 5
# this line kills the wpa_supplicant process at shut down
post-down killall -p wpa_supplicant

```

/etc/wpa_supplicant.conf
```

# Minimal /etc/wpa_supplicant.conf to associate with open
#  access points. Please see 
#  /usr/share/doc/wpasupplicant/wpa_supplicant.conf.gz for more complete
#  configuration parameters.

ctrl_interface=/var/run/wpa_supplicant
ctrl_interface_group=0

eapol_version=1
ap_scan=1
fast_reauth=1

### Associate with any open access point
###  Scans/ESSID changes can be done with wpa_cli

network={
	ssid="my ssid"
	key_mgmt=WPA-PSK
	proto=WPA2
	pairwise=CCMP
	psk=<My PSK Removed>
}


```

Instead of using an ascii key for the *psk* variable, I used a hex key made with: ```
wpa_passphrase "my ssid" "mypassword"
```
This command will automatically generate a network{} block to be used in /etc/wpa_supplicant.conf.  You can use this block if you want your password actually in the file for reference.
The output of this would be something like: ```
network={
        ssid="my ssid"
        #psk="mypassword"
        psk=9cdf36d8511fc9d39f309cc52bc59635b92040abefb2179f5d7e94c57c340587
}

```

/etc/default/wpasupplicant (used to pass command line options to wpa_supplicant at startup)
```
# /etc/default/wpasupplicant

# WARNING! Make sure you have a configuration file!

ENABLED=1

# Useful flags:
#  -D <driver>		Wireless drive, typically optional.
#  -i <ifname>		Interface
#  -c <config file>	Configuration file
#  -d 			Debugging (-dd for more)
#  -w			Wait for interface to come up

# See the manual page wpa_supplicant(1) for more options and information.

OPTIONS="-iath0 -Dmadwifi -c/etc/wpa_supplicant.conf"
#OPTIONS="-w"

# EXAMPLES:

# OPTIONS="-i wlan0 -D hostap -c /etc/wpa_supplicant.conf"
# OPTIONS="-i ath0 -D madwifi -c /etc/wpa_supplicant.conf"

```

Now I boot up my computer, and it just works!

Note that this setup uses WPA2 with AES (CCMP) encryption.  If you want TKIP instead for some reason, change "CCMP" in /etc/wpa_supplicant.conf to "TKIP".  This setup also assumes dhcp is being used. If for some reason you need static IP assignment, in your /etc/network/interfaces file, use:
```

auto ath0
iface ath0 inet static
address 192.168.0.101  #example ip's are used here, change according to your network if needed
netmask 255.255.255.0
gateway 192.168.0.1
# these two lines set up wpasupplicant to start in the boot sequence
# only use these after making sure you can connect using terminal commands
pre-up /etc/init.d/wpasupplicant start
pre-up sleep 5
# this line kills the wpa_supplicant process at shut down
post-down killall -p wpa_supplicant

```

I am also using the latest version of the madwifi drivers, and the latest cvs version of wpa_supplicant (configured/compiled manually for use with madwifi).  I can't guarantee that these configuration files will work with older versions of wpa_supplicant and madwifi.. but they should probably work.

---

### Post by Hangetsu on 2006-03-23
Trin, thank you VERY MUCH for this writeup!  It got my connectivity working without a hitch!!!

---

### Post by TrinitronX on 2006-04-04
Thanks... glad this helped :D.

I'm now working on getting rid of a new issue in Dapper flight 6 with the network manager app and atheros based cards.  Apparently with the combination of madwifi drivers packaged in dapper and an atheros card (D-Link DWL-g520) , background scanning causes uncontrollable network disconnects.  If anyone is having this same issue, I've reported it as bug #37821 in malone.  [https://launchpad.net/malone/bugs/37821](https://launchpad.net/malone/bugs/37821)

---

