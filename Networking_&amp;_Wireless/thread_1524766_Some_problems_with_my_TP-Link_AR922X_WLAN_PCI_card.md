---
title: "Some problems with my TP-Link AR922X WLAN PCI card..."
date: 2010-07-05
forum: Networking &amp; Wireless
---

### Post by dtwai on 2010-07-05
I've just got a TP-Link wn-851n PCI WLAN card, and the problem is that ubuntu can search for the network, but I can't join into the network after typing the password. I'm sure that it is correct as m Windows notebook is also using that network.
Taking a look in dmesg, and it start to loop this message after I joined the network.

> [  257.298391] wlan0: direct probe to AP 94:0c:6d:f4:fb:8e (try 1)
[  257.303422] wlan0: direct probe responded
[  257.303429] wlan0: authenticate with AP 94:0c:6d:f4:fb:8e (try 1)
[  257.305298] wlan0: authenticated
[  257.305320] wlan0: associate with AP 94:0c:6d:f4:fb:8e (try 1)
[  257.311939] wlan0: RX AssocResp from 94:0c:6d:f4:fb:8e (capab=0x431 status=0 aid=1)
[  257.311945] wlan0: associated
[  258.852402] wlan0: deauthenticating from 94:0c:6d:f4:fb:8e by local choice (reason=2)


Can anyone help me to get this working?

---

### Post by roosh on 2010-07-06
Hi,

Could you post the output of ```
lspci
``` and ```
lsmod
```?

---

