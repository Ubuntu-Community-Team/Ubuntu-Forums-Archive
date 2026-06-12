---
title: "Wireless not connecting on upgrade to 9.04"
date: 2009-04-24
forum: Networking &amp; Wireless
---

### Post by rsageofdunstable on 2009-04-24
I am recently new to Linux. I started with Ubuntu 8.10 and everything I did in Windows I got working in Ubuntu 8.10

Upgraded to 9.04 last night and since then my wireless card will not associate with my Netgear AP

Wireless network is seen but the system keeps coming back asking for wireless authentication.

I have attached the syslog which shows the wireless association stuck in some sort of loop.

Any advice appreciated.

wlan0     Scan completed :
          Cell 01 - Address: 00:1E:2A:10:90:16
                    ESSID:"LINKSYS"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:90/100  Signal level:-38 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK


Apr 23 20:55:04 russell-laptop NetworkManager: <info>  (wlan0): device state change: 6 -> 2 
Apr 23 20:55:04 russell-laptop NetworkManager: <info>  (wlan0): deactivating device (reason: 0). 
Apr 23 20:55:04 russell-laptop NetworkManager: <info>  Policy set 'Vodafone (contract)' (ppp0) as default for routing and DNS. 
Apr 23 20:55:04 russell-laptop NetworkManager: <info>  (wlan0): taking down device. 
Apr 23 20:55:04 russell-laptop avahi-daemon[2689]: Withdrawing address record for fe80::290:4bff:fed1:69a3 on wlan0.
Apr 23 20:55:11 russell-laptop NetworkManager: <info>  (wlan0): bringing up device. 
Apr 23 20:55:11 russell-laptop NetworkManager: <info>  (wlan0): device state change: 2 -> 3 
Apr 23 20:55:11 russell-laptop kernel: [ 2358.165358] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Apr 23 20:55:11 russell-laptop NetworkManager: <info>  (wlan0): supplicant interface state:  starting -> ready 
Apr 23 20:55:21 russell-laptop NetworkManager: <info>  Activation (wlan0) starting connection 'Auto LINKSYS' 
Apr 23 20:55:21 russell-laptop NetworkManager: <info>  (wlan0): device state change: 3 -> 4 
Apr 23 20:55:21 russell-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled... 
Apr 23 20:55:21 russell-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started... 
Apr 23 20:55:21 russell-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled... 
Apr 23 20:55:21 russell-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete. 
Apr 23 20:55:21 russell-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting... 
Apr 23 20:55:21 russell-laptop NetworkManager: <info>  (wlan0): device state change: 4 -> 5 
Apr 23 20:55:21 russell-laptop NetworkManager: <info>  Activation (wlan0/wireless): access point 'Auto LINKSYS' has security, but secrets are required. 
Apr 23 20:55:21 russell-laptop NetworkManager: <info>  (wlan0): device state change: 5 -> 6 
Apr 23 20:55:21 russell-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete. 
Apr 23 20:55:31 russell-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  inactive -> scanning 
Apr 23 20:55:40 russell-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled... 
Apr 23 20:55:40 russell-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started... 
Apr 23 20:55:40 russell-laptop NetworkManager: <info>  (wlan0): device state change: 6 -> 4 
Apr 23 20:55:40 russell-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled... 
Apr 23 20:55:40 russell-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete. 
Apr 23 20:55:40 russell-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting... 
Apr 23 20:55:40 russell-laptop NetworkManager: <info>  (wlan0): device state change: 4 -> 5 
Apr 23 20:55:40 russell-laptop NetworkManager: <info>  Activation (wlan0/wireless): connection 'Auto LINKSYS' has security, and secrets exist.  No new secrets needed. 
Apr 23 20:55:40 russell-laptop NetworkManager: <info>  Config: added 'ssid' value 'LINKSYS' 
Apr 23 20:55:40 russell-laptop NetworkManager: <info>  Config: added 'scan_ssid' value '1' 
Apr 23 20:55:40 russell-laptop NetworkManager: <info>  Config: added 'key_mgmt' value 'WPA-PSK' 
Apr 23 20:55:40 russell-laptop NetworkManager: <info>  Config: added 'psk' value '<omitted>' 
Apr 23 20:55:40 russell-laptop NetworkManager: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Apr 23 20:55:40 russell-laptop NetworkManager: nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Apr 23 20:55:40 russell-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete. 
Apr 23 20:55:40 russell-laptop NetworkManager: <info>  Config: set interface ap_scan to 1 
Apr 23 20:55:40 russell-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> disconnected 
Apr 23 20:55:41 russell-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning 
Apr 23 20:55:46 russell-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating 
Apr 23 20:55:46 russell-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> associated 
Apr 23 20:55:46 russell-laptop kernel: [ 2393.611144] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Apr 23 20:55:46 russell-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> 4-way handshake 
Apr 23 20:55:46 russell-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  4-way handshake -> group handshake 
Apr 23 20:55:48 russell-laptop avahi-daemon[2689]: Registering new address record for fe80::290:4bff:fed1:69a3 on wlan0.*.
Apr 23 20:55:52 russell-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  group handshake -> associated 
Apr 23 20:55:52 russell-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> 4-way handshake 
Apr 23 20:55:52 russell-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  4-way handshake -> group handshake 
Apr 23 20:55:55 russell-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  group handshake -> associated 
Apr 23 20:55:56 russell-laptop NetworkManager: <info>  wlan0: link timed out. 
Apr 23 20:55:56 russell-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> 4-way handshake 
Apr 23 20:55:56 russell-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  4-way handshake -> group handshake 
Apr 23 20:55:57 russell-laptop kernel: [ 2404.444228] wlan0: no IPv6 routers present
Apr 23 20:56:00 russell-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  group handshake -> associated 
Apr 23 20:56:01 russell-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> 4-way handshake 
Apr 23 20:56:01 russell-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  4-way handshake -> group handshake 
Apr 23 20:56:04 russell-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  group handshake -> associated 
Apr 23 20:56:04 russell-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> 4-way handshake 
Apr 23 20:56:04 russell-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  4-way handshake -> group handshake 
Apr 23 20:56:08 russell-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  group handshake -> associated 
Apr 23 20:56:08 russell-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> 4-way handshake 
Apr 23 20:56:08 russell-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  4-way handshake -> group handshake 
Apr 23 20:56:11 russell-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  group handshake -> associated 
Apr 23 20:56:11 russell-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> 4-way handshake 
Apr 23 20:56:11 russell-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  4-way handshake -> group handshake 
Apr 23 20:56:15 russell-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  group handshake -> associated 
Apr 23 20:56:15 russell-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> 4-way handshake 
Apr 23 20:56:15 russell-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  4-way handshake -> group handshake 
Apr 23 20:56:18 russell-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  group handshake -> associated 
Apr 23 20:56:18 russell-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> 4-way handshake 
Apr 23 20:56:18 russell-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  4-way handshake -> group handshake 
Apr 23 20:56:21 russell-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  group handshake -> associated 
Apr 23 20:56:21 russell-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> 4-way handshake 
Apr 23 20:56:21 russell-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  4-way handshake -> group handshake 
Apr 23 20:56:25 russell-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  group handshake -> associated 
Apr 23 20:56:26 russell-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> 4-way handshake 
Apr 23 20:56:26 russell-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  4-way handshake -> group handshake 
Apr 23 20:56:29 russell-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  group handshake -> associated 
Apr 23 20:56:29 russell-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> 4-way handshake 
Apr 23 20:56:29 russell-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  4-way handshake -> group handshake 
Apr 23 20:56:33 russell-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  group handshake -> associated 
Apr 23 20:56:33 russell-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> 4-way handshake 
Apr 23 20:56:33 russell-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  4-way handshake -> group handshake 
Apr 23 20:56:36 russell-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  group handshake -> associated 
Apr 23 20:56:36 russell-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> 4-way handshake 
Apr 23 20:56:36 russell-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  4-way handshake -> group handshake 
Apr 23 20:56:40 russell-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  group handshake -> associated 
Apr 23 20:56:40 russell-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> 4-way handshake 
Apr 23 20:56:40 russell-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  4-way handshake -> group handshake 
Apr 23 20:56:41 russell-laptop NetworkManager: <info>  Activation (wlan0/wireless): association took too long. 
Apr 23 20:56:41 russell-laptop NetworkManager: <info>  (wlan0): device state change: 5 -> 9 
Apr 23 20:56:41 russell-laptop NetworkManager: <info>  Activation (wlan0) failed for access point (LINKSYS) 
Apr 23 20:56:41 russell-laptop NetworkManager: <info>  Marking connection 'Auto LINKSYS' invalid. 
Apr 23 20:56:41 russell-laptop NetworkManager: <info>  Activation (wlan0) failed. 
Apr 23 20:56:41 russell-laptop NetworkManager: <info>  (wlan0): device state change: 9 -> 3 
Apr 23 20:56:41 russell-laptop NetworkManager: <info>  (wlan0): deactivating device (reason: 0). 
Apr 23 20:56:41 russell-laptop NetworkManager: <info>  Policy set 'Vodafone (contract)' (ppp0) as default for routing and DNS.

---

### Post by lisati on 2009-04-24
can't see the syslog.....

---

### Post by jimv on 2009-04-24
Mine appears to be doing the same thing in 9.04.  If I disable the security (WPA) on my router, it connects just fine.  Oddly, the only error reported by wpa-supplicant is that connection timed out.

---

### Post by davidyu on 2009-04-25
I have the same 9.04 upgrade problem. My wireless not working any more.

Model : Thinkpad T40
Networrd card : Atheros  AR5211 802.11ab NIC

---

### Post by Otterpanda on 2009-04-25
Yup, same problem here. My wireless was fine in Intrepid, upgraded to Jaunty and now the network is detected but it just asks for the password over and over, refuses to connect. Blah, hopefully we'll find a fix soon :D

---

### Post by shaze on 2009-04-25
Pretty similar issue with me on an Intel 2200BG, I started a launchpad bug on it.

[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/366217?comments=all](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/366217?comments=all)

---

### Post by gopalsingh on 2009-04-25
Same problem here. I cannot connect to my router when it has got WPA encryption since upgrading to 9.04, but when i change the encryption to WEP or even if I disable encryption (open wlan) then it connects fine.

I am using a TP-Link TL-WN320G usb wifi dongle (SiS163U chipset) with ndiswrapper to load the driver for it, and my router is a D-Link DGL-4300.

Here is a log from my daemon.log of me trying to connect and then it failing, my wifi SSID is 'chauhan':

```


Apr 25 21:19:40 Medion NetworkManager: <info>  Activation (wlan0) starting connection 'Auto chauhan' 
Apr 25 21:19:40 Medion NetworkManager: <info>  (wlan0): device state change: 3 -> 4 
Apr 25 21:19:40 Medion NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled... 
Apr 25 21:19:40 Medion NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started... 
Apr 25 21:19:40 Medion NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled... 
Apr 25 21:19:40 Medion NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete. 
Apr 25 21:19:40 Medion NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting... 
Apr 25 21:19:40 Medion NetworkManager: <info>  (wlan0): device state change: 4 -> 5 
Apr 25 21:19:40 Medion avahi-daemon[2807]: Interface wlan0.IPv4 no longer relevant for mDNS.
Apr 25 21:19:40 Medion NetworkManager: <info>  Activation (wlan0/wireless): connection 'Auto chauhan' has security, and secrets exist.  No new secrets needed. 
Apr 25 21:19:40 Medion NetworkManager: <info>  Config: added 'ssid' value 'chauhan' 
Apr 25 21:19:40 Medion NetworkManager: <info>  Config: added 'scan_ssid' value '1' 
Apr 25 21:19:40 Medion NetworkManager: <info>  Config: added 'key_mgmt' value 'WPA-PSK' 
Apr 25 21:19:40 Medion NetworkManager: <info>  Config: added 'psk' value '<omitted>' 
Apr 25 21:19:40 Medion NetworkManager: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Apr 25 21:19:40 Medion NetworkManager: nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Apr 25 21:19:40 Medion NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete. 
Apr 25 21:19:40 Medion NetworkManager: <info>  (wlan0): supplicant connection state:  completed -> disconnected 
Apr 25 21:19:40 Medion NetworkManager: <info>  Config: set interface ap_scan to 1 
Apr 25 21:19:40 Medion NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning 
Apr 25 21:19:45 Medion NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating 
Apr 25 21:19:46 Medion NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> 4-way handshake 
Apr 25 21:19:46 Medion NetworkManager: <info>  (wlan0): supplicant connection state:  4-way handshake -> associated 
Apr 25 21:19:56 Medion NetworkManager: <info>  wlan0: link timed out. 
Apr 25 21:19:57 Medion NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> disconnected 
Apr 25 21:19:57 Medion NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning 
Apr 25 21:20:12 Medion NetworkManager: <info>  wlan0: link timed out. 
Apr 25 21:20:12 Medion NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating 
Apr 25 21:20:13 Medion NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> 4-way handshake 
Apr 25 21:20:13 Medion NetworkManager: <info>  (wlan0): supplicant connection state:  4-way handshake -> associated 
Apr 25 21:20:24 Medion NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> disconnected 
Apr 25 21:20:24 Medion NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning 
Apr 25 21:20:29 Medion NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating 
Apr 25 21:20:29 Medion NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> 4-way handshake 
Apr 25 21:20:29 Medion NetworkManager: <info>  (wlan0): supplicant connection state:  4-way handshake -> associated 
Apr 25 21:20:39 Medion NetworkManager: <info>  wlan0: link timed out. 
Apr 25 21:20:40 Medion NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> disconnected 
Apr 25 21:20:40 Medion NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning 
Apr 25 21:20:41 Medion NetworkManager: <info>  Activation (wlan0/wireless): association took too long. 
Apr 25 21:20:41 Medion NetworkManager: <info>  (wlan0): device state change: 5 -> 6 
Apr 25 21:20:41 Medion NetworkManager: <info>  Activation (wlan0/wireless): asking for new secrets 
Apr 25 21:20:41 Medion NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> disconnected 
Apr 25 21:20:44 Medion NetworkManager: <WARN>  get_secrets_cb(): Couldn't get connection secrets: applet-device-wifi.c.1539 (get_secrets_dialog_response_cb): canceled. 
Apr 25 21:20:44 Medion NetworkManager: <info>  (wlan0): device state change: 6 -> 9 
Apr 25 21:20:44 Medion NetworkManager: <info>  Activation (wlan0) failed for access point (chauhan) 
Apr 25 21:20:44 Medion NetworkManager: <info>  Marking connection 'Auto chauhan' invalid. 
Apr 25 21:20:44 Medion NetworkManager: <info>  Activation (wlan0) failed. 


```

---

### Post by Tiger770 on 2009-04-25
I'm having the same problem on my Dell Latitude D620 laptop.  

Ironically, I upgraded my *OLD* IBM Thinkpad from 8.10 to 9.04 last night as well, and it's working fine.  I think the distinction may be that I'm running xubuntu on the thinkpad laptop with older hardware than the Latitude - it's running Kubuntu 9.04.

The Wireless network they both are connecting to is the same - a WPA-PSK network.  Weird how the xubuntu network manager lets it connect while the kubuntu won't.  Of course with different hardware, I'm curious if it IS the hardware or the software.

---

### Post by gopalsingh on 2009-04-25
Just wondering if any of you guys getting this problem could boot into Ubuntu 9.04 from the 9.04 install CD/usb in the "Live" mode to test if it still happens with a completely fresh install?

(I would but I have run out of blank discs and my pc doesnt boot from usb :()

Also, another thing to try could be to use another wifi manager to connect to the wifi network ([such as wicd]("http://wicd.sourceforge.net/")) and see if it connects with software other than the NetworkManager Applet that comes with Ubuntu by default.

Hopefully this gets sorted soon because its forcing me to use WinXP at the moment for internet access :(

---

### Post by Tiger770 on 2009-04-25
> **gopalsingh said:**
> Just wondering if any of you guys getting this problem could boot into Ubuntu 9.04 from the 9.04 install CD/usb in the "Live" mode to test if it still happens with a completely fresh install?

(I would but I have run out of blank discs and my pc doesnt boot from usb :()

Also, another thing to try could be to use another wifi manager to connect to the wifi network ([such as wicd]("http://wicd.sourceforge.net/")) and see if it connects with software other than the NetworkManager Applet that comes with Ubuntu by default. (I dont have the technical knowledge on how to do this sorry!)

Hopefully this gets sorted soon because its forcing me to use WinXP at the moment for internet access :(


I can test out the live CD on my Latitude, but unfortunately I only burned the i386 version and the laptop had x64 installed.  I guess I failed to mention that last post - the Latitude with the problem is also running x64 and the laptop that is working is running i386.

I test it out in live and post back.

---

### Post by Shawn Parr on 2009-04-25
I'm working with a Dell D600 that has this issue.  I installed WICD and it connects to my wpa network.  It has several different options for the WPA supplicant, I am using the default (wext) right now.  What is the supplicant used by the build in Network Manager?

I just had 8.10 installed and it worked fine, so hopefully this is a minor bug that can be quickly fixed.

One interesting thing, in 8.10 the B43 showed up in the Hardware Drivers app, but in 9.04 it doesn't seem to.  Hmm, just double checked that and now it does, and it shows in use.  Perhaps installing WICD had that effect?

Anyway I'm going to keep an eye on this thread just in case.  For the time being probably will go back to 8.10.  Ultimately I'll probably use this very little, I was hoping to get a couple associates into the linux game.  Ah well.

---

### Post by gopalsingh on 2009-04-25
> **gopalsingh said:**
> Same problem here. I cannot connect to my router when it has got WPA encryption since upgrading to 9.04, but when i change the encryption to WEP or even if I disable encryption (open wlan) then it connects fine.

I am using a TP-Link TL-WN320G usb wifi dongle (SiS163U chipset) with ndiswrapper to load the driver for it, and my router is a D-Link DGL-4300.

Here is a log from my daemon.log of me trying to connect and then it failing, my wifi SSID is 'chauhan':

(See prev post for log)



I managed to get mine connecting to WPA networks again.

My wireless chipset (sis163u) is not supported by default by a fresh ubuntu install, so I have always used ndiswrapper and load up the windows drivers to get wifi working.

I previously had the WinXP sis163u drivers installed from the TP-Link website using ndiswrapper (using the ndisgtk GUI) which previously worked perfectly under Ubuntu 8.10, but were now causing WPA issues in 9.04. I simply uninstalled the WinXP drivers from the TP-Link website and installed the WinXP drivers from the SiS website, and now WPA works perfect! :)

Uninstalling the SiS WinXP drives and returning to the TP-Link WinXP drivers causes the problem with WPA networks again, so it seems to be a driver incompatibility for me, but extremely strange that everything worked perfect in ubuntu 8.10.

If anybody else is having the same problems with WPA and are using ndiswrapper, just try out some other drivers and you could get it working again.

---

### Post by Tiger770 on 2009-04-25
The Wifi Card in my D620 has always worked with previous revisions - also, I just booted up and am posting from the Live x86 CD - so I know it's functional from the disc.  

I too, had 8.10 installed and customized just the way I like it.  I'd be really sad if I had to start over from scratch.....

---

### Post by borzwazie on 2009-04-26
FWIW, I have a Prism2 card, and wpa wasn't working, so I did this:

blacklist orinoco_pci
blacklist orinoco
blacklist prism2_pci
blacklist hermes

in /etc/modprobe.d/blacklist.conf

Rebooted, and all is well.

Hope this helps!

---

### Post by darkreaction on 2009-04-26
I have the same problem here I have a Netgear card with a Linksys router. Worked fine in 8.10 no longer works in 9.04. secured or unsecured.

---

### Post by davidyu on 2009-04-26
Fortunately, my wireless issue is solved now.
My solution:
1.From menu bar\System\Administration\Hardware Drivers
2. In the Hardware Drivers dialogbox, there's an Deactived item:
   Alternate Atheros "MadWifi" driver.
3. There's a "Activate" button, and I click this button and press "Close" button
4. Reboot my Ubuntu. then wireless works OK.

You may can find the appropriate wireless driver from "Hardware Driver"

---

### Post by gopalsingh on 2009-04-26
> **gopalsingh said:**
> I managed to get mine fully working and connecting to WPA networks again.

My wireless chipset (sis163u) is not supported by default by a fresh ubuntu install, so I have always used ndiswrapper and load up the windows drivers to get wifi working.

I previously had the WinXP sis163u drivers installed from the TP-Link website using ndiswrapper (using the ndisgtk GUI) which previously worked perfectly under Ubuntu 8.10, but were now causing WPA issues in 9.04. I simply uninstalled the WinXP drivers from the TP-Link website and installed the WinXP drivers from the SiS website, and now WPA works perfect! :)

Uninstalling the SiS WinXP drives and returning to the TP-Link WinXP drivers causes the problem with WPA networks again, so its definitely a driver incompatibility for me.

If anybody else is having the same problems with WPA and are using ndiswrapper, just try out some other drivers and you could get it working again. :)

God this is doing my head in, just found that I cannot connect to WEP networks with the tp-link driver.

With the TP-Link drivers, WEP networks work fine, but WPA networks do not work.

With the SiS drivers, WPA networks work fine, but WEP networks do not work.

:confused:

EDIT: Just tried out WICD instead of the default NetworkManager that comes with Ubuntu. Using the TP-Link driver I could connect to WEP networks but not any WPA. With the SiS driver the system would completely freeze when trying to connect to any network at all.


EDIT2: After searching through the launchpad bugs for Jaunty, it seems quite a lot of people have the exact same problem that after upgrading to 9.04 they cannot connect to WPA networks, but non-WPA networks work fine. A few people said it was solved after they installed "linux-backports-modules-jaunty" through the synaptic package manager and then restarting their pc, but that didnt work for me :(

---

### Post by themisanthrope on 2009-04-26
*Also, another thing to try could be to use another wifi manager to connect to the wifi network (such as wicd) and see if it connects with software other than the NetworkManager Applet that comes with Ubuntu by default.*

Hello people.

Maybe by version 10 Ubuntu will finally make WiFi something other than a six-hour, hair-pulling, foul-language-spewing affair?

FWIW, I just tried replacing network-manager with wicd. wicd failed over and over again, but at least quickly. Prior to installing wicd, network-manager would, after about four tries, and after popping up a "Disconnected" message, connect. Re-installed network-manager and now no amount of retries will connect.

With so many having trouble with wireless through all these versions, why the f--k can they not get this fixed? Like so many, I want with all my heart to flip Redmond the bird, and I have for the most part on my wired desktops, but when I try to go wireless, I just give up and surender to XP.

This is just plain bullshjt.

---

### Post by Sunflower1970 on 2009-04-26
> **gopalsingh said:**
> Just wondering if any of you guys getting this problem could boot into Ubuntu 9.04 from the 9.04 install CD/usb in the "Live" mode to test if it still happens with a completely fresh install?

(I would but I have run out of blank discs and my pc doesnt boot from usb :()

Also, another thing to try could be to use another wifi manager to connect to the wifi network ([such as wicd]("http://wicd.sourceforge.net/")) and see if it connects with software other than the NetworkManager Applet that comes with Ubuntu by default.

Hopefully this gets sorted soon because its forcing me to use WinXP at the moment for internet access :(

Just tried out the live CD here. I cannot connect using WPA2 & NM. Works fine in Intrepid. On a Thinkpad R40, the card's a D-Link, Atheros Communications Inc. Atheros AR5001X+ Wireless Network Adapter (rev 01) and the router's a Linksys WRT54G

Have used wicd in the past, and will use it again, if needed...but was kind of hoping to stick with NM since it worked so well in Intrepid

---

### Post by jimv on 2009-04-27
Bump.

---

### Post by Titoolsen on 2009-04-27
Has this been resolved yet? I am in the process of trying to boot my PC using the new Ubuntu 9 download but dont want to do this if wireless access is a problem.

---

### Post by helmut0 on 2009-04-27
I just upgraded myself from 8.10 to 9.04 on a MSI 64 bit and have no wired or wireless on network manager.I went under networking and the OS see's both my cards and says they are transmitting and receiving,but network manager doesn't see it.

---

### Post by jimv on 2009-04-28
Bump.  My syslog looks like the OP's.  Tries doing the handshake but eventually times out.  I'm writing this from 8.10, which is working fine.

---

### Post by gopalsingh on 2009-04-28
I just booted up the 8.10 live cd, didnt do anything apart from used ndiswrapper and loaded my wifi driver and it worked perfect with WEP and WPA.
I booted up the 9.04 live cd, didnt do anything apart from ndiswrapper with the EXACT same driver files. It came up with the "Unable to see if hardware is present" message which didnt happen in 8.10, but the driver seemed to load perfectly fine. I could connect fine to WEP and open networks, but not with WPA. It would just keep retrying and then eventually come back with the WPA password request box.

So this proves that from 8.10 to 9.10 they have definately broken something to do with WPA for all of us...

---

### Post by jimv on 2009-04-28
When I was using Juanty Beta 4 or 5, everything was working perfectly.  Then I installed some updates and WPA stopped working...it hasn't worked since.

Now, if I install a fresh copy of 9.04, I can connect with the rtl8180 driver, but that driver cuts out all the time (with my rtl8185L) and shows the wrong signal strength, so I use Ndiswrapper.  In 9.04, when I install Ndiswrapper, WPA stops working.  I tried installing a newer build from the code repo on Sourceforge, but that didn't help.  I tried installing the older version of wpasupplicant from Intrepid...didn't help.  I also tried a manual connection from the command line, but that didn't work either.

I'm also noticing that it doesn't save my password like Intrepid does...it saves a long hex string.  Also, in the syslog in Jaunty, NetworkManager says a bunch of stuff about a 4-way handshake, while Intrepid doesn't say anything about that.

Ideas are welcome!

---

### Post by groovomata on 2009-04-28
While looking through some other posts, I found this rather helpful looking page to help troubleshoot this issue. Once I get home (sssh, I'm at work now) I'm going to give it a go.
[https://help.ubuntu.com/9.04/internet/C/troubleshooting-wireless.html](https://help.ubuntu.com/9.04/internet/C/troubleshooting-wireless.html)

---

### Post by barrel_master on 2009-04-28
I had similar problems myself... my solution... use 8.04 LTS.

---

### Post by helmut0 on 2009-04-28
Yup 8.10 is really looking good.I am running 9.04 on 3 machines.2 are 32 bit and one 64 bit,and it's just the 64bit that network manager won't talk to my wired or wireless cards.

---

### Post by jimv on 2009-04-28
> **barrel_master said:**
> I had similar problems myself... my solution... use 8.04 LTS.

That's why I always install the new version on a different partition...in case the new version has issues.  That said, I'd like to use 9.04 full-time as it's a lot snappier on my machine than 8.10 or 8.04.

---

### Post by gnoob on 2009-04-28
I have this same problem with a belkin card. I temporarily solved this by switching my router to WEP (from WPA2). Obviously this isn't a very good solution though. I think we just have to wait for an update which will probably be coming soon. or go back to hardy/intrepid.

---

### Post by Bogdon6 on 2009-04-29
I had a similar problem. Here's what worked for me: 

1. Click on System | Administration | Hardware Drivers
2. In the Hardware Drivers dialog box, there's an deactivated item:
Alternate Atheros "MadWifi" driver.
3. Click on Alternate Atheros "MadWifi" driver, the click on "Activate" in the lower left hand corner. Then click close.  
4. Reboot. 

Now wireless works, at least for me. Good luck!

---

### Post by alexi452 on 2009-05-01
Hello everyone,

I have a Broadcom BCM4306, and it took a while for me to get it to work on 8.10 (needed it to work with amd64), but I eventually did.  When I upgraded it could see the networks, and could connect to unprotected networks fine, but wouldn't connect to my WPA network (which sounds like the problem some of you have been having).

I have gotten something to work, although it isn't a great solution: 1) get rid of IPv6 and 2) manually setup connection with wpasupplicant. I don't know how well it will work for others.

To get rid of IPv6, which (if I remember what I read correctly) is no longer a separate module, but is built into the kernel, I had to recompile the kernel.  I followed the directions outlined by MidasTouch in [http://ubuntuforums.org/showthread.php?t=1114211](http://ubuntuforums.org/showthread.php?t=1114211) about 3/4 down the first page.  If your relatively new to linux, be a little careful in following the directions, namely don't just copy what he says in step 3, for example where he has "$(uname -r)", which (perhaps I'm mistaken), but you should first find the output of uname -r and then enter that output.    Also, this will take a little while (a few hours for me).  I told it to not include IPv6, but it might be desireable to include it as a module and then blacklist it (which should produce the same effect, but perhaps won't with respect to this problem - I don't know in quite what way IPv6 was causing problems with netmanager).

Once that is done, I then followed the directions by Kevdog in [http://ubuntuforums.org/showthread.php?t=684495](http://ubuntuforums.org/showthread.php?t=684495) which describes how to connect without using network manager.  This is fairly simple and quick.  Two things that might be noteworthy is that when running wpa_supplicant, it told me "-w" was not an option, so I ignored that, and wpa_supplicant will run continuously, so in typing the rest of the commands (assuming you are using the WPA section), enter them into a separate terminal.   Also, network manager will display that there is no working connection, even though there (hopefully) will be.   

Also, one thing that is occuring to me that might work is that perhaps if you do recompile without IPv6, and then recompile networkmanager, then the latter might work (just recompiling the kernel didn't seem to fix it for me).

Good luck!

---

### Post by desgua on 2009-05-01
I had spent hours to make my atheros 5007eg wireless work in ubuntu 8.10 but now it work "out of the box" in a clear install although not with the update.

It took me a long time to get to work my Atheros 5007eg wireless card in ubuntu 8.10, but with a clear install of ubuntu 9.10 it worked automatically, although it doesn't work with the update of previous version.

Great!

---

### Post by justin23 on 2009-05-02
Im having the exact same issue.  It keeps asking for my password over and over.  Can't connect.  I installed the OS three times and still have the same issue.  I installed the 32 bit version and I'm still having the same problem.

---

### Post by groovomata on 2009-05-09
My issue is that my Dell Inspiron 6400, can only connect to my wireless network immediately after a boot, suspend or hibernation and then it will invariably lose that connection after a few minutes. Every time. I can see wireless networks with the Broadcom BCM4311 fwcutter driver installed, and the wireless network indicator light is on. If I use the Broadcom STA driver then I don't see any networks and my wireless indicator light doesn't go on. So I'm pretty much stuck with the Broadcom BCM4311 driver. Anyhow, I posted a launchpad bug report: [HTML]https://bugs.launchpad.net/ubuntu/+bug/373791[/HTML]
Regards,
Erik.

---

### Post by albertz on 2009-05-14
Having the same issue here. Is there any possibility to downgrade to 8.10 ?

---

### Post by sebeni on 2009-05-14
same problem for me, just upgraded from Ibex to Jacky.I still have WinXP installed parallel.And the W-Lan is still working perfectly.

-----------------------------------

Thinkpad T41, CiscoSystemsW-LanAdapter 802.11g,Speedport500 (AP)




"Imagination creates reality.Man is all imagination" *Neville*

---

### Post by frank_cny on 2009-05-14
I tried Davidyu's suggestion and it solved my problem on my IBM T40.

---

### Post by themisanthrope on 2009-05-23
This thing has been running long enough now with no issues (couple of weeks) that I think I can say it's working.

I had wireless without WPA-PSK working with a WuBi install and MadWi-Fi driver. Nothing would get WPA-PSK to happen with any degree of reliability. After a rainy day, nothing to lose and nothing better to do "real" (partitioned) install - only this time around, WITHOUT using the alternate driver - lo and behold, not just wireless, but WPA-PSK as well. Hundreds of boot cycles - and not quite as many crossed fingers - later, I can honestly say that this thing is working with solid, reliable, WPA wireless connections. Your mileage may vary, but you can add one working instance of the following machine/card to the list:

Model: Toshiba L25-S1192
Card: Atheros AR5211

---

### Post by Wolfhere on 2009-05-26
While in 8.10, I upgraded rather than built a new install. Knowing the problems others here have had with wireless, I was hesitant. Well, the in-place upgrade went smoothly. I am now running 9.04 with Broadcom Corporation BCM4312 802.11a/b/g on my Dell D620 wireless and Broadcom Corporation NetXtreme BCM5752 Gigabit Ethernet PCI Express (rev 02) wired. When doing the install, I was prompted to upgrade my drivers for wireless, and everything went smoothly. Well done Ubuntu! Much better than upgrading from 8.04 to 8.10.

---

### Post by groovomata on 2009-06-01
I am currently typing this note using a wireless connection. After I was unable to get wireless to work with ubuntu 9.04, I got paranoid that my wireless adapter was no longer working and decided to see if it would work if I install Windows Vista on my computer. Lo and behold, it did not, but while digging around in vista, one dialogue box informed me that my card was not enabled, and indeed the little wireless light was not lit in vista. Once I enabled it, wireless worked fine in vista. So then I wiped out vista and re-installed Jaunty and voila! My wireless worked. I very much prefer ubuntu over Windows, but I do wish in all of the different outputs of various commands that I pored over, one of them had simply said that my wireless card was not enabled, afterall, the little wireless light was on the whole time in ubuntu. How was I to know?
Anyways, I'm happy to report that my wireless now works fine!

---

### Post by calebhoward on 2009-06-03
This is interesting.  I just installed on a new laptop.  The live disk found my wifi network OK, but the install did not.  Why did you ask this question, and can you offer a clue as to why this should be the case?

THanks!

-caleb

---

### Post by peterwil on 2009-06-05
I have a TOSHIBA L305D-S5881 (AMD 64bit) with Atheros wireless chip. The wireless has been working right for about 6 months now
without any problems on Hardy 8.0.4.
Yesterday I switched over to Jaunty and used the same procedure
to connect to my WEP enabled wireless network.
Please see this link..
[http://ubuntuforums.org/showthread.php?t=816780&highlight=HOWTO+madwifi](http://ubuntuforums.org/showthread.php?t=816780&highlight=HOWTO+madwifi).

Here is my process
1) Boot from live CD.Install Jaunty
2) sudo aptitude update
3) sudo apt-get install build-essential
4) sudo apt-get install linux-restricted-modules-$(uname -r)
5) sudo make install ( from the previous subversion downloaded madwifi package .. now in my home directory)
6)sudo depmod -ae
7) sudo modprobe ath_pci

Go to System Prefs -Network Connections -Wireless..add a connection.. Put in your SSID and security creds
and you are connected..

Hope this works for you as well..

Cheers
Peter

---

### Post by ks07078 on 2009-12-04
I installed Ubuntu 9.04 on my Dell Latitude laptop yesterday. Wireless did not work but it alerted me that there is a wireless driver (Broadcom I think)  that I can enable. I did that, but it still wouldn't work.

For the rest of the day I just moved near the router and plugged into a ethernet cable. Then shut the machine off for the night.

Today I turned it on and started using the ethernet. On whim I clicked on the wireless icon and said 'connect to new network' and put my wireless NW name in and it connected!

No clue why it would work now - I had tried the same thing a dozen times yesterday!

Anyway I hope it continues to work after I reboot!

---

