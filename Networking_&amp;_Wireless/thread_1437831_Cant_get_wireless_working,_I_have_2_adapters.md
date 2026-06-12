---
title: "Cant get wireless working, I have 2 adapters"
date: 2010-03-24
forum: Networking &amp; Wireless
---

### Post by paulrogers on 2010-03-24
I have a Netgear WG111T USB and a Edimax EW-7711UAn USB.

I have the latest version of ubuntu.

I have installed ndiswrapper, and loaded the windows drivers in for the netgear, and it will show up in iwconfig but wont connect to anything, I got rid of network manager and installed wicd as I heard that may solve the problem, to no avail.

The Edimax one, I got because I read it worked straight out of the box, but looking into it apparently i need to compile the firmware from ralinks website, but I get errors with that.

Im not too fussed what one I use as long as I get a wireless connection, currently i have it connected to my laptop through a cable and bridging the connections.

If I type in iwconfig with the edimax:
> 
paul@paul-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan2     IEEE 802.11bgn  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=13 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
iwconfig with the netgear:
> 
paul@paul-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:108 Mb/s   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
Any help at all would be appreciated, and like a lot of people here, im new to using linux but im willing to learn. I used Xandros a few years ago and got my wireless working with ndiswrapper back then, and I occasionly install software on a webserver.

Thanks,
Paul

---

### Post by paulrogers on 2010-03-24
Weird, just after I posted this, wicd recognized my 2 wireless networks but thats where it stopped, it wont connect to either.

[IMG]http://i43.tinypic.com/15ouxc6.png[/IMG]

---

### Post by chili555 on 2010-03-24
It shows Wired as default and looks like it's connected. If you click Disconnect from the wired ethernet and even detach the ethernet cable, is there any improvement?

---

### Post by paulrogers on 2010-03-24
I apologise, I took the screenshot when I was connected, I had disconnected from the ethernet connection, to try and connect via wireless.

I did try and take a screenshot, but not it wont show anything in wicd other than wireless, even when I remove the cable and refresh. Im confused

---

### Post by paulrogers on 2010-03-24
Earlier on when it recognized 2 networks but wouldnt connect, that was via the Netgear.


lsusb on netgear:
> 
paul@paul-desktop:~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 007: ID 1385:4250 Netgear, Inc WG111T
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 002: ID 04fc:05d8 Sunplus Technology Co., Ltd 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
lsusb on edimax:
> 
us 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 008: ID 7392:7711  
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 002: ID 04fc:05d8 Sunplus Technology Co., Ltd 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
edit--
its showing my router again now, the other access point (my mobile phone) is switched off now, but when i try to connect to sky33627 it says at the bottom trying to connect to pauls iphone mywi, and it just stays like that and eventually fails.

---

### Post by paulrogers on 2010-03-24
Ive been trying everything but still not got this solved :( I really want to make this move to Ubuntu permanent. I have finally got my sound working, my theme setup, the only problem now seems to be the wireless connection.

---

### Post by chili555 on 2010-03-24
With which is it showing your router? Both? Let's pick one and try to get it working. Please leave the one inserted that is wlan0.

Did you use the native driver or ndiswrapper? What is the output of:```
sudo iwlist wlan0 scan
```

---

### Post by paulrogers on 2010-03-24
It was showing my router with the netgear adapter, ill stick to this one as although its not as good an adapter, it shows more hope of working. The netgear one is wlan0.

I used the windows drivers and installed them with the ndiswrapper GUI add on.
the output of the command is:
paul@paul-desktop:~$ sudo iwlist wlan0 scan
wlan0     No scan results

---

### Post by paulrogers on 2010-03-24
Ive just restarted and tried again:

> ^[[Apaul@paul-desktop:~$ sudo iwlist wlan0 scan
[sudo] password for paul: 
wlan0     Scan completed :
          Cell 01 - Address: 00:23:40:60:83:5C
                    ESSID:"SKY33627"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:37/100  Signal level:-72 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0

paul@paul-desktop:~$

---

### Post by chili555 on 2010-03-24
Is your network encrypted with WEP? Does Network Manager ask you for the key? 40/128-bit Hex key?

---

### Post by paulrogers on 2010-03-24
My network is encrypted with WPA2-PSK (TKIP)
In WICD I selected WPA but it tries WEP, I change it and enter my key and it tries to connect and fails.

Here is a screenshot of my router settings:
[http://i41.tinypic.com/2n1ckrm.png](http://i41.tinypic.com/2n1ckrm.png)

I want to show a screenshot of WICD but again its showing no wireless networks again.

---

### Post by chili555 on 2010-03-24
ndiswrapper with wpa_supplicant is very tricky. There are lots of reports of failure here. Can we try to get one or the other of your devices going with native drivers? Are you using the .inf file that came in the box with the device? The XP driver or which?

What does this tell us?```
ndiswrapper -l
```

---

### Post by chili555 on 2010-03-24
The Edimax ought to work natively with a few tweaks.

---

### Post by paulrogers on 2010-03-24
ndiswrapper -l Output:
```

paul@paul-desktop:~$ ndiswrapper -l
athfmwdl : driver installed
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
netwg11t : driver installed
	device (1385:4250) present

```

and as i explained earlier, the settings for encryption i have in wicd:
[http://i40.tinypic.com/1zmmiir.png](http://i40.tinypic.com/1zmmiir.png)

Im more than happy to use the edimax dongle, im willing to try anything.

Thankyou,

---

### Post by chili555 on 2010-03-24
Here is the process. Please remove the device and do:

```
sudo gedit /etc/modprobe.d/blacklist.conf
```
Add the following lines:
```
blacklist rt2800usb
blacklist rt2x00usb
blacklist rt2x00lib
blacklist rt2870sta
blacklist ndiswrapper
```If the native driver rt3070sta is in there, remove it. Proofread carefully, save and close gedit. Next do:```
sudo gedit /etc/modules
```If ndiswrapper is in there, comment it out, and add a new line:```
#ndiswrapper
rt3070sta
```Proofread these changes carefully and be sure to click save and then close gedit. Reboot and insert the Edimax. Any improvement?

---

### Post by paulrogers on 2010-03-24
Ive done them changes and even tried a restart, nothing has changed other than the light on the edimax is not flickering fast like it was before. I changed wireless device in wicd to wlan2 and tried again but the edimax isnt doing anything.

---

### Post by chili555 on 2010-03-24
With the Edimax still inserted, please let me see:```
dmesg | grep -e rt2 -e rt3 -e ndis
```Thanks.

---

### Post by paulrogers on 2010-03-24
Here it is
> paul@paul-desktop:~$ dmesg | grep -e rt2 -e rt3 -e ndis
[    5.493921] rt3070sta: module is from the staging directory, the quality is unknown, you have been warned.
[    5.498128] usbcore: registered new interface driver rt2870
[    5.499069] rt3070sta: module is from the staging directory, the quality is unknown, you have been warned.


Thanks

---

### Post by chili555 on 2010-03-24
Let's have a peek at:```
iwconfig
```If you are sure the Edimax is wlan2, let's also see:```
sudo iwlist wlan2 scan
sudo iwlist wlan2 auth
```Thanks.

---

### Post by paulrogers on 2010-03-24
Ah, it is now ra0:
```
paul@paul-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ra0       RT2870 Wireless  ESSID:""  Nickname:""
          Mode:Auto  Frequency=2.412 GHz  
          Link Quality=10/100  Signal level:0 dBm  Noise level:-143 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


```

I changed the settings in wicd and it finds my router but still wont connect, says it cant obtain an IP address, I entered a static address then it says cant contact the router.

The rest of the commands:
```
paul@paul-desktop:~$ sudo iwlist ra0 scan
[sudo] password for paul: 
ra0       Scan completed :
          Cell 01 - Address: 00:23:40:60:83:5C
                    Protocol:802.11b/g
                    ESSID:"SKY33627"
                    Mode:Managed
                    Channel:1
                    Quality:68/100  Signal level:-63 dBm  Noise level:-97 dBm
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK

paul@paul-desktop:~$ sudo iwlist ra0 auth
ra0       Authentication capabilities :
		WPA
		WPA2
		CIPHER-TKIP
		CIPHER-CCMP
          Current Drop unencrypted : no
          Current Authentication algorithm :
		open



```

Thanks

---

### Post by chili555 on 2010-03-24
Please try:```
sudo ifconfig ra0 up
sudo iwconfig ra0 mode managed
sudo /etc/init.d/networking restart
```Any improvement?

---

### Post by paulrogers on 2010-03-24
Hi, sorry for the delayed reply, my laptop which im sharing the connection with messed up.

I tried them but no improvement.

It keeps saying 11n-AP: Obtaining IP Address, which eventually fails.

Its the same when I try to connect to my phones wifi tethering option, and this is an unsecured AP

Thankyou

---

### Post by chili555 on 2010-03-24
Remove the device. There are two or, maybe, three files we might tweak. Please do:```
cd /etc/Wireless && ls
```You will see a folder for RT2870STA and maybe RT3070STA. Do:```
cd RT2870STA
sudo gedit RT2870STA.dat
```Here are some changes I suggest in the file:> Default
CountryRegion=5
CountryRegionABand=7
CountryCode=[COLOR="Blue"]UK[/COLOR]   [COLOR="Red"]<---maybe???[/COLOR]
SSID=[COLOR="Blue"]SKY33627[/COLOR]
NetworkType=Infra
WirelessMode=9
Channel=0
BeaconPeriod=100
TxPower=100
BGProtection=0
TxPreamble=0
RTSThreshold=2347
FragThreshold=2346
TxBurst=1
WmmCapable=0
AckPolicy=0;0;0;0
AuthMode=[COLOR="Blue"]WPA2PSK[/COLOR]   
EncrypType=[COLOR="Blue"]TKIP [/COLOR]    
WPAPSK=[COLOR="Blue"]yourkeyhere[/COLOR]
--- snip ---Make those changes, proofread carefully, save and close gedit.

The other files may be in RT3070STA and may be named RT2870STA.dat or RT3070STA.dat. Let's just do it the easy way; let's copy!```
sudo cp RT2870STA.dat /etc/Wireless/RT3070STA/RT2870STA.dat
sudo cp RT2870STA.dat /etc/Wireless/RT3070STA/RT3070STA.dat
```If it complains that the file RT3070STA doesn't exist, that's fine, you can stop.

Reinsert the device and please post back your good news!

---

### Post by paulrogers on 2010-03-24
Hi

Ive just done them, but unfortunately it does the following:
Disconnecting Active Connections
Putting Interface Down
Verifying Access Point Association
Connection Failed: Could not contact the remote access point.

---

### Post by chili555 on 2010-03-24
Please reboot with the device inserted and tell me what Wicd has to say.

---

### Post by paulrogers on 2010-03-24
Its exactly the same.

This is while I have my own IP Address/DNS setup, if I put it back to automatic it gets stuck on Obtaining IP address before failing.

---

### Post by chili555 on 2010-03-24
Your little Edimax is being stubborn. Mind if I back over it in my truck? Just kidding. Please do:```
sudo tail -n50 /var/log/wicd/wicd.log
```Try to find the last place where authentication fails and post about ten lines up to and including its failure so we can try to work out what's wrong.> This is while I have my own IP Address/DNS setupWhere is your own setup? In Wicd or in */etc/network/interfaces*?

---

### Post by paulrogers on 2010-03-24
I disconnected from LAN, then attempted wireless connnection, and here are the results:

> paul@paul-desktop:~$ sudo tail -n50 /var/log/wicd/wicd.log
2010/03/24 23:59:48 :: Releasing DHCP leases...
2010/03/24 23:59:49 :: Setting false IP...
2010/03/24 23:59:49 :: Stopping wpa_supplicant
2010/03/24 23:59:49 :: Flushing the routing table...
2010/03/24 23:59:49 :: Putting interface up...
2010/03/24 23:59:49 :: Generating psk...
2010/03/24 23:59:49 :: Attempting to authenticate...
2010/03/24 23:59:49 :: Setting static IP : 192.168.1.12
2010/03/24 23:59:49 :: Setting default gateway : 192.168.1.1
2010/03/24 23:59:49 :: Verifying AP association
2010/03/24 23:59:52 :: Connection Failed: Failed to ping the access point!
2010/03/24 23:59:52 :: exiting connection thread
2010/03/24 23:59:52 :: Sending connection attempt result association_failed
2010/03/25 00:00:02 :: Putting interface down
2010/03/25 00:00:02 :: Releasing DHCP leases...
2010/03/25 00:00:02 :: Setting false IP...
2010/03/25 00:00:02 :: Flushing the routing table...
2010/03/25 00:00:02 :: Putting interface up...
2010/03/25 00:00:02 :: Setting static IP : 192.168.1.11
2010/03/25 00:00:02 :: Setting default gateway : 192.168.1.1
2010/03/25 00:00:02 :: Connecting thread exiting.
2010/03/25 00:00:02 :: Sending connection attempt result Success
2010/03/25 00:15:40 :: Connecting to wireless network SKY33627
2010/03/25 00:15:40 :: Putting interface down
2010/03/25 00:15:40 :: Releasing DHCP leases...
2010/03/25 00:15:41 :: Setting false IP...
2010/03/25 00:15:41 :: Stopping wpa_supplicant
2010/03/25 00:15:41 :: Flushing the routing table...
2010/03/25 00:15:41 :: Putting interface up...
2010/03/25 00:15:41 :: Generating psk...
2010/03/25 00:15:41 :: Attempting to authenticate...
2010/03/25 00:15:41 :: Running DHCP
2010/03/25 00:15:41 :: Internet Systems Consortium DHCP Client V3.1.2
2010/03/25 00:15:41 :: Copyright 2004-2008 Internet Systems Consortium.
2010/03/25 00:15:41 :: All rights reserved.
2010/03/25 00:15:41 :: For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
2010/03/25 00:15:41 :: 
2010/03/25 00:15:42 :: Listening on LPF/ra0/00:1f:1f:50:a4:51
2010/03/25 00:15:42 :: Sending on   LPF/ra0/00:1f:1f:50:a4:51
2010/03/25 00:15:42 :: Sending on   Socket/fallback
2010/03/25 00:15:42 :: DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 8
2010/03/25 00:15:50 :: DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 15
2010/03/25 00:16:05 :: DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 8
2010/03/25 00:16:13 :: DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 13
2010/03/25 00:16:26 :: DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 17
2010/03/25 00:16:43 :: No DHCPOFFERS received.
2010/03/25 00:16:43 :: No working leases in persistent database - sleeping.
2010/03/25 00:16:52 :: DHCP connection failed
2010/03/25 00:16:52 :: exiting connection thread
2010/03/25 00:16:53 :: Sending connection attempt result dhcp_failed


---

### Post by chili555 on 2010-03-24
Unfortunately, I don't see anything very revealing there. Does Wicd still see your netwrork as WEP? One scan result (post #9) looked like WEP, as did Wicd. In post #20, it was clearly WPA. I also noticed, in one of your Wicd screenshots, that signal strength is low. However, in post #20, it looks quite healthy. Is this a laptop that you can walk over to the router?

I wonder if it would help to reset the router by unplugging it and plugging it back in.

Everything looks fine, except it won't connect!!!

It's getting late over there, isn't it?

---

### Post by chili555 on 2010-03-24
> make[3]: *** No rule to make target `kernel/bounds.c', needed by `kernel/bounds.s'.  Stop.

make[2]: *** [prepare0] Error 2

make[2]: Leaving directory `/usr/src/linux-headers-2.6.31-14-generic'

make[1]: *** [modules] Error 2

make[1]: Leaving directory `/home/cameron/Realtek/rtl8192se/HAL/rtl8192'

make: *** [install] Error 2Please run 'sudo su' before make and make install. Let's get rid of that error.

I don't quite know how this is running if 'make install' errored out.

---

### Post by paulrogers on 2010-03-24
Here is a current wicd screenshot, pretty good signal strengh and showing WPA2:
[http://i44.tinypic.com/2565il3.png](http://i44.tinypic.com/2565il3.png)

Its a desktop pc, I have it connected to my laptop via ethernet and the laptop connected to the router then the connections bridged.

Is that last post of yours meant for another thread?

Thanks

---

### Post by paulrogers on 2010-03-24
IT IS WORKING!!!!

For anyone else who follows this thread.

Wicd --> Preferences --> Advanced Settings --> Driver

Was set as ralink_legacy

Changed to Wext

I am now writing this on a wireless connection.

Thankyou so much for your help

---

