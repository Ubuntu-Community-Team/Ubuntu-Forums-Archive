---
title: "wireless help 11.04"
date: 2011-08-11
forum: Networking &amp; Wireless
---

### Post by jg579224a on 2011-08-11
I have Ununtu 11.04, and I am trying to connect to the internet, I'm sure Ubuntu recognises my wireless card as the wireless light shows when I'm logged into Ununtu.
The problem I have, is that when I enter the network security key, network manager searches and the give me back to box where one puts their security key, without connecting to the internet.

I have the following (as shown on windows connection properties)

security type: WPA personal

encryption type: AES

---

### Post by pytheas22 on 2011-08-11
Please try connecting once, then open a terminal, run the following commands and post the output here.  That will help us figure out what could be wrong:
```

dmesg | tail -50
sudo iwlist scan
lshw -C Network
lspci -nn
lsusb
uname -rm
```

---

### Post by jg579224a on 2011-08-11
To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

alex@alex-Aspire-5742:~$ dmesg | tail -50
[  177.257909] cfg80211: All devices are disconnected, going to restore regulatory settings
[  177.257920] cfg80211: Restoring regulatory settings
[  177.257940] cfg80211: Calling CRDA to update world regulatory domain
[  177.264255] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain 
[  177.264267] cfg80211: World regulatory domain updated:
[  177.264270] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  177.264277] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  177.264282] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  177.264287] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  177.264292] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  177.264297] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  178.405385] wlan0: authenticate with 00:8b:5d:aa:a2:ca (try 1)
[  178.407686] wlan0: authenticated
[  178.407727] wlan0: associate with 00:8b:5d:aa:a2:ca (try 1)
[  178.414333] wlan0: RX AssocResp from 00:8b:5d:aa:a2:ca (capab=0x431 status=0 aid=1)
[  178.414338] wlan0: associated
[  188.434414] wlan0: deauthenticating from 00:8b:5d:aa:a2:ca by local choice (reason=3)
[  188.568415] cfg80211: All devices are disconnected, going to restore regulatory settings
[  188.568425] cfg80211: Restoring regulatory settings
[  188.568449] cfg80211: Calling CRDA to update world regulatory domain
[  188.574755] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain 
[  188.574765] cfg80211: World regulatory domain updated:
[  188.574769] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  188.574775] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  188.574781] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  188.574786] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  188.574791] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  188.574796] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  189.717794] wlan0: authenticate with 00:8b:5d:aa:a2:ca (try 1)
[  189.720068] wlan0: authenticated
[  189.720093] wlan0: associate with 00:8b:5d:aa:a2:ca (try 1)
[  189.723667] wlan0: RX AssocResp from 00:8b:5d:aa:a2:ca (capab=0x431 status=0 aid=1)
[  189.723671] wlan0: associated
[  199.746393] wlan0: deauthenticating from 00:8b:5d:aa:a2:ca by local choice (reason=3)
[  199.819092] cfg80211: All devices are disconnected, going to restore regulatory settings
[  199.819103] cfg80211: Restoring regulatory settings
[  199.819127] cfg80211: Calling CRDA to update world regulatory domain
[  199.825513] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain 
[  199.825524] cfg80211: World regulatory domain updated:
[  199.825528] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  199.825534] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  199.825539] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  199.825545] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  199.825550] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  199.825555] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  201.006737] wlan0: authenticate with 00:8b:5d:aa:a2:ca (try 1)
[  201.009048] wlan0: authenticated
[  201.009089] wlan0: associate with 00:8b:5d:aa:a2:ca (try 1)
[  201.012679] wlan0: RX AssocResp from 00:8b:5d:aa:a2:ca (capab=0x431 status=0 aid=1)
[  201.012685] wlan0: associated
alex@alex-Aspire-5742:~$ 
alex@alex-Aspire-5742:~$ sudo iwlist scan
[sudo] password for alex:

---

### Post by jg579224a on 2011-08-11
Did I put the command in right?

---

### Post by pytheas22 on 2011-08-12
After you type "sudo iwlist scan" the system will prompt you for your password.  Enter it and press enter.  You won't see the characters on the screen as you type, but after you input the password the command will run and give you output.  Please post that, along with the output from the other commands.  I'll need all that information to figure out what could be wrong.

Sorry not to have explained the "sudo" bit earlier; I forgot that that can be confusing for people new to the Linux command line.

---

### Post by jg579224a on 2011-08-12
Here you go.

---

### Post by jg579224a on 2011-08-12
Unable to connect to internet through wireless.

I have attached the output from the following code:

dmesg | tail -50
sudo iwlist scan
lshw -C Network
lspci -nn
lsusb
uname -rm Thank you.

---

### Post by pytheas22 on 2011-08-12
Thanks for the information.  This provides a better idea of what we're working with.

I doubt your driver is the issue, since you have an Intel card, which should have flawless Linux support.  I suspect the problem lies with the connection manager.  Often in these situations you have better luck using a different application to connect, such as wicd.  You can install wicd in the Ubuntu Software Center, then launch it from the Applications>Internet menu.  (Note that in wicd you have to enter your wireless router's password before trying to connect; it will not automatically prompt you for the password as NetworkManager does.)  Do you have any better luck with wicd?

A second potential solution would be to change the settings on your router.  From the command line output you posted, it actually looks like your router is using WPA1 and WPA2 concurrently.  Normally this should be alright, but it could confuse some connection managers.  It might help to configure your router to use only WPA1 or only WPA2.  Experimenting with the encryption type and channel might also help.  If you don't know how to change the settings on your router, I can provide instructions (or you can google--in most cases it's pretty simple).

---

### Post by jg579224a on 2011-08-12
I am unable to install wicd from the mentiond source, It asks me for my password, the computer makes a noise and then nothing, do you have to be connected to the internet to install it? I mean is it a download, if so could I transfer it from windows where I can use the internet, could this be done on a memory stick?

---

### Post by pdc on 2011-08-12
have a read of this thread

[http://ubuntuforums.org/showthread.php?p=11023142#post11023142](http://ubuntuforums.org/showthread.php?p=11023142#post11023142)

it has the same wireless driver as you 

> Atheros Communications Inc. AR9287 Wireless Network Adapter (PCI-Express) [168c:002e] (rev 01)

chili555 in this post asked for 

> sudo modprobe ath9k
rfkill list all
dmesg | grep -e ath -e wlan

do you want to run those commands and see what they say; (and copy and paste them back to the forum)

reading through the thread will help you see what worked in that case

---

### Post by jg579224a on 2011-08-13
alex@alex-Aspire-5742:~$ sudo modprobe ath9k
[sudo] password for alex: 
Sorry, try again.
[sudo] password for alex: 
alex@alex-Aspire-5742:~$ rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
alex@alex-Aspire-5742:~$ 
alex@alex-Aspire-5742:~$ dmesg | grep -e ath -e wlan
[    3.316687] device-mapper: multipath: version 1.2.0 loaded
[    3.316689] device-mapper: multipath round-robin: version 1.0.0 loaded
[   15.468422] ath9k 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   15.468436] ath9k 0000:02:00.0: setting latency timer to 64
[   15.558747] ath: EEPROM regdomain: 0x65
[   15.558751] ath: EEPROM indicates we should expect a direct regpair map
[   15.558754] ath: Country alpha2 being used: 00
[   15.558756] ath: Regpair used: 0x65
[   15.575934] ieee80211 phy0: Selected rate control algorithm 'ath9k_rate_control'
[   15.576500] Registered led device: ath9k-phy0::radio
[   15.576526] Registered led device: ath9k-phy0::assoc
[   15.576550] Registered led device: ath9k-phy0::tx
[   15.576571] Registered led device: ath9k-phy0::rx
[   15.616645] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   34.134648] wlan0: authenticate with 00:8b:5d:aa:a2:ca (try 1)
[   34.136938] wlan0: authenticated
[   34.136978] wlan0: associate with 00:8b:5d:aa:a2:ca (try 1)
[   34.141973] wlan0: RX AssocResp from 00:8b:5d:aa:a2:ca (capab=0x431 status=0 aid=2)
[   34.141980] wlan0: associated
[   34.151142] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   44.329080] wlan0: no IPv6 routers present
[   81.363079] wlan0: deauthenticating from 00:8b:5d:aa:a2:ca by local choice (reason=3)
[   85.288368] wlan0: authenticate with 00:8b:5d:aa:a2:ca (try 1)
[   85.290726] wlan0: authenticated
[   85.290769] wlan0: associate with 00:8b:5d:aa:a2:ca (try 1)
[   85.294351] wlan0: RX AssocResp from 00:8b:5d:aa:a2:ca (capab=0x431 status=0 aid=2)
[   85.294358] wlan0: associated
[  130.276595] wlan0: deauthenticating from 00:8b:5d:aa:a2:ca by local choice (reason=3)
[  134.202469] wlan0: authenticate with 00:8b:5d:aa:a2:ca (try 1)
[  134.204821] wlan0: authenticated
[  134.204852] wlan0: associate with 00:8b:5d:aa:a2:ca (try 1)
[  134.208453] wlan0: RX AssocResp from 00:8b:5d:aa:a2:ca (capab=0x431 status=0 aid=2)
[  134.208458] wlan0: associated
[  179.193473] wlan0: deauthenticating from 00:8b:5d:aa:a2:ca by local choice (reason=3)
[  183.077221] wlan0: authenticate with 00:8b:5d:aa:a2:ca (try 1)
[  183.081446] wlan0: authenticated
[  183.081491] wlan0: associate with 00:8b:5d:aa:a2:ca (try 1)
[  183.085045] wlan0: RX AssocResp from 00:8b:5d:aa:a2:ca (capab=0x431 status=0 aid=2)
[  183.085055] wlan0: associated
[  228.107760] wlan0: deauthenticating from 00:8b:5d:aa:a2:ca by local choice (reason=3)
[  232.015455] wlan0: authenticate with 00:8b:5d:aa:a2:ca (try 1)
[  232.017708] wlan0: authenticated
[  232.017745] wlan0: associate with 00:8b:5d:aa:a2:ca (try 1)
[  232.023282] wlan0: RX AssocResp from 00:8b:5d:aa:a2:ca (capab=0x431 status=0 aid=2)
[  232.023288] wlan0: associated
[  277.021291] wlan0: deauthenticating from 00:8b:5d:aa:a2:ca by local choice (reason=3)
[  280.960973] wlan0: authenticate with 00:8b:5d:aa:a2:ca (try 1)
[  280.963280] wlan0: authenticated
[  280.963312] wlan0: associate with 00:8b:5d:aa:a2:ca (try 1)
[  280.968442] wlan0: RX AssocResp from 00:8b:5d:aa:a2:ca (capab=0x431 status=0 aid=2)
[  280.968449] wlan0: associated
[  290.983179] wlan0: deauthenticating from 00:8b:5d:aa:a2:ca by local choice (reason=3)
[  292.139215] wlan0: authenticate with 00:8b:5d:aa:a2:ca (try 1)
[  292.141476] wlan0: authenticated
[  292.141518] wlan0: associate with 00:8b:5d:aa:a2:ca (try 1)
[  292.145088] wlan0: RX AssocResp from 00:8b:5d:aa:a2:ca (capab=0x431 status=0 aid=2)
[  292.145096] wlan0: associated
[  302.167061] wlan0: deauthenticating from 00:8b:5d:aa:a2:ca by local choice (reason=3)
[  303.443941] wlan0: authenticate with 00:8b:5d:aa:a2:ca (try 1)
[  303.446242] wlan0: authenticated
[  303.446268] wlan0: associate with 00:8b:5d:aa:a2:ca (try 1)
[  303.449791] wlan0: RX AssocResp from 00:8b:5d:aa:a2:ca (capab=0x431 status=0 aid=2)
[  303.449795] wlan0: associated
[  313.470040] wlan0: deauthenticating from 00:8b:5d:aa:a2:ca by local choice (reason=3)
[  314.662946] wlan0: authenticate with 00:8b:5d:aa:a2:ca (try 1)
[  314.665253] wlan0: authenticated
[  314.665298] wlan0: associate with 00:8b:5d:aa:a2:ca (try 1)
[  314.668891] wlan0: RX AssocResp from 00:8b:5d:aa:a2:ca (capab=0x431 status=0 aid=2)
[  314.668898] wlan0: associated
[  320.741613] wlan0: deauthenticated from 00:8b:5d:aa:a2:ca (Reason: 2)
[  321.967880] wlan0: authenticate with 00:8b:5d:aa:a2:ca (try 1)
[  321.970113] wlan0: authenticated
[  321.970158] wlan0: associate with 00:8b:5d:aa:a2:ca (try 1)
[  321.973726] wlan0: RX AssocResp from 00:8b:5d:aa:a2:ca (capab=0x431 status=0 aid=2)
[  321.973736] wlan0: associated
[  331.993953] wlan0: deauthenticating from 00:8b:5d:aa:a2:ca by local choice (reason=3)
[  333.221018] wlan0: authenticate with 00:8b:5d:aa:a2:ca (try 1)
[  333.224999] wlan0: authenticated
[  333.225042] wlan0: associate with 00:8b:5d:aa:a2:ca (try 1)
[  333.228674] wlan0: RX AssocResp from 00:8b:5d:aa:a2:ca (capab=0x431 status=0 aid=2)
[  333.228680] wlan0: associated
[  339.713649] wlan0: deauthenticating from 00:8b:5d:aa:a2:ca by local choice (reason=3)
alex@alex-Aspire-5742:~$

---

### Post by jg579224a on 2011-08-13
I have been trying to connect ot wireless for ever with various people helping me and no luck ( have a look at my other threads and see if you can gleam a soultion).

A quick solution would make my decade.

---

### Post by chili555 on 2011-08-13
Please stay on one thread at a time so I don't have to chase you; preferably this one. I gather, from various threads that your ath9k won't connect although it sees the router. Please try:```
sudo ifconfig wlan0 down
sudo rmmod -f ath9k
sudo modprobe ath9k nohwcrypt=1
sudo ifconfig wlan0 up
```Now can you connect? If not, please post:```
sudo cat /var/log/syslog | grep etwork | tail -n20
```Thanks.

---

### Post by Valleyman1988 on 2011-08-13
I have the same issue, any luck yet?

Cheers,

Valleyman

---

### Post by chili555 on 2011-08-13
Please try the fix I proposed and let us know, Valleyman.

---

### Post by pytheas22 on 2011-08-13
Yes, you need an Internet connection to download wicd.  It's possible to download the files you need and transfer them to Ubuntu with a USB stick, but that would be quite complicated.  If you have any way to get a wired connection temporarily that would be easiest; if not, let me know and I can give instructions for installing wicd offline.

Another possibility would be to disable security on your router temporarily, which I suspect would allow you to connect.  Then you could use that wireless connection to download wicd.

---

### Post by jg579224a on 2011-08-13
alex@alex-Aspire-5742:~$ sudo ifconfig wlan0 down
[sudo] password for alex: 
Sorry, try again.
[sudo] password for alex: 
alex@alex-Aspire-5742:~$ sudo rmmod -f ath9k
alex@alex-Aspire-5742:~$ sudo modprobe ath9k nohwcrypt=1
alex@alex-Aspire-5742:~$ sudo ifconfig wlan0 up
alex@alex-Aspire-5742:~$ sudo cat /var/log/syslog | grep etwork | tail -n20
Aug 13 21:30:44 alex-Aspire-5742 NetworkManager[441]: <info> Config: added 'key_mgmt' value 'WPA-PSK'
Aug 13 21:30:44 alex-Aspire-5742 NetworkManager[441]: <info> Config: added 'psk' value '<omitted>'
Aug 13 21:30:44 alex-Aspire-5742 NetworkManager[441]: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Aug 13 21:30:44 alex-Aspire-5742 NetworkManager[441]: nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Aug 13 21:30:44 alex-Aspire-5742 NetworkManager[441]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Aug 13 21:30:44 alex-Aspire-5742 NetworkManager[441]: <info> Config: set interface ap_scan to 1
Aug 13 21:30:44 alex-Aspire-5742 NetworkManager[441]: <info> (wlan0): supplicant connection state:  disconnected -> scanning
Aug 13 21:30:45 alex-Aspire-5742 NetworkManager[441]: <info> (wlan0): supplicant connection state:  scanning -> associating
Aug 13 21:30:45 alex-Aspire-5742 NetworkManager[441]: <info> (wlan0): supplicant connection state:  associating -> associated
Aug 13 21:30:45 alex-Aspire-5742 NetworkManager[441]: <info> (wlan0): supplicant connection state:  associated -> 4-way handshake
Aug 13 21:30:45 alex-Aspire-5742 NetworkManager[441]: <info> (wlan0): supplicant connection state:  4-way handshake -> group handshake
Aug 13 21:30:45 alex-Aspire-5742 NetworkManager[441]: <info> (wlan0): supplicant connection state:  group handshake -> completed
Aug 13 21:30:45 alex-Aspire-5742 NetworkManager[441]: <info> Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'BTHomeHub2-CHPH'.
Aug 13 21:30:45 alex-Aspire-5742 NetworkManager[441]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled.
Aug 13 21:30:45 alex-Aspire-5742 NetworkManager[441]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) started...
Aug 13 21:30:45 alex-Aspire-5742 NetworkManager[441]: <info> (wlan0): device state change: 5 -> 7 (reason 0)
Aug 13 21:30:45 alex-Aspire-5742 NetworkManager[441]: <info> Activation (wlan0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Aug 13 21:30:45 alex-Aspire-5742 NetworkManager[441]: <info> dhclient started with pid 3432
Aug 13 21:30:45 alex-Aspire-5742 NetworkManager[441]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
Aug 13 21:30:45 alex-Aspire-5742 NetworkManager[441]: <info> (wlan0): DHCPv4 state changed nbi -> preinit
alex@alex-Aspire-5742:~$

---

### Post by jg579224a on 2011-08-13
Hello Chili thank you for your help, I will stay on this thread.

The first bit of code did not connect me

---

### Post by chili555 on 2011-08-13
> **jg579224a said:**
> Hello Chili thank you for your help, I will stay on this thread.

The first bit of code did not connect meIt sure looks like it did:> NetworkManager[441]: <info> Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful. [COLOR="Red"]Connected to wireless network 'BTHomeHub2-CHPH'[/COLOR].What does this tell us?```
ifconfig
ping -c3 www.google.com
```

---

### Post by jg579224a on 2011-08-13
The wireless tries to connect, and then it says disconnected and prompts me for my wireless key again, and it cycles like that.

alex@alex-Aspire-5742:~$ sudo ifconfig wlan0 down
[sudo] password for alex: 
alex@alex-Aspire-5742:~$ sudo rmmod -f ath9k
alex@alex-Aspire-5742:~$ sudo modprobe ath9k nohwcrypt=1
alex@alex-Aspire-5742:~$ sudo ifconfig wlan0 up
alex@alex-Aspire-5742:~$ sudo cat /var/log/syslog | grep etwork | tail -n20
Aug 13 22:19:54 alex-Aspire-5742 NetworkManager[452]: <info> Config: added 'key_mgmt' value 'WPA-PSK'
Aug 13 22:19:54 alex-Aspire-5742 NetworkManager[452]: <info> Config: added 'psk' value '<omitted>'
Aug 13 22:19:54 alex-Aspire-5742 NetworkManager[452]: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Aug 13 22:19:54 alex-Aspire-5742 NetworkManager[452]: nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Aug 13 22:19:54 alex-Aspire-5742 NetworkManager[452]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Aug 13 22:19:54 alex-Aspire-5742 NetworkManager[452]: <info> Config: set interface ap_scan to 1
Aug 13 22:19:54 alex-Aspire-5742 NetworkManager[452]: <info> (wlan0): supplicant connection state:  disconnected -> scanning
Aug 13 22:19:55 alex-Aspire-5742 NetworkManager[452]: <info> (wlan0): supplicant connection state:  scanning -> associating
Aug 13 22:19:55 alex-Aspire-5742 NetworkManager[452]: <info> (wlan0): supplicant connection state:  associating -> associated
Aug 13 22:19:55 alex-Aspire-5742 NetworkManager[452]: <info> (wlan0): supplicant connection state:  associated -> 4-way handshake
Aug 13 22:19:55 alex-Aspire-5742 NetworkManager[452]: <info> (wlan0): supplicant connection state:  4-way handshake -> group handshake
Aug 13 22:19:55 alex-Aspire-5742 NetworkManager[452]: <info> (wlan0): supplicant connection state:  group handshake -> completed
Aug 13 22:19:55 alex-Aspire-5742 NetworkManager[452]: <info> Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'BTHomeHub2-CHPH'.
Aug 13 22:19:55 alex-Aspire-5742 NetworkManager[452]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled.
Aug 13 22:19:55 alex-Aspire-5742 NetworkManager[452]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) started...
Aug 13 22:19:55 alex-Aspire-5742 NetworkManager[452]: <info> (wlan0): device state change: 5 -> 7 (reason 0)
Aug 13 22:19:55 alex-Aspire-5742 NetworkManager[452]: <info> Activation (wlan0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Aug 13 22:19:55 alex-Aspire-5742 NetworkManager[452]: <info> dhclient started with pid 1889
Aug 13 22:19:55 alex-Aspire-5742 NetworkManager[452]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
Aug 13 22:19:55 alex-Aspire-5742 NetworkManager[452]: <info> (wlan0): DHCPv4 state changed nbi -> preinit
alex@alex-Aspire-5742:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 88:ae:1d:9c:96:94  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:172 errors:0 dropped:0 overruns:0 frame:0
          TX packets:172 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:13264 (13.2 KB)  TX bytes:13264 (13.2 KB)

wlan0     Link encap:Ethernet  HWaddr 5c:ac:4c:54:68:c1  
          inet6 addr: fe80::5eac:4cff:fe54:68c1/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:55 errors:0 dropped:0 overruns:0 frame:0
          TX packets:60 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:8935 (8.9 KB)  TX bytes:14140 (14.1 KB)

alex@alex-Aspire-5742:~$ ping -c3 [www.google.com](www.google.com)
ping: unknown host [www.google.com](www.google.com)
alex@alex-Aspire-5742:~$ 


I ran all the code again in case something changed.

---

### Post by chili555 on 2011-08-13
> Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful. Connected to wireless network 'BTHomeHub2-CHPH'.Nope, I don't think anything changed. Let's see:```
sudo cat /var/log/syslog | grep -e dhc -e wlan | tail -n25
```You don't have to run the original code again unless you reboot. When you reboot, the nohwcrypt=1 disappears.

---

### Post by jg579224a on 2011-08-13
I am constantly rebooting as I'm swapping between OS's on a partition and I'm getting nervous, so I don't want to miss anything.

alex@alex-Aspire-5742:~$ sudo ifconfig wlan0 down
[sudo] password for alex: 
Sorry, try again.
[sudo] password for alex: 
alex@alex-Aspire-5742:~$ sudo rmmod -f ath9k
alex@alex-Aspire-5742:~$ 
alex@alex-Aspire-5742:~$ sudo modprobe ath9k nohwcrypt=1
alex@alex-Aspire-5742:~$ 
alex@alex-Aspire-5742:~$ sudo ifconfig wlan0 up
alex@alex-Aspire-5742:~$ sudo cat /var/log/syslog | grep etwork | tail -n20
Aug 13 22:55:12 alex-Aspire-5742 NetworkManager[437]: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Aug 13 22:55:12 alex-Aspire-5742 NetworkManager[437]: nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Aug 13 22:55:12 alex-Aspire-5742 NetworkManager[437]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Aug 13 22:55:12 alex-Aspire-5742 NetworkManager[437]: <info> Config: set interface ap_scan to 1
Aug 13 22:55:13 alex-Aspire-5742 NetworkManager[437]: <info> (wlan0): supplicant connection state:  inactive -> scanning
Aug 13 22:55:14 alex-Aspire-5742 NetworkManager[437]: <info> (wlan0): supplicant connection state:  scanning -> associating
Aug 13 22:55:14 alex-Aspire-5742 NetworkManager[437]: <info> (wlan0): supplicant connection state:  associating -> associated
Aug 13 22:55:14 alex-Aspire-5742 NetworkManager[437]: <info> (wlan0): supplicant connection state:  associated -> 4-way handshake
Aug 13 22:55:14 alex-Aspire-5742 NetworkManager[437]: <info> (wlan0): supplicant connection state:  4-way handshake -> group handshake
Aug 13 22:55:14 alex-Aspire-5742 NetworkManager[437]: <info> (wlan0): supplicant connection state:  group handshake -> completed
Aug 13 22:55:14 alex-Aspire-5742 NetworkManager[437]: <info> Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'BTHomeHub2-CHPH'.
Aug 13 22:55:14 alex-Aspire-5742 NetworkManager[437]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled.
Aug 13 22:55:14 alex-Aspire-5742 NetworkManager[437]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) started...
Aug 13 22:55:14 alex-Aspire-5742 NetworkManager[437]: <info> (wlan0): device state change: 5 -> 7 (reason 0)
Aug 13 22:55:14 alex-Aspire-5742 NetworkManager[437]: <info> Activation (wlan0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Aug 13 22:55:14 alex-Aspire-5742 NetworkManager[437]: <info> dhclient started with pid 2105
Aug 13 22:55:14 alex-Aspire-5742 NetworkManager[437]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
Aug 13 22:55:14 alex-Aspire-5742 NetworkManager[437]: <info> (wlan0): DHCPv4 state changed nbi -> preinit
Aug 13 22:55:36 alex-Aspire-5742 NetworkManager[437]: <info> (wlan0): supplicant connection state:  completed -> group handshake
Aug 13 22:55:36 alex-Aspire-5742 NetworkManager[437]: <info> (wlan0): supplicant connection state:  group handshake -> completed
alex@alex-Aspire-5742:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 88:ae:1d:9c:96:94  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:108 errors:0 dropped:0 overruns:0 frame:0
          TX packets:108 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:8304 (8.3 KB)  TX bytes:8304 (8.3 KB)

wlan0     Link encap:Ethernet  HWaddr 5c:ac:4c:54:68:c1  
          inet6 addr: fe80::5eac:4cff:fe54:68c1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:40 errors:0 dropped:0 overruns:0 frame:0
          TX packets:40 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:7713 (7.7 KB)  TX bytes:11815 (11.8 KB)

alex@alex-Aspire-5742:~$ 
alex@alex-Aspire-5742:~$ ping -c3 [www.google.com](www.google.com)
ping: unknown host [www.google.com](www.google.com)


alex@alex-Aspire-5742:~$ sudo cat /var/log/syslog | grep -e dhc -e wlan | tail -n25
Aug 13 22:56:48 alex-Aspire-5742 NetworkManager[437]: <info> Activation (wlan0) Stage 5 of 5 (IP Configure Commit) complete.
Aug 13 22:56:48 alex-Aspire-5742 NetworkManager[437]: <info> (wlan0): device state change: 9 -> 3 (reason 0)
Aug 13 22:56:48 alex-Aspire-5742 NetworkManager[437]: <info> (wlan0): deactivating device (reason: 0).
Aug 13 22:56:48 alex-Aspire-5742 kernel: [  832.064184] wlan0: deauthenticating from 00:8b:5d:aa:a2:ca by local choice (reason=3)
Aug 13 22:56:51 alex-Aspire-5742 NetworkManager[437]: <info> Activation (wlan0) starting connection 'Auto BTHomeHub2-CHPH'
Aug 13 22:56:51 alex-Aspire-5742 NetworkManager[437]: <info> (wlan0): device state change: 3 -> 4 (reason 0)
Aug 13 22:56:51 alex-Aspire-5742 NetworkManager[437]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Aug 13 22:56:51 alex-Aspire-5742 NetworkManager[437]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Aug 13 22:56:51 alex-Aspire-5742 NetworkManager[437]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Aug 13 22:56:51 alex-Aspire-5742 NetworkManager[437]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Aug 13 22:56:51 alex-Aspire-5742 NetworkManager[437]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Aug 13 22:56:51 alex-Aspire-5742 NetworkManager[437]: <info> (wlan0): device state change: 4 -> 5 (reason 0)
Aug 13 22:56:51 alex-Aspire-5742 NetworkManager[437]: <info> Activation (wlan0/wireless): access point 'Auto BTHomeHub2-CHPH' has security, but secrets are required.
Aug 13 22:56:51 alex-Aspire-5742 NetworkManager[437]: <info> (wlan0): device state change: 5 -> 6 (reason 0)
Aug 13 22:56:51 alex-Aspire-5742 NetworkManager[437]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Aug 13 22:56:51 alex-Aspire-5742 NetworkManager[437]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Aug 13 22:56:51 alex-Aspire-5742 NetworkManager[437]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Aug 13 22:56:51 alex-Aspire-5742 NetworkManager[437]: <info> (wlan0): device state change: 6 -> 4 (reason 0)
Aug 13 22:56:51 alex-Aspire-5742 NetworkManager[437]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Aug 13 22:56:51 alex-Aspire-5742 NetworkManager[437]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Aug 13 22:56:51 alex-Aspire-5742 NetworkManager[437]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Aug 13 22:56:51 alex-Aspire-5742 NetworkManager[437]: <info> (wlan0): device state change: 4 -> 5 (reason 0)
Aug 13 22:56:51 alex-Aspire-5742 NetworkManager[437]: <info> Activation (wlan0/wireless): connection 'Auto BTHomeHub2-CHPH' has security, and secrets exist.  No new secrets needed.
Aug 13 22:56:51 alex-Aspire-5742 NetworkManager[437]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Aug 13 22:56:51 alex-Aspire-5742 NetworkManager[437]: <info> (wlan0): supplicant connection state:  disconnected -> scanning

---

### Post by jg579224a on 2011-08-13
Another user recommended using "wicd", do you think that will help?

---

### Post by chili555 on 2011-08-13
When you click the Network Manager icon and Edit Connections, what settings or other details have you entered? None, I hope. NM should see your network, ask for encryption details and connect automatically without any work on your part.

It still looks pretty healthy until here:> <info> (wlan0): supplicant connection state: [COLOR="Red"]disconnected[/COLOR] -> scanning Is the signal strength good and high?```
sudo iwlist wlan0 scan
```You don't have to show us the six or eight other networks in the neighborhood, just BTHomeHub2-CHPH. Are there by chance several access points named BTHomeHub2-CHPH?

---

### Post by overdrank on 2011-08-13
Hi and welcome, please do not create multiple threads on the same issue. Threads merged :)

---

### Post by jg579224a on 2011-08-13
alex@alex-Aspire-5742:~$ sudo iwlist wlan0 scan
[sudo] password for alex: 
wlan0     Scan completed :
          Cell 01 - Address: 00:8B:5D:AA:A2:CA
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=52/70  Signal level=-58 dBm  
                    Encryption key:on
                    ESSID:"BTHomeHub2-CHPH"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000820fd774f
                    Extra: Last beacon: 530ms ago
                    IE: Unknown: 000F4254486F6D65487562322D43485048
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101860003A4000027A4000042435E0062322F00
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606001900000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010020FF7F
                    IE: Unknown: DD0A00037F04010000000000
          Cell 02 - Address: 0A:8B:5D:AA:A2:CA
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=53/70  Signal level=-57 dBm  
                    Encryption key:off
                    ESSID:"BTFON"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000820fd24d4
                    Extra: Last beacon: 530ms ago
                    IE: Unknown: 00054254464F4E
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101860003A4000027A4000042435E0062322F00
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606001900000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010020FF7F
                    IE: Unknown: DD0A00037F04010000000000
          Cell 03 - Address: 06:8B:5D:AA:A2:CA
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=53/70  Signal level=-57 dBm  
                    Encryption key:off
                    ESSID:"BTOpenzone"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000820fcd180
                    Extra: Last beacon: 520ms ago
                    IE: Unknown: 000A42544F70656E7A6F6E65
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101860003A4000027A4000042435E0062322F00
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606001900000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010020FF7F
                    IE: Unknown: DD0A00037F04010000000000
          Cell 04 - Address: E0:91:F5:42:AA:E6
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:on
                    ESSID:"LESLEY-PC_Network"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000001cbf457180
                    Extra: Last beacon: 540ms ago
                    IE: Unknown: 00114C45534C45592D50435F4E6574776F726B
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 0706444520010D14
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101020003A4000027A4000042435E0062322F00
                    IE: Unknown: DD940050F204104A0001101044000102103B00010310470010824FF22B8C7D41C5A13144F534E12555102100074E455447454152102300164E4554474541522044474E3130303020526F7574657210240007312E30302E33331042000831323334353637381054000800060050F2040001101100164E4554474541522044474E3130303020526F757465721008000201AA103C000103
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010000000000
          Cell 05 - Address: C0:D0:44:48:B1:F4
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=23/70  Signal level=-87 dBm  
                    Encryption key:on
                    ESSID:"SKY45555"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000834fb9007
                    Extra: Last beacon: 890ms ago
                    IE: Unknown: 0008534B593435353535
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD090010180202F4000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: 00:18:E7:40:9D:41
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=33/70  Signal level=-77 dBm  
                    Encryption key:on
                    ESSID:"Livebox-22B9"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000124dbcd4181
                    Extra: Last beacon: 970ms ago
                    IE: Unknown: 000C4C697665626F782D32324239
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 050400030000
                    IE: Unknown: 2A0100
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101890003A4000027A4000042435E0062322F00

alex@alex-Aspire-5742:~$ 

I dont know I might have changed something in a moment of idiotic frustration a while ago. Here are some details

I had something under wired heading and it said something about connecting 3 mins ago, but in wireless I have a list of many BTHOMEHUB2-CHCP with "never" next to them, it also says auto next to this.

When I click on AUTOBTHOMEHUB2-CHCP I get a box and under the wireless heading nothing in the fields except MODE:INFRASTRUCTURE
MTU:AUTOMATIC

under wireless security heading I have

SECURITY:WPA & WPA2 PERSONAL

PASSWORD: ***********

under ipv4 settings header I have:

METHOD: AUTOMATIC (DHCP)  and  REQUIRE IPV4 ADDRESSING FOR THIS CONNECTION TO COMPLETE TICKED

under IPV6 I have:

METHOD - AUTOMATIC AND THE SAME BOX TICKED AS FOR ABOVE

---

### Post by nm_geo on 2011-08-13
Mind if I step in here for a moment...

> under IPV6 I have:

METHOD - AUTOMATIC AND THE [COLOR=Red]_SAME BOX TICKED AS FOR ABOVE     _[/COLOR][COLOR=Black]I was following the doctor chili555 on this thread and like I do from time to time.. I changed my wireless setup to be like yours..  Unless you need the IPV6 I would recommend un[/COLOR]-clicking that Box.  When I clicked mine on it cause my wireless to be very unstable so I rebooted same thing..

I unclicked mine under IPV6 because at present I am not using IPV6 for anything that I am aware of.  Try it it will not hurt anything.

In fact I set my IPV6 to[COLOR=Red]** Ignore**[/COLOR] in my Natty version.

---

### Post by chili555 on 2011-08-13
I appreciate you looking in on me, nm_geo. I always appreciate your extra eyes. I would set IPv6 to 'Ignore.' Also, I notice:> Cell 01 - Address: 00:8B:5D:AA:A2:CA
Channel:6
Frequency:2.437 GHz (Channel 6)
Quality=52/70 Signal level=-58 dBm
Encryption keyn
ESSID:"BTHomeHub2-CHPH"
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
9 Mb/s; 12 Mb/s; 18 Mb/s
Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
Mode:Master
Extra:tsf=0000000820fd774f
Extra: Last beacon: 530ms ago
IE: Unknown: 000F4254486F6D65487562322D43485048
IE: Unknown: 010882848B960C121824
IE: Unknown: 030106
[COLOR="Red"]IE: IEEE 802.11i/WPA2 Version 1[/COLOR]
Group Cipher : TKIP
Pairwise Ciphers (2) : CCMP TKIP
Authentication Suites (1) : PSK
[COLOR="Red"]IE: WPA Version 1[/COLOR]
Group Cipher : TKIP
Pairwise Ciphers (2) : CCMP TKIP
Authentication Suites (1) : PSK
IE: Unknown: 2A0100
IE: Unknown: 32043048606C
IE: Unknown: DD180050F2020101860003A4000027A4000042435E0062322F 00
IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000 000000
IE: Unknown: 3D1606001900000000000000000000000000000000000000
IE: Unknown: DD0900037F01010020FF7F
IE: Unknown: DD0A00037F04010000000000Quite often, we have better luck with WPA2 mode only and not mixed mode WPA and WPA2. Can you reset the router and set IPv6 to ignore in NM and try again?

---

### Post by jg579224a on 2011-08-13
Thank you for your continued help,I will do what you say first thing in the morning

---

### Post by chili555 on 2011-08-13
> **jg579224a said:**
> Thank you for your continued help,I will do what you say first thing in the morningIn the morning? In the MORNING?? What the heck, man! We work 25 hours a day, 8 days a week and 400 days a year around here!!

Just kidding. See you then. Have a great evening!

---

### Post by northd_tech on 2011-08-26
> **jg579224a said:**
> I am unable to install wicd from the mentiond source, It asks me for my password, the computer makes a noise and then nothing, do you have to be connected to the internet to install it? I mean is it a download, if so could I transfer it from windows where I can use the internet, could this be done on a memory stick?
I'm not sure if JG is having the same wicd vs. [Gnome] Network Manager problem that I recently solved on my laptop, but if JG's is related to the "Bad Password"/wicd problem, this is a good thread to review:

[http://ubuntuforums.org/showthread.php?t=1675398](http://ubuntuforums.org/showthread.php?t=1675398)

---

