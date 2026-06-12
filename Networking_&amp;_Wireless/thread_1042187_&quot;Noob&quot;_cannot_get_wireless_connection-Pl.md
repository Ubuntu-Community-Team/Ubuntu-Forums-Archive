---
title: "&quot;Noob&quot; cannot get wireless connection-Please help"
date: 2009-01-17
forum: Networking &amp; Wireless
---

### Post by Liam_K on 2009-01-17
hi all...
first time to try ubuntu, absolutly sick of vista and antivirus slowing my machine down. I can connect to my netgear wireless modem by wire no problem, but i can't seem to connect wirelessly. some help would be appreciated. And...i am not exactly a whiz on computers, but willing to learn..

Thanks

Liam K

---

### Post by albinootje on 2009-01-17
> **Liam_K said:**
> I can connect to my netgear wireless modem by wire no problem, but i can't seem to connect wirelessly. some help would be appreciated.

Please post the output of the following in a terminal :
```

sudo lshw -C network
sudo update-usbids
lspci
lsusb

```
Thanks.

---

