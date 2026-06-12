---
title: "WPA2-PSK does not work with Intel 5100 AGN Card."
date: 2010-06-29
forum: Networking &amp; Wireless
---

### Post by sieger007 on 2010-06-29
I used KwifiManager - turned out to be a primitive piece and I beleive does not support  WPA2
tried WiCD and it throws  up with too many errors.
iwlist scan will show networks and I can connect to unsecured ones.

I tried to put info into the /etc/network/interfaces ( see the # commented info - I used Wext and Iwlang and none of them work )

[COLOR="SeaGreen"]I[B]nterface       Chipset         Driver

wlan0           Intel 4965/5xxx iwlagn - [phy0]
                                (monitor mode enabled on mon7)[/B]
[/COLOR]

Analysis  : ( Not sure If I am right - you tell me ) 
So airmon tells me that iwlagn is the driver whereas wext is what wpa_supplicant mentions. Now is wext a generic name that will include iwlagn below it or both are at the same level , which means it could be a hopeless excersie getting iwlagn driver run on Intel 51000 agn as this iwlagn is not mentioned in list of drivers supported OR I can hope to get wext running instead of iwlagn and that in turn will work..? If that is the cause- that is if in fact if it is only then - how do I unload iwlagn and load wext .


**_/etc/network/interfaces _**
[COLOR="Green"]auto lo
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
# wpa-driver iwlagn /* and yes I tried wext here too. No good. */
# wpa-ssid biggassbbq1
# wpa-ap-scan 1
# wpa-proto RSN
# wpa-pairwise CCMP
# wpa-group CCMP
# wpa-key-mgmt WPA-PSK
# wpa-psk 0c2895ae8a31a76ef800adcae1f6246a706b412e033efc49486647f148fe926a[/COLOR]

**_wpa_supplicant -d<driver> etc -c<filename>-dd  etc command ( run in verbose mode ) output _**

[COLOR="Green"]                                             
Initializing interface 'wlan0' conf '/etc/wpa_supplicant/wpa_supplicant.conf' driver 'wext' ctrl_interface 'N/A' bridge 'N/A'
Configuration file '/etc/wpa_supplicant/wpa_supplicant.conf' -> '/etc/wpa_supplicant/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant/wpa_supplicant.conf'
ctrl_interface='/var/run/wpa_supplicant'
Line: 4 - start of a new network block
ssid - hexdump_ascii(len=6):
     7a 73 75 7a 73 61                                 <SSIDName>
scan_ssid=1 (0x1)
proto: 0x3
key_mgmt: 0x2
pairwise: 0x10
group: 0x10
PSK - hexdump(len=32): [REMOVED]
Priority group 0
   id=0 ssid='zsuzsa'
Initializing interface (2) 'wlan0'
SIOCGIWRANGE: WE(compiled)=22 WE(source)=21 enc_capa=0xf
  capabilities: key_mgmt 0xf enc 0xf flags 0x0
WEXT: Operstate: linkmode=1, operstate=5
Own MAC address: 00:1e:65:83:7a:4a
wpa_driver_wext_set_wpa
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=1 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=2 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=3 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_countermeasures
wpa_driver_wext_set_drop_unencrypted
RSN: flushing PMKID list in the driver
Setting scan request: 0 sec 100000 usec
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: KEY_RX entering state NO_KEY_RECEIVE
EAPOL: SUPP_BE entering state INITIALIZE
EAP: EAP entering state DISABLED
Using existing control interface directory.
Added interface wlan0
Daemonize..
root@bt:/# iwpriv wlan0 set Authmode=WPA2PAK
iwpriv wlan0 set Authmode=WPA2PAK
wlan0     no private ioctls.

root@bt:/# . hq mount
[/COLOR]

and when I restart  /etc/init.d/networking I get wlan0 no DHCP offers received. Sleeping ....

ANY IDEA folks ..how to get this running
Thanks many 
Sam

---

### Post by geofurtado on 2010-07-11
I turn off the card with the physical switch on my laptop, the turn it on after booting.  This is the only way that I can get it to work.

---

### Post by sieger007 on 2010-07-11
[COLOR="Blue"]I am using BT4. BT4 is modified Kbuntu.
It worked for me after I just specified the key and let it choose the encryption type in the .conf file.Earlier I was asking in to connection via WPA2-PSK AES which the router, I knew, had and which connected perfectly via the W2K Partition. A boot time message related to AES was noticed, can recollect what it was but I figured that AES is not working as it should on this OS. I am probably connecting via WPA-PSK TKIP[/COLOR]

---

### Post by plainsane on 2010-08-01
i have it working on lucid.

the trick for me was stopping network-manager first
```
sudo /etc/init.d/network-manager stop
```
then associating the nic to the ap with wpa_supplicant or wicd.

hope this helps.

---

