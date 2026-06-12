---
title: "Connection timout errors"
date: 2010-09-29
forum: Networking &amp; Wireless
---

### Post by mlinchits on 2010-09-29
I have the common problem of having to use a wireless connection with a lackluster signal (50%). I therefore get "connection timeout" messages in firefox all the time and the only way to load a complete website id to hit enter a dozen times. I've tried to improve the situation by increasing the timeout values in Kde network settings and fiddling with firefox's about:config, but to no avail. I have a direct connection with proxy disabled. 

I imagine that if there is a way for me to access a site by repeatedly pounding the "enter" key, there has to be a way to force the computer to maintain communication with the server before the connection breaks off.

I did an hour of googling on tuning the linux TCP/IP stack but coundn't find any set of instruction I could comprehend. Could someone help on this?

thanks

---

### Post by kreggz on 2010-09-29
50% signal should be fine.

in Konsole try this

ping google.com 

and leave it for a minute or so check to see if you are you seeing Packet Loss.

see my output:

--- google.com.au ping statistics ---
3 packets transmitted, 0 received, 100% packet loss, time 2000ms

100% packet loss means connecting to Google won't work at all.

You may also want to look at this guide [https://wiki.ubuntu.com/WirelessTroubleshootingGuide](https://wiki.ubuntu.com/WirelessTroubleshootingGuide)

---

### Post by mlinchits on 2010-09-29
Ran ping test 80 times and got 17 percent packet loss. I should mention that I am connected to a university-wide wireless network.

---

### Post by kreggz on 2010-09-29
Ok if you are on a Uni network, that probably rules out the Access Point.

Are you able to issue the command dmesg in a terminal?

There might be a clue there as to what is happening.

---

### Post by mlinchits on 2010-09-29
the output is very long - if youre willing to glance at a portion, it's attached

thanks

---

### Post by kreggz on 2010-09-29
So your constantly associating and disconnecting. 

When did this start occurring? Did you only recently put Linux on your laptop or recently upgrade to a new kernel/release or something?

---

### Post by mlinchits on 2010-09-29
This has occured for as long as I used this wireless connection - which the past 3 weeks or so. I've never had similar problems with wireless before.

I should mention that I have all the latest unpdates installed for 10.04.

---

### Post by kreggz on 2010-09-29
Sounds like your WiFi driver is not working correctly

Follow this procedure and make sure you card is supported then I recommend you create a bug report.

[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

---

