---
title: "Wireless available before login?"
date: 2009-01-30
forum: Networking &amp; Wireless
---

### Post by Another Monkey on 2009-01-30
I have an old laptop that I bought an Edimax card for and run 8.10 on. I would like to be able to remote login over XDMCP from this laptop, but I cannot as wireless is not available from boot.

At boot I see various warnings flash past "WLAN1: error fetching interface information.  Device not found" and so on (I wish I could get a log of the boot messages, but that seems to be impossible).  Firestarter also fails on boot.

All I appear to have in "/etc/inferfaces/network" file is
```
auto lo
iface lo inet loopback
```
And this confuses me as everything is configured correctly in NetworkManager; I thought it would have been in sync with this file.

How do I get my wireless card functional from boot?  Is this even possible?

---

### Post by Another Monkey on 2009-01-30
Hmm...I think this link may be the ticket
[http://dilationtime.wordpress.com/2008/06/07/linux-automating-wireless-connection/]("http://dilationtime.wordpress.com/2008/06/07/linux-automating-wireless-connection/")

If that works I'll say so and try to mark this thread as "solved".

---

### Post by Another Monkey on 2009-01-31
I followed the instructions in that link to try and get wireless operational from boot - no dice.

When trying the reset it seems to work, but I have no connection.  When I switch to DHCP I can see it failing to connect.

I am using an Edimax PCMCIA card on a laptop - is it not possible to have these working from boot?  My "/etc/network/interfaces" now looks like this
```
auto lo
iface lo inet loopback

auto wlan1
#iface wlan1 inet dhcp
iface wlan1 inet static
address 192.168.32.3
netmask 255.255.255.0
gateway 192.168.32.128
broadcast 192.168.32.255
#wireless-mode managed
#wireless-essid default
wpa-driver wext
wpa-ssid mynet
wpa-ap-scan 1
wpa-proto WPA
wpa-pairwise CCMP
wpa-group CCMP
wpa-key-mgmt WPA-PSK
wpa-psk my-pass-key-in-here
```

Have I done something wrong?

Also, "System Setting" for my wireless keeps re-setting itself in "Network Manager".  I take it that means I cannot have wireless from boot?

---

### Post by Another Monkey on 2009-01-31
Solved!

Seems it is Network Manager just being flakey.  What I had to do was uncheck "connect automatically" and "system setting" for eth0.  It then asked for authentication.

After I had given my password it allowed me to apply "System setting" for wlan1 and that held.

So it seems that NM is not always doing what you ask and the answer is to just keep on trying until some change makes it realise.

---

### Post by excbuntu on 2009-03-01
i have the same problem. 

for me, unchecking "connect automatically" and "system setting" on eth0 does not prompt for authentication. eth0's tick for connect automatically dissappears but the tick for system setting persists. wlan's tick for connect automatically persists but the tick for system setting does not.

suggestions?

---

### Post by excbuntu on 2009-03-01
you know what...

is there a config file of some sort that we could edit and thereby force the ticking? it just doesn't stick!

---

