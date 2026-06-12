---
title: "Large file copy resets wireless connection over and over"
date: 2009-11-13
forum: Networking &amp; Wireless
---

### Post by copperhead on 2009-11-13
I searched through the forum, but I didn't see anyone else with the same problem.  I hope someone is able to help.

As a preface, I was running with no problems on 9.04.  Last week, I did a fresh installation of 9.10, and started noticing this problem immediately.

Here's what's happening: I'm using a wireless connection from my Asus Aspire 4530 (Atheros Communications Inc. AR928X Wireless Network Adapter) to a Buffalo wireless router.  It connects just fine via WPA, and I can surf the internet, watch youtube, and other low bandwidth activities with no problems.

I have an CIFS mount to a NAS that I copy large files to and from, and I noticed that my effective transfer rate was somewhere around 500KB/S.  Also, I found that surfing the Internet became almost impossible, since my network seemed to sporadically die.

I loaded up the System Monitor and saw a repeated pattern.  I tried using SFTP to transfer a file to a linux server on my network and saw the same pattern.

[IMG]http://www.glamdring.org/images/flakey_network.png[/IMG]

My connection never "drops" per se... the wireless signal is strong, and I'm never disconnected from the router.  When the connection hiccups, all network dies, not just the transfer itself.  After a while, it seems my transfer gives up.

Any help would be greatly appreciated...

EDIT: I uploaded a [movie]("http://www.glamdring.org/images/test-0000.mpeg") so you can see what happens when I upload a file.  I think it's a speed issue, since uploading a file to a server over the Internet works with no problems.  It almost seems like I'm transferring too fast and it chokes.

EDIT:  Looks like I was wrong about losing the wireless. Here's what's happening in the /var/log/kern.log

```

Nov 14 16:05:26 smaug kernel: [ 6857.013034] wlan0: no probe response from AP 00:1d:73:55:9b:69 - disassociating
Nov 14 16:05:27 smaug kernel: [ 6858.226016] wlan0: authenticate with AP 00:1d:73:55:9b:69
Nov 14 16:05:27 smaug kernel: [ 6858.228100] wlan0: authenticated
Nov 14 16:05:27 smaug kernel: [ 6858.228107] wlan0: associate with AP 00:1d:73:55:9b:69
Nov 14 16:05:27 smaug kernel: [ 6858.230767] wlan0: RX ReassocResp from 00:1d:73:55:9b:69 (capab=0x411 status=0 aid=2)
Nov 14 16:05:27 smaug kernel: [ 6858.230772] wlan0: associated
Nov 14 16:05:36 smaug kernel: [ 6867.021038] wlan0: no probe response from AP 00:1d:73:55:9b:69 - disassociating
Nov 14 16:05:37 smaug kernel: [ 6868.253631] wlan0: authenticate with AP 00:1d:73:55:9b:69
Nov 14 16:05:37 smaug kernel: [ 6868.256316] wlan0: authenticated
Nov 14 16:05:37 smaug kernel: [ 6868.256326] wlan0: associate with AP 00:1d:73:55:9b:69
Nov 14 16:05:37 smaug kernel: [ 6868.258968] wlan0: RX ReassocResp from 00:1d:73:55:9b:69 (capab=0x411 status=0 aid=2)
Nov 14 16:05:37 smaug kernel: [ 6868.258976] wlan0: associated
Nov 14 16:05:46 smaug kernel: [ 6877.013324] wlan0: no probe response from AP 00:1d:73:55:9b:69 - disassociating
Nov 14 16:05:47 smaug kernel: [ 6878.212237] wlan0: authenticate with AP 00:1d:73:55:9b:69
Nov 14 16:05:47 smaug kernel: [ 6878.214324] wlan0: authenticated
Nov 14 16:05:47 smaug kernel: [ 6878.214334] wlan0: associate with AP 00:1d:73:55:9b:69
Nov 14 16:05:47 smaug kernel: [ 6878.217620] wlan0: RX ReassocResp from 00:1d:73:55:9b:69 (capab=0x411 status=0 aid=2)
Nov 14 16:05:47 smaug kernel: [ 6878.217629] wlan0: associated
Nov 14 16:05:56 smaug kernel: [ 6887.021027] wlan0: no probe response from AP 00:1d:73:55:9b:69 - disassociating
Nov 14 16:05:57 smaug kernel: [ 6888.223236] wlan0: authenticate with AP 00:1d:73:55:9b:69
Nov 14 16:05:57 smaug kernel: [ 6888.225349] wlan0: authenticated
Nov 14 16:05:57 smaug kernel: [ 6888.225355] wlan0: associate with AP 00:1d:73:55:9b:69
Nov 14 16:05:57 smaug kernel: [ 6888.229047] wlan0: RX ReassocResp from 00:1d:73:55:9b:69 (capab=0x411 status=0 aid=2)
Nov 14 16:05:57 smaug kernel: [ 6888.229053] wlan0: associated
Nov 14 16:06:06 smaug kernel: [ 6897.021032] wlan0: no probe response from AP 00:1d:73:55:9b:69 - disassociating

```

My daemon.log

```

Nov 14 16:09:32 smaug wpa_supplicant[1312]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Nov 14 16:09:32 smaug NetworkManager: <info>  (wlan0): supplicant connection state:  completed -> disconnected
Nov 14 16:09:32 smaug NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Nov 14 16:09:33 smaug wpa_supplicant[1312]: CTRL-EVENT-SCAN-RESULTS 
Nov 14 16:09:33 smaug wpa_supplicant[1312]: Trying to associate with 00:1d:73:55:9b:69 (SSID='001D73559B68' freq=2412 MHz)
Nov 14 16:09:33 smaug NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Nov 14 16:09:33 smaug wpa_supplicant[1312]: Associated with 00:1d:73:55:9b:69
Nov 14 16:09:33 smaug NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> associated
Nov 14 16:09:33 smaug NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> 4-way handshake
Nov 14 16:09:33 smaug NetworkManager: <info>  (wlan0): supplicant connection state:  4-way handshake -> group handshake
Nov 14 16:09:34 smaug wpa_supplicant[1312]: WPA: Key negotiation completed with 00:1d:73:55:9b:69 [PTK=CCMP GTK=CCMP]
Nov 14 16:09:34 smaug wpa_supplicant[1312]: CTRL-EVENT-CONNECTED - Connection to 00:1d:73:55:9b:69 completed (reauth) [id=0 id_str=]
Nov 14 16:09:34 smaug NetworkManager: <info>  (wlan0): supplicant connection state:  group handshake -> completed
Nov 14 16:09:41 smaug wpa_supplicant[1312]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Nov 14 16:09:41 smaug NetworkManager: <info>  (wlan0): supplicant connection state:  completed -> disconnected
Nov 14 16:09:41 smaug NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Nov 14 16:09:42 smaug wpa_supplicant[1312]: CTRL-EVENT-SCAN-RESULTS 
Nov 14 16:09:42 smaug wpa_supplicant[1312]: Trying to associate with 00:1d:73:55:9b:69 (SSID='001D73559B68' freq=2412 MHz)
Nov 14 16:09:42 smaug NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Nov 14 16:09:42 smaug wpa_supplicant[1312]: Associated with 00:1d:73:55:9b:69
Nov 14 16:09:42 smaug NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> associated
Nov 14 16:09:42 smaug NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> 4-way handshake
Nov 14 16:09:42 smaug NetworkManager: <info>  (wlan0): supplicant connection state:  4-way handshake -> group handshake
Nov 14 16:09:43 smaug wpa_supplicant[1312]: WPA: Key negotiation completed with 00:1d:73:55:9b:69 [PTK=CCMP GTK=CCMP]
Nov 14 16:09:43 smaug wpa_supplicant[1312]: CTRL-EVENT-CONNECTED - Connection to 00:1d:73:55:9b:69 completed (reauth) [id=0 id_str=]
Nov 14 16:09:43 smaug NetworkManager: <info>  (wlan0): supplicant connection state:  group handshake -> completed
Nov 14 16:09:51 smaug wpa_supplicant[1312]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Nov 14 16:09:51 smaug NetworkManager: <info>  (wlan0): supplicant connection state:  completed -> disconnected
Nov 14 16:09:51 smaug NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Nov 14 16:09:52 smaug wpa_supplicant[1312]: CTRL-EVENT-SCAN-RESULTS 
Nov 14 16:09:52 smaug wpa_supplicant[1312]: Trying to associate with 00:1d:73:55:9b:69 (SSID='001D73559B68' freq=2412 MHz)
Nov 14 16:09:52 smaug NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Nov 14 16:09:52 smaug wpa_supplicant[1312]: Associated with 00:1d:73:55:9b:69
Nov 14 16:09:52 smaug NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> associated
Nov 14 16:09:52 smaug NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> 4-way handshake
Nov 14 16:09:52 smaug NetworkManager: <info>  (wlan0): supplicant connection state:  4-way handshake -> group handshake

```

And my syslog

```

Nov 14 16:10:37 smaug NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> associated
Nov 14 16:10:37 smaug NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> 4-way handshake
Nov 14 16:10:37 smaug NetworkManager: <info>  (wlan0): supplicant connection state:  4-way handshake -> group handshake
Nov 14 16:10:38 smaug wpa_supplicant[1312]: WPA: Key negotiation completed with 00:1d:73:55:9b:69 [PTK=CCMP GTK=CCMP]
Nov 14 16:10:38 smaug wpa_supplicant[1312]: CTRL-EVENT-CONNECTED - Connection to 00:1d:73:55:9b:69 completed (reauth) [id=0 id_str=]
Nov 14 16:10:38 smaug NetworkManager: <info>  (wlan0): supplicant connection state:  group handshake -> completed
Nov 14 16:10:46 smaug wpa_supplicant[1312]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Nov 14 16:10:46 smaug NetworkManager: <info>  (wlan0): supplicant connection state:  completed -> disconnected
Nov 14 16:10:46 smaug kernel: [ 7177.025259] wlan0: no probe response from AP 00:1d:73:55:9b:69 - disassociating
Nov 14 16:10:46 smaug NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Nov 14 16:10:47 smaug kernel: [ 7178.226011] wlan0: authenticate with AP 00:1d:73:55:9b:69
Nov 14 16:10:47 smaug wpa_supplicant[1312]: CTRL-EVENT-SCAN-RESULTS 
Nov 14 16:10:47 smaug wpa_supplicant[1312]: Trying to associate with 00:1d:73:55:9b:69 (SSID='001D73559B68' freq=2412 MHz)
Nov 14 16:10:47 smaug NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Nov 14 16:10:47 smaug wpa_supplicant[1312]: Associated with 00:1d:73:55:9b:69
Nov 14 16:10:47 smaug kernel: [ 7178.229217] wlan0: authenticated
Nov 14 16:10:47 smaug kernel: [ 7178.229225] wlan0: associate with AP 00:1d:73:55:9b:69
Nov 14 16:10:47 smaug kernel: [ 7178.231870] wlan0: RX ReassocResp from 00:1d:73:55:9b:69 (capab=0x411 status=0 aid=2)
Nov 14 16:10:47 smaug kernel: [ 7178.231875] wlan0: associated
Nov 14 16:10:47 smaug NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> associated
Nov 14 16:10:47 smaug NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> 4-way handshake
Nov 14 16:10:47 smaug NetworkManager: <info>  (wlan0): supplicant connection state:  4-way handshake -> group handshake
Nov 14 16:10:48 smaug wpa_supplicant[1312]: WPA: Key negotiation completed with 00:1d:73:55:9b:69 [PTK=CCMP GTK=CCMP]
Nov 14 16:10:48 smaug wpa_supplicant[1312]: CTRL-EVENT-CONNECTED - Connection to 00:1d:73:55:9b:69 completed (reauth) [id=0 id_str=]
Nov 14 16:10:48 smaug NetworkManager: <info>  (wlan0): supplicant connection state:  group handshake -> completed
Nov 14 16:10:56 smaug wpa_supplicant[1312]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Nov 14 16:10:56 smaug kernel: [ 7187.021036] wlan0: no probe response from AP 00:1d:73:55:9b:69 - disassociating
Nov 14 16:10:56 smaug NetworkManager: <info>  (wlan0): supplicant connection state:  completed -> disconnected
Nov 14 16:10:56 smaug NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Nov 14 16:10:57 smaug wpa_supplicant[1312]: CTRL-EVENT-SCAN-RESULTS 
Nov 14 16:10:57 smaug wpa_supplicant[1312]: Trying to associate with 00:1d:73:55:9b:69 (SSID='001D73559B68' freq=2412 MHz)
Nov 14 16:10:57 smaug NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Nov 14 16:10:57 smaug kernel: [ 7188.206999] wlan0: authenticate with AP 00:1d:73:55:9b:69
Nov 14 16:10:57 smaug wpa_supplicant[1312]: Associated with 00:1d:73:55:9b:69
Nov 14 16:10:57 smaug kernel: [ 7188.209300] wlan0: authenticated
Nov 14 16:10:57 smaug kernel: [ 7188.209311] wlan0: associate with AP 00:1d:73:55:9b:69
Nov 14 16:10:57 smaug kernel: [ 7188.211884] wlan0: RX ReassocResp from 00:1d:73:55:9b:69 (capab=0x411 status=0 aid=2)
Nov 14 16:10:57 smaug kernel: [ 7188.211893] wlan0: associated
Nov 14 16:10:57 smaug NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> associated
Nov 14 16:10:57 smaug NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> 4-way handshake
Nov 14 16:10:57 smaug NetworkManager: <info>  (wlan0): supplicant connection state:  4-way handshake -> group handshake
Nov 14 16:10:58 smaug wpa_supplicant[1312]: WPA: Key negotiation completed with 00:1d:73:55:9b:69 [PTK=CCMP GTK=CCMP]
Nov 14 16:10:58 smaug wpa_supplicant[1312]: CTRL-EVENT-CONNECTED - Connection to 00:1d:73:55:9b:69 completed (reauth) [id=0 id_str=]
Nov 14 16:10:58 smaug NetworkManager: <info>  (wlan0): supplicant connection state:  group handshake -> completed
Nov 14 16:11:05 smaug wpa_supplicant[1312]: CTRL-EVENT-SCAN-RESULTS 

```

---

### Post by copperhead on 2009-11-14
I installed wicd and it is working much better...

---

### Post by agro666 on 2009-11-22
I am in the same boat as you.  I installed wicd and its better, but its not perfect.  My AP shows 45-55%.  I can connect and do all normal web browsing activities, but if I attempt to SFTP a file over, I get maybe 1-2 seconds of transfer speeds, then it hiccups.  If I have a 'ping' going in the background I will see:

ping: sendmsg: Network is unreachable

My Acer Aspire Revo is solid as a rock if I use ethernet to my Client Bridge (a WRT54G that is bridged wirelessly (over 802.11g) to my Buffalo WHR-G300N (dd-wrt with high gain external antennas).  But I want to go wirelessly directly to the WHR-G300N and gain the "802.11n" transfer speeds.  This is really annoying why it isn't working.

---

### Post by Iskendar on 2010-02-01
Same problem here: I can ssh into my htpc box (Zotac IONITX-F based system) over the wireless connection, no problem, and scp and samba work for small files, but once I try to transfer a big file (180Mb+) it freezes after about 2-4%, and I get "Destination host unreachable" errors if I try to ping the htpc after that. The system isn't down, xbmc keeps on working fine on it, so it's just the network which goes down. I didn't have this problem over a wired connection. Annoying. I'll try  [this]("http://ubuntuforums.org/showpost.php?p=3767474&postcount=11") proposed solution, I'll let you know if it works.

---

