---
title: "Strange Wireless Problem!"
date: 2011-11-19
forum: Networking &amp; Wireless
---

### Post by x-D on 2011-11-19
Hello, I've been lately having a strange wireless problem in Ubuntu 11.10 Ocelot...

Basically I got a wna3100 Netgear Wireless Adapter. To my dismay I found that it was not supported on Linux (apparently Netgear do not support it). Anyway, ndiswrapper did the job and I found the appropriate .sys and .inf files for download here on the Ubuntu forums, that someone had managed to salvage out of their XP machine. I opened up the ndiswrapper GUI as normal, and located the directory (Home Folder) where the .inf and .sys files were, and selected the .inf, it installed with no problems and came back as 'installed - hardware is present'. I added ndiswrapper to my /etc/modules file in nano and saved this. I get the regular wireless 'panel' up at the top and get all my wireless networks come up. When I click on a Network however, it asks for the password, which I enter correctly, and I have checked this so many times, and every time I enter the passcode in it looks like it's loading the wireless for a while and loops back to asking for the password again. As I say, I've triple checked the password is correct, I don't know what to do here.

Any help is greatly appreciated,

x-D :guitar:

---

### Post by x-D on 2011-11-19
```
xxxx@xxxxx$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan1     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:300 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

---

### Post by scradock on 2011-11-19
> **x-D said:**
> Hello, I've been lately having a strange wireless problem in Ubuntu 11.10 Ocelot...

Basically I got a wna3100 Netgear Wireless Adapter. To my dismay I found that it was not supported on Linux (apparently Netgear do not support it). Anyway, ndiswrapper did the job and I found the appropriate .sys and .inf files for download here on the Ubuntu forums, that someone had managed to salvage out of their XP machine. I opened up the ndiswrapper GUI as normal, and located the directory (Home Folder) where the .inf and .sys files were, and selected the .inf, it installed with no problems and came back as 'installed - hardware is present'. I added ndiswrapper to my /etc/modules file in nano and saved this. I get the regular wireless 'panel' up at the top and get all my wireless networks come up. When I click on a Network however, it asks for the password, which I enter correctly, and I have checked this so many times, and every time I enter the passcode in it looks like it's loading the wireless for a while and loops back to asking for the password again. As I say, I've triple checked the password is correct, I don't know what to do here.

Any help is greatly appreciated,

x-D :guitar:
You should check the Edit Connections dialog. Every time I change to a new install or a new network I find the Wireless Security setting defaults to "Open", whereas my network only associates correctly if it's on "Shared Key". I may have to set that a couple of times until it works correctly - the symptoms you describe of the password prompt coming up repeatedly then goes away and it connects perfectly every time.

---

### Post by x-D on 2011-11-19
> **scradock said:**
> You should check the Edit Connections dialog. Every time I change to a new install or a new network I find the Wireless Security setting defaults to "Open", whereas my network only associates correctly if it's on "Shared Key". I may have to set that a couple of times until it works correctly - the symptoms you describe of the password prompt coming up repeatedly then goes away and it connects perfectly every time.

Hey thanks for the reply scradock. I have gone through as you described to the wireless network settings, and under security, it's already on WPA&WPA2 Personal

---

### Post by x-D on 2011-11-19
Also, it's working with other networks perfectly (both of which are open).

---

### Post by scradock on 2011-11-19
> **x-D said:**
> Also, it's working with other networks perfectly (both of which are open).
OK - sorry that didn't help. I use WEP, so I can't help with WPA settings....

---

