---
title: "wpa_supplicant and ndiswrapper"
date: 2009-08-30
forum: Networking &amp; Wireless
---

### Post by gareththered on 2009-08-30
Hi,

I've come to the end of my tethers with the linux driver for my Broadcom BC4311 wifi adapter on my laptop which is running Ubuntu Server 9.04.

I've installed ndiswrapper, a Windows driver and wpa_supplicant.

Here is my wpa_supplicant.conf file:-
```
network={
	ssid="GTR"
	proto=RSN
	key_mgmt=WPA-PSK
	pairwise=CCMP TKIP
	group=CCMP TKIP
	psk=<my psk code>
}
```
which is stored in /etc.

If I run```
sudo wpa_supplicant -Dwext -iwlan0 -c/etc/wpa_supplicant.conf
```
i get the following on the terminal```
CTRL-EVENT-SCAN-RESULTS 
Trying to associate with 00:1f:9f:d6:39:b7 (SSID='GTR' freq=2412 MHz)
Associated with 00:1f:9f:d6:39:b7
WPA: Key negotiation completed with 00:1f:9f:d6:39:b7 [PTK=CCMP GTK=TKIP]
CTRL-EVENT-CONNECTED - Connection to 00:1f:9f:d6:39:b7 completed (auth) [id=0 id_str=]
```and I can ping the server.  If, on the other, hand I add the '-B' option to make it a daemon:- ```
sudo wpa_supplicant -B -Dwext -iwlan0 -c/etc/wpa_supplicant.conf
``` or configure /etc/network/interface with a pre-up consisting of the same line (with the -B option) then I cannot ping the server!
I ran it as a daemon again, this time with the '-f' option to send it's output to a log file as follows:-
```
sudo wpa_supplicant -B -Dwext -iwlan0 -c/etc/wpa_supplicant.conf -f/home/gareth/wpalog.txt
``` and the log file contained the following:-```
CTRL-EVENT-SCAN-RESULTS 
Trying to associate with 00:1f:9f:d6:39:b7 (SSID='GTR' freq=2412 MHz)
Associated with 00:1f:9f:d6:39:b7
WPA: Key negotiation completed with 00:1f:9f:d6:39:b7 [PTK=CCMP GTK=TKIP]
CTRL-EVENT-CONNECTED - Connection to 00:1f:9f:d6:39:b7 completed (auth) [id=0 id_str=]
``` which is identical to what I received when I ran wpa_supplicant in the foreground!

Does anyone have any idea why I can ping this server when wpa_supplicant is running in the foreground but not when it's running as a daemon?

Many thanks in advance!

---

### Post by kevdog on 2009-08-30
Do you have a route set up and a dns server?  What server are you trying to ping?

---

### Post by gareththered on 2009-08-31
Yes, all other settings are correct as I can ping when I run wpa_supplicant in the foreground.

I'm actually pinging this server from an Ubuntu desktop which is on the same wireless network.

The only difference is that with wpa_supplicant running as a daemon (-B option) the server is not online and won't reply, while when its in the foreground it is online and replies to a ping.

The output of wpa_supplicant is the same both times, but one works while the other doesn't.

Thanks,

Gareth

---

### Post by gareththered on 2009-08-31
Also....

If I remove the linux drivers from the blacklist and reboot I can ping the server with wpa_supplicant running in the foreground, as a daemon (-B option) or launched from the /etc/network/interfaces' pre-up line.

This issue only seems to happen when running wpa_supplicant with ndiswrapper!!

---

### Post by easytaker on 2009-08-31
Jumping into the thread as I'm having similar problems.

Broadcom bcm4318 driver with ndiswrapper, trying to authenticate with WPA-PSK without success using wpa_supplicant.

Questions...

does gnome-network-manager configure wpa_supplicant.conf accordingly when it asks you for WPA passphrase? If so where is that config? I had no wpa_supplicant.conf on my /etc so I had to create one myself.

My network is being detected but Authentication times out and network-manager keeps asking me my WPA password.

---

### Post by gareththered on 2009-09-01
NetworkManager controls wpa_supplicant differently and without the file '/etc/wpa_supplicant.conf' or '/etc/network/interfaces'.  I'm using these files as I am using Ubuntu Server which has no GUI and therefore no Network Manager.

If you look in the output of 'ps ax' you will see something similar (this is from my Ubuntu Desktop powered laptop):-
```
 2928 ?        S      0:00 /sbin/wpa_supplicant -u -f /var/log/wpa_supplicant.log
```The '-u' command line option allows wpa_supplicant to be controlled via DBus, which, I presume, is how Network Manager controls it.

I've resolved my slow network by reverting to the linux driver and updating the firmware using 'b43-fwcutter' which is a package that updates the Broadcom firmware to the latest version.

I've confirmed that it works well using Netpipe-TCP which shows the link to my linux powered router to peak at about 17Mb/sec; a similar value to the link between my Ubuntu Desktop powered laptop and the router.  I have a RT2500 chipset media server which only manages about 2Mb/sec to the router, so that's the next task!

Good luck!

---

