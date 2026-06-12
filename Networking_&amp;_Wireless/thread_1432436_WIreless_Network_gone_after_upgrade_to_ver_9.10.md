---
title: "WIreless Network gone after upgrade to ver 9.10"
date: 2010-03-17
forum: Networking &amp; Wireless
---

### Post by luisfm on 2010-03-17
I had Ubuntu 8.10 running fine (my wireless card is Linksys WPC54GS) and as a matter of fact I downloaded all the upgrades using it. However when I rebooted, I lost the wireless connection. When I click on Wireless network Drivers it shows the lsbcmnds and says: Hardware Present: Yes but when I click on the Configure Network button, I get "Could Not Find Network Configuration Tool". What I am missing here?. THe network Icon shows my home wireless network, but it won't connect to it. My wireless network uses WPA-PSK Security. Thanks in advance for the input

---

### Post by chili555 on 2010-03-17
> THe network Icon shows my home wireless network, but it won't connect to it. My wireless network uses WPA-PSK Security. Are you prompted for the WPA-PSK key or password? Key will not work in the password drop-down and vice-versa.

---

### Post by luisfm on 2010-03-18
Well, no it does not ask for it. However, I tried editing the Network Connection and first I see WPA WPA2 on the security tab where it has a field for Password. I input the password set  for the router (Netgear WNR 3500), but still does not connect. As mentioned before, before upgrading to 9.10 I had 8.10 (or close to it, the last version of 2008) and it was working at that point. I figure the upgrade removed some driver that I'm not aware of or something like that. I'm at a loss here. I'm not well versed on Linux (a fault of my own, I had spent most of my time trying to get better at Java and Algorithms theory). Your help is highly appreciated.

---

### Post by chili555 on 2010-03-18
Let's take a look at:```
ndiswrapper -l
iwconfig
rfkill list
lspcmcia -v
```Thanks.

---

### Post by luisfm on 2010-03-18
One more thing: when I go to the System -> Administration -> WIndows Wireless Drivers I get a screen that says "Unable to see if Hardware is present" I press OK and I get the Wireless Network Drivers screen that shows "lsbcmnds Hardware Present: Yes". I click on configure Network button and get the message "Could not find a network configuration tool".

---

### Post by luisfm on 2010-03-18
Here's what I'm getting:


luis@luis-Unix-Monster:~$ ndiswrapper -l
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/blaklist, it will be ignored in a future release.
lsbcmnds : driver installed
	device (14E4:4318) present (alternate driver: ssb)
luis@luis-Unix-Monster:~$ ^C
luis@luis-Unix-Monster:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:25 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

luis@luis-Unix-Monster:~$ rfkill list
luis@luis-Unix-Monster:~$ lspcmcia -v
Socket 0 Bridge:   	[yenta_cardbus] 	(bus ID: 0000:02:05.0)
	Configuration:	state: on	ready: unknown
Socket 1 Bridge:   	[yenta_cardbus] 	(bus ID: 0000:02:05.1)
	Configuration:	state: on	ready: unknown
			Voltage: 3.3V Vcc: 3.3V Vpp: 3.3V
  CardBus card -- see "lspci" for more information

---

### Post by chili555 on 2010-03-18
> All config files need .conf: /etc/modprobe.d/blaklist, it will be ignored in a future release.Uh oh! I think your tutorial meant for it to be 'bla[COLOR="Red"]c[/COLOR]klist.' Let's fix it up:```
sudo mv /etc/modprobe.d/blaklist /etc/modprobe.d/blacklist.conf
sudo mv /etc/modprobe.d/ndiswrapper /etc/modprobe.d/ndiswrapper.conf
```Reboot with the ethernet cable detached and let's see if we have improved.

---

### Post by luisfm on 2010-03-18
Nothing. I still can't connect to the wireless net. THe only change I see is that when I open System -> Administration -> WIndows Wireless Drivers I don't get the screen "Unable to see if Hardware is present" but when I  click on configure Network button still get the message "Could not find a network configuration tool".

---

### Post by bkratz on 2010-03-18
> **luisfm said:**
> Nothing. I still can't connect to the wireless net. THe only change I see is that when I open System -> Administration -> WIndows Wireless Drivers I don't get the screen "Unable to see if Hardware is present" but when I  click on configure Network button still get the message "Could not find a network configuration tool".


Sorry to interrupt (since you already have the best help anywhere going on) but in you earlier posting it said "

device (14E4:431 present (alternate driver: ssb)

"  and the last digit was obscured by a smiley face ( you can turn those off in postings) anyway the first part of the number indicates a Broadcom device--would the last part be either 4318 or 4310,11?  If so, you might be able to get by without ndiswrapper at all.  ( I never did get ndiswrapper to work with WPA2 in 9.10 ( until I changed kernels)) but that is another story. There are threads regarding this like

[http://ubuntuforums.org/showthread.php?t=1343847](http://ubuntuforums.org/showthread.php?t=1343847).

---

### Post by chili555 on 2010-03-18
Are you able to click on the Network Manager icon and see networks? Please see attached.

If you don't see this icon, right-click the panel and add 'Notification Area.'

---

### Post by luisfm on 2010-03-18
Sorry about the smiley face. So you suggest that I run:

sudo apt-get install linux-headers-$(uname -r) dh-make fakeroot gcc-4.4 build-essential

to fix the ndiswrapper problem?

Here's the screen without the smiley face:

luis@luis-Unix-Monster:~$ ndiswrapper -l
lsbcmnds : driver installed
	device (14E4:4318) present (alternate driver: ssb)
luis@luis-Unix-Monster:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:25 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

luis@luis-Unix-Monster:~$ lspcmcia -v
Socket 0 Bridge:   	[yenta_cardbus] 	(bus ID: 0000:02:05.0)
	Configuration:	state: on	ready: unknown
Socket 1 Bridge:   	[yenta_cardbus] 	(bus ID: 0000:02:05.1)
	Configuration:	state: on	ready: unknown
			Voltage: 3.3V Vcc: 3.3V Vpp: 3.3V
  CardBus card -- see "lspci" for more information
luis@luis-Unix-Monster:~$ rfkill list
luis@luis-Unix-Monster:~$ lspcmcia -v
Socket 0 Bridge:   	[yenta_cardbus] 	(bus ID: 0000:02:05.0)
	Configuration:	state: on	ready: unknown
Socket 1 Bridge:   	[yenta_cardbus] 	(bus ID: 0000:02:05.1)
	Configuration:	state: on	ready: unknown
			Voltage: 3.3V Vcc: 3.3V Vpp: 3.3V
  CardBus card -- see "lspci" for more information
luis@luis-Unix-Monster:~$

---

### Post by luisfm on 2010-03-18
Yes. I'm able to see the icons similar to your screen. I don't know how to copy the screen to show you but I do see my wireless network in there with the bars at full since right now I'm next to the router (tethered to it).

---

### Post by bkratz on 2010-03-18
> **luisfm said:**
> Sorry about the smiley face. So you suggest that I run:

sudo apt-get install linux-headers-$(uname -r) dh-make fakeroot gcc-4.4 build-essential

to fix the ndiswrapper problem?




No, that doesn't always work ( believe me!).  Broadcom devices are way better supported now than last time you used them ( I think you said 8.10 but I'm not sure, and to lazy to look back!). I would suggest following Chili555 advice ( always very good) and only change if you reach a dead end, because it would require removing ndiswrapper and probably blacklisting some stuff.  anyway, if needed here is the recommended documentation, look for your card and the section labeled " ubuntu/Debian ".

[http://linuxwireless.org/en/users/Drivers/b43](http://linuxwireless.org/en/users/Drivers/b43)

---

### Post by chili555 on 2010-03-18
> I do see my wireless network in there with the bars at full since right now I'm next to the router (tethered to it).Please detach the cable and try to connect.

---

### Post by luisfm on 2010-03-18
I did that. Nothing. Following the other thread suggested I found that issuing theis command:

sudo renice +19 $(pidof wpa_supplicant)

while attempting to connect to the wireless, it connects. But if I reboot, then the wireless connection does not work.

What gives?

---

### Post by bkratz on 2010-03-18
> **luisfm said:**
> I did that. Nothing. Following the other thread suggested I found that issuing theis command:

sudo renice +19 $(pidof wpa_supplicant)

while attempting to connect to the wireless, it connects. But if I reboot, then the wireless connection does not work.

What gives?

NO, I didn't suggest you do any of that! It was just for information, sorry I sent it.  Just follow Chili555 advice until and if a roadblock occurs!

---

### Post by luisfm on 2010-03-18
I have to take that back. It worked only once, and that was after I disconnected the wired network cable. It doesn't work from a fresh re-boot.

---

### Post by rahulshah on 2010-03-18
ubuntu has created a package of the restricted drivers and codecs that they do not ship with the OS. Please type,

# sudo aptitude install ubuntu-restricted-extras

if this doesn't work as is, try updating the repositories using 

#sudo aptitude update

and then try again. After doing so restart and it might just work... :)

---

### Post by chili555 on 2010-03-18
> # sudo aptitude install ubuntu-restricted-extrasWill this help with a ndiswrapper install?

---

### Post by luisfm on 2010-03-18
I tried Rahulsha's suggestion. After each command I rebooted. Nothing. Still no wireless connection. What do you think Chili555? Should I do the ndiswrapper manual re-install?

---

### Post by chili555 on 2010-03-18
With the ethernet cable detached and when you see wireless networks in the icon, when you click on your network and ask it to connect, what happens? Does it try? After that, run: ```
dmesg | grep -e ndis -e wlan
```Attach the ethernet cable and post the result.> Should I do the ndiswrapper manual re-install? Not yet.

---

### Post by luisfm on 2010-03-18
I tried disconnecting the ethernet cable and then click on the wireless network icon for my network. It tries to connect but after a while it quits. Then I run the dmesg command as you instructed and got the following:

luis@luis-Unix-Monster:~$ dmesg | grep - ndis -e wlan
(standard input):[   23.525625] wlan0: ethernet device 00:14:bf:95:b4:22 using NDIS driver: lsbcmnds, version: 0x35a2600, NDIS version: 0x500, vendor: 'NDIS Network Adapter', 14E4:4318.5.conf
(standard input):[   23.525686] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
(standard input):[   23.563430] ADDRCONF(NETDEV_UP): wlan0: link is not ready
(standard input):[   64.065308] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
(standard input):[   74.672046] wlan0: no IPv6 routers present
grep: ndis: No such file or directory
luis@luis-Unix-Monster:~$

---

### Post by chili555 on 2010-03-18
> dmesg | grep -[COLOR="Red"]e[/COLOR] ndis -e wlanI would also like to see:```
sudo cat /var/log/syslog | grep -i network
```> (standard input):[ 64.065308] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
(standard input):[ 74.672046] wlan0: no IPv6 routers presentThat part looks very good; like its ready to connect.

---

### Post by luisfm on 2010-03-18
This is long. I don't think I got it all. Maybe I can generate a text file with the output...... here it goes:

Mar 18 15:11:39 luis-Unix-Monster NetworkManager: <info>  (eth0): device state change: 1 -> 2 (reason 2)
Mar 18 15:11:39 luis-Unix-Monster NetworkManager: <info>  (eth0): bringing up device.
Mar 18 15:11:39 luis-Unix-Monster NetworkManager: <info>  (eth0): preparing device.
Mar 18 15:11:39 luis-Unix-Monster NetworkManager: <info>  (eth0): deactivating device (reason: 2).
Mar 18 15:11:39 luis-Unix-Monster NetworkManager: Added default wired connection 'Auto eth0' for /sys/devices/pci0000:00/0000:00:1e.0/0000:02:08.0/net/eth0
Mar 18 15:11:39 luis-Unix-Monster NetworkManager: <info>  modem-manager is now available
Mar 18 15:11:39 luis-Unix-Monster NetworkManager: <WARN>  default_adapter_cb(): bluez error getting default adapter: The name org.bluez was not provided by any .service files
Mar 18 15:11:39 luis-Unix-Monster NetworkManager: <info>  Trying to start the supplicant...
Mar 18 15:11:40 luis-Unix-Monster kernel: [    2.074771] e100: Intel(R) PRO/100 Network Driver, 3.5.24-k2-NAPI
Mar 18 15:11:40 luis-Unix-Monster kernel: [    7.001369] type=1505 audit(1268939484.429:4): operation="profile_load" pid=370 name=/usr/lib/NetworkManager/nm-dhcp-client.action
Mar 18 15:11:40 luis-Unix-Monster kernel: [   23.108546] type=1505 audit(1268939500.537:14): operation="profile_replace" pid=945 name=/usr/lib/NetworkManager/nm-dhcp-client.action
Mar 18 15:11:40 luis-Unix-Monster kernel: [   23.525625] wlan0: ethernet device 00:14:bf:95:b4:22 using NDIS driver: lsbcmnds, version: 0x35a2600, NDIS version: 0x500, vendor: 'NDIS Network Adapter', 14E4:4318.5.conf
Mar 18 15:11:40 luis-Unix-Monster NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1e.0/0000:02:05.1/0000:07:00.0/net/wlan0, iface: wlan0)
Mar 18 15:11:40 luis-Unix-Monster NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1e.0/0000:02:05.1/0000:07:00.0/net/wlan0, iface: wlan0): no ifupdown configuration found.
Mar 18 15:11:40 luis-Unix-Monster NetworkManager: <info>  (wlan0): driver does not support SSID scans (scan_capa 0x00).
Mar 18 15:11:41 luis-Unix-Monster NetworkManager: <info>  (wlan0): new 802.11 WiFi device (driver: 'ndiswrapper')
Mar 18 15:11:41 luis-Unix-Monster NetworkManager: <info>  (wlan0): exported as /org/freedesktop/NetworkManager/Devices/1
Mar 18 15:11:41 luis-Unix-Monster NetworkManager: <info>  (wlan0): now managed
Mar 18 15:11:41 luis-Unix-Monster NetworkManager: <info>  (wlan0): device state change: 1 -> 2 (reason 2)
Mar 18 15:11:41 luis-Unix-Monster NetworkManager: <info>  (wlan0): bringing up device.
Mar 18 15:11:41 luis-Unix-Monster NetworkManager: <info>  (wlan0): preparing device.
Mar 18 15:11:41 luis-Unix-Monster NetworkManager: <info>  (wlan0): deactivating device (reason: 2).
Mar 18 15:11:41 luis-Unix-Monster NetworkManager: <info>  (wlan0): supplicant interface state:  starting -> ready
Mar 18 15:11:41 luis-Unix-Monster NetworkManager: <info>  (wlan0): device state change: 2 -> 3 (reason 42)
Mar 18 15:12:12 luis-Unix-Monster NetworkManager: <info>  Activation (wlan0) starting connection 'Auto Lucho's Net'
Mar 18 15:12:12 luis-Unix-Monster NetworkManager: <info>  (wlan0): device state change: 3 -> 4 (reason 0)
Mar 18 15:12:12 luis-Unix-Monster NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Mar 18 15:12:12 luis-Unix-Monster NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Mar 18 15:12:12 luis-Unix-Monster NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Mar 18 15:12:12 luis-Unix-Monster NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Mar 18 15:12:12 luis-Unix-Monster NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Mar 18 15:12:12 luis-Unix-Monster NetworkManager: <info>  (wlan0): device state change: 4 -> 5 (reason 0)
Mar 18 15:12:12 luis-Unix-Monster NetworkManager: <info>  Activation (wlan0/wireless): access point 'Auto Lucho's Net' has security, but secrets are required.
Mar 18 15:12:12 luis-Unix-Monster NetworkManager: <info>  (wlan0): device state change: 5 -> 6 (reason 0)
Mar 18 15:12:12 luis-Unix-Monster NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Mar 18 15:12:12 luis-Unix-Monster NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Mar 18 15:12:12 luis-Unix-Monster NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Mar 18 15:12:12 luis-Unix-Monster NetworkManager: <info>  (wlan0): device state change: 6 -> 4 (reason 0)
Mar 18 15:12:13 luis-Unix-Monster NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Mar 18 15:12:13 luis-Unix-Monster NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Mar 18 15:12:13 luis-Unix-Monster NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Mar 18 15:12:13 luis-Unix-Monster NetworkManager: <info>  (wlan0): device state change: 4 -> 5 (reason 0)
Mar 18 15:12:13 luis-Unix-Monster NetworkManager: <info>  Activation (wlan0/wireless): connection 'Auto Lucho's Net' has security, and secrets exist.  No new secrets needed.
Mar 18 15:12:13 luis-Unix-Monster NetworkManager: <info>  Config: added 'ssid' value 'Lucho's Net'
Mar 18 15:12:13 luis-Unix-Monster NetworkManager: <info>  Config: added 'scan_ssid' value '1'
Mar 18 15:12:13 luis-Unix-Monster NetworkManager: <info>  Config: added 'key_mgmt' value 'WPA-PSK'
Mar 18 15:12:13 luis-Unix-Monster NetworkManager: <info>  Config: added 'psk' value '<omitted>'
Mar 18 15:12:13 luis-Unix-Monster NetworkManager: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Mar 18 15:12:13 luis-Unix-Monster NetworkManager: nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Mar 18 15:12:13 luis-Unix-Monster NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Mar 18 15:12:13 luis-Unix-Monster NetworkManager: <info>  Config: set interface ap_scan to 1
Mar 18 15:12:13 luis-Unix-Monster NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> disconnected
Mar 18 15:12:16 luis-Unix-Monster NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Mar 18 15:12:21 luis-Unix-Monster NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Mar 18 15:12:21 luis-Unix-Monster NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> associated
Mar 18 15:12:21 luis-Unix-Monster NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> 4-way handshake
Mar 18 15:12:21 luis-Unix-Monster NetworkManager: <info>  (wlan0): supplicant connection state:  4-way handshake -> group handshake
Mar 18 15:12:21 luis-Unix-Monster NetworkManager: <info>  (wlan0): supplicant connection state:  group handshake -> completed
Mar 18 15:12:21 luis-Unix-Monster NetworkManager: <info>  Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'Lucho's Net'.
Mar 18 15:12:21 luis-Unix-Monster NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled.
Mar 18 15:12:21 luis-Unix-Monster NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) started...
Mar 18 15:12:21 luis-Unix-Monster NetworkManager: <info>  (wlan0): device state change: 5 -> 7 (reason 0)
Mar 18 15:12:21 luis-Unix-Monster NetworkManager: <info>  Activation (wlan0) Beginning DHCP transaction (timeout in 45 seconds)
Mar 18 15:12:21 luis-Unix-Monster NetworkManager: <info>  dhclient started with pid 1687
Mar 18 15:12:21 luis-Unix-Monster NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP6 Configure Get) scheduled...
Mar 18 15:12:21 luis-Unix-Monster NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
Mar 18 15:12:21 luis-Unix-Monster NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP6 Configure Get) started...
Mar 18 15:12:21 luis-Unix-Monster NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP6 Configure Get) complete.
Mar 18 15:12:21 luis-Unix-Monster NetworkManager: <info>  DHCP: device wlan0 state changed (null) -> preinit
Mar 18 15:12:29 luis-Unix-Monster NetworkManager: <info>  (wlan0): supplicant connection state:  completed -> associated
Mar 18 15:12:30 luis-Unix-Monster NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> 4-way handshake
Mar 18 15:12:30 luis-Unix-Monster NetworkManager: <info>  (wlan0): supplicant connection state:  4-way handshake -> group handshake
Mar 18 15:12:30 luis-Unix-Monster NetworkManager: <info>  (wlan0): supplicant connection state:  group handshake -> completed
Mar 18 15:12:38 luis-Unix-Monster NetworkManager: <info>  (wlan0): supplicant connection state:  completed -> associated
Mar 18 15:12:38 luis-Unix-Monster NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> 4-way handshake
Mar 18 15:12:38 luis-Unix-Monster NetworkManager: <info>  (wlan0): supplicant connection state:  4-way handshake -> group handshake
Mar 18 15:12:38 luis-Unix-Monster NetworkManager: <info>  (wlan0): supplicant connection state:  group handshake -> completed
Mar 18 15:12:47 luis-Unix-Monster NetworkManager: <info>  (wlan0): supplicant connection state:  completed -> associated
Mar 18 15:12:47 luis-Unix-Monster NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> 4-way handshake
Mar 18 15:12:47 luis-Unix-Monster NetworkManager: <info>  (wlan0): supplicant connection state:  4-way handshake -> group handshake
Mar 18 15:12:47 luis-Unix-Monster NetworkManager: <info>  (wlan0): supplicant connection state:  group handshake -> completed
Mar 18 15:12:55 luis-Unix-Monster NetworkManager: <info>  (wlan0): supplicant connection state:  completed -> associated
Mar 18 15:12:55 luis-Unix-Monster NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> 4-way handshake
Mar 18 15:12:55 luis-Unix-Monster NetworkManager: <info>  (wlan0): supplicant connection state:  4-way handshake -> group handshake
Mar 18 15:12:55 luis-Unix-Monster NetworkManager: <info>  (wlan0): supplicant connection state:  group handshake -> completed
Mar 18 15:13:04 luis-Unix-Monster NetworkManager: <info>  (wlan0): supplicant connection state:  completed -> associated
Mar 18 15:13:04 luis-Unix-Monster NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> 4-way handshake
Mar 18 15:13:04 luis-Unix-Monster NetworkManager: <info>  (wlan0): supplicant connection state:  4-way handshake -> group handshake
Mar 18 15:13:04 luis-Unix-Monster NetworkManager: <info>  (wlan0): supplicant connection state:  group handshake -> completed
Mar 18 15:13:07 luis-Unix-Monster NetworkManager: <info>  (wlan0): DHCP transaction took too long, stopping it.
Mar 18 15:13:07 luis-Unix-Monster NetworkManager: <info>  (wlan0): canceled DHCP transaction, dhcp client pid 1687
Mar 18 15:13:07 luis-Unix-Monster NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP4 Configure Timeout) scheduled...
Mar 18 15:13:07 luis-Unix-Monster NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP4 Configure Timeout) started...
Mar 18 15:13:07 luis-Unix-Monster NetworkManager: <info>  (wlan0): device state change: 7 -> 9 (reason 5)
Mar 18 15:13:07 luis-Unix-Monster NetworkManager: <info>  Activation (wlan0) failed for access point (Lucho's Net)
Mar 18 15:13:07 luis-Unix-Monster NetworkManager: <info>  Marking connection 'Auto Lucho's Net' invalid.
Mar 18 15:13:07 luis-Unix-Monster NetworkManager: <info>  Activation (wlan0) failed.
Mar 18 15:13:07 luis-Unix-Monster NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP4 Configure Timeout) complete.
Mar 18 15:13:07 luis-Unix-Monster NetworkManager: <info>  (wlan0): device state change: 9 -> 3 (reason 0)
Mar 18 15:13:07 luis-Unix-Monster NetworkManager: <info>  (wlan0): deactivating device (reason: 0).
Mar 18 15:13:16 luis-Unix-Monster NetworkManager: <info>  (eth0): carrier now ON (device state 2)
Mar 18 15:13:16 luis-Unix-Monster NetworkManager: <info>  (eth0): device state change: 2 -> 3 (reason 40)
Mar 18 15:13:16 luis-Unix-Monster NetworkManager: <info>  Activation (eth0) starting connection 'Auto eth0'
Mar 18 15:13:16 luis-Unix-Monster NetworkManager: <info>  (eth0): device state change: 3 -> 4 (reason 0)
Mar 18 15:13:16 luis-Unix-Monster NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled...
Mar 18 15:13:16 luis-Unix-Monster NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) started...
Mar 18 15:13:16 luis-Unix-Monster NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) scheduled...
Mar 18 15:13:16 luis-Unix-Monster NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) complete.
Mar 18 15:13:16 luis-Unix-Monster NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) starting...
Mar 18 15:13:16 luis-Unix-Monster NetworkManager: <info>  (eth0): device state change: 4 -> 5 (reason 0)
Mar 18 15:13:16 luis-Unix-Monster NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) successful.
Mar 18 15:13:16 luis-Unix-Monster NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled.
Mar 18 15:13:16 luis-Unix-Monster NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) complete.
Mar 18 15:13:16 luis-Unix-Monster NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) started...
Mar 18 15:13:16 luis-Unix-Monster NetworkManager: <info>  (eth0): device state change: 5 -> 7 (reason 0)
Mar 18 15:13:16 luis-Unix-Monster NetworkManager: <info>  Activation (eth0) Beginning DHCP transaction (timeout in 45 seconds)
Mar 18 15:13:16 luis-Unix-Monster NetworkManager: <info>  dhclient started with pid 1740
Mar 18 15:13:16 luis-Unix-Monster NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP6 Configure Get) scheduled...
Mar 18 15:13:16 luis-Unix-Monster NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) complete.
Mar 18 15:13:16 luis-Unix-Monster NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP6 Configure Get) started...
Mar 18 15:13:16 luis-Unix-Monster NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP6 Configure Get) complete.
Mar 18 15:13:16 luis-Unix-Monster NetworkManager: <info>  DHCP: device eth0 state changed (null) -> preinit
Mar 18 15:13:17 luis-Unix-Monster NetworkManager: <info>  DHCP: device eth0 state changed preinit -> bound
Mar 18 15:13:17 luis-Unix-Monster NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Get) scheduled...
Mar 18 15:13:17 luis-Unix-Monster NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Get) started...
Mar 18 15:13:17 luis-Unix-Monster NetworkManager: <info>    address 192.168.1.4
Mar 18 15:13:17 luis-Unix-Monster NetworkManager: <info>    prefix 24 (255.255.255.0)
Mar 18 15:13:17 luis-Unix-Monster NetworkManager: <info>    gateway 192.168.1.1
Mar 18 15:13:17 luis-Unix-Monster NetworkManager: <info>    nameserver '192.168.1.1'
Mar 18 15:13:17 luis-Unix-Monster NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) scheduled...
Mar 18 15:13:17 luis-Unix-Monster NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Get) complete.
Mar 18 15:13:17 luis-Unix-Monster NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) started...
Mar 18 15:13:18 luis-Unix-Monster NetworkManager: <info>  (eth0): device state change: 7 -> 8 (reason 0)
Mar 18 15:13:18 luis-Unix-Monster NetworkManager: <info>  Policy set 'Auto eth0' (eth0) as default for routing and DNS.
Mar 18 15:13:18 luis-Unix-Monster NetworkManager: <info>  Activation (eth0) successful, device activated.
Mar 18 15:13:18 luis-Unix-Monster NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) complete.
Mar 18 15:13:52 luis-Unix-Monster NetworkManager: <info>  (eth0): carrier now OFF (device state 8, deferring action for 4 seconds)
Mar 18 15:13:56 luis-Unix-Monster NetworkManager: <info>  (eth0): device state change: 8 -> 2 (reason 40)
Mar 18 15:13:56 luis-Unix-Monster NetworkManager: <info>  (eth0): deactivating device (reason: 40).
Mar 18 15:13:56 luis-Unix-Monster NetworkManager: <info>  (eth0): canceled DHCP transaction, dhcp client pid 1740
Mar 18 15:13:56 luis-Unix-Monster NetworkManager: <WARN>  check_one_route(): (eth0) error -34 returned from rtnl_route_del(): Sucess#012
Mar 18 15:13:59 luis-Unix-Monster NetworkManager: <info>  Activation (wlan0) starting connection 'Auto Lucho's Net'
Mar 18 15:13:59 luis-Unix-Monster NetworkManager: <info>  (wlan0): device state change: 3 -> 4 (reason 0)
Mar 18 15:13:59 luis-Unix-Monster NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Mar 18 15:13:59 luis-Unix-Monster NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Mar 18 15:13:59 luis-Unix-Monster NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Mar 18 15:13:59 luis-Unix-Monster NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Mar 18 15:13:59 luis-Unix-Monster NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Mar 18 15:13:59 luis-Unix-Monster NetworkManager: <info>  (wlan0): device state change: 4 -> 5 (reason 0)
Mar 18 15:13:59 luis-Unix-Monster NetworkManager: <info>  Activation (wlan0/wireless): access point 'Auto Lucho's Net' has security, but secrets are required.
Mar 18 15:13:59 luis-Unix-Monster NetworkManager: <info>  (wlan0): device state change: 5 -> 6 (reason 0)
Mar 18 15:13:59 luis-Unix-Monster NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Mar 18 15:13:59 luis-Unix-Monster NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Mar 18 15:13:59 luis-Unix-Monster NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Mar 18 15:13:59 luis-Unix-Monster NetworkManager: <info>  (wlan0): device state change: 6 -> 4 (reason 0)
Mar 18 15:13:59 luis-Unix-Monster NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Mar 18 15:13:59 luis-Unix-Monster NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Mar 18 15:13:59 luis-Unix-Monster NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Mar 18 15:13:59 luis-Unix-Monster NetworkManager: <info>  (wlan0): device state change: 4 -> 5 (reason 0)
Mar 18 15:13:59 luis-Unix-Monster NetworkManager: <info>  Activation (wlan0/wireless): connection 'Auto Lucho's Net' has security, and secrets exist.  No new secrets needed.
Mar 18 15:13:59 luis-Unix-Monster NetworkManager: <info>  Config: added 'ssid' value 'Lucho's Net'
Mar 18 15:13:59 luis-Unix-Monster NetworkManager: <info>  Config: added 'scan_ssid' value '1'
Mar 18 15:13:59 luis-Unix-Monster NetworkManager: <info>  Config: added 'key_mgmt' value 'WPA-PSK'
Mar 18 15:13:59 luis-Unix-Monster NetworkManager: <info>  Config: added 'psk' value '<omitted>'
Mar 18 15:13:59 luis-Unix-Monster NetworkManager: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Mar 18 15:13:59 luis-Unix-Monster NetworkManager: nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Mar 18 15:13:59 luis-Unix-Monster NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Mar 18 15:13:59 luis-Unix-Monster NetworkManager: <info>  Config: set interface ap_scan to 1
Mar 18 15:13:59 luis-Unix-Monster NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> disconnected
Mar 18 15:13:59 luis-Unix-Monster NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Mar 18 15:14:04 luis-Unix-Monster NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Mar 18 15:14:05 luis-Unix-Monster NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> associated
Mar 18 15:14:05 luis-Unix-Monster NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> 4-way handshake
Mar 18 15:14:05 luis-Unix-Monster NetworkManager: <info>  (wlan0): supplicant connection state:  4-way handshake -> group handshake
Mar 18 15:14:05 luis-Unix-Monster NetworkManager: <info>  (wlan0): supplicant connection state:  group handshake -> completed
Mar 18 15:14:05 luis-Unix-Monster NetworkManager: <info>  Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'Lucho's Net'.
Mar 18 15:14:05 luis-Unix-Monster NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled.
Mar 18 15:14:05 luis-Unix-Monster NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) started...
Mar 18 15:14:05 luis-Unix-Monster NetworkManager: <info>  (wlan0): device state change: 5 -> 7 (reason 0)
Mar 18 15:14:05 luis-Unix-Monster NetworkManager: <info>  Activation (wlan0) Beginning DHCP transaction (timeout in 45 seconds)
Mar 18 15:14:05 luis-Unix-Monster NetworkManager: <info>  dhclient started with pid 1855
Mar 18 15:14:05 luis-Unix-Monster NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP6 Configure Get) scheduled...
Mar 18 15:14:05 luis-Unix-Monster NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
Mar 18 15:14:05 luis-Unix-Monster NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP6 Configure Get) started...
Mar 18 15:14:05 luis-Unix-Monster NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP6 Configure Get) complete.
Mar 18 15:14:05 luis-Unix-Monster NetworkManager: <info>  DHCP: device wlan0 state changed normal exit -> preinit
Mar 18 15:14:13 luis-Unix-Monster NetworkManager: <info>  (wlan0): supplicant connection state:  completed -> associated
Mar 18 15:14:13 luis-Unix-Monster NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> 4-way handshake
Mar 18 15:14:13 luis-Unix-Monster NetworkManager: <info>  (wlan0): supplicant connection state:  4-way handshake -> group handshake
Mar 18 15:14:13 luis-Unix-Monster NetworkManager: <info>  (wlan0): supplicant connection state:  group handshake -> completed
Mar 18 15:14:22 luis-Unix-Monster NetworkManager: <info>  (wlan0): supplicant connection state:  completed -> associated
Mar 18 15:14:22 luis-Unix-Monster NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> 4-way handshake
Mar 18 15:14:22 luis-Unix-Monster NetworkManager: <info>  (wlan0): supplicant connection state:  4-way handshake -> group handshake
Mar 18 15:14:22 luis-Unix-Monster NetworkManager: <info>  (wlan0): supplicant connection state:  group handshake -> completed
Mar 18 15:14:30 luis-Unix-Monster NetworkManager: <info>  (wlan0): supplicant connection state:  completed -> associated
Mar 18 15:14:30 luis-Unix-Monster NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> 4-way handshake
Mar 18 15:14:30 luis-Unix-Monster NetworkManager: <info>  (wlan0): supplicant connection state:  4-way handshake -> group handshake
Mar 18 15:14:30 luis-Unix-Monster NetworkManager: <info>  (wlan0): supplicant connection state:  group handshake -> completed
Mar 18 15:14:39 luis-Unix-Monster NetworkManager: <info>  (wlan0): supplicant connection state:  completed -> associated
Mar 18 15:14:39 luis-Unix-Monster NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> 4-way handshake
Mar 18 15:14:39 luis-Unix-Monster NetworkManager: <info>  (wlan0): supplicant connection state:  4-way handshake -> group handshake
Mar 18 15:14:39 luis-Unix-Monster NetworkManager: <info>  (wlan0): supplicant connection state:  group handshake -> completed
Mar 18 15:14:47 luis-Unix-Monster NetworkManager: <info>  (wlan0): supplicant connection state:  completed -> associated
Mar 18 15:14:47 luis-Unix-Monster NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> 4-way handshake
Mar 18 15:14:47 luis-Unix-Monster NetworkManager: <info>  (wlan0): supplicant connection state:  4-way handshake -> group handshake
Mar 18 15:14:47 luis-Unix-Monster NetworkManager: <info>  (wlan0): supplicant connection state:  group handshake -> completed
Mar 18 15:14:51 luis-Unix-Monster NetworkManager: <info>  (wlan0): DHCP transaction took too long, stopping it.
Mar 18 15:14:51 luis-Unix-Monster NetworkManager: <info>  (wlan0): canceled DHCP transaction, dhcp client pid 1855
Mar 18 15:14:51 luis-Unix-Monster NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP4 Configure Timeout) scheduled...
Mar 18 15:14:51 luis-Unix-Monster NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP4 Configure Timeout) started...
Mar 18 15:14:51 luis-Unix-Monster NetworkManager: <info>  (wlan0): device state change: 7 -> 9 (reason 5)
Mar 18 15:14:51 luis-Unix-Monster NetworkManager: <info>  Activation (wlan0) failed for access point (Lucho's Net)
Mar 18 15:14:51 luis-Unix-Monster NetworkManager: <info>  Marking connection 'Auto Lucho's Net' invalid.
Mar 18 15:14:51 luis-Unix-Monster NetworkManager: <info>  Activation (wlan0) failed.
Mar 18 15:14:51 luis-Unix-Monster NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP4 Configure Timeout) complete.
Mar 18 15:14:51 luis-Unix-Monster NetworkManager: <info>  (wlan0): device state change: 9 -> 3 (reason 0)
Mar 18 15:14:51 luis-Unix-Monster NetworkManager: <info>  (wlan0): deactivating device (reason: 0).
Mar 18 15:15:26 luis-Unix-Monster NetworkManager: <info>  (eth0): carrier now ON (device state 2)
Mar 18 15:15:26 luis-Unix-Monster NetworkManager: <info>  (eth0): device state change: 2 -> 3 (reason 40)
Mar 18 15:15:26 luis-Unix-Monster NetworkManager: <info>  Activation (eth0) starting connection 'Auto eth0'
Mar 18 15:15:26 luis-Unix-Monster NetworkManager: <info>  (eth0): device state change: 3 -> 4 (reason 0)
Mar 18 15:15:26 luis-Unix-Monster NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled...
Mar 18 15:15:26 luis-Unix-Monster NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) started...
Mar 18 15:15:26 luis-Unix-Monster NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) scheduled...
Mar 18 15:15:26 luis-Unix-Monster NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) complete.
Mar 18 15:15:26 luis-Unix-Monster NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) starting...
Mar 18 15:15:26 luis-Unix-Monster NetworkManager: <info>  (eth0): device state change: 4 -> 5 (reason 0)
Mar 18 15:15:26 luis-Unix-Monster NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) successful.
Mar 18 15:15:26 luis-Unix-Monster NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled.
Mar 18 15:15:26 luis-Unix-Monster NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) complete.
Mar 18 15:15:26 luis-Unix-Monster NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) started...
Mar 18 15:15:26 luis-Unix-Monster NetworkManager: <info>  (eth0): device state change: 5 -> 7 (reason 0)
Mar 18 15:15:26 luis-Unix-Monster NetworkManager: <info>  Activation (eth0) Beginning DHCP transaction (timeout in 45 seconds)
Mar 18 15:15:26 luis-Unix-Monster NetworkManager: <info>  dhclient started with pid 1881
Mar 18 15:15:26 luis-Unix-Monster NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP6 Configure Get) scheduled...
Mar 18 15:15:26 luis-Unix-Monster NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) complete.
Mar 18 15:15:26 luis-Unix-Monster NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP6 Configure Get) started...
Mar 18 15:15:26 luis-Unix-Monster NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP6 Configure Get) complete.
Mar 18 15:15:26 luis-Unix-Monster NetworkManager: <info>  DHCP: device eth0 state changed normal exit -> preinit
Mar 18 15:15:28 luis-Unix-Monster NetworkManager: <info>  DHCP: device eth0 state changed preinit -> reboot
Mar 18 15:15:28 luis-Unix-Monster NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Get) scheduled...
Mar 18 15:15:28 luis-Unix-Monster NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Get) started...
Mar 18 15:15:28 luis-Unix-Monster NetworkManager: <info>    address 192.168.1.4
Mar 18 15:15:28 luis-Unix-Monster NetworkManager: <info>    prefix 24 (255.255.255.0)
Mar 18 15:15:28 luis-Unix-Monster NetworkManager: <info>    gateway 192.168.1.1
Mar 18 15:15:28 luis-Unix-Monster NetworkManager: <info>    nameserver '192.168.1.1'
Mar 18 15:15:28 luis-Unix-Monster NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) scheduled...
Mar 18 15:15:28 luis-Unix-Monster NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Get) complete.
Mar 18 15:15:28 luis-Unix-Monster NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) started...
Mar 18 15:15:29 luis-Unix-Monster NetworkManager: <info>  (eth0): device state change: 7 -> 8 (reason 0)
Mar 18 15:15:29 luis-Unix-Monster NetworkManager: <info>  Policy set 'Auto eth0' (eth0) as default for routing and DNS.
Mar 18 15:15:29 luis-Unix-Monster NetworkManager: <info>  Activation (eth0) successful, device activated.
Mar 18 15:15:29 luis-Unix-Monster NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) complete.
luis@luis-Unix-Monster:~$

---

### Post by luisfm on 2010-03-18
And this is what I get with the ethernet cable unplugged:


Mar 18 15:48:00 luis-Unix-Monster NetworkManager: <info>  DHCP: device eth0 state changed preinit -> reboot
Mar 18 15:48:00 luis-Unix-Monster NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Get) scheduled...
Mar 18 15:48:00 luis-Unix-Monster NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Get) started...
Mar 18 15:48:00 luis-Unix-Monster NetworkManager: <info>    address 192.168.1.4
Mar 18 15:48:00 luis-Unix-Monster NetworkManager: <info>    prefix 24 (255.255.255.0)
Mar 18 15:48:00 luis-Unix-Monster NetworkManager: <info>    gateway 192.168.1.1
Mar 18 15:48:00 luis-Unix-Monster NetworkManager: <info>    nameserver '192.168.1.1'
Mar 18 15:48:00 luis-Unix-Monster NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) scheduled...
Mar 18 15:48:00 luis-Unix-Monster NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Get) complete.
Mar 18 15:48:00 luis-Unix-Monster NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) started...
Mar 18 15:48:01 luis-Unix-Monster NetworkManager: <info>  (eth0): device state change: 7 -> 8 (reason 0)
Mar 18 15:48:01 luis-Unix-Monster NetworkManager: <info>  Policy set 'Auto eth0' (eth0) as default for routing and DNS.
Mar 18 15:48:01 luis-Unix-Monster NetworkManager: <info>  Activation (eth0) successful, device activated.
Mar 18 15:48:01 luis-Unix-Monster NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) complete.
Mar 18 15:48:52 luis-Unix-Monster NetworkManager: <info>  starting...
Mar 18 15:48:52 luis-Unix-Monster NetworkManager: <info>  Trying to start the modem-manager...
Mar 18 15:48:52 luis-Unix-Monster avahi-daemon[725]: Network interface enumeration completed.
Mar 18 15:48:52 luis-Unix-Monster NetworkManager:    SCPlugin-Ifupdown: init!
Mar 18 15:48:52 luis-Unix-Monster NetworkManager:    SCPlugin-Ifupdown: update_system_hostname
Mar 18 15:48:52 luis-Unix-Monster NetworkManager:    SCPluginIfupdown: management mode: unmanaged
Mar 18 15:48:52 luis-Unix-Monster NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1e.0/0000:02:08.0/net/eth0, iface: eth0)
Mar 18 15:48:52 luis-Unix-Monster NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1e.0/0000:02:08.0/net/eth0, iface: eth0): no ifupdown configuration found.
Mar 18 15:48:52 luis-Unix-Monster NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/lo, iface: lo)
Mar 18 15:48:52 luis-Unix-Monster NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration found.
Mar 18 15:48:52 luis-Unix-Monster NetworkManager:    SCPlugin-Ifupdown: end _init.
Mar 18 15:48:52 luis-Unix-Monster NetworkManager: Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
Mar 18 15:48:52 luis-Unix-Monster NetworkManager: Loaded plugin keyfile: (c) 2007 - 2008 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
Mar 18 15:48:52 luis-Unix-Monster NetworkManager: <info>  Wireless now enabled by radio killswitch
Mar 18 15:48:52 luis-Unix-Monster NetworkManager:    SCPlugin-Ifupdown: (144988912) ... get_connections.
Mar 18 15:48:52 luis-Unix-Monster NetworkManager:    SCPlugin-Ifupdown: (144988912) ... get_connections (managed=false): return empty list.
Mar 18 15:48:52 luis-Unix-Monster NetworkManager:    Ifupdown: get unmanaged devices count: 0
Mar 18 15:48:53 luis-Unix-Monster NetworkManager: <info>  (eth0): carrier is OFF
Mar 18 15:48:53 luis-Unix-Monster NetworkManager: <info>  (eth0): new Ethernet device (driver: 'e100')
Mar 18 15:48:53 luis-Unix-Monster NetworkManager: <info>  (eth0): exported as /org/freedesktop/NetworkManager/Devices/0
Mar 18 15:48:53 luis-Unix-Monster NetworkManager: <info>  (eth0): now managed
Mar 18 15:48:53 luis-Unix-Monster NetworkManager: <info>  (eth0): device state change: 1 -> 2 (reason 2)
Mar 18 15:48:53 luis-Unix-Monster NetworkManager: <info>  (eth0): bringing up device.
Mar 18 15:48:53 luis-Unix-Monster NetworkManager: <info>  (eth0): preparing device.
Mar 18 15:48:53 luis-Unix-Monster NetworkManager: <info>  (eth0): deactivating device (reason: 2).
Mar 18 15:48:53 luis-Unix-Monster NetworkManager: Added default wired connection 'Auto eth0' for /sys/devices/pci0000:00/0000:00:1e.0/0000:02:08.0/net/eth0
Mar 18 15:48:53 luis-Unix-Monster NetworkManager: <WARN>  default_adapter_cb(): bluez error getting default adapter: The name org.bluez was not provided by any .service files
Mar 18 15:48:53 luis-Unix-Monster NetworkManager: <info>  modem-manager is now available
Mar 18 15:48:53 luis-Unix-Monster NetworkManager: <info>  Trying to start the supplicant...
Mar 18 15:48:53 luis-Unix-Monster kernel: [    2.103211] e100: Intel(R) PRO/100 Network Driver, 3.5.24-k2-NAPI
Mar 18 15:48:53 luis-Unix-Monster kernel: [    7.163770] type=1505 audit(1268941717.583:4): operation="profile_load" pid=364 name=/usr/lib/NetworkManager/nm-dhcp-client.action
Mar 18 15:48:53 luis-Unix-Monster kernel: [   23.218507] type=1505 audit(1268941733.639:14): operation="profile_replace" pid=936 name=/usr/lib/NetworkManager/nm-dhcp-client.action
Mar 18 15:48:54 luis-Unix-Monster kernel: [   23.713617] wlan0: ethernet device 00:14:bf:95:b4:22 using NDIS driver: lsbcmnds, version: 0x35a2600, NDIS version: 0x500, vendor: 'NDIS Network Adapter', 14E4:4318.5.conf
Mar 18 15:48:54 luis-Unix-Monster NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1e.0/0000:02:05.1/0000:07:00.0/net/wlan0, iface: wlan0)
Mar 18 15:48:54 luis-Unix-Monster NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1e.0/0000:02:05.1/0000:07:00.0/net/wlan0, iface: wlan0): no ifupdown configuration found.
Mar 18 15:48:54 luis-Unix-Monster NetworkManager: <info>  (wlan0): driver does not support SSID scans (scan_capa 0x00).
Mar 18 15:48:54 luis-Unix-Monster NetworkManager: <info>  (wlan0): new 802.11 WiFi device (driver: 'ndiswrapper')
Mar 18 15:48:54 luis-Unix-Monster NetworkManager: <info>  (wlan0): exported as /org/freedesktop/NetworkManager/Devices/1
Mar 18 15:48:54 luis-Unix-Monster NetworkManager: <info>  (wlan0): now managed
Mar 18 15:48:54 luis-Unix-Monster NetworkManager: <info>  (wlan0): device state change: 1 -> 2 (reason 2)
Mar 18 15:48:54 luis-Unix-Monster NetworkManager: <info>  (wlan0): bringing up device.
Mar 18 15:48:54 luis-Unix-Monster NetworkManager: <info>  (wlan0): preparing device.
Mar 18 15:48:54 luis-Unix-Monster NetworkManager: <info>  (wlan0): deactivating device (reason: 2).
Mar 18 15:48:54 luis-Unix-Monster NetworkManager: <info>  (wlan0): supplicant interface state:  starting -> ready
Mar 18 15:48:54 luis-Unix-Monster NetworkManager: <info>  (wlan0): device state change: 2 -> 3 (reason 42)
Mar 18 15:48:55 luis-Unix-Monster NetworkManager: <info>  (eth0): carrier now ON (device state 2)
Mar 18 15:48:55 luis-Unix-Monster NetworkManager: <info>  (eth0): device state change: 2 -> 3 (reason 40)
Mar 18 15:48:55 luis-Unix-Monster NetworkManager: <info>  Activation (eth0) starting connection 'Auto eth0'
Mar 18 15:48:55 luis-Unix-Monster NetworkManager: <info>  (eth0): device state change: 3 -> 4 (reason 0)
Mar 18 15:48:55 luis-Unix-Monster NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled...
Mar 18 15:48:55 luis-Unix-Monster NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) started...
Mar 18 15:48:55 luis-Unix-Monster NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) scheduled...
Mar 18 15:48:55 luis-Unix-Monster NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) complete.
Mar 18 15:48:55 luis-Unix-Monster NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) starting...
Mar 18 15:48:55 luis-Unix-Monster NetworkManager: <info>  (eth0): device state change: 4 -> 5 (reason 0)
Mar 18 15:48:55 luis-Unix-Monster NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) successful.
Mar 18 15:48:55 luis-Unix-Monster NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled.
Mar 18 15:48:55 luis-Unix-Monster NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) complete.
Mar 18 15:48:55 luis-Unix-Monster NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) started...
Mar 18 15:48:55 luis-Unix-Monster NetworkManager: <info>  (eth0): device state change: 5 -> 7 (reason 0)
Mar 18 15:48:55 luis-Unix-Monster NetworkManager: <info>  Activation (eth0) Beginning DHCP transaction (timeout in 45 seconds)
Mar 18 15:48:55 luis-Unix-Monster NetworkManager: <info>  dhclient started with pid 1152
Mar 18 15:48:55 luis-Unix-Monster NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP6 Configure Get) scheduled...
Mar 18 15:48:55 luis-Unix-Monster NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) complete.
Mar 18 15:48:55 luis-Unix-Monster NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP6 Configure Get) started...
Mar 18 15:48:55 luis-Unix-Monster NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP6 Configure Get) complete.
Mar 18 15:48:55 luis-Unix-Monster NetworkManager: <info>  DHCP: device eth0 state changed (null) -> preinit
Mar 18 15:48:56 luis-Unix-Monster NetworkManager: <info>  DHCP: device eth0 state changed preinit -> bound
Mar 18 15:48:56 luis-Unix-Monster NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Get) scheduled...
Mar 18 15:48:56 luis-Unix-Monster NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Get) started...
Mar 18 15:48:56 luis-Unix-Monster NetworkManager: <info>    address 192.168.1.4
Mar 18 15:48:56 luis-Unix-Monster NetworkManager: <info>    prefix 24 (255.255.255.0)
Mar 18 15:48:56 luis-Unix-Monster NetworkManager: <info>    gateway 192.168.1.1
Mar 18 15:48:56 luis-Unix-Monster NetworkManager: <info>    nameserver '192.168.1.1'
Mar 18 15:48:56 luis-Unix-Monster NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) scheduled...
Mar 18 15:48:56 luis-Unix-Monster NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Get) complete.
Mar 18 15:48:56 luis-Unix-Monster NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) started...
Mar 18 15:48:57 luis-Unix-Monster NetworkManager: <info>  (eth0): device state change: 7 -> 8 (reason 0)
Mar 18 15:48:57 luis-Unix-Monster NetworkManager: <info>  Policy set 'Auto eth0' (eth0) as default for routing and DNS.
Mar 18 15:48:57 luis-Unix-Monster NetworkManager: <info>  Activation (eth0) successful, device activated.
Mar 18 15:48:57 luis-Unix-Monster NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) complete.
Mar 18 15:49:21 luis-Unix-Monster NetworkManager: <info>  Activation (wlan0) starting connection 'Auto Lucho's Net'
Mar 18 15:49:21 luis-Unix-Monster NetworkManager: <info>  (wlan0): device state change: 3 -> 4 (reason 0)
Mar 18 15:49:21 luis-Unix-Monster NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Mar 18 15:49:21 luis-Unix-Monster NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Mar 18 15:49:21 luis-Unix-Monster NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Mar 18 15:49:21 luis-Unix-Monster NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Mar 18 15:49:21 luis-Unix-Monster NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Mar 18 15:49:21 luis-Unix-Monster NetworkManager: <info>  (wlan0): device state change: 4 -> 5 (reason 0)
Mar 18 15:49:21 luis-Unix-Monster NetworkManager: <info>  Activation (wlan0/wireless): access point 'Auto Lucho's Net' has security, but secrets are required.
Mar 18 15:49:21 luis-Unix-Monster NetworkManager: <info>  (wlan0): device state change: 5 -> 6 (reason 0)
Mar 18 15:49:21 luis-Unix-Monster NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Mar 18 15:49:21 luis-Unix-Monster NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Mar 18 15:49:21 luis-Unix-Monster NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Mar 18 15:49:21 luis-Unix-Monster NetworkManager: <info>  (wlan0): device state change: 6 -> 4 (reason 0)
Mar 18 15:49:21 luis-Unix-Monster NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Mar 18 15:49:21 luis-Unix-Monster NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Mar 18 15:49:21 luis-Unix-Monster NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Mar 18 15:49:21 luis-Unix-Monster NetworkManager: <info>  (wlan0): device state change: 4 -> 5 (reason 0)
Mar 18 15:49:21 luis-Unix-Monster NetworkManager: <info>  Activation (wlan0/wireless): connection 'Auto Lucho's Net' has security, and secrets exist.  No new secrets needed.
Mar 18 15:49:21 luis-Unix-Monster NetworkManager: <info>  Config: added 'ssid' value 'Lucho's Net'
Mar 18 15:49:21 luis-Unix-Monster NetworkManager: <info>  Config: added 'scan_ssid' value '1'
Mar 18 15:49:21 luis-Unix-Monster NetworkManager: <info>  Config: added 'key_mgmt' value 'WPA-PSK'
Mar 18 15:49:21 luis-Unix-Monster NetworkManager: <info>  Config: added 'psk' value '<omitted>'
Mar 18 15:49:21 luis-Unix-Monster NetworkManager: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Mar 18 15:49:21 luis-Unix-Monster NetworkManager: nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Mar 18 15:49:21 luis-Unix-Monster NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Mar 18 15:49:21 luis-Unix-Monster NetworkManager: <info>  Config: set interface ap_scan to 1
Mar 18 15:49:21 luis-Unix-Monster NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> disconnected
Mar 18 15:49:21 luis-Unix-Monster NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Mar 18 15:49:26 luis-Unix-Monster NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Mar 18 15:49:27 luis-Unix-Monster NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> associated
Mar 18 15:49:27 luis-Unix-Monster NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> 4-way handshake
Mar 18 15:49:27 luis-Unix-Monster NetworkManager: <info>  (wlan0): supplicant connection state:  4-way handshake -> group handshake
Mar 18 15:49:27 luis-Unix-Monster NetworkManager: <info>  (wlan0): supplicant connection state:  group handshake -> completed
Mar 18 15:49:27 luis-Unix-Monster NetworkManager: <info>  Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'Lucho's Net'.
Mar 18 15:49:27 luis-Unix-Monster NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled.
Mar 18 15:49:27 luis-Unix-Monster NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) started...
Mar 18 15:49:27 luis-Unix-Monster NetworkManager: <info>  (wlan0): device state change: 5 -> 7 (reason 0)
Mar 18 15:49:27 luis-Unix-Monster NetworkManager: <info>  Activation (wlan0) Beginning DHCP transaction (timeout in 45 seconds)
Mar 18 15:49:27 luis-Unix-Monster NetworkManager: <info>  dhclient started with pid 1727
Mar 18 15:49:27 luis-Unix-Monster NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP6 Configure Get) scheduled...
Mar 18 15:49:27 luis-Unix-Monster NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
Mar 18 15:49:27 luis-Unix-Monster NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP6 Configure Get) started...
Mar 18 15:49:27 luis-Unix-Monster NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP6 Configure Get) complete.
Mar 18 15:49:27 luis-Unix-Monster NetworkManager: <info>  DHCP: device wlan0 state changed (null) -> preinit
Mar 18 15:49:35 luis-Unix-Monster NetworkManager: <info>  (wlan0): supplicant connection state:  completed -> associated
Mar 18 15:49:35 luis-Unix-Monster NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> 4-way handshake
Mar 18 15:49:35 luis-Unix-Monster NetworkManager: <info>  (wlan0): supplicant connection state:  4-way handshake -> group handshake
Mar 18 15:49:35 luis-Unix-Monster NetworkManager: <info>  (wlan0): supplicant connection state:  group handshake -> completed
Mar 18 15:49:44 luis-Unix-Monster NetworkManager: <info>  (wlan0): supplicant connection state:  completed -> associated
Mar 18 15:49:44 luis-Unix-Monster NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> 4-way handshake
Mar 18 15:49:44 luis-Unix-Monster NetworkManager: <info>  (wlan0): supplicant connection state:  4-way handshake -> group handshake
Mar 18 15:49:44 luis-Unix-Monster NetworkManager: <info>  (wlan0): supplicant connection state:  group handshake -> completed
Mar 18 15:49:52 luis-Unix-Monster NetworkManager: <info>  (wlan0): supplicant connection state:  completed -> associated
Mar 18 15:49:52 luis-Unix-Monster NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> 4-way handshake
Mar 18 15:49:52 luis-Unix-Monster NetworkManager: <info>  (wlan0): supplicant connection state:  4-way handshake -> group handshake
Mar 18 15:49:52 luis-Unix-Monster NetworkManager: <info>  (wlan0): supplicant connection state:  group handshake -> completed
Mar 18 15:50:01 luis-Unix-Monster NetworkManager: <info>  (wlan0): supplicant connection state:  completed -> associated
Mar 18 15:50:01 luis-Unix-Monster NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> 4-way handshake
Mar 18 15:50:01 luis-Unix-Monster NetworkManager: <info>  (wlan0): supplicant connection state:  4-way handshake -> group handshake
Mar 18 15:50:01 luis-Unix-Monster NetworkManager: <info>  (wlan0): supplicant connection state:  group handshake -> completed
Mar 18 15:50:09 luis-Unix-Monster NetworkManager: <info>  (wlan0): supplicant connection state:  completed -> associated
Mar 18 15:50:09 luis-Unix-Monster NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> 4-way handshake
Mar 18 15:50:09 luis-Unix-Monster NetworkManager: <info>  (wlan0): supplicant connection state:  4-way handshake -> group handshake
Mar 18 15:50:09 luis-Unix-Monster NetworkManager: <info>  (wlan0): supplicant connection state:  group handshake -> completed
Mar 18 15:50:12 luis-Unix-Monster NetworkManager: <info>  (wlan0): DHCP transaction took too long, stopping it.
Mar 18 15:50:12 luis-Unix-Monster NetworkManager: <info>  (wlan0): canceled DHCP transaction, dhcp client pid 1727
Mar 18 15:50:12 luis-Unix-Monster NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP4 Configure Timeout) scheduled...
Mar 18 15:50:12 luis-Unix-Monster NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP4 Configure Timeout) started...
Mar 18 15:50:12 luis-Unix-Monster NetworkManager: <info>  (wlan0): device state change: 7 -> 9 (reason 5)
Mar 18 15:50:12 luis-Unix-Monster NetworkManager: <info>  Activation (wlan0) failed for access point (Lucho's Net)
Mar 18 15:50:12 luis-Unix-Monster NetworkManager: <info>  Marking connection 'Auto Lucho's Net' invalid.
Mar 18 15:50:12 luis-Unix-Monster NetworkManager: <info>  Activation (wlan0) failed.
Mar 18 15:50:12 luis-Unix-Monster NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP4 Configure Timeout) complete.
Mar 18 15:50:12 luis-Unix-Monster NetworkManager: <info>  (wlan0): device state change: 9 -> 3 (reason 0)
Mar 18 15:50:12 luis-Unix-Monster NetworkManager: <info>  (wlan0): deactivating device (reason: 0).
Mar 18 15:50:12 luis-Unix-Monster NetworkManager: <info>  Policy set 'Auto eth0' (eth0) as default for routing and DNS.
Mar 18 15:50:23 luis-Unix-Monster NetworkManager: <info>  (eth0): carrier now OFF (device state 8, deferring action for 4 seconds)
Mar 18 15:50:27 luis-Unix-Monster NetworkManager: <info>  (eth0): device state change: 8 -> 2 (reason 40)
Mar 18 15:50:27 luis-Unix-Monster NetworkManager: <info>  (eth0): deactivating device (reason: 40).
Mar 18 15:50:27 luis-Unix-Monster NetworkManager: <info>  (eth0): canceled DHCP transaction, dhcp client pid 1152
Mar 18 15:50:27 luis-Unix-Monster NetworkManager: <WARN>  check_one_route(): (eth0) error -34 returned from rtnl_route_del(): Sucess#012
Mar 18 15:50:33 luis-Unix-Monster NetworkManager: <info>  Activation (wlan0) starting connection 'Auto Lucho's Net'
Mar 18 15:50:33 luis-Unix-Monster NetworkManager: <info>  (wlan0): device state change: 3 -> 4 (reason 0)
Mar 18 15:50:33 luis-Unix-Monster NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Mar 18 15:50:33 luis-Unix-Monster NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Mar 18 15:50:33 luis-Unix-Monster NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Mar 18 15:50:33 luis-Unix-Monster NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Mar 18 15:50:33 luis-Unix-Monster NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Mar 18 15:50:33 luis-Unix-Monster NetworkManager: <info>  (wlan0): device state change: 4 -> 5 (reason 0)
Mar 18 15:50:33 luis-Unix-Monster NetworkManager: <info>  Activation (wlan0/wireless): access point 'Auto Lucho's Net' has security, but secrets are required.
Mar 18 15:50:33 luis-Unix-Monster NetworkManager: <info>  (wlan0): device state change: 5 -> 6 (reason 0)
Mar 18 15:50:33 luis-Unix-Monster NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Mar 18 15:50:33 luis-Unix-Monster NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Mar 18 15:50:33 luis-Unix-Monster NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Mar 18 15:50:33 luis-Unix-Monster NetworkManager: <info>  (wlan0): device state change: 6 -> 4 (reason 0)
Mar 18 15:50:33 luis-Unix-Monster NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Mar 18 15:50:33 luis-Unix-Monster NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Mar 18 15:50:33 luis-Unix-Monster NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Mar 18 15:50:33 luis-Unix-Monster NetworkManager: <info>  (wlan0): device state change: 4 -> 5 (reason 0)
Mar 18 15:50:33 luis-Unix-Monster NetworkManager: <info>  Activation (wlan0/wireless): connection 'Auto Lucho's Net' has security, and secrets exist.  No new secrets needed.
Mar 18 15:50:33 luis-Unix-Monster NetworkManager: <info>  Config: added 'ssid' value 'Lucho's Net'
Mar 18 15:50:33 luis-Unix-Monster NetworkManager: <info>  Config: added 'scan_ssid' value '1'
Mar 18 15:50:33 luis-Unix-Monster NetworkManager: <info>  Config: added 'key_mgmt' value 'WPA-PSK'
Mar 18 15:50:33 luis-Unix-Monster NetworkManager: <info>  Config: added 'psk' value '<omitted>'
Mar 18 15:50:33 luis-Unix-Monster NetworkManager: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Mar 18 15:50:33 luis-Unix-Monster NetworkManager: nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Mar 18 15:50:33 luis-Unix-Monster NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Mar 18 15:50:33 luis-Unix-Monster NetworkManager: <info>  Config: set interface ap_scan to 1
Mar 18 15:50:33 luis-Unix-Monster NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> disconnected
Mar 18 15:50:33 luis-Unix-Monster NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Mar 18 15:50:38 luis-Unix-Monster NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Mar 18 15:50:38 luis-Unix-Monster NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> associated
Mar 18 15:50:38 luis-Unix-Monster NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> 4-way handshake
Mar 18 15:50:38 luis-Unix-Monster NetworkManager: <info>  (wlan0): supplicant connection state:  4-way handshake -> group handshake
Mar 18 15:50:38 luis-Unix-Monster NetworkManager: <info>  (wlan0): supplicant connection state:  group handshake -> completed
Mar 18 15:50:38 luis-Unix-Monster NetworkManager: <info>  Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'Lucho's Net'.
Mar 18 15:50:38 luis-Unix-Monster NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled.
Mar 18 15:50:38 luis-Unix-Monster NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) started...
Mar 18 15:50:38 luis-Unix-Monster NetworkManager: <info>  (wlan0): device state change: 5 -> 7 (reason 0)
Mar 18 15:50:38 luis-Unix-Monster NetworkManager: <info>  Activation (wlan0) Beginning DHCP transaction (timeout in 45 seconds)
Mar 18 15:50:38 luis-Unix-Monster NetworkManager: <info>  dhclient started with pid 1854
Mar 18 15:50:38 luis-Unix-Monster NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP6 Configure Get) scheduled...
Mar 18 15:50:38 luis-Unix-Monster NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
Mar 18 15:50:38 luis-Unix-Monster NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP6 Configure Get) started...
Mar 18 15:50:38 luis-Unix-Monster NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP6 Configure Get) complete.
Mar 18 15:50:38 luis-Unix-Monster NetworkManager: <info>  DHCP: device wlan0 state changed normal exit -> preinit
Mar 18 15:50:47 luis-Unix-Monster NetworkManager: <info>  (wlan0): supplicant connection state:  completed -> associated
Mar 18 15:50:47 luis-Unix-Monster NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> 4-way handshake
Mar 18 15:50:47 luis-Unix-Monster NetworkManager: <info>  (wlan0): supplicant connection state:  4-way handshake -> group handshake
Mar 18 15:50:47 luis-Unix-Monster NetworkManager: <info>  (wlan0): supplicant connection state:  group handshake -> completed
Mar 18 15:50:55 luis-Unix-Monster NetworkManager: <info>  (wlan0): supplicant connection state:  completed -> associated
Mar 18 15:50:55 luis-Unix-Monster NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> 4-way handshake
Mar 18 15:50:55 luis-Unix-Monster NetworkManager: <info>  (wlan0): supplicant connection state:  4-way handshake -> group handshake
Mar 18 15:50:55 luis-Unix-Monster NetworkManager: <info>  (wlan0): supplicant connection state:  group handshake -> completed
Mar 18 15:51:04 luis-Unix-Monster NetworkManager: <info>  (wlan0): supplicant connection state:  completed -> associated
Mar 18 15:51:04 luis-Unix-Monster NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> 4-way handshake
Mar 18 15:51:04 luis-Unix-Monster NetworkManager: <info>  (wlan0): supplicant connection state:  4-way handshake -> group handshake
Mar 18 15:51:04 luis-Unix-Monster NetworkManager: <info>  (wlan0): supplicant connection state:  group handshake -> completed
Mar 18 15:51:12 luis-Unix-Monster NetworkManager: <info>  (wlan0): supplicant connection state:  completed -> associated
Mar 18 15:51:12 luis-Unix-Monster NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> 4-way handshake
Mar 18 15:51:12 luis-Unix-Monster NetworkManager: <info>  (wlan0): supplicant connection state:  4-way handshake -> group handshake
Mar 18 15:51:12 luis-Unix-Monster NetworkManager: <info>  (wlan0): supplicant connection state:  group handshake -> completed
Mar 18 15:51:21 luis-Unix-Monster NetworkManager: <info>  (wlan0): supplicant connection state:  completed -> associated
Mar 18 15:51:21 luis-Unix-Monster NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> 4-way handshake
Mar 18 15:51:21 luis-Unix-Monster NetworkManager: <info>  (wlan0): supplicant connection state:  4-way handshake -> group handshake
Mar 18 15:51:21 luis-Unix-Monster NetworkManager: <info>  (wlan0): supplicant connection state:  group handshake -> completed
Mar 18 15:51:24 luis-Unix-Monster NetworkManager: <info>  (wlan0): DHCP transaction took too long, stopping it.
Mar 18 15:51:24 luis-Unix-Monster NetworkManager: <info>  (wlan0): canceled DHCP transaction, dhcp client pid 1854
Mar 18 15:51:24 luis-Unix-Monster NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP4 Configure Timeout) scheduled...
Mar 18 15:51:24 luis-Unix-Monster NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP4 Configure Timeout) started...
Mar 18 15:51:24 luis-Unix-Monster NetworkManager: <info>  (wlan0): device state change: 7 -> 9 (reason 5)
Mar 18 15:51:24 luis-Unix-Monster NetworkManager: <info>  Activation (wlan0) failed for access point (Lucho's Net)
Mar 18 15:51:24 luis-Unix-Monster NetworkManager: <info>  Marking connection 'Auto Lucho's Net' invalid.
Mar 18 15:51:24 luis-Unix-Monster NetworkManager: <info>  Activation (wlan0) failed.
Mar 18 15:51:24 luis-Unix-Monster NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP4 Configure Timeout) complete.
Mar 18 15:51:24 luis-Unix-Monster NetworkManager: <info>  (wlan0): device state change: 9 -> 3 (reason 0)
Mar 18 15:51:24 luis-Unix-Monster NetworkManager: <info>  (wlan0): deactivating device (reason: 0).
luis@luis-Unix-Monster:~$

---

### Post by chili555 on 2010-03-18
> Mar 18 15:13:59 luis-Unix-Monster NetworkManager: <info> Config: added 'ssid' value 'Lucho's Net'
Mar 18 15:13:59 luis-Unix-Monster NetworkManager: <info> Config: added 'scan_ssid' value '1'
Mar 18 15:13:59 luis-Unix-Monster NetworkManager: <info> Config: added 'key_mgmt' value '[COLOR="Red"]WPA-PSK[/COLOR]'
Mar 18 15:13:59 luis-Unix-Monster NetworkManager: <info> Config: added [COLOR="Red"]'psk' value '<omitted>'[/COLOR]This suggests to me that your network is encrypted with WPA-PSK and that Network Manager was not given a password or was given an incorrect password. Therefor the router declined to connect. Are you being prompted for a password?

You can insert it manually by right clicking the Network Manager icon and selecting Edit connections > select the wireless tab > highlight your network and click Edit. Select Wireless Security and add your password as shown attached. Make sure Connect Automatically is checked and try again.

---

### Post by luisfm on 2010-03-18
No it does not ask for it because it is already there in that field you highlighted. One thing though, remember that when the computer is connected with the ethernet cable, I issue this command:

luis@luis-Unix-Monster:~$ sudo renice +19 $(pidof wpa_supplicant)

then disconnect the ethernet, it sometimes, **not all the times**, connect using the wireless connection which suggests that the password is correct. The manual password processs you suggest was one of the first things I actually did (after I did the Ubuntu upgrade).

---

### Post by luisfm on 2010-03-18
Something I think is noteworthy is this. When I run the renice command as told before, this is what I get:

luis@luis-Unix-Monster:~$ sudo renice +19 $(pidof wpa_supplicant)
[sudo] password for luis: 
864: old priority 0, new priority 19
luis@luis-Unix-Monster:~$ What does it mean to change the priority from 0 to 19?

---

### Post by luisfm on 2010-03-18
FOr example: I  run the command to show you the results and after disconnecting the ethernet cable, about 30 seconds later it connected using the wireless. I don't run sudo renice +19 $(pidof wpa_supplicant), it won't connect.

---

### Post by chili555 on 2010-03-18
Let's try:```
sudo gedit /etc/wpa_supplicant/functions.sh
```Go down to line 262. Change this line:> start-stop-daemon --start --oknodo $DAEMON_VERBOSITY \To read like this:> start-stop-daemon --start [COLOR="Red"]--nicelevel 19[/COLOR] --oknodo $DAEMON_VERBOSITY \Proofread carefully, save and close gedit. Reboot. Post back with good news.

---

### Post by luisfm on 2010-03-18
No Luck. I does not connect. It show a message close to the nework connection icon but I can't read it. But that's another issue. Some things like that and for example the Cosmos Screen saver don't display correctly. But I'm not worried about that for now. Why couldn't leave good enough alone? Ver 8.10 was working like a dandy. We always have to have the latest and greatest.

---

### Post by luisfm on 2010-03-18
Oddly enough, that change on the functions.sh file does not affect the priority changes by the renice command. After rebooting and not connecting, I re-run the command: sudo renice +19 $(pidof wpa_supplicant)
And got the following output line: 
817: old priority 0, new priority 19

Which tells me that the priority was not affected by the change in that file

---

### Post by chili555 on 2010-03-18
> Which tells me that the priority was not affected by the change in that fileThen you might as well remove it. While you are in there, proofread it carefully to be sure it didn't work because you mistyped someting (been there, done that!).

Next, let's try:```
sudo gedit /etc/rc.local
```Add a new line so it looks like:```
# By default this script does nothing.

pre-up nice -19 wpa_supplicant

exit 0
```Proofread, save and close gedit and reboot.

I also saw this:[http://ubuntuforums.org/showthread.php?t=1343847&page=6](http://ubuntuforums.org/showthread.php?t=1343847&page=6)> After a couple of months using the 2.26.32-10 kernel mentioned earlier in the thread I booted today into the current 2.26.31-20 and ndiswrapper seems to work fine. I wonder if the problem has been finally fixed or it is just I am being lucky.If you have not upgraded yet to 2.26.31-20 (it came out just in the last day or so) you might try to do so.

You could also try the Lucid kernel; if it doesn't work, you can remove it in as few minutes as you installed it.

Last, I believe your device is just a Broadcom device. We might try to get it going without ndiswrapper.

I am certain that this is a problem with ndiswrapper and wpa_supplicant. I am connected with WPA and Network manager at this moment with no problem at all.

---

### Post by luisfm on 2010-03-19
I edited the file rc.local as suggested and rebooted. Nothing. However, I run again the command  sudo renice +19 $(pidof wpa_supplicant) and this time the computer connected through the Wireless. I haven't checked the Kernel version. I did the upgrade to 9.10 just a couple of days ago. So I assume I have the latest version. Let me check that and then I'll report back.

---

### Post by luisfm on 2010-03-19
As I suspected, I have the latest Kernel. See below:

luis@luis-Unix-Monster:~$ uname -r
2.6.31-20-generic

---

### Post by luisfm on 2010-03-19
> **chili555 said:**
> 

Last, I believe your device is just a Broadcom device. We might try to get it going without ndiswrapper.

I am certain that this is a problem with ndiswrapper and wpa_supplicant. I am connected with WPA and Network manager at this moment with no problem at all.

How do I go about it?

---

### Post by chili555 on 2010-03-19
Please remove the previous not-working entry in *rc.local* and substitute:```
renice +19 $(pidof wpa_supplicant) 
```I am sure there is someway to automate this; we just haven't yet worked out how.

---

### Post by luisfm on 2010-03-19
Changed the entry on rc.local as suggested, but the priority was unchanged. I had to run sudo renice +19 $(pidof wpa_supplicant) several times until the wireless came alive. Sometimes it does, sometimes it doesn't. I installed Ubuntu 9.10 on a newer laptop (different wireless modem) and it went without a hitch. Works as advertised. But this is my main Ubuntu box. Need to make sure it connects all the time. Your help is greatly appreciated.

---

### Post by chili555 on 2010-03-20
> $ ndiswrapper -l
lsbcmnds : driver installed
device (14E4:431 present (alternate driver: [COLOR="Blue"]ssb[/COLOR])Is the module *ssb* actually loading? Is it needed for a Broadcom ethernet device using *b44* and *ssb*? I wonder if this has any impact on this baffling problem. Find out if it is loading with:```
lsmod | grep -e ssb -e b44
```If *b44* and *ssb* are both loaded, then you need *ssb* for your ethernet device. If only ssb is loaded, please blacklist it:```
sudo su
echo "blacklist ssb" >> /etc/init.d/blacklist.conf
rmmod -f ssb
exit
```Is there any improvement?

I am still looking for a way to use native drivers, and not ndiswrapper, but I am not having much luck.

Do you have an earlier kernel on your system, 2.6.28-xx for example? Is the behavior the same if you boot into it by interrupting the boot process at the GRUB prompt and selecting an earlier kernel?

---

### Post by luisfm on 2010-03-21
> **chili555 said:**
> Is the module *ssb* actually loading? Is it needed for a Broadcom ethernet device using *b44* and *ssb*? I wonder if this has any impact on this baffling problem. Find out if it is loading with:```
lsmod | grep -e ssb -e b44
```If *b44* and *ssb* are both loaded, then you need *ssb* for your ethernet device. If only ssb is loaded, please blacklist it:```
sudo su
echo "blacklist ssb" >> /etc/init.d/blacklist.conf
rmmod -f ssb
exit
```Is there any improvement?

 

I run the  first line: No output

Then run the su script suggested. I rebooted and now I can't get it to connect to the wireless at all, not even after running "sudo renice +19 $(pidof wpa_supplicant)" that had worked in the past. Therefore, I think I need to remove the ssb from the blacklist. What do you think?.

Also, I looked into other Kernel versions at boot time, and found 2.6.28.18 (boots without mouse pad support) and 2.6.27.14 (doesn't boot - stops after "inotify add.watch(6,(null),10) failed: bad address driver "pcspkr" is already registered. Aborting"

So, there goes that idea.

---

### Post by chili555 on 2010-03-21
> Therefore, I think I need to remove the ssb from the blacklist. What do you think?.Yes, I agree.

I saw this: [http://ubuntuforums.org/showthread.php?t=1343847](http://ubuntuforums.org/showthread.php?t=1343847)

I don't know if you have *ndiswrapper (iw_set_auth:1602): invalid cmd 12 * in dmesg or not. However, you certainly don't have the ability to connect to WPA with ndiswrapper. The thread is very long with some 'fixed for me' comments.

Are you up for building ndiswrapper from source, patching it and trying again? If so, I am willing to help out all you need.

I did notice that version 1.56 is now available, but the patch may only apply to 1.55. I think I'd try 1.56 first.

Let me know what you'd like to try.

---

### Post by luisfm on 2010-03-22
I'm willing to do anything at this point. You know Linux 1000% better than I do. I'm what you call the occassional user that's willing to go heads on into the Linux World.  Your help is appreciated. Fire away. What do I do now?

---

### Post by luisfm on 2010-03-22
The only thing is that when I run dmesg **I don't get** the message:
"[ 227.277096] ndiswrapper (iw_set_auth:1602): invalid cmd 12 "
So, I don't know how much of that post affects me.

---

### Post by chili555 on 2010-03-23
Let's try another approach here:  [https://bugs.launchpad.net/ubuntu/+source/wpasupplicant/+bug/207446](https://bugs.launchpad.net/ubuntu/+source/wpasupplicant/+bug/207446)

See posts #71 and #73. I just tried the download and patch and it seems to work without errors. I suggest you modify it slightly to use the latest version of wpa_supplicant. For the most part, you can copy and paste these commands:```
sudo apt-get install quilt libpcsclite-dev build-essential libssl-dev libdbus-1-dev
mkdir wpa
cd wpa/
pool=http://ftp.ubuntu.com/ubuntu/pool/
wget $pool/main/w/wpasupplicant/wpasupplicant_0.6.9.orig.tar.gz
wget $pool/main/w/wpasupplicant/wpasupplicant_0.6.9-3.diff.gz
wget $pool/main/w/wpasupplicant/wpasupplicant_0.6.9-3ubuntu3.dsc
dpkg-source -x wpasupplicant_0.6.9-3ubuntu3.dsc
cd wpasupplicant-0.6.9/
sudo gedit ./src/rsn_supp/wpa.c 
```Add a new line at line 997, please see attached. Proofread very carefully, save and close gedit.

This is where I stopped because my own wpa_supplicant works fine and I don't need to 'fix' anything. Please proceed and let us know about any errors. ```
dpkg-buildpackage -us -uc -rfakeroot -d
```Failing on building the wpa_gui is okay.```
strip wpa_supplicant/wpa_supplicant
sudo mv /sbin/wpa_supplicant /sbin/wpa_supplicant.orig
sudo cp wpa_supplicant/wpa_supplicant /sbin/
```Reboot. Any improvements?

---

### Post by luisfm on 2010-03-23
Question on these instructions: Do I have to be root for them? Because I tried them without and got the following:
luis@luis-Unix-Monster:~/wpa$ wget $pool/main/w/wpasupplicant/wpasupplicant_0.6.9-3.diff.gz
--2010-03-23 20:27:43--  [http://ftp.ubuntu.com/ubuntu/pool//main/w/wpasupplicant/wpasupplicant_0.6.9-3.diff.gz](http://ftp.ubuntu.com/ubuntu/pool//main/w/wpasupplicant/wpasupplicant_0.6.9-3.diff.gz)
Resolving ftp.ubuntu.com... 91.189.88.46, 91.189.88.45, 91.189.88.30, ...
Connecting to ftp.ubuntu.com|91.189.88.46|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
2010-03-23 20:27:43 ERROR 404: Not Found.

luis@luis-Unix-Monster:~/wpa$ dpkg-source -x wpasupplicant_0.6.9-3ubuntu3.dsc
gpgv: Signature made Sat 06 Mar 2010 07:11:30 PM EST using RSA key ID 140C6664
gpgv: Can't check signature: public key not found
dpkg-source: warning: failed to verify signature on ./wpasupplicant_0.6.9-3ubuntu3.dsc
dpkg-source: error: cannot fstat file ./wpasupplicant_0.6.9-3ubuntu3.diff.gz: No such file or directory
luis@luis-Unix-Monster:~/wpa$ cd wpasupplicant-0.6.9/
bash: cd: wpasupplicant-0.6.9/: No such file or directory


And finally, 

luis@luis-Unix-Monster:~/wpa$ sudo gedit ./src/rsn_supp/wpa.c

Was a new file. Empty. 

Please advise.

---

### Post by chili555 on 2010-03-23
If you get an error at some point, the remaining steps will fail. Let's try to solve the first one. I assume you got the first file. The second is a typo; it should be:```
wget $pool/main/w/wpasupplicant/wpasupplicant_0.6.9-3ubuntu3.diff.gz
```Grab that file and proceed with the remaining steps. If you encounter an error, any error, stop and we'll fix it.

---

### Post by luisfm on 2010-03-23
I was folling your commands blindly and realized that since the instruction:
dpkg-source -x wpasupplicant_0.6.9-3ubuntu3.dsc
failed I could not change to the directory, because it was not created and therefore could not edit a non-existing file. Sorry about this. However, what did I missed here?

---

### Post by chili555 on 2010-03-23
Were you able to wget all three files, one of which is the .dsc file? What was the error?

---

### Post by luisfm on 2010-03-23
This is what I got on the last three lines. I'm goint to reboot now and see what happens:

luis@luis-Unix-Monster:~/wpa/wpasupplicant-0.6.9$ sudo gedit ./src/rsn_supp/wpa.c
[sudo] password for luis: 
luis@luis-Unix-Monster:~/wpa/wpasupplicant-0.6.9$ dpkg-buildpackage -us -uc -rfakeroot -d
dpkg-buildpackage: set CFLAGS to default value: -g -O2
dpkg-buildpackage: set CPPFLAGS to default value: 
dpkg-buildpackage: set LDFLAGS to default value: -Wl,-Bsymbolic-functions
dpkg-buildpackage: set FFLAGS to default value: -g -O2
dpkg-buildpackage: set CXXFLAGS to default value: -g -O2
dpkg-buildpackage: source package wpasupplicant
dpkg-buildpackage: source version 0.6.9-3ubuntu3
dpkg-buildpackage: source changed by Alexander Sack <asac@ubuntu.com>
dpkg-buildpackage: host architecture i386
 fakeroot debian/rules clean
QUILT_PATCHES=debian/patches quilt --quiltrc /dev/null pop -a -R || test $? = 2 
No patch removed
rm -rf .pc debian/stamp-patched
dh_testdir
make: dh_testdir: Command not found
make: *** [clean] Error 127
dpkg-buildpackage: error: fakeroot debian/rules clean gave error exit status 2
luis@luis-Unix-Monster:~/wpa/wpasupplicant-0.6.9$ strip wpa_supplicant/wpa_supplicant
strip: 'wpa_supplicant/wpa_supplicant': No such file
luis@luis-Unix-Monster:~/wpa/wpasupplicant-0.6.9$ sudo mv /sbin/wpa_supplicant /sbin/wpa_supplicant.orig
luis@luis-Unix-Monster:~/wpa/wpasupplicant-0.6.9$ sudo cp wpa_supplicant/wpa_supplicant /sbin/
cp: cannot stat `wpa_supplicant/wpa_supplicant': No such file or directory

---

### Post by luisfm on 2010-03-23
I rebooted and bad news: I cannot even see the wireless network anymore. All I see now is "device not ready" under the Wireless Networks header. BEfore, it showed my home wireless network. ANd to answer your previous question, yes, after correcting the typo, I was able to get all three files. I have to check again to find the error.

---

### Post by chili555 on 2010-03-23
> dpkg-buildpackage: error: fakeroot debian/rules clean gave [COLOR="Red"]error [/COLOR]exit status 2
luis@luis-Unix-Monster:~/wpa/wpasupplicant-0.6.9$ strip wpa_supplicant/wpa_supplicant
strip: 'wpa_supplicant/wpa_supplicant': No such file
luis@luis-Unix-Monster:~/wpa/wpasupplicant-0.6.9$ sudo mv /sbin/wpa_supplicant /sbin/wpa_supplicant.orig
luis@luis-Unix-Monster:~/wpa/wpasupplicant-0.6.9$ sudo cp wpa_supplicant/wpa_supplicant /sbin/
cp: cannot stat `wpa_supplicant/wpa_supplicant': No such file or directoryAs I said before, ***If you encounter an error, any error, stop and we'll fix it. ***

It does no good to proceed with any further steps. It does no good to reboot.

---

### Post by luisfm on 2010-03-23
oops. Sorry. I guess I screwed big time. Any way to fix this?

---

### Post by chili555 on 2010-03-23
The problem with continuing is that you move a rotten apple into a working system. Please do:```
sudo cp /sbin/wpa_supplicant.orig /sbin/wpa_supplicant
```Good thing we made a backup, eh? Reboot and let's see what happens. Please give me some time to refine this.

---

### Post by luisfm on 2010-03-23
Done. THe wireless network is showing up again. Good thinking with the back up. It does not connect to the wireless yet, but at least it appears in the list of wireless networks.

---

### Post by luisfm on 2010-03-26
Hi Chili555: Did you give up on me? I've been using this machine by clicking on my wireless network and issueing the command " sudo renice +19 $(pidof wpa_supplicant)" two or three times until it connects. If I'm coming from a reboot, it changes the priority from 0 to 19. If I'm coming from power save mode, it says "old priority 19, new priority 19. It eventually connects to the wireless after a few tries. It is more anoying than a real problem at this point since I'm able to connect to the wireless network. But it was not like that before my upgrade to 9.10. Go figure!

---

### Post by chili555 on 2010-03-26
I think I have it!

Please do:```
sudo apt-get install debhelper libnl-dev
```I assume you still have the wpasupplicant files with the modification you made: usleep (1000000000000) (or something!). ```
cd wpasupplicant-0.6.9
```Proceed with the remaining steps. As predicted, there will be errors we can ignore related to wpa-gui.

Let me know your result.

We have a Plan B!

---

### Post by luisfm on 2010-03-27
Thanks for these new instructions. I run "sudo apt-get install debhelper..." and as you said, I still had the wpa.c modified file. Then I continued with the rest of the instructions as suggested before. I run "dpkg-buildpackage -us -uc -rfakeroot -d" and got a screen full of stuff that went so fast I could not read it. The last part gives me this:

cc -MMD -Wall -g -O2 -I../src -I../src/crypto -I../src/utils -I../src/common -I../src/rsn_supp -DCONFIG_BACKEND_FILE -DCONFIG_DRIVER_WEXT -DCONFIG_DRIVER_NL80211 -DCONFIG_DRIVER_ATMEL -DCONFIG_DRIVER_WIRED -DEAP_TLS -DEAP_PEAP -DEAP_TTLS -DEAP_MD5 -DEAP_MSCHAPv2 -DEAP_GTC -DEAP_OTP -DEAP_SIM -DEAP_LEAP -DEAP_PSK -DEAP_AKA -DEAP_PAX -DCONFIG_WPS -DEAP_WSC -DIEEE8021X_EAPOL -DPCSC_FUNCS -I/usr/include/PCSC -DEAP_TLS_FUNCS -DEAP_TLS_OPENSSL -DPKCS12_FUNCS -DCONFIG_SMARTCARD -DINTERNAL_SHA256 -DCONFIG_IEEE80211W -DNEED_SHA256 -DCONFIG_WIRELESS_EXTENSION -DCONFIG_CTRL_IFACE -DCONFIG_CTRL_IFACE_UNIX -DCONFIG_CTRL_IFACE_DBUS -DDBUS_API_SUBJECT_TO_CHANGE -I/usr/include/dbus-1.0 -I/usr/lib/dbus-1.0/include   -DDBUS_VERSION_MAJOR=1 -DDBUS_VERSION_MINOR=2 -DCONFIG_READLINE -DCONFIG_PEERKEY -DCONFIG_IEEE80211R -DCONFIG_NO_T_PRF -DCONFIG_DEBUG_FILE -DCONFIG_DEBUG_SYSLOG -DCONFIG_DELAYED_MIC_ERROR_REPORT   -c -o wpa_cli.o wpa_cli.c
wpa_cli.c:23:31: warning: readline/readline.h: No such file or directory
wpa_cli.c:24:30: warning: readline/history.h: No such file or directory
wpa_cli.c: In function &#8216;wpa_cli_completion&#8217;:
wpa_cli.c:1528: warning: implicit declaration of function &#8216;rl_completion_matches&#8217;
wpa_cli.c:1529: warning: return makes pointer from integer without a cast
wpa_cli.c: In function &#8216;wpa_cli_interactive&#8217;:
wpa_cli.c:1546: error: &#8216;rl_attempted_completion_function&#8217; undeclared (first use in this function)
wpa_cli.c:1546: error: (Each undeclared identifier is reported only once
wpa_cli.c:1546: error: for each function it appears in.)
wpa_cli.c:1558: warning: implicit declaration of function &#8216;read_history&#8217;
wpa_cli.c:1559: warning: implicit declaration of function &#8216;stifle_history&#8217;
wpa_cli.c:1571: warning: implicit declaration of function &#8216;readline&#8217;
wpa_cli.c:1571: warning: assignment makes pointer from integer without a cast
wpa_cli.c:1573: error: &#8216;HIST_ENTRY&#8217; undeclared (first use in this function)
wpa_cli.c:1573: error: &#8216;h&#8217; undeclared (first use in this function)
wpa_cli.c:1574: warning: implicit declaration of function &#8216;next_history&#8217;
wpa_cli.c:1576: warning: implicit declaration of function &#8216;previous_history&#8217;
wpa_cli.c:1578: warning: implicit declaration of function &#8216;add_history&#8217;
wpa_cli.c:1632: warning: implicit declaration of function &#8216;history_set_pos&#8217;
wpa_cli.c:1633: warning: implicit declaration of function &#8216;current_history&#8217;
wpa_cli.c:1638: warning: implicit declaration of function &#8216;remove_history&#8217;
wpa_cli.c:1638: warning: implicit declaration of function &#8216;where_history&#8217;
wpa_cli.c:1648: warning: implicit declaration of function &#8216;write_history&#8217;
make[1]: *** [wpa_cli.o] Error 1
make[1]: Leaving directory `/home/luis/wpa/wpasupplicant-0.6.9/wpa_supplicant'
make: *** [build-stamp] Error 2
dpkg-buildpackage: error: debian/rules build gave error exit status 2

Should I continue with the rest?

Once again, thanks for the help.

---

### Post by luisfm on 2010-03-27
When I said the rest, I meant these:

strip wpa_supplicant/wpa_supplicant
sudo mv /sbin/wpa_supplicant /sbin/wpa_supplicant.orig
sudo cp wpa_supplicant/wpa_supplicant /sbin/

??

---

### Post by chili555 on 2010-03-27
> Should I continue with the rest?Yes, sir! That is the wpa_cli error I referred to. Please proceed.

---

### Post by luisfm on 2010-03-27
> **chili555 said:**
> Yes, sir! That is the wpa_cli error I referred to. Please proceed.

Happy to report: Big Success. I rebooted several times and every time the wireless comes up automatically. I'll try to put together all the directions I got from you in a useful format for everyone else. Thanks a million. (You might want to check what I put together to make sure I did not screwed up some more). I'll do that by Monday. I'm tied up today and tomorrow.

---

### Post by chili555 on 2010-03-27
Woo hoo! That is just great! Good work. I know we will help quite a few searchers. Just think: we only needed a lightning fast 60 posts. This was a very tough case but you persevered.

Congratulations.

Note to searchers: This seems to be specific to Broadcom + ndiswrapper + wpa_supplicant. If this is not your situation, then this is probably ***not ***your fix.

---

### Post by luisfm on 2010-03-27
[QUOTE=chili555;9036993]Woo hoo! That is just great! Good work. I know we will help quite a few searchers. Just think: we only needed a lightning fast 60 posts. This was a very tough case but you persevered.

Congratulations.

Note to searchers: This seems to be specific to Broadcom + ndiswrapper + wpa_supplicant. If this is not your situation, then this is probably ***not ***your fix.[/QUOTE
Hey Chili555: You[re the one that stuck with me and my shortcomings. Thanks a lot for the help. Now I'm onto a new thread: video.display probl]ems. But that's for another day.

---

### Post by luisfm on 2010-03-27
> **chili555 said:**
> Woo hoo! That is just great! Good work. I know we will help quite a few searchers. Just think: we only needed a lightning fast 60 posts. This was a very tough case but you persevered.

Congratulations.

Note to searchers: This seems to be specific to Broadcom + ndiswrapper + wpa_supplicant. If this is not your situation, then this is probably ***not ***your fix.

I guess I screwed up the posting. Anyways, thanks

---

