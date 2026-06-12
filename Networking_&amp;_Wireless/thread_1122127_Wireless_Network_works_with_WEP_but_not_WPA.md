---
title: "Wireless Network works with WEP but not WPA"
date: 2009-04-10
forum: Networking &amp; Wireless
---

### Post by kiff on 2009-04-10
I have two computers running intrepid in my house. Both don't seem to be able to connect to my wireless router when the connection is encrypted with WPA, but can can connect fine with no encryption or WEP encryption. 

I have tried using WPA or WPA2, and both AES and TKIP encryption in my router settings, but nothing seems to work (apart from WEP).

If I boot into XP on my desktop, WPA works fine.

When I try to connect to the WPA encrypted connection, the first green light of the animated network comes on, and the status message is "Attempting to join the wireless network 'x'...", where x is the SSID. Then, after a period of no activity, I am prompted to re-enter the password for the connection. When I do that, the process repeats.

Has anyone else had this issue?

---

### Post by spiderbatdad on 2009-04-10
might help to know what version of Ubuntu you are running and whether you are using any special wifi manager...like madwifi?
Some older network cards cannot be supported for wpa unless a firmware upgrade is applied by via microsoft...for example a snippet from my dmesg log during boot:
```
20.564724] airo(): WPA unsupported (only firmware versions 5.30.17 and greater support WPA.  Detected 5.02.19)

```

---

### Post by kiff on 2009-04-10
Thanks for the feedback, I'll respond one at a time:

> might help to know what version of Ubuntu you are running and whether you are using any special wifi manager...like madwifi?

I'm running Intrepid (8.10) with the standard network manager applet (NetworkManager Applet 0.7.0)

> Some older network cards cannot be supported for wpa unless a firmware upgrade is applied by via microsoft...for example a snippet from my dmesg log during boot:

Good point, but given that I'm able to boot up in XP on the same machine with the same card, I assumed that it wasn't a firmware issue. Happy to be corrected. How would I check the log from which you got that message?

---

### Post by spiderbatdad on 2009-04-11
```
dmesg > ~/Desktop/dmesg.txt
```
better
```
dmesg | grep WPA
```

---

### Post by kiff on 2009-04-17
Thanks for getting back to me so promptly. That doesn't seem to be the issue. Here's the output:

```
[   42.766083] wlan0: encryption modes supported: WEP; TKIP with WPA
```

---

### Post by superprash2003 on 2009-04-17
[https://help.ubuntu.com/community/WifiDocs/WPAHowTo](https://help.ubuntu.com/community/WifiDocs/WPAHowTo)

---

