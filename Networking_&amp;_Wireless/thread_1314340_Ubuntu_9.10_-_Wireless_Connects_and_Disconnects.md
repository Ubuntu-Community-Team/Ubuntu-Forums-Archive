---
title: "Ubuntu 9.10 - Wireless Connects and Disconnects"
date: 2009-11-04
forum: Networking &amp; Wireless
---

### Post by sirsmilealot on 2009-11-04
Hello All,

For some reason since the upgrade to .10 my wireless connection will connect and disconnect at regular intervals for no apparent reason. I can confirm this was working without fault before the upgrade.

Here's a snippet from my syslog:

```
Nov  4 16:34:40 Laptop-1 wpa_supplicant[1510]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Nov  4 16:34:40 Laptop-1 NetworkManager: <info>  (wlan0): supplicant connection state:  completed -> disconnected
Nov  4 16:34:41 Laptop-1 kernel: [ 3350.972049] wlan0: direct probe to AP 00:02:72:75:34:28 try 1
Nov  4 16:34:41 Laptop-1 kernel: [ 3350.974600] wlan0 direct probe responded
Nov  4 16:34:41 Laptop-1 kernel: [ 3350.974606] wlan0: authenticate with AP 00:02:72:75:34:28
Nov  4 16:34:41 Laptop-1 kernel: [ 3350.976902] wlan0: authenticated
Nov  4 16:34:41 Laptop-1 kernel: [ 3350.976907] wlan0: associate with AP 00:02:72:75:34:28
Nov  4 16:34:41 Laptop-1 kernel: [ 3350.979502] wlan0: RX ReassocResp from 00:02:72:75:34:28 (capab=0x411 status=12 aid=1)
Nov  4 16:34:41 Laptop-1 kernel: [ 3350.979507] wlan0: AP denied association (code=12)
Nov  4 16:34:41 Laptop-1 kernel: [ 3351.177618] wlan0: associate with AP 00:02:72:75:34:28
Nov  4 16:34:41 Laptop-1 kernel: [ 3351.179732] wlan0: RX AssocResp from 00:02:72:75:34:28 (capab=0x411 status=12 aid=1)
Nov  4 16:34:41 Laptop-1 kernel: [ 3351.179738] wlan0: AP denied association (code=12)
Nov  4 16:34:42 Laptop-1 kernel: [ 3351.376036] wlan0: associate with AP 00:02:72:75:34:28
Nov  4 16:34:42 Laptop-1 kernel: [ 3351.378287] wlan0: RX AssocResp from 00:02:72:75:34:28 (capab=0x411 status=12 aid=1)
Nov  4 16:34:42 Laptop-1 kernel: [ 3351.378292] wlan0: AP denied association (code=12)
Nov  4 16:34:42 Laptop-1 wpa_supplicant[1510]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Nov  4 16:34:42 Laptop-1 kernel: [ 3351.576052] wlan0: association with AP 00:02:72:75:34:28 timed out
Nov  4 16:34:44 Laptop-1 NetworkManager: <debug> [1257352484.001865] periodic_update(): Roamed from BSSID 00:02:72:75:34:28 (WLAN-1) to (none) ((none))
Nov  4 16:34:45 Laptop-1 NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Nov  4 16:34:48 Laptop-1 wpa_supplicant[1510]: CTRL-EVENT-SCAN-RESULTS 
Nov  4 16:34:48 Laptop-1 wpa_supplicant[1510]: Trying to associate with 00:02:72:75:34:28 (SSID='WLAN-1' freq=2462 MHz)
Nov  4 16:34:48 Laptop-1 wpa_supplicant[1510]: Association request to the driver failed
Nov  4 16:34:48 Laptop-1 NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Nov  4 16:34:48 Laptop-1 kernel: [ 3358.146270] wlan0: authenticate with AP 00:02:72:75:34:28
Nov  4 16:34:48 Laptop-1 kernel: [ 3358.148235] wlan0: authenticated
Nov  4 16:34:48 Laptop-1 kernel: [ 3358.148240] wlan0: associate with AP 00:02:72:75:34:28
Nov  4 16:34:48 Laptop-1 kernel: [ 3358.151176] wlan0: RX AssocResp from 00:02:72:75:34:28 (capab=0x411 status=12 aid=1)
Nov  4 16:34:48 Laptop-1 kernel: [ 3358.151182] wlan0: AP denied association (code=12)
Nov  4 16:34:49 Laptop-1 kernel: [ 3358.348046] wlan0: associate with AP 00:02:72:75:34:28
Nov  4 16:34:49 Laptop-1 kernel: [ 3358.350185] wlan0: RX AssocResp from 00:02:72:75:34:28 (capab=0x411 status=12 aid=1)
Nov  4 16:34:49 Laptop-1 kernel: [ 3358.350190] wlan0: AP denied association (code=12)
Nov  4 16:34:49 Laptop-1 kernel: [ 3358.548049] wlan0: associate with AP 00:02:72:75:34:28
Nov  4 16:34:49 Laptop-1 kernel: [ 3358.550153] wlan0: RX AssocResp from 00:02:72:75:34:28 (capab=0x411 status=12 aid=1)
Nov  4 16:34:49 Laptop-1 kernel: [ 3358.550159] wlan0: AP denied association (code=12)
Nov  4 16:34:49 Laptop-1 wpa_supplicant[1510]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Nov  4 16:34:49 Laptop-1 NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> disconnected
Nov  4 16:34:49 Laptop-1 kernel: [ 3358.748050] wlan0: association with AP 00:02:72:75:34:28 timed out
Nov  4 16:34:53 Laptop-1 wpa_supplicant[1510]: Authentication with 00:00:00:00:00:00 timed out.
Nov  4 16:34:53 Laptop-1 NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Nov  4 16:34:56 Laptop-1 NetworkManager: <info>  (wlan0): device state change: 8 -> 3 (reason 11)
Nov  4 16:34:56 Laptop-1 NetworkManager: <info>  (wlan0): deactivating device (reason: 11).
Nov  4 16:34:56 Laptop-1 NetworkManager: <info>  (wlan0): canceled DHCP transaction, dhcp client pid 6696
Nov  4 16:34:56 Laptop-1 NetworkManager: <info>  Policy set 'Auto eth0' (eth0) as default for routing and DNS.
Nov  4 16:34:56 Laptop-1 NetworkManager: <info>  Activation (wlan0) starting connection 'WLAN-1'
Nov  4 16:34:56 Laptop-1 NetworkManager: <info>  (wlan0): device state change: 3 -> 4 (reason 0)
Nov  4 16:34:56 Laptop-1 NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Nov  4 16:34:56 Laptop-1 NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Nov  4 16:34:56 Laptop-1 NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Nov  4 16:34:56 Laptop-1 NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Nov  4 16:34:56 Laptop-1 NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Nov  4 16:34:56 Laptop-1 NetworkManager: <info>  (wlan0): device state change: 4 -> 5 (reason 0)
Nov  4 16:34:56 Laptop-1 NetworkManager: <info>  Activation (wlan0/wireless): access point 'WLAN-1' has security, but secrets are required.
Nov  4 16:34:56 Laptop-1 NetworkManager: <info>  (wlan0): device state change: 5 -> 6 (reason 0)
Nov  4 16:34:56 Laptop-1 NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Nov  4 16:34:56 Laptop-1 NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> disconnected
Nov  4 16:34:56 Laptop-1 NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Nov  4 16:34:56 Laptop-1 NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Nov  4 16:34:56 Laptop-1 NetworkManager: <info>  (wlan0): device state change: 6 -> 4 (reason 0)
Nov  4 16:34:56 Laptop-1 NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Nov  4 16:34:56 Laptop-1 NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Nov  4 16:34:56 Laptop-1 NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Nov  4 16:34:56 Laptop-1 NetworkManager: <info>  (wlan0): device state change: 4 -> 5 (reason 0)
Nov  4 16:34:56 Laptop-1 NetworkManager: <info>  Activation (wlan0/wireless): connection 'WLAN-1' has security, and secrets exist.  No new secrets needed.
Nov  4 16:34:56 Laptop-1 NetworkManager: <info>  Config: added 'ssid' value 'WLAN-1'
Nov  4 16:34:56 Laptop-1 NetworkManager: <info>  Config: added 'scan_ssid' value '1'
Nov  4 16:34:56 Laptop-1 NetworkManager: <info>  Config: added 'key_mgmt' value 'WPA-PSK'
Nov  4 16:34:56 Laptop-1 NetworkManager: <info>  Config: added 'psk' value '<omitted>'
Nov  4 16:34:56 Laptop-1 NetworkManager: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Nov  4 16:34:56 Laptop-1 NetworkManager: nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Nov  4 16:34:56 Laptop-1 NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Nov  4 16:34:56 Laptop-1 NetworkManager: <info>  Config: set interface ap_scan to 1
Nov  4 16:34:56 Laptop-1 wpa_supplicant[1510]: Failed to initiate AP scan.
Nov  4 16:34:56 Laptop-1 NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Nov  4 16:34:57 Laptop-1 wpa_supplicant[1510]: CTRL-EVENT-SCAN-RESULTS 
Nov  4 16:35:06 Laptop-1 NetworkManager: <info>  (wlan0): device state change: 5 -> 3 (reason 39)
Nov  4 16:35:06 Laptop-1 NetworkManager: <info>  (wlan0): deactivating device (reason: 39).
Nov  4 16:35:06 Laptop-1 NetworkManager: <info>  Policy set 'Auto eth0' (eth0) as default for routing and DNS.
Nov  4 16:35:09 Laptop-1 wpa_supplicant[1510]: CTRL-EVENT-SCAN-RESULTS 
```

I'd be most very grateful for any help you can offer!

Cheers,

Paul.

---

### Post by ajithjk on 2009-11-05
>i have the same problem. The WLAN goes on n off at regular intervals. Please help!

---

### Post by Stevie B on 2009-11-05
Same problem here.
Running Ubuntu 9.10 on a netbook acer aspire one d250.
Also my netbook turn off when I plug in my adapter to charge ...
All help is appreciated.

---

### Post by Spartachris on 2009-11-05
Hi--hate to just post a "me to", but it happens to me and is really irritating. Hoping that someone might know what is going on.

---

### Post by GarrettFoster on 2009-11-06
Having the same problem with Network Manager. I went ahead and installed wicd instead and it seems to be doing much better. I would however like to know what it broken with Network Manager though (or what is making it disconnect so much).

Anyways here is how I did it:

System > Administration > Synaptic Package Manager
Search for: wicd
Mark for installation. It will also uninstall Network Manager
Once everything is installed restart and you should be good to go.
Note that installing Network Manager should remove wicd if the thing ever gets fixed.

---

### Post by s-s on 2009-11-07
Hi, have the same problem here on my ASUS 1005HA. Looks like I have this problem only when working as admin. When working as normal user I don't have this problem.
Probably it has something to do with the energy safe settings.

Best regards

---

### Post by mercury80 on 2009-11-16
Yeah I got the same problem... as i said here:
[http://ubuntuforums.org/showthread.php?p=8329484#post8329484](http://ubuntuforums.org/showthread.php?p=8329484#post8329484)

---

### Post by audacs on 2009-11-16
I had the same problem, all fixed with installation of wicd.

Specs: Netgear WG311v3, ndiswrapper, Ubuntu 9.10 64 bit

---

### Post by debsys07 on 2009-11-16
And another "me too" on a Toshiba Satellite. Just installed 9.10 as dual boot a few days ago & was disappointed to have to go back to Vista for decent wireless support -- embarassing.

I'll try the wicd suggestion, but why no "official" response from 9.10?

-Ron

---

### Post by SurferGTO on 2009-11-16
im not having that problem exactly, on WICD. so perhaps that may help, but what i AM noticing using WICD is that it is unable to automatically connect. upon login, i have to cancel the connection attempt, attempt, cancel, and attempt a 3rd time before it can obtain an IP. never had this problem before, and other devices on the network are not suffering from connection issues.

---

### Post by mercury80 on 2009-11-17
> **debsys07 said:**
> 
I'll try the wicd suggestion, but why no "official" response from 9.10?


Yeah I was wondering about that too... 
and I just installed ubuntu on my girlfriends computer... trying to "save" her from microsoft... you could say she is not convinced...

---

### Post by sjvega on 2009-12-01
I've tried to install wicd but it keeps disconecting...
Another solution?

---

### Post by Marc Higgins on 2009-12-01
I have exactly the same problem, network dropouts on an Acer Aspire One D250-1DQw & installing WICD did not seem to fix it for me. Also it looks like if I uninstall gnome-network-manager I lose the ability to use my mobile phone as a modem (there may be a work around for this)

Anyway this is my hardware

marc@aspireone:~$ lspci 
00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
01:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
03:00.0 Ethernet controller: Attansic Technology Corp. Atheros AR8132 / L1c Gigabit Ethernet Adapter (rev c0)

I found this bug report & I am going to trying the work the suggested here

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/474858](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/474858)

I have installed the following packages & will report back if it fixes the problem. 

linux-backports-modules-2.6.31-15-generic (2.6.31-15.17)
linux-backports-modules-2.6.31-15-generic-pae (2.6.31-15.17)
linux-backports-modules-karmic (2.6.31.15.28)
linux-backports-modules-karmic-generic (2.6.31.15.28)
linux-backports-modules-wireless-karmic-generic-pae (2.6.31.15.28)
linux-image-2.6.31-15-generic-pae (2.6.31-15.50)

So far it looks good, I just simultaneously downloaded a 700mg iso image, copied a 1.5g movie to a windows share, while I was listening to internet radio & talking on skype.... I am hopeful this is a fix

---

### Post by Marc Higgins on 2009-12-02
After almost 24 hours with no drop wireless dropouts I think I can say installing the following backport modules fixes this problem, at least for me.

linux-backports-modules-2.6.31-15-generic (2.6.31-15.17)
linux-backports-modules-2.6.31-15-generic-pae (2.6.31-15.17)
linux-backports-modules-karmic (2.6.31.15.28)
linux-backports-modules-karmic-generic (2.6.31.15.28)
linux-backports-modules-wireless-karmic-generic-pae (2.6.31.15.28)
linux-image-2.6.31-15-generic-pae (2.6.31-15.50)

---

### Post by Marc Higgins on 2009-12-02
After almost 24 hours with no drop wireless dropouts I think I can say installing the following backport modules fixes this problem, at least for me.

linux-backports-modules-2.6.31-15-generic (2.6.31-15.17)
linux-backports-modules-2.6.31-15-generic-pae (2.6.31-15.17)
linux-backports-modules-karmic (2.6.31.15.28)
linux-backports-modules-karmic-generic (2.6.31.15.28)
linux-backports-modules-wireless-karmic-generic-pae (2.6.31.15.28)
linux-image-2.6.31-15-generic-pae (2.6.31-15.50)

---

### Post by fabulous.dude on 2009-12-15
[FONT=Arial]hello,

I found a work around (sort of)...

_My setup_:
Lenovo ThinkPad T61p running Ubuntu 9.10 Karmic.
Apple AirPort Extreme router
D-Link WBR-1310 router

_Symptoms_:
Wicd Network Manager continuously connects and disconnects from the network router at regular intervals (about every 10 seconds).[/FONT]

 [FONT=Arial]_Workaround_:[/FONT]
 [FONT=Arial]Connecting to another network (D-Link) and then back to the initial network (Apple) establishes a stable connection. This has to be repeated every time my PC is powered on.[/FONT]

---

### Post by swaminathy on 2009-12-15
hii guys,

i have installed 9.10 version and now i have a problem there is no wvdial package available. i got some packages but there are not working:o
 so wat should i do now to connect internet in my desktop. i am using reliance ec325 usbmodem.

---

### Post by haribol707 on 2009-12-15
hi, I have the same problem too with my setup (posted on another thread today morning). I also found that the connection is stable on a non-secure network but shows the above behavior when I connect to a secure network. Any ideas why?

---

### Post by matmota on 2009-12-30
Same here on a Lenovo W500.
I've added the following information as comment #24 in the bug #303802 [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/303802?comments=all](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/303802?comments=all)

I have to restart network manager each time it disconnects:

```
 sudo /etc/init.d/network-manager restart
```Using HTTP, SSH, SMTP, BitTorrent etc. the disconnects are very rare, it's a bit more often with BitTorrent but I didn't have it running more than a few hours at a time.

However, VoIP (Pidgin with Google Talk) and Skype disconnect often.

Google Talk can last for a whole 10 minutes call, but it seems cumulative: sometimes it disconnects during the call, but not if I restart the network manager shortly before it.

With Skype it lasts maybe one minute. It failed each time I tried. I had to use my old PowerBook G4 running MacOS X 10.5 Leopard, which worked flawlessly, so I'm inclined to think that the problem is in my Ubuntu laptop, not the ASUS WIFI router. The network is encrypted with WPA2, which might be a factor according to another poster.

I don't remember having these problems before updating to Karmic from Jaunty, but I've had the laptop just since last June and was most of August without Internet access.

---

### Post by koshari on 2010-01-02
there Appears to be a bug regarding wpa2 tkip in 9.04 using metwork manager.

a workaround for me was to change the access point security to wpa2 aep.

[https://bugs.launchpad.net/network-manager/+bug/425455](https://bugs.launchpad.net/network-manager/+bug/425455)

its not a fix but a viable workaround for those with access to the access points config.

besides tkip is less secure than aep anyway.

---

### Post by andoty_jazz on 2010-02-12
> **GarrettFoster said:**
> 
Anyways here is how I did it:

System > Administration > Synaptic Package Manager
Search for: wicd
Mark for installation. It will also uninstall Network Manager
Once everything is installed restart and you should be good to go.
Note that installing Network Manager should remove wicd if the thing ever gets fixed.

Thank you for this. Works really good. Network Manager gives me a lot of headache when I upgrade to 9.10.

Many thanks again

---

### Post by budo on 2010-02-23
> **koshari said:**
> there Appears to be a bug regarding wpa2 tkip in 9.04 using metwork manager.

a workaround for me was to change the access point security to wpa2 aep.

[https://bugs.launchpad.net/network-manager/+bug/425455](https://bugs.launchpad.net/network-manager/+bug/425455)

its not a fix but a viable workaround for those with access to the access points config.

besides tkip is less secure than aep anyway.

Same problem!
Do you mean AES? ... unfortunately my router doesn' support it!!!
What can I try? does the backported packages in an above post really work?

---

### Post by budo on 2010-02-25
> **Marc Higgins said:**
> After almost 24 hours with no drop wireless dropouts I think I can say installing the following backport modules fixes this problem, at least for me.

linux-backports-modules-2.6.31-15-generic (2.6.31-15.17)
linux-backports-modules-2.6.31-15-generic-pae (2.6.31-15.17)
linux-backports-modules-karmic (2.6.31.15.28)
linux-backports-modules-karmic-generic (2.6.31.15.28)
linux-backports-modules-wireless-karmic-generic-pae (2.6.31.15.28)
linux-image-2.6.31-15-generic-pae (2.6.31-15.50)

I tried this. It did not work!
I don't know what to do at this point... that server must be 24x7 connected to the internet. In that room I have no telephone cable to bring the modem there and connect directly using ethernet... and Ubuntu does not work with wireless, it's always disconnecting... moreover Canonical doesn't seem to be committed in solving the BUG (that comes from 9.10 ALPHA version). I even tried another workaround:
[http://muzehyun.blogspot.com/2009/04/workaround-for-wireless-disconnection.html](http://muzehyun.blogspot.com/2009/04/workaround-for-wireless-disconnection.html)
I'ts a script to identify disconnections and restart the network, but it doesn't work either: I need to manually unplug/re-plug the wifi-USB-dongle...
Any idea (exept reinstalling Windows and using Windows software?) :( :( :(
It' about ten year now I'm using Linux... never thought something like that would happen!!!

---

### Post by Majino on 2010-02-25
i've got the same problem, network manager disconnects and ask for the wep password many times... now it's 30minutes that is online, but previously it disconnects every 2-3 minutes. i've upgraded to network manager 0.8 (unless it show me 0.7.998)... my network has a wep password... i've also tried using wicd, but with that i couldn't connect at all. don't really know what to do, i'm new to linux, and i want to keep it, but with wireless on. anyway that's my system:

Wireless Card: Intel BG2200
Ubuntu 9.10
Network Manager 0.8 (0.7.998)

---

### Post by asbesto on 2010-02-25
Same problem here, eeepc 701. And I had this problem only since about 4 days ago!!! So, what have they broken in those 4 days? THIS

```

Log started: 2010-02-08  14:31:25
Selecting previously deselected package linux-image-2.6.28-18-generic.
Preparing to replace linux-restricted-modules-common 2.6.28-17.22 (using .../linux-restricted-modules-common_2.6.28-18.23_all.deb) ...
Preparing to replace linux-libc-dev 2.6.28-17.58 (using .../linux-libc-dev_2.6.28-18.59_i386.deb) ...
Preparing to replace linux-restricted-modules-generic 2.6.28.17.22 (using .../linux-restricted-modules-generic_2.6.28.18.23_i386.deb) ...

```

Maybe this new kernel is the real problem? I will try restarting with my old one and I will write here the result :(

This is what I have in logs:
```

[70693.324675] ath5k phy1: noise floor calibration timeout (2432MHz)
[70704.324622] ath5k phy1: noise floor calibration timeout (2432MHz)
[70712.585871] ath5k phy1: failed to wakeup the MAC Chip
[70712.585885] ath5k phy1: can't reset hardware (-5)
[70712.633442] ath5k phy1: failed to wakeup the MAC Chip
[70712.633457] ath5k phy1: can't reset hardware (-5)
[70712.693904] ath5k phy1: failed to wakeup the MAC Chip
[70712.693919] ath5k phy1: can't reset hardware (-5)
[70712.740309] ath5k phy1: failed to wakeup the MAC Chip
[70712.740325] ath5k phy1: can't reset hardware (-5)
[70712.799276] ath5k phy1: failed to wakeup the MAC Chip
[70726.324600] __ratelimit: 20 callbacks suppressed

```

I also opened another thread for this, now I discovered this. :confused:

---

### Post by flair-kun on 2010-03-16
Could anyone fix this issue?

I am facing the same issue with my new install of 9.10, My wireless connection (Intel 3945 ABG) keeps getting disconnected every 5 mins, like others have said i think its when multiple tabs are opened. Tried installing wicd, that doesn't work.

---

### Post by euriconeto on 2010-03-22
Hi All,

I have a similar problem. And a few others too... After completely installing karmic on a HP dv6 2120tx I noticed a few bugs.

1- Wireless doesn't work (the network manager only displays "enable networking" but not "enable wireless). I get no signal at all.
2- My mobile key (a Huawei 3 mobilebroadband from Australia) is recognised, but the appled does not allow me to connect to it.
3- The speakers do not stop working when I plug my headphones.
4- Speakers are doing a weird noise when I turn off the laptop
5- The screen gets buggered when turning off as well (comes back nicely though)

If you know how to help me or need more information in order to help, please give me a step by step on how to get the info you need from the terminal, as I don't know yet how to run these things.

Thanks!
Eurico

---

### Post by chili555 on 2010-03-22
> **euriconeto said:**
> Hi All,

I have a similar problem. And a few others too... After completely installing karmic on a HP dv6 2120tx I noticed a few bugs.

1- Wireless doesn't work (the network manager only displays "enable networking" but not "enable wireless). I get no signal at all.
2- My mobile key (a Huawei 3 mobilebroadband from Australia) is recognised, but the appled does not allow me to connect to it.
3- The speakers do not stop working when I plug my headphones.
4- Speakers are doing a weird noise when I turn off the laptop
5- The screen gets buggered when turning off as well (comes back nicely though)

If you know how to help me or need more information in order to help, please give me a step by step on how to get the info you need from the terminal, as I don't know yet how to run these things.

Thanks!
Eurico

As requested elsewhere, please start a new thread.

---

### Post by kanimani on 2010-03-22
I have the same issue but it drops more frequently, it connects and has full signal(100%) after a few seconds it has about 50% and then a few seconds later it goes down and reconnects which is realy annoying.. but it seams it not a problem only of ubuntu iam facing the same problem on fedora but not on archlinux a fix would be nice

btw in the new beta its still the same


Edit:
Wicd doesn't find any wireless network at all..
i have a m1330 with Intel wireless chipset 4965agn

---

### Post by idrinkwhisky on 2010-05-26
I had a similar problem on both my linux as well as my windows machine. What solved it for me was doing the following:

1) go inside the routersoftware (in your webbrowser it should be something like 192.168.1.1). Then change the default channel. 

2) change wpa2 key to wpa. (you could also try no key)
For some reason my linux does not like wpa2.

hope this helps

---

### Post by fuyao on 2010-07-23
me too but i have my own workaround

i also have a mac mini, i used a LAN wire and networked my xubuntu PC and my Mac, my PC will then share the internet with my Mac

my problem is different, i connect on wireless for a while, then suddenly disconnects and i have to restart my computer for the wireless to work again, kinda worst then you guys actually because it seemed that you guys' wireless disconnects and reconnects at a fixed interval, i have to restart my whole system for the thing to work again and my laptop is very slow at rebooting

---

### Post by geoffsn on 2010-08-07
> **Marc Higgins said:**
> After almost 24 hours with no drop wireless dropouts I think I can say installing the following backport modules fixes this problem, at least for me.

linux-backports-modules-2.6.31-15-generic (2.6.31-15.17)
linux-backports-modules-2.6.31-15-generic-pae (2.6.31-15.17)
linux-backports-modules-karmic (2.6.31.15.28)
linux-backports-modules-karmic-generic (2.6.31.15.28)
linux-backports-modules-wireless-karmic-generic-pae (2.6.31.15.28)
linux-image-2.6.31-15-generic-pae (2.6.31-15.50)

Still may be too early to say (I've only been online for 30 minutes since the fix), but after installing the new versions of these backport modules ( linux-backports-modules-wireless-lucid-generic-pae  and  linux-backport-modules-wireless-2.6.32-24-generic-pae ) I haven't dropped once.  Before I would lose signal every 2-5 minutes.  I'll update in a couple days to follow up.

---

### Post by geoffsn on 2010-08-08
> **geoffsn said:**
> Still may be too early to say (I've only been online for 30 minutes since the fix), but after installing the new versions of these backport modules ( linux-backports-modules-wireless-lucid-generic-pae  and  linux-backport-modules-wireless-2.6.32-24-generic-pae ) I haven't dropped once.  Before I would lose signal every 2-5 minutes.  I'll update in a couple days to follow up.
Yeah, I spoke too soon.  I still had the problem.  I did solve my problem though.  I had attempted to install a network printer a few days earlier and was unsuccessful.  However, I hadn't deleted the nonfunctional printer from the system.  After I deleted the network printer I no longer had a problem with my wifi disconnecting.  Hopefully this helps someone.

---

### Post by Gene_s on 2010-08-08
I have a eeePc HA1005HAG; installed Ubuntu 9.10 from USB stick. Here is the problem,

No wired connection. do not really care about this one.

No wireless connection; It will detect my wireless router (2WIRE705) and says it is "connected" but no signal bars shows in the upper right hand banner.

here is the output:

gene@netbook:~$ iwconfig


lo        no wireless extensions.



eth0      no wireless extensions.



wmaster0  no wireless extensions.



wlan0     IEEE 802.11bgn  ESSID:"2WIRE705"  

          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   

          Tx-Power=20 dBm   

          Retry  long limit:7   RTS thr:off   Fragment thr:off

          Power Management:on

          Link Quality:0  Signal level:0  Noise level:0

          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0

          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


does it have to do with the "no associated point"?

thanks, Gene

---

