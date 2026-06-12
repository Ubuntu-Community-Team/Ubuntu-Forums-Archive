---
title: "Using MA111with Dapper"
date: 2006-06-17
forum: Networking &amp; Wireless
---

### Post by rscow on 2006-06-17
I have installed Dapper Drake via the Live CD on a Dell box.  I am trying to get it to work with a Netgear MA111 USB dongle.

I have searched the forums.  I have found the How-To and followed the instructions.  ([https://wiki.ubuntu.com/WifiDocs/Device/NetgearMA111?highlight=%28ma11](https://wiki.ubuntu.com/WifiDocs/Device/NetgearMA111?highlight=%28ma11))

The prism2_usb driver is installed.  The wlan0 interface shows up in the Networking application ... it didn't before I went through the HowTo.  The MA111 shows up in the Device Manager.  It is recognized as an USB wireless adapter.

The wlan file in /etc/modprobe.d/wlan didn't exist.  So I created one and then put in alias wlan0 prism2_usb in that file, using pico.

I installed linux-wlan-ng via the install CD.  I edited /etc/network/interfaces.

The MA111 flashes its LED, which supposedly indicates that it isn't getting an IP etc.  I still can't connect with the internet. 

So, what should I do next?

---

### Post by tormod on 2006-06-18
Are you using WEP? Please post your interfaces file (anonymize your key if you like).
Please also post the output of iwconfig.

I updated the WifiDocs/Device/NetgearMA111 last night. Did you follow the latest instructions (there was some mixup in the /etc/network/interfaces example)?

See also [https://wiki.ubuntu.com/WifiDocs/Driver/prism2_usb](https://wiki.ubuntu.com/WifiDocs/Driver/prism2_usb) (new page).

---

### Post by rscow on 2006-06-18
Here is my iwconfig file:

lo        no wireless extensions.

wlan0     IEEE 802.11-DS  ESSID:""
          Mode:Auto  Frequency:2.462 GHz  Access Point: Not-Associated
          Bit Rate:2 Mb/s   Tx-Power:18 dBm
          Retry min limit:8   RTS thr:off   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

sit0      no wireless extensions.


Here is my interfaces file:  (I have the WEP turned off right now just to set up)

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
wireless_mode managed
#wireless-essid SeacowNetwork
#wireless_enc on
#wlan_ng_key0 xx:xx:xx:xx:xx
#wlan_ng_authtype opensystem

---

### Post by tormod on 2006-06-18
Was that iwconfig output from using this interfaces file, and it was working without encryption? I thought you would need the essid even without encryption (but I never tried).

Is your router set to use "sharedkey"? In that case use: wlan_ng_authtype sharedkey

ps. and you did replace the xx's with your actual WEP hex key? ;)

---

