---
title: "Wireless configuration at the command line"
date: 2011-09-29
forum: Networking &amp; Wireless
---

### Post by rubixibuc on 2011-09-29
I've been trying to get my wireless card to connect using iwconfig, but keep getting errors prefixed with " SET failed on device wlan0 ;"

I should have all the drivers because it can connect using network manager.  I just don't always want this running, and need to be able to connect manually.  

Here are the steps I am taking

I am in root

iwconfig wlan0 essid "Network Name"
iwconfig wlan0 key "s:networkey"
dhclient wlan0

I am using WPA

Does anyone know what can be causing this, I read it might not be compatible with WPA, is this the case?

Thanks in advance :-)

---

### Post by TeoBigusGeekus on 2011-09-29
That'd be the correct procedure in the case of WEP.
Using WPA:
```
sudo wpa_passphrase ssid_name_here "password_here" > /etc/wpa_supplicant.conf
sudo wpa_supplicant -B -Dwext -i wlan0 -c /etc/wpa_supplicant.conf
dhcpcd wlan0
```

---

### Post by rubixibuc on 2011-09-29
It didn't work :-(, here is my output to all the commands.  I used a different name for the config file, let me know if that matters.  

> $ sudo wpa_supplicant -Bd -Dwext -i wlan0 -c ./wireless.conf 
Initializing interface 'wlan0' conf './wireless.conf' driver 'wext' ctrl_interface 'N/A' bridge 'N/A'
Configuration file './wireless.conf' -> '/home/rubixibuc/./wireless.conf'
Reading configuration file '/home/rubixibuc/./wireless.conf'
Priority group 0
   id=0 ssid='RinaJasonWireless'
WEXT: cfg80211-based driver detected
SIOCGIWRANGE: WE(compiled)=22 WE(source)=21 enc_capa=0xf
  capabilities: key_mgmt 0xf enc 0xf flags 0x0
netlink: Operstate: linkmode=1, operstate=5
Own MAC address: 00:26:c7:7f:3c:74
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=1 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=2 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=3 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_countermeasures
RSN: flushing PMKID list in the driver
Setting scan request: 0 sec 100000 usec
WPS: UUID based on MAC address - hexdump(len=16): b0 b5 54 09 a0 7f 58 69 a3 8b cb eb 44 f3 03 55
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: Supplicant port status: Unauthorized
EAPOL: KEY_RX entering state NO_KEY_RECEIVE
EAPOL: SUPP_BE entering state INITIALIZE
EAP: EAP entering state DISABLED
EAPOL: Supplicant port status: Unauthorized
EAPOL: Supplicant port status: Unauthorized
Added interface wlan0
Daemonize..Are those unauthorized warnings a problem?

> $ sudo dhcpcd wlan0
err, wlan0: timed out
warn, wlan0: using IPV4LL address 169.254.144.32
rubixibuc@ubuntu:~$ dhcpcd.sh: interface wlan0 has been configured with new IP=169.254.144.32

That shouldn't be my ip.  Let me know if I'm doing anything wrong.  Should I be powering down the device first, or a different driver.  I saw that it timed out, is that a permanent failure, or is there a way I can increase the timeout?

I didn't know how to do the code box, so I just did quotes.

Thank you for helping me :-)

---

### Post by TeoBigusGeekus on 2011-09-29
Try this
```
sudo wpa_supplicant -B -Dwext -i wlan0 -c ./wireless.conf
```
instead of this
```
sudo wpa_supplicant -B[COLOR="Red"]d[/COLOR] -Dwext -i wlan0 -c ./wireless.conf
```
Also, give the dhcpcd command without sudo.
To use the code tags, select the desired text and press the (#) button from the reply toolbar.

---

### Post by rubixibuc on 2011-09-29
Thank you again for you help, it worked but I had to try something else as well.

I disabled network-manager completely, and I ran ```
dhclient wlan0 
``` after running ```
dhcpcd wlan0
```What is the difference between the two? and is there a reason I would have to run both?  It didn't seem like I would need to because I was already assigned a proper IP address, but the web browser wouldn't connect until I ran dhclient.

---

### Post by TeoBigusGeekus on 2011-09-30
I don't know mate.
dhcpcd is enough in Arch; I don't know about Ubuntu, as I don't use it.
I know that dhcpcd is preferred to dhclient, as it is more efficient; my knowledge ends here...
Glad you've made it though.

---

