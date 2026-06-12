---
title: "Dual-Band (5Ghz) Wifi not working"
date: 2013-06-14
forum: Networking &amp; Wireless
---

### Post by iNate71 on 2013-06-14
I recently bought a new router (Asus RT-N66U). With my scenario, I have two wifi routers--both with the same SSID. One router is the Asus, the other is a D-Link DIR-655. The Asus supports dual-band, so, in an effort to reduce conflicting noise, I disabled the 2.4Ghz radio on the Asus and kept the 5Ghz broadcasting. Now, I did this change on another computer--I go to get on my computer, and I can't connect to the internet. The D-Link router is in the basement, so I don't get good reception from it. The Asus' SSID was showing to me, but my internet wasn't connecting. I got to another wired computer and changed the Asus to disable the 5Ghz radio, and only keep the 2.4Ghz radio on. After that, I was able to connect to the internet again. I know for a fact my computer and wireless chip support dual-band; I have a **HP Envy Spectre 14** and the wireless chip is the **Intel Corporation Centrino Advanced-N 6235 (rev 24). **The only reason I noticed this was because before yesterday, I had the Asus broadcasting both bands--I assume my laptop just connected to the 2.4Ghz one.

Actual question: [B][I]How do I fix this so I can use the 5Ghz band?
[/I][/B]
Random question: ***How do I know if my computer is using the N-protocol? ***


All help is appreciated!

---

### Post by ahallubuntu on 2013-06-14
~

---

### Post by iNate71 on 2013-06-14
> **ahallubuntu said:**
> Change the SSIDs so they are all different, at least for  now, to avoid confusion.  Give the 5GHZ radio a different SSID than the 2.4GHZ radio.  (If your 2.4GHZ SSID was "MyWiFi" call the 5GHZ one "MyWiFi5".)

If you give the 5GHZ radio a different SSID, then you are certain you are connecting to a 5GHZ radio.

When connected, open a terminal and check the connection rate:

```
iwconfig
```

Your router should also have a status showing connected wireless devices and, perhaps, their connection rates.

Make sure you use WPA2 (probably WPA2 Personal) and AES to get the maximum connection speeds.  Don't bother with WEP, it will limit you to 54MPS plus it's hopelessly insecure.

I don't want to have the Asus pumping out two SSIDs. It messes up other devices. For now, only a few devices in my house have support for 5Ghz, so I think I'll keep it disabled. However, I typed in the command, but it doesn't tell me what protocol I'm using. I wanted to make sure the N-protocol was working on Linux. Plus, I don't know why I can't get my laptop to connect to the 5Ghz band.

EDIT: Trust me, I don't use WEP--everything is locked down and blazing fast. I get 60mbps down. ;)

---

### Post by ahallubuntu on 2013-06-14
~

---

### Post by iNate71 on 2013-06-15
> **ahallubuntu said:**
> How does it "mess up" other devices?  I don't understand.   If you change your 5GHZ SSID to a different name temporarily, then it will show up as an entirely different wireless network, so you'll be sure you aren't connecting to the 2.4GHZ radio.  And it's easy to change your SSIDs back if you want.  I'm not sure why you don't want to try something so simple.

Linux has no trouble with 802.11n.  If iwconfig shows that you are connected at a rate faster than 54Mbps, then you are obviously not connected at G speed (54Mbps max).


I have reasons to not want to change the SSID; first of all, this isn't even helping my issue. I said it doesn't connect to the 5Ghz. I've already tested that. This isn't the board/forum to discuss my network setup--as it isn't Ubuntu related. 

Oh right, duh--that's good at least the N works then.

---

### Post by houstonbofh on 2013-06-15
Turn your 2.4 back off.  Go into network manager and delete the wireless network you have right now for the ssid of your AP.  Now reconnect with only 5ghz running.  You may just have saved a 2.4 only config.  However, if it fails, you need to make sure your nic supports 5ghz under Linux...

---

