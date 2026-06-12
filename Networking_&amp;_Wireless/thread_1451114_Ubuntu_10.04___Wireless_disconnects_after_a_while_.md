---
title: "Ubuntu 10.04  : Wireless disconnects after a while with netgear wn111 v2"
date: 2010-04-10
forum: Networking &amp; Wireless
---

### Post by donya16 on 2010-04-10
My wireless disconnects after around 10 minutes.
It does not reconnect automatically. I've to pull out the usb dongle and then put it  back in to connect again.

> lsusb
Bus 004 Device 002: ID 0461:4d0f Primax Electronics, Ltd 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 04f2:0841 Chicony Electronics Co., Ltd 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
**Bus 002 Device 005: ID 0846:9001 NetGear, Inc. WN111 v2 802.11n**
Bus 002 Device 004: ID 058f:6362 Alcor Micro Corp. Hi-Speed 21-in-1 Flash Card Reader/Writer (Internal/External)
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 03f0:110c Hewlett-Packard 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hubFollowing the daemon.log when this happens.

> Apr  9 22:37:37   wpa_supplicant[978]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Apr  9 22:37:37   NetworkManager: <info>  (wlan0): supplicant connection state:  completed -> disconnected
Apr  9 22:37:38   NetworkManager: <debug> [1270877858.001200] periodic_update(): Roamed from BSSID 00:21:29:88:3D:3B (This network is wired) to (none) ((none))
Apr  9 22:37:38   NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Apr  9 22:37:39   wpa_supplicant[978]: WPS-AP-AVAILABLE 
Apr  9 22:37:39   wpa_supplicant[978]: Trying to associate with 00:21:29:88:3d:3b (SSID='This network is wired' freq=2437 MHz)
Apr  9 22:37:39   NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Apr  9 22:37:49   wpa_supplicant[978]: Authentication with 00:21:29:88:3d:3b timed out.
Apr  9 22:37:49   NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> disconnected
Apr  9 22:37:49   NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Apr  9 22:37:50   wpa_supplicant[978]: WPS-AP-AVAILABLE 
Apr  9 22:37:50   wpa_supplicant[978]: Trying to associate with 00:21:29:88:3d:3b (SSID='This network is wired' freq=2437 MHz)
Apr  9 22:37:50   NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Apr  9 22:37:53   NetworkManager: <info>  (wlan0): device state change: 8 -> 3 (reason 11)
Apr  9 22:37:53   NetworkManager: <info>  (wlan0): deactivating device (reason: 11).
Apr  9 22:37:53   NetworkManager: <info>  (wlan0): canceled DHCP transaction, dhcp client pid 1988
Apr  9 22:37:53   NetworkManager: <WARN>  check_one_route(): (wlan0) error -34 returned from rtnl_route_del(): Sucess#012
Apr  9 22:37:53   avahi-daemon[972]: Withdrawing address record for 192.168.1.102 on wlan0.
Apr  9 22:37:53   avahi-daemon[972]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 192.168.1.102.
Apr  9 22:37:53   avahi-daemon[972]: Interface wlan0.IPv4 no longer relevant for mDNS.
Apr  9 22:37:53   NetworkManager: <info>  (wlan0): removing resolv.conf from /sbin/resolvconf
Apr  9 22:37:53   NetworkManager: <info>  Activation (wlan0) starting connection 'Auto This network is wired'
Apr  9 22:37:53   NetworkManager: <info>  (wlan0): device state change: 3 -> 4 (reason 0)
Apr  9 22:37:53   NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Apr  9 22:37:53   NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> disconnected
Apr  9 22:37:53   NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Apr  9 22:37:53   NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Apr  9 22:37:53   NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Apr  9 22:37:53   NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Apr  9 22:37:53   NetworkManager: <info>  (wlan0): device state change: 4 -> 5 (reason 0)
Apr  9 22:37:53   NetworkManager: <info>  Activation (wlan0/wireless): connection 'Auto This network is wired' has security, and secrets exist.  No new secrets needed.
Apr  9 22:37:53   NetworkManager: <info>  Config: added 'ssid' value 'This network is wired'
Apr  9 22:37:53   NetworkManager: <info>  Config: added 'scan_ssid' value '1'
Apr  9 22:37:53   NetworkManager: <info>  Config: added 'key_mgmt' value 'WPA-PSK'
Apr  9 22:37:53   NetworkManager: <info>  Config: added 'psk' value '<omitted>'
Apr  9 22:37:53   NetworkManager: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Apr  9 22:37:53   NetworkManager: nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Apr  9 22:37:53   NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Apr  9 22:37:53   NetworkManager: <info>  Config: set interface ap_scan to 1
Apr  9 22:37:53   NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Apr  9 22:37:54   wpa_supplicant[978]: WPS-AP-AVAILABLE 
Apr  9 22:37:54   wpa_supplicant[978]: Trying to associate with 00:21:29:88:3d:3b (SSID='This network is wired' freq=2437 MHz)
Apr  9 22:37:54   NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Apr  9 22:38:04   wpa_supplicant[978]: Authentication with 00:21:29:88:3d:3b timed out.
Apr  9 22:38:04   NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> disconnected
Apr  9 22:38:04   NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Apr  9 22:38:05   wpa_supplicant[978]: WPS-AP-AVAILABLE 
Apr  9 22:38:05   wpa_supplicant[978]: Trying to associate with 00:21:29:88:3d:3b (SSID='This network is wired' freq=2437 MHz)
Apr  9 22:38:05   NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Apr  9 22:38:15   wpa_supplicant[978]: Authentication with 00:21:29:88:3d:3b timed out.
Apr  9 22:38:15   NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> disconnected
Apr  9 22:38:15   NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Apr  9 22:38:16   wpa_supplicant[978]: WPS-AP-AVAILABLE 
Apr  9 22:38:16   wpa_supplicant[978]: Trying to associate with 00:21:29:88:3d:3b (SSID='This network is wired' freq=2437 MHz)
Apr  9 22:38:16   NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Apr  9 22:38:26   wpa_supplicant[978]: Authentication with 00:21:29:88:3d:3b timed out.
Apr  9 22:38:26 heartofgold NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> disconnected
Apr  9 22:38:26 heartofgold NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Apr  9 22:38:28 heartofgold wpa_supplicant[978]: WPS-AP-AVAILABLE 
Apr  9 22:38:28 heartofgold wpa_supplicant[978]: Trying to associate with 00:21:29:88:3d:3b (SSID='This network is wired' freq=2437 MHz)
Apr  9 22:38:28 heartofgold NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Apr  9 22:38:35 heartofgold NetworkManager: <info>  wlan0: link timed out.
Apr  9 22:38:38 heartofgold wpa_supplicant[978]: Authentication with 00:21:29:88:3d:3b timed out.
Apr  9 22:38:38 heartofgold NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> disconnected
Apr  9 22:38:38 heartofgold NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Apr  9 22:38:39 heartofgold wpa_supplicant[978]: WPS-AP-AVAILABLE 
Apr  9 22:38:39 heartofgold wpa_supplicant[978]: Trying to associate with 00:21:29:88:3d:3b (SSID='This network is wired' freq=2437 MHz)
Apr  9 22:38:39 heartofgold NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Apr  9 22:38:49 heartofgold wpa_supplicant[978]: Authentication with 00:21:29:88:3d:3b timed out.
Apr  9 22:38:49 heartofgold NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> disconnected
Apr  9 22:38:49 heartofgold NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Apr  9 22:38:50 heartofgold wpa_supplicant[978]: WPS-AP-AVAILABLE 
Apr  9 22:38:50 heartofgold wpa_supplicant[978]: Trying to associate with 00:21:29:88:3d:3b (SSID='This network is wired' freq=2437 MHz)
Apr  9 22:38:50 heartofgold NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Apr  9 22:38:54 heartofgold NetworkManager: <info>  Activation (wlan0/wireless): association took too long.
Apr  9 22:38:54 heartofgold NetworkManager: <info>  (wlan0): device state change: 5 -> 6 (reason 0)
Apr  9 22:38:54 heartofgold NetworkManager: <info>  Activation (wlan0/wireless): asking for new secrets
Apr  9 22:38:54 heartofgold NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> disconnected
Apr  9 22:39:00 heartofgold wpa_supplicant[978]: Authentication with 00:00:00:00:00:00 timed out.
Apr  9 22:39:09 heartofgold NetworkManager: <info>  wlan0: link timed out.

---

### Post by Rofko on 2010-04-14
I have the same problem with this dongle. On 9.10.
Any ideas anyone?

---

### Post by dimitris233 on 2010-05-01
same problem here with 10.04....wifi disconnects and connects after new retry...any solution???

---

### Post by atulkakrana on 2010-05-03
Its a bug..I believe...i have internal broadcom wifi card...Wifi disconnects after a while and does not connect till I turn off and ON networking.
:confused:

---

### Post by flash63 on 2010-05-03
Hello,
netgear wn111v2 > Module ar9170usb (Atheros Otus)

Update the driver
```

sudo apt-get install linux-backports-modules-wireless-lucid-generic

```
Restart

@Rofko
with 10.04 the driver supports Draft-N now! Ubuntu 9.10:
```

sudo apt-get install linux-backports-modules-karmic

```

---

### Post by Tulainas on 2010-05-03
> **flash63 said:**
> Hello,
netgear wn111v2 > Module ar9170usb (Atheros Otus)

Update the driver
```

sudo apt-get install linux-backports-modules-wireless-lucid-generic

```
Restart

@Rofko
with 10.04 the driver supports Draft-N now! Ubuntu 9.10:
```

sudo apt-get install linux-backports-modules-karmic

```



I'm trying the first one... let me try it and i'll give you my advise. I'm on an AAO 105 netbook

---

### Post by karabasik on 2010-05-05
> **flash63 said:**
> Hello,
netgear wn111v2 > Module ar9170usb (Atheros Otus)

Update the driver
```

sudo apt-get install linux-backports-modules-wireless-lucid-generic

```Restart

@Rofko
with 10.04 the driver supports Draft-N now! Ubuntu 9.10:
```

sudo apt-get install linux-backports-modules-karmic

```

I'm trying to troubleshoot the same issue, when I'm running "sudo apt-get install linux-backports-modules-wireless-lucid-generic", the system returns the following error -> canot find package.
How do I get around it?

---

### Post by flash63 on 2010-05-05
You can download the packages here (Meta): [http://packages.ubuntu.com/search?keywords=linux-backports-modules-wireless-lucid-generic&searchon=names&suite=lucid&section=all](http://packages.ubuntu.com/search?keywords=linux-backports-modules-wireless-lucid-generic&searchon=names&suite=lucid&section=all)

an for the specific Kernel (example)
```
sudo apt-get install linux-backports-modules-wireless-2.6.32-21-generic
```
[http://packages.ubuntu.com/lucid/linux-backports-modules-wireless-2.6.32-21-generic](http://packages.ubuntu.com/lucid/linux-backports-modules-wireless-2.6.32-21-generic)

Attend to your version 32bit or 64bit and pae or not!

Kernel in use:
```
uname -a
```
respective
```
sudo apt-get install linux-backports-modules-wireless-$(uname -r)
```

---

### Post by karabasik on 2010-05-05
> **flash63 said:**
> You can download the packages here (Meta): [http://packages.ubuntu.com/search?keywords=linux-backports-modules-wireless-lucid-generic&searchon=names&suite=lucid&section=all](http://packages.ubuntu.com/search?keywords=linux-backports-modules-wireless-lucid-generic&searchon=names&suite=lucid&section=all)

an for the specific Kernel (example)
```
sudo apt-get install linux-backports-modules-wireless-2.6.32-21-generic
```[http://packages.ubuntu.com/lucid/linux-backports-modules-wireless-2.6.32-21-generic](http://packages.ubuntu.com/lucid/linux-backports-modules-wireless-2.6.32-21-generic)

Attend to your version 32bit or 64bit and pae or not!

Kernel in use:
```
uname -a
```respective
```
sudo apt-get install linux-backports-modules-wireless-$(uname -r)
```


I've enabled backports, but that didn't solve the problem, my wireless still disconnecting once a minute...

---

### Post by lotacus on 2010-05-07
I would like to add to this thread that I am using a dlink dwa-160 and 10.04 loads the ar9170usb f/w. After several minutes go by I notice that the link dies. Many have referred to this as the module crashing or the card loosing connection.

re-inserting the stick did not solve the problem. The only way to have ubuntu initialize the stick was to either log out and then log in or restart the computer.

At first I thought maybe it was some power-save function of the usb port (if there is such a thing implimented) that was mis-behaving, but eliminated that possibility after inserting a usb drive into the same usb port.

I did notice one oddity however before I noticed this problem. The physical kill switch or the F-key combination to kill the laptop's internal wireless would also kill the dlink usb wireless. I am not sure why this would be unless the dlink is sharing the same interrupt as the internal wireless.

Now I decided to try something different. I loaded the live disk in vmware (without installation) and directly connected the dlink dwa-160 to the guest os.

Ubuntu detected the device and I was able to connect to the access point as usual. I left the connection running and now, about an estimated 2 hours later, the dir-160 is still functioning as it should.

I believe this may have to do with other usb hubs/devices attached to the system which may be causing the problem, or perhaps some conflict with the laptops internal wireless and the ar9170usb f/w or even how Ubuntu see's and loads the two wireless devices. Maybe even a combination of both.

What I will do next is have the laptops internal wireless attached directly to the guest os (10.04) and see if the ar9170usb crashes or not.

---

### Post by jschille on 2010-05-07
I am also having the same problem with wireless disconnects.

NOTE: When I am at my apartment in San Diego I am using a WIRELESS G router and lose connection OFTEN.  But, when I am in LA using my WIRELESS N router I never lose the connection.

Would love to fix the problem with the disconnects though, quite annoying.

---

### Post by sumit_m84 on 2010-05-07
> **flash63 said:**
> You can download the packages here (Meta): [http://packages.ubuntu.com/search?keywords=linux-backports-modules-wireless-lucid-generic&searchon=names&suite=lucid&section=all](http://packages.ubuntu.com/search?keywords=linux-backports-modules-wireless-lucid-generic&searchon=names&suite=lucid&section=all)

an for the specific Kernel (example)
```
sudo apt-get install linux-backports-modules-wireless-2.6.32-21-generic
```[http://packages.ubuntu.com/lucid/linux-backports-modules-wireless-2.6.32-21-generic](http://packages.ubuntu.com/lucid/linux-backports-modules-wireless-2.6.32-21-generic)

Attend to your version 32bit or 64bit and pae or not!

Kernel in use:
```
uname -a
```respective
```
sudo apt-get install linux-backports-modules-wireless-$(uname -r)
```


After disconnecting Tata Photone Plus it is not connectin again. What to doooooo

---

### Post by lotacus on 2010-05-07
Just want to say that I blacklisted the laptops wlan adapter. sudo gedit /etc/modprobe.d/blacklist-wifi.conf  added the line "blacklist rtl8187" rebooted and everything, within my own scenario with the wifi problem, is working fine now.

In my case it seems there is some sort of conflict between the built-in wireless and the usb wireless.

---

### Post by kachkeis on 2010-05-09
Hi there,

Try this thread, it's for the WPN111 but i heard that it COULD be  helping for other Netgear adapters. Or  You just use it for inspiration to find a solution.

[http://ubuntuforums.org/showthread.php?t=1477931](http://ubuntuforums.org/showthread.php?t=1477931)

Cheers,
kachkeis :smile:

---

### Post by ngc2997 on 2010-05-29
Hi,

> **flash63 said:**
> [..]
with 10.04 the driver supports Draft-N now!
[..]

Are you sure it really does? I've just purchased a TP-Link TN821N which also uses the ar9170usb driver, and iwconfig says:

```

wlan0     IEEE 802.11bg  ESSID:"..."
```

So, no sign of an 'n' in there..

[Edit]
The device mentioned above is actually suffering from the same disconnection problem described in this thread (although at first I thought it was not). *sigh*

Installing the backports-modules has no effect here either; connection to an associated AP is still dropped intermittently. This happens while no other WiFi device is present on my system, so I guess it is rather not related to 'interferences' from other wireless devices. As [mentioned]("https://bugzilla.gnome.org/show_bug.cgi?id=620218") by one of the NetworkManager developers, the issue might perhaps be caused by the driver failing to properly handling periodic scanning. This would also correlate with the syslog showing this entry immediately before the connection is dropped:

```
Jun  1 07:04:43 Antares kernel: [ 3085.528009] No probe response from AP xx:xx:xx:xx:xx:xx after 500ms, disconnecting.

```

Best wishes,
Karsten

---

### Post by lotacus on 2010-06-16
well, the issue still remains. I thought blacklisting the internal driver for the laptop helped, but I was wrong. Since then I have been using ethernet.

This is becoming a very annoying problem. Someone would think that after SEVERAL releases, they would get it right. Apparently they are more concerned with social integration of the gnome desktop rather than fixing the actual operating system. I guess this sort of thing happens when open source software gets fragmented.

---

### Post by cspadijer on 2010-06-20
Ya.  Running a D-Link DWA-160 Rev A1.  It is using the AR9170_usb.  I have the exact same issue.  After 5-10 minutes the connection drops.

Connection only occurs when running in 802.11n mode.

As a temporary fix I changed my router to only accept 802.11g connections.
This solved the connection drop issue for me until the issue is fixed with 802.11n.

Not the solution I want as 802.11g is quite slow in comparison to 802.11n.
Hopefully its fixed soon.

---

### Post by jheartfred on 2010-06-25
> **cspadijer said:**
> Ya.  Running a D-Link DWA-160 Rev A1.  It is using the AR9170_usb.  I have the exact same issue.  After 5-10 minutes the connection drops.

Connection only occurs when running in 802.11n mode.

As a temporary fix I changed my router to only accept 802.11g connections.
This solved the connection drop issue for me until the issue is fixed with 802.11n.

Not the solution I want as 802.11g is quite slow in comparison to 802.11n.
Hopefully its fixed soon.

i would be doing this.. hopefully it would fix mine as well

---

### Post by cjmiller00 on 2010-06-28
same issue here as well.  

1. disconnects reguardless of load and 
2. has to be removed then reconnected to regain connection.  
3.  no updates helped. 
4. the b43XX driver did the same thing

any solutions.  is there a bug number on launchpad







i dont want to go back to Bill G but mobility is a priority for me and this worked fine with the bad mans software.

---

### Post by gusnz on 2010-07-03
The relevant bug is [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/540827](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/540827) so if this affects you, please login and click "This affects me" at the top of the screen and/or subscribe.

It appears to be an issue with the ar9170usb driver that is seriously breaking many/all cards based on the chipset (I have a TP-LINK TL-WN821N stick, very similar to the Netgear WN111v2). Any Wifi experts would be very welcome!

---

### Post by flash63 on 2010-07-04
Hello,
there's a problem with the Network-Manager too (disconnecting, Driver hangs).

Patches available by using the ppa sources. Add following lines to your software repositories:
```
deb http://ppa.launchpad.net/network-manager/trunk/ubuntu karmic main
deb-src http://ppa.launchpad.net/network-manager/trunk/ubuntu karmic main
```
Update
```
sudo apt-get update && sudo apt-get upgrade
```
Alternative LAN/WLAN-Manager Wicd.
```
sudo apt-get install wicd
sudo apt-get remove --purge network-manager network-manger-gnome
```

---

### Post by cspadijer on 2010-07-04
> **cspadijer said:**
> Ya.  Running a D-Link DWA-160 Rev A1.  It is using the AR9170_usb.  I have the exact same issue.  After 5-10 minutes the connection drops.

Connection only occurs when running in 802.11n mode.

As a temporary fix I changed my router to only accept 802.11g connections.
This solved the connection drop issue for me until the issue is fixed with 802.11n.

Not the solution I want as 802.11g is quite slow in comparison to 802.11n.
Hopefully its fixed soon.


Update: Switching my router to only accept 802.11g connections didn't solve the problem.  After further testing it just delayed the amount of time before the connection drops

---

### Post by netmanny on 2010-08-19
My problem got resolve when i remove  ar9271.fw from /lib/firmware
it looks like the driver or kernel loads that firmware instead of  ar9170.fw
Don't know why just know my netgear wn111v2 works now . just in G and never in "N". Also Using Wicd.

---

### Post by atulkakrana on 2010-08-21
NO MATTER WHAT I DO MY WIFI DISCONNECTS RANDOMLY....ONLY WHILE DOWNLOADING TORRENTS

Limit speed...turn off Wifi card power saver...Play Rhythmbox to prevent sleep/whatever....etc etc....nothing works...

I am a proponent of linux...i am using it for last 5 years...and when these problems can violently distract me..what will happen to new users....

Canonical and Ubuntu developers...please stop it...you have done enough....do not develop it any more...stop and concentrate on what you have developed already...

I ASSURE YOU THAT ONLY BECAUSE OF THIS PROBLEM>>>I WILL SHIFT TO WINDOWS 7....I personally believe that its easy to use Windows 7 and it is more stable then Ubuntu these days....

GO AWAY UBUNTU...

Atul Kakrana

---

### Post by 5HourButt on 2010-09-27
I have been struggling with this problem since I upgraded to 10.04. I thought perhaps it was fixed in the 10.10 beta and same deal. So, I found a perfect solution. I did a clean install of 9.1 and the WN111v2 connects and stays connected. Working right now. I have no clue what is going on since I am a total Linux noob. But all the frustration is gone. :P

---

### Post by 5HourButt on 2010-09-28
oops. . . :confused:   I just had the problem start again. The connection was lost and the WN111v2 was dark (no blue LED) and I unplugged it and then plugged it back in and got it going again. . . Sorry. . .

---

### Post by 5HourButt on 2010-10-02
I have to admit I can't get it fixed but I ruefully switched over to SUSE 11.3 and had the same issues but once I used YaST2 to set the network parameters it works perfectly. It stays connected and even when I close the lid on my laptop and then reopen it after a minute or even a day the networks connects instantly. I feel really bad having to switch away from Ubuntu since I love it but I had to solve the problem. :(

I am still a Ubuntu fan since I have another laptop (an HP) running it and it works just fine. It has a built in wireless card so no dongle.

---

### Post by robtynan on 2010-11-05
This is an absolute disaster :(

Is this resolved with 10.10 and the new kernel?

---

### Post by Pepp-elito on 2010-11-05
This problem is happening to me as well on Ubuntu 10.04, using TP-Link TL-WN821N.
Random disconnects and slow network speeds.
(Disconnects seems more frequent if e.g. streaming video)

Probably this bug that is causing the problem:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/540827](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/540827)

Have not tried the carl-driver solution yet, but i will. I'm abit unsure how to verify that ubuntu is truly running the carl-driver after install, any ideas?

I can't really understand why this bug seems to get so litle attention as it seems to be causing a relly bad experience for new users of ubuntu.
If it really is a driver issue , caused by the ar9170-driver not being capable of handling scans while connected. Couldn't this be temporarally fixed by pushing out a networkmangar update that disables scanning while connected for this chip:set, and only forces a scan if the user is truly interacting with the network-manager applet etc?

---

### Post by max54 on 2011-03-11
Hi.i have the same problem my card wn111v2 disconection .i use Ubuntu 10.10 and problem still be .I try install new kernel 2.6.37 and 2.6.38 rc6 and problem still be..i dont know why this is good card but always disconetcion..

---

### Post by janrocks on 2011-06-14
Makes no difference what dongle/card (5 tested) is used bug still exists. Bug listing classes as "medium" which is stupid as it should be "critical" 

Looks like nobody cares enough to fix something which does not affect Debian (tested hardware with lenny, squeeze and wheezy.. connection stable and solid) and is a fatal flaw on a netbook with no ethernet capability. For a LTS release this really is not good enough.

---

### Post by arnold2ice on 2011-08-06
FWIW my Dlink DWA-160 does the same thing with my ActionTec V1000H modem/router.  Ironically I chose the DWA-160 because it was listed as working out of the box.  It does.  For a minute or two...

---

### Post by arnold2ice on 2011-08-07
This solution solved my problems.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/540827/comments/23]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/540827/comments/23")

I'm using 10.04 with a D-link DWA-160 A2 usb network adapter with the ar9170 driver.  YMMV

---

### Post by tech7 on 2011-09-25
I'm using a Dell D600 with Ubuntu 10.04.  I have had no problems with the wifi on this computer until yesterday.  All of the sudden, my wifi keeps dropping.  If I restart my computer and let it sit for a little while, I can get a connection to my router for about 10-15 minutes.  Then it drops.
I am running two different networks in my home, both of which broadcast a wifi signal.  It has this issue on both of them.  Also, my family uses windows computers and have had no issues.  In fact, I also have a 'twin' dell d600 which runs windows xp that does not have this issue.  I am using that computer right now.
This is terrible inconvenient because I just started a new web project which is what I use ubuntu for, lamp on an easy linux distro.  I cannot stand coding on a windows computer, I would rather drive nails into my forehead than have to resort to using windows for a web project.
Does anybody know of any solid fixes to this issue yet?
The last suggestion does not apply as my routers are not password protected in any way.
I cannot understand why my 10.04 has had no problems until now?  I did just install some updates recently, but do not recall what they pertained to.

---

### Post by Bill_Gates on 2012-01-17
Is there a solution for this issue? I recently bought a TP-Link WN821N adapter and i have the same problem. :(

Heat related?

[https://lists.ath9k.org/pipermail/ath9k-devel/2012-January/007782.html](https://lists.ath9k.org/pipermail/ath9k-devel/2012-January/007782.html)

---

### Post by Silverflyer on 2012-01-17
Add another 10.04 LTS user who is having this problem.  Currently using a wired connection to browse the Internet.

---

