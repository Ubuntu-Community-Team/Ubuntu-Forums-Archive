---
title: "attempting wireless via &quot;wpa_supplicant&quot;, but no cigar"
date: 2012-11-23
forum: Networking &amp; Wireless
---

### Post by duodecillian on 2012-11-23
[COLOR="Silver"]I'll try to be as informative about my process as possible, for a couple of reasons, one of them being that if anybody else experiences similar errors to mine, this may help. The other being that I'm unsure of what would be considered important information, so I'd rather put too much information than too little[/COLOR]

After following many tutorials to get my broadcom drivers installed, which I managed. I then attempted to connect to my router.

I was following[this tutorial]("http://http://www.ghacks.net/2009/04/14/connect-to-a-wireless-network-via-command-line/"), until I was supposed to issue this command:

```
iwconfig wlan0 essid NETWORK_ID key WIRELESS_KEY
```

Which gave me:
 ```

Error for wireless request "Set Encode" (8B2A)
```


I then found out, since my network was using WPA, I had to use wpa_supplicant and tried to follow [this tutorial]("http://ubuntuforums.org/showthread.php?t=263136")

After much frustration with it giving me an error telling me:

```
wpa_supplicant: invalid option -- 'w'
```

I eventually got what appeared NOT to be an error message after stopping network manager and wicd.

This was what I got:
```
Trying to associate with 14:d6:4d:30:03:d4 (SSID='Duodecillian' freq = 2312 MHZ)
Associated with 14:d6:4d:30:03:d4
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys 
```

It then also told me my pre shared key was incorrect.

So I went back into my wpa_supplicant.conf and changed what I had used from [this tutorial]("http://ubuntuforums.org/showthread.php?t=263136") into just a string with quotation marks around it.
(```
psk="mypass"
``` )

Rather than that long string of letters that I had before.

That gave me a similar error to the other one, ctrl-event connecting and disconnecting except it didn't tell me my psk was incorrect.

So I started fooling around with the #ap_scan= and managed to get it to stay connected for a while with #ap_scan=1.

Unfortunately, even while it said it was connected, I still couldn't ping google.com

The last errors I seem to be getting are

```
CTLR-EVENT-DISCONNECTED - Disconnect event - remove keys
```


______________________________________________________________________________________________________________________________________
Here's a bit of extra info:

What my /etc/wpa_supplicant.conf looks like:

```
ctrl_interface=/var/run/wpa_supplicant
ap_scan=1

network={
ssid="Duodecillian"
scan_ssid=1
proto=WPA RSN
key_mgmt=WPA-PSK
pairwise=CCMP TKIP
group=CCMP TKIP
psk="Mypasswordinquotes"

```

OS:Crunchbang
Computer is very old, which is pretty much the reason I'm using such an archaic method. I generally don't fool around with terminals too much so I'm a bit of a noob to linux.

Let me know if I'm missing any important info.

I hope I'm being coherent, I'm feeling a tad scatterbrained from fooling around with this all day.

Any help is appreciated. I've been working on this for a couple of days now, but I'm finally completely stumped and need a bit of help.

Thank you in advance : )

---

