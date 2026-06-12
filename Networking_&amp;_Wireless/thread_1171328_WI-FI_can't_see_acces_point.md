---
title: "WI-FI can't see acces point"
date: 2009-05-27
forum: Networking &amp; Wireless
---

### Post by phpmaster on 2009-05-27
Hello everybody, Sorry for maybe stupid question, but I can't solve this problem.
How can I see available Wi-Fi networks near me, when I type ```
iwlist interface scanning
``` it shows ```
Interface interface doesn't support scanning
```, it seems to be like disabled, thanks

---

### Post by x33a on 2009-05-27
hi, first you'll need to load the drivers for your wifi card.

take a look here:

[https://help.ubuntu.com/community/WifiDocs/WiFiHowTo](https://help.ubuntu.com/community/WifiDocs/WiFiHowTo)

and search the forums, this question has been asked thousands of time.

if you still aren't able to find a solution, then post that problem here.

---

### Post by phpmaster on 2009-05-27
> **x33a said:**
> hi, first you'll need to load the drivers for your wifi card.

take a look here:

[https://help.ubuntu.com/community/WifiDocs/WiFiHowTo](https://help.ubuntu.com/community/WifiDocs/WiFiHowTo)

and search the forums, this question has been asked thousands of time.

if you still aren't able to find a solution, then post that problem here.

I think my drivers are loaded , because when I type

```
iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11a  ESSID:off/any  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:270 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

```

I know that it is a problem of lots of people but I wasn't able to find an answer there

---

### Post by x33a on 2009-05-27
ok, so iwconfig is showing the access point, but iwlist scan isn't?

---

### Post by phpmaster on 2009-05-27
> **x33a said:**
> ok, so iwconfig is showing the access point, but iwlist scan isn't?


Yes, it gave me the error from first post,
Another problem may be that I can't make the WI-FI Led shining, but as I showed the driver is loaded

---

### Post by x33a on 2009-05-27
try it with sudo.

---

### Post by phpmaster on 2009-05-27
> **x33a said:**
> try it with sudo.
Damn , now I am on windows ubuntu - crashed, I'm done for the last one week, I installed ubuntu for 5 or six times, but never crashed, I'm done, i will install it later again

---

