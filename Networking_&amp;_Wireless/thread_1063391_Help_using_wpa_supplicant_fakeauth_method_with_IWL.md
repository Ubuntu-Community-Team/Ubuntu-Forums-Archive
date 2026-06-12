---
title: "Help using wpa_supplicant fakeauth method with IWL4965!"
date: 2009-02-07
forum: Networking &amp; Wireless
---

### Post by entropy89 on 2009-02-07
Alright, after many countless hours scanning through forums and posts, I've finally got my drivers for my iwl4965 all updated and working.

I can :
```

$ sudo airmon-ng start wlan0

Interface	Chipset		Driver

wlan0		Unknown 	iwlagn - [phy0]
				(monitor mode enabled on mon0)

$ sudo aireplay-ng -9 -a 00:1c:10:8f:xx:xx mon0
19:25:46  Waiting for beacon frame (BSSID: 00:1C:10:8F:xx:xx) on channel 6
19:25:46  Trying broadcast probe requests...
19:25:46  Injection is working!
19:25:48  Found 1 AP 

19:25:48  Trying directed probe requests...
19:25:48  00:1C:10:8F:xx:xx - channel: 6 - 'Network_name'
19:25:49  Ping (min/avg/max): 1.516ms/52.678ms/71.944ms Power: -61.23
19:25:49  30/30: 100%

```

So far so good, so because I have the iwl4965, and fakeauth is currently broken. I read I was to use wpa_supplicant to fakeauth with the ap, and then start to read packets and inject. I'm having a hard time authenticating with the AP....

```

network={
        ssid="Network_name"
        key_mgmt=NONE
        wep_key0="fakekey"
}

```
```

$ sudo wpa_supplicant -c ~/conf.conf -D wext -i wlan0 -dd
....
....
....
Try to find non-WPA AP
6: 00:1c:10:8f:xx:xx ssid='Network_name' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   selected non-WPA AP 00:1c:10:8f:xx:xx ssid='Network_name'
Trying to associate with 00:1c:10:8f:xx:xx (SSID='Network_name' freq=2437 MHz)
Cancelling scan request
WPA: clearing own WPA/RSN IE
Automatic auth_alg selection: 0x1
WPA: clearing AP WPA IE
WPA: clearing AP RSN IE
WPA: clearing own WPA/RSN IE
No keys have been configured - skip key clearing

```

Or without -dd

```

$ sudo wpa_supplicant -c ~/conf.conf -D wext -i wlan0
CTRL-EVENT-SCAN-RESULTS 
CTRL-EVENT-SCAN-RESULTS 
Trying to associate with 00:1c:10:8f:xx:xx (SSID='Network_name' freq=2437 MHz)
ioctl[SIOCSIWENCODEEXT]: Invalid argument
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Authentication with 00:00:00:00:00:00 timed out.
CTRL-EVENT-SCAN-RESULTS 
Trying to associate with 00:1c:10:8f:xx:xx (SSID='Network_name' freq=2437 MHz)
ioctl[SIOCSIWENCODEEXT]: Invalid argument
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys

```

If I need to post more of the wpa_supplicant output, let me know, I grabbed what looks important. Arg!!!

---

