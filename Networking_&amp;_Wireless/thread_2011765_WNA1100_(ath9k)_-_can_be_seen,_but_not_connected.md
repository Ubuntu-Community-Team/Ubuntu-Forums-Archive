---
title: "WNA1100 (ath9k) - can be seen, but not connected?"
date: 2012-06-27
forum: Networking &amp; Wireless
---

### Post by marcusadamski on 2012-06-27
Hi I'm currently trying to set up Lubuntu on an old computer for my mother in law. Lubuntu appeared to be a good choice.

It orginally crashed during the install, during the ubiquity slide show, but I got around this by using the text installer on the 12.04 alternative ISO.

Finally got it running, but the system will not recognise the WNA 1100 netgear usb network adapter. Despite during the installation process, it appears it successfully did work to download updates?? It just will not work on the newly installed system.

Looking at the network connection icon, it states under wireless networks "device not managed". However, it appears to be using the Ath9k_htc driver ... it just won't connect:

"
$ lsusb
Bus 002 Device 002: ID 0846:9030 NetGear, Inc. WNA1100 Wireless-N 150 [Atheros AR9271]


$ lsmod
...
ath9k_htc              90811  0 
mac80211              436455  1 ath9k_htc
ath9k_hw              391523  2 ath9k_htc,ath9k_common
ath                    19387  3 ath9k_htc,ath9k_common,ath9k_hw
cfg80211              178679  3 ath9k_htc,mac80211,ath
...

$ iwconfig
wlan0     IEEE 802.11bgn  ESSID:"mynetwork"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: A0:21:B7:AE:09:00   
          Bit Rate=65 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=69/70  Signal level=-41 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:43   Missed beacon:0


$ dmesg
...
[   18.792888] usb 2-1: ath9k_htc: Transferred FW: htc_9271.fw, size: 51272
[   19.045069] ath9k_htc 2-1:1.0: ath9k_htc: HTC initialized with 33 credits
[   19.489740] ath9k_htc 2-1:1.0: ath9k_htc: FW Version: 1.3
[   19.489755] ath: EEPROM regdomain: 0x60
[   19.489760] ath: EEPROM indicates we should expect a direct regpair map
[   19.489776] ath: Country alpha2 being used: 00
[   19.489781] ath: Regpair used: 0x60
[   19.489793] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
...
[   19.499616] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
[   20.831271] ieee80211 phy0: Atheros AR9271 Rev:1
[   20.838966] Registered led device: ath9k_htc-phy0
[   20.838987] usb 2-1: ath9k_htc: USB layer initialized
[   20.842195] usbcore: registered new interface driver ath9k_htc
[   22.887491] ADDRCONF(NETDEV_UP): wlan0: link is not ready
...
[   28.399276] wlan0: authenticate with a0:21:b7:ae:09:00 (try 1)
[   28.404613] wlan0: authenticated
[   29.110784] wlan0: associate with a0:21:b7:ae:09:00 (try 1)
[   29.119115] wlan0: RX AssocResp from a0:21:b7:ae:09:00 (capab=0x431 status=0 aid=2)
[   29.119136] wlan0: associated
...
"

I'm not very familiar with networking, so I'm not sure how to resolve this.
I would be very greatful for any body who could help !! I've been struggling with this issue for days....

Many Thanks,
Marc

---

### Post by chili555 on 2012-06-27
> ... it just won't connect:It sure *looks* connected:> wlan0 IEEE 802.11bgn ESSID:"[COLOR="Red"]mynetwork[/COLOR]"
Mode:Managed Frequency:2.412 GHz Access Point: A0:21:B7:AE:09:00
[COLOR="Red"]Bit Rate=65 Mb/s[/COLOR] Tx-Power=20 dBm 
etc., etc.As well as:> [ 28.404613] wlan0: authenticated
[ 29.110784] wlan0: associate with a0:21:b7:ae:09:00 (try 1)
[ 29.119115] wlan0: RX AssocResp from a0:21:b7:ae:09:00 (capab=0x431 status=0 aid=2)
[ 29.119136] [COLOR="Red"]wlan0: associated[/COLOR]Can you ping Google's nameserver?```
ping -c3 8.8.8.8
```How about Google themselves?```
ping -c3 www.google.com
```If so, can you open Firefox and pull web pages?

What exactly can't you do?

---

### Post by marcusadamski on 2012-06-28
Hi chili555 - thanks for getting back to me...

> It sure *looks* connected:I know.... as requested:
- if I use the default browser "chrome" and enter "www.google.com" for the URL, I get "web page not found"

- ping -c3 8.8.8.8, I get "network unreachable"

- ping -c3 [www.google.com]("http://www.google.com"), I get "unknown host: www.google.com"


Note - if i put the USB adapter into my Ubuntu 12.04 box, it works immediately.
I.e. the adapter and wireless access point are working correctly, and the currently Ubuntu base works with this adapter.

Note 2 = I haven't changed anything on the newly installed Lubuntu system, just installed new. Also I've re-installed multiple times .... just in case

I'm open for any other suggestions ....

Many thanks
Marc

---

### Post by chili555 on 2012-06-28
Weird! 

Let's have a look at:```
cat /etc/network/interfaces
cat /etc/NetworkManager/NetworkManager.conf
```Also, make sure that when you click the Network Manager icon and Edit Connections, that the wireless settings are set to Infrastructure and under IPv4, there are no extra settings beyond DHCP.

---

### Post by marcusadamski on 2012-06-29
Thanks for helping me investigate this. As requested :

cat /etc/network/interfaces

> 
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto wlan0
#NetworkManager#iface wlan0 inet dhcp
# This is an autoconfigured IPv6 interface
iface wlan0 inet6 auto
	wpa-ssid adams-lv
	wpa-psk  XXXXXXXX <displayed correct password>



cat /etc/NetworkManager/NetworkManager.conf

> 
[main]
plugins=ifupdown,keyfile
dns=dnsmasq

[ifupdown]
managed=false



Regarding the Network Manager Icon - the wireless tab does not display / find any wireless connections, so I'm unable to configure anything. 

The logs suggest I'm configured to use "adams-lv". Note this is the wireless connection I configured during the installation. During the installation multiple wireless APs were detected and I was able to configure "adams-lv". 

However, I've never selected this connection after the installation because the Network Manager Icon has never displayed / detected  any wireless connections?

Any ideas why the Network connectivity would work during the installation, but leave me in this "in-between" state after the installation?

Many thanks!

---

### Post by chili555 on 2012-06-29
Yikes! Network Manager, in your case, is set to not manage any interfaces outlined in /etc/network/interfaces; wlan0 is declared and so won't be handled by NM, just as you note:> Regarding the Network Manager Icon - the wireless tab does not display / find any wireless connections, so I'm unable to configure anything. I suggest you comment out all the wlan0 lines in /etc/network/interfaces *OR* remove NM altogether. Mixed mode some of this and some of that hardly ever works well if at all.

Whichever course of action you take ought be followed with a reboot.

---

### Post by marcusadamski on 2012-06-29
Fantastic ! That did the trick, thanks very much for taking the time to work through the issue.
Solution:
- commented out the wlan0 lines

Network manager then happily picked up the wireless connection after a reboot.

Seems like this is a bug in the Lunbutu Alternative text installer (12.04). 

Again thanks for your patience. I've now got a fully functional 12 year old PC, running Lubuntu.

All the best 
Marc

---

### Post by wredgum on 2012-10-13
Gotta agree, I also used the alternate text installer and got the extra lines, same scenario (worked during install, not after).  Seems I got some IPV6 lines added to interfaces as well - commented out, restart NM it worked fine.

---

