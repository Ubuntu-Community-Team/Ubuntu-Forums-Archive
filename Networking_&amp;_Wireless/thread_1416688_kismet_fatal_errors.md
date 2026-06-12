---
title: "kismet fatal errors"
date: 2010-02-26
forum: Networking &amp; Wireless
---

### Post by mickmouse13 on 2010-02-26
I have been looking around for a while and found alot of stuff that should of been helpful, but none of it was =( 

im working on getting some pentesting of my network going and i am gonna use a combo of kismet, aircrack-ng and a few other tool, im stuf on kismet though, i dont know what to fill in the -c ***,wlan0,***** fields. no matter what i have entered i get "illegal card sourse" or something similar. i can post all the info i know and hopefully someone here will know what i should putt. 
this is kismet -c wlan0
```
mick@mick-laptop:~$ sudo airmon-ng start wlan0


Found 5 processes that could cause trouble.
If airodump-ng, aireplay-ng or airtun-ng stops working after
a short period of time, you may want to kill (some of) them!

PID    Name
895    NetworkManager
964    avahi-daemon
966    avahi-daemon
1100    wpa_supplicant
2954    dhclient
Process with PID 2954 (dhclient) is running on interface wlan0


Interface    Chipset        Driver

wlan0        Intel 4965/5xxx    iwlagn - [phy0]
                (monitor mode enabled on mon1)
mon0        Intel 4965/5xxx    iwlagn - [phy0]

```running airmon-ng start wlan0 gives me 
```
mick@mick-laptop:~$ sudo airmon-ng start wlan0


Found 5 processes that could cause trouble.
If airodump-ng, aireplay-ng or airtun-ng stops working after
a short period of time, you may want to kill (some of) them!

PID    Name
895    NetworkManager
964    avahi-daemon
966    avahi-daemon
1100    wpa_supplicant
2954    dhclient
Process with PID 2954 (dhclient) is running on interface wlan0


Interface    Chipset        Driver

wlan0        Intel 4965/5xxx    iwlagn - [phy0]
                (monitor mode enabled on mon1)
mon0        Intel 4965/5xxx    iwlagn - [phy0]

```could those programs be causing problems?

Looking inside kismet.conf i found this like, i read a a bit about it but i would not know what to enter.
```
# source=sourcetype,interface,name[,initialchannel]
and
source=none,none,addme

```my laptop is a sony vaio vgn-fw560f and all the info on the wireless card is that its a 
```
Wi-Fi :  Intel® WiFi Link 5100AGN (802.11a/b/g/n)[3]("http://javascript%3Cb%3E%3C/b%3E:showFootnotes%28%29;")
```ifconfig gives me this for the wifi
```

wlan0     Link encap:Ethernet  HWaddr 00:22:fb:be:98:1c  
          inet addr:192.168.1.103  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::222:fbff:febe:981c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9089 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6802 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6899239 (6.8 MB)  TX bytes:1439906 (1.4 MB)

```if i forgot anything please let me know and I apologize for the semi "do it for me" question.

---

### Post by chili555 on 2010-02-26
> I apologize for the semi "do it for me" question.Search is your friend. [http://ubuntuforums.org/showpost.php?p=8807024&postcount=2](http://ubuntuforums.org/showpost.php?p=8807024&postcount=2)

---

### Post by mickmouse13 on 2010-02-26
awesome. thanks.

---

### Post by mickmouse13 on 2010-02-26
i ran that command and it seems to add up well
```
 *-network               
       description: Wireless interface
       product: Wireless WiFi Link 5100
       vendor: Intel Corporation
       physical id: 0
       bus info: meh
       logical name: wmaster0
       version: 00
       serial: meh
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn ip=meh latency=0 multicast=yes wireless=IEEE 802.11abgn
       resources: irq:33 memory:d1500000-d1501fff

```so i entered the info as pointed to in the link sent by chili555
```
# Sources are defined as:
# source=sourcetype,interface,name[,initialchannel]
# Source types and required drivers are listed in the README under the
# CAPTURE SOURCES section.
# The initial channel is optional, if hopping is not enabled it can be used
# to set the channel the interface listens on.
# YOU MUST CHANGE THIS TO BE THE SOURCE YOU WANT TO USE
source=iwlagn,wmaster0,Intel
```then i went into kismet and used 
sudo kismet -c iwlagn,wmaster0,Intel
same error
sudo kismet -c Intel,wmaster0,iwlagn
no luck... i will keep playing around and searching around, if anyone sees something im doing wrong let me know.

---

### Post by mickmouse13 on 2010-02-26
FATAL: Unknown capture source type 'Intel' in source 'Intel,wmaster0,iwlagn'

---

### Post by mickmouse13 on 2010-02-26
source=iwl4965,wlan0,test
seemed to work for me. kismet did start up, and my Internet died which means my card was doing other things.

---

### Post by chili555 on 2010-02-26
Lordy.

If you properly amend the kismet.conf file, it is not necessary to include those details when you start kismet. Moreover, since kismet will need to put your wireless card into Monitor mode, it will want root priveleges; e.g.:```
sudo kismet
```More moreover, try wlan0:```
# YOU MUST CHANGE THIS TO BE THE SOURCE YOU WANT TO USE
source=iwlagn,wlan0,Intel
```More, more moreover, some Intel cards are hard to get back into Managed mode after running kismet. Search will help you there if that turns out to be the case for you.

---

### Post by tenebrous_paradise on 2010-02-26
here is my kismet error...

root@ubuntu:~# sudo kismet
Server options:  none
Client options:  none
Starting server...
Waiting for server to start before starting UI...
Suid priv-dropping disabled.  This may not be secure.
No specific sources given to be enabled, all will be enabled.
Enabling channel hopping.
Enabling channel splitting.
Source 0 (madwifi): Enabling monitor mode for madwifi_ag source interface wlan0 channel 6...
FATAL: Failed to retrieve list of private ioctls 95:Operation not supported
[1] + Done(1)                    ${BIN}/kismet_server --silent ${server}

if someone knows how to deal with aircrack and wep's and what not please let me know id like to do a one on one chat thing to try to get help with this i have yahoo and an email address.. thanks

---

### Post by sadcruel on 2011-01-03
I have a Intel Link 1000 in a Acer 1825PTZ laptop.  It also has a Intel 4965/5xxx (iwlagn driver) card.  So the line in the   /etc/kismet/kismet.conf 

source=iwl4965,wlan0,intel

works for me.  Remember that you can change the last word (in this case intel), it is only the name you give.

---

