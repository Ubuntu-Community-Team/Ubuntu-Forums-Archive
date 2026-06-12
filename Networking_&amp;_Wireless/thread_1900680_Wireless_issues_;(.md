---
title: "Wireless issues ;("
date: 2011-12-26
forum: Networking &amp; Wireless
---

### Post by Jaykos on 2011-12-26
Hi everyone!
I'm absolutely new to Ubuntu and Linux so please forgive me for my lack of understanding certain codes and advice. I'm able and willing to learn as I go. I took the plunge and installed Ubuntu 11.10 on my IBM Desktop. Everything looks great so far but I have issues with my network adapter. I bought a Netgear WDNA 3100v2 usb adapter and have the resource CD and every piece of literature. Where do I go from here? considering I have no connection to internet and HD was reformatted brand new with Ubuntu 11.10. Any help would be great. Like I said I'm new and I'm a quick learner. 
Thanks!

---

### Post by inobe on 2011-12-26
with your computer turned off, plug in usb adapter.

startup, open terminal, and type in

```
nm-tool
```

highlight everything in the terminal under wlan, copy and paste it here on next post using forum```
code wrap
```

an example of mines

```
dev:~$ nm-tool

NetworkManager Tool



- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath9k
  State:             unavailable
  Default:           no
  HW Address:        5C:D9:98:A3:03:56

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes                                                                                       
    WPA2 Encryption: yes

  Wireless Access Points 

```

with my wireless enabled

```
- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath9k
  State:             disconnected
  Default:           no
  HW Address:        5C:D9:98:A3:03:56

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes                                                                                       
    WPA2 Encryption: yes

  Wireless Access Points 
    home:            Infra, 00:1D:7E:F5:40:1F, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 WPA2



```

---

### Post by Jaykos on 2011-12-28
Got it all figured out man, Thanks!
I'm pretty content with this new OS and looking forward to using it more. I appreciate the community as well. 

Cheers!

---

