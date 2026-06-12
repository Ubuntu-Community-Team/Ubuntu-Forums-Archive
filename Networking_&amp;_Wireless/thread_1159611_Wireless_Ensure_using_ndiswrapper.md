---
title: "Wireless: Ensure using ndiswrapper"
date: 2009-05-14
forum: Networking &amp; Wireless
---

### Post by whaledawg on 2009-05-14
I've installed ndiswrappers but I suspect my system is still using the legacy wireless drivers.

Here is the output I get from lspci:

```
whaledawg@whaledawg-desktop:~$ lspci | grep Wireless
04:05.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller (rev 20)
whaledawg@whaledawg-desktop:~$ lspci -n | grep 04:05.0
04:05.0 0200: 10ec:8185 (rev 20)
```

I've installed and configured ndiswrappers according to this document:
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper")

Which mentions adding other drivers to a black list but nothing about RTL-8185. 

I know that ndis is working because I'm getting decent speed, but my wireless signal strength is still being listed as very low(a symptom I have when using legacy drivers). 

How can I purge any legacy driver to ensure that I don't have a conflict in the future?

---

