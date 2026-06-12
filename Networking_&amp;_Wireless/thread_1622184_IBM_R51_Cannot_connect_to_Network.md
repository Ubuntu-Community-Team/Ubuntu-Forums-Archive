---
title: "IBM R51 Cannot connect to Network"
date: 2010-11-15
forum: Networking &amp; Wireless
---

### Post by stevebond001 on 2010-11-15
Hi
I have an IBM R51 laptop which I would like to run on ubuntu (as I'm currently running Maverick on my Desktop and like it very much)
I have run the liveCD and everything runs OK except for the wireless network, which although it detects my wireless network, will not let me connect.  I have edited the wireless connections with my SSID, (WPA) password, etc, but when I try to connect it will not connect.

I have also tried this on an unsecured wireless network with the same result.

Running lshw -c network shows the following information:

*-network:0             
       description: Wireless interface
       product: PRO/Wireless LAN 2100 3B Mini PCI Adapter
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:02:02.0
       logical name: eth1
       version: 04
       serial: 00:13:e8:03:c6:d4
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2100 driverversion=git-1.2.2 firmware=712.0.3:3:00000001 latency=64 maxlatency=34 mingnt=2 multicast=yes wireless=unassociated
       resources: irq:11 memory:c0204000-c0204fff

I would dearly love to fix this as this is the only issue preventing me from running ubuntu on my Laptop, which is currently running Windows 7 with no problems.

Any assistance would be greatly appreciated.

---

### Post by chili555 on 2010-11-15
May we please see:```
sudo iwlist eth1 auth
```Is an Intel 2100 card and the ipw2100 driver actually capable of doing WPA?

The reply that it works great in Windows is trivial; a great many things work great in Windows but not in Linux; for instance, most versions of Microsoft Flight Simulator (duh!) and viruses. As well, a great many things work in Linux but not in Windows.

However, you might try the Windows drivers for your card with ndiswrapper if your result comes out as I suspect. I don't know if it will work; when I ran into this issue with my Intel 2200, I swapped it for an Intel 2915, albeit with some whitelist issues.

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

--------
note to chili: wext??

---

### Post by stevebond001 on 2010-11-15
Hi
Thanks for the response.  The output you requested is as follows:

eth1      Authentication capabilities :
		WPA
		WPA2
		CIPHER-TKIP
		CIPHER-CCMP
          Current WPA version :
		Unknown
          Current Key management :
		Unknown
          Current Pairwise cipher :
		WEP-104
		Unknown
          Current Pairwise cipher :
		WEP-104
		Unknown
          Current TKIP countermeasures : yes
          Current Drop unencrypted : yes
          Current Authentication algorithm :
          Current Receive unencrypted EAPOL : yes
          Current Roaming control : no
          Current Privacy invoked : no



Also, as far as I can tell, my wireless should work according to:
[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsIntel#miniPCI](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsIntel#miniPCI)



In the meantime I'll try using ndiswrapper to see if it helps

---

### Post by chili555 on 2010-11-15
If you haven't already, please wait. It is clear that your card and driver do WPA. Next, we need to see if wpa-supplicant is using the ipw driver or wext. I believe wext is preferred. I will Google a bit and, if necessary, fire up the one computer I have remaining that uses Network Manager; coincidentally, it is the one with the Intel 2915.> Also, as far as I can tell, my wireless should work according to:We know it works. The question is whether it works with all features.

---

### Post by stevebond001 on 2010-11-15
I've already installed NdisWrapper, located the driver and installed it.  It still doesn't work, so I'll uninstall the NdisWrapper driver and wait for you to get back to me.

Many thanks

---

### Post by chili555 on 2010-11-15
I thought that perhaps the utility wpa_supplicant was erroneously calling the wpa driver ipw instead of wext. After examining my machine and Google for the last while, I am not so sure; I think wpa_supplicant uses wext unless another driver is specified on the command line. You are not using the command line, you are using the GUI Network Manager. I am therefor less convinced that wext is the culprit.

Is your network WPA or WPA2 or the dreaded and not very well handled WPA *and* mixed WPA2? If it is set up in mixed mode, I'd suggest changing to WPA or WPA2, not both.

This may give us some clues:```
sudo cat /var/log/syslog | grep -i wpa | tail -n20
```Please post it.

---

### Post by stevebond001 on 2010-11-15
Hi
Output from the command is as follows:

ov 15 16:26:17 ubuntu wpa_supplicant[997]: CTRL-EVENT-CONNECTED - Connection to 00:26:5a:09:ba:49 completed (reauth) [id=0 id_str=]
Nov 15 16:27:02 ubuntu wpa_supplicant[997]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Nov 15 18:27:29 ubuntu NetworkManager[842]: <info> Config: added 'key_mgmt' value 'WPA-PSK'
Nov 15 18:27:30 ubuntu wpa_supplicant[941]: Trying to associate with 00:26:5a:09:ba:49 (SSID='WLAN' freq=2412 MHz)
Nov 15 18:27:30 ubuntu wpa_supplicant[941]: Association request to the driver failed
Nov 15 18:27:35 ubuntu wpa_supplicant[941]: Authentication with 00:26:5a:09:ba:49 timed out.
Nov 15 18:27:35 ubuntu wpa_supplicant[941]: Trying to associate with 00:26:5a:09:ba:49 (SSID='WLAN' freq=2412 MHz)
Nov 15 18:27:36 ubuntu wpa_supplicant[941]: Association request to the driver failed
Nov 15 18:27:41 ubuntu wpa_supplicant[941]: Authentication with 00:26:5a:09:ba:49 timed out.
Nov 15 18:27:41 ubuntu wpa_supplicant[941]: Trying to associate with 00:26:5a:09:ba:49 (SSID='WLAN' freq=2412 MHz)
Nov 15 18:27:41 ubuntu wpa_supplicant[941]: Association request to the driver failed
Nov 15 18:27:46 ubuntu wpa_supplicant[941]: Authentication with 00:26:5a:09:ba:49 timed out.
Nov 15 18:27:47 ubuntu wpa_supplicant[941]: Trying to associate with 00:26:5a:09:ba:49 (SSID='WLAN' freq=2412 MHz)
Nov 15 18:27:49 ubuntu wpa_supplicant[941]: Association request to the driver failed
Nov 15 18:27:54 ubuntu wpa_supplicant[941]: Authentication with 00:26:5a:09:ba:49 timed out.
Nov 15 18:27:54 ubuntu wpa_supplicant[941]: Trying to associate with 00:26:5a:09:ba:49 (SSID='WLAN' freq=2412 MHz)
Nov 15 18:27:55 ubuntu wpa_supplicant[941]: Association request to the driver failed
Nov 15 18:27:55 ubuntu wpa_supplicant[941]: Associated with 00:26:5a:09:ba:49
Nov 15 18:27:58 ubuntu wpa_supplicant[941]: WPA: Key negotiation completed with 00:26:5a:09:ba:49 [PTK=CCMP GTK=TKIP]
Nov 15 18:27:58 ubuntu wpa_supplicant[941]: CTRL-EVENT-CONNECTED - Connection to 00:26:5a:09:ba:49 completed (auth) [id=0 id_str=]


I'm pretty sure my Wireless network is WPA/WPA2 so I will check later and set to WPA2 only, to see if this helps.  When I do I'll post the result.

EDIT:  Just tried changing my Wireless network to WPA only (and also WPA2 only) with the same result, no connection


Thanks once again

---

### Post by chili555 on 2010-11-15
Please try another thing:```
sudo rmmod -f ipw2100
sudo modprobe ipw2100 associate=1
```Any improvement?

---

### Post by stevebond001 on 2010-11-15
Hi
Tried as you suggested but still the same result.  The Wireless Network Icon in the top panel looks like it's attempting to connect (the icon is animated for a while) but it won't connect, I just get a message saying that I'm not connected

EDIT:  I have tried another couple of things but not sure if this helps or not.  Firstly I ran iwconfig, the output is below:
lo        no wireless extensions.

eth0      no wireless extensions.

irda0     no wireless extensions.

eth1      unassociated  ESSID:off/any  Nickname:"ipw2100"
          Mode:Managed  Channel=0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:16 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:1   Missed beacon:0


I have also installed wicd and attempted to connect to the network.  I can see wicd attempting to connect but it eventually returns an error message stating "Bad Password".  I know the password is correct and have re-entered it several times, but without success.  I therefore think that this error message is a red herring.


Any other ideas please??

Thanks

---

### Post by stevebond001 on 2010-11-16
I have also tried another router (different manufacturer) but the issue is still the same.

Any help would be greatly appreciated

---

### Post by chili555 on 2010-11-16
Do you still have Wicd installed, I hope? Can you look around in its preferences and settings and see if it's using the wpa_supplicant driver ipw or wext? I think it should use wext, but I'd try either.

Did you remove NM entirely when you installed Wicd? See if it's running (and fighting):```
ps aux | grep -i network
```Does the password work seamlessly on other computers on the network? Is upper or lower-case an issue?

---

### Post by stevebond001 on 2010-11-16
Well not sure what happened but it's now solved.  I had trouble with my router and ended up resetting it back to it's default connection.  Once I'd set it up again (with security, IP addresses, etc) I could access the Internet via the wireless card.

Sorry I couldn't find a definitive answer but at least it's working.  My only worry now is that I have to rebuild my Laptop again and install Maverick from scratch (my previous installation was a dual boot but now I want to remove Windows 7). Fingers crossed the wireless driver will work when it's rebuilt.

Thanks for the help

---

### Post by chili555 on 2010-11-16
In any case, I am glad it's working. When you reinstall, if you get stuck, please post here and we'll be glad to help. Feel free to PM me if I don't catch it quickly.

---

