---
title: "WPA authentication required by wireless network"
date: 2009-12-20
forum: Networking &amp; Wireless
---

### Post by RunnerBri24 on 2009-12-20
I have Ubuntu 9.04 on a laptop that I have used at school and airports without a password for the network. I am home for Christmas and cannot connect to my network which is WPA protected. When I took off the WPA I connected just fine. When attempting to connect it just sends me back to the Wireless Network Authentication Required even though I have entered the correct password in both hex and ascii.

I fooled around with the wpa_supplicant.conf, but receive the error that the network block did not parse correctly. I am a moderate linux user, Windows on my pc, but am at a total loss with this one. Any advice on something else or something I have tried would be greatly appreciated. I'm willing to post results of iwconfig and such if needed, but I know my driver works.

---

### Post by jetpeach on 2009-12-20
could you post the chipset information for you wireless and the details regarding for wpa setup? ( can use 'sudo iwlist wlan0 essid YOURESSID' (may need to change  wlan0 to adapter name on ur computer). Whether WPA is using AES or TKIP can make a difference...

---

### Post by RunnerBri24 on 2009-12-20
Running that command, "sudo iwlist wlan0 essid Snagglepuss" gave me and error unknown command "essid". I checked out the iwlist --help and found scanning as what I assume is essid. Here is what I think you are looking for.

iwconfig:
wlan0 IEEE 802.11g ESSID: off/any
      Mode:Managed Frequency:2.417 GHz Access Point: Not-Associated
      Bit Rate: 54 Mb/s
      Link Quality:0 Signal level:0 Noise level:0
      Rx invalid nwid:0 Rx invalid crpyt:0 Rx invalid frag:0
      Tx excessive retries:0 Invalid misc:0 Missed beacon:0

sudo iwlist wlan0 scanning:
Cell 03 Address: *valid MAC address of the router here*
        ESSID: "Snagglepuss"
        Protocol:IEEE 802.11g
        Mode:Managed
        Frequency:2.417 GHz (Channel 2)
        Quality:100/100 Signal level:-29 dBm Noise level:-96 dBm
        Encryption Key: on
        Bit Rates:1 MB/s; 2 MB/s; 5.5 MB/s; 11 MB/s; 6 MB/s
                  12 MB/s; 24 MB/s; 36 MB/s; 9 MB/s; 18 MB/s
                  48 MB/s; 54 MB/s;
        Extra:bcn_int=100
        Extra:atim=0
        IE: WPA version 1
            Group Cipher : TKIP
            Pairwise Ciphers (1) : TKIP
            Authentication Suites (1) : PSK

I knew it was TKIP because I tried messing with the wpa_supplicant.conf file. Not sure if I did it right, but here is what that looks like.

wpa_supplicant.conf (/etc):

ctrl_interface=/var/run/wpa_supplicant
ap_scan=1
network={
   ssid="Snagglepuss"
   key_mgmt=WPA-PSK
   proto=WPA
   pairwise=TKIP
   group=TKIP
   psk=3e4......*Hex value that is correct*
   }

then I run this code with this error:
sudo wpa_supplicant -Dwext -iwlan0 -c/etc/wpa_supplicant.conf
ioctl[SIOCSIWPMKSA]: Invalid argument
ioctl[SIOCSIWPMKSA]: Invalid argument
ioctl[SIOCSISCAN]: resource temporarily unavailable
CTRL-EVENT-SCAN-RESULTS
Trying to associate with 00:0F:b5..*MAC of router* (SSID='Snagglepuss' freq=2417)
Associated with 00:00:00:00:00:00
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys

then it just repeats that error until I kill the command. Not sure what is going on, but thanks for the help in advance.

---

