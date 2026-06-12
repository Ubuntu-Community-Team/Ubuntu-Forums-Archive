---
title: "dwl-g650 wireless card won't accept encryption key"
date: 2009-11-07
forum: Networking &amp; Wireless
---

### Post by Gforce20 on 2009-11-07
I have an old (1999) laptop that I installed Ubuntu 9.10 Server on; I got my DWL-G650 card to work with unetbootin (Madwifi is [recommended]("https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsDlink") but I couldn't find a way to get it without Internet access). The only problem is that it won't accept "iwconfig wlan0 enc s:mynetworkkey" and gives me this error message:
```
Error for wireless request "Set Encode" (8b2a) :
SET failed on device wlan0 ; invalid argument
```Setting essid and other parameters works just fine, and running "iwconfig wlan0" shows that it has indeed accepted these parameters. How can I get encryption to work? I've also tried putting [1] after "enc", quoting the network key, and doing various other tricks to get it to accept the key, but nothing helps. I know it's capable of using encryption because I managed to do it with Windows and Ubuntu 8.04 desktop.

---

### Post by pytheas22 on 2009-11-08
Try:
```

iwconfig wlan0 key s:mynetworkkey
```

I'm not familiar with the "enc" argument.  I've always used "key" and it's worked.  Also, you only need the s: part for certain kinds of WEP keys (namely ASCII ones, as opposed to hex, which are more common), so make sure you're doing that properly; for more information, this [tutorial]("http://ubuntuforums.org/showthread.php?t=571188") is very helpful.

---

### Post by Gforce20 on 2009-11-08
> **pytheas22 said:**
> Try:
```

iwconfig wlan0 key s:mynetworkkey
```I'm not familiar with the "enc" argument.  I've always used "key" and it's worked.
Sorry, that was a typo. I used the "key" argument originally.
> Also, you only need the s: part for certain kinds of WEP keys (namely ASCII ones, as opposed to hex, which are more common), so make sure you're doing that properly; for more information, this [tutorial]("http://ubuntuforums.org/showthread.php?t=571188") is very helpful.My router's key is ASCII; I'll check out that tutorial, though. Thanks for the tips.

Edit: The tutorial was exactly what I needed! Thanks for the help. I didn't know that the "key s:networkkey" was only for WEP; I needed to use wpa_supplicant instead.

---

