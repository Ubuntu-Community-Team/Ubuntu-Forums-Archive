---
title: "Need Some Help With Wireless"
date: 2009-09-18
forum: Networking &amp; Wireless
---

### Post by Vampyer on 2009-09-18
Hey guys,

I but Ubuntu (Intrepid) on my IBM X60s last night but I cant seem to connect to my wireless network for some reason...

I'm using the build-in wifi that comes with the X60s. It finds my network and gives me the option to input the WEP details and stuff but after I do it, it just sends me right back to that screen. It's like one big circle :(

I've double checked my WEP key and have even changed it from a key to a passphrase, changed the SSID and enabled more IPs.

If anyone could help me out, that would be awesome... plus there's a ham and cheese sandwich in it for you ;)

---

### Post by x22 on 2009-09-18
2 suggestions--
number one: try with a wired connection to ensure the
router is setup OK
number two: try manually setting the wireless somewhat
like this

ifconfig wlan0 up
iwconfig wlan0 essid 2236a
iwconfig wlan0 channel 40
iwconfig wlan0 mode managed
iwconfig wlan0 key 1234567890
iwconfig wlan0 key open
dhclient wlan0 2>&1>/dev/null

changing parameters to suit

---

### Post by Vampyer on 2009-09-18
A Wired connection works fine, I took the time to install some updates and wicd because I thought there might have been a problem with network manager but I still can't connect :(

And I'm not sure what you mean by:

ifconfig wlan0 up <<< I dont know what this means :(
iwconfig wlan0 essid 2236a   <<< I assume that's the SSID, in my case "Frank" :)
iwconfig wlan0 channel 40
iwconfig wlan0 mode managed <<< I don't know what this means either :(
iwconfig wlan0 key 1234567890
iwconfig wlan0 key open
dhclient wlan0 2>&1>/dev/null <<< Nor this :(

Would I have to re-enter this stuff everytime I wanted to connect to the Internet or does it save it to a .conf file somewhere?

thanks

---

