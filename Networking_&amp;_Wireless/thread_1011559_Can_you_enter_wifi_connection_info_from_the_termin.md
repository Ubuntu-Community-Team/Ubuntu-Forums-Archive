---
title: "Can you enter wifi connection info from the terminal?"
date: 2008-12-14
forum: Networking &amp; Wireless
---

### Post by Howinlinux on 2008-12-14
I have a D-Link G132 usb wifi card, whose connectivity has regressed when upgrading from Gutsy to Hardy.  I have gotten the card to the point that it sees available networks in both Network Manager, and Wicd.  It will not handle the WPA-PSK TKIP key.  I want to see if there is a way that I can pass those credentials to the router via the terminal?  If so, what file(s)/start-up commands would I use to automate that connection with a Desktop "launcher" or start-up option.

---

### Post by kevdog on 2008-12-15
See the link in my signature.

---

### Post by Howinlinux on 2008-12-15
Just finished my first read through on your post and I am impressed! Well written guide and I think I may get somewhere with this.  I will repost my findings in a few minutes.  If all works well I will reference this as a fix for the current lack of support via manufacturers/linux distros of USB wireless adapters.

Oh yeah, btw, I like the "better off dead" quote :D

---

### Post by Howinlinux on 2008-12-15
I was able to follow the tutorial but I could not connect.  Here is the command I typed and what was returned:

postitz@postitz-desktop:~$ sudo wpa_supplicant -Dndiswrapper -iwlan0- -c/etc/wpa_supplicant.conf -dd

Initializing interface 'wlan0-' conf '/etc/wpa_supplicant.conf' driver 'ndiswrapper' ctrl_interface 'N/A' bridge 'N/A'
Configuration file '/etc/wpa_supplicant.conf' -> '/etc/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant.conf'
ap_scan=1
ctrl_interface='/var/run/wpa_supplicant'
Line: 4 - start of a new network block
ssid - hexdump_ascii(len=6):
     64 64 2d 77 72 74                                 dd-wrt          
scan_ssid=0 (0x0)
proto: 0x1
key_mgmt: 0x2
PSK (ASCII passphrase) - hexdump_ascii(len=8): [REMOVED]
pairwise: 0x8
group: 0x8
PSK (from passphrase) - hexdump(len=32): [REMOVED]
Priority group 0
   id=0 ssid='dd-wrt'
Initializing interface (2) 'wlan0-'
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: KEY_RX entering state NO_KEY_RECEIVE
EAPOL: SUPP_BE entering state INITIALIZE
EAP: EAP entering state DISABLED
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
ioctl[SIOCSIWPMKSA]: No such device
ioctl[SIOCSIWMODE]: No such device
Could not configure driver to use managed mode
ioctl[SIOCGIFFLAGS]: No such device
Could not set interface 'wlan0-' UP
ioctl[SIOCGIWRANGE]: No such device
WEXT: Operstate: linkmode=1, operstate=5
ioctl[SIOCGIFINDEX]: No such device
Failed to add interface wlan0-
State: DISCONNECTED -> DISCONNECTED
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
ioctl[SIOCSIWENCODEEXT]: No such device
Driver did not support SIOCSIWENCODEEXT, trying SIOCSIWENCODE
ioctl[SIOCSIWENCODE]: No such device
wpa_driver_wext_set_key: alg=0 key_idx=1 set_tx=0 seq_len=0 key_len=0
ioctl[SIOCSIWENCODEEXT]: No such device
Driver did not support SIOCSIWENCODEEXT, trying SIOCSIWENCODE
ioctl[SIOCSIWENCODE]: No such device
wpa_driver_wext_set_key: alg=0 key_idx=2 set_tx=0 seq_len=0 key_len=0
ioctl[SIOCSIWENCODEEXT]: No such device
Driver did not support SIOCSIWENCODEEXT, trying SIOCSIWENCODE
ioctl[SIOCSIWENCODE]: No such device
wpa_driver_wext_set_key: alg=0 key_idx=3 set_tx=0 seq_len=0 key_len=0
ioctl[SIOCSIWENCODEEXT]: No such device
Driver did not support SIOCSIWENCODEEXT, trying SIOCSIWENCODE
ioctl[SIOCSIWENCODE]: No such device
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
Failed to disable WPA in the driver.
No keys have been configured - skip key clearing
Cancelling scan request
Cancelling authentication timeout
ioctl[SIOCSIWAP]: No such device
WEXT: Operstate: linkmode=0, operstate=6
ioctl[SIOCGIFFLAGS]: No such device

Any suggestions would be great

---

### Post by kevdog on 2008-12-15
Read the guide carefully

-Dndiswrapper is not valid

use
-Dwext

---

### Post by Howinlinux on 2008-12-15
Not exactly a "responsive" answer considering that the guide has critical type-o's and stuff.  I think a better answer would be an accurate analysis of the output.  Keep in mind, not every1 with this problem is linux savvy.  I am back to square 1 trying to analyze the output....

---

### Post by cdtech on 2008-12-15
I haven't tried this yet but looks like it would help it say's it supports WPA-PSK.
[http://www.linuxant.com/driverloader/index.php#about](http://www.linuxant.com/driverloader/index.php#about)

Let me know....

---

