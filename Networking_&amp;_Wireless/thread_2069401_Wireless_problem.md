---
title: "Wireless problem"
date: 2012-10-10
forum: Networking &amp; Wireless
---

### Post by Virtueofselfishness on 2012-10-10
Yesterday my boss asked me why her WiFi wasn't working on her laptop so i asked what OS she had on it she told me it was Ubuntu her ex bf had given her the laptop with Ubuntu. anyways when she tried connecting to WiFi her WiFi wouldn't connect i asked her if there was an error MSG she said yes and sent me this picture below
i know the picture isn't much help an also i haven't checked out the laptop personally but i was wondering if anyone knew an answer just by the picture.
Thanks in advance :)

---

### Post by steeldriver on 2012-10-10
Could be one of several things I think -

[LIST]
[*]wireless soft or hard blocked by a switch
[*]missing or incompatible driver
[/LIST]
If you could post the outputs of the following terminal commands that would likely get us started towards finding out

```
rfkill list all
``````
lshw -C network
``````
lspci -vnn | grep -e '\[0200\]' -e '\[0280\]'
```or if it has a USB wireless adapter
```
lsusb | grep -i 'net'
```

---

### Post by Virtueofselfishness on 2012-10-10
ok will do i will be getting the laptop tomorrow.

---

