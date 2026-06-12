---
title: "Realtek Semiconductor 802.11b/g/n WiFi Adapter Keeps Disconnecting Randomly"
date: 2011-11-01
forum: Networking &amp; Wireless
---

### Post by theterabyteboy on 2011-11-01
Hi I am running
Ubuntu 11.10.
and I have a
03:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter (rev 01)

My computer is a lenovo T520 and my wireless card keep randomly disconnecting from the wireless network.  Does anybody have some checks I can run to see if I need to update the driver or know of a fix for this?

Thank you!

---

### Post by wildmanne39 on 2011-11-01
Hi please post the results of:
```
lspci -nnk | grep -iA2 net
```
Thank you

---

### Post by theterabyteboy on 2011-11-01
> **wildmanne39 said:**
> Hi please post the results of:
```
lspci -nnk | grep -iA2 net
```
Thank you

Here is the result of that command:
```

00:19.0 Ethernet controller [0200]: Intel Corporation 82579LM Gigabit Network Connection [8086:1502] (rev 04)
	Subsystem: Lenovo Device [17aa:21ce]
	Kernel driver in use: e1000e
--
03:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter [10ec:8176] (rev 01)
	Subsystem: Realtek Semiconductor Co., Ltd. Device [10ec:8195]
	Kernel driver in use: rtl8192ce

```

Thank you!

---

### Post by wildmanne39 on 2011-11-01
Hi, I have been researching your issue for quite a while now and it looks like it is issues with the driver most likely and it does not look promising, but post the results of these commands after you get disconnected and we will see if we can find anything that might help.
```
nm-tool
```
```
rfkill list all
```
```
iwconfig
```
```
sudo cat /var/log/syslog | grep -e rtl -e firmware -e wlan -e wpa -e etwork | tail -n55
```
```
dmesg | grep rtl
```
by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by bogan on 2011-11-01
Hi! **theterabyteboy**.

You posted:
> My computer is a lenovo T520 and my wireless card keep randomly  disconnecting from the wireless network.  Does anybody have some checks I  can run to see if I need to update the driver or know of a fix for  this?I too have problems with a Realtek RTL8188 Wlan Usb Adapter, but mine is a SU not a CE.
 I have no idea what the difference is, but mine runs under Ubuntu 11.10, but not properly under 10.10,
equally mine also does not see the Wlanx entries from ```
lspci -nnk | grep -a2 net 
```Try```
 sudo nm-tool
```It is a bit querky but showed the driver with mine as** r8172u**, but when I tried it again, just now, it showed: driver = usb  !!

Good luck! but do not ask what is the right way to find out what wlan driver is in use!
 It`s no,no question. The last person to ask before me, without being given an answer, got told:>  "Halloween has been an(sic) gone.
Please do not raise old threads from the dead.
[Thread] Closed.
Quote:
Linux assumes you know exactly what you  are doing"That last bit is his very appropriate signature, pity he did not add the word " wrong" to the end of it.

Chao"** bogan**.

---

### Post by praseodym on 2011-11-01
Hi,

cable connection is working? Update the driver **rtl8192ce** via:

```
sudo apt-get install --reinstall linux-headers-$(uname -r) build-essential
wget http://media.cdn.ubuntu-de.org/forum/attachments/2844083/rtl_92ce_92se_92de_Ubuntu_11.x_mac80211_0004.0816.2011.tar.gz
tar xvf rtl_92ce_92se_92de_Ubuntu_11.x_mac80211_0004.0816.2011.tar.gz
cd rtl_92ce_92se_92de_Ubuntu_11.x_mac80211_0004.0816.2011
make
sudo make install
sudo cp -r firmware/* /lib/firmware 
```
Reboot and check:


```
uname -a
iwconfig
lsmod
sudo iwlist scan
modinfo rtl8192ce | egrep 'versi|filen'
rfkill list
```
Dont remove the driver, you need to compile it again if a kernel update occurs.

---

### Post by wildmanne39 on 2011-11-01
Hi praseodym, I thought that since the client is running 11.10 and from what I read that the driver is already the latest?
Thank you

---

### Post by praseodym on 2011-11-01
Hi,

the driver I posted is Source-Version 0004.0816.2011. The client may check

```
modinfo rtl8192ce | egrep 'versi|filen'
```

first. Maybe the new firnware is enough?!

---

### Post by wildmanne39 on 2011-11-01
Hi,this is what is shown.
larryshp:~$ modinfo rtl8192ce | egrep 'versi|filen'
> filename:       /lib/modules/3.0.0-12-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192ce/rtl8192ce.ko
srcversion:     88D2C6ADED1C5FC2EAE88BB
vermagic:       3.0.0-12-generic SMP mod_unload modversions 
Thank you

---

### Post by bogan on 2011-11-02
Hi!,** praseodym,**
You posted:>  The client may check:

  	modinfo rtl8192ce | egrep 'versi|filen'To help sort out my own problems, if I substitute the correct driver name in that command, should it work in Ubuntu 10.10?
I only get a series of: > No command `xxxxx` found !!!!

---

### Post by praseodym on 2011-11-02
In 10.10 you need to install it by hand, too. See here

[http://forum.ubuntuusers.de/topic/kein-w-lan-mit-thinkpad-edge-11-amd-k/#post-2785845](http://forum.ubuntuusers.de/topic/kein-w-lan-mit-thinkpad-edge-11-amd-k/#post-2785845)

The module name there is r8192ce_pci

---

### Post by theterabyteboy on 2011-11-03
> **wildmanne39 said:**
> Hi, I have been researching your issue for quite a while now and it looks like it is issues with the driver most likely and it does not look promising, but post the results of these commands after you get disconnected and we will see if we can find anything that might help.
```
nm-tool
```
```
rfkill list all
```
```
iwconfig
```
```
sudo cat /var/log/syslog | grep -e rtl -e firmware -e wlan -e wpa -e etwork | tail -n55
```
```
dmesg | grep rtl
```
by clicking on new reply and click # and paste the information between the brackets.
Thank you

Here are the results of those commands:
```

NetworkManager Tool

State: connected (global)

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            e1000e
  State:             unavailable
  Default:           no
  HW Address:        F0:DE:F1:94:23:76

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


- Device: wlan0  [ECE Wireless Network] ----------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8192ce
  State:             connected
  Default:           yes
  HW Address:        38:59:F9:E1:FA:07

  Capabilities:
    Speed:           54 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    ECE Wireless Network: Infra, 00:20:A6:50:90:F3, Freq 2412 MHz, Rate 54 Mb/s, Strength 67
    moobilenet:      Infra, 00:0B:86:F3:F2:E1, Freq 2437 MHz, Rate 54 Mb/s, Strength 87
    eduroam:         Infra, 00:0B:86:F3:F2:E2, Freq 2437 MHz, Rate 54 Mb/s, Strength 84 WPA2 Enterprise
    moobilenetx:     Infra, 00:0B:86:F3:F2:E0, Freq 2437 MHz, Rate 54 Mb/s, Strength 69 WPA2 Enterprise
    CS wireless network: Infra, 00:20:A6:B3:B3:93, Freq 2462 MHz, Rate 54 Mb/s, Strength 52
    owens_group:     Infra, 00:02:6F:4E:B7:D1, Freq 2462 MHz, Rate 54 Mb/s, Strength 52 WPA WPA2
    CS wireless network: Infra, 00:02:2D:5F:E4:F0, Freq 2432 MHz, Rate 11 Mb/s, Strength 65
    CS wireless network: Infra, 00:02:2D:5F:E4:D6, Freq 2427 MHz, Rate 11 Mb/s, Strength 79
    CS wireless network: Infra, 00:02:2D:4F:B7:F5, Freq 2427 MHz, Rate 11 Mb/s, Strength 69
    ECE Wireless Network: Infra, 00:20:A6:51:9B:DC, Freq 2447 MHz, Rate 54 Mb/s, Strength 65
    *ECE Wireless Network: Infra, 00:20:A6:5E:98:02, Freq 2412 MHz, Rate 54 Mb/s, Strength 80
    ECE Wireless Network: Infra, 00:20:A6:51:B0:D6, Freq 2412 MHz, Rate 54 Mb/s, Strength 64
    CS wireless network: Infra, 00:20:A6:57:EB:7E, Freq 2427 MHz, Rate 54 Mb/s, Strength 79
    CHMS Conference Room: Infra, 00:24:01:67:FF:14, Freq 2462 MHz, Rate 54 Mb/s, Strength 85 WEP
    CS wireless network: Infra, 00:02:2D:5F:E4:E7, Freq 2462 MHz, Rate 11 Mb/s, Strength 67
    hpsetup:         Ad-Hoc, 2E:25:B3:96:D5:F9, Freq 2437 MHz, Rate 11 Mb/s, Strength 67
    CS wireless network: Infra, 00:02:2D:32:C7:B3, Freq 2437 MHz, Rate 11 Mb/s, Strength 67
    CS wireless network: Infra, 00:20:A6:B7:5A:A1, Freq 2462 MHz, Rate 54 Mb/s, Strength 67
    CS wireless network: Infra, 00:20:A6:57:EB:B4, Freq 2462 MHz, Rate 54 Mb/s, Strength 85
    ECE Wireless Network: Infra, 00:20:A6:51:9B:D4, Freq 2462 MHz, Rate 54 Mb/s, Strength 85
    linksys-g:       Infra, 00:16:B6:9C:C7:54, Freq 2437 MHz, Rate 54 Mb/s, Strength 69
    CS wireless network: Infra, 00:02:2D:53:7A:8A, Freq 2412 MHz, Rate 11 Mb/s, Strength 67
    supreme:         Ad-Hoc, 06:18:0A:01:AF:E8, Freq 2412 MHz, Rate 11 Mb/s, Strength 65
    ECE Wireless Network: Infra, 00:20:A6:52:1D:08, Freq 2412 MHz, Rate 54 Mb/s, Strength 69
    TRENDnet:        Infra, 00:14:D1:C6:D3:F7, Freq 2412 MHz, Rate 54 Mb/s, Strength 67
    RUBINET:         Infra, 00:50:18:06:FD:CE, Freq 2437 MHz, Rate 11 Mb/s, Strength 70 WEP
    DAS 160:         Infra, 00:25:9C:30:8F:6D, Freq 2462 MHz, Rate 54 Mb/s, Strength 67 WPA2
    ap1207:          Infra, 00:11:95:2B:A8:78, Freq 2437 MHz, Rate 54 Mb/s, Strength 69 WPA
    M. Saif Islam's Network: Infra, 10:9A:DD:8D:CA:49, Freq 2412 MHz, Rate 54 Mb/s, Strength 67 WPA2

  IPv4 Settings:
    Address:         169.237.152.90
    Prefix:          24 (255.255.255.0)
    Gateway:         169.237.152.254

    DNS:             169.237.32.1
    DNS:             169.237.32.5

========================================================

0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no


=======================================================


lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"ECE Wireless Network"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:20:A6:5E:98:02   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=54/70  Signal level=-56 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:140   Missed beacon:0


==================================================================

Nov  3 09:17:11 Velociraptor kernel: [67975.887560] wlan0: authenticated
Nov  3 09:17:11 Velociraptor kernel: [67975.887652] wlan0: associate with 00:20:a6:5e:98:02 (try 1)
Nov  3 09:17:11 Velociraptor wpa_supplicant[1158]: Associated with 00:20:a6:5e:98:02
Nov  3 09:17:11 Velociraptor wpa_supplicant[1158]: CTRL-EVENT-CONNECTED - Connection to 00:20:a6:5e:98:02 completed (reauth) [id=0 id_str=]
Nov  3 09:17:11 Velociraptor kernel: [67975.889276] wlan0: RX ReassocResp from 00:20:a6:5e:98:02 (capab=0x21 status=0 aid=5)
Nov  3 09:17:11 Velociraptor kernel: [67975.889279] wlan0: associated
Nov  3 09:17:11 Velociraptor NetworkManager[914]: <info> (wlan0): supplicant interface state: authenticating -> associating
Nov  3 09:17:11 Velociraptor NetworkManager[914]: <info> (wlan0): supplicant interface state: associating -> completed
Nov  3 09:17:15 Velociraptor NetworkManager[914]: <info> (wlan0): roamed from BSSID (none) ((none)) to 00:20:A6:5E:98:02 (ECE Wireless Network)
Nov  3 09:23:58 Velociraptor wpa_supplicant[1158]: Trying to authenticate with 00:20:a6:52:1d:08 (SSID='ECE Wireless Network' freq=2412 MHz)
Nov  3 09:23:58 Velociraptor NetworkManager[914]: <info> (wlan0): supplicant interface state: completed -> authenticating
Nov  3 09:23:58 Velociraptor kernel: [68382.313439] wlan0: direct probe to 00:20:a6:52:1d:08 (try 1/3)
Nov  3 09:23:58 Velociraptor kernel: [68382.510757] wlan0: direct probe to 00:20:a6:52:1d:08 (try 2/3)
Nov  3 09:23:58 Velociraptor kernel: [68382.710509] wlan0: direct probe to 00:20:a6:52:1d:08 (try 3/3)
Nov  3 09:23:58 Velociraptor kernel: [68382.910240] wlan0: direct probe to 00:20:a6:52:1d:08 timed out
Nov  3 09:24:04 Velociraptor kernel: [68389.040607] wlan0: deauthenticating from 00:20:a6:5e:98:02 by local choice (reason=2)
Nov  3 09:24:05 Velociraptor wpa_supplicant[1158]: Trying to authenticate with 00:20:a6:5e:98:02 (SSID='ECE Wireless Network' freq=2412 MHz)
Nov  3 09:24:05 Velociraptor wpa_supplicant[1158]: CTRL-EVENT-DISCONNECTED bssid=00:20:a6:5e:98:02 reason=2
Nov  3 09:24:05 Velociraptor wpa_supplicant[1158]: Trying to associate with 00:20:a6:5e:98:02 (SSID='ECE Wireless Network' freq=2412 MHz)
Nov  3 09:24:05 Velociraptor kernel: [68389.075579] wlan0: authenticate with 00:20:a6:5e:98:02 (try 1)
Nov  3 09:24:05 Velociraptor kernel: [68389.077862] wlan0: authenticated
Nov  3 09:24:05 Velociraptor kernel: [68389.078337] wlan0: associate with 00:20:a6:5e:98:02 (try 1)
Nov  3 09:24:05 Velociraptor wpa_supplicant[1158]: Associated with 00:20:a6:5e:98:02
Nov  3 09:24:05 Velociraptor wpa_supplicant[1158]: CTRL-EVENT-CONNECTED - Connection to 00:20:a6:5e:98:02 completed (reauth) [id=0 id_str=]
Nov  3 09:24:05 Velociraptor kernel: [68389.079912] wlan0: RX ReassocResp from 00:20:a6:5e:98:02 (capab=0x21 status=0 aid=5)
Nov  3 09:24:05 Velociraptor kernel: [68389.079915] wlan0: associated
Nov  3 09:24:05 Velociraptor NetworkManager[914]: <info> (wlan0): supplicant interface state: authenticating -> associating
Nov  3 09:24:05 Velociraptor NetworkManager[914]: <info> (wlan0): supplicant interface state: associating -> completed
Nov  3 09:31:57 Velociraptor wpa_supplicant[1158]: Trying to authenticate with 00:20:a6:52:1d:08 (SSID='ECE Wireless Network' freq=2412 MHz)
Nov  3 09:31:57 Velociraptor kernel: [68861.278932] wlan0: direct probe to 00:20:a6:52:1d:08 (try 1/3)
Nov  3 09:31:57 Velociraptor NetworkManager[914]: <info> (wlan0): supplicant interface state: completed -> authenticating
Nov  3 09:31:58 Velociraptor kernel: [68861.476230] wlan0: direct probe to 00:20:a6:52:1d:08 (try 2/3)
Nov  3 09:31:58 Velociraptor kernel: [68861.675974] wlan0: direct probe to 00:20:a6:52:1d:08 (try 3/3)
Nov  3 09:31:58 Velociraptor kernel: [68861.875713] wlan0: direct probe to 00:20:a6:52:1d:08 timed out
Nov  3 09:32:04 Velociraptor kernel: [68867.770411] wlan0: deauthenticating from 00:20:a6:5e:98:02 by local choice (reason=2)
Nov  3 09:32:04 Velociraptor wpa_supplicant[1158]: Trying to authenticate with 00:20:a6:5e:98:02 (SSID='ECE Wireless Network' freq=2412 MHz)
Nov  3 09:32:04 Velociraptor wpa_supplicant[1158]: CTRL-EVENT-DISCONNECTED bssid=00:20:a6:5e:98:02 reason=2
Nov  3 09:32:04 Velociraptor kernel: [68867.805300] wlan0: authenticate with 00:20:a6:5e:98:02 (try 1)
Nov  3 09:32:04 Velociraptor kernel: [68867.807730] wlan0: authenticated
Nov  3 09:32:04 Velociraptor wpa_supplicant[1158]: Trying to associate with 00:20:a6:5e:98:02 (SSID='ECE Wireless Network' freq=2412 MHz)
Nov  3 09:32:04 Velociraptor wpa_supplicant[1158]: Associated with 00:20:a6:5e:98:02
Nov  3 09:32:04 Velociraptor wpa_supplicant[1158]: CTRL-EVENT-CONNECTED - Connection to 00:20:a6:5e:98:02 completed (reauth) [id=0 id_str=]
Nov  3 09:32:04 Velociraptor kernel: [68867.809204] wlan0: associate with 00:20:a6:5e:98:02 (try 1)
Nov  3 09:32:04 Velociraptor kernel: [68867.810740] wlan0: RX ReassocResp from 00:20:a6:5e:98:02 (capab=0x21 status=0 aid=5)
Nov  3 09:32:04 Velociraptor kernel: [68867.810743] wlan0: associated
Nov  3 09:32:04 Velociraptor NetworkManager[914]: <info> (wlan0): supplicant interface state: authenticating -> associating
Nov  3 09:32:04 Velociraptor NetworkManager[914]: <info> (wlan0): supplicant interface state: associating -> completed
Nov  3 09:37:10 Velociraptor dhclient: DHCPREQUEST of 169.237.152.90 on wlan0 to 169.237.152.1 port 67
Nov  3 09:37:10 Velociraptor NetworkManager[914]: <info> (wlan0): DHCPv4 state changed reboot -> renew
Nov  3 09:37:10 Velociraptor NetworkManager[914]: <info>   address 169.237.152.90
Nov  3 09:37:10 Velociraptor NetworkManager[914]: <info>   prefix 24 (255.255.255.0)
Nov  3 09:37:10 Velociraptor NetworkManager[914]: <info>   gateway 169.237.152.254
Nov  3 09:37:10 Velociraptor NetworkManager[914]: <info>   nameserver '169.237.32.1'
Nov  3 09:37:10 Velociraptor NetworkManager[914]: <info>   nameserver '169.237.32.5'
Nov  3 09:37:10 Velociraptor NetworkManager[914]: <info>   domain name 'ece.ucdavis.edu'


========================================================================

dmesg | grep rtl
[66806.405464] rtl8192ce 0000:03:00.0: PCI INT A disabled
[66808.859220] rtl8192ce 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[66808.859240] rtlwifi: wireless switch is on
[66812.038600] rtl8192c: Loading firmware file rtlwifi/rtl8192cfw.bin
[66812.579915] rtl8192c: Loading firmware file rtlwifi/rtl8192cfw.bin
[66821.181513] rtl8192c: Loading firmware file rtlwifi/rtl8192cfw.bin
[66828.028706] rtl8192c: Loading firmware file rtlwifi/rtl8192cfw.bin
[66834.866215] rtl8192c: Loading firmware file rtlwifi/rtl8192cfw.bin
[66836.314215] rtl8192c: Loading firmware file rtlwifi/rtl8192cfw.bin
[67755.361765] rtl8192c: Loading firmware file rtlwifi/rtl8192cfw.bin
[67771.976865] rtl8192c: Loading firmware file rtlwifi/rtl8192cfw.bin
[67974.698066] rtl8192c: Loading firmware file rtlwifi/rtl8192cfw.bin


```

Thank you!

---

### Post by wildmanne39 on 2011-11-03
Hi, I am not sure there is anything we can do.

1. You have many network's in your area and to make it worse many of them are named the same as the one you are connecting too and are on the same channel, all of that is a nightmare with network manager.  

But I will continue to research the information you just posted from the commands and I well let you know if I find something that might help.
Thank you

---

### Post by theterabyteboy on 2011-11-03
> **wildmanne39 said:**
> Hi, I am not sure there is anything we can do.

1. You have many network's in your area and to make it worse many of them are named the same as the one you are connecting too and are on the same channel, all of that is a nightmare with network manager.  

But I will continue to research the information you just posted from the commands and I well let you know if I find something that might help.
Thank you

The network I am trying to connect to is ECE wireless network, as you can see in the logs, it keeps disconnecting and reconnecting.

Thank you!

---

### Post by praseodym on 2011-11-03
Try to change the ESSID to a one without blanks

---

### Post by wildmanne39 on 2011-11-03
Hi, also there are five networks in your area that have the same name, can you change the name of your network to something unique that should help but do not use all numbers or include dashes or strange characters.

You have to change the name in your router configuration itself and in network manager in the icon in the top right corner.
Thank you

---

### Post by theterabyteboy on 2011-11-03
> **wildmanne39 said:**
> Hi, also there are five networks in your area that have the same name, can you change the name of your network to something unique that should help but do not use all numbers or include dashes or strange characters.

You have to change the name in your router configuration itself and in network manager in the icon in the top right corner.
Thank you

Sorry, can't change any of the network names, I am not the admin.  This is at a univeristy.

---

### Post by wildmanne39 on 2011-11-03
Hi, after you change what I mentioned in my last post we will install wicd and uninstall network manager as a last resort.
Thank you

---

### Post by theterabyteboy on 2011-11-03
> **wildmanne39 said:**
> Hi, after you change what I mentioned in my last post we will install wicd and uninstall network manager as a last resort.
Thank you

Those multiple networks with the same name are just multiple access points to the same network.

---

### Post by wildmanne39 on 2011-11-03
That is what I was wondering, you share internet with many people correct?

---

### Post by theterabyteboy on 2011-11-03
> **wildmanne39 said:**
> That is what I was wondering, you share internet with many people correct?

Yes, i share the internet with many people at the school

---

### Post by wildmanne39 on 2011-11-03
Hi, it looks like your signal strength is weak that could be the problem also.

You can install wicd with software center if you want to see if it will work better and after it is installed run this command to get rid of network manager.
```
sudo apt-get purge network-manager network-manager-gnome
```
Then reboot.

Can you connect to a wired connection if you need too?
Thank you

---

### Post by theterabyteboy on 2011-11-03
> **wildmanne39 said:**
> Hi, it looks like your signal strength is weak that could be the problem also.

You can install wicd with software center if you want to see if it will work better and after it is installed run this command to get rid of network manager.
```
sudo apt-get purge network-manager network-manager-gnome
```
Then reboot.

Can you connect to a wired connection if you need too?
Thank you

I cannot connect to a wired network.  Perhaps I can ask the network admin if I can get access to it, but I would need special permission.  Do I need the wicd client kde as well?

---

### Post by wildmanne39 on 2011-11-03
Hi, no you are running ubuntu not kubuntu, just install the other two, there is no guarantee this will help but in many cases it does.

You only need a wired connection if something goes wrong which it should not, just make sure you install wicd before removing network manager.
Thank you

---

### Post by theterabyteboy on 2011-11-04
> **wildmanne39 said:**
> Hi, no you are running ubuntu not kubuntu, just install the other two, there is no guarantee this will help but in many cases it does.

You only need a wired connection if something goes wrong which it should not, just make sure you install wicd before removing network manager.
Thank you

Hey,  thanks for your help.  I installed wicd, but was forced to restart because then i had no internet.  I got internet before I restarted by connecting via a wired connection, then i reinstalled network-manager.  so i am not sure if my wireless works now because i have network-manager, or if it would work with just wicd on its own.  Either way,  I believe the problem is just with the ECE network.  I am connected to another network now and I appear to not be having issues.  I think my wifi card has a problem with recognizing that all ECE networks are the same, so maybe it keeps switching between them.

Is it possible a driver would fix this issue?

---

### Post by wildmanne39 on 2011-11-04
Hi, after you got rid of network manager you should have rebooted then let wicd take over.

A new driver is not likely since you are running 11.10 that just cane out and it came out with updated drivers.
Thank you

---

### Post by theterabyteboy on 2011-11-16
> **wildmanne39 said:**
> Hi, after you got rid of network manager you should have rebooted then let wicd take over.

A new driver is not likely since you are running 11.10 that just cane out and it came out with updated drivers.
Thank you

No, I appreciate your trying to helping me, but here is the real issue: Ubuntu 11.10 is a garbage with horrible driver support.  Reverting to windows.  I have been using linux for over 10 years and this is frankly ridiculous.  I have many more issues with ubuntu besides this wireless issue.

Thank you but Ubuntu has steadily gone downhill.  It was supposed to be better than windows, but never have I had this many issues with windows.

---

### Post by praseodym on 2011-11-16
For 11.10 the driver can be build with dkms:

```

sudo apt-get install --reinstall linux-headers-$(uname -r) build-essential dkms
wget http://media.cdn.ubuntu-de.org/forum/attachments/2844083/rtl8192ce_dkms_2.6.0006.0321.tar.gz
sudo tar xvf rtl8192ce_dkms_2.6.0006.0321.tar.gz -C /usr/src
sudo dkms add -m rtl8192ce -v 2.6.0006.0321
sudo dkms build -m rtl8192ce -v 2.6.0006.0321
sudo dkms install -m rtl8192ce -v 2.6.0006.0321 

```
Reboot.

---

### Post by PePas on 2012-01-26
> Sounds great to have dkms do it! Something doesn't work...

# cat /etc/issue
Ubuntu 11.10 \n \l

> Error after this:

# sudo dkms build -m rtl8192ce -v 2.6.0006.0321

Kernel preparation unnecessary for this kernel.  Skipping...

Building module:
cleaning build area....(bad exit status: 2)
'make' -C src/ all....(bad exit status: 2)
ERROR (dkms apport): binary package for rtl8192ce: 2.6.0006.0321 not found
Error! Bad return status for module build on kernel: 3.0.0-15-generic (i686)
Consult /var/lib/dkms/rtl8192ce/2.6.0006.0321/build/make.log for more information.

# cat /var/lib/dkms/rtl8192ce/2.6.0006.0321/build/make.log

DKMS make.log for rtl8192ce-2.6.0006.0321 for kernel 3.0.0-15-generic (i686)
Thu Jan 26 23:26:17 ICT 2012
make: Entering directory `/var/lib/dkms/rtl8192ce/2.6.0006.0321/build/src'
make[1]: Entering directory `/usr/src/linux-headers-3.0.0-15-generic'
gcc: error: /lib/modules/3.0.0-15-generic/build/include/linux/autoconf.h: No such file or directory
gcc: fatal error: no input files
compilation terminated.
scripts/Makefile.build:49: *** CFLAGS was changed in "/var/lib/dkms/rtl8192ce/2.6.0006.0321/build/src/HAL/rtl8192/Makefile". Fix it to use EXTRA_CFLAGS.  Stop.
make[1]: *** [_module_/var/lib/dkms/rtl8192ce/2.6.0006.0321/build/src/HAL/rtl8192] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.0.0-15-generic'
make: *** [all] Error 2
make: Leaving directory `/var/lib/dkms/rtl8192ce/2.6.0006.0321/build/src'

---

### Post by Broker on 2012-02-10
I can not enable wireless internet to netbook Dell Mini 1018

```
brok@brok-dell:~$ uname -a
Linux brok-dell 3.0.0-15-generic #26-Ubuntu SMP Fri Jan 20 15:59:53 UTC 2012 i686 i686 i386 GNU/Linux
brok@brok-dell:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:on
          
brok@brok-dell:~$ sudo iwlist scan
[sudo] password for brok: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Network is down

brok@brok-dell:~$ modinfo rtl8192ce | egrep 'versi|filen'
filename:       /lib/modules/3.0.0-15-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192ce/rtl8192ce.ko
srcversion:     49EC1DBDAA57F653E6B7D15
vermagic:       3.0.0-15-generic SMP mod_unload modversions 686 
brok@brok-dell:~$ rfkill list
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: dell-wifi: Wireless LAN
    Soft blocked: yes
    Hard blocked: yes
2: dell-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
3: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
brok@brok-dell:~$ modinfo rtl8192ce | egrep 'versi|filen'
filename:       /lib/modules/3.0.0-15-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192ce/rtl8192ce.ko
srcversion:     49EC1DBDAA57F653E6B7D15
vermagic:       3.0.0-15-generic SMP mod_unload modversions 686 
brok@brok-dell:~$ 
``````

brok@brok-dell:~$ modinfo rtl8192ce | egrep 'versi|filen'
filename:       /lib/modules/3.0.0-15-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192ce/rtl8192ce.ko
srcversion:     49EC1DBDAA57F653E6B7D15
vermagic:       3.0.0-15-generic SMP mod_unload modversions 686 
brok@brok-dell:~$ lspci -nnk | grep -iA2 net
05:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
    Subsystem: Dell Device [1028:048e]
    Kernel driver in use: r8169
--
07:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter [10ec:8176] (rev 01)
    Subsystem: Dell Device [1028:9197]
    Kernel driver in use: rtl8192ce
brok@brok-dell:~$ 
```I am upgrading from 10.10 to 11.10. Wireless worked to 10.10.
I can not enable wireless switch.

---

### Post by praseodym on 2012-02-11
Hi,

try to reset the BIOS

---

### Post by Broker on 2012-02-20
> **praseodym said:**
> Hi,

try to reset the BIOS


 How do reset BIOS?
 It is [Dell Mini Inspiron 1018 netbook]("http://www.dell.com/us/p/inspiron-mini1018/pd").
[http://www.dell.com/us/p/inspiron-mini1018/pd](http://www.dell.com/us/p/inspiron-mini1018/pd)

I install Mint 12 and also I can't switch to wireless button.
 In Windows 7 (triple boot) wireless works fine but I do not like Windows.
 Earlier I have installed PingOS Eee and wireless works fine.

Any ideas please.

---

### Post by praseodym on 2012-02-20
Press the appropriate button at boot up (DEL or F12 or sth.), reset it with e.g. F9 and save&exit with F10

---

### Post by Broker on 2012-02-21
> **praseodym said:**
> Press the appropriate button at boot up (DEL or F12 or sth.), reset it with e.g. F9 and save&exit with F10

Resolved problem.:guitar:
 Thank you very much Praseodym.):P

---

### Post by gaboesquivel on 2012-07-24
I simply installed wicd and unistalled gnome network manager as suggested and that solved my problem, thanks :)

---

### Post by Broker on 2012-07-26
I can not fix  wireless Internet to Mint Mate 13. :(
 I have a triple boot, on Ubuntu 10.0.4 wireless working great, also on MW 7 starter.

---

### Post by halloigen on 2012-08-26
> **PePas said:**
> > Sounds great to have dkms do it! Something doesn't work...

# cat /etc/issue
Ubuntu 11.10 \n \l

> Error after this:

# sudo dkms build -m rtl8192ce -v 2.6.0006.0321

Kernel preparation unnecessary for this kernel.  Skipping...

Building module:
cleaning build area....(bad exit status: 2)
'make' -C src/ all....(bad exit status: 2)
ERROR (dkms apport): binary package for rtl8192ce: 2.6.0006.0321 not found
Error! Bad return status for module build on kernel: 3.0.0-15-generic (i686)
Consult /var/lib/dkms/rtl8192ce/2.6.0006.0321/build/make.log for more information.

# cat /var/lib/dkms/rtl8192ce/2.6.0006.0321/build/make.log

DKMS make.log for rtl8192ce-2.6.0006.0321 for kernel 3.0.0-15-generic (i686)
Thu Jan 26 23:26:17 ICT 2012
make: Entering directory `/var/lib/dkms/rtl8192ce/2.6.0006.0321/build/src'
make[1]: Entering directory `/usr/src/linux-headers-3.0.0-15-generic'
gcc: error: /lib/modules/3.0.0-15-generic/build/include/linux/autoconf.h: No such file or directory
gcc: fatal error: no input files
compilation terminated.
scripts/Makefile.build:49: *** CFLAGS was changed in "/var/lib/dkms/rtl8192ce/2.6.0006.0321/build/src/HAL/rtl8192/Makefile". Fix it to use EXTRA_CFLAGS.  Stop.
make[1]: *** [_module_/var/lib/dkms/rtl8192ce/2.6.0006.0321/build/src/HAL/rtl8192] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.0.0-15-generic'
make: *** [all] Error 2
make: Leaving directory `/var/lib/dkms/rtl8192ce/2.6.0006.0321/build/src'


Hello!  
I had the exact error message as PePas (above), and have been searching for a long time, now, to solve my wireless problem.  
When I saw PePas post, I was encouraged, but no one responded to his/her problem.  
Rug pulled out from under my feet again!  AAAAAAHHHHH!
I love ubuntu, and I'm not about to give up.  Especially, when I feel like I'm so close.  
But, does anyone have an answer to PePas and my issue?  
The poster right after PePas brought up a seperate issue, and then no one ever replied to PePas.  
Please Help!!  and thank you very much in advance.  
Before registering, I've been saved by ubuntuforums many times, and I really appreciate it.

---

### Post by praseodym on 2012-08-27
Older Version 0004.0816.2011 until 11.10:

```
sudo apt-get install --reinstall linux-headers-$(uname -r) build-essential
wget http://media.cdn.ubuntu-de.org/forum/attachments/55/37/2844083-rtl_92ce_92se_92de_Ubuntu_11.x_mac80211_0004.0816.2011.tar.gz
tar xvf 2844083-rtl_92ce_92se_92de_Ubuntu_11.x_mac80211_0004.0816.2011.tar.gz
cd rtl_92ce_92se_92de_Ubuntu_11.x_mac80211_0004.0816.2011
make
sudo make install
sudo cp -r firmware/* /lib/firmware 
```

New Version 0005.1230.2011 for Ubuntu 12.04:

```
sudo apt-get install --reinstall linux-headers-$(uname -r) build-essential
wget http://media.cdn.ubuntu-de.org/forum/attachments/43/33/2844083-rtl_92ce_92se_92de_0005.1230.2011.tar.gz
tar xvf 2844083-rtl_92ce_92se_92de_0005.1230.2011.tar.gz
cd rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011
make
sudo make install
sudo cp -r firmware/* /lib/firmware 
```

Reboot. The driver doesnt work with dkms so far. It needs to be rebuild after a kernel upgrade

---

### Post by halloigen on 2012-08-27
So far so good!!
I've tried other solutions that worked for a while then stopped working after a couple days, so I'll wait to fully celebrate.  
But thank you very much, in advance!
I am very grateful.  
I will try to learn enough where I can figure this stuff out on my own.  

Thank you praseodym and ubuntuforums!

):P

---

