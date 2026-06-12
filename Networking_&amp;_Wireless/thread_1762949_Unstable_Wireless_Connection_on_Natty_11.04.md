---
title: "Unstable Wireless Connection on Natty 11.04"
date: 2011-05-19
forum: Networking &amp; Wireless
---

### Post by edvar on 2011-05-19
I'm using an Atheros ath9k wireless card that has been pretty stable since Ubuntu 9.04. I did a clean install of Natty and ever since my wireless connection has been pretty unstable.

It doesn't actually disconnects but I lose all connectivity. The wifi card continues loaded with a static IP Address assigned to it but I cannot connect to anything. The only way to fix it is restating the network manager and I have to do it at least a couple of times every day.

I tried to whitelist ath_pci on /etc/modprobe.d/blacklist-ath_pci.conf but the problem still persists. Also yesterday I enabled the ubuntu backports on my software sources but so far no kernel updates.

Here are some of the messages filling up the logs:

May 18 08:09:06 ed-linux kernel: [ 4029.970605] cfg80211: Regulatory domain changed to country: AU
May 18 08:09:06 ed-linux kernel: [ 4029.970607] cfg80211: (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
May 18 08:09:06 ed-linux kernel: [ 4029.970611] cfg80211: (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm)
May 18 08:09:06 ed-linux kernel: [ 4029.970614] cfg80211: (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2300 mBm)
May 18 08:09:06 ed-linux kernel: [ 4029.970618] cfg80211: (5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2300 mBm)
May 18 08:09:06 ed-linux kernel: [ 4029.970622] cfg80211: (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)
May 18 08:09:06 ed-linux wpa_supplicant[1616]: WPA: Key negotiation completed with 00:24:36:ab:42:a9 [PTK=CCMP GTK=CCMP]
May 18 08:09:06 ed-linux wpa_supplicant[1616]: CTRL-EVENT-CONNECTED - Connection to 00:24:36:ab:42:a9 completed (reauth) [id=0 id_str=]

...

May 18 07:17:06 ed-linux wpa_supplicant[1616]: WPA: Key negotiation completed with 00:24:36:ab:42:a9 [PTK=CCMP GTK=CCMP]
May 18 07:17:06 ed-linux wpa_supplicant[1616]: CTRL-EVENT-CONNECTED - Connection to 00:24:36:ab:42:a9 completed (reauth) [id=0 id_str=]
May 18 07:17:06 ed-linux NetworkManager[1464]: <info> (wlan0): supplicant connection state: 4-way handshake -> group handshake
May 18 07:17:06 ed-linux NetworkManager[1464]: <info> (wlan0): supplicant connection state: group handshake -> completed
May 18 07:17:56 ed-linux wpa_supplicant[1616]: WPA: Group rekeying completed with 00:24:36:ab:42:a9 [GTK=CCMP]
May 18 07:17:56 ed-linux NetworkManager[1464]: <info> (wlan0): supplicant connection state: completed -> group handshake
May 18 07:17:56 ed-linux NetworkManager[1464]: <info> (wlan0): supplicant connection state: group handshake -> completed
May 18 07:23:01 ed-linux NetworkManager[1464]: <info> (wlan0): supplicant connection state: completed -> group handshake
May 18 07:23:01 ed-linux wpa_supplicant[1616]: WPA: Group rekeying completed with 00:24:36:ab:42:a9 [GTK=CCMP]
May 18 07:23:01 ed-linux NetworkManager[1464]: <info> (wlan0): supplicant connection state: group handshake -> completed
May 18 07:23:05 ed-linux wpa_supplicant[1616]: CTRL-EVENT-DISCONNECTED bssid=00:24:36:ab:42:a9 reason=0
May 18 07:23:05 ed-linux NetworkManager[1464]: <info> (wlan0): supplicant connection state: completed -> disconnected
May 18 07:23:05 ed-linux kernel: [ 1268.964164] cfg80211: All devices are disconnected, going to restore regulatory settings
May 18 07:23:05 ed-linux kernel: [ 1268.964170] cfg80211: Restoring regulatory settings
May 18 07:23:05 ed-linux kernel: [ 1268.964175] cfg80211: Calling CRDA to update world regulatory domain
May 18 07:23:05 ed-linux kernel: [ 1268.968140] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
May 18 07:23:05 ed-linux kernel: [ 1268.968144] cfg80211: 2402000 KHz - 2482000 KHz @ KHz), (N/A mBi, 2000 mBm)
May 18 07:23:05 ed-linux kernel: [ 1268.968147] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
May 18 07:23:05 ed-linux kernel: [ 1268.968149] cfg80211: 2402000 KHz - 2482000 KHz @ KHz), (N/A mBi, 2000 mBm)
May 18 07:23:05 ed-linux kernel: [ 1268.968151] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
May 18 07:23:05 ed-linux kernel: [ 1268.968154] cfg80211: 2402000 KHz - 2482000 KHz @ KHz), (N/A mBi, 2000 mBm)
May 18 07:23:05 ed-linux kernel: [ 1268.968156] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
May 18 07:23:05 ed-linux kernel: [ 1268.968158] cfg80211: 2402000 KHz - 2482000 KHz @ KHz), (N/A mBi, 2000 mBm)
May 18 07:23:05 ed-linux kernel: [ 1268.968161] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
May 18 07:23:05 ed-linux kernel: [ 1268.968163] cfg80211: 2402000 KHz - 2482000 KHz @ KHz), (N/A mBi, 2000 mBm)
May 18 07:23:05 ed-linux kernel: [ 1268.968165] cfg80211: Updating information on frequency 2437 MHz fo...

...

May 19 09:34:18 ed-linux NetworkManager[20127]: <info> (wlan0): supplicant conne
ction state:  group handshake -> completed
May 19 09:39:02 ed-linux CRON[7081]: (root) CMD (  [ -x /usr/lib/php5/maxlifetim
e ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -depth -mindepth 1 -maxdepth
1 -type f -cmin +$(/usr/lib/php5/maxlifetime) -delete)
May 19 09:44:18 ed-linux wpa_supplicant[1071]: WPA: Group rekeying completed wit
h 00:1d:73:b4:96:10 [GTK=CCMP]
May 19 09:44:18 ed-linux NetworkManager[20127]: <info> (wlan0): supplicant conne
ction state:  completed -> group handshake
May 19 09:44:18 ed-linux NetworkManager[20127]: <info> (wlan0): supplicant conne
ction state:  group handshake -> completed
May 19 09:54:18 ed-linux wpa_supplicant[1071]: WPA: Group rekeying completed wit
h 00:1d:73:b4:96:10 [GTK=CCMP]
May 19 09:54:18 ed-linux NetworkManager[20127]: <info> (wlan0): supplicant connection state:  completed -> group handshake
May 19 09:54:18 ed-linux NetworkManager[20127]: <info> (wlan0): supplicant connection state:  group handshake -> completed
May 19 10:04:18 ed-linux NetworkManager[20127]: <info> (wlan0): supplicant connection state:  completed -> group handshake
May 19 10:04:18 ed-linux wpa_supplicant[1071]: WPA: Group rekeying completed with 00:1d:73:b4:96:10 [GTK=CCMP]
May 19 10:04:18 ed-linux NetworkManager[20127]: <info> (wlan0): supplicant connection state:  group handshake -> completed



lspci -k
05:01.0 Network controller: Atheros Communications Inc. AR5008 Wireless Network Adapter (rev 01)
        Subsystem: D-Link System Inc Device 3a6b
        Kernel driver in use: ath9k
        Kernel modules: ath9k

uname -a
Linux ed-linux 2.6.38-9-generic #43-Ubuntu SMP Thu Apr 28 15:25:15 UTC 2011 i686 i686 i386 GNU/Linux

cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.04
DISTRIB_CODENAME=natty
DISTRIB_DESCRIPTION="Ubuntu 11.04"

I added all this info to this bug as well: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/759997](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/759997)

---

### Post by betaman23 on 2011-05-19
I had a similar problem as you describe, but a kernel upgrade fixed it for me a 4-days ago. The only difference is I have a broadcom. It drove me mad.. Worth a shot?

My uname -a
2.6.39-0-generic #5-20110427-Ubuntu

Try this: (taken from broadcom sticky, thanks to NormanFLinux)

Re: Solution to Broadcom 43xx Card Problem (11.04, Natty Narwhal)
You probably have a Broadcom card. To enable wireless networking again, you will have to install a new kernel from the PPA. Follow the instructions below and you should be good to go:

You will have to install a PPA to get the update to install the new kernel.

sudo add-apt-repository ppa:kernel-ppa/ppa

sudo apt-get update

apt-cache showpkg linux-headers

sudo apt-get install linux-headers-2.6.39-0 linux-headers-2.6.39-0-generic linux-image-2.6.39-0-generic --fix-missing

Run the above commands in terminal and once the upgrade is finished, reboot.

---

### Post by edvar on 2011-05-20
Thanks a lot! I installed the new kernel about 10mins ago and so far no wireless related messages filling up /var/log/syslog.

Hopefully it got fixed!

---

### Post by edvar on 2011-05-22
I started getting these messages again on /var/log/syslog:

May 23 10:34:25 ed-linux wpa_supplicant[1060]: WPA: Group rekeying completed wit
h 00:24:36:ab:42:a9 [GTK=CCMP]
May 23 10:34:25 ed-linux NetworkManager[978]: <info> (wlan0): supplicant connect
ion state:  completed -> group handshake
May 23 10:34:25 ed-linux NetworkManager[978]: <info> (wlan0): supplicant connect
ion state:  group handshake -> completed
May 23 10:38:27 ed-linux NetworkManager[978]: <info> (wlan0): supplicant connect
ion state:  completed -> group handshake
May 23 10:38:27 ed-linux wpa_supplicant[1060]: WPA: Group rekeying completed wit
h 00:24:36:ab:42:a9 [GTK=CCMP]
May 23 10:38:27 ed-linux NetworkManager[978]: <info> (wlan0): supplicant connect
ion state:  group handshake -> completed

However the connection itself has been stable since I installed the 2.26.39-0 kernel.

---

