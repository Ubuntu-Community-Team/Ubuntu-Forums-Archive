---
title: "Intel 5300AGN config problems"
date: 2010-05-30
forum: Networking &amp; Wireless
---

### Post by unicorn13 on 2010-05-30
Hi all,

I see there are a few people who have had problems with this mini-pcie card, I am also one of these people.

I have this card installed in and IONITX-F-E board, and have been able to get so far as to see my wifi router, but thats it

I have tried many of the 'how-to's' but with no joy as yet.

Has ANYONE got one of these cards working, if so would you be willing to share your config and method with me as a starting point.

The install is minimal Karmic Prior to installing XBMC via xci.sh

Network is WPA2-PSK on a Netgear DGN2000

TIA a frustrated user :)

---

### Post by unicorn13 on 2010-05-31
I found this over on another forum

> drivers for the Intel 5300 have been merged into the kernel (2.6.27), and it's simply a matter of having these options enabled.  Since any distribution that's been released for about 8-9 months now will have a newer kernel than the one listed above, we should be able to put to rest this issue

This may be the case mostly, but they are usually GUI installs that use lan/net managers, but when you use a CLI install as a base starting point where do you look to starting the darn thing.

Have tried the how-to's but must be missing something? What I dunno, the lack or should I say the hard to find infomation on things like this is what puts people off Linux.

Any info welcome

Current Config:-

Firmware was missing/not in correct place copied iwlwifi-5000-2.ucode to correct location and had to add lbm- prefix.

During boot All seems ok

/etc/wpa_supplicant.conf is
```
ctrl_interface=/var/run/wpa_supplicant
ctrl_interface_group=0
ap_scan=1

network={
        ssid="BABYLON5"
        proto=RSN
        key_mgmt=WPA-PSK
        pairwise=CCMP TKIP
        group=CCMP TKIP
        psk=77612d19ce325818d334254a9a1c57ddb2bd48778f5da37c8ccbddd06b354752
}
```


/etc/network/networks is

```
# The Wifi Lan Interface

auto wlan0
iface wlan0 inet dhcp
pre-up wpa_supplicant -B -Dwext -iwlan0 -c/etc/wpa_supplicant.conf
post-down killall -q wpa_supplicant 
```
Regards
Andy

---

### Post by unicorn13 on 2010-06-01
Answering own thread again

Partially Solved :???:

Have now got a link/association with my router, but if inactive browsing for more that a couple of minutes, then browsing fails:-


What I've done so far:-


1. Installed latest *[COLOR=Lime][Intel Pro Wireless 5300agn firmware]("http://www.intellinuxwireless.org/?n=Downloads")[/COLOR]*, on my cli install v2 the firmware was missing which is what was needed.

2. To get passphrase in hex rather than plain text for wpa/wpa2, make sure wpa_supplicant is installed, if not install it, then execute the following command:-

```
**wpa_passphrase** [ ***MY_SSID*** ] [ ***MY_PASSPHRASE*** ] >> /etc/wpa_supplicant.conf 
```2b. edit wpa_supplicat.conf placed in /etc/, new items in red

```
[COLOR=Red]ctrl_interface=/var/run/wpa_supplicant
ctrl_interface_group=0
ap_scan=1[/COLOR]

network={
        ssid="MY_SSID"
[COLOR=Red]        proto=WPA RSN
        key_mgmt=WPA-PSK
        pairwise=CCMP TKIP
        group=CCMP TKIP[/COLOR]
        psk=MY_PASWD_IN_HEX_Result_from_running_wpa_passphrase
}
```3. interfaces located /etc/network/

Commented out Wired Lan entry, left auto lo intact

Added at bottom:-

```
# The Wifi Lan Interface

auto wlan0
iface wlan0 inet dhcp
wireless-essid MY_ESSID
pre-up wpa_supplicant -B -Dwext -iwlan0 -c/etc/wpa_supplicant.conf
post-down killall -q wpa_supplicant 
```As I said above this is only partial solution for me, as it is not holding internet traffic after being inactive, I blieve this is dhcp/routing so will open another thread.

The information is for reference and may or may not work for you, please remember that.

Regards
Andy

Remember whenever you can, help those who ask, if you can. Keep Linux Free and Flowing for the Masses ):P

---

