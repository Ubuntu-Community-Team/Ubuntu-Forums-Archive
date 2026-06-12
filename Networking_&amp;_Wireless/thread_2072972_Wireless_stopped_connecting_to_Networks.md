---
title: "Wireless stopped connecting to Networks"
date: 2012-10-18
forum: Networking &amp; Wireless
---

### Post by jeffpkamp on 2012-10-18
I have been running 12.04 for three days, and the wireless was connecting to wireless networks at boot up right away.  If the computer went to sleep it would not longer be able to connect to any of the networks (it could still see them though), however a restart would fix this. 

I attempted to fix the problem without a restart by rmmod of the wireless (rtlwifi) and modprobe.  Now, I don't even get a wireless connection at start up.  It still shows the wireless networks that are available, but after several minutes scanning it fails to connect.  dmesg during an attempt to connect gives

```
wlan0: selected IBSS BSSID (ADDRESS) based on configured SSID
wlan0: no active IBSS STAs - trying to scan for other IBSS networks with the same SSID (merge)
wlan0: no IPv6 routers present
```

Sorry I can't post the codes because the computer cannot connect to the internet (I don't have access to wired internet at the moment, since I have been running it through another computer on an ad hoc network).  Assistance would be greatly appreciated!

---

### Post by jeffpkamp on 2012-10-19
I took my computer from my work to my home, and it connected to my home wireless internet with out issue right away.  This is odd since there are security settings on my network at home, where as my test network is ad hoc network.  I am not sure if it makes a difference, but my network at home is hosted by computers running windows and using a router, where as the one at work is hosted by a mac.

---

### Post by chili555 on 2012-10-19
> This is odd since there are security settings on my network at home, where as my test network is *ad hoc network*.I believe that's the key. Your readings suggest NM is looking for an ad-hoc network:> selected [COLOR="Red"]IBSS[/COLOR] BSSID (ADDRESS) based on configured SSID[http://en.wikipedia.org/wiki/Independent_Basic_Service_Set](http://en.wikipedia.org/wiki/Independent_Basic_Service_Set)> With 802.11, it is possible to create an *ad-hoc network* of client devices without a controlling access point; the result is called an independent basic service set (*IBSS*).To connect at work, reset Network Manager to Infrastructure. Please see attached.

It may help to *de*-select 'Connect automatically.'

---

### Post by jeffpkamp on 2012-10-19
Hum... After going home and coming back to work my wireless is now working again...  I will have to wait for it to stop working again to try your advice (I am sure it is only a matter of time).  I will let you know if that worked when that happens!  Thanks for the help.

---

