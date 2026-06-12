---
title: "Motorola WR850G and Ubuntu connection"
date: 2009-03-20
forum: Networking &amp; Wireless
---

### Post by 3eddy on 2009-03-20
I just received my Dell Mini 9. It is loaded with Ubuntu 8.04.1. I have a Motorola WR850G wireless router.

I can get the computer to see the network. It seems as though it is connected to it but when i try to get online it will not go out onto the internet. I have tried reconfiguring the router and reinstalling the netwrok on the computer, several times, but with no improvement. It is also strnage because it will show the signal strength as 100% but then sometimes show the network at 20% or 40% even though i am sitting right next to the wireless rotuer. Any suggestions?

---

### Post by MaindotC on 2009-03-20
Couple of things - from now on please replace the word "router" with the phrase "access point".  Also, the transmissions standards of 802.11a/b/g are open standards and are not dependent on this issue unless you think there could be an electrical problem and you'll save time exchanging the AP than troubleshooting it.  If you are trying to connect to an open, unencrypted wireless network that does not have any security restrictions on it, the place you would need to troubleshoot is your management of settings in Ubuntu.  If you are connected to the AP's wireless network, post the output of:
```

iwconfig
ifconfig

```

---

### Post by 3eddy on 2009-03-20
strAlan,

Thanks. unfortunately I am not connected to the AP at this moment. I will check when I can connect. No electrical problem, my Windows Xp laptop connects with no problem. I am connecting to an open 128 bit encrypted

---

### Post by MaindotC on 2009-03-20
What is 128 bit encrypted?  Are you using WPA, WPA2, or WEP?

---

