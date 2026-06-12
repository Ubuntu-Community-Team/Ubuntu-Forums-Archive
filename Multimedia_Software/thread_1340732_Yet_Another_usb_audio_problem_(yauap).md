---
title: "Yet Another usb audio problem (yauap)"
date: 2009-11-28
forum: Multimedia Software
---

### Post by Terryg on 2009-11-28
Greetings,

I just finisthed a double upgrade.  First from intrepid (where sound worked) to Jaunty (no sound at all) to finally Karmic. Where oddly enough sound initially worked fine.  I was listening to music on audacious. Then let's test this and I started up Firefox and went to the Nexuiz site and watched some fragging.  Evertything started out fine. After several minutes, the sound started sounding scratchy. Eventually no music at all, just noice.  Oddly I get system sounds (with a scratchy note).

My sound card is a builtin C-Media C6501

lsusb -vv | grep C-Media
Bus 002 Device 003: ID 0d8c:0201 C-Media Electronics, Inc. CM6501
  idVendor           0x0d8c C-Media Electronics, Inc.

I have posted output to pastebin: 

[http://pastebin.ca/1691949](http://pastebin.ca/1691949)


<>```
alsamixer
cannot open mixer: No such file or directory
```
```
sudo alsaconf 
```
doesnot find my sound card

I have searched several links on the Ubuntu forums and am still stumped.  I have compiled and installed the latest alsa. 

Tia,

Terry

---

