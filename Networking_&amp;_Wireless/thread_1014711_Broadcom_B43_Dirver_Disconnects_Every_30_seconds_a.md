---
title: "Broadcom B43 Dirver Disconnects Every 30 seconds after Intrepid upgrade"
date: 2008-12-18
forum: Networking &amp; Wireless
---

### Post by CharlieM on 2008-12-18
Hi all,

I am experiencing a very annoying WIFI bug. Previously on hardy the connection was very stable. It had another issue where it forgot the WPA PSK every time it rebooted, but once connected it worked flawlessly.

After upgrading to Intrepid the WIFI key bug has been solved with the new Network Manager but I have a much worse one now. Every 30 or so seconds it disconnects waits about 20 seconds then connects again. This keeps happening in a never ending cycle. When its connected the connection works flawlessly but it makes downloads impossible and even basic surfing difficult. Its taken me a couple of attempts just to open this post not sure what posting will be like :).

Its a US robotics PCMCIA card which uses the Broadcom B43 drivers. I have two access points (on different frequencies) which are different makes and models. It has exactly the same problem with both of them so I am fairly sure its not something odd they are doing.

I have included the DMESG output for one of these connect and disconnect cycles. I have obscured the MAC address, but suffice to say its the same address each time.

```
[  615.641946] wlan0: associated
[  625.648187] wlan0: disassociating by local choice (reason=3)
[  626.465206] wlan0: authenticate with AP 00:c0:49:xx:xx:xx
[  637.270651] wlan0: authenticate with AP 00:c0:49:xx:xx:xx
[  637.273741] wlan0: authenticated
[  637.273763] wlan0: associate with AP 00:c0:49:xx:xx:xx
[  637.275862] wlan0: RX AssocResp from 00:c0:49:xx:xx:xx (capab=0x411 status=0 aid=2)
[  637.275881] wlan0: associated
```

Does anyone have any suggestions or experienced the same problem? I have done a fair bit of Googling and have found few similar issues and absolutely now possible workarounds.

Any suggestions would be greatly appreciated.

Charlie M

---

### Post by nixscripter on 2008-12-18
If you still have the driver CD for the card, try using the Windows driver and Ndiswrapper. Some people have had better luck with it in terms of performance and reliability, and it might fix this problem too (but that's just a guess).

Instructions for ndiswrapper setup and install can be found here: [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

---

### Post by Ayuthia on 2008-12-18
Can you post your lspci -nn info?

---

