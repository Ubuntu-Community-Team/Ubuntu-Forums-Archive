---
title: "Wireless Packet Injection and Fake Authitication"
date: 2008-12-15
forum: Networking &amp; Wireless
---

### Post by binaryburnout on 2008-12-15
At this moment I have been playing around with some simple WEP key cracking on my own network. I am using the aircrack-ng tools and I am running into problems when doing the fake authentication attack. After reading a bunch of forums it seems as though the behaviour I am seeing is most common when there is to weak of a signal. It seems as though that is hard to believe though, seeing as I am only 5 feet away from the actual router itself. I am running the following command...
```
aireplay-ng -1 0 -e T0KX1 -a 00:1F:90:EB:37:89 -h 00:04:23:55:93:9C wlan0
```
Where:
[LIST]
[*]-1 = fake authentication
[*]0 = re-association timing in seconds
[*]-e T0KX1 = my ESSID of router
[*]-a 00:1F:90:EB:37:89 = the BSSID of router
[*]-h 00:04:23:55:93:9C = MAC address of associated client
[*]wlan0 = my wireless interface
[/LIST]
And this is the output I get...
```
root@Leetsys:/home/binaryburnout/WEP-WPA# aireplay-ng -1 0 -e T0KX1 -a 00:1F:90:EB:37:89 -h 00:04:23:55:93:9C wlan0
17:55:33  Waiting for beacon frame (BSSID: 00:1F:90:EB:37:89)
17:55:33  Sending Authentication Request
17:55:35  Sending Authentication Request
17:55:37  Sending Authentication Request
17:55:39  Sending Authentication Request
17:55:41  Sending Authentication Request
17:55:43  Sending Authentication Request
17:55:45  Sending Authentication Request
17:55:47  Sending Authentication Request
17:55:49  Sending Authentication Request
17:55:51  Sending Authentication Request
17:55:53  Sending Authentication Request
17:55:55  Sending Authentication Request
17:55:57  Sending Authentication Request
17:55:59  Sending Authentication Request
17:56:01  Sending Authentication Request
17:56:04  Sending Authentication Request
Attack was unsuccessful. Possible reasons:

    * Perhaps MAC address filtering is enabled.
    * Check that the BSSID (-a option) is correct.
    * Try to change the number of packets (-o option).
    * The driver/card doesn't support injection.
    * This attack sometimes fails against some APs.
    * The card is not on the same channel as the AP.
    * You're too far from the AP. Get closer, or lower
      the transmit rate.
```

I have also tried replacing the currently associated clients MAC with my own MAC, but because I am not truly associated with the AP I just receive a DeAuthentication packet and my data set of IV's slows down to a crawl.

Any help, or at the least ideas, would be much appreciated.
~BinaryBurnout

---

### Post by binaryburnout on 2008-12-15
bump :(

---

### Post by jflaker on 2008-12-15
> **binaryburnout said:**
> At this moment I have been playing around with some simple WEP key cracking on my own network. I am using the aircrack-ng tools and I am running into problems when doing the fake authentication attack. After reading a bunch of forums it seems as though the behaviour I am seeing is most common when there is to weak of a signal. It seems as though that is hard to believe though, seeing as I am only 5 feet away from the actual router itself. I am running the following command...
```
aireplay-ng -1 0 -e T0KX1 -a 00:1F:90:EB:37:89 -h 00:04:23:55:93:9C wlan0
```
Where:
[LIST]
[*]-1 = fake authentication
[*]0 = re-association timing in seconds
[*]-e T0KX1 = my ESSID of router
[*]-a 00:1F:90:EB:37:89 = the BSSID of router
[*]-h 00:04:23:55:93:9C = MAC address of associated client
[*]wlan0 = my wireless interface
[/LIST]
And this is the output I get...
```
root@Leetsys:/home/binaryburnout/WEP-WPA# aireplay-ng -1 0 -e T0KX1 -a 00:1F:90:EB:37:89 -h 00:04:23:55:93:9C wlan0
17:55:33  Waiting for beacon frame (BSSID: 00:1F:90:EB:37:89)
17:55:33  Sending Authentication Request
17:55:35  Sending Authentication Request
17:55:37  Sending Authentication Request
17:55:39  Sending Authentication Request
17:55:41  Sending Authentication Request
17:55:43  Sending Authentication Request
17:55:45  Sending Authentication Request
17:55:47  Sending Authentication Request
17:55:49  Sending Authentication Request
17:55:51  Sending Authentication Request
17:55:53  Sending Authentication Request
17:55:55  Sending Authentication Request
17:55:57  Sending Authentication Request
17:55:59  Sending Authentication Request
17:56:01  Sending Authentication Request
17:56:04  Sending Authentication Request
Attack was unsuccessful. Possible reasons:

    * Perhaps MAC address filtering is enabled.
    * Check that the BSSID (-a option) is correct.
    * Try to change the number of packets (-o option).
    * The driver/card doesn't support injection.
    * This attack sometimes fails against some APs.
    * The card is not on the same channel as the AP.
    * You're too far from the AP. Get closer, or lower
      the transmit rate.
```

I have also tried replacing the currently associated clients MAC with my own MAC, but because I am not truly associated with the AP I just receive a DeAuthentication packet and my data set of IV's slows down to a crawl.

Any help, or at the least ideas, would be much appreciated.
~BinaryBurnout

From what I understand of wep or even wpa cracking is that you need to wireless cards...one to inject and one to recieve.

I may be wrong...anyone?

---

### Post by Ghafud on 2008-12-16
Try lowering down the wireless cards bit rate.

iwconfig <interface> rate 1M

Hope it helps.

---

