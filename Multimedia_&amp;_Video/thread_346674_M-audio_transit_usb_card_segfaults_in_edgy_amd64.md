---
title: "M-audio transit usb card segfaults in edgy amd64"
date: 2007-01-26
forum: Multimedia &amp; Video
---

### Post by 2ndunit on 2007-01-26
Hi,

I am trying to get my M-Audio Transit USB card to work in Edgy on AMD64 (kernel 2.6.17-10-generic #2 x86_64). The card used to work fine in Dapper.

I am using usb-midi-fw loader (madfuload) ver 1.2. dmesg indicates that madfuload dies with a segmentation fault.

lsusb shows:
```

Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 0763:2806 Midiman 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000

```

I tried running madfuload by hand, and got these results:

```
$ sudo ./madfuload -v -f ma006100.bin --waitbyte3 -D /proc/bus/usb/002/003
ma006100.bin: 5616 bytes read successfully
reading device descriptor ...
interface descriptor 0:0
interface descriptor 1:0
interface descriptor 1:1
interface descriptor 1:2
interface descriptor 1:3
interface descriptor 1:4
interface descriptor 1:5
interface descriptor 2:0
interface descriptor 2:1
interface descriptor 2:2
interface descriptor 2:3
Segmentation fault (core dumped)

```

Plugging the soundcard to a different USB port makes no difference. Previous posts on this seemed to indicate this could be a problem with udev (my version is 093-0ubuntu18 )

Can anyone please help?

I am hoping I don't have to downgrade to dapper just to get this working :(

---

