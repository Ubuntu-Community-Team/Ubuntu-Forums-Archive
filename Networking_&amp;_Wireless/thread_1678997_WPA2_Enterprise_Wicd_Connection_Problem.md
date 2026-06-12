---
title: "WPA2 Enterprise Wicd Connection Problem"
date: 2011-01-31
forum: Networking &amp; Wireless
---

### Post by rks171 on 2011-01-31
Hi, I'm having problems getting connected to my office network with my laptop, loaded with Ubuntu 10.10.  I uninstalled Network Manager and tried Wicd after a search for a solution, but I'm still getting connection errors.  The network setup instructions say:

```
[FONT=&quot] SSID (aka, Network Name):      COE-WPA    * note that the SSID is case sensitive and must be all lower case
Network Type:      Infrastructure
Security:      WPA2-Enterprise (not WPA2-PSK)
Encryption:      AES
Authentication Type:      EAP-TTLS
Authentication Protocol:      PAP
Certificate Authority:      Thawte Premium Server CA
Authentication Server:      engrrad.ecs.psu.edu [/FONT]
```In Wicd, I go into properties for the network and select 'use encryption', 'WPA 1/2 (Passphrase)', and enter my password.  When I try to connect, I get the error "Connection Failed: Bad Password".  However, my password is definately right.  My dmesg displays this after the connection attempt:

```
[ 1212.570053] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1212.762770] r8169 0000:09:00.0: eth0: link down
[ 1212.762770] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 1213.081307] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1251.311310] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1251.532843] r8169 0000:09:00.0: eth0: link down
[ 1251.533572] ADDRCONF(NETDEV_UP): eth0: link is not ready
```Wifi works fine on my home network, which uses WPA encryption.  Any ideas why I can't get connected?

---

### Post by gordintoronto on 2011-01-31
You missed this:
"note that the SSID is case sensitive and must be all lower case."

I don't supposed you can change the SSID...

---

### Post by rks171 on 2011-01-31
Hmm, I'm looking into that, but so far I can't see how I could do that.  However, there is another network that I can see, which doesn't seem to suffer that same problem.  Supposedly, according to connection instructions, I should just be able to open my laptop and connect right to the psu network; however, when I try, I get the same 'bad password' error.  This network correctly shows up in all lowercase letters.

```
SSID (aka, Network Name):       psu    *note that the SSID is case sensitive and must be all lower case
Network Type:       Infrastructure
Security:       WPA2-Enterprise (not WPA2-PSK)
Encryption:       AES
Authentication Type:       EAP-TTLS
Authentication Protocol:       PAP
Certificate Authority:       Thawte Premium Server CA
Authentication Server:       radius1.aset.psu.edu
```

---

### Post by perspectoff on 2011-01-31
May or not may work, but try using a hex key instead of a passphrase. I have some routers that only like hex keys.

If you can't find out the hex key from the router, there are online tools that can translate an ASCII text passphrase to hex.

I wouldn't suppose that you would get any type of dialogue at all if the SSID weren't recogised (from case problems with the name).

---

### Post by rks171 on 2011-01-31
Isn't hex key for WEP encryption?

---

### Post by perspectoff on 2011-01-31
> **rks171 said:**
> Isn't hex key for WEP encryption?

Can be, but WPA2 doesn't accept hex? Ok, I see your point. WPA2 has a 63 character limit, whereas hex keys can be 64 characters. I hadn't realized there was a difference.

So using a hex key translation probably won't work, then, with WPA2, since it will be too many characters.

I'll look further at the wpa-supplicant instructions at:

[http://hostap.epitest.fi/wpa_supplicant/](http://hostap.epitest.fi/wpa_supplicant/)

---

