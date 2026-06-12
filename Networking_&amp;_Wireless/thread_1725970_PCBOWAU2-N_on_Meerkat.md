---
title: "PCBOWAU2-N on Meerkat"
date: 2011-04-10
forum: Networking &amp; Wireless
---

### Post by Dr. Strange on 2011-04-10
Hello, all;

I have a Patriot PCBOWAU2-N USB wifi adapter on Kubuntu Meerkat 64-bit. I can see the device in lsusb as a Realtek RTL8191S WLAN adapter. dmesg says the stock firmware loads fine. It shows up in network manager, sees my wifi network (as well as others nearby) just fine, and tries to connect to my wireless network, but keeps failing authentication. Network manager just keeps asking for the PSK and wicd actually says bad password (which I know for a fact is not correct - I am using the right credentials). I've confirmed that the adapter works on another machine running Kubuntu Meerkat 32-bit with no additional work needed - just plug in and go.

I've done my googling but I can't get this thing to work. Any suggestions would be greatly appreciated.

Alternately, can anyone recommend a USB 802.11 adapter that works with Kubuntu Meerkat 64-bit right out of the box? G necesary, N would be nice.


PS: I've tried the Patriot part in a similar machine also running Meerkat 64-bit, with the same negative results. That plus my googling suggests that either this device isn't supported under Meerkat 64-bit or it is but additional work is required. I'd love to be pointed in the right direction on getting this part working, or - failing that - recommendations for a replacement. Thanks.

---

### Post by NevilleS on 2011-04-24
I've got the same problem, with the exact same symptoms. The install CD contains some Linux drivers which I tried following the readme to install, but they didn't seem to help much. The readme recommends disabling network manager and using some command line scripts but I don't really like that... Although if it can be made to work I could be convinced ;)

---

