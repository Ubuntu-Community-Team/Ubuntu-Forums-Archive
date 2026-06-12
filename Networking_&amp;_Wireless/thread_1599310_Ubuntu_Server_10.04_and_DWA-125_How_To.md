---
title: "Ubuntu Server 10.04 and DWA-125 How To"
date: 2010-10-17
forum: Networking &amp; Wireless
---

### Post by ario on 2010-10-17
I figured out how to connect wirelessly with D-Link DWA-125 adapter in ad-hoc mode and WEP encryption using Ubuntu 10.04 Server Edition. Here's how to:
Downloaded driver source code for RT3070sta chipset (The main chip of DWA-125 dangle). The version I downloaded is 2.3.0.4_20100604. I attached it here because they removed it from their site and put a new version (2.4.0.1) which is obviously for rt3370sta and is not working!
You can download the attachment if you want.
Extracted somewhere and went to the extraction directory (You can search for needed shell commands somewhere else!;) ).
Then in the source code directory ran:
```
make clean
make uninstall
rm -r --force /etc/Wireless
make
cp RT2870STA.dat RT3070STA.dat
make install
mkdir /etc/Wireless/RT2870STA
cp /etc/Wireless/RT3070STA/RT3070STA.dat /etc/Wireless/RT2870STA/RT2870STA.dat
rmmod rt3070sta
modprobe rt3070sta

```
also by running:
```
nano /etc/modprobe.d/blacklist.conf
```
added these lines in the end of opened file:
```
blacklist rt2x00usb
blacklist rt2x00lib
blacklist rt2800usb
blacklist rt2870sta

```
be careful to enter exact characters. Saved by pressing Ctrl+O and then Ctrl+X.
ran:
```
nano /etc/Wireless/RT2870STA/RT2870STA.dat
```
and it opened a big file with a lot of setting for the adapter. I changed some of them, because iwconfig and ifconfig in USE 10.04 can not enable WEP encryption by default And I don't now why! So I edited this file to make mentioned settings by driver on start-up.
So find and change values in the opened file like below:
```
NetworkType=Adhoc
AuthMode=OPEN
EncrypType=WEP
Key1Type=1
Key1Str="my-password"

```
You should not add the above lines, You must find them one by one and change the value in front of '=' sign to the mentioned value. Ok?
Then ran:
```
nano /etc/network/interfaces
```
and entered lines below at the end of opened file:
```
auto ra0
iface ra0 inet static
wireless-mode ad-hoc
wireless-essid my-essid
wireless-key s:my-password
wireless-channel 11
address 192.168.0.2
netmask 255.255.255.0

```
Then saved by pressing Ctrl+O and then Ctrl+X.
Finally just plugged in my USB dangle.
It started to blink after a second. I entered **iwconfig** and it was like this:
```
iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ra0       Ralink STA  ESSID:"aario-server-10"  Nickname:"RT2870STA"
          Mode:Ad-Hoc  Frequency=2.462 GHz  Cell: B6:12:23:9E:BB:3A   
          Bit Rate=54 Mb/s   
          RTS thr:off   Fragment thr:off
          Encryption key:XXXX-XXXX-XXXX-XXXX-XXXX-XXXX-XX
          Link Quality=100/100  Signal level:-43 dBm  Noise level:-115 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```
Those XXXX things was hexadecimal converted value of my password (Something like 4A6C-...).
And it showed me that Connection is on and in Ad-Hoc mode with a cell ID and and also encryption is on too.
I then successfully connected to this Ad-Hoc created connection using only network manager applet in gnome and from my laptop. For the Encryption I selected WEP 128-bit mode there and entered my-password.
Hope this helps;)
------------------------------------
P.S.: I never created an Ad-Hoc connection based on WPA encryption using this dangle. If anyone knows how to do that (Using CLI, network-manager, wpa_supplicant), please let me know.

---

