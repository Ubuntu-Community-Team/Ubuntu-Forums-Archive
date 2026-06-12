---
title: "Macmini 2012 Broadcom BCM4331 - &quot;Destination Host Unreachable&quot; after a while"
date: 2012-12-16
forum: Networking &amp; Wireless
---

### Post by edvar on 2012-12-16
I'm dual booting Mac OS X and Ubuntu (12.10 x64) on a brand new macmini from late 2012. 

It was a pain to setup the EFI dual booting but after lots of troubleshooting I got it working just to realize the BCM4331 wireless card was not recognized by Ubuntu. I followed the instructions here to get it working: [https://help.ubuntu.com/community/MacBookPro8-2/Oneiric#Wireless](https://help.ubuntu.com/community/MacBookPro8-2/Oneiric#Wireless)

It works fine until it doesn't. It connects to my home wireless network however after a while I lose all internet connectivity despite of the wireless network still showing as connected at the system tray. There are no error messages on /var/log/syslog or /var/log/dmesg. And this is the main symptom after I setup an intermitent ping to the wireless router:

> 
64 bytes from 192.168.1.1: icmp_req=2368 ttl=64 time=132 ms
64 bytes from 192.168.1.1: icmp_req=2369 ttl=64 time=1239 ms
64 bytes from 192.168.1.1: icmp_req=2370 ttl=64 time=1098 ms
64 bytes from 192.168.1.1: icmp_req=2371 ttl=64 time=848 ms
From 192.168.1.119 icmp_seq=2408 Destination Host Unreachable
From 192.168.1.119 icmp_seq=2409 Destination Host Unreachable
From 192.168.1.119 icmp_seq=2412 Destination Host Unreachable
From 192.168.1.119 icmp_seq=2415 Destination Host Unreachable


The only way to get it fixed is by restarting the network with "sudo service networking restart". After a while it happens again. The other problem is that I cannot connect to my 5Ghz wireless network. It's not a big deal as it connects fine to my alternate 2.4Ghz SSID.

When I boot to the Mac OS X partition, the wireless works perfectly. No dropped packets and I can connect fine to 5Ghz.

Any ideas? Anyone else having similar problems? I want to use Ubuntu as my main OS however I need to connect to it remotely from work and it's not possible with an unstable wireless connection.

---

### Post by edvar on 2012-12-17
Actually I cannot connect to Wireless N networks anymore. THis is what I get on iwconfig when I'm trying to connect:

> 
wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off


However lspci tells me I do have a Wireless N card:

> 
02:00.0 Network controller: Broadcom Corporation BCM4331 802.11a/b/g/n (rev 02)


I can confirm on lsmod I'm using the b43 driver:
 
> 
$ lsmod |grep b43
b43                   369753  0 
mac80211              539908  1 b43
cfg80211              206566  2 b43,mac80211
ssb                    52036  1 b43
bcma                   35656  1 b43


And here some of the messages on /var/log/syslog:

> 
Dec 17 23:50:52 ed-linux NetworkManager[1021]: <info> Activation (wlan0) successful, device activated.
Dec 17 23:50:52 ed-linux NetworkManager[1021]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Commit) complete.
Dec 17 23:50:52 ed-linux NetworkManager[1021]: <info> (wlan0): disconnecting for new activation request.
Dec 17 23:50:52 ed-linux NetworkManager[1021]: <info> (wlan0): device state change: activated -> disconnected (reason 'none') [100 30 0]
Dec 17 23:50:52 ed-linux NetworkManager[1021]: <info> (wlan0): deactivating device (reason 'none') [0]
Dec 17 23:50:52 ed-linux avahi-daemon[1037]: Joining mDNS multicast group on interface wlan0.IPv6 with address fe80::22c9:d0ff:fe92:7f9d.
Dec 17 23:50:52 ed-linux avahi-daemon[1037]: New relevant interface wlan0.IPv6 for mDNS.
Dec 17 23:50:52 ed-linux avahi-daemon[1037]: Registering new address record for fe80::22c9:d0ff:fe92:7f9d on wlan0.*.
Dec 17 23:50:52 ed-linux NetworkManager[1021]: <info> (wlan0): canceled DHCP transaction, DHCP client pid 2803
Dec 17 23:50:52 ed-linux avahi-daemon[1037]: Withdrawing address record for fe80::22c9:d0ff:fe92:7f9d on wlan0.
Dec 17 23:50:52 ed-linux avahi-daemon[1037]: Leaving mDNS multicast group on interface wlan0.IPv6 with address fe80::22c9:d0ff:fe92:7f9d.
Dec 17 23:50:52 ed-linux avahi-daemon[1037]: Interface wlan0.IPv6 no longer relevant for mDNS.
Dec 17 23:50:52 ed-linux kernel: [  169.643159] wlan0: deauthenticating from 00:1d:73:b4:96:10 by local choice (reason=3)
Dec 17 23:50:52 ed-linux wpa_supplicant[1396]: wlan0: CTRL-EVENT-DISCONNECTED bssid=00:00:00:00:00:00 reason=3
Dec 17 23:50:52 ed-linux avahi-daemon[1037]: Withdrawing address record for 192.168.1.103 on wlan0.
Dec 17 23:50:52 ed-linux avahi-daemon[1037]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 192.168.1.103.
Dec 17 23:50:52 ed-linux avahi-daemon[1037]: Interface wlan0.IPv4 no longer relevant for mDNS.
Dec 17 23:50:52 ed-linux NetworkManager[1021]: <info> Activation (wlan0) starting connection '8ball'
Dec 17 23:50:52 ed-linux NetworkManager[1021]: <info> (wlan0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Dec 17 23:50:52 ed-linux NetworkManager[1021]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Dec 17 23:50:52 ed-linux NetworkManager[1021]: <info> (wlan0): supplicant interface state: completed -> disconnected
Dec 17 23:50:52 ed-linux NetworkManager[1021]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Dec 17 23:50:52 ed-linux NetworkManager[1021]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Dec 17 23:50:52 ed-linux NetworkManager[1021]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Dec 17 23:50:52 ed-linux NetworkManager[1021]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Dec 17 23:50:52 ed-linux NetworkManager[1021]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Dec 17 23:50:52 ed-linux NetworkManager[1021]: <info> Activation (wlan0/wireless): access point '8ball' has security, but secrets are required.
Dec 17 23:50:52 ed-linux NetworkManager[1021]: <info> (wlan0): device state change: config -> need-auth (reason 'none') [50 60 0]
Dec 17 23:50:52 ed-linux NetworkManager[1021]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Dec 17 23:50:52 ed-linux NetworkManager[1021]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Dec 17 23:50:52 ed-linux NetworkManager[1021]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Dec 17 23:50:52 ed-linux NetworkManager[1021]: <info> (wlan0): device state change: need-auth -> prepare (reason 'none') [60 40 0]
Dec 17 23:50:52 ed-linux NetworkManager[1021]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Dec 17 23:50:52 ed-linux NetworkManager[1021]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Dec 17 23:50:52 ed-linux NetworkManager[1021]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Dec 17 23:50:52 ed-linux NetworkManager[1021]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Dec 17 23:50:52 ed-linux NetworkManager[1021]: <info> Activation (wlan0/wireless): connection 'xxxxx' has security, and secrets exist.  No new secrets needed.
Dec 17 23:50:52 ed-linux NetworkManager[1021]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Dec 17 23:50:53 ed-linux NetworkManager[1021]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Dec 17 23:50:54 ed-linux avahi-daemon[1037]: Joining mDNS multicast group on interface wlan0.IPv6 with address fe80::22c9:d0ff:fe92:7f9d.
Dec 17 23:50:54 ed-linux avahi-daemon[1037]: New relevant interface wlan0.IPv6 for mDNS.
Dec 17 23:50:54 ed-linux avahi-daemon[1037]: Registering new address record for fe80::22c9:d0ff:fe92:7f9d on wlan0.*.
Dec 17 23:50:54 ed-linux wpa_supplicant[1396]: wlan0: SME: Trying to authenticate with 00:1d:73:b4:96:10 (SSID='xxxxx' freq=2447 MHz)
Dec 17 23:50:54 ed-linux kernel: [  171.301369] wlan0: authenticate with 00:1d:73:b4:96:10
Dec 17 23:50:54 ed-linux NetworkManager[1021]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Dec 17 23:50:54 ed-linux wpa_supplicant[1396]: wlan0: Trying to associate with 00:1d:73:b4:96:10 (SSID='xxxxx' freq=2447 MHz)
Dec 17 23:50:54 ed-linux kernel: [  171.312937] wlan0: send auth to 00:1d:73:b4:96:10 (try 1/3)
Dec 17 23:50:54 ed-linux kernel: [  171.314882] wlan0: authenticated
Dec 17 23:50:54 ed-linux kernel: [  171.316707] wlan0: associate with 00:1d:73:b4:96:10 (try 1/3)
Dec 17 23:50:54 ed-linux NetworkManager[1021]: <info> (wlan0): supplicant interface state: authenticating -> associating
Dec 17 23:50:54 ed-linux kernel: [  171.380486] wlan0: RX AssocResp from 00:1d:73:b4:96:10 (capab=0x411 status=0 aid=1)
Dec 17 23:50:54 ed-linux wpa_supplicant[1396]: wlan0: Associated with 00:1d:73:b4:96:10
Dec 17 23:50:54 ed-linux kernel: [  171.380877] wlan0: associated
Dec 17 23:50:54 ed-linux NetworkManager[1021]: <info> (wlan0): supplicant interface state: associating -> associated
Dec 17 23:50:54 ed-linux NetworkManager[1021]: <info> (wlan0): supplicant interface state: associated -> 4-way handshake
Dec 17 23:50:54 ed-linux wpa_supplicant[1396]: wlan0: WPA: Key negotiation completed with 00:1d:73:b4:96:10 [PTK=CCMP GTK=CCMP]
Dec 17 23:50:54 ed-linux wpa_supplicant[1396]: wlan0: CTRL-EVENT-CONNECTED - Connection to 00:1d:73:b4:96:10 completed (reauth) [id=0 id_str=]
Dec 17 23:50:54 ed-linux NetworkManager[1021]: <info> (wlan0): supplicant interface state: 4-way handshake -> completed
Dec 17 23:50:54 ed-linux NetworkManager[1021]: <info> Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'xxxxx'.
Dec 17 23:50:54 ed-linux NetworkManager[1021]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled.
Dec 17 23:50:54 ed-linux NetworkManager[1021]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) started...
Dec 17 23:50:54 ed-linux NetworkManager[1021]: <info> (wlan0): device state change: config -> ip-config (reason 'none') [50 70 0]
Dec 17 23:50:54 ed-linux NetworkManager[1021]: <info> Activation (wlan0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Dec 17 23:50:54 ed-linux NetworkManager[1021]: <info> Activation (wlan0) Beginning IP6 addrconf.
Dec 17 23:50:54 ed-linux avahi-daemon[1037]: Withdrawing address record for fe80::22c9:d0ff:fe92:7f9d on wlan0.
Dec 17 23:50:54 ed-linux avahi-daemon[1037]: Leaving mDNS multicast group on interface wlan0.IPv6 with address fe80::22c9:d0ff:fe92:7f9d.
Dec 17 23:50:54 ed-linux avahi-daemon[1037]: Interface wlan0.IPv6 no longer relevant for mDNS.
Dec 17 23:50:54 ed-linux NetworkManager[1021]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
Dec 17 23:50:54 ed-linux NetworkManager[1021]: <info> (wlan0): DHCPv4 state changed nbi -> preinit
Dec 17 23:50:54 ed-linux dhclient: Listening on LPF/wlan0/20:c9:d0:92:7f:9d
Dec 17 23:50:54 ed-linux dhclient: Sending on   LPF/wlan0/20:c9:d0:92:7f:9d
Dec 17 23:50:54 ed-linux dhclient: DHCPREQUEST of 192.168.1.103 on wlan0 to 255.255.255.255 port 67
Dec 17 23:50:54 ed-linux NetworkManager[1021]: <info> (wlan0): DHCPv4 state changed preinit -> reboot
Dec 17 23:50:54 ed-linux NetworkManager[1021]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Configure Commit) scheduled...
Dec 17 23:50:54 ed-linux NetworkManager[1021]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Commit) started...
Dec 17 23:50:54 ed-linux avahi-daemon[1037]: Joining mDNS multicast group on interface wlan0.IPv4 with address 192.168.1.103.
Dec 17 23:50:54 ed-linux avahi-daemon[1037]: New relevant interface wlan0.IPv4 for mDNS.
Dec 17 23:50:54 ed-linux avahi-daemon[1037]: Registering new address record for 192.168.1.103 on wlan0.IPv4.
Dec 17 23:50:55 ed-linux NetworkManager[1021]: <info> (wlan0): device state change: ip-config -> activated (reason 'none') [70 100 0]
Dec 17 23:50:55 ed-linux NetworkManager[1021]: <info> Policy set '8ball' (wlan0) as default for IPv4 routing and DNS.
Dec 17 23:50:55 ed-linux NetworkManager[1021]: <info> Activation (wlan0) successful, device activated.
Dec 17 23:50:55 ed-linux NetworkManager[1021]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Commit) complete.
Dec 17 23:50:55 ed-linux avahi-daemon[1037]: Joining mDNS multicast group on interface wlan0.IPv6 with address fe80::22c9:d0ff:fe92:7f9d.
Dec 17 23:50:55 ed-linux avahi-daemon[1037]: New relevant interface wlan0.IPv6 for mDNS.
Dec 17 23:50:55 ed-linux avahi-daemon[1037]: Registering new address record for fe80::22c9:d0ff:fe92:7f9d on wlan0.*.
Dec 17 23:51:15 ed-linux NetworkManager[1021]: <info> (wlan0): IP6 addrconf timed out or failed.
Dec 17 23:51:15 ed-linux NetworkManager[1021]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
Dec 17 23:51:15 ed-linux NetworkManager[1021]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) started...
Dec 17 23:51:15 ed-linux NetworkManager[1021]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) complete.
Dec 17 23:51:42 ed-linux wpa_supplicant[1396]: wlan0: WPA: Group rekeying completed with 00:1d:73:b4:96:10 [GTK=CCMP]


---

### Post by edvar on 2012-12-17
When I try to connect via Wireless N, I get this:

> 
Dec 17 23:50:41 ed-linux wpa_supplicant[1396]: wlan0: SME: Trying to authenticate with 00:24:36:ab:42:a9 (SSID='xxxxxN' freq=2432 MHz)
Dec 17 23:50:41 ed-linux wpa_supplicant[1396]: wlan0: Trying to associate with 00:24:36:ab:42:a9 (SSID='xxxxxN' freq=2432 MHz)
Dec 17 23:50:46 ed-linux NetworkManager[1021]: <info> Marking connection 'xxxxxN' invalid.
Dec 17 23:50:46 ed-linux NetworkManager[1021]: <warn> Activation (wlan0) failed for connection 'xxxxxN'


---

### Post by edvar on 2013-01-02
Bump*

---

### Post by edvar on 2013-01-22
Bump again... No one with a similar problem running Ubuntu on mac?

---

### Post by hardwickj on 2013-02-12
See the ongoing comment thread in the sole answer here: [http://askubuntu.com/questions/235049/my-mac-mini-late-2012-will-not-show-any-wireless-networks-ubuntu-12-10](http://askubuntu.com/questions/235049/my-mac-mini-late-2012-will-not-show-any-wireless-networks-ubuntu-12-10)

---

### Post by edvar on 2013-02-12
I'm already using the b43 driver. Without it the wireless doesn't work at all.

---

### Post by vardyh on 2013-03-27
> **edvar said:**
> Bump again... No one with a similar problem running Ubuntu on mac?

Hi edvar, I met the same issue with you :(
I posted a new thread, [http://ubuntuforums.org/showthread.php?t=2129701](http://ubuntuforums.org/showthread.php?t=2129701), before I find yours :)
Did you find any way of getting rid of this issue?
If there's no way of solving it, I have to switch back using OSX...

---

### Post by Hadaka on 2013-03-27
Hi, the broadcom cards and the linux drivers dont always
play nice with N speeds You can disable the N speed in
your router, or do a search on Broadcom disable N.
I found a couple, but the command is dependant upon
your type of computer...as in acer,dell, look for the 
(computer name) wmi..then issue the command.
good luck !

---

### Post by edvar on 2013-03-27
What's the point of having a wireless N card if you can't take full advantage of it? It's like driving a ferrari on a race track at 20km/h. I'm using the computer as a media center and video streaming over wireless is a "must have" for me.

I love Ubuntu and used it for 5 years on my previous media center without any problems however the lack of reliable wireless (and lack of any help to get it fixed on this thread) forced me into using Mac OS X for months. Now I can see Miguel de Icaza's point: [http://tirania.org/blog/archive/2013/Mar-05.html](http://tirania.org/blog/archive/2013/Mar-05.html) . Unfortunately because of that Ubuntu lost me to Mac OS X as well at least on the desktop... I still have a couple of virtualbox VMs running ubuntu server minimal on the macmini.

---

### Post by vardyh on 2013-03-28
b43 kmod does not support `iwconfig wlan0 modu 11g' sort of things, so I'm building my own kernel w/ b43 PHY_N disabled. I'll give it the last try... If this doesn't work neither, I'm gonna replace all my Linux partitions w/ SnowLeopard...
Linus bless me :):), AND if this works, will you,Linus, fix this ISSUE for us Linux users please ...

---

### Post by vardyh on 2013-03-28
Update:

I compiled and installed kernel 3.8 w/ b43 PHY_N disabled. I didn't help neither... My wireless drops connection just after a few seconds after it established...

---

