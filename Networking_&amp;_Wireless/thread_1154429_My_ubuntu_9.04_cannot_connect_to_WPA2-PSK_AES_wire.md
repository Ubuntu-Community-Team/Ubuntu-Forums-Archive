---
title: "My ubuntu 9.04 cannot connect to WPA2-PSK AES wireless network"
date: 2009-05-09
forum: Networking &amp; Wireless
---

### Post by safetycritical on 2009-05-09
I'm trying to connect a laptop to my wireless network. Windows XP can connect from the laptop without trouble.

My wireless network is a WPA2-PSK with AES encryption

With the default WUBI ubuntu 9.04 install the wireless card would scan for networks and correctly listed my neighbours networks

I have tried the changes recommended by the wireless WPA2 trouble shooter on the Ubuntu web site

I have run the commands recommended for this forum. They are

****************

**system.hardware.product**	AMILO A1650G
**system.hardware.vendor**	FUJITSU SIEMENS 

****************

**$ lspci -nn**
02:05.0 Ethernet controller [0200]: Atheros Communications Inc. AR2413 802.11bg NIC [168c:001a] (rev 01)

**$ lsusb**
no wireless devices

*****************

**iwconfig**
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11b  ESSID:""  Nickname:""
          Mode:Managed  Channel:0  Access Point:Not-Associated   
          Bit Rate: 0 kb/s   Tx-Power: 0 dBm   Sensitivity=1/1  
          Retry: off   RTS thr: off   Fragment thr: off
          Power Management: off
          Link Quality=0/70  Signal level=0 dBm  Noise level=0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

*****************

**lsmod | grep wlan**
wlan_scan_sta          20480  0 
wlan                  210288  4 wlan_scan_sta,ath_rate_sample,ath_pci

*****************
[B]
dmesg | grep wlan[/B]
[   14.959651] wlan: 0.9.4

*****************

**sudo lshw -C network**
  *-network:0 DISABLED    
       description: Wireless interface
       product: AR2413 802.11bg NIC
       vendor: Atheros Communications Inc.
       physical id: 5
       bus info: pci@0000:02:05.0
       logical name: wifi0
       version: 01
       serial: 00:c0:a8:ad:9c:09
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci latency=168 maxlatency=28 mingnt=10 

module=ath_pci multicast=yes wireless

******************************

**iwlist scan**
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wifi0     Interface doesn't support scanning.

ath0      No scan results

pan0      Interface doesn't support scanning.

************************
[B]
 lsb_release -d[/B]
Description:	Ubuntu 9.04

************************

**uname -mr**
2.6.28-11-generic i686

************************

** sudo /etc/init.d/networking restart**
 * Reconfiguring network interfaces...                                                          

/etc/network/interfaces:5: unknown method
ifdown: couldn't read interfaces file "/etc/network/interfaces"
/etc/network/interfaces:5: unknown method
ifup: couldn't read interfaces file "/etc/network/interfaces"

*************************
[B]
My /ETC/NETWORK/INTERFACES FILE[/B]

auto lo
iface lo inet loopback
#
auto wifi0
iface wifi0 inet dchp
wpa-driver wext
wpa-ssid <my network name>
wpa-ap-scan 2
wpa-proto RSN
wpa-pairwise CCMP
wpa-group CCMP
wpa-key-mgmt WPA-PSK
wpa-psk <my network password>

My wireless network does DCHP and a hidden broadcast name. The network restart fails as shown above

*********************************
[B]
ALSO TRIED CHANGING "wifi0" to "ath0" in the /etc/network/interfaces file[/B]

sudo /etc/init.d/networking restart 
 * Reconfiguring network interfaces...                                          

/etc/network/interfaces:5: unknown method
ifdown: couldn't read interfaces file "/etc/network/interfaces"
/etc/network/interfaces:5: unknown method
ifup: couldn't read interfaces file "/etc/network/interfaces"

Can you help please!! Once this works I can use Ubuntu all the time !!! :P

Regards

SafetyCritical

---

### Post by ajaysutton on 2009-05-14
This is very interesting to me as I'm having a similar issue.  I'm using either of two wireless devices, a Netopia 2241 or an ActionTec GT704 WG and cannot connect my Eee 1000HE running 9.04 to either network in my home.  It seems to connect to other wireless networks fine, and other devices (my iMac) connect to either DSL gateway.  This only started about two days ago, prior to that it was working fine, no changes had been made to the network.

In a desperate effort to make this work, I swapped hard drives in the Little Eee and installed Ubuntu fresh.  I'm not sure what's up with it, but I'd be delighted to entertain ideas.

What kind of wireless device(s) are you using?

---

### Post by _sleeper on 2009-05-15
i face the same problem with a compaq. and, although, i have blacklisted ath_pci, wlan associates with ath_pci rather than ath5k.

```
joc@joc-laptop:~$ lsmod | grep ath
ath_pci               217784  0
wlan                  237936  1 ath_pci
ath_hal               312160  1 ath_pci
ath5k                 126724  0
lbm_cw_mac80211       227364  1 ath5k
lbm_cw_cfg80211        73760  2 ath5k,lbm_cw_mac80211
led_class              12036  1 ath5k
```

---

### Post by RodP on 2009-06-06
I have a similar problem.  When I first installed 9.04 everything worked consistently and well.  Then an update came along in mid-May and things still worked well.  Then in early June (4th or 5th I think) another set of updates came along.  After installing the early June updates, my wireless connection (Acer 5100, with an Atheros AR2413 wireless chip) stopped working.  I would get the window asking for the WPA2 passphrase, but it showed what seemed to be an encoded passphrase instead of my actual passphrase.  Afterward, the software would not accept the actual passphrase under any conditions and I lost internet connections completely.

I finally did a complete reinstall of 9.04, after which everything worked perfectly.  Then the update manager found the 105 updates.  I installed them and the wireless connection was lost again, and in the same way.  The software asked me for a passphrase, which it would not accept as a replacement for its long string of numbers and letters.  

This time, I did another complete reinstall and have refused to allow any of the 105 updates to install.  Everything works perfectly again.  

Wha?

---

### Post by Vined Adobo on 2009-06-11
> **RodP said:**
> I have a similar problem.  When I first installed 9.04 everything worked consistently and well.  Then an update came along in mid-May and things still worked well.  Then in early June (4th or 5th I think) another set of updates came along.  After installing the early June updates, my wireless connection (Acer 5100, with an Atheros AR2413 wireless chip) stopped working.  I would get the window asking for the WPA2 passphrase, but it showed what seemed to be an encoded passphrase instead of my actual passphrase.  Afterward, the software would not accept the actual passphrase under any conditions and I lost internet connections completely.

I finally did a complete reinstall of 9.04, after which everything worked perfectly.  Then the update manager found the 105 updates.  I installed them and the wireless connection was lost again, and in the same way.  The software asked me for a passphrase, which it would not accept as a replacement for its long string of numbers and letters.  

This time, I did another complete reinstall and have refused to allow any of the 105 updates to install.  Everything works perfectly again.  

Wha?


I had a similar problem,  On Ubuntu, the wireless network had always been unstable.  Without Firefox running, I could ping my router and mozilla.org with network tools w/80% success.  Was able to get updates.  When I would start either Evolution or Firefox, the network completely stopped.  Couldn't ping anything.  After trying multiple re-installs and trying a lot of things which didn't work, I increased the power of the router from one to six.  Voila! problem fixed!  I can't imagine why.  It just worked.  We were running two Vista wireless laptops without problem.  Then when I'd boot Ubuntu, no network, but Vista laptop was still fine.  Boosting the wireless output power of the router fixed it, though.  Go figure.

Hope it helps you.

Dave

---

### Post by kevdog on 2009-06-11
Look at the output of lshw -C network --- and analyze the results!
Disabled is a big problem.  That likely means your ath_pci driver is incorrect.  You likely need the ath5k driver instead.

You could try
sudo modprobe -r ath_pci
sudo modprobe ath5k

And see if the driver "claims" your card by rechecking with lshw -C network, or the lsmod statement (list module command) -- something like:
lsmod | grep ath

and see what that puts out.

---

### Post by lucloubier on 2009-06-15
Hi ! I have the same problem. I did not even think the update process would caused the problem.

Any clue on what package update causes the problem ?

Anyone tried this :
sudo modprobe -r ath_pci
sudo modprobe ath5k

I am myself looking for a quick and easy solution to fix that !

---

### Post by crummins on 2009-06-15
Same problem here.  Wireless was working PERFECTLY until I installed updates recently (few days ago, maybe?).  I'm a Ubuntu noob so am not even sure where to start.  Running ubuntu 9.04 on an eeepc 1000.  I have it all configured the way I like it, so I'd hate to have to reinstall ubuntu again.  Right now the only way I have access to the internet is through a wire, which is a drag.  Anyone have any ideas?  I'm tempted to stop running updates because every time I do something breaks!
](*,)

---

### Post by carcar1 on 2009-06-15
Can you all go to terminal and type the following.

```
Sudo iwlist auth
```

And tell me what you get.  So this way we can know if your driver you are using can support wpa or your wext is messed up.

---

### Post by lucloubier on 2009-06-15
Hi carcar1 !

This is what I get :

> lo        no authentication information.

eth0      no authentication information.

ra0       Authentication capabilities :
		WPA
		WPA2
		CIPHER-TKIP
		CIPHER-CCMP
          Current Drop unencrypted : no
          Current Authentication algorithm :
		open


pan0      no authentication information.

What's next ?

---

### Post by crummins on 2009-06-16
And here's my result, too:

lo        no authentication information.

eth0      no authentication information.

ra0       Authentication capabilities :
        WPA
        WPA2
        CIPHER-TKIP
        CIPHER-CCMP
          Current Drop unencrypted : no
          Current Authentication algorithm :
        open


pan0      no authentication information.

---

### Post by kevdog on 2009-06-16
How have you tried to connect to the wpa2 network.  Through the command line, network manager, wicd, or other method?

---

### Post by lucloubier on 2009-06-16
Hi ! 

With my eeePC 1000He, XP works fine with wifi.
I use WPA and my wifi lan has a hidden SSID name.

If I choose to connect to it with Ubuntu, I enter :
- my SSID name
- choose security type : (WPA & WPA2 personal)
- enter my password
then click connect
the little network icon starts "rolling"...
then a message box shows asking me for the required password.

The password (shown if I click the show password box) looks like a generated pw! If I enter my wlan pw again, it goes searching for a minute and the same message appears again.

If I make my wlan visible, I can connect without any problem !

---

### Post by iReboot on 2009-06-16
I have the same problem.  I can connect to unsecured wireless networks, but not to WPA or WPA2.  I have tried connecting through the network manager.

iwlist auth output:
> 
ath0      Authentication capabilities :
		WPA
		WPA2
		CIPHER-TKIP
		CIPHER-CCMP
          Current Authentication algorithm :
		open

iwconfig output:
> lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

ath0      IEEE 802.11abg  ESSID:"Caltech Guest"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:0B:86:33:06:90   
          Bit Rate=1 Mb/s   Tx-Power=20 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=56/100  Signal level:-61 dBm  Noise level=-97 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

I've had this problem since upgrading to Jaunty.
I have a Lenovo T61 and an Atheros AR5212 wireless card with the ath5k driver.

---

### Post by crummins on 2009-06-17
> **crummins said:**
> Same problem here.  Wireless was working PERFECTLY until I installed updates recently (few days ago, maybe?).  I'm a Ubuntu noob so am not even sure where to start.  Running ubuntu 9.04 on an eeepc 1000.  I have it all configured the way I like it, so I'd hate to have to reinstall ubuntu again.  Right now the only way I have access to the internet is through a wire, which is a drag.  Anyone have any ideas?  I'm tempted to stop running updates because every time I do something breaks!
](*,)


Update:  my problem was fixed by installing the updates that came out today (June 17, 2009).  Now sure what they fixed or how, but wireless is back, perfect as before.

---

### Post by lucloubier on 2009-06-18
Hi !

Following what Crummins replied, I did an update last night.

It was not able to connect to my hidden wifi lan before and still not able to do so!

:(

---

### Post by own3mall on 2009-08-07
> **lucloubier said:**
> 
If I choose to connect to it with Ubuntu, I enter :
- my SSID name
- choose security type : (WPA & WPA2 personal)
- enter my password
then click connect
the little network icon starts "rolling"...
then a message box shows asking me for the required password.

The password (shown if I click the show password box) looks like a generated pw! If I enter my wlan pw again, it goes searching for a minute and the same message appears again.

If I make my wlan visible, I can connect without any problem !

I have the exact same problem?  Any way to get it working?  I'm using a Ralink RT2870 USB wireless N card.

---

### Post by lucloubier on 2009-08-08
I know the feeling !

Even after a few updates being applied, my problem is not solved yet ! My wlan has to be visible if I want to use it! I suspect it is a wlan driver problem! I dont know how to fix it though !

---

### Post by Dorrax on 2009-08-10
> **lucloubier said:**
> Hi ! 

With my eeePC 1000He, XP works fine with wifi.
I use WPA and my wifi lan has a hidden SSID name.

If I choose to connect to it with Ubuntu, I enter :
- my SSID name
- choose security type : (WPA & WPA2 personal)
- enter my password
then click connect
the little network icon starts "rolling"...
then a message box shows asking me for the required password.

The password (shown if I click the show password box) looks like a generated pw! If I enter my wlan pw again, it goes searching for a minute and the same message appears again.

If I make my wlan visible, I can connect without any problem !

I also have this problem. I have to hide the network because I live in an apartment building full of freeloading dirty hippies. My girlfriend's vista laptop connects fine, my printer and iphone connect fine, and when I use XP on my laptop, it works fine. But I can't get Ubuntu to connect, I'm using Jaunty. I have no clue what to do.

---

### Post by fallen04 on 2009-08-11
> **safetycritical said:**
> I'm trying to connect a laptop to my wireless network. Windows XP can connect from the laptop without trouble.

My wireless network is a WPA2-PSK with AES encryption

With the default WUBI ubuntu 9.04 install the wireless card would scan for networks and correctly listed my neighbours networks

I have tried the changes recommended by the wireless WPA2 trouble shooter on the Ubuntu web site

I have run the commands recommended for this forum. They are

****************

**system.hardware.product**	AMILO A1650G
**system.hardware.vendor**	FUJITSU SIEMENS 

****************

**$ lspci -nn**
02:05.0 Ethernet controller [0200]: Atheros Communications Inc. AR2413 802.11bg NIC [168c:001a] (rev 01)

**$ lsusb**
no wireless devices

*****************

**iwconfig**
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11b  ESSID:""  Nickname:""
          Mode:Managed  Channel:0  Access Point:Not-Associated   
          Bit Rate: 0 kb/s   Tx-Power: 0 dBm   Sensitivity=1/1  
          Retry: off   RTS thr: off   Fragment thr: off
          Power Management: off
          Link Quality=0/70  Signal level=0 dBm  Noise level=0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

*****************

**lsmod | grep wlan**
wlan_scan_sta          20480  0 
wlan                  210288  4 wlan_scan_sta,ath_rate_sample,ath_pci

*****************
[B]
dmesg | grep wlan[/B]
[   14.959651] wlan: 0.9.4

*****************

**sudo lshw -C network**
  *-network:0 DISABLED    
       description: Wireless interface
       product: AR2413 802.11bg NIC
       vendor: Atheros Communications Inc.
       physical id: 5
       bus info: pci@0000:02:05.0
       logical name: wifi0
       version: 01
       serial: 00:c0:a8:ad:9c:09
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci latency=168 maxlatency=28 mingnt=10 

module=ath_pci multicast=yes wireless

******************************

**iwlist scan**
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wifi0     Interface doesn't support scanning.

ath0      No scan results

pan0      Interface doesn't support scanning.

************************
[B]
 lsb_release -d[/B]
Description:	Ubuntu 9.04

************************

**uname -mr**
2.6.28-11-generic i686

************************

** sudo /etc/init.d/networking restart**
 * Reconfiguring network interfaces...                                                          

/etc/network/interfaces:5: unknown method
ifdown: couldn't read interfaces file "/etc/network/interfaces"
/etc/network/interfaces:5: unknown method
ifup: couldn't read interfaces file "/etc/network/interfaces"

*************************
[B]
My /ETC/NETWORK/INTERFACES FILE[/B]

auto lo
iface lo inet loopback
#
auto wifi0
iface wifi0 inet dchp
wpa-driver wext
wpa-ssid <my network name>
wpa-ap-scan 2
wpa-proto RSN
wpa-pairwise CCMP
wpa-group CCMP
wpa-key-mgmt WPA-PSK
wpa-psk <my network password>

My wireless network does DCHP and a hidden broadcast name. The network restart fails as shown above

*********************************
[B]
ALSO TRIED CHANGING "wifi0" to "ath0" in the /etc/network/interfaces file[/B]

sudo /etc/init.d/networking restart 
 * Reconfiguring network interfaces...                                          

/etc/network/interfaces:5: unknown method
ifdown: couldn't read interfaces file "/etc/network/interfaces"
/etc/network/interfaces:5: unknown method
ifup: couldn't read interfaces file "/etc/network/interfaces"

Can you help please!! Once this works I can use Ubuntu all the time !!! :P

Regards

SafetyCritical

Is your wireless network Hidden? I had issues connecting to my hidden wireless network. By broadcasting my network SSID, I was able to connect to my network (WPA/WPA2)

---

### Post by mvm on 2009-08-16
Hi, I was a bit tired of Xandros on my Asus eee pc 901, because I got so few security updates. So I installed Ubuntu 9.0.4 remix.
Now I encountered the same problem as many here with a hidden SSID, which hinders the wifi connection.
I.m.h.o. there is no valid reason in general to hide your SSID, but nevertheless, this should work. It worked with Xandros, it works with OpenSuse 11.1, so Linux is not at fault here.

[B]
I found this work-around
Open a terminal, enter: [I]sudo iwconfig ra0 ESSID <your-ssdid>
[/I][/B]You have to enter your password. After a while the connection is established. ra0 is the name of my wireless card. Unfortunately, you have to do it after every start.

But why hide your connection? It is not a security matter. Anyway, as soon as you unhid the ssid, it will be picked up by all the wireless neighbours automatically, and kept in their internal tables, and be lookup up at each startup . To prevent that, you should keep your ssid hidden from the very start, so *never* broadcast it.
My router has a hard disk in it, that starts spinning as soon as some foreigner tries to make contact, and I don't want that. That's my sole reason to have a hidden SSID.
What* is* a security issue, is the strength of your password.
I took my password from the famous grc site: [https://www.grc.com/passwords.htm](https://www.grc.com/passwords.htm)

Hope this helps a bit.Marc

---

### Post by Dorrax on 2009-08-16
It works, thank you!

---

### Post by BLiNDiNG on 2009-10-07
I'm newbie to linux and just start with jaunty

I use zyxel g-302 v3 pci card 
I have found many topic about problem on this card
all of them can not use at all

I have found this link [http://rtl-wifi.sourceforge.net/wiki/Installing]("http://rtl-wifi.sourceforge.net/wiki/Installing")

told me that jaunty kernel are driver included

But I can connect to none secure wifi and it works fine but not wpa-psk

I assume this was config problem not driver. Is it? or maybe driver problem?

---

### Post by DouglasAWh on 2010-05-20
There don't appear to be any mentions of certificate based authentication in this thread.  Can this be done with certificates?  It doesn't look like NetworkManager can, anyway.

---

