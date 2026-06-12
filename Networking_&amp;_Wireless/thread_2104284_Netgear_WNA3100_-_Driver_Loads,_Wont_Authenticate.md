---
title: "Netgear WNA3100 - Driver Loads, Wont Authenticate"
date: 2013-01-12
forum: Networking &amp; Wireless
---

### Post by Fyfey on 2013-01-12
Hi there!

I'm new to Ubuntu and have just installed 12.10 32-bit.

I have a Netgear WNA3100 and have done some searching on how to get it to work. I downloaded and built ndiswrapper 1.58rc1 as I was getting a problem with the gui tool not finding the module.
I then downloaded the bcmwlhigh5 drivers and installed them using ndiswrapper.

I can list and view my network, but it wont authenticate, it continually brings up the the psk entry box. Looking in the syslog, it seems to be failing at authentication
tail -n 50 /var/log/syslog | grep wlan3:
```
Jan 12 20:15:03 ubuntu wpa_supplicant[1150]: wlan3: Trying to associate with a0:21:b7:c9:6e:05 (SSID='virginmedia3327840' freq=2462 MHz)
Jan 12 20:15:03 ubuntu NetworkManager[982]: <info> (wlan3): supplicant interface state: scanning -> associating
Jan 12 20:15:03 ubuntu wpa_supplicant[1150]: wlan3: Associated with a0:21:b7:c9:6e:05
Jan 12 20:15:03 ubuntu NetworkManager[982]: <info> (wlan3): supplicant interface state: associating -> 4-way handshake
Jan 12 20:15:13 ubuntu wpa_supplicant[1150]: wlan3: Authentication with a0:21:b7:c9:6e:05 timed out.
Jan 12 20:15:13 ubuntu wpa_supplicant[1150]: wlan3: CTRL-EVENT-DISCONNECTED bssid=00:00:00:00:00:00 reason=0
Jan 12 20:15:13 ubuntu NetworkManager[982]: <info> (wlan3): supplicant interface state: 4-way handshake -> disconnected
Jan 12 20:15:14 ubuntu NetworkManager[982]: <info> (wlan3): supplicant interface state: disconnected -> scanning
Jan 12 20:15:18 ubuntu NetworkManager[982]: <warn> Activation (wlan3/wireless): association took too long.
Jan 12 20:15:18 ubuntu NetworkManager[982]: <info> (wlan3): device state change: config -> need-auth (reason 'none') [50 60 0]
Jan 12 20:15:18 ubuntu NetworkManager[982]: <warn> Activation (wlan3/wireless): asking for new secrets
Jan 12 20:15:24 ubuntu NetworkManager[982]: <info> (wlan3): supplicant interface state: scanning -> inactive

```

The stupid thing is, I can create a hotspot on my Android phone and it CAN authenticate and connect to it?

I've tried changing the various WPA2 settings in my router with no avail.

Any pointers in to where to try next is greatly apreciated,

Regards,

Stu

---

